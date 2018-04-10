---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: f9a121c320ffb780503dbe0c278f698a6fa40289
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="side-by-side-version-support-on-powershell-50-or-newer"></a><span data-ttu-id="0a075-102">Obsługa wersji Side-by-Side programu PowerShell w wersji 5.0 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="0a075-102">Side-by-Side Version Support on PowerShell 5.0 or newer</span></span>

<span data-ttu-id="0a075-103">Teraz jest obsługa wersji modułu side-by-side (SxS) w Module instalacji aktualizacji modułu i poleceń cmdlet Publish-Module uruchamiających w programie Windows PowerShell 5.0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="0a075-103">There is now side-by-side (SxS) module version support in Install-Module, Update-Module, and Publish-Module cmdlets that run in Windows PowerShell 5.0 or newer.</span></span>
<span data-ttu-id="0a075-104">Ponadto dodano parametru - RequiredVersion do polecenia cmdlet Publish-Module do określania wersji do opublikowania.</span><span class="sxs-lookup"><span data-stu-id="0a075-104">Also, we have added a -RequiredVersion parameter to the Publish-Module cmdlet to specify the version to be published.</span></span> <span data-ttu-id="0a075-105">Parametr Path obsługuje teraz ścieżki bazowej modułu z folderem wersji.</span><span class="sxs-lookup"><span data-stu-id="0a075-105">The Path parameter now supports the module base path with the version folder.</span></span>

<span data-ttu-id="0a075-106">**Zainstaluj moduł przykłady:**</span><span class="sxs-lookup"><span data-stu-id="0a075-106">**Install-Module examples:**</span></span>
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