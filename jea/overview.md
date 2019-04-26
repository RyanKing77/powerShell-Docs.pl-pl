---
ms.date: 06/12/2017
keywords: jea, programu powershell, zabezpieczeń
title: Omówienie wystarczający zakres administracji
ms.openlocfilehash: c097838fb25a63d42502eebf751c64c537bdd077
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084916"
---
# <a name="just-enough-administration"></a>Narzędzia Just Enough Administration

Tylko tyle administracji (JEA) to technologia zabezpieczeń, która umożliwia delegowane administracji dla każdego elementu, którymi można zarządzać za pomocą programu PowerShell.
Za pomocą technologii JEA możesz wykonywać następujące czynności:

- **Zmniejsz liczbę administratorów na maszynach** wykorzystaniem kont wirtualnych lub grup zarządzanych kont usług, które wykonania uprzywilejowanych akcji w imieniu użytkowników regularne.
- **Ograniczenia, które mogą wykonywać użytkownicy** , określając, który poleceń cmdlet, funkcji i poleceń zewnętrznych mogą uruchamiać.
- **Lepiej zrozumieć, co robią użytkownicy** przy użyciu transkrypcji i dzienniki, dowiesz się dokładnie, które polecenia wykonywane podczas ich sesji użytkownika.

**Dlaczego jest to istotne?**

Wysoce uprzywilejowanych kont używane do administrowania serwerami stwarzać poważne zagrożenie bezpieczeństwa.
Należy osobie atakującej naruszenie jednego z tych kont, ich można uruchomić [poprzecznego ataków](http://aka.ms/pth) całej organizacji.
Każde konto, które mogą naruszyć można nadały im dostęp nawet więcej kont i zasobów, umieszczając je o krok bliżej kradzież firmy wpisów tajnych oraz ich uruchamianie ataku typu "odmowa usługi" i nie tylko.

Nie zawsze jest łatwo albo Usuń uprawnienia administracyjne.
Należy rozważyć typowy scenariusz, w którym rola DNS jest zainstalowany na tym samym komputerze jako kontrolera domeny usługi Active Directory.
Administratorzy usługi DNS wymagają uprawnień administratora lokalnego, aby rozwiązać problemy z serwerem DNS, ale aby to zrobić, więc trzeba były wysoko uprzywilejowane grupy zabezpieczeń "Administratorzy domeny".
Takie podejście zapewnia efektywne Administratorzy DNS kontroli nad całej domeny i dostęp do wszystkich zasobów na tym komputerze.

JEA pomaga rozwiązać ten problem, która ułatwia przyjęcie zasady *najniższych uprawnień*.
Za pomocą technologii JEA można skonfigurować punktu końcowego zarządzania dla administratorów DNS, które umożliwia im dostęp do wszystkich potrzebnych im uzyskać ich gotowe poleceń programu PowerShell, ale nic więcej.
Oznacza to zapewnić odpowiedni dostęp, aby naprawić uszkodzone kolejką pamięci podręcznej DNS lub uruchom ponownie serwer DNS bez przypadkowo nadawania im praw do usługi Active Directory lub Przeglądaj system plików lub uruchamianie skryptów potencjalnie niebezpieczne.
Jeszcze lepiej, gdy sesja JEA jest skonfigurowany do używania tymczasowe uprzywilejowanych kont wirtualnych, administratorów DNS można nawiązać połączenie serwera za pomocą *nieadministracyjna* poświadczeń i nadal mieć możliwość uruchamiania poleceń, które zwykle wymagają uprawnienia administratora.
Ta funkcja pozwala na usuwanie użytkowników z ról administratora domenę lokalną powszechnie uprzywilejowanego i zamiast tego dokładnie kontrolować co to są w stanie wykonać na każdym komputerze.

## <a name="get-started-with-jea"></a>Wprowadzenie do usługi JEA

Możesz rozpocząć korzystanie z usługi JEA już dziś na dowolnym komputerze z systemem Windows Server 2016 lub Windows 10.
Można również uruchomić JEA w starszych systemach operacyjnych z aktualizacją systemu Windows Management Framework.
Aby dowiedzieć się więcej o wymaganiach dotyczących do używania usługi JEA i Dowiedz się, jak tworzyć, używać i inspekcji punktu końcowego JEA, zapoznaj się z następujących tematów:

- [Wymagania wstępne](prerequisites.md) — wyjaśnia, jak skonfigurować środowisko do używania usługi JEA.
- [Możliwości roli](role-capabilities.md) — wyjaśnia, jak tworzyć role, które określają, co użytkownik może wykonywać w ramach sesji usługi JEA.
- [Konfiguracje sesji](session-configurations.md) — objaśnienie sposobu konfigurowania punktów końcowych JEA mapowanie użytkowników do ról, które ustawienia tożsamości usługi JEA
- [Rejestrowanie usługi JEA](register-jea.md) — Tworzenie punktu końcowego JEA i udostępnić użytkownikom łączenie się z.
- [Korzystanie z usługi JEA](using-jea.md) -informacje dotyczące różnych sposobów, można użyć technologii JEA.
- [Zagadnienia dotyczące zabezpieczeń](security-considerations.md) — Przejrzyj najlepsze rozwiązania dotyczące zabezpieczeń i zagadnień dotyczących opcji konfiguracji technologii JEA.
- [Inspekcja i raportowanie dotyczące technologii JEA](audit-and-report.md) — Dowiedz się, jak Inspekcja i raportowanie dla punktów końcowych JEA.

## <a name="samples-and-dsc-resource"></a>Przykłady i zasobów DSC

Przykładowe JEA konfiguracji i zasobów DSC JEA znajdują się w [repozytorium GitHub usługi JEA](https://github.com/PowerShell/JEA).