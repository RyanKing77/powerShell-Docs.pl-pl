---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 82b8046d5cbb47300f090ce2ffbf3c279ed19458
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a><span data-ttu-id="1a6fe-102">Odnajdywanie modułu programu PowerShell, zainstalować i spisu z PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="1a6fe-102">PowerShell Module Discovery, Install and Inventory with PowerShellGet</span></span>

<span data-ttu-id="1a6fe-103">PowerShellGet znajduje się w tej wersji platformy WMF:</span><span class="sxs-lookup"><span data-stu-id="1a6fe-103">PowerShellGet is included in this release of WMF:</span></span>
-   <span data-ttu-id="1a6fe-104">Znajdź moduł można filtrować według metadanych z parametrem - Tag</span><span class="sxs-lookup"><span data-stu-id="1a6fe-104">Find-Module can filter on module metadata with the -Tag parameter</span></span>
-   <span data-ttu-id="1a6fe-105">Znajdź moduł można filtrować według języka wyszukiwania specyficznego dla repozytorium z parametrem - filtru</span><span class="sxs-lookup"><span data-stu-id="1a6fe-105">Find-Module can filter on repository-specific search language with the -Filter parameter</span></span>
-   <span data-ttu-id="1a6fe-106">Można znaleźć modułu filtr oparty na module zawartości — polecenie - DscResource i - zawiera parametry</span><span class="sxs-lookup"><span data-stu-id="1a6fe-106">Find-Module can filter based on module contents with the -Command, -DscResource, and -Includes parameters</span></span>
-   <span data-ttu-id="1a6fe-107">Znajdź DscResource umożliwia odnajdywania poszczególnych zasobów DSC w repozytoria</span><span class="sxs-lookup"><span data-stu-id="1a6fe-107">Find-DscResource allows discovery of individual DSC resources in repositories</span></span>
-   <span data-ttu-id="1a6fe-108">Obsługa instalowania z i publikowania dla udziałów plików z NuGet</span><span class="sxs-lookup"><span data-stu-id="1a6fe-108">Support for installing from and publishing to file shares with NuGet</span></span>

## <a name="example-commands"></a><span data-ttu-id="1a6fe-109">Przykładowe polecenia</span><span class="sxs-lookup"><span data-stu-id="1a6fe-109">Example commands</span></span>
```powershell
\# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

\# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

\#Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

\# Find all modules with Dsc resources
Find-Module -Includes DscResource

\# Find all modules with cmdlets
Find-Module -Includes Cmdlet

\# Find all modules with functions
Find-Module -Includes Function

\# Find all DSC resources
Find-DscResource

\# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking

\# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

\# Find modules using -Filter parameter
\# Specified filter value is searched in Name and Description properties
Find-Module -Filter Cookbook -Repository PSGallery
Find-Module -Filter RBAC -Repository PSGallery
```

## <a name="new-features-in-powershellget"></a><span data-ttu-id="1a6fe-110">Nowe funkcje w PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="1a6fe-110">New features in PowerShellGet</span></span>
-   <span data-ttu-id="1a6fe-111">Obsługa wersji Side-by-side, w programie Windows PowerShell 5.0 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="1a6fe-111">Side-by-side version support on Windows PowerShell 5.0 or newer</span></span>
-   <span data-ttu-id="1a6fe-112">Obsługa instalacji modułu zależności</span><span class="sxs-lookup"><span data-stu-id="1a6fe-112">Module dependency installation support</span></span>
-   <span data-ttu-id="1a6fe-113">Trzy nowe polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="1a6fe-113">Three new cmdlets</span></span>
    -   <span data-ttu-id="1a6fe-114">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="1a6fe-114">Get-InstalledModule</span></span>
    -   <span data-ttu-id="1a6fe-115">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="1a6fe-115">Uninstall-Module</span></span>
    -   <span data-ttu-id="1a6fe-116">Save-Module</span><span class="sxs-lookup"><span data-stu-id="1a6fe-116">Save-Module</span></span>