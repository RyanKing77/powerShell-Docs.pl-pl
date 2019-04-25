---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 0a481fb9d4f2aab89bc448c71b01f1d541cf24bc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085086"
---
# <a name="side-by-side-version-support-on-powershell-50-or-newer"></a>Obsługa wersji Side-by-Side, w programie PowerShell 5.0 lub nowszy

Jest teraz obsługę wersji modułu side-by-side (SxS) w Install-Module modułu aktualizacji i polecenia cmdlet Publish-Module, uruchamianą w programie Windows PowerShell 5.0 lub nowszej.
Ponadto dodaliśmy parametru - RequiredVersion do polecenia cmdlet Publish-Module do określenia wersji do opublikowania. Parametr ścieżki obsługuje teraz moduł ścieżki podstawowej z folderu wersji.

**Przykłady Install-Module:**
```powershell
Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.0 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name : PSScriptAnalyzer
Version : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.1 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name       : PSScriptAnalyzer
Version    : 1.1.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.1
Name       : PSScriptAnalyzer
Version    : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

Get-InstalledModule -Name PSScriptAnalyzer -AllVersions

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.1.0      PSScriptAnalyzer                    Module     PSGallery            PSScriptAnalyzer provides script analysis...
1.1.1      PSScriptAnalyzer                    Module     PSGallery            PSScriptAnalyzer provides script analysis...
```
