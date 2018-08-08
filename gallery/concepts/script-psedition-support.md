---
ms.date: 06/12/2017
contributor: manikb
keywords: Galeria, programu powershell, polecenie cmdlet, psget
title: Skrypt za pomocą niezgodne wersje programu PowerShell
ms.openlocfilehash: 2313131fe17dcd9508db514883ae3dcb837fb07e
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587214"
---
# <a name="script-with-compatible-powershell-editions"></a>Skrypt za pomocą niezgodne wersje programu PowerShell

Od wersji 5.1 program PowerShell jest dostępny w różnych wersjach, które charakteryzują się różnymi zestawami funkcji i zgodnością z różnymi platformami.

- **Wersja Desktop:** jest oparta na programie .NET Framework i zapewnia zgodność ze skryptami i modułami przeznaczonymi dla wersji programu PowerShell działających w pełnych wersjach systemu Windows, takich jak instalacja Podstawowe funkcje serwera i system Windows dla komputerów stacjonarnych.

- **Wersja Core:** jest oparta na module .NET Core i zapewnia zgodność ze skryptami i modułami przeznaczonymi dla wersji programu PowerShell działających w ograniczonych wersjach systemu Windows, takich jak system Nano Server i Windows IoT.

Informacje o działającej wersji programu PowerShell można znaleźć we właściwości PSEdition tabeli $PSVersionTable.

```powershell
$PSVersionTable

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

Autorzy skryptów mogą uniemożliwić wykonywanie, chyba że jest on uruchamiany w zgodnej wersji programu PowerShell przy użyciu parametru PSEdition w skrypcie `#requires` instrukcji.

```powershell
Set-Content C:\script.ps1 -Value "#requires -PSEdition Core
Get-Process -Name PowerShell"
Get-Content C:\script.ps1
#requires -PSEdition Core
Get-Process -Name PowerShell

C:\script.ps1
C:\script.ps1 : The script 'script.ps1' cannot be run because it contained a "#requires" statement for PowerShell editions 'Core'. The edition of PowerShell that is required by the script does not match the currently running PowerShell Desktop edition.
At line:1 char:1
+ C:\script.ps1
+ ~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (script.ps1:String) [], RuntimeException
    + FullyQualifiedErrorId : ScriptRequiresUnmatchedPSEdition
```

Użytkownicy z galerii programu PowerShell można znaleźć listy skrypty obsługiwane w określonej wersji programu PowerShell.
Skrypty bez użycia tagów PSEdition_Desktop i PSEdition_Core są traktowane jako działają prawidłowo w wersji Desktop programu PowerShell.

```powershell
# Find scripts supported on PowerShell Desktop edition
Find-Script -Tag PSEdition_Desktop

# Find scripts supported on PowerShell Core edition
Find-Script -Tag PSEdition_Core
```

## <a name="more-details"></a>Więcej szczegółów

- [Moduły z elementami PSEdition](module-psedition-support.md)
- [Obsługa elementami Psedition w galerii PowerShellGallery](../how-to/finding-items/searching-by-psedition.md)
