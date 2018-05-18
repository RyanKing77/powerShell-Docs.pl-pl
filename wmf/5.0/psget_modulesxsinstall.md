---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: d4168640f67cb1dd44e91d1867e87fd7a6b7f549
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="side-by-side-version-support-on-powershell-50-or-newer"></a><span data-ttu-id="0b4e6-102">Obsługa wersji Side-by-Side programu PowerShell w wersji 5.0 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="0b4e6-102">Side-by-Side Version Support on PowerShell 5.0 or newer</span></span>

<span data-ttu-id="0b4e6-103">Teraz jest obsługa wersji modułu side-by-side (SxS) w Module instalacji aktualizacji modułu i poleceń cmdlet Publish-Module uruchamiających w programie Windows PowerShell 5.0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="0b4e6-103">There is now side-by-side (SxS) module version support in Install-Module, Update-Module, and Publish-Module cmdlets that run in Windows PowerShell 5.0 or newer.</span></span>
<span data-ttu-id="0b4e6-104">Ponadto dodano parametru - RequiredVersion do polecenia cmdlet Publish-Module do określania wersji do opublikowania.</span><span class="sxs-lookup"><span data-stu-id="0b4e6-104">Also, we have added a -RequiredVersion parameter to the Publish-Module cmdlet to specify the version to be published.</span></span> <span data-ttu-id="0b4e6-105">Parametr Path obsługuje teraz ścieżki bazowej modułu z folderem wersji.</span><span class="sxs-lookup"><span data-stu-id="0b4e6-105">The Path parameter now supports the module base path with the version folder.</span></span>

<span data-ttu-id="0b4e6-106">**Zainstaluj moduł przykłady:**</span><span class="sxs-lookup"><span data-stu-id="0b4e6-106">**Install-Module examples:**</span></span>
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
