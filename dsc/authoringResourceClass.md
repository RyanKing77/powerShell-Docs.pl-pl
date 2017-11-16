---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Pisanie niestandardowych zasobów DSC z klasami programu PowerShell"
ms.openlocfilehash: 6e482f45c7d09898d46de20f43dcf16ecf3da7da
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="writing-a-custom-dsc-resource-with-powershell-classes"></a><span data-ttu-id="21c7a-103">Pisanie niestandardowych zasobów DSC z klasami programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="21c7a-103">Writing a custom DSC resource with PowerShell classes</span></span>

> <span data-ttu-id="21c7a-104">Dotyczy: Windows środowiska Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="21c7a-104">Applies To: Windows Windows PowerShell 5.0</span></span>

<span data-ttu-id="21c7a-105">Wraz z wprowadzeniem klasy środowiska PowerShell w programie Windows PowerShell 5.0 można zdefiniować zasobów DSC przez tworzenie klasy.</span><span class="sxs-lookup"><span data-stu-id="21c7a-105">With the introduction of PowerShell classes in Windows PowerShell 5.0, you can now define a DSC resource by creating a class.</span></span> <span data-ttu-id="21c7a-106">Klasa definiuje zarówno schematu, jak i implementację zasobu, więc nie trzeba utworzyć oddzielny plik MOF.</span><span class="sxs-lookup"><span data-stu-id="21c7a-106">The class defines both the schema and the implementation of the resource, so there is no need to create a separate MOF file.</span></span> <span data-ttu-id="21c7a-107">Struktura folderów dla klasy zasobu również jest łatwiejsze, ponieważ **DSCResources** folder nie jest konieczne.</span><span class="sxs-lookup"><span data-stu-id="21c7a-107">The folder structure for a class-based resource is also simpler, because a **DSCResources** folder is not necessary.</span></span>

<span data-ttu-id="21c7a-108">W zasobie DSC klasy schemat jest zdefiniowany jako właściwości klasy, które można zmodyfikować atrybutów, aby określić typ właściwości.</span><span class="sxs-lookup"><span data-stu-id="21c7a-108">In a class-based DSC resource, the schema is defined as properties of the class which can be modified with attributes to specify the property type..</span></span> <span data-ttu-id="21c7a-109">Zasób jest implementowany przez **Get()**, **Set()**, i **Test()** metod (odpowiednikiem **Get-TargetResource**, **Zestaw TargetResource**, i **TargetResource testu** funkcji zasobu skryptu.</span><span class="sxs-lookup"><span data-stu-id="21c7a-109">The resource is implemented by **Get()**, **Set()**, and **Test()** methods (equivalent to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="21c7a-110">W tym temacie, utworzymy proste zasób o nazwie **FileResource** który zarządza pliku w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="21c7a-110">In this topic, we will create a simple resource named **FileResource** that manages a file in a specified path.</span></span>

<span data-ttu-id="21c7a-111">Aby uzyskać więcej informacji o zasobach DSC, zobacz [kompilacji systemu Windows PowerShell Desired stan konfiguracji zasobów niestandardowych](authoringResource.md)</span><span class="sxs-lookup"><span data-stu-id="21c7a-111">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md)</span></span>

><span data-ttu-id="21c7a-112">**Uwaga:** kolekcje ogólne nie są obsługiwane w zasoby oparte na klasie.</span><span class="sxs-lookup"><span data-stu-id="21c7a-112">**Note:** Generic collections are not supported in class-based resources.</span></span>

## <a name="folder-structure-for-a-class-resource"></a><span data-ttu-id="21c7a-113">Struktura folderów dla zasobu — klasa</span><span class="sxs-lookup"><span data-stu-id="21c7a-113">Folder structure for a class resource</span></span>

<span data-ttu-id="21c7a-114">Aby zaimplementować DSC niestandardowego zasobu z klasą programu PowerShell, utwórz następującą strukturę folderów.</span><span class="sxs-lookup"><span data-stu-id="21c7a-114">To implement a DSC custom resource with a PowerShell class, create the following folder structure.</span></span> <span data-ttu-id="21c7a-115">Klasa jest zdefiniowana w **MyDscResource.psm1** i manifestu modułu jest zdefiniowany w **MyDscResource.psd1**.</span><span class="sxs-lookup"><span data-stu-id="21c7a-115">The class is defined in **MyDscResource.psm1** and the module manifest is defined in **MyDscResource.psd1**.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResource (folder)
        |- MyDscResource.psm1 
           MyDscResource.psd1 
```

## <a name="create-the-class"></a><span data-ttu-id="21c7a-116">Tworzenie klasy</span><span class="sxs-lookup"><span data-stu-id="21c7a-116">Create the class</span></span>

<span data-ttu-id="21c7a-117">Class — słowo kluczowe umożliwia tworzenie klasy środowiska PowerShell.</span><span class="sxs-lookup"><span data-stu-id="21c7a-117">You use the class keyword to create a PowerShell class.</span></span> <span data-ttu-id="21c7a-118">Aby określić, że klasa jest zasobem DSC, użyj **DscResource()** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="21c7a-118">To specify that a class is a DSC resource, use the **DscResource()** attribute.</span></span> <span data-ttu-id="21c7a-119">Nazwa klasy jest nazwa zasobu usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="21c7a-119">The name of the class is the name of the DSC resource.</span></span>

```powershell
[DscResource()]
class FileResource {
}
```

### <a name="declare-properties"></a><span data-ttu-id="21c7a-120">Deklarowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="21c7a-120">Declare properties</span></span>

<span data-ttu-id="21c7a-121">Schemat zasobów DSC jest zdefiniowany jako właściwości klasy.</span><span class="sxs-lookup"><span data-stu-id="21c7a-121">The DSC resource schema is defined as properties of the class.</span></span> <span data-ttu-id="21c7a-122">Firma Microsoft zadeklarować trzech właściwości w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="21c7a-122">We declare three properties as follows.</span></span>

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

<span data-ttu-id="21c7a-123">Należy zauważyć, że właściwości są modyfikowane przez atrybuty.</span><span class="sxs-lookup"><span data-stu-id="21c7a-123">Notice that the properties are modified by attributes.</span></span> <span data-ttu-id="21c7a-124">Znaczenie atrybutów jest następujący:</span><span class="sxs-lookup"><span data-stu-id="21c7a-124">The meaning of the attributes is as follows:</span></span>

- <span data-ttu-id="21c7a-125">**DscProperty(Key)**: właściwość jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="21c7a-125">**DscProperty(Key)**: The property is required.</span></span> <span data-ttu-id="21c7a-126">Właściwość jest kluczem.</span><span class="sxs-lookup"><span data-stu-id="21c7a-126">The property is a key.</span></span> <span data-ttu-id="21c7a-127">Wartości wszystkich właściwości oznaczone jako klucze połączyć do unikatowej identyfikacji wystąpienia zasobu, w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="21c7a-127">The values of all properties marked as keys must combine to uniquely identify a resource instance within a configuration.</span></span>
- <span data-ttu-id="21c7a-128">**DscProperty(Mandatory)**: właściwość jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="21c7a-128">**DscProperty(Mandatory)**: The property is required.</span></span>
- <span data-ttu-id="21c7a-129">**DscProperty(NotConfigurable)**: właściwość jest tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="21c7a-129">**DscProperty(NotConfigurable)**: The property is read-only.</span></span> <span data-ttu-id="21c7a-130">Oznaczone atrybutem tej właściwości nie można ustawić konfiguracji, ale są wypełnione przez **Get()** metody, jeśli jest obecny.</span><span class="sxs-lookup"><span data-stu-id="21c7a-130">Properties marked with this attribute cannot be set by a configuration, but are populated by the **Get()** method when present.</span></span>
- <span data-ttu-id="21c7a-131">**DscProperty()**: właściwość jest konfigurowalne, ale nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="21c7a-131">**DscProperty()**: The property is configurable, but it is not required.</span></span>

<span data-ttu-id="21c7a-132">**$Path** i **$SourcePath** właściwości są oba parametry.</span><span class="sxs-lookup"><span data-stu-id="21c7a-132">The **$Path** and **$SourcePath** properties are both strings.</span></span> <span data-ttu-id="21c7a-133">**$CreationTime** jest [DateTime](https://technet.microsoft.com/en-us/library/system.datetime.aspx) właściwości.</span><span class="sxs-lookup"><span data-stu-id="21c7a-133">The **$CreationTime** is a [DateTime](https://technet.microsoft.com/en-us/library/system.datetime.aspx) property.</span></span> <span data-ttu-id="21c7a-134">**$Ensure** właściwość jest typu wyliczeniowego, zdefiniowane w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="21c7a-134">The **$Ensure** property is an enumeration type, defined as follows.</span></span>

```powershell
enum Ensure 
{ 
    Absent 
    Present 
}
```

### <a name="implementing-the-methods"></a><span data-ttu-id="21c7a-135">Implementacja metody</span><span class="sxs-lookup"><span data-stu-id="21c7a-135">Implementing the methods</span></span>

<span data-ttu-id="21c7a-136">**Get()**, **Set()**, i **Test()** metody są odpowiednikiem **Get-TargetResource**, **TargetResource zestawu** , i **TargetResource testu** funkcji zasobu skryptu.</span><span class="sxs-lookup"><span data-stu-id="21c7a-136">The **Get()**, **Set()**, and **Test()** methods are analogous to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="21c7a-137">Ten kod zawiera również funkcję CopyFile() funkcji pomocnika, który kopiuje plik z **$SourcePath** do **$Path**.</span><span class="sxs-lookup"><span data-stu-id="21c7a-137">This code also includes the CopyFile() function, a helper function that copies the file from **$SourcePath** to **$Path**.</span></span> 

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

### <a name="the-complete-file"></a><span data-ttu-id="21c7a-138">Zakończenie pliku</span><span class="sxs-lookup"><span data-stu-id="21c7a-138">The complete file</span></span>
<span data-ttu-id="21c7a-139">Plik klasy pełną jest zgodna.</span><span class="sxs-lookup"><span data-stu-id="21c7a-139">The complete class file follows.</span></span>

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


## <a name="create-a-manifest"></a><span data-ttu-id="21c7a-140">Tworzenie manifestu</span><span class="sxs-lookup"><span data-stu-id="21c7a-140">Create a manifest</span></span>

<span data-ttu-id="21c7a-141">Aby udostępnić aparat DSC klasy zasobu, należy uwzględnić **DscResourcesToExport** instrukcji w pliku manifestu, który powoduje, że modułu do eksportu zasobu.</span><span class="sxs-lookup"><span data-stu-id="21c7a-141">To make a class-based resource available to the DSC engine, you must include a **DscResourcesToExport** statement in the manifest file that instructs the module to export the resource.</span></span> <span data-ttu-id="21c7a-142">Nasze manifest wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="21c7a-142">Our manifest looks like this:</span></span>

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

## <a name="test-the-resource"></a><span data-ttu-id="21c7a-143">Test zasobu</span><span class="sxs-lookup"><span data-stu-id="21c7a-143">Test the resource</span></span>

<span data-ttu-id="21c7a-144">Po zapisaniu klasy i pliki manifestu w strukturze folderu, jak opisano wcześniej, można utworzyć konfiguracji, który używa nowego zasobu.</span><span class="sxs-lookup"><span data-stu-id="21c7a-144">After saving the class and manifest files in the folder structure as described earlier, you can create a configuration that uses the new resource.</span></span> <span data-ttu-id="21c7a-145">Aby uzyskać informacje o sposobie uruchamiania konfiguracji DSC, zobacz [wprowadzania konfiguracji](enactingConfigurations.md).</span><span class="sxs-lookup"><span data-stu-id="21c7a-145">For information about how to run a DSC configuration, see [Enacting configurations](enactingConfigurations.md).</span></span> <span data-ttu-id="21c7a-146">Następująca konfiguracja będzie sprawdzać czy pliku `c:\test\test.txt` istnieje i, jeśli nie, kopiuje plik z `c:\test.txt` (należy utworzyć `c:\test.txt` przed uruchomieniem konfiguracji).</span><span class="sxs-lookup"><span data-stu-id="21c7a-146">The following configuration will check to see whether the file at `c:\test\test.txt` exists, and, if not, copies the file from `c:\test.txt` (you should create `c:\test.txt` before you run the configuration).</span></span>

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

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="21c7a-147">Obsługa PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="21c7a-147">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="21c7a-148">**Uwaga:** **PsDscRunAsCredential** jest obsługiwana w programie PowerShell 5.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="21c7a-148">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="21c7a-149">**PsDscRunAsCredential** właściwość może być używana w [konfiguracji DSC](configurations.md) bloku zasobów, aby określić, że zasób powinny być uruchamiane w określonym zestawie poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="21c7a-149">The **PsDscRunAsCredential** property can be used in [DSC configurations](configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="21c7a-150">Aby uzyskać więcej informacji, zobacz [DSC uruchomiony przy użyciu poświadczeń użytkownika](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="21c7a-150">For more information, see [Running DSC with user credentials](runAsUser.md).</span></span>

### <a name="require-or-disallow-psdscrunascredential-for-your-resource"></a><span data-ttu-id="21c7a-151">Wymagaj lub nie zezwalaj na PsDscRunAsCredential dla zasobu</span><span class="sxs-lookup"><span data-stu-id="21c7a-151">Require or disallow PsDscRunAsCredential for your resource</span></span>

<span data-ttu-id="21c7a-152">**DscResource()** atrybut przyjmuje opcjonalny parametr **RunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="21c7a-152">The **DscResource()** attribute takes an optional parameter **RunAsCredential**.</span></span>
<span data-ttu-id="21c7a-153">Ten parametr przyjmuje jeden z trzech wartości:</span><span class="sxs-lookup"><span data-stu-id="21c7a-153">This parameter takes one of three values:</span></span>

- <span data-ttu-id="21c7a-154">`Optional`**PsDscRunAsCredential** jest opcjonalny w przypadku konfiguracji, które wywołują tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="21c7a-154">`Optional` **PsDscRunAsCredential** is optional for configurations that call this resource.</span></span> <span data-ttu-id="21c7a-155">Jest to wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="21c7a-155">This is the default value.</span></span>
- <span data-ttu-id="21c7a-156">`Mandatory`**PsDscRunAsCredential** muszą być używane do żadnej konfiguracji, który wywołuje tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="21c7a-156">`Mandatory` **PsDscRunAsCredential** must be used for any configuration that calls this resource.</span></span>
- <span data-ttu-id="21c7a-157">`NotSupported`Konfiguracje, które wywołują tego zasobu nie można użyć **PsDscRunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="21c7a-157">`NotSupported` Configurations that call this resource cannot use **PsDscRunAsCredential**.</span></span>
- <span data-ttu-id="21c7a-158">`Default`Taki sam jak `Optional`.</span><span class="sxs-lookup"><span data-stu-id="21c7a-158">`Default` Same as `Optional`.</span></span>

<span data-ttu-id="21c7a-159">Na przykład użyć następującego atrybutu, aby określić, że zasób niestandardowy nie obsługuje używania **PsDscRunAsCredential**:</span><span class="sxs-lookup"><span data-stu-id="21c7a-159">For example, use the following attribute to specify that your custom resource does not support using **PsDscRunAsCredential**:</span></span>

```powershell
[DscResource(RunAsCredential=NotSupported)]
class FileResource {
}
```

### <a name="access-the-user-context"></a><span data-ttu-id="21c7a-160">Dostęp z kontekstu użytkownika</span><span class="sxs-lookup"><span data-stu-id="21c7a-160">Access the user context</span></span>

<span data-ttu-id="21c7a-161">Aby uzyskać dostęp z kontekstu użytkownika, w ramach zasobów niestandardowych, można użyć automatycznego zmiennej `$global:PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="21c7a-161">To access the user context from within a custom resource, you can use the automatic variable `$global:PsDscContext`.</span></span>

<span data-ttu-id="21c7a-162">Na przykład następujący kod zapisać kontekstu użytkownika, na którym uruchomiono zasobu w strumieniu pełne dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="21c7a-162">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $global:PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="21c7a-163">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="21c7a-163">See Also</span></span>
### <a name="concepts"></a><span data-ttu-id="21c7a-164">Pojęcia</span><span class="sxs-lookup"><span data-stu-id="21c7a-164">Concepts</span></span>
[<span data-ttu-id="21c7a-165">Tworzenie niestandardowych Windows PowerShell Desired konfiguracji stanu zasobów</span><span class="sxs-lookup"><span data-stu-id="21c7a-165">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)

