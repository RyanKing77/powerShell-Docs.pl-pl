---
ms.date: 03/28/2019
contributor: manikb
keywords: Galeria, programu powershell, polecenie cmdlet, psget
title: Moduły z niezgodne wersje programu PowerShell
ms.openlocfilehash: 425588c168a4f864fdc0c52aa53cfd748b80dc98
ms.sourcegitcommit: f268dce5b5e72be669be0c6634b8db11369bbae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/29/2019
ms.locfileid: "58623844"
---
# <a name="modules-with-compatible-powershell-editions"></a>Moduły z niezgodne wersje programu PowerShell

Od wersji 5.1 program PowerShell jest dostępny w różnych wersjach, które charakteryzują się różnymi zestawami funkcji i zgodnością z różnymi platformami.

- **Wersja Desktop:** Oparta na programie .NET Framework, dotyczy programu Windows PowerShell w wersji 4.0, a poniżej, a także program Windows PowerShell 5.1 w Windows Desktop, Windows Server, Windows Server Core i większości innych wersji Windows.
- **Wersja Core:** Oparta na module .NET Core, stosuje się do programu PowerShell Core 6.0 i nowszych oraz systemu Windows PowerShell 5.1 w ograniczonych wersjach Windows, takich jak Windows Nanoserver i Windows IoT.

Aby uzyskać więcej informacji na temat wersji programu PowerShell, zobacz [about_PowerShell_Editions][].

## <a name="declaring-compatible-editions"></a>Deklarowanie zgodne wersje

Autorzy modułów mogą zadeklarować zgodność swoich modułów z jedną lub kilkoma wersjami programu PowerShell przy użyciu klucza manifestu modułu CompatiblePSEditions. Ten klucz jest obsługiwany tylko w programie PowerShell 5.1 i w nowszych wersjach.

> [!NOTE]
> Po określeniu manifestu modułu CompatiblePSEditions kluczem, nie mogą być importowane w programie PowerShell w wersji 4 i poniżej.

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion 5.1
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
```

```Output
Desktop
Core
```

```powershell
$ModuleInfo | Get-Member CompatiblePSEditions
```

```Output
   TypeName: System.Management.Automation.PSModuleInfo

Name                 MemberType Definition
----                 ---------- ----------
CompatiblePSEditions Property   System.Collections.Generic.IEnumerable[string] CompatiblePSEditions {get;}
```

Podczas pobierania listy dostępnych modułów można filtrować tę listę według wersji programu PowerShell.

```powershell
Get-Module -ListAvailable -PSEdition Desktop
```

```Output
    Directory: C:\Program Files\WindowsPowerShell\Modules


ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Manifest   1.0        ModuleWithPSEditions
```

```powershell
Get-Module -ListAvailable -PSEdition Core | % CompatiblePSEditions
```

```Output
Desktop
Core
```

## <a name="targeting-multiple-editions"></a>Przeznaczone dla wielu wersji

Autorzy modułów mogą publikować moduł pojedynczego celem lub obie te wersje programu PowerShell (Desktop i Core).

Pojedynczy moduł może pracować na komputerach stacjonarnych, jak i Core wersje, w tym module Autor ma dodać logikę wymagane w obu polach RootModule, lub w manifeście modułu przy użyciu zmiennej $PSEdition. Moduły mogą mieć dwa zestawy skompilowane pliki dll przeznaczonych dla programów CoreCLR i FullCLR. Poniżej przedstawiono kilka opcji, aby pakiet modułu z logiką ładowania odpowiednie biblioteki dll.

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a>Option 1: Pakowanie modułu dla przeznaczone dla wielu wersji i wiele wersji programu PowerShell

Zawartość folderu modułu

- Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll
- Microsoft.Windows.PowerShell.ScriptAnalyzer.dll
- PSScriptAnalyzer.psd1
- PSScriptAnalyzer.psm1
- ScriptAnalyzer.format.ps1xml
- ScriptAnalyzer.types.ps1xml
- coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll
- coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll
- en-US\about_PSScriptAnalyzer.help.txt
- en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml
- PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll
- PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll
- Settings\CmdletDesign.psd1
- Settings\DSC.psd1
- Settings\ScriptFunctions.psd1
- Settings\ScriptingStyle.psd1
- Settings\ScriptSecurity.psd1

Zawartość pliku PSScriptAnalyzer.psd1

```powershell
@{

# Author of this module
Author = 'Microsoft Corporation'

# Script module or binary module file associated with this manifest.
RootModule = 'PSScriptAnalyzer.psm1'

# Version number of this module.
ModuleVersion = '1.6.1'

# ---
}
```

Poniżej logiki ładuje wymaganych zestawów w zależności od bieżącej wersji lub wersji.

Zawartość pliku PSScriptAnalyzer.psm1:

```powershell
#
# Script module for module 'PSScriptAnalyzer'
#
Set-StrictMode -Version Latest

# Set up some helper variables to make it easier to work with the module
$PSModule = $ExecutionContext.SessionState.Module
$PSModuleRoot = $PSModule.ModuleBase

# Import the appropriate nested binary module based on the current PowerShell version
$binaryModuleRoot = $PSModuleRoot


if (($PSVersionTable.Keys -contains "PSEdition") -and ($PSVersionTable.PSEdition -ne 'Desktop')) {
    $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'coreclr'
}
else
{
    if ($PSVersionTable.PSVersion -lt [Version]'5.0')
    {
        $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'PSv3'
    }
}

$binaryModulePath = Join-Path -Path $binaryModuleRoot -ChildPath 'Microsoft.Windows.PowerShell.ScriptAnalyzer.dll'
$binaryModule = Import-Module -Name $binaryModulePath -PassThru

# When the module is unloaded, remove the nested binary module that was loaded with it
$PSModule.OnRemove = {
    Remove-Module -ModuleInfo $binaryModule
}
```

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls-and-nestedrequired-modules"></a>Opcja 2: Użyj zmiennej $PSEdition w pliku PSD1 ładują odpowiednie biblioteki dll i zagnieżdżone/wymagane moduły

W PS 5.1 lub nowszej $PSEdition zmienna globalna jest dozwolone w pliku manifestu modułu. Za pomocą tej zmiennej, autora modułu, można określić wartości warunkowym w pliku manifestu modułu. $PSEdition zmiennej można odwoływać się w trybie ograniczonym języka lub w sekcji danych.

> [!NOTE]
> Gdy manifestu modułu jest określony za pomocą klucza CompatiblePSEditions lub używa `$PSEdition` zmiennej, nie można zaimportować na niższe wersje programu PowerShell.

Przykładowy plik manifestu modułu przy użyciu klucza CompatiblePSEditions

```powershell
@{
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
}
```

### <a name="module-contents"></a>Zawartość modułu

```powershell
dir -Recurse
```

```Output
    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions

Mode           LastWriteTime   Length Name
----           -------------   ------ ----
d-----    7/5/2016   1:37 PM          clr
d-----    7/5/2016   1:36 PM          coreclr
-a----    7/5/2016   1:34 PM     4906 ModuleWithEditions.psd1

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\clr

Mode           LastWriteTime    Length Name
----           -------------    ------ ----
-a----    7/5/2016   1:35 PM         0 MyFullClrNM1.dll
-a----    7/5/2016   1:35 PM         0 MyFullClrNM2.dll
-a----    7/5/2016   1:35 PM         0 MyFullClrRM.dl

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\coreclr

Mode           LastWriteTime   Length Name
----           -------------   ------ ----
-a----    7/5/2016   1:35 PM        0 MyCoreClrNM1.dll
-a----    7/5/2016   1:35 PM        0 MyCoreClrNM2.dll
-a----    7/5/2016   1:35 PM        0 MyCoreClrRM.dl
```

Użytkownicy z galerii programu PowerShell można znaleźć na liście modułów obsługiwane w określonej wersji programu PowerShell przy użyciu tagów PSEdition_Desktop i PSEdition_Core.

Moduły bez użycia tagów PSEdition_Desktop i PSEdition_Core są traktowane jako działają prawidłowo w wersji Desktop programu PowerShell.

```powershell
# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core
```

## <a name="more-details"></a>Więcej szczegółów

[Skrypty z elementami PSEdition](script-psedition-support.md)

[Obsługa elementami Psedition w galerii PowerShellGallery](../how-to/finding-packages/searching-by-compatibility.md)

[Aktualizowanie manifestu modułu](/powershell/module/powershellget/update-modulemanifest)

[about_PowerShell_Editions][]

[about_PowerShell_Editions]: /powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_Editions
