---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Omówienie platformy Desired State Configuration dla osób podejmujących decyzje
ms.openlocfilehash: 7c36aa5fadeab8bcb381f316288d102b5ce402e2
ms.sourcegitcommit: ac20e0faaa37142e9c6e4507a21df2f4a3fdbece
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44339841"
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a>Omówienie platformy Desired State Configuration dla osób podejmujących decyzje

W tym dokumencie opisano korzyści dla firm za pomocą Windows PowerShell Desired State Configuration (DSC). Nie jest podręcznik techniczny.

## <a name="what-is-desired-state-configuration"></a>Co to jest Desired State Configuration?

PowerShell Desired State Configuration jest wbudowana w Windows, który jest oparty na otwartych standardach platforma zarządzania konfiguracji. DSC jest wystarczająco elastyczny, aby działać niezawodnie i spójne na każdym etapie cyklu życia wdrożenia (rozwoju, testowania, środowiska produkcji wstępnej, produkcji), a także podczas skalowania w poziomie.

DSC koncentruje się wokół [konfiguracje](configurations.md).
Konfiguracja jest dokument łatwych do zrozumienia, który opisuje środowisko, które składają się z komputerów "(węzłów) o określonej charakterystyce.
Te cechy mogą być proste i polega na zapewnienie, że określoną funkcję Windows jest włączona lub tak złożonego jak wdrażanie programu SharePoint.

DSC ma, monitorowania i raportowania, wbudowane.
Jeśli system nie jest już zgodne, DSC można zgłosić alert i działania, aby poprawić systemu.

## <a name="benefits-of-using-desired-state-configuration"></a>Korzyści z używania Desired State Configuration

Konfiguracje są przeznaczone do można łatwo odczytać, przechowywane i zaktualizowane.
Konfiguracje zadeklarować urządzenia docelowe stanu powinien być, zamiast pisania instrukcji dotyczących sposobu umieść je w tym stanie.
Dzięki temu znacznie mniej kosztowne, Dowiedz się, przyjmuje, wdrożenia i obsługa konfiguracji za pomocą DSC.

Tworzenie konfiguracji oznacza, że złożone wdrożenia kroki są przechwytywane jako "pojedyncze wiarygodne źródło" w obrębie jednej lokalizacji.
Dzięki temu wielokrotnego wdrożeń określonego zestawu maszyn znacznie mniej podatne na błędy.
Z kolei, że wdrożenia szybszy i bardziej niezawodny umożliwiająca sprawność w złożonych wdrożeń.

Konfiguracje są również możliwe do udostępnienia za pośrednictwem [galerii programu PowerShell](https://powershellgallery.com) oznacza typowe scenariusze i najlepsze rozwiązania mogą już istnieć dla prac, które należy wykonać.


## <a name="desired-state-configuration-and-devops"></a>Desired State Configuration i metodyki DevOps

DSC zaprojektowano pod kątem [DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) należy pamiętać, połączeniu ludzi, procesów i narzędzi, które pozwalają na szybkie wdrażanie i iterację koncentruje się na dostarczaniu wartości dla użytkowników końcowych, czy wewnętrzny lub zewnętrzny.
Po jednej konfiguracji zdefiniować środowiska oznacza deweloperzy mogą kodowanie ich wymagań na konfigurację, sprawdź tę konfigurację do kontroli źródła i operacji zespoły mogą z łatwością wdrażać kod bez konieczności podatne na błędy Ręczne procesy.

Są również konfiguracje [opartych na danych](configData.md), który ułatwia platformy ops zidentyfikować i zmienić środowiskach bez interwencji dla deweloperów.

## <a name="desired-state-configuration-on--and-off-premises"></a>Desired State Configuration na — i poza siedzibą firmy

DSC może służyć do zarządzania wdrożeniami zarówno lokalnych, jak i poza siedzibą firmy.
W przypadku rozwiązań lokalnych ma DSC [serwera ściągania](pullServer.md) , można scentralizować zarządzania maszynami oraz generowania raportów dotyczących stanu.
Dla rozwiązań w chmurze DSC nadaje wszędzie tam, gdzie Windows jest używany.
Dostępne są także określonych oferty z platformy Azure, oparta na Desired State Configuration, takich jak [usługi Azure Automation](https://azure.microsoft.com/en-us/documentation/services/automation/), który umożliwia scentralizowanie raportowanie DSC.

## <a name="dsc-and-compatibility"></a>DSC i zgodność

Chociaż DSC została wprowadzona w systemie Windows Server 2012 R2, jest dostępny dla systemów operacyjnych niższego poziomu przy użyciu pakietu Windows Management Framework (WMF).
Więcej informacji na temat platformy WMF znajdują się na [strona główna programu PowerShell](/powershell/).

DSC może służyć także do zarządzania systemem Linux. Aby uzyskać więcej informacji, zobacz [wprowadzenie DSC dla systemu Linux](lnxGettingStarted.md).
