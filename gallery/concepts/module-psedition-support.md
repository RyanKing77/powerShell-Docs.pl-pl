---
ms.date: 06/12/2017
contributor: manikb
keywords: Galeria, programu powershell, polecenie cmdlet, psget
title: Moduły z niezgodne wersje programu PowerShell
ms.openlocfilehash: 653cfa82be9d0150da8d8765c96e35be99497262
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892325"
---
# <a name="modules-with-compatible-powershell-editions"></a><span data-ttu-id="215a0-103">Moduły z niezgodne wersje programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="215a0-103">Modules with compatible PowerShell Editions</span></span>

<span data-ttu-id="215a0-104">Od wersji 5.1 program PowerShell jest dostępny w różnych wersjach, które charakteryzują się różnymi zestawami funkcji i zgodnością z różnymi platformami.</span><span class="sxs-lookup"><span data-stu-id="215a0-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="215a0-105">**Wersja Desktop:** jest oparta na programie .NET Framework i zapewnia zgodność ze skryptami i modułami przeznaczonymi dla wersji programu PowerShell działających w pełnych wersjach systemu Windows, takich jak instalacja Podstawowe funkcje serwera i system Windows dla komputerów stacjonarnych.</span><span class="sxs-lookup"><span data-stu-id="215a0-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="215a0-106">**Wersja Core:** jest oparta na module .NET Core i zapewnia zgodność ze skryptami i modułami przeznaczonymi dla wersji programu PowerShell działających w ograniczonych wersjach systemu Windows, takich jak system Nano Server i Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="215a0-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

## <a name="the-running-edition-of-powershell-is-shown-in-the-psedition-property-of-psversiontable"></a><span data-ttu-id="215a0-107">Informacje o działającej wersji programu PowerShell można znaleźć we właściwości PSEdition tabeli $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="215a0-107">The running edition of PowerShell is shown in the PSEdition property of $PSVersionTable.</span></span>

```powershell
$PSVersionTable
```

```output
Name                           Value
----                           -----
PSVersion                      5.1.14300.1000
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
CLRVersion                     4.0.30319.42000
BuildVersion                   10.0.14300.1000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

## <a name="module-authors-can-declare-their-modules-to-be-compatible-with-one-or-more-powershell-editions-using-the-compatiblepseditions-module-manifest-key-this-key-is-only-supported-on-powershell-51-or-later"></a><span data-ttu-id="215a0-108">Autorzy modułów mogą zadeklarować zgodność swoich modułów z jedną lub kilkoma wersjami programu PowerShell przy użyciu klucza manifestu modułu CompatiblePSEditions.</span><span class="sxs-lookup"><span data-stu-id="215a0-108">Module authors can declare their modules to be compatible with one or more PowerShell editions using the CompatiblePSEditions module manifest key.</span></span> <span data-ttu-id="215a0-109">Ten klucz jest obsługiwany tylko w programie PowerShell 5.1 i w nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="215a0-109">This key is only supported on PowerShell 5.1 or later.</span></span>

> [!NOTE]
> <span data-ttu-id="215a0-110">Po określeniu manifestu modułu CompatiblePSEditions kluczem, nie mogą być importowane w niższych wersjach programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="215a0-110">Once a module manifest is specified with the CompatiblePSEditions key, it can not be imported on lower versions of PowerShell.</span></span>

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion 5.1
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
```

```output
Desktop
Core
```

```powershell
$ModuleInfo | Get-Member CompatiblePSEditions
```

```output
   TypeName: System.Management.Automation.PSModuleInfo

Name                 MemberType Definition
----                 ---------- ----------
CompatiblePSEditions Property   System.Collections.Generic.IEnumerable[string] CompatiblePSEditions {get;}
```

<span data-ttu-id="215a0-111">Podczas pobierania listy dostępnych modułów można filtrować tę listę według wersji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="215a0-111">When getting a list of available modules, you can filter the list by PowerShell edition.</span></span>

```powershell
Get-Module -ListAvailable -PSEdition Desktop
```

```output
    Directory: C:\Program Files\WindowsPowerShell\Modules


ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Manifest   1.0        ModuleWithPSEditions
```

```powershell
Get-Module -ListAvailable -PSEdition Core | % CompatiblePSEditions
```

```output
Desktop
Core
```

## <a name="module-authors-can-publish-a-single-module-targeting-to-either-or-both-powershell-editions-desktop-and-core"></a><span data-ttu-id="215a0-112">Autorzy modułów mogą publikować moduł pojedynczego celem lub obie te wersje programu PowerShell (Desktop i rdzeni)</span><span class="sxs-lookup"><span data-stu-id="215a0-112">Module authors can publish a single module targeting to either or both PowerShell editions (Desktop and Core)</span></span>

<span data-ttu-id="215a0-113">Pojedynczy moduł może pracować na komputerach stacjonarnych, jak i Core wersje, w tym module Autor ma dodać logikę wymagane w obu polach RootModule, lub w manifeście modułu przy użyciu zmiennej $PSEdition.</span><span class="sxs-lookup"><span data-stu-id="215a0-113">A single module can work on both Desktop and Core editions, in that module author has to add required logic in either RootModule or in the module manifest using $PSEdition variable.</span></span>
<span data-ttu-id="215a0-114">Moduły mogą mieć dwa zestawy skompilowane pliki dll przeznaczonych dla programów CoreCLR i FullCLR.</span><span class="sxs-lookup"><span data-stu-id="215a0-114">Modules can have two sets of compiled DLLs targeting both CoreCLR and FullCLR.</span></span>
<span data-ttu-id="215a0-115">Poniżej przedstawiono kilka opcji, aby pakiet modułu z logiką ładowania odpowiednie biblioteki dll.</span><span class="sxs-lookup"><span data-stu-id="215a0-115">Here are the couple of options to package your module with logic for loading proper dlls.</span></span>

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a><span data-ttu-id="215a0-116">Opcja 1: Pakowanie modułu dla przeznaczone dla wielu wersji i wiele wersji programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="215a0-116">Option 1: Packaging a module for targeting multiple versions and multiple editions of PowerShell</span></span>

#### <a name="module-folder-contents"></a><span data-ttu-id="215a0-117">Zawartość folderu modułu</span><span class="sxs-lookup"><span data-stu-id="215a0-117">Module folder contents</span></span>

- <span data-ttu-id="215a0-118">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="215a0-118">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="215a0-119">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="215a0-119">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="215a0-120">PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="215a0-120">PSScriptAnalyzer.psd1</span></span>
- <span data-ttu-id="215a0-121">PSScriptAnalyzer.psm1</span><span class="sxs-lookup"><span data-stu-id="215a0-121">PSScriptAnalyzer.psm1</span></span>
- <span data-ttu-id="215a0-122">ScriptAnalyzer.format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="215a0-122">ScriptAnalyzer.format.ps1xml</span></span>
- <span data-ttu-id="215a0-123">ScriptAnalyzer.types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="215a0-123">ScriptAnalyzer.types.ps1xml</span></span>
- <span data-ttu-id="215a0-124">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="215a0-124">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="215a0-125">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="215a0-125">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="215a0-126">en-US\about_PSScriptAnalyzer.help.txt</span><span class="sxs-lookup"><span data-stu-id="215a0-126">en-US\about_PSScriptAnalyzer.help.txt</span></span>
- <span data-ttu-id="215a0-127">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span><span class="sxs-lookup"><span data-stu-id="215a0-127">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span></span>
- <span data-ttu-id="215a0-128">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="215a0-128">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="215a0-129">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="215a0-129">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="215a0-130">Settings\CmdletDesign.psd1</span><span class="sxs-lookup"><span data-stu-id="215a0-130">Settings\CmdletDesign.psd1</span></span>
- <span data-ttu-id="215a0-131">Settings\DSC.psd1</span><span class="sxs-lookup"><span data-stu-id="215a0-131">Settings\DSC.psd1</span></span>
- <span data-ttu-id="215a0-132">Settings\ScriptFunctions.psd1</span><span class="sxs-lookup"><span data-stu-id="215a0-132">Settings\ScriptFunctions.psd1</span></span>
- <span data-ttu-id="215a0-133">Settings\ScriptingStyle.psd1</span><span class="sxs-lookup"><span data-stu-id="215a0-133">Settings\ScriptingStyle.psd1</span></span>
- <span data-ttu-id="215a0-134">Settings\ScriptSecurity.psd1</span><span class="sxs-lookup"><span data-stu-id="215a0-134">Settings\ScriptSecurity.psd1</span></span>

#### <a name="contents-of-psscriptanalyzerpsd1-file"></a><span data-ttu-id="215a0-135">Zawartość pliku PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="215a0-135">Contents of PSScriptAnalyzer.psd1 file</span></span>

```powershell
@{

# Author of this module
Author = 'Microsoft Corporation'

# Script module or binary module file associated with this manifest.
RootModule = 'PSScriptAnalyzer.psm1'

# Version number of this module.
ModuleVersion = '1.6.1'

# ---
}
```

#### <a name="contents-of-psscriptanalyzerpsm1-file"></a><span data-ttu-id="215a0-136">Zawartość pliku PSScriptAnalyzer.psm1</span><span class="sxs-lookup"><span data-stu-id="215a0-136">Contents of PSScriptAnalyzer.psm1 file</span></span>

<span data-ttu-id="215a0-137">Poniżej logiki ładuje wymaganych zestawów w zależności od bieżącej wersji lub wersji.</span><span class="sxs-lookup"><span data-stu-id="215a0-137">Below logic loads the required assemblies depending on the current edition or version.</span></span>

```powershell
#
# Script module for module 'PSScriptAnalyzer'
#
Set-StrictMode -Version Latest

# Set up some helper variables to make it easier to work with the module
$PSModule = $ExecutionContext.SessionState.Module
$PSModuleRoot = $PSModule.ModuleBase

# Import the appropriate nested binary module based on the current PowerShell version
$binaryModuleRoot = $PSModuleRoot


if (($PSVersionTable.Keys -contains "PSEdition") -and ($PSVersionTable.PSEdition -ne 'Desktop')) {
    $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'coreclr'
}
else
{
    if ($PSVersionTable.PSVersion -lt [Version]'5.0') {
        $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'PSv3'
    }
}

$binaryModulePath = Join-Path -Path $binaryModuleRoot -ChildPath 'Microsoft.Windows.PowerShell.ScriptAnalyzer.dll'
$binaryModule = Import-Module -Name $binaryModulePath -PassThru

# When the module is unloaded, remove the nested binary module that was loaded with it
$PSModule.OnRemove = {
    Remove-Module -ModuleInfo $binaryModule
}

```

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls-and-nestedrequired-modules"></a><span data-ttu-id="215a0-138">Opcja 2: Użyj zmiennej $PSEdition w pliku PSD1 ładują odpowiednie biblioteki dll i zagnieżdżone/wymagane moduły</span><span class="sxs-lookup"><span data-stu-id="215a0-138">Option 2: Use $PSEdition variable in the PSD1 file to load the proper DLLs and Nested/Required modules</span></span>

<span data-ttu-id="215a0-139">W PS 5.1 lub nowszej $PSEdition zmienna globalna jest dozwolone w pliku manifestu modułu.</span><span class="sxs-lookup"><span data-stu-id="215a0-139">In PS 5.1 or newer, $PSEdition global variable is allowed in the module manifest file.</span></span>
<span data-ttu-id="215a0-140">Za pomocą tej zmiennej, autora modułu, można określić wartości warunkowym w pliku manifestu modułu.</span><span class="sxs-lookup"><span data-stu-id="215a0-140">Using this variable, module author can specify the conditional values in the module manifest file.</span></span> <span data-ttu-id="215a0-141">$PSEdition zmiennej można odwoływać się w trybie ograniczonym języka lub w sekcji danych.</span><span class="sxs-lookup"><span data-stu-id="215a0-141">$PSEdition variable can be referenced in restricted language mode or a Data section.</span></span>

> [!NOTE]
> <span data-ttu-id="215a0-142">Gdy manifestu modułu została określona za pomocą klucza CompatiblePSEditions lub użyto zmiennej $PSEdition, nie mogą być importowane w niższych wersjach programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="215a0-142">Once a module manifest is specified with the CompatiblePSEditions key or uses $PSEdition variable, it can not be imported on lower versions of PowerShell.</span></span>

#### <a name="sample-module-manifest-file-with-compatiblepseditions-key"></a><span data-ttu-id="215a0-143">Przykładowy plik manifestu modułu przy użyciu klucza CompatiblePSEditions</span><span class="sxs-lookup"><span data-stu-id="215a0-143">Sample module manifest file with CompatiblePSEditions key</span></span>

```powershell
@{
# - - -

# Script module or binary module file associated with this manifest.
RootModule = if($PSEdition -eq 'Core')
{
'coreclr\MyCoreClrRM.dll'
}
else # Desktop
{
'clr\MyFullClrRM.dll'
}

# Supported PSEditions
CompatiblePSEditions = 'Desktop', 'Core'

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = if($PSEdition -eq 'Core')
{
'coreclr\MyCoreClrNM1.dll',
'coreclr\MyCoreClrNM2.dll'
}
else # Desktop
{
'clr\MyFullClrNM1.dll',
'clr\MyFullClrNM2.dll'
}

# -- - -
}
```

#### <a name="module-contents"></a><span data-ttu-id="215a0-144">Zawartość modułu</span><span class="sxs-lookup"><span data-stu-id="215a0-144">Module contents</span></span>

```powershell
dir -Recurse
```

```output
    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/5/2016   1:37 PM                clr
d-----         7/5/2016   1:36 PM                coreclr
-a----         7/5/2016   1:34 PM           4906 ModuleWithEditions.psd1

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\clr

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         7/5/2016   1:35 PM              0 MyFullClrNM1.dll
-a----         7/5/2016   1:35 PM              0 MyFullClrNM2.dll
-a----         7/5/2016   1:35 PM              0 MyFullClrRM.dl

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\coreclr

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         7/5/2016   1:35 PM              0 MyCoreClrNM1.dll
-a----         7/5/2016   1:35 PM              0 MyCoreClrNM2.dll
-a----         7/5/2016   1:35 PM              0 MyCoreClrRM.dl
```

## <a name="powershell-gallery-users-can-find-the-list-of-modules-supported-on-a-specific-powershell-edition-using-tags-pseditiondesktop-and-pseditioncore"></a><span data-ttu-id="215a0-145">Użytkownicy z galerii programu PowerShell można znaleźć na liście modułów obsługiwane w określonej wersji programu PowerShell przy użyciu tagów PSEdition_Desktop i PSEdition_Core.</span><span class="sxs-lookup"><span data-stu-id="215a0-145">PowerShell Gallery users can find the list of modules supported on a specific PowerShell Edition using tags PSEdition_Desktop and PSEdition_Core.</span></span>

<span data-ttu-id="215a0-146">Moduły bez użycia tagów PSEdition_Desktop i PSEdition_Core są traktowane jako działają prawidłowo w wersji Desktop programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="215a0-146">Modules without PSEdition_Desktop and PSEdition_Core tags are considered to work fine on PowerShell Desktop editions.</span></span>

```powershell

# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core

```

## <a name="more-details"></a><span data-ttu-id="215a0-147">Więcej szczegółów</span><span class="sxs-lookup"><span data-stu-id="215a0-147">More details</span></span>

[<span data-ttu-id="215a0-148">Skrypty z elementami PSEdition</span><span class="sxs-lookup"><span data-stu-id="215a0-148">Scripts with PSEditions</span></span>](script-psedition-support.md)

[<span data-ttu-id="215a0-149">Obsługa elementami Psedition w galerii PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="215a0-149">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-items/searching-by-psedition.md)

[<span data-ttu-id="215a0-150">Aktualizowanie manifestu modułu</span><span class="sxs-lookup"><span data-stu-id="215a0-150">Update module manifest</span></span>](/powershell/module/powershellget/update-modulemanifest)