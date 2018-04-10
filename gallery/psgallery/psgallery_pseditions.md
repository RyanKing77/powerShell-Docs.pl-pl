---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeria, programu powershell, polecenia cmdlet, psgallery
title: psgallery_pseditions
ms.openlocfilehash: 0b30c1da53832a6b74be7aa14ed9331b1e9fe643
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="items-with-compatible-powershell-editions"></a>Elementy z niezgodne wersje programu PowerShell
Od wersji 5.1 program PowerShell jest dostępny w różnych wersjach, które charakteryzują się różnymi zestawami funkcji i zgodnością z różnymi platformami.

- **Wersja Desktop:** jest oparta na programie .NET Framework i zapewnia zgodność ze skryptami i modułami przeznaczonymi dla wersji programu PowerShell działających w pełnych wersjach systemu Windows, takich jak instalacja Podstawowe funkcje serwera i system Windows dla komputerów stacjonarnych.
- **Wersja Core:** jest oparta na module .NET Core i zapewnia zgodność ze skryptami i modułami przeznaczonymi dla wersji programu PowerShell działających w ograniczonych wersjach systemu Windows, takich jak system Nano Server i Windows IoT.

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-items-compatible-for-specific-powershell-editions"></a>Galerii programu PowerShell umożliwia wyodrębnianie metadanych PSEditions obsługiwane i pozwala filtrami elementy zgodny dla określonej wersji programu PowerShell

Jeśli element ma niezgodny PSEditions określony, zostaną wyświetlone jako część "Wersje programu PowerShell" na stronie wyświetlania elementu, a także w wynikach elementów.
![Strona wyświetlania elementu z PSEditions](Images/ItemDisplayPageWithPSEditions.PNG)

## <a name="search-for-items-in-the-gallery-ui-which-works-on-powershellcore"></a>Wyszukiwanie elementów w galerii interfejsu użytkownika, który działa na PowerShellCore
Używaj tagów: "PSEdition_Desktop" i tagów: "PSEdition_Core" filtrami elementy galerii programu PowerShell.

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>Używaj tagów: "PSEdition_Core", aby wyszukać elementy zgodne z programu PowerShell w wersji podstawowej.
![Elementy zgodne z Core PSEdition wyniki wyszukiwania](Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Używaj tagów: "PSEdition_Desktop", aby wyszukać elementy zgodne z wersji pulpitu programu PowerShell.
![Wyniki wyszukiwania dla elementów zgodne z PSEdition pulpitu](Images/SearchResultsWithPSEdition_Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-items-with-compatible-powershell-editions"></a>Więcej informacji na temat tworzenia i znajdowanie elementów z niezgodne wersje programu PowerShell
### <a name="modules-with-pseditionspsgetmodulemodulewithpseditionsupportmd"></a>[Moduły z elementami PSEdition](../psget/module/modulewithpseditionsupport.md)
### <a name="scripts-with-pseditionspsgetscriptscriptwithpseditionsupportmd"></a>[Skrypty z elementami PSEdition](../psget/script/scriptwithpseditionsupport.md)