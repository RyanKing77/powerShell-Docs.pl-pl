---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Żądany przegląd stanu konfiguracji dla inne osoby podejmujące decyzje"
ms.openlocfilehash: e39ab5138b20653e46ac35fa32b99d268f96b2df
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/13/2017
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a>Żądany przegląd stanu konfiguracji dla inne osoby podejmujące decyzje

Ten dokument zawiera opis korzyści biznesowe przy użyciu konfiguracji żądanego stanu środowiska PowerShell (DSC). Nie jest podręcznik techniczny.

## <a name="what-is-desired-state-configuration"></a>Co to jest Konfiguracja żądanego stanu?

Windows PowerShell Desired stan konfiguracji (DSC) to platforma zarządzania konfiguracji wbudowanego w systemie Windows, która jest oparta na standardach Otwórz. DSC jest wystarczająco elastyczny, działają niezawodnie i spójnej na każdym etapie cyklu wdrażania (Programowanie, testu, produkcji wstępnej, produkcji), a także podczas skalowania w poziomie. 

DSC koncentruje się wokół "[konfiguracje](https://msdn.microsoft.com/en-us/powershell/dsc/configurations)".
Konfiguracja jest łatwy do odczytania dokument, który opisuje środowisko złożoną z komputerów "(węzłów) o określonej charakterystyce. Te właściwości można tak proste, jak zapewnienie, że określonych funkcji systemu Windows jest włączona lub złożonym wdrażania SharePoint. 

DSC ma, monitorowania i raportowania wbudowane. Jeśli system nie jest zgodne, DSC można Zgłoś alert i działania, aby naprawić system. 

## <a name="benefits-of-using-desired-state-configuration"></a>Korzyści wynikające ze stosowania konfiguracji żądanego stanu

Konfiguracje są przeznaczone do można łatwo odczytać przechowywane i aktualizacji. Konfiguracje zadeklarować urządzenia stan powinien być, zamiast zapisywania instrukcje dotyczące sposobu umieść je w tym stanie. Dzięki temu można znacznie mniej kosztowne Dowiedz się, przyjmuje, wdrożenia i obsługa konfiguracji za pośrednictwem usługi Konfiguracja DSC. 

Tworzenie konfiguracji oznacza, że kroki wdrażania złożone są przechwytywane jako "pojedynczego źródła prawdy" w jednym miejscu. Dzięki temu można znacznie mniej podatne na błędy powtarzane wdrożeń określonego zestawu komputerów. Z kolei wprowadzenie wdrożeniami szybszy i bardziej niezawodny co pozwala sprawność na złożone wdrożenia.

Konfiguracje są również współużytkowane przez [galerii programu PowerShell](https://powershellgallery.com) oznacza typowych scenariuszy i najlepszych rozwiązań może już istnieć pracy należy wykonać.


## <a name="desired-state-configuration-and-devops"></a>Konfiguracji żądanego stanu i opracowywania oprogramowania

[DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) jest kombinacją osób, technologii i kultura, która umożliwia szybkie wdrażanie i iteracji. DSC została zaprojektowana z DevOps pamiętać. O pojedynczą konfiguracją zdefiniuj środowisku oznacza, że deweloperzy mogą kodowanie ich wymagań na konfigurację, sprawdź tej konfiguracji do kontroli źródła i zespołów operacyjnych z łatwością wdrożyć kodu bez konieczności przechodzenia przez podatne na błędy procesów ręcznych. 

Konfiguracje są również [opartych na danych](https://msdn.microsoft.com/en-us/powershell/dsc/configdata), które ułatwia tworzenie zespołów ops do identyfikowania i zmienić środowiskach bez interwencji developer. 

## <a name="desired-state-configuration-on--and-off-premises"></a>Konfiguracji żądanego stanu na — i poza siedzibą firmy

DSC może służyć do zarządzania wdrożeniami zarówno lokalnie, jak i poza siedzibą firmy. Rozwiązania lokalnego ma DSC [serwera ściągania](https://msdn.microsoft.com/en-us/powershell/dsc/pullserver) który umożliwia scentralizowane zarządzanie maszyn i raport dotyczący ich stan. Rozwiązania chmury DSC jest możliwe wszędzie tam, gdzie Windows nadaje się do użytku. Dostępne są także określonych ofert z platformy Azure, takich jak oparta na konfiguracji żądanego stanu [usługi Automatyzacja Azure](https://azure.microsoft.com/en-us/documentation/services/automation/), która centralizuje raportowania usługi Konfiguracja DSC. 

## <a name="dsc-and-compatibility"></a>DSC i zgodności

Mimo że DSC została wprowadzona w systemie Windows Server 2012 R2, jest dostępna dla systemów operacyjnych niskiego poziomu za pomocą pakietu Windows Management Framework (WMF). Więcej informacji na temat WMF można znaleźć w [strona główna programu PowerShell](https://msdn.microsoft.com/en-us/powershell/). 

DSC mogą służyć do zarządzania systemem Linux. Aby uzyskać więcej informacji, zobacz [wprowadzenie do korzystania z usługi Konfiguracja DSC Linux](https://msdn.microsoft.com/en-us/powershell/dsc/lnxgettingstarted).

