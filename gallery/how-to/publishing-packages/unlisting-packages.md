---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, programu powershell, polecenie cmdlet, galerii programu PowerShell
title: Usuwanie pakietów
ms.openlocfilehash: fb66fd23dae1d4640056a764c31426f61f56d910
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004096"
---
# <a name="unlisting-packages"></a>Unlisting pakietów

**Dlaczego jest usunięcie pakietu z galerii programu PowerShell, które nie są widoczne jako opcja?**

Galeria programu PowerShell nie obsługuje użytkowników trwale swoich pakietów.
Dzięki temu inne osoby do podjęcia zależności pakietów bez konieczności martwienia się o przerwy możliwe w przyszłości.
Na przykład jeśli moduł usług Pester zależy od modułu platformy Azure i platformy Azure zostanie on usunięty z galerii, wówczas użytkownik może już nie korzysta z modułu usług Pester.

Zamiast usuwania pakietu, jednak użytkownik może wyrejestrowanie go zamiast tego.

**Ile kosztuje, usuwanie, czy pakiet w galerii programu PowerShell?**

Usuwanie pakietów, takich jak moduł lub skryptu w galerii programu PowerShell spowoduje usunięcie go z karty pakietów. Ponadto nie będzie wykrywalny, korzystając z paska wyszukiwania nieznajdujące się na liście pakietów.
Jedynym sposobem, aby pobrać pakiet nieznajdujące się na liście jest określenie dokładnej nazwy i wersji pakietu.
W związku z tym usuwanie pakietu nie będę powodować inne moduły lub skrypty, które od niego zależne.

Wyrejestrowanie pakietu, można znaleźć na stronie szczegółów pakietu i wybierz pozycję "Usuń Module". Usuń zaznaczenie pola wyboru "Lista", a następnie kliknij przycisk Zapisz.

**Jak usunąć pakiet?**

Występują scenariusz, w których jest konieczne usunięcie pakietów, skontaktuj się z administratorami galerii programu PowerShell.
Prawidłowe usunięcie scenariusze są następujące:
- Problemy dotyczące praw autorskich.
- Pakiet zawiera potencjalnie niebezpieczną zawartość.
- Pakiet zawiera dane poufne.

Aby przesłać żądanie, usuń pakiet żądania do administratorów galerii programu PowerShell, odwiedź stronę szczegółów Twojego pakietu i wybierz pozycję Kontakt z pomocą techniczną.
