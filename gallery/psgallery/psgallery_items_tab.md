---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeria, programu powershell, polecenia cmdlet, psgallery
title: psgallery_items_tab
ms.openlocfilehash: 5058253678a4f996b080e43820fee06b35b681f4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="items-tab"></a>Karta elementy

[Karta elementy](https://www.powershellgallery.com/items) Wyświetla wszystkie dostępne elementy w galerii programu PowerShell.

Istnieje kilka sposobów, aby filtrowanie, sortowanie i wyszukiwanie elementów.
Aby uzyskać szczegółowe informacje dotyczące określonego elementu, kliknij element.

## <a name="filter-by"></a>Filtruj według

Na liście rozwijanej w obszarze "Filtruj wg" umożliwia użytkownikom filtrować wyniki według:
* Uwzględnij wersję wstępną
* Tylko stabilne

Uzyskać informacji o "Wydanie wstępne" i "Stabilna", zobacz [wstępnej wersji dodane PowerShellGet i galerii programu PowerShell](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) w blogu zespołu programu PowerShell.

W obszarze listy rozwijanej pola wyboru Zezwalaj użytkownikom na filtrować wyniki według:
* Typy elementów
  - Moduł
  - Skrypt
* Kategorie
  - Polecenie cmdlet
  - Zasób DSC
  - Funkcja
  - Możliwość roli
  - Przepływ pracy

Aby wyświetlić tylko moduły w galerii programu PowerShell, Sprawdź moduł w typów elementów.
Podobnie Aby wyświetlić tylko skrypty w galerii programu PowerShell, należy sprawdzić skryptu w typów elementów.

> [!NOTE]
> Filtry są włącznie.
> Przykład: Element zawierająca poleceń cmdlet i funkcje pojawi się zaznaczenie albo polecenia Cmdlet funkcji (i/lub).
> Jeśli nie wybrano żadnego z tych celów, element nie pojawi się.
> Podobnie w przypadku wszystkich kategorii będą wyświetlane tylko elementy zawierające jeden z tych kategorii.
> **Elementy, które nie należą do żadnej z tych kategorii nie będą wyświetlane.**

## <a name="sort-by"></a>Sortuj według

Sortuj według listy rozwijanej umożliwia użytkownikom Sortuj wyniki według:
* Popularne - popularne jest określany przez pobieranie liczby
* A-Z — alfabetycznie według nazw
* Ostatnie — elementy są wyświetlane w kolejności daty opublikowania

## <a name="search-box"></a>Pole wyszukiwania

Pole wyszukiwania umożliwia użytkownikom wyszukiwanie elementy słów kluczowych.
Aby uzyskać więcej informacji, zobacz [składni wyszukiwania galerii](psgallery_search_syntax.md).