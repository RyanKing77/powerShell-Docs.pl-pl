---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
ms.openlocfilehash: 2c7e718bc518b332cb4303ef73b1bf5c924ca471
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a><span data-ttu-id="8e050-102">Odnajdywanie modułu programu PowerShell, zainstalować i spisu z PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="8e050-102">PowerShell Module Discovery, Install and Inventory with PowerShellGet</span></span>
 
<span data-ttu-id="8e050-103">PowerShellGet znajduje się w tej wersji platformy WMF:</span><span class="sxs-lookup"><span data-stu-id="8e050-103">PowerShellGet is included in this release of WMF:</span></span>
-   <span data-ttu-id="8e050-104">Znajdź moduł można filtrować według metadanych z parametrem - Tag</span><span class="sxs-lookup"><span data-stu-id="8e050-104">Find-Module can filter on module metadata with the -Tag parameter</span></span>
-   <span data-ttu-id="8e050-105">Znajdź moduł można filtrować według języka wyszukiwania specyficznego dla repozytorium z parametrem - filtru</span><span class="sxs-lookup"><span data-stu-id="8e050-105">Find-Module can filter on repository-specific search language with the -Filter parameter</span></span>
-   <span data-ttu-id="8e050-106">Można znaleźć modułu filtr oparty na module zawartości — polecenie - DscResource i - zawiera parametry</span><span class="sxs-lookup"><span data-stu-id="8e050-106">Find-Module can filter based on module contents with the -Command, -DscResource, and -Includes parameters</span></span>
-   <span data-ttu-id="8e050-107">Znajdź DscResource umożliwia odnajdywania poszczególnych zasobów DSC w repozytoria</span><span class="sxs-lookup"><span data-stu-id="8e050-107">Find-DscResource allows discovery of individual DSC resources in repositories</span></span>
-   <span data-ttu-id="8e050-108">Obsługa instalowania z i publikowania dla udziałów plików z NuGet</span><span class="sxs-lookup"><span data-stu-id="8e050-108">Support for installing from and publishing to file shares with NuGet</span></span>

## <a name="example-commands"></a><span data-ttu-id="8e050-109">Przykładowe polecenia</span><span class="sxs-lookup"><span data-stu-id="8e050-109">Example commands</span></span>
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

## <a name="new-features-in-powershellget"></a><span data-ttu-id="8e050-110">Nowe funkcje w PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="8e050-110">New features in PowerShellGet</span></span>
-   <span data-ttu-id="8e050-111">Obsługa wersji Side-by-side, w programie Windows PowerShell 5.0 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="8e050-111">Side-by-side version support on Windows PowerShell 5.0 or newer</span></span>
-   <span data-ttu-id="8e050-112">Obsługa instalacji modułu zależności</span><span class="sxs-lookup"><span data-stu-id="8e050-112">Module dependency installation support</span></span>
-   <span data-ttu-id="8e050-113">Trzy nowe polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="8e050-113">Three new cmdlets</span></span>
    -   <span data-ttu-id="8e050-114">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="8e050-114">Get-InstalledModule</span></span>
    -   <span data-ttu-id="8e050-115">Odinstaluj moduł</span><span class="sxs-lookup"><span data-stu-id="8e050-115">Uninstall-Module</span></span>
    -   <span data-ttu-id="8e050-116">Moduł zapisywania</span><span class="sxs-lookup"><span data-stu-id="8e050-116">Save-Module</span></span>
    
