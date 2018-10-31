---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, programu powershell, polecenie cmdlet, galerii programu PowerShell
title: Filtrowanie wyników wyszukiwania
ms.openlocfilehash: 13270a310613a974e1588a9f56d443a936cfebb8
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004121"
---
# <a name="filtering-search-results"></a>Filtrowanie wyników wyszukiwania

[Karcie pakiety](https://www.powershellgallery.com/packages) Wyświetla wszystkie dostępne pakiety w galerii programu PowerShell.

Istnieje kilka sposobów, aby filtrować, sortować i wyszukiwać pakiety.
Aby wyświetlić więcej szczegółów na temat danego pakietu, kliknij pakiet.

## <a name="filter-by"></a>Filtruj według

Z listy rozwijanej w obszarze "Filtruj wg" umożliwia użytkownikom przefiltrować wyniki według:
- Uwzględnij wersję wstępną
- Tylko wersja stabilna

Aby uzyskać informacji na temat "Wersja wstępna" i "Stałe", zobacz [wersję wstępną Versioning dodane do modułu PowerShellGet oraz spełnione galerii programu PowerShell](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) na blogu zespołu programu PowerShell.

Pola wyboru w obszarze listy rozwijanej Zezwalaj użytkownikom na przefiltrować wyniki według:
- Typy pakietów
  - Moduł
  - Skrypt
- Kategorie
  - Polecenie cmdlet
  - Zasób DSC
  - Funkcja
  - Możliwości roli
  - Przepływ pracy

Aby zapoznać się tylko moduły w galerii programu PowerShell, zobacz moduł w typów pakietów.
Podobnie Aby wyświetlić tylko skrypty w galerii programu PowerShell, Sprawdź skrypt w typów pakietów.

> [!NOTE]
> Filtry są włącznie.
> Przykład: Pakiet zawierający wersję poleceń cmdlet i funkcje będą wyświetlane, jeśli albo polecenia Cmdlet funkcji (i/lub) są sprawdzane.
> Jeśli nie zaznaczono żadnego z tych celów, nie pojawi się pakiet.
> Podobnie jeśli wszystkie kategorie są zaznaczone, tylko pakiety zawierające jeden z tych kategorii będą wyświetlane.
> **Pakiety, które nie należą do żadnej z tych kategorii nie będą wyświetlane.**

## <a name="sort-by"></a>Sortuj według

Sortuj według listy rozwijanej umożliwia użytkownikom Sortuj wyniki według:
- Popularność - popularność jest określana przez pobieranie liczby
- A-Z - alfabetycznie według nazwy pakietu
- Ostatnie - pakiety są widoczne w kolejności daty opublikowania

## <a name="search-box"></a>Pole wyszukiwania

Pole wyszukiwania umożliwia użytkownikom wyszukiwanie pakietów na słowa kluczowe.
Aby uzyskać więcej informacji, zobacz [składnia wyszukiwania w galerii](search-syntax.md).
