---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: Galeria, programu powershell, polecenie cmdlet, galerii programu PowerShell
title: Pakiety z zgodne wersje programu PowerShell lub systemu operacyjnego
ms.openlocfilehash: 8230866561d3021379a48cc2c83fb4104a4058c1
ms.sourcegitcommit: d396d0e4cfe3d279f399c17e7337380a31d373ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2018
ms.locfileid: "53747708"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a><span data-ttu-id="b8092-103">Pakiety z zgodne wersje programu PowerShell lub systemów operacyjnych</span><span class="sxs-lookup"><span data-stu-id="b8092-103">Packages with compatible PowerShell Editions or Operating Systems</span></span>

<span data-ttu-id="b8092-104">Począwszy od wersji 5.1 program PowerShell jest dostępny w różnych wersjach, które charakteryzują się różnymi zestawami funkcji i możliwości platformy.</span><span class="sxs-lookup"><span data-stu-id="b8092-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibilities.</span></span>

## <a name="searching-by-powershell-edition"></a><span data-ttu-id="b8092-105">Wyszukiwanie według wersji programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="b8092-105">Searching by PowerShell Edition</span></span> 
<span data-ttu-id="b8092-106">Dwie wersje programu Powershell są:</span><span class="sxs-lookup"><span data-stu-id="b8092-106">The two editions of Powershell are:</span></span>
- <span data-ttu-id="b8092-107">**Wersja Desktop:** Oparta na programie .NET Framework i zapewnia zgodność ze skryptami i modułami przeznaczonymi dla wersji programu PowerShell działających w pełnych wersjach systemu Windows, takich jak instalacja Server Core i Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="b8092-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="b8092-108">**Wersja Core:** Oparta na module .NET Core i zapewnia zgodność ze skryptami i modułami przeznaczonymi dla wersji programu PowerShell działających w ograniczonych wersjach systemu Windows, takich jak Nano Server i Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="b8092-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a><span data-ttu-id="b8092-109">Galeria programu PowerShell umożliwia filtrowanie pakietów zgodnych dla określonej wersji programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="b8092-109">PowerShell Gallery allows you to filter packages compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="b8092-110">Jeżeli pakiet zawiera niezgodny elementami Psedition określony, są one wyświetlane jako część "Wersje programu PowerShell" na stronie wyświetlania pakietu, a także w wynikach pakietów.</span><span class="sxs-lookup"><span data-stu-id="b8092-110">If a package has compatible PSEditions specified, they are listed as part of 'PowerShell Editions' in the package display page and also in packages results.</span></span>
<span data-ttu-id="b8092-111">Możesz również wyszukać zgodnych pakietów przy użyciu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b8092-111">You can also search for compatible packages using PowerShell.</span></span>

![Strona wyświetlania elementu z elementami Psedition](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a><span data-ttu-id="b8092-113">Wyszukaj pakiety w galerii interfejsu użytkownika, które działają w programie PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="b8092-113">Search for packages in the gallery UI that work on PowerShell Core</span></span>

<span data-ttu-id="b8092-114">Za pomocą tagów: "PSEdition_Desktop" i tagów: "PSEdition_Core" do filtrów pakietów w galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b8092-114">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the packages on PowerShell Gallery.</span></span>

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="b8092-115">Za pomocą tagów: "PSEdition_Core", aby wyszukać elementy zgodne z programu PowerShell Core Edition.</span><span class="sxs-lookup"><span data-stu-id="b8092-115">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![Wyniki wyszukiwania dla elementów zgodnych z psedition tabeli podstawowej](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="b8092-117">Za pomocą tagów: "PSEdition_Desktop", aby wyszukać elementy zgodne z programu PowerShell w wersji Desktop.</span><span class="sxs-lookup"><span data-stu-id="b8092-117">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![Wyniki wyszukiwania dla elementów, spełniając Desktop PSEdition](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a><span data-ttu-id="b8092-119">Wyszukaj pakiety, aby znaleźć zgodne wersje przy użyciu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="b8092-119">Search for packages to find compatible editions using PowerShell</span></span>
<span data-ttu-id="b8092-120">Można określić znaczniki, aby filtrować przy użyciu wersji programu PowerShell i systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="b8092-120">You can specify tags to filter for the PowerShell edition and OS.</span></span> <span data-ttu-id="b8092-121">Możesz użyć `Find-Package` polecenia cmdlet, określając `-Tag` parametru do określenia wersji (i systemu operacyjnego) przeznaczonych do pracy.</span><span class="sxs-lookup"><span data-stu-id="b8092-121">You use the `Find-Package` cmdlet specifying the `-Tag` parameter to specify the edition (and OS) you are targeting.</span></span>
<span data-ttu-id="b8092-122">Jak to:</span><span class="sxs-lookup"><span data-stu-id="b8092-122">Like this:</span></span>

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a><span data-ttu-id="b8092-123">Wyszukiwanie według systemu operacyjnego</span><span class="sxs-lookup"><span data-stu-id="b8092-123">Searching by Operating System</span></span> 

<span data-ttu-id="b8092-124">Ponieważ program PowerShell Core jest dostępna dla Windows, Linux i MacOS, pakietów w galerii, mogą być przeznaczone dla dowolnej kombinacji tych systemów operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="b8092-124">Since PowerShell Core is available for Windows, Linux, and MacOS, packages in the Gallery may be designed for any combination of these operating systems.</span></span> <span data-ttu-id="b8092-125">W galerii interfejsu użytkownika za pomocą następujących znaczników searchs wyszukiwać pakiety oznaczone przez system operacyjny:</span><span class="sxs-lookup"><span data-stu-id="b8092-125">In the gallery UI use the following searchs tags to find packages tagged by operating system:</span></span>

- <span data-ttu-id="b8092-126">Tagi: "Windows"</span><span class="sxs-lookup"><span data-stu-id="b8092-126">Tags: "Windows"</span></span>
- <span data-ttu-id="b8092-127">Tagi: "Linux"</span><span class="sxs-lookup"><span data-stu-id="b8092-127">Tags: "Linux"</span></span>
- <span data-ttu-id="b8092-128">Tagi: "System MacOS"</span><span class="sxs-lookup"><span data-stu-id="b8092-128">Tags: "MacOS"</span></span> 

<span data-ttu-id="b8092-129">Można określić te znaczniki `Find-Module` (i inne polecenia cmdlet w PowerShellGet module), podobnie do następującego:</span><span class="sxs-lookup"><span data-stu-id="b8092-129">You can specify these tags on `Find-Module` (and other cmdlets in the PowerShellGet module), like this:</span></span>

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a><span data-ttu-id="b8092-130">Wyszukiwanie wiele możliwości</span><span class="sxs-lookup"><span data-stu-id="b8092-130">Searching for Multiple Compatibilities</span></span>

<span data-ttu-id="b8092-131">Można wyszukać pakiet, który ma wiele możliwości przy użyciu składni:</span><span class="sxs-lookup"><span data-stu-id="b8092-131">You can look for a package that has multiple compatibilities by using the syntax:</span></span> 

<span data-ttu-id="b8092-132">Tagi: "Compatibility1" "Compatibility2"</span><span class="sxs-lookup"><span data-stu-id="b8092-132">Tags: "Compatibility1" "Compatibility2"</span></span> 

<span data-ttu-id="b8092-133">Na przykład jeśli szukasz pakietu przy użyciu programu PowerShell Core zgodności, który działa na maszynach Moje Windows i Linux, należy użyć tagów wyszukiwania:</span><span class="sxs-lookup"><span data-stu-id="b8092-133">For example, if you are looking for a package with PowerShell Core Compatibility that runs on both my Windows and Linux machines, use the search tags:</span></span>

<span data-ttu-id="b8092-134">Tagi: "PSEdition_Core" "Windows" "Linux"</span><span class="sxs-lookup"><span data-stu-id="b8092-134">Tags: "PSEdition_Core" "Windows" "Linux"</span></span> 

<span data-ttu-id="b8092-135">Aby przeprowadzić wyszukiwanie, przy użyciu programu PowerShell, można użyć `Find-Module` i inne polecenia cmdlet modułu PowerShellGet, podobnie do następującego:</span><span class="sxs-lookup"><span data-stu-id="b8092-135">To search using PowerShell, you can use the `Find-Module` (and the other cmdlets in the PowerShellGet module), like this:</span></span>

```powewrshell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a><span data-ttu-id="b8092-136">Szczegółowe informacje na temat tworzenia i znalezienie pakietów o niezgodne wersje programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="b8092-136">More details on authoring and finding the packages with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="b8092-137">Moduły z elementami PSEdition</span><span class="sxs-lookup"><span data-stu-id="b8092-137">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="b8092-138">Skrypty z elementami PSEdition</span><span class="sxs-lookup"><span data-stu-id="b8092-138">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)
