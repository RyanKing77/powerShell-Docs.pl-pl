---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zaawansowane tworzenie zawartości DSC na potrzeby składania i współpracy
ms.openlocfilehash: 3e40ba94de0a53c1c9663553c4ec443b5e0df3fd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687174"
---
# <a name="advanced-dsc-authoring-for-composition-and-collaboration"></a>Zaawansowane tworzenie zawartości DSC na potrzeby składania i współpracy

W tym artykule opisano rodzaje metody łączenia konfiguracjami i zasobami.
Celem dla każdego scenariusza jest takie same, aby ograniczyć złożoność przy konfiguracji z wieloma są preferowane nawiązać połączenie z serwerem stanu końcowego wdrożenia.
Na przykład będzie wiele zespołów współtworzących wynik wdrożenia serwera, na przykład właściciela aplikacji, utrzymanie stanu aplikacji i centralny zespół przy zwalnianiu zmiany podstawy zabezpieczeń.
Szczegóły skutecznego każde podejście, w tym korzyści i zagrożeń są szczegółowo opisane w tym miejscu.

![Potok](../images/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a>Typy wspólne technik tworzenia pakietów administracyjnych

Istnieją dwa rozwiązania wbudowane Local Configuration Manager, aby włączyć tę koncepcję:

| Pojęcia | Szczegółowe informacje
|-|-
| Konfiguracje częściowe | [Dokumentacja](../pull-server/partialConfigs.md)
| Zasoby złożone | [Dokumentacja](../resources/authoringResourceComposite.md)

## <a name="understanding-the-impact-of-each-approach"></a>Opis wpływu każde podejście

Jedno z poniższych rozwiązań może służyć do zarządzania wynik wdrożenia serwera.
Istnieje jednak istotną różnicą w wpływ za pomocą danej metody.

## <a name="partial-configurations"></a>Konfiguracje częściowe

Korzystając z konfiguracje częściowe, Local Configuration Manager jest skonfigurowany do niezależnie zarządzać wieloma konfiguracjami.
Konfiguracje są kompilowane niezależnie i przypisywany do węzła.
Wymaga to LCM należy skonfigurować z wyprzedzeniem o nazwie każdej konfiguracji.

![PartialConfiguration](../images/PartialConfiguration.jpg)

Konfiguracje częściowe zapewnia dwa lub więcej, zespoły Pełna kontrola nad konfiguracji serwera, często bez korzyści komunikacji i współpracy.

Klienci zostały podane opinie, które może to prowadzić do konfliktów zasobów niezamierzone zastąpienia i ostatecznie utraty kontroli true konfiguracji zasobu.

Ponadto klientów zostały podane opinii, korzystając z tego modelu, każdego kontroli zmian konfiguracji zespoły prawdopodobnie nie można w pełni przetestowane za pomocą potoku wydania, co prowadzi do nieoczekiwanych wyników w środowisku produkcyjnym.

**Jest niezwykle, że jeden potok używane do oceny, wszystkie zmiany wersji serwerów.**

Na poniższej ilustracji zespół B zwalnia ich częściowe konfiguracji do zespołu A. zespołu, A następnie uruchamia testy na serwerze z obu konfiguracje stosowane.
W tym modelu tylko jeden urząd ma uprawnienia do wprowadzania zmian w środowisku produkcyjnym.

![PartialSinglePipeline](../images/PartialSinglePipeline.jpg)

Gdy są wymagane zmiany z zespół B, należy przesłać, żądanie ściągnięcia względem środowiska kontroli źródła Team A.
Zespół A może następnie przejrzyj zmiany, przy użyciu automatyzacji testów i wydania do środowiska produkcyjnego, gdy istnieje pewność, że zmiany nie spowoduje błędów w aplikacji lub usług hostowanych na serwerze.

## <a name="composite-resources"></a>Zasoby złożone

Zasób złożonego jest po prostu konfiguracji DSC w pakiecie jako zasób.
Nie istnieją specjalne wymagania dotyczące konfigurowania LCM do akceptowania zasoby złożone.
Zasoby są używane w ramach nowej konfiguracji i kompilacji pojedynczej wyniki w jednym pliku MOF.

![CompositeResource](../images/CompositeResource.jpg)

Istnieją dwa typowe scenariusze zasoby złożone.
Pierwsza to zmniejszyć złożoność i abstrakcyjny unikatowe koncepcje.
Drugi cel to umożliwić odniesienia do umieszczenia w pakiecie przez zespół aplikacji bezpiecznie wdrażać za pośrednictwem ich potoku tworzenia wersji w środowisku produkcyjnym, po pomyślnym przejściu wszystkich testów.

```PowerShell
Configuration Name
{
  File 1
  {
    Ensure = “Present”
    Path = “c:\inetpub\file1.zip”
    Source = “http://uri/file1.zip”
  }
  Service A
  {
    Ensure = “Present”
    Name = “ServiceA”
    Status = “Running”
  }
  SecurityBaseline Settings
  {
    Ensure = “Present”
    Datacenter = “NorthAmerica”
  }
}
```

Zasoby złożone promowanie kompozycji i współpraca przy użyciu potoku podczas kompilowania dojrzałości operacyjne

Być może już używasz zasoby złożone bez wiedzy.
Na przykład **ServiceSet**.
Ten zasób zarządza stan wielu usług Windows bez wymienienie ich osobno.
Właściwość Nazwa przyjmuje tablicę ciągów, aby podać nazwę każdej usługi.
Podczas kompilowania konfiguracji MOF będzie zawierać unikatowy sekcji usługi dla każdej nazwy przekazywane do ServiceSet.

Organizacje może być "agents" lub "pośredniczącym", który powinien być zainstalowany na każdym serwerze.
Zasób złożonego jest najlepszą odpowiedź, zarządzanie, zależnościami, instalacji i konfiguracji takiego narzędzia i programy narzędziowe.

Osobę lub zespół odpowiedzialny za rozwiązań obejmujących wiele serwerów autorów zawierające ich wymagania dotyczące konfiguracji.
Następnie konfiguracji będzie dostarczana jako zasób złożonego za pomocą instrukcje podane w dokumentacji programu composite zasobów.
Na koniec nowy zasób złożonego powinny być publikowane do lokalizacji, na przykład do udziału plików lub NuGet źródła danych, w którym zespoły aplikacji mogą wykorzystywać je w ich konfiguracji.

Każdorazowo zespół udostępnia nową wersję, będą one zwiększenie numeru wersji w manifeście modułu dla swojego zasobu złożonego.
Zespoły aplikacji obejmują złożonego zasobów w konfiguracji, które one tworzenie zarządzania zależności aplikacji.
Gdy zespoły Operations/Security wydasz nową wersję ich zasobu, informują one zespoły aplikacji, nowe zmiany.

Zespoły aplikacji mogą wyzwoliła wydanie do produkcji, gdzie jedyna różnica polega na linii bazowych.
Jednak zapewnia możliwość oceny wpływu na aplikacje przed ryzykiem przerwa w działaniu usługi.

Uwaga — informacje zwrotne dotyczące użytkowania zasoby złożone dołączyła krytykę, że wprowadzanie zmian wymaga kompilacji i zwalniania nowego pliku MOF.
To działanie jest celowe.
Każdą nową wersją konfiguracji powinien zawierać statyczne odwołanie do określonej wersji poszczególnych zasobów i powinny być weryfikowane przez testy przed osiągnięciem węzły serwera produkcyjnego.
Proces testowania i zwalniania zmian z kontroli źródła tworzy bezpieczne środowisko służącą do zwalniania zmiany w partiach małe, ale często.

Aby uzyskać więcej informacji o zarządzaniu infrastrukturze podstawowej za pomocą potoków wydania zobacz oficjalny dokument: [Model potoku wydania](../further-reading/whitepapers.md).
