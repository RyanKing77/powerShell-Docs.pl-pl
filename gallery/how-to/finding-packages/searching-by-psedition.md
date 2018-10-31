---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, programu powershell, polecenie cmdlet, galerii programu PowerShell
title: Pakiety z niezgodne wersje programu PowerShell
ms.openlocfilehash: e16cfb0ee30e344c9399bec2985baafc5a252fd7
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004081"
---
# <a name="packages-with-compatible-powershell-editions"></a><span data-ttu-id="e5fa4-103">Pakiety z niezgodne wersje programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="e5fa4-103">Packages with compatible PowerShell Editions</span></span>

<span data-ttu-id="e5fa4-104">Od wersji 5.1 program PowerShell jest dostępny w różnych wersjach, które charakteryzują się różnymi zestawami funkcji i zgodnością z różnymi platformami.</span><span class="sxs-lookup"><span data-stu-id="e5fa4-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="e5fa4-105">**Wersja Desktop:** jest oparta na programie .NET Framework i zapewnia zgodność ze skryptami i modułami przeznaczonymi dla wersji programu PowerShell działających w pełnych wersjach systemu Windows, takich jak instalacja Podstawowe funkcje serwera i system Windows dla komputerów stacjonarnych.</span><span class="sxs-lookup"><span data-stu-id="e5fa4-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="e5fa4-106">**Wersja Core:** jest oparta na module .NET Core i zapewnia zgodność ze skryptami i modułami przeznaczonymi dla wersji programu PowerShell działających w ograniczonych wersjach systemu Windows, takich jak system Nano Server i Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="e5fa4-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-packages-compatible-for-specific-powershell-editions"></a><span data-ttu-id="e5fa4-107">Galeria programu PowerShell wyodrębnia obsługiwanych metadane z elementami Psedition i pozwala filtry pakietów zgodnych dla określonej wersji programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="e5fa4-107">PowerShell Gallery extracts supported PSEditions metadata and allows you to filters the packages compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="e5fa4-108">Jeżeli pakiet zawiera niezgodny elementami Psedition określony, zostaną one wyświetlone jako część "Wersje programu PowerShell" na stronie wyświetlania pakietu, a także w wynikach pakietów.</span><span class="sxs-lookup"><span data-stu-id="e5fa4-108">If a package has compatible PSEditions specified, they will be listed as part of 'PowerShell Editions' in the package display page and also in packages results.</span></span>

![Strona wyświetlania elementu z elementami Psedition](../../Images/manual_package_download.png)

## <a name="search-for-packages-in-the-gallery-ui-which-works-on-powershellcore"></a><span data-ttu-id="e5fa4-110">Wyszukaj pakiety w galerii interfejsu użytkownika, który działa na PowerShellCore</span><span class="sxs-lookup"><span data-stu-id="e5fa4-110">Search for packages in the gallery UI which works on PowerShellCore</span></span>

<span data-ttu-id="e5fa4-111">Za pomocą tagów: "PSEdition_Desktop" i tagów: "PSEdition_Core" do filtrów pakietów w galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e5fa4-111">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the packages on PowerShell Gallery.</span></span>

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="e5fa4-112">Za pomocą tagów: "PSEdition_Core", aby wyszukać elementy zgodne z programu PowerShell Core Edition.</span><span class="sxs-lookup"><span data-stu-id="e5fa4-112">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![Wyniki wyszukiwania dla elementów zgodnych z psedition tabeli podstawowej](../../Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="e5fa4-114">Za pomocą tagów: "PSEdition_Desktop", aby wyszukać elementy zgodne z programu PowerShell w wersji Desktop.</span><span class="sxs-lookup"><span data-stu-id="e5fa4-114">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![Wyniki wyszukiwania dla elementów, spełniając Desktop PSEdition](../../Images/SearchResultsWithPSEdition-Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a><span data-ttu-id="e5fa4-116">Szczegółowe informacje na temat tworzenia i znalezienie pakietów o niezgodne wersje programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="e5fa4-116">More details on authoring and finding the packages with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="e5fa4-117">Moduły z elementami PSEdition</span><span class="sxs-lookup"><span data-stu-id="e5fa4-117">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="e5fa4-118">Skrypty z elementami PSEdition</span><span class="sxs-lookup"><span data-stu-id="e5fa4-118">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)
