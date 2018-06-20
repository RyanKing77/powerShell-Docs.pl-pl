---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: da603fda4499129b415477f627842fe10abefe06
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188500"
---
# <a name="just-enough-administration-jea"></a>Just Enough Administration (JEA)
Po prostu wystarczająco administracji jest nową funkcją w programie WMF 5.0, który umożliwia administracji opartej na rolach, za pośrednictwem usługi zdalne środowiska PowerShell.  Rozszerza istniejącą infrastrukturę ograniczonego punktu końcowego, zezwalając z systemem innym niż Administratorzy na uruchamianie określonych poleceń, skrypty i pliki wykonywalne jako administrator.  Dzięki temu można zmniejszyć liczbę administratorów pełna w danym środowisku i zwiększyć bezpieczeństwo.  JEA działa dla wszystkich, którymi można zarządzać za pomocą programu PowerShell; Jeśli można zarządzać za pomocą programu PowerShell, JEA można to robić, więc bezpieczniejsze.  Aby uzyskać szczegółowy widok tylko tyle administracji, zapoznaj się z [wystąpić przewodnik](http://aka.ms/JEA).

W odróżnieniu od starego ograniczonego punktów końcowych JEA jest zaawansowaną i łatwa do skonfigurowania.  Możliwości użytkowników w ramach zasad JEA można częściami kontrolować, dół ograniczanie zestawów parametrów i wartości, które mogą być dostarczane do określonego polecenia. Akcje użytkownika są uruchamiane w kontekście jednorazowe konta wirtualnych, które ma prawa do wykonania czynności wykonywane przez administratorów.  Polecenia wywoływane przez użytkownika mogą być rejestrowane dla inspekcji zabezpieczeń.

JEA działa, umożliwiając tworzenie specjalnie skonfigurować ograniczone punktów końcowych.  Te punkty końcowe mają kilka najważniejsze czynniki:

1. Użytkowników łączących się z nimi "Uruchom jako" uprzywilejowanego konta wirtualnego, który istnieje tylko na czas tej sesji zdalnej.  Domyślnie to wirtualny konto jest członkiem grupy Administratorzy domeny, na kontrolerach domeny, a także wbudowanej grupy administratorów (Uwaga: te uprawnienia są konfigurowalne). Łącząc jako jednego użytkownika i uruchamiając jako inny użytkownik uprzywilejowanego, umożliwiają użytkownikom bez uprawnień do wykonywania określonych zadań administracyjnych bez udzielania uprawnień administracyjnych na systemy.
2. Punkt końcowy jest zablokowana.  Oznacza to, programu PowerShell działa w trybie bez języka.  Tylko polecenia specyficzne, skrypty i pliki wykonywalne są widoczne dla użytkownika.
3. Różnych użytkowników łączących się są prezentowane z innym zestawem funkcji na podstawie przynależności do grupy.  Musisz podać różne role różnych funkcji w tym samym punkcie końcowym.
