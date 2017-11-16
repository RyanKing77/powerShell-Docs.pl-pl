---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: "jea, programu powershell, zabezpieczeń"
title: "Omówienie wystarczającego administracji"
ms.openlocfilehash: a664a8ad44916f8112f7ef7bac145a54b83f126d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="just-enough-administration"></a>Narzędzia Just Enough Administration

Po prostu wystarczająco administracyjnej (JEA) jest to technologia zabezpieczeń, która umożliwia delegowane administracji dla wszystkich elementów, którymi można zarządzać za pomocą programu PowerShell.
JEA można:

- **Zmniejsz liczbę administratorów na maszynach** kont wirtualnych korzystanie z usług lub grupy zarządzane konta usług, które wykonania uprzywilejowanych akcji w imieniu użytkowników regularne.
- **Ograniczenia, które mogą wykonywać użytkownicy** przez określenie, które polecenia cmdlet, funkcji i poleceń zewnętrznych, które mogą uruchamiać.
- **Lepiej zrozumieć, co robią użytkownicy** z dzienników i zapisy który opisano dokładnie które polecenia wykonywane podczas sesji użytkownika.

**Dlaczego jest to istotne?**

Kont z wysokimi uprawnieniami do administrowania serwerami stwarzać poważne zagrożenie bezpieczeństwa.
Należy osoba atakująca naruszenia zabezpieczeń jeden z tych kont, one będą mogły uruchamiać [penetracji ataków](http://aka.ms/pth) całej organizacji.
Każde konto, które wykraczają może umożliwić im dostępu do nawet więcej kont i zasobów, wprowadzenie ich bliższe kradzież kluczy tajnych firmy, uruchamianie ataku typu "odmowa usługi" i inne.

Nie zawsze jest łatwo albo Usuń uprawnienia administracyjne.
Należy wziąć pod uwagę typowy scenariusz, w którym jest zainstalowana rola DNS na tym samym komputerze co kontrolerze domeny usługi Active Directory.
Administratorzy powinni DNS wymagają uprawnień administratora lokalnego, aby rozwiązać problemy z serwerem DNS, ale aby zrobić, należy je wysoko uprzywilejowane grupy zabezpieczeń "Administratorzy domeny".
Takie podejście skutecznie zapewnia kontrolę administratorów DNS w całej domenie i dostęp do wszystkich zasobów na tym komputerze.

JEA pomaga rozwiązać ten problem, pomagając przyjmuje zasady *najniższych uprawnień*.
Punkt końcowy zarządzania JEA, można skonfigurować dla administratorów DNS, które umożliwi im dostęp do wszystkich poleceń programu PowerShell, które są niezbędne do ich pracy get, ale nic więcej.
Oznacza to zapewnienia odpowiedniego dostępu do naprawy skażone pamięć podręczna DNS lub uruchom ponownie serwer DNS nie przypadkowo nadanie im prawa do usługi Active Directory lub przeglądać systemu plików lub uruchamianie skryptów potencjalnie niebezpieczne.
Jeszcze lepiej, gdy sesja JEA jest skonfigurowany do używania tymczasowego uprzywilejowanych kont wirtualnych, administratorami DNS mogą łączyć się z serwera przy użyciu *bez uprawnień administratora* poświadczenia i nadal będzie można uruchamiać polecenia, które zwykle wymagają uprawnienia administratora.
Ta funkcja umożliwia usunąć użytkowników z ról administratora domenę lokalną powszechnie uprzywilejowanych i zamiast tego ścisła kontrola, jakie są można wykonać na każdym komputerze.

## <a name="get-started-with-jea"></a>Rozpoczynanie pracy z JEA

Możesz rozpocząć używać JEA dzisiaj na dowolnym komputerze z systemem Windows Server 2016 lub Windows 10.
Można również uruchomić JEA w starszych systemach operacyjnych w aktualizacji Windows Management Framework.
Aby dowiedzieć się więcej o wymaganiach dotyczących używania JEA i informacje na temat tworzenia, użyć i inspekcji punktu końcowego JEA, zobacz następujące tematy:

- [Wymagania wstępne](prerequisites.md) -opisano sposób konfigurowania środowiska, aby użyć JEA.
- [Możliwości roli](role-capabilities.md) -wyjaśniono, jak tworzyć role, które określają, co użytkownik może wykonywać w sesji JEA.
- [Konfiguracje sesji](session-configurations.md) -opisano sposób konfigurowania punktów końcowych JEA, które mapowanie użytkowników do ról i ustaw tożsamość JEA
- [Rejestrowanie JEA](register-jea.md) — Tworzenie punktu końcowego JEA i udostępnić użytkownikom łączenie się z.
- [Przy użyciu JEA](using-jea.md) -informacje dotyczące różnych sposobów korzystania JEA.
- [Zagadnienia dotyczące zabezpieczeń](security-considerations.md) — Przegląd najlepszych rozwiązań dotyczących zabezpieczeń i wpływ JEA opcji konfiguracji.
- [Inspekcja i raport dotyczący JEA](audit-and-report.md) — Dowiedz się, jak inspekcji i raport dotyczący JEA punktów końcowych.

## <a name="samples-and-dsc-resource"></a>Przykłady i zasobów usługi Konfiguracja DSC

Przykładowe konfiguracje JEA i zasobów JEA DSC znajdują się w [repozytorium JEA GitHub](https://github.com/PowerShell/JEA).

