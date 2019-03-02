---
title: Parametry działań | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e4e0cf6-19e0-44b8-8b40-d6f6075276cf
caps.latest.revision: 5
ms.openlocfilehash: 489d8bcdabe904d6a3d2bc6cdb9d7e23d09cbef2
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251221"
---
# <a name="activity-parameters"></a>Parametry działań

W poniższej tabeli wymieniono nazwy zalecane i funkcje dotyczące parametrów działań.

|Parametr|Funkcja|
|---|---|
|**Dołącz**<br>Typ danych: SwitchParameter|Implementowanie tego parametru, użytkownik może dodawać zawartość do końca zasobu, jeśli określono parametr.|
|**CaseSensitive**<br>Typ danych: SwitchParameter|Implementuje ten parametr, dzięki czemu użytkownik może wymagać rozróżnianie wielkości liter, jeśli określono parametr.|
|**Polecenie**<br>Typ danych: Ciąg|Ten parametr należy zaimplementować, dzięki czemu użytkownik może określić ciąg polecenia do uruchomienia.|
|**CompatibleVersion**<br>Typ danych: Obiekt System.Version|Ten parametr należy zaimplementować, dzięki czemu użytkownik może określić semantykę, która polecenie cmdlet musi być zgodny z potrzeby utrzymywania zgodności z poprzednimi wersjami.|
|**Kompresuj**<br>Typ danych: SwitchParameter|Implementowanie tego parametru, kompresja danych jest używany, gdy określono parametr.|
|**Kompresuj**<br>Typ danych: Słowo kluczowe|Implementowanie tego parametru, użytkownik może określić algorytm kompresji danych.|
|**Ciągłe**<br>Typ danych: SwitchParameter|Implementowanie tego parametru, dane zostaną przetworzone, dopóki użytkownik kończy działanie polecenia cmdlet, gdy określono parametr. Jeśli parametr nie jest określony, polecenie cmdlet przetwarza wstępnie zdefiniowanych ilości danych i następnie kończy operację.|
|**Tworzenie**<br>Typ danych: SwitchParameter|Implementowanie tego parametru, aby wskazać, czy zasób został utworzony, jeśli jeden nie już istnieć, gdy określono parametr.|
|**Usuwanie**<br>Typ danych: SwitchParameter|Implementowanie tego parametru, aby zasoby zostaną usunięte po zakończeniu jego działania polecenia cmdlet, jeśli określono parametr.|
|**Opróżniania**<br>Typ danych: SwitchParameter|Implementowanie tego parametru, aby wskazać, że elementy robocze oczekujących są przetwarzane przed polecenia cmdlet przetwarza nowe dane, gdy określono parametr. Jeśli parametr nie jest określony, elementy robocze są przetwarzane od razu.|
|**Erase**<br>Typ danych: Int32|Implementowanie tego parametru, użytkownik może określić liczbę przypadków, gdy zasób jest usunięte przed usunięciem.|
|**Zmienna środowiskowa errorLevel**<br>Typ danych: Int32|Implementowanie tego parametru, użytkownik może określić poziom błędów do zgłoszenia.|
|**Exclude**<br>Typ danych: Ciąg]|Implementowanie tego parametru, aby użytkownik wykluczyć coś z działania. Aby uzyskać więcej informacji o tym, jak używać filtrów danych wejściowych, zobacz [wprowadzania parametrów filtru](input-filter-parameters.md).|
|**Filtr**<br>Typ danych: Słowo kluczowe|Implementowanie tego parametru, użytkownik może określić filtr, który wybiera zasoby, na którym do wykonania tego działania polecenia cmdlet. Aby uzyskać więcej informacji o tym, jak używać filtrów danych wejściowych, zobacz [wprowadzania parametrów filtru](./input-filter-parameters.md).|
|**Postępuj zgodnie z**<br>Typ danych: SwitchParameter|Implementowanie tego parametru, postęp jest widoczny, jeśli określono parametr.|
|**Force**<br>Typ danych: SwitchParameter|Implementuje ten parametr, aby wskazać, że użytkownik będzie mógł wykonać akcję nawet, jeśli ograniczenia zostaną napotkane, gdy określono parametr. Parametr nie zezwala na zabezpieczenia, aby być narażone na ataki. Na przykład ten parametr umożliwia użytkownikowi zastąpić plik tylko do odczytu.|
|**Obejmują**<br>Typ danych: Ciąg]|Implementowanie tego parametru, użytkownik może zawierać coś w działaniu. Aby uzyskać więcej informacji o tym, jak używać filtrów danych wejściowych, zobacz [wprowadzania parametrów filtru](input-filter-parameters.md).|
|**Przyrostowe**<br>Typ danych: SwitchParameter|Implementowanie tego parametru, aby wskazać, że przetwarzanie odbywa się przyrostowo gdy określono parametr. Na przykład ten parametr umożliwia użytkownikowi wykonywać przyrostowe kopie zapasowe, które wykonują kopie zapasowe plików tylko od czasu ostatniej kopii zapasowej.|
|**InputObject**<br>Typ danych: Obiekt|Implementuje ten parametr, gdy polecenie cmdlet pobiera inne polecenia cmdlet. Podczas definiowania **InputObject** parametru zawsze określać **ValueFromPipeline** — słowo kluczowe, kiedy Deklarujesz **parametru** atrybutu. Aby uzyskać więcej informacji o korzystaniu z filtrów wejściowych, zobacz [wprowadzania parametrów filtru](./input-filter-parameters.md).|
|**Wstaw**<br>Typ danych: SwitchParameter|Implementowanie tego parametru, jeśli parametr jest określony, polecenie cmdlet wstawia element.|
|**Interaktywne**<br>Typ danych: SwitchParameter|Implementowanie tego parametru, polecenie cmdlet działa interaktywnie z użytkownikiem, gdy parametr jest określony.|
|**Interval**<br>Typ danych: Tablica skrótów|Implementowanie tego parametru, użytkownik może określić tabeli mieszania słów kluczowych, która zawiera wartości. W poniższym przykładzie przedstawiono przykładowe wartości dla **interwał** parametru: `-interval @{ResumeScan=15; Retry=3}`.|
|**Dziennik**<br>Typ danych: SwitchParameter|Implementuje inspekcji tego parametru działania polecenia cmdlet, gdy określono parametr.|
|**NoClobber**<br>Typ danych: SwitchParameter|Implementowanie tego parametru, zasób nie zostaną zastąpione, jeśli określono parametr. Ten parametr dotyczy poleceń cmdlet, które tworzyć nowych obiektów, dzięki czemu można zapobiec zastępowaniu istniejących obiektów o tej samej nazwie.|
|**Powiadom**<br>Typ danych: SwitchParameter|Implementowanie tego parametru, użytkownik zostanie powiadomiony, że działanie została zakończona, gdy określono parametr.|
|**NotifyAddress**<br>Typ danych: Adres e-mail|Implementowanie tego parametru, aby użytkownik może określić adres e-mail do wysłania powiadomienia po **powiadamiania** określono parametr.|
|**Zastąp**<br>Typ danych: SwitchParameter|Implementowanie tego parametru, polecenie cmdlet zastępuje wszelkie istniejące dane, gdy określono parametr.|
|**wiersz**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić w wierszu polecenia cmdlet.|
|**cichy**<br>Typ danych: SwitchParameter|Implementowanie tego parametru polecenia cmdlet pomija opinie użytkowników podczas jej działania, gdy określono parametr.|
|**Recurse**<br>Typ danych: SwitchParameter|Implementowanie tego parametru rekursywnie polecenia cmdlet wykonuje swoje działania dotyczące zasobów, gdy parametr jest określony.|
|**Napraw**<br>Typ danych: SwitchParameter|Implementowanie tego parametru, polecenie cmdlet podejmie próbę Popraw coś w stanie uszkodzenia, gdy określono parametr.|
|**RepairString**<br>Typ danych: Ciąg|Implementowanie tego parametru, aby użytkownik może określić ciąg do użycia podczas **naprawy** określono parametr.|
|**Spróbuj ponownie**<br>Typ danych: Int32|Implementuje ten parametr, dzięki czemu użytkownik może określić, ile razy polecenie cmdlet podejmie akcję.|
|**Select**<br>Typ danych: Array — słowo kluczowe|Implementowanie tego parametru, użytkownik może określić tablicę typów elementów.|
|**Stream**<br>Typ danych: SwitchParameter|Implementuje ten parametr, dzięki czemu użytkownik może strumienia wielu obiektów danych wyjściowych przez potok, gdy określono parametr.|
|**Strict**<br>Typ danych: SwitchParameter|Implementowanie tego parametru, aby wszystkie błędy są obsługiwane jako błędy Trwa przerywanie działania, gdy określono parametr.|
|**TempLocation**<br>Typ danych: Ciąg|Ten parametr należy zaimplementować, dzięki czemu użytkownik może określić lokalizację danych tymczasowych, który jest używany podczas działania polecenia cmdlet.|
|**limit czasu**<br>Typ danych: Int32|Implementowanie tego parametru, użytkownik może określić interwał limitu czasu (w milisekundach).|
|**Obetnij**<br>Typ danych: SwitchParameter|Implementowanie tego parametru polecenia cmdlet obetnie swoje działania, gdy określono parametr. Jeśli parametr nie jest określony, polecenie cmdlet wykonuje kolejną akcję.|
|**Sprawdź**<br>Typ danych: SwitchParameter|Implementowanie tego parametru polecenia cmdlet zostanie test, aby ustalić, czy działanie miało miejsce, gdy określono parametr.|
|**Czekaj**<br>Typ danych: SwitchParameter|Implementowanie tego parametru, polecenie cmdlet będzie czekać na dane wejściowe użytkownika przed kontynuowaniem, gdy określono parametr.
|**WaitTime**<br>Typ danych: Int32|Implementowanie tego parametru, aby użytkownik może określić czas trwania (w sekundach), polecenia cmdlet będzie czekać użytkownika danych wejściowych podczas **oczekiwania** określono parametr.|

## <a name="see-also"></a>Zobacz też

[Parametry polecenia cmdlet](./cmdlet-parameters.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)
