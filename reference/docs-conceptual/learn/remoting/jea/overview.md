---
ms.date: 07/10/2019
keywords: jea, PowerShell, zabezpieczenia
title: Przegląd wystarczającej administracji
ms.openlocfilehash: 4b74e5be9558810748a8844a325c8213e1b3ebc9
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017860"
---
# <a name="just-enough-administration"></a>Narzędzia Just Enough Administration

Wystarczy tylko Administracja (JEA) to technologia zabezpieczeń, która umożliwia administrację delegowaną dla wszystkich elementów zarządzanych przez program PowerShell. Za pomocą JEA można:

- **Zmniejszenie liczby administratorów na maszynach** przy użyciu kont wirtualnych lub kont usług zarządzanych przez grupę w celu wykonywania uprzywilejowanych akcji w imieniu zwykłych użytkowników.
- Ograniczanie możliwości, które **Użytkownicy mogą wykonywać** , określając, które polecenia cmdlet, funkcje i polecenia zewnętrzne, które mogą być uruchamiane.
- **Lepiej zrozumieć, co robią Użytkownicy** przy użyciu transkrypcji i dzienników, które pokazują, które polecenia użytkownik wykonał podczas sesji.

**Dlaczego JEA ważne?**

Konta o wysokim poziomie uprawnień używane do administrowania serwerami stanowią poważne zagrożenie bezpieczeństwa. Jeśli osoba atakująca naruszy jeden z tych kont, może uruchamiać [ataki boczne](https://aka.ms/pth) w całej organizacji. Każde naruszone konto zapewnia atakującemu dostęp do jeszcze większej liczby kont i zasobów oraz umieszcza je w jednym kroku bliżej kradzieży tajemnicy firmy, uruchomienie ataku typu "odmowa usługi" i nie tylko.

Nie zawsze można łatwo usuwać uprawnień administracyjnych. Rozważmy typowy scenariusz, w którym rola DNS jest zainstalowana na tym samym komputerze co kontroler domena usługi Active Directory. Administratorzy DNS muszą mieć uprawnienia administratora lokalnego, aby naprawić problemy z serwerem DNS. Jednak w tym celu należy wprowadzić członków grupy zabezpieczeń **Administratorzy domeny** o wysokim poziomie uprawnień. Takie podejście efektywnie zapewnia administratorom DNS kontrolę nad całą domeną i dostęp do wszystkich zasobów na tym komputerze.

JEA rozwiązuje ten problem z zasadą najniższych **uprawnień**. Za pomocą JEA można skonfigurować punkt końcowy zarządzania dla administratorów DNS, który zapewnia im dostęp tylko do poleceń programu PowerShell, które są potrzebne do wykonania zadania. Oznacza to, że można zapewnić odpowiedni dostęp do naprawy trującej pamięci podręcznej DNS lub ponownie uruchomić serwer DNS bez przypadkowego udzielenia im praw do Active Directory lub przeglądania systemu plików lub uruchamiania potencjalnie niebezpiecznych skryptów. Jeszcze lepiej, gdy sesja JEA jest skonfigurowana do używania tymczasowych, uprzywilejowanych kont wirtualnych, Administratorzy DNS mogą łączyć się z serwerem przy użyciu poświadczeń **innych niż administracyjne** i nadal uruchamiać polecenia, które zwykle wymagają uprawnień administratora. Program JEA umożliwia usuwanie użytkowników z ról administratorów lokalnych/domenowych, a także precyzyjną kontrolę nad tym, co mogą robić na poszczególnych komputerach.

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej o wymaganiach dotyczących używania JEA, zobacz artykuł [wymagania wstępne](prerequisites.md) .

## <a name="samples-and-dsc-resource"></a>Przykłady i zasób DSC

Przykładowe konfiguracje JEA i zasób JEA DSC można znaleźć w [repozytorium usługi GitHub jea](https://github.com/PowerShell/JEA).
