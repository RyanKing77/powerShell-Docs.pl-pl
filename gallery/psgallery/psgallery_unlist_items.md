---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeria, programu powershell, polecenia cmdlet, psgallery
title: psgallery_unlist_items
ms.openlocfilehash: af48f2ca889dcc101d466e40f2ecbe0cdf62c066
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="unlisting-items"></a>Usuwanie elementów z listy

**Dlaczego jest usunięcie elementu z galerii programu PowerShell, które nie są widoczne jako opcja?**

Galerii programu PowerShell nie obsługuje użytkowników trwałe usunięcie ich elementów.
Dzięki temu inne osoby do podjęcia zależności elementów bez obaw o możliwości podziałów w przyszłości.
Na przykład jeśli moduł Pester zależy od modułu platformy Azure i moduł Azure zostanie usunięty z galerii, a następnie użytkownik może już używa modułu Pester.

Zamiast usuwania elementu, jednak użytkownik może unlist go zamiast tego.

**Jaki jest unlisting elementu w galerii programu PowerShell zrobić?**

Unlisting elementów, takich jak moduł lub skryptu w galerii programu PowerShell spowoduje usunięcie jej z karty elementów. Ponadto nie będzie wykrywalny, przy użyciu pasek wyszukiwania nieznajdujące się na liście elementów.
Jedynym sposobem na pobranie elementu nieznajdujące się na liście jest określenie dokładnej nazwy i wersji elementu.
W związku z tym unlisting elementu nie będę powodować utraty inne moduły lub skrypty, które od niego zależne.

Aby unlist tego elementu, można znaleźć na stronie Szczegóły elementu, a następnie usuń element. Usuń zaznaczenie pola wyboru "Lista", a następnie kliknij przycisk Zapisz.

**Jak usunąć element?**

Jeśli wystąpią scenariusza, gdy jest konieczne usunięcie elementu skontaktuj się z administratorami w galerii programu PowerShell.
Usuwanie prawidłowe scenariusze są następujące:
- Problemy dotyczące praw autorskich.
- Element zawiera potencjalnie niebezpieczną zawartość.
- Element zawiera poufne dane.

Aby przesłać, Usuń element żądanie administratorom galerii programu PowerShell, odwiedź stronę szczegółów tego elementu, a następnie wybierz się z pomocą techniczną.