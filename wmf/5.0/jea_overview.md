---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 0bc085588190f134c4a687c952509aa256b5f840
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085205"
---
# <a name="just-enough-administration-jea"></a>Just Enough Administration (JEA)
Just Enough Administration to nowa funkcja programu WMF 5.0, która umożliwia administracji opartej na rolach za pomocą komunikacji zdalnej programu PowerShell.  Rozszerza istniejącą infrastrukturę ograniczone punktu końcowego, umożliwiając użytkowników niebędących administratorami uruchamiać odpowiednie polecenia, skrypty i pliki wykonywalne jako administrator.  Dzięki temu można zmniejszyć liczbę administratorów pełnego w danym środowisku i zwiększenia poziomu bezpieczeństwa.  JEA działa w przypadku wszystkie elementy, którymi można zarządzać za pomocą programu PowerShell; Jeśli zarządzasz za pomocą programu PowerShell, usługi JEA pomóc więc bezpieczniejsze.  Aby uzyskać szczegółowy widok Just Enough Administration, zapoznaj się [środowisko przewodnik](http://aka.ms/JEA).

W przeciwieństwie do starego ograniczone punktów końcowych JEA jest zaawansowane i łatwa do skonfigurowania.  Możliwości użytkownika w JEA mogą być precyzyjne kontrolowane, dół ograniczenie zestawów parametrów i wartości, które mogą być dostarczane do określonego polecenia. Akcje użytkownika są uruchamiane w kontekście konta wirtualnego jednorazowego, które ma uprawnienia do wykonywania akcji administratora.  Polecenia wywołany przez użytkownika mogą być rejestrowane dla inspekcji zabezpieczeń.

JEA działa, umożliwiając tworzenie specjalnie skonfigurowanym ograniczone punktów końcowych.  Te punkty końcowe mają kilka istotne cechy:

1. Użytkowników łączących się do nich "Uruchom jako" uprzywilejowanego konta wirtualnego, który istnieje tylko na czas tej sesji zdalnej.  Domyślnie to wirtualne konto jest członkiem wbudowanej grupy Administratorzy, Administratorzy domeny, na kontrolerach domeny (Uwaga: te uprawnienia są konfigurowalne). Łączenie się jako jeden z użytkowników, a następnie uruchamiając jako użytkownik inny, uprzywilejowanego, możesz zezwolić użytkownikom bez uprawnień wykonywanie określonych zadań administracyjnych bez nadawania im praw administracyjnych na systemy.
2. Punkt końcowy został zablokowany.  Oznacza to, programu PowerShell działa w trybie bez języka.  Tylko polecenia specyficzne, skrypty i pliki wykonywalne są widoczne dla użytkownika.
3. Różni użytkownicy łączenie są prezentowane z innym zestawem funkcji na podstawie przynależności do grupy.  Możesz podać różne role w różne możliwości, w tym samym punkcie końcowym.
