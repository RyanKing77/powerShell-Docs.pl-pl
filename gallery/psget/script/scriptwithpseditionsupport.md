---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galeria, programu powershell, polecenia cmdlet, psget
title: scriptwithpseditionsupport
ms.openlocfilehash: 18ce2d729199e0587ef92993db7fec44ef744ec7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="script-with-compatible-powershell-editions"></a><span data-ttu-id="f658e-103">Skrypt z niezgodne wersje programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="f658e-103">Script with compatible PowerShell Editions</span></span>
<span data-ttu-id="f658e-104">Od wersji 5.1 program PowerShell jest dostępny w różnych wersjach, które charakteryzują się różnymi zestawami funkcji i zgodnością z różnymi platformami.</span><span class="sxs-lookup"><span data-stu-id="f658e-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="f658e-105">**Wersja Desktop:** jest oparta na programie .NET Framework i zapewnia zgodność ze skryptami i modułami przeznaczonymi dla wersji programu PowerShell działających w pełnych wersjach systemu Windows, takich jak instalacja Podstawowe funkcje serwera i system Windows dla komputerów stacjonarnych.</span><span class="sxs-lookup"><span data-stu-id="f658e-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="f658e-106">**Wersja Core:** jest oparta na module .NET Core i zapewnia zgodność ze skryptami i modułami przeznaczonymi dla wersji programu PowerShell działających w ograniczonych wersjach systemu Windows, takich jak system Nano Server i Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="f658e-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="f658e-107">Informacje o działającej wersji programu PowerShell można znaleźć we właściwości PSEdition tabeli $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="f658e-107">The running edition of PowerShell is shown in the PSEdition property of $PSVersionTable.</span></span>
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

<span data-ttu-id="f658e-108">Autorzy skryptów mogą uniemożliwić wykonywanie skryptu, jeśli nie jest on uruchamiany w zgodnej wersji programu PowerShell, przy użyciu parametru PSEdition w instrukcji #requires.</span><span class="sxs-lookup"><span data-stu-id="f658e-108">Script authors can prevent a script from executing unless it is run on a compatible edition of PowerShell using the PSEdition parameter on a #requires statement.</span></span>
```powershell
Set-Content C:\script.ps1 -Value "#requires -PSEdition Core
Get-Process -Name PowerShell"
Get-Content C:\script.ps1
#requires -PSEdition Core
Get-Process -Name PowerShell

C:\script.ps1
C:\script.ps1 : The script 'script.ps1' cannot be run because it contained a "#requires" statement for PowerShell Core edition. The edition of PowerShell that is required by the script does not match the currently running PowerShell Desktop edition.
At line:1 char:1
+ C:\script.ps1
+ ~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (script.ps1:String) [], RuntimeException
    + FullyQualifiedErrorId : ScriptRequiresUnmatchedPSEdition
```

<span data-ttu-id="f658e-109">Użytkownicy w galerii programu PowerShell można znaleźć listy skryptów obsługiwane w określonej wersji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f658e-109">PowerShell Gallery users can find the list of scripts supported on a specific PowerShell Edition.</span></span>
<span data-ttu-id="f658e-110">Skrypty bez PSEdition_Desktop i PSEditon_Core są traktowane jako działają prawidłowo w przypadku wersji środowiska PowerShell pulpitu.</span><span class="sxs-lookup"><span data-stu-id="f658e-110">Scripts without PSEdition_Desktop and PSEditon_Core are considered to work fine on PowerShell Desktop editions.</span></span>

```powershell

# Find scripts supported on PowerShell Desktop edition
Find-Script -Tag PSEditon_Desktop

# Find scripts supported on PowerShell Core editions
Find-Script -Tag PSEditon_Core

```

## <a name="more-details"></a><span data-ttu-id="f658e-111">więcej informacji</span><span class="sxs-lookup"><span data-stu-id="f658e-111">More details</span></span>
### <a name="modules-with-pseditionsmodulemodulewithpseditionsupportmd"></a>[<span data-ttu-id="f658e-112">Moduły z elementami PSEdition</span><span class="sxs-lookup"><span data-stu-id="f658e-112">Modules with PSEditions</span></span>](../module/modulewithpseditionsupport.md)
### <a name="pseditions-support-on-powershellgallerypsgallerypsgallerypseditionsmd"></a>[<span data-ttu-id="f658e-113">Obsługa PSEditions na PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="f658e-113">PSEditions support on PowerShellGallery</span></span>](../../psgallery/psgallery_pseditions.md)