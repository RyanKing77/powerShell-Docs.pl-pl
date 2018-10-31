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
# <a name="packages-with-compatible-powershell-editions"></a>Pakiety z niezgodne wersje programu PowerShell

Od wersji 5.1 program PowerShell jest dostępny w różnych wersjach, które charakteryzują się różnymi zestawami funkcji i zgodnością z różnymi platformami.

- **Wersja Desktop:** jest oparta na programie .NET Framework i zapewnia zgodność ze skryptami i modułami przeznaczonymi dla wersji programu PowerShell działających w pełnych wersjach systemu Windows, takich jak instalacja Podstawowe funkcje serwera i system Windows dla komputerów stacjonarnych.
- **Wersja Core:** jest oparta na module .NET Core i zapewnia zgodność ze skryptami i modułami przeznaczonymi dla wersji programu PowerShell działających w ograniczonych wersjach systemu Windows, takich jak system Nano Server i Windows IoT.

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-packages-compatible-for-specific-powershell-editions"></a>Galeria programu PowerShell wyodrębnia obsługiwanych metadane z elementami Psedition i pozwala filtry pakietów zgodnych dla określonej wersji programu PowerShell

Jeżeli pakiet zawiera niezgodny elementami Psedition określony, zostaną one wyświetlone jako część "Wersje programu PowerShell" na stronie wyświetlania pakietu, a także w wynikach pakietów.

![Strona wyświetlania elementu z elementami Psedition](../../Images/manual_package_download.png)

## <a name="search-for-packages-in-the-gallery-ui-which-works-on-powershellcore"></a>Wyszukaj pakiety w galerii interfejsu użytkownika, który działa na PowerShellCore

Za pomocą tagów: "PSEdition_Desktop" i tagów: "PSEdition_Core" do filtrów pakietów w galerii programu PowerShell.

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>Za pomocą tagów: "PSEdition_Core", aby wyszukać elementy zgodne z programu PowerShell Core Edition.

![Wyniki wyszukiwania dla elementów zgodnych z psedition tabeli podstawowej](../../Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Za pomocą tagów: "PSEdition_Desktop", aby wyszukać elementy zgodne z programu PowerShell w wersji Desktop.

![Wyniki wyszukiwania dla elementów, spełniając Desktop PSEdition](../../Images/SearchResultsWithPSEdition-Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a>Szczegółowe informacje na temat tworzenia i znalezienie pakietów o niezgodne wersje programu PowerShell

- [Moduły z elementami PSEdition](../../concepts/module-psedition-support.md)
- [Skrypty z elementami PSEdition](../../concepts/script-psedition-support.md)
