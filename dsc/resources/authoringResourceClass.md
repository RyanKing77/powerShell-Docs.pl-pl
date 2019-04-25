---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Pisanie zasobu DSC niestandardowych przy użyciu klas programu PowerShell
ms.openlocfilehash: 34356f65bcb83153e7395a16d2a4a5cf2e507332
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076722"
---
# <a name="writing-a-custom-dsc-resource-with-powershell-classes"></a>Pisanie zasobu DSC niestandardowych przy użyciu klas programu PowerShell

> Dotyczy: Windows PowerShell 5.0

Wraz z wprowadzeniem klas programu PowerShell w programie Windows PowerShell 5.0 można zdefiniować zasób DSC, tworząc klasę. Klasa określa zarówno schematu, jak i wdrażania zasobów, dzięki czemu nie trzeba utworzyć oddzielny plik MOF. Struktura folderów dla zasobu oparte na klasach również jest prostsze, ponieważ **DSCResources** folder nie jest konieczne.

W zasobie DSC oparte na klasach schematu jest zdefiniowany jako właściwości klasy, które można modyfikować za pomocą atrybutów, aby określić typ właściwości... Zasób jest implementowany przez **Get()**, **elementu Set()**, i **Test()** metody (równoważne **Get TargetResource**, **TargetResource zestaw**, i **TargetResource testu** funkcje w zasobie skryptu.

W tym temacie utworzymy prostą zasób o nazwie **FileResource** który zarządza pliku w określonej ścieżce.

Aby uzyskać więcej informacji na temat zasobów DSC, zobacz [kompilacji Windows PowerShell Desired State Configuration zasobów niestandardowych](authoringResource.md)

>**Uwaga:** Kolekcje ogólne nie są obsługiwane w ramach oparte na klasach zasobów.

## <a name="folder-structure-for-a-class-resource"></a>Struktura folderów dla zasób klasy

Aby zaimplementować niestandardowy zasobu DSC przy użyciu klas programu PowerShell, utwórz następującą strukturę folderów. Klasa jest zdefiniowana w **MyDscResource.psm1** i manifestu modułu jest zdefiniowany w **MyDscResource.psd1**.

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResource (folder)
        MyDscResource.psm1
        MyDscResource.psd1
```

## <a name="create-the-class"></a>Tworzenie klasy

Class — słowo kluczowe jest użyć do tworzenia klas programu PowerShell. Aby określić, że klasa jest zasób DSC, użyj **DscResource()** atrybutu. Nazwa klasy jest nazwą zasobu DSC.

```powershell
[DscResource()]
class FileResource {
}
```

### <a name="declare-properties"></a>Deklarowanie właściwości

Schemat zasobów DSC jest zdefiniowany jako właściwości klasy. Firma Microsoft w następujący sposób deklarowania trzy właściwości.

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

Należy zauważyć, że właściwości są modyfikowane przez atrybuty. Znaczenie atrybutów jest następująca:

- **DscProperty(Key)**: Właściwość jest wymagana. Właściwość jest kluczem. Wartości wszystkich właściwości oznaczone jako klucze należy łączyć do unikatowego identyfikowania wystąpienia zasobu, w ramach konfiguracji.
- **DscProperty(Mandatory)**: Właściwość jest wymagana.
- **DscProperty(NotConfigurable)**: Właściwość jest tylko do odczytu. Właściwości oznaczona za pomocą tego atrybutu nie może ustawić konfigurację, ale są wypełniane przez **Get()** metody, jeśli jest obecny.
- **DscProperty()**: Właściwości nie można skonfigurować, ale nie jest wymagane.

**$Path** i **$SourcePath** właściwości są oba ciągi. **$CreationTime** jest [daty/godziny](/dotnet/api/system.datetime) właściwości. **$Ensure** właściwość jest typem wyliczenia, zdefiniowane w następujący sposób.

```powershell
enum Ensure
{
    Absent
    Present
}
```

### <a name="implementing-the-methods"></a>Implementacja metody

**Get()**, **elementu Set()**, i **Test()** metody są analogiczne do **Get TargetResource**, **TargetResource zestawu** , i **TargetResource testu** funkcje w zasobie skryptu.

Ten kod zawiera również funkcję CopyFile() funkcja pomocnicza, która kopiuje plik z **$SourcePath** do **$Path**.

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

### <a name="the-complete-file"></a>Kompletny plik

Plik klasy pełną poniżej.

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

Aby udostępnić zasób oparte na klasach aparatu DSC, należy dołączyć **DscResourcesToExport** instrukcja w pliku manifestu, który powoduje, że moduł można wyeksportować zasobu. Nasze manifest wygląda następująco:

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

## <a name="test-the-resource"></a>Zasób testowy

Po zapisaniu klasy i pliki manifestu w strukturze folderów, zgodnie z wcześniejszym opisem, można utworzyć konfiguracji, który używa nowego zasobu. Aby uzyskać informacje o sposobach uruchamiania konfiguracji DSC, zobacz [realizacja konfiguracji](../pull-server/enactingConfigurations.md). Następująca konfiguracja będzie sprawdzać czy plik w rozmiarze `c:\test\test.txt` istnieje i, jeśli nie, kopiuje plik z `c:\test.txt` (należy utworzyć `c:\test.txt` przed rozpoczęciem konfiguracji).

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

**PsDscRunAsCredential** właściwości mogą być używane w [konfiguracje DSC](../configurations/configurations.md) bloku zasobów, aby określić, że zasób powinien być wykonywany w ramach określonego zestawu poświadczeń.
Aby uzyskać więcej informacji, zobacz [systemem DSC przy użyciu poświadczeń użytkownika](../configurations/runAsUser.md).

### <a name="require-or-disallow-psdscrunascredential-for-your-resource"></a>Wymagaj lub nie zezwalaj na PsDscRunAsCredential zasobu bazy danych

**DscResource()** atrybut przyjmuje opcjonalny parametr **RunAsCredential**.
Ten parametr ma jedną z trzech wartości:

- `Optional` **PsDscRunAsCredential** jest opcjonalny w przypadku konfiguracji, które wywołują tego zasobu. Jest to wartość domyślna.
- `Mandatory` **PsDscRunAsCredential** musi być używany dla żadnej konfiguracji, który wywołuje ten zasób.
- `NotSupported` Konfiguracje, które wywołują tego zasobu nie można użyć **PsDscRunAsCredential**.
- `Default` Taki sam jak `Optional`.

Na przykład użyć do określenia, czy niestandardowy zasób nie obsługuje następujący atrybut **PsDscRunAsCredential**:

```powershell
[DscResource(RunAsCredential=NotSupported)]
class FileResource {
}
```

### <a name="declaring-multiple-class-resources-in-a-module"></a>Deklarowanie wiele zasobów klasy w module

Moduł można zdefiniować wiele zasobów DSC oparte na klasach. Struktura folderów można utworzyć w następujący sposób:

1. Zdefiniuj pierwszy zasób w "<ModuleName>psm1" plików i kolejnych zasobów w ramach **DSCResources** folderu.

   ```
   $env:ProgramFiles\WindowsPowerShell\Modules (folder)
        |- MyDscResource (folder)
           |- MyDscResource.psm1
              MyDscResource.psd1
        |- DSCResources
           |- SecondResource.psm1
   ```

2. Zdefiniuj wszystkich zasobów w ramach **DSCResources** folderu.

   ```
   $env:ProgramFiles\WindowsPowerShell\Modules (folder)
        |- MyDscResource (folder)
           |- MyDscResource.psm1
              MyDscResource.psd1
        |- DSCResources
           |- FirstResource.psm1
              SecondResource.psm1
   ```

> [!NOTE]
> W powyższych przykładach dodać dowolne pliki PSM1, w obszarze **DSCResources** do **NestedModules** kluczy w pliku PSD1.

### <a name="access-the-user-context"></a>Dostęp do kontekstu użytkownika

Aby uzyskać dostęp z kontekstu użytkownika, w ramach zasobów niestandardowych, można użyć zmiennej automatyczne `$global:PsDscContext`.

Na przykład poniższy kod napisać kontekstu użytkownika, pod którym jest uruchamiany zasób w strumieniu pełne dane wyjściowe:

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $global:PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a>Zobacz też

[Tworzenie niestandardowych Windows PowerShell Desired State Configuration zasobów](authoringResource.md)
