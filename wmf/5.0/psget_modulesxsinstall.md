---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
ms.openlocfilehash: f68847ba8292a277e464025c1baa17a5aa2752f5
ms.sourcegitcommit: 4ab9a86e47b6effe8fe22ebeb81e8fadff41d31c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2017
---
# <a name="side-by-side-version-support-on-powershell-50-or-newer"></a><span data-ttu-id="79022-102">Obsługa wersji Side-by-Side programu PowerShell w wersji 5.0 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="79022-102">Side-by-Side Version Support on PowerShell 5.0 or newer</span></span>

<span data-ttu-id="79022-103">Teraz jest obsługa wersji modułu side-by-side (SxS) w Module instalacji aktualizacji modułu i poleceń cmdlet Publish-Module uruchamiających w programie Windows PowerShell 5.0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="79022-103">There is now side-by-side (SxS) module version support in Install-Module, Update-Module, and Publish-Module cmdlets that run in Windows PowerShell 5.0 or newer.</span></span>
<span data-ttu-id="79022-104">Ponadto dodano parametru - RequiredVersion do polecenia cmdlet Publish-Module do określania wersji do opublikowania.</span><span class="sxs-lookup"><span data-stu-id="79022-104">Also, we have added a -RequiredVersion parameter to the Publish-Module cmdlet to specify the version to be published.</span></span> <span data-ttu-id="79022-105">Parametr Path obsługuje teraz ścieżki bazowej modułu z folderem wersji.</span><span class="sxs-lookup"><span data-stu-id="79022-105">The Path parameter now supports the module base path with the version folder.</span></span>

<span data-ttu-id="79022-106">**Zainstaluj moduł przykłady:**</span><span class="sxs-lookup"><span data-stu-id="79022-106">**Install-Module examples:**</span></span>
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

