---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Pisanie niestandardowych zasobów DSC z klasami programu PowerShell"
ms.openlocfilehash: 53757f965c51fee699409b5a8ecda802dda9801f
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="writing-a-custom-dsc-resource-with-powershell-classes"></a>Pisanie niestandardowych zasobów DSC z klasami programu PowerShell

> Dotyczy: Windows środowiska Windows PowerShell 5.0

Wraz z wprowadzeniem klasy środowiska PowerShell w programie Windows PowerShell 5.0 można zdefiniować zasobów DSC przez tworzenie klasy. Klasa definiuje zarówno schematu, jak i implementację zasobu, więc nie trzeba utworzyć oddzielny plik MOF. Struktura folderów dla klasy zasobu również jest łatwiejsze, ponieważ **DSCResources** folder nie jest konieczne.

W zasobie DSC klasy schemat jest zdefiniowany jako właściwości klasy, które można zmodyfikować atrybutów, aby określić typ właściwości. Zasób jest implementowany przez **Get()**, **Set()**, i **Test()** metod (odpowiednikiem **Get-TargetResource**, **Zestaw TargetResource**, i **TargetResource testu** funkcji zasobu skryptu.

W tym temacie, utworzymy proste zasób o nazwie **FileResource** który zarządza pliku w określonej ścieżce.

Aby uzyskać więcej informacji o zasobach DSC, zobacz [kompilacji systemu Windows PowerShell Desired stan konfiguracji zasobów niestandardowych](authoringResource.md)

>**Uwaga:** kolekcje ogólne nie są obsługiwane w zasoby oparte na klasie.

## <a name="folder-structure-for-a-class-resource"></a>Struktura folderów dla zasobu — klasa

Aby zaimplementować DSC niestandardowego zasobu z klasą programu PowerShell, utwórz następującą strukturę folderów. Klasa jest zdefiniowana w **MyDscResource.psm1** i manifestu modułu jest zdefiniowany w **MyDscResource.psd1**.

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResource (folder)
        |- MyDscResource.psm1 
           MyDscResource.psd1 
```

## <a name="create-the-class"></a>Tworzenie klasy

Class — słowo kluczowe umożliwia tworzenie klasy środowiska PowerShell. Aby określić, że klasa jest zasobem DSC, użyj **DscResource()** atrybutu. Nazwa klasy jest nazwa zasobu usługi Konfiguracja DSC.

```powershell
[DscResource()]
class FileResource {
}
```

### <a name="declare-properties"></a>Deklarowanie właściwości

Schemat zasobów DSC jest zdefiniowany jako właściwości klasy. Firma Microsoft zadeklarować trzech właściwości w następujący sposób.

```powershell
[DscProperty(Key)]
[string]$Path

[DscProperty(Mandatory)]
[Ensure] $Ensure

[DscProperty(Mandatory)]
[string] $SourcePath

[DscProperty(NotConfigurable)]
[Nullable[datetime]] $CreationTime
```

Należy zauważyć, że właściwości są modyfikowane przez atrybuty. Znaczenie atrybutów jest następujący:

- **DscProperty(Key)**: właściwość jest wymagana. Właściwość jest kluczem. Wartości wszystkich właściwości oznaczone jako klucze połączyć do unikatowej identyfikacji wystąpienia zasobu, w konfiguracji.
- **DscProperty(Mandatory)**: właściwość jest wymagana.
- **DscProperty(NotConfigurable)**: właściwość jest tylko do odczytu. Oznaczone atrybutem tej właściwości nie można ustawić konfiguracji, ale są wypełnione przez **Get()** metody, jeśli jest obecny.
- **DscProperty()**: właściwość jest konfigurowalne, ale nie jest wymagana.

**$Path** i **$SourcePath** właściwości są oba parametry. **$CreationTime** jest [DateTime](https://technet.microsoft.com/library/system.datetime.aspx) właściwości. **$Ensure** właściwość jest typu wyliczeniowego, zdefiniowane w następujący sposób.

```powershell
enum Ensure 
{ 
    Absent 
    Present 
}
```

### <a name="implementing-the-methods"></a>Implementacja metody

**Get()**, **Set()**, i **Test()** metody są odpowiednikiem **Get-TargetResource**, **TargetResource zestawu** , i **TargetResource testu** funkcji zasobu skryptu.

Ten kod zawiera również funkcję CopyFile() funkcji pomocnika, który kopiuje plik z **$SourcePath** do **$Path**. 

```powershell

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)

        if ($this.ensure -eq [Ensure]::Present)
        {
            if(-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    <#
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ErrorAction Ignore

        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }

        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = New-Object -TypeName System.IO.FileInfo($this.Path)

        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
```

### <a name="the-complete-file"></a>Zakończenie pliku
Plik klasy pełną jest zgodna.

```powershell
enum Ensure
{
    Absent
    Present
}

<#
   This resource manages the file in a specific path.
   [DscResource()] indicates the class is a DSC resource
#>

[DscResource()]
class FileResource
{
    <#
       This property is the fully qualified path to the file that is
       expected to be present or absent.

       The [DscProperty(Key)] attribute indicates the property is a
       key and its value uniquely identifies a resource instance.
       Defining this attribute also means the property is required
       and DSC will ensure a value is set before calling the resource.

       A DSC resource must define at least one key property.
    #>
    [DscProperty(Key)]
    [string]$Path

    <#
        This property indicates if the settings should be present or absent
        on the system. For present, the resource ensures the file pointed
        to by $Path exists. For absent, it ensures the file point to by
        $Path does not exist.

        The [DscProperty(Mandatory)] attribute indicates the property is
        required and DSC will guarantee it is set.

        If Mandatory is not specified or if it is defined as
        Mandatory=$false, the value is not guaranteed to be set when DSC
        calls the resource.  This is appropriate for optional properties.
    #>
    [DscProperty(Mandatory)]
    [Ensure] $Ensure

    <#
       This property defines the fully qualified path to a file that will
       be placed on the system if $Ensure = Present and $Path does not
        exist.

       NOTE: This property is required because [DscProperty(Mandatory)] is
        set.
    #>
    [DscProperty(Mandatory)]
    [string] $SourcePath

    <#
       This property reports the file's create timestamp.

       [DscProperty(NotConfigurable)] attribute indicates the property is
       not configurable in DSC configuration.  Properties marked this way
       are populated by the Get() method to report additional details
       about the resource when it is present.

    #>
    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $CreationTime

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)
        if ($this.ensure -eq [Ensure]::Present)
        {
            if (-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    <#
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ea Ignore
        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }

        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = new-object System.IO.FileInfo($this.Path)
        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                 to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
} # This module defines a class for a DSC "FileResource" provider.
```


## <a name="create-a-manifest"></a>Tworzenie manifestu

Aby udostępnić aparat DSC klasy zasobu, należy uwzględnić **DscResourcesToExport** instrukcji w pliku manifestu, który powoduje, że modułu do eksportu zasobu. Nasze manifest wygląda następująco:

```powershell
@{

# Script module or binary module file associated with this manifest.
RootModule = 'MyDscResource.psm1'

DscResourcesToExport = 'FileResource'

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '81624038-5e71-40f8-8905-b1a87afe22d7'

# Author of this module
Author = 'Microsoft Corporation'

# Company or vendor of this module
CompanyName = 'Microsoft Corporation'

# Copyright statement for this module
Copyright = '(c) 2014 Microsoft. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '5.0'

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''
} 
```

## <a name="test-the-resource"></a>Test zasobu

Po zapisaniu klasy i pliki manifestu w strukturze folderu, jak opisano wcześniej, można utworzyć konfiguracji, który używa nowego zasobu. Aby uzyskać informacje o sposobie uruchamiania konfiguracji DSC, zobacz [wprowadzania konfiguracji](enactingConfigurations.md). Następująca konfiguracja będzie sprawdzać czy pliku `c:\test\test.txt` istnieje i, jeśli nie, kopiuje plik z `c:\test.txt` (należy utworzyć `c:\test.txt` przed uruchomieniem konfiguracji).

```powershell
Configuration Test
{
    Import-DSCResource -module MyDscResource
    FileResource file
    {
        Path = "C:\test\test.txt"
        SourcePath = "c:\test.txt"
        Ensure = "Present"
    } 
}
Test
Start-DscConfiguration -Wait -Force Test
```

## <a name="supporting-psdscrunascredential"></a>Obsługa PsDscRunAsCredential

>**Uwaga:** **PsDscRunAsCredential** jest obsługiwana w programie PowerShell 5.0 i nowszych.

**PsDscRunAsCredential** właściwość może być używana w [konfiguracji DSC](configurations.md) bloku zasobów, aby określić, że zasób powinny być uruchamiane w określonym zestawie poświadczeń.
Aby uzyskać więcej informacji, zobacz [DSC uruchomiony przy użyciu poświadczeń użytkownika](runAsUser.md).

### <a name="require-or-disallow-psdscrunascredential-for-your-resource"></a>Wymagaj lub nie zezwalaj na PsDscRunAsCredential dla zasobu

**DscResource()** atrybut przyjmuje opcjonalny parametr **RunAsCredential**.
Ten parametr przyjmuje jeden z trzech wartości:

- `Optional` **PsDscRunAsCredential** jest opcjonalny w przypadku konfiguracji, które wywołują tego zasobu. Jest to wartość domyślna.
- `Mandatory` **PsDscRunAsCredential** muszą być używane do żadnej konfiguracji, który wywołuje tego zasobu.
- `NotSupported` Konfiguracje, które wywołują tego zasobu nie można użyć **PsDscRunAsCredential**.
- `Default` Taki sam jak `Optional`.

Na przykład użyć następującego atrybutu, aby określić, że zasób niestandardowy nie obsługuje używania **PsDscRunAsCredential**:

```powershell
[DscResource(RunAsCredential=NotSupported)]
class FileResource {
}
```

### <a name="access-the-user-context"></a>Dostęp z kontekstu użytkownika

Aby uzyskać dostęp z kontekstu użytkownika, w ramach zasobów niestandardowych, można użyć automatycznego zmiennej `$global:PsDscContext`.

Na przykład następujący kod zapisać kontekstu użytkownika, na którym uruchomiono zasobu w strumieniu pełne dane wyjściowe:

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $global:PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a>Zobacz też
### <a name="concepts"></a>Pojęcia
[Tworzenie niestandardowych Windows PowerShell Desired konfiguracji stanu zasobów](authoringResource.md)

