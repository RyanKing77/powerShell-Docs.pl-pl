---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeria, programu powershell, polecenia cmdlet, psgallery
title: Filtrowanie wyników wyszukiwania
ms.openlocfilehash: 5a7ea8207619318efd8195ee3d1c8f8ab51209da
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="filtering-search-results"></a><span data-ttu-id="d459e-103">Filtrowanie wyników wyszukiwania</span><span class="sxs-lookup"><span data-stu-id="d459e-103">Filtering search results</span></span>

<span data-ttu-id="d459e-104">[Karta elementy](https://www.powershellgallery.com/items) Wyświetla wszystkie dostępne elementy w galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d459e-104">The [Items tab](https://www.powershellgallery.com/items) displays all available items in the PowerShell Gallery.</span></span>

<span data-ttu-id="d459e-105">Istnieje kilka sposobów, aby filtrowanie, sortowanie i wyszukiwanie elementów.</span><span class="sxs-lookup"><span data-stu-id="d459e-105">There are several ways to filter, sort, and search the items.</span></span>
<span data-ttu-id="d459e-106">Aby uzyskać szczegółowe informacje dotyczące określonego elementu, kliknij element.</span><span class="sxs-lookup"><span data-stu-id="d459e-106">To see more details about a particular item, click the item.</span></span>

## <a name="filter-by"></a><span data-ttu-id="d459e-107">Filtruj według</span><span class="sxs-lookup"><span data-stu-id="d459e-107">Filter By</span></span>

<span data-ttu-id="d459e-108">Na liście rozwijanej w obszarze "Filtruj wg" umożliwia użytkownikom filtrować wyniki według:</span><span class="sxs-lookup"><span data-stu-id="d459e-108">The drop-down under "Filter By" allows users to filter the results by:</span></span>
- <span data-ttu-id="d459e-109">Uwzględnij wersję wstępną</span><span class="sxs-lookup"><span data-stu-id="d459e-109">Include Prerelease</span></span>
- <span data-ttu-id="d459e-110">Tylko stabilne</span><span class="sxs-lookup"><span data-stu-id="d459e-110">Stable Only</span></span>

<span data-ttu-id="d459e-111">Uzyskać informacji o "Wydanie wstępne" i "Stabilna", zobacz [wstępnej wersji dodane PowerShellGet i galerii programu PowerShell](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) w blogu zespołu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d459e-111">For information about "Prerelease" and "Stable", see [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) in the PowerShell Team Blog.</span></span>

<span data-ttu-id="d459e-112">W obszarze listy rozwijanej pola wyboru Zezwalaj użytkownikom na filtrować wyniki według:</span><span class="sxs-lookup"><span data-stu-id="d459e-112">The checkboxes under the drop-down allow users to filter the results by:</span></span>
- <span data-ttu-id="d459e-113">Typy elementów</span><span class="sxs-lookup"><span data-stu-id="d459e-113">Item Types</span></span>
  - <span data-ttu-id="d459e-114">Moduł</span><span class="sxs-lookup"><span data-stu-id="d459e-114">Module</span></span>
  - <span data-ttu-id="d459e-115">Skrypt</span><span class="sxs-lookup"><span data-stu-id="d459e-115">Script</span></span>
- <span data-ttu-id="d459e-116">Kategorie</span><span class="sxs-lookup"><span data-stu-id="d459e-116">Categories</span></span>
  - <span data-ttu-id="d459e-117">Polecenie cmdlet</span><span class="sxs-lookup"><span data-stu-id="d459e-117">Cmdlet</span></span>
  - <span data-ttu-id="d459e-118">Zasób DSC</span><span class="sxs-lookup"><span data-stu-id="d459e-118">DSC Resource</span></span>
  - <span data-ttu-id="d459e-119">Funkcja</span><span class="sxs-lookup"><span data-stu-id="d459e-119">Function</span></span>
  - <span data-ttu-id="d459e-120">Możliwość roli</span><span class="sxs-lookup"><span data-stu-id="d459e-120">Role Capability</span></span>
  - <span data-ttu-id="d459e-121">Przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="d459e-121">Workflow</span></span>

<span data-ttu-id="d459e-122">Aby wyświetlić tylko moduły w galerii programu PowerShell, Sprawdź moduł w typów elementów.</span><span class="sxs-lookup"><span data-stu-id="d459e-122">To see only modules in the PowerShell Gallery, check Module in the Item Types.</span></span>
<span data-ttu-id="d459e-123">Podobnie Aby wyświetlić tylko skrypty w galerii programu PowerShell, należy sprawdzić skryptu w typów elementów.</span><span class="sxs-lookup"><span data-stu-id="d459e-123">Similarly, to see only scripts in the PowerShell Gallery, check Script in the Item Types.</span></span>

> [!NOTE]
> <span data-ttu-id="d459e-124">Filtry są włącznie.</span><span class="sxs-lookup"><span data-stu-id="d459e-124">Filters are inclusive.</span></span>
> <span data-ttu-id="d459e-125">Przykład: Element zawierająca poleceń cmdlet i funkcje pojawi się zaznaczenie albo polecenia Cmdlet funkcji (i/lub).</span><span class="sxs-lookup"><span data-stu-id="d459e-125">Example: An item containing both cmdlets and functions will appear if either Cmdlet or Function (or both) are checked.</span></span>
> <span data-ttu-id="d459e-126">Jeśli nie wybrano żadnego z tych celów, element nie pojawi się.</span><span class="sxs-lookup"><span data-stu-id="d459e-126">If neither are selected, the item will not appear.</span></span>
> <span data-ttu-id="d459e-127">Podobnie w przypadku wszystkich kategorii będą wyświetlane tylko elementy zawierające jeden z tych kategorii.</span><span class="sxs-lookup"><span data-stu-id="d459e-127">Similarly, if all categories are selected, only items containing one of those categories will appear.</span></span>
> <span data-ttu-id="d459e-128">**Elementy, które nie należą do żadnej z tych kategorii nie będą wyświetlane.**</span><span class="sxs-lookup"><span data-stu-id="d459e-128">**Items that do not belong to any of those categories will not appear.**</span></span>

## <a name="sort-by"></a><span data-ttu-id="d459e-129">Sortuj według</span><span class="sxs-lookup"><span data-stu-id="d459e-129">Sort By</span></span>

<span data-ttu-id="d459e-130">Sortuj według listy rozwijanej umożliwia użytkownikom Sortuj wyniki według:</span><span class="sxs-lookup"><span data-stu-id="d459e-130">The Sort By drop-down allows users to sort the results by:</span></span>
- <span data-ttu-id="d459e-131">Popularne - popularne jest określany przez pobieranie liczby</span><span class="sxs-lookup"><span data-stu-id="d459e-131">Popularity - Popularity is determined by Download Count</span></span>
- <span data-ttu-id="d459e-132">A-Z — alfabetycznie według nazw</span><span class="sxs-lookup"><span data-stu-id="d459e-132">A-Z - Alphabetically by item name</span></span>
- <span data-ttu-id="d459e-133">Ostatnie — elementy są wyświetlane w kolejności daty opublikowania</span><span class="sxs-lookup"><span data-stu-id="d459e-133">Recent - Items appear in order of publish date</span></span>

## <a name="search-box"></a><span data-ttu-id="d459e-134">Pole wyszukiwania</span><span class="sxs-lookup"><span data-stu-id="d459e-134">Search Box</span></span>

<span data-ttu-id="d459e-135">Pole wyszukiwania umożliwia użytkownikom wyszukiwanie elementy słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="d459e-135">The Search Box allows users to search the items on keywords.</span></span>
<span data-ttu-id="d459e-136">Aby uzyskać więcej informacji, zobacz [składni wyszukiwania galerii](search-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="d459e-136">For more information, see [Gallery Search Syntax](search-syntax.md).</span></span>