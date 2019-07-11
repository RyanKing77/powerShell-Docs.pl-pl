---
ms.date: 07/10/2019
keywords: jea, programu powershell, zabezpieczeń
title: Omówienie wystarczający zakres administracji
ms.openlocfilehash: 4b74e5be9558810748a8844a325c8213e1b3ebc9
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726650"
---
# <a name="just-enough-administration"></a>Narzędzia Just Enough Administration

Tylko tyle administracji (JEA) to technologia zabezpieczeń, która umożliwia delegowane administracji dla każdego elementu zarządzane przez program PowerShell. Za pomocą technologii JEA możesz wykonywać następujące czynności:

- **Zmniejsz liczbę administratorów na maszynach** przy użyciu kont wirtualnych lub konta usług zarządzane grupy do wykonania uprzywilejowanych akcji w imieniu użytkowników regularne.
- **Ograniczenia, które mogą wykonywać użytkownicy** , określając, który poleceń cmdlet, funkcji i poleceń zewnętrznych mogą uruchamiać.
- **Lepiej zrozumieć, co robią użytkownicy** przy użyciu transkrypcji i dzienniki, dowiesz się dokładnie, które polecenia wykonywane podczas ich sesji użytkownika.

**JEA jest ważna**

Wysoce uprzywilejowanych kont używane do administrowania serwerami stwarzać poważne zagrożenie bezpieczeństwa. Należy osobie atakującej naruszenie jednego z tych kont, ich można uruchomić [poprzecznego ataków](https://aka.ms/pth) całej organizacji. Każdego konta ze złamanymi zabezpieczeniami daje osobie atakującej uzyskanie dostępu do jeszcze więcej kont i zasobów i umieszcza je o krok bliżej od celu kradzież firmy wpisów tajnych oraz ich uruchamianie ataku typu "odmowa usługi" i nie tylko.

Nie zawsze jest łatwo albo Usuń uprawnienia administracyjne. Należy rozważyć typowy scenariusz, w którym rola DNS jest zainstalowany na tym samym komputerze jako kontrolera domeny usługi Active Directory. Administratorzy usługi DNS wymagają uprawnień administratora lokalnego, aby rozwiązać problemy z serwerem DNS. Aby to zrobić, należy ich elementy członkowskie o wysokim poziomie uprawnień, ale **Administratorzy domeny** grupy zabezpieczeń. Takie podejście zapewnia efektywne Administratorzy DNS kontroli nad całej domeny i dostęp do wszystkich zasobów na tym komputerze.

JEA rozwiązuje ten problem za pomocą zasady **najniższych uprawnień**. JEA można skonfigurować punktu końcowego zarządzania dla administratorów DNS, które umożliwia im dostęp tylko do poleceń programu PowerShell, potrzebnych im uzyskać ich pracę. Oznacza to zapewnić odpowiedni dostęp, aby naprawić uszkodzone kolejką pamięci podręcznej DNS lub uruchom ponownie serwer DNS bez przypadkowo nadawania im praw do usługi Active Directory lub Przeglądaj system plików lub uruchamianie skryptów potencjalnie niebezpieczne. Jeszcze lepiej, gdy sesja JEA jest skonfigurowany do używania tymczasowe uprzywilejowanych kont wirtualnych, administratorów DNS można nawiązać połączenie serwera za pomocą **nieadministracyjna** poświadczenia i nadal uruchamianie poleceń, które zwykle wymagają administratora uprawnienia. JEA umożliwia usuwanie użytkowników z ról administratora powszechnie uprzywilejowanego lokalne/domeny i dokładnie kontrolować, co może zrobić na każdym komputerze.

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej na temat wymagań w zakresie używania usługi JEA, zobacz [wymagania wstępne](prerequisites.md) artykułu.

## <a name="samples-and-dsc-resource"></a>Przykłady i zasobów DSC

Przykładowe JEA konfiguracji i zasobów DSC JEA znajdują się w [repozytorium GitHub usługi JEA](https://github.com/PowerShell/JEA).
