---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 0a481fb9d4f2aab89bc448c71b01f1d541cf24bc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687993"
---
# <a name="side-by-side-version-support-on-powershell-50-or-newer"></a><span data-ttu-id="ad116-102">Obsługa wersji Side-by-Side, w programie PowerShell 5.0 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="ad116-102">Side-by-Side Version Support on PowerShell 5.0 or newer</span></span>

<span data-ttu-id="ad116-103">Jest teraz obsługę wersji modułu side-by-side (SxS) w Install-Module modułu aktualizacji i polecenia cmdlet Publish-Module, uruchamianą w programie Windows PowerShell 5.0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="ad116-103">There is now side-by-side (SxS) module version support in Install-Module, Update-Module, and Publish-Module cmdlets that run in Windows PowerShell 5.0 or newer.</span></span>
<span data-ttu-id="ad116-104">Ponadto dodaliśmy parametru - RequiredVersion do polecenia cmdlet Publish-Module do określenia wersji do opublikowania.</span><span class="sxs-lookup"><span data-stu-id="ad116-104">Also, we have added a -RequiredVersion parameter to the Publish-Module cmdlet to specify the version to be published.</span></span> <span data-ttu-id="ad116-105">Parametr ścieżki obsługuje teraz moduł ścieżki podstawowej z folderu wersji.</span><span class="sxs-lookup"><span data-stu-id="ad116-105">The Path parameter now supports the module base path with the version folder.</span></span>

<span data-ttu-id="ad116-106">**Przykłady Install-Module:**</span><span class="sxs-lookup"><span data-stu-id="ad116-106">**Install-Module examples:**</span></span>
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
