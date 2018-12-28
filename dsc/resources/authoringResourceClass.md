---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Pisanie zasobu DSC niestandardowych przy użyciu klas programu PowerShell
ms.openlocfilehash: 0759685b04688f574d72b62a15833832ad19e816
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405186"
---
# <a name="writing-a-custom-dsc-resource-with-powershell-classes"></a><span data-ttu-id="312e1-103">Pisanie zasobu DSC niestandardowych przy użyciu klas programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="312e1-103">Writing a custom DSC resource with PowerShell classes</span></span>

> <span data-ttu-id="312e1-104">Dotyczy: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="312e1-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="312e1-105">Wraz z wprowadzeniem klas programu PowerShell w programie Windows PowerShell 5.0 można zdefiniować zasób DSC, tworząc klasę.</span><span class="sxs-lookup"><span data-stu-id="312e1-105">With the introduction of PowerShell classes in Windows PowerShell 5.0, you can now define a DSC resource by creating a class.</span></span> <span data-ttu-id="312e1-106">Klasa określa zarówno schematu, jak i wdrażania zasobów, dzięki czemu nie trzeba utworzyć oddzielny plik MOF.</span><span class="sxs-lookup"><span data-stu-id="312e1-106">The class defines both the schema and the implementation of the resource, so there is no need to create a separate MOF file.</span></span> <span data-ttu-id="312e1-107">Struktura folderów dla zasobu oparte na klasach również jest prostsze, ponieważ **DSCResources** folder nie jest konieczne.</span><span class="sxs-lookup"><span data-stu-id="312e1-107">The folder structure for a class-based resource is also simpler, because a **DSCResources** folder is not necessary.</span></span>

<span data-ttu-id="312e1-108">W zasobie DSC oparte na klasach schematu jest zdefiniowany jako właściwości klasy, które można modyfikować za pomocą atrybutów, aby określić typ właściwości...</span><span class="sxs-lookup"><span data-stu-id="312e1-108">In a class-based DSC resource, the schema is defined as properties of the class which can be modified with attributes to specify the property type..</span></span> <span data-ttu-id="312e1-109">Zasób jest implementowany przez **Get()**, **elementu Set()**, i **Test()** metody (równoważne **Get TargetResource**, **TargetResource zestaw**, i **TargetResource testu** funkcje w zasobie skryptu.</span><span class="sxs-lookup"><span data-stu-id="312e1-109">The resource is implemented by **Get()**, **Set()**, and **Test()** methods (equivalent to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="312e1-110">W tym temacie utworzymy prostą zasób o nazwie **FileResource** który zarządza pliku w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="312e1-110">In this topic, we will create a simple resource named **FileResource** that manages a file in a specified path.</span></span>

<span data-ttu-id="312e1-111">Aby uzyskać więcej informacji na temat zasobów DSC, zobacz [kompilacji Windows PowerShell Desired State Configuration zasobów niestandardowych](authoringResource.md)</span><span class="sxs-lookup"><span data-stu-id="312e1-111">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md)</span></span>

><span data-ttu-id="312e1-112">**Uwaga:** Kolekcje ogólne nie są obsługiwane w ramach oparte na klasach zasobów.</span><span class="sxs-lookup"><span data-stu-id="312e1-112">**Note:** Generic collections are not supported in class-based resources.</span></span>

## <a name="folder-structure-for-a-class-resource"></a><span data-ttu-id="312e1-113">Struktura folderów dla zasób klasy</span><span class="sxs-lookup"><span data-stu-id="312e1-113">Folder structure for a class resource</span></span>

<span data-ttu-id="312e1-114">Aby zaimplementować niestandardowy zasobu DSC przy użyciu klas programu PowerShell, utwórz następującą strukturę folderów.</span><span class="sxs-lookup"><span data-stu-id="312e1-114">To implement a DSC custom resource with a PowerShell class, create the following folder structure.</span></span> <span data-ttu-id="312e1-115">Klasa jest zdefiniowana w **MyDscResource.psm1** i manifestu modułu jest zdefiniowany w **MyDscResource.psd1**.</span><span class="sxs-lookup"><span data-stu-id="312e1-115">The class is defined in **MyDscResource.psm1** and the module manifest is defined in **MyDscResource.psd1**.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResource (folder)
        |- MyDscResource.psm1
           MyDscResource.psd1
```

## <a name="create-the-class"></a><span data-ttu-id="312e1-116">Tworzenie klasy</span><span class="sxs-lookup"><span data-stu-id="312e1-116">Create the class</span></span>

<span data-ttu-id="312e1-117">Class — słowo kluczowe jest użyć do tworzenia klas programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="312e1-117">You use the class keyword to create a PowerShell class.</span></span> <span data-ttu-id="312e1-118">Aby określić, że klasa jest zasób DSC, użyj **DscResource()** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="312e1-118">To specify that a class is a DSC resource, use the **DscResource()** attribute.</span></span> <span data-ttu-id="312e1-119">Nazwa klasy jest nazwą zasobu DSC.</span><span class="sxs-lookup"><span data-stu-id="312e1-119">The name of the class is the name of the DSC resource.</span></span>

```powershell
[DscResource()]
class FileResource {
}
```

### <a name="declare-properties"></a><span data-ttu-id="312e1-120">Deklarowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="312e1-120">Declare properties</span></span>

<span data-ttu-id="312e1-121">Schemat zasobów DSC jest zdefiniowany jako właściwości klasy.</span><span class="sxs-lookup"><span data-stu-id="312e1-121">The DSC resource schema is defined as properties of the class.</span></span> <span data-ttu-id="312e1-122">Firma Microsoft w następujący sposób deklarowania trzy właściwości.</span><span class="sxs-lookup"><span data-stu-id="312e1-122">We declare three properties as follows.</span></span>

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

<span data-ttu-id="312e1-123">Należy zauważyć, że właściwości są modyfikowane przez atrybuty.</span><span class="sxs-lookup"><span data-stu-id="312e1-123">Notice that the properties are modified by attributes.</span></span> <span data-ttu-id="312e1-124">Znaczenie atrybutów jest następująca:</span><span class="sxs-lookup"><span data-stu-id="312e1-124">The meaning of the attributes is as follows:</span></span>

- <span data-ttu-id="312e1-125">**DscProperty(Key)**: Właściwość jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="312e1-125">**DscProperty(Key)**: The property is required.</span></span> <span data-ttu-id="312e1-126">Właściwość jest kluczem.</span><span class="sxs-lookup"><span data-stu-id="312e1-126">The property is a key.</span></span> <span data-ttu-id="312e1-127">Wartości wszystkich właściwości oznaczone jako klucze należy łączyć do unikatowego identyfikowania wystąpienia zasobu, w ramach konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="312e1-127">The values of all properties marked as keys must combine to uniquely identify a resource instance within a configuration.</span></span>
- <span data-ttu-id="312e1-128">**DscProperty(Mandatory)**: Właściwość jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="312e1-128">**DscProperty(Mandatory)**: The property is required.</span></span>
- <span data-ttu-id="312e1-129">**DscProperty(NotConfigurable)**: Właściwość jest tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="312e1-129">**DscProperty(NotConfigurable)**: The property is read-only.</span></span> <span data-ttu-id="312e1-130">Właściwości oznaczona za pomocą tego atrybutu nie może ustawić konfigurację, ale są wypełniane przez **Get()** metody, jeśli jest obecny.</span><span class="sxs-lookup"><span data-stu-id="312e1-130">Properties marked with this attribute cannot be set by a configuration, but are populated by the **Get()** method when present.</span></span>
- <span data-ttu-id="312e1-131">**DscProperty()**: Właściwości nie można skonfigurować, ale nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="312e1-131">**DscProperty()**: The property is configurable, but it is not required.</span></span>

<span data-ttu-id="312e1-132">**$Path** i **$SourcePath** właściwości są oba ciągi.</span><span class="sxs-lookup"><span data-stu-id="312e1-132">The **$Path** and **$SourcePath** properties are both strings.</span></span> <span data-ttu-id="312e1-133">**$CreationTime** jest [daty/godziny](/dotnet/api/system.datetime) właściwości.</span><span class="sxs-lookup"><span data-stu-id="312e1-133">The **$CreationTime** is a [DateTime](/dotnet/api/system.datetime) property.</span></span> <span data-ttu-id="312e1-134">**$Ensure** właściwość jest typem wyliczenia, zdefiniowane w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="312e1-134">The **$Ensure** property is an enumeration type, defined as follows.</span></span>

```powershell
enum Ensure
{
    Absent
    Present
}
```

### <a name="implementing-the-methods"></a><span data-ttu-id="312e1-135">Implementacja metody</span><span class="sxs-lookup"><span data-stu-id="312e1-135">Implementing the methods</span></span>

<span data-ttu-id="312e1-136">**Get()**, **elementu Set()**, i **Test()** metody są analogiczne do **Get TargetResource**, **TargetResource zestawu** , i **TargetResource testu** funkcje w zasobie skryptu.</span><span class="sxs-lookup"><span data-stu-id="312e1-136">The **Get()**, **Set()**, and **Test()** methods are analogous to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="312e1-137">Ten kod zawiera również funkcję CopyFile() funkcja pomocnicza, która kopiuje plik z **$SourcePath** do **$Path**.</span><span class="sxs-lookup"><span data-stu-id="312e1-137">This code also includes the CopyFile() function, a helper function that copies the file from **$SourcePath** to **$Path**.</span></span>

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

### <a name="the-complete-file"></a><span data-ttu-id="312e1-138">Kompletny plik</span><span class="sxs-lookup"><span data-stu-id="312e1-138">The complete file</span></span>
<span data-ttu-id="312e1-139">Plik klasy pełną poniżej.</span><span class="sxs-lookup"><span data-stu-id="312e1-139">The complete class file follows.</span></span>

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


## <a name="create-a-manifest"></a><span data-ttu-id="312e1-140">Tworzenie manifestu</span><span class="sxs-lookup"><span data-stu-id="312e1-140">Create a manifest</span></span>

<span data-ttu-id="312e1-141">Aby udostępnić zasób oparte na klasach aparatu DSC, należy dołączyć **DscResourcesToExport** instrukcja w pliku manifestu, który powoduje, że moduł można wyeksportować zasobu.</span><span class="sxs-lookup"><span data-stu-id="312e1-141">To make a class-based resource available to the DSC engine, you must include a **DscResourcesToExport** statement in the manifest file that instructs the module to export the resource.</span></span> <span data-ttu-id="312e1-142">Nasze manifest wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="312e1-142">Our manifest looks like this:</span></span>

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

## <a name="test-the-resource"></a><span data-ttu-id="312e1-143">Zasób testowy</span><span class="sxs-lookup"><span data-stu-id="312e1-143">Test the resource</span></span>

<span data-ttu-id="312e1-144">Po zapisaniu klasy i pliki manifestu w strukturze folderów, zgodnie z wcześniejszym opisem, można utworzyć konfiguracji, który używa nowego zasobu.</span><span class="sxs-lookup"><span data-stu-id="312e1-144">After saving the class and manifest files in the folder structure as described earlier, you can create a configuration that uses the new resource.</span></span> <span data-ttu-id="312e1-145">Aby uzyskać informacje o sposobach uruchamiania konfiguracji DSC, zobacz [realizacja konfiguracji](../pull-server/enactingConfigurations.md).</span><span class="sxs-lookup"><span data-stu-id="312e1-145">For information about how to run a DSC configuration, see [Enacting configurations](../pull-server/enactingConfigurations.md).</span></span> <span data-ttu-id="312e1-146">Następująca konfiguracja będzie sprawdzać czy plik w rozmiarze `c:\test\test.txt` istnieje i, jeśli nie, kopiuje plik z `c:\test.txt` (należy utworzyć `c:\test.txt` przed rozpoczęciem konfiguracji).</span><span class="sxs-lookup"><span data-stu-id="312e1-146">The following configuration will check to see whether the file at `c:\test\test.txt` exists, and, if not, copies the file from `c:\test.txt` (you should create `c:\test.txt` before you run the configuration).</span></span>

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

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="312e1-147">Obsługa PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="312e1-147">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="312e1-148">**Uwaga:** **PsDscRunAsCredential** jest obsługiwana w programie PowerShell 5.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="312e1-148">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="312e1-149">**PsDscRunAsCredential** właściwości mogą być używane w [konfiguracje DSC](../configurations/configurations.md) bloku zasobów, aby określić, że zasób powinien być wykonywany w ramach określonego zestawu poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="312e1-149">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="312e1-150">Aby uzyskać więcej informacji, zobacz [systemem DSC przy użyciu poświadczeń użytkownika](../configurations/runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="312e1-150">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

### <a name="require-or-disallow-psdscrunascredential-for-your-resource"></a><span data-ttu-id="312e1-151">Wymagaj lub nie zezwalaj na PsDscRunAsCredential zasobu bazy danych</span><span class="sxs-lookup"><span data-stu-id="312e1-151">Require or disallow PsDscRunAsCredential for your resource</span></span>

<span data-ttu-id="312e1-152">**DscResource()** atrybut przyjmuje opcjonalny parametr **RunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="312e1-152">The **DscResource()** attribute takes an optional parameter **RunAsCredential**.</span></span>
<span data-ttu-id="312e1-153">Ten parametr ma jedną z trzech wartości:</span><span class="sxs-lookup"><span data-stu-id="312e1-153">This parameter takes one of three values:</span></span>

- <span data-ttu-id="312e1-154">`Optional` **PsDscRunAsCredential** jest opcjonalny w przypadku konfiguracji, które wywołują tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="312e1-154">`Optional` **PsDscRunAsCredential** is optional for configurations that call this resource.</span></span> <span data-ttu-id="312e1-155">Jest to wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="312e1-155">This is the default value.</span></span>
- <span data-ttu-id="312e1-156">`Mandatory` **PsDscRunAsCredential** musi być używany dla żadnej konfiguracji, który wywołuje ten zasób.</span><span class="sxs-lookup"><span data-stu-id="312e1-156">`Mandatory` **PsDscRunAsCredential** must be used for any configuration that calls this resource.</span></span>
- <span data-ttu-id="312e1-157">`NotSupported` Konfiguracje, które wywołują tego zasobu nie można użyć **PsDscRunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="312e1-157">`NotSupported` Configurations that call this resource cannot use **PsDscRunAsCredential**.</span></span>
- <span data-ttu-id="312e1-158">`Default` Taki sam jak `Optional`.</span><span class="sxs-lookup"><span data-stu-id="312e1-158">`Default` Same as `Optional`.</span></span>

<span data-ttu-id="312e1-159">Na przykład użyć do określenia, czy niestandardowy zasób nie obsługuje następujący atrybut **PsDscRunAsCredential**:</span><span class="sxs-lookup"><span data-stu-id="312e1-159">For example, use the following attribute to specify that your custom resource does not support using **PsDscRunAsCredential**:</span></span>

```powershell
[DscResource(RunAsCredential=NotSupported)]
class FileResource {
}
```

### <a name="access-the-user-context"></a><span data-ttu-id="312e1-160">Dostęp do kontekstu użytkownika</span><span class="sxs-lookup"><span data-stu-id="312e1-160">Access the user context</span></span>

<span data-ttu-id="312e1-161">Aby uzyskać dostęp z kontekstu użytkownika, w ramach zasobów niestandardowych, można użyć zmiennej automatyczne `$global:PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="312e1-161">To access the user context from within a custom resource, you can use the automatic variable `$global:PsDscContext`.</span></span>

<span data-ttu-id="312e1-162">Na przykład poniższy kod napisać kontekstu użytkownika, pod którym jest uruchamiany zasób w strumieniu pełne dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="312e1-162">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $global:PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="312e1-163">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="312e1-163">See Also</span></span>
### <a name="concepts"></a><span data-ttu-id="312e1-164">Pojęcia</span><span class="sxs-lookup"><span data-stu-id="312e1-164">Concepts</span></span>
[<span data-ttu-id="312e1-165">Tworzenie niestandardowych Windows PowerShell Desired State Configuration zasobów</span><span class="sxs-lookup"><span data-stu-id="312e1-165">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)