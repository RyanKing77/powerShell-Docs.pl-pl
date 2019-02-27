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
ms.openlocfilehash: 32e2b8acf33bc733c5e4cab94a721076ff46225d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849091"
---
# <a name="activity-parameters"></a>Parametry działań

W poniższej tabeli wymieniono nazwy zalecane i funkcje dotyczące parametrów działań.

Dołącz — typ danych: SwitchParameter

Implementowanie tego parametru, użytkownik może dodawać zawartość do końca zasobu, jeśli określono parametr.

Typ danych CaseSensitive: SwitchParameter

Implementuje ten parametr, dzięki czemu użytkownik może wymagać rozróżnianie wielkości liter, jeśli określono parametr.

Typ danych z poleceń: Ciąg

Ten parametr należy zaimplementować, dzięki czemu użytkownik może określić ciąg polecenia do uruchomienia.

Typ danych CompatibleVersion: Obiekt System.Version

Ten parametr należy zaimplementować, dzięki czemu użytkownik może określić semantykę, która polecenie cmdlet musi być zgodny z potrzeby utrzymywania zgodności z poprzednimi wersjami.

Kompresuj — typ danych: SwitchParameter

Implementowanie tego parametru, kompresja danych jest używany, gdy określono parametr.

Kompresuj — typ danych: Słowo kluczowe

Implementowanie tego parametru, użytkownik może określić algorytm kompresji danych.

Ciągłe typ danych: SwitchParameter

Implementowanie tego parametru, dane zostaną przetworzone, dopóki użytkownik kończy działanie polecenia cmdlet, gdy określono parametr. Jeśli parametr nie jest określony, polecenie cmdlet przetwarza wstępnie zdefiniowanych ilości danych i następnie kończy operację.

Utwórz typ danych: SwitchParameter

Implementowanie tego parametru, aby wskazać, czy zasób został utworzony, jeśli jeden nie już istnieć, gdy określono parametr.

Usuń typ danych: SwitchParameter

Implementowanie tego parametru, aby zasoby zostaną usunięte po zakończeniu jego działania polecenia cmdlet, jeśli określono parametr.

Opróżnij — typ danych: SwitchParameter

Implementowanie tego parametru, aby wskazać, że elementy robocze oczekujących są przetwarzane przed polecenia cmdlet przetwarza nowe dane, gdy określono parametr. Jeśli parametr nie jest określony, elementy robocze są przetwarzane od razu.

ERASE — typ danych: Int32

Implementowanie tego parametru, użytkownik może określić liczbę przypadków, gdy zasób jest usunięte przed usunięciem.

Typ danych parametru ErrorLevel: Int32

Implementowanie tego parametru, użytkownik może określić poziom błędów do zgłoszenia.

Wyklucz — typ danych: Ciąg]

Implementowanie tego parametru, aby użytkownik wykluczyć coś z działania. Aby uzyskać więcej informacji o tym, jak używać filtrów danych wejściowych, zobacz [wprowadzania parametrów filtru](./input-filter-parameters.md).

Filtruj typ danych: Słowo kluczowe

Implementowanie tego parametru, użytkownik może określić filtr, który wybiera zasoby, na którym do wykonania tego działania polecenia cmdlet. Aby uzyskać więcej informacji o tym, jak używać filtrów danych wejściowych, zobacz [wprowadzania parametrów filtru](./input-filter-parameters.md).

Postępuj zgodnie z typem danych: SwitchParameter

Implementowanie tego parametru, postęp jest widoczny, jeśli określono parametr.

Wymusić typ danych: SwitchParameter

Implementuje ten parametr, aby wskazać, że użytkownik będzie mógł wykonać akcję nawet, jeśli ograniczenia zostaną napotkane, gdy określono parametr. Parametr nie zezwala na zabezpieczenia, aby być narażone na ataki. Na przykład ten parametr umożliwia użytkownikowi zastąpić plik tylko do odczytu.

Obejmują typ danych: Ciąg]

Implementowanie tego parametru, użytkownik może zawierać coś w działaniu. Aby uzyskać więcej informacji o tym, jak używać filtrów danych wejściowych, zobacz [wprowadzania parametrów filtru](./input-filter-parameters.md).

Typ danych przyrostowe: SwitchParameter

Implementowanie tego parametru, aby wskazać, że przetwarzanie odbywa się przyrostowo gdy określono parametr. Na przykład ten parametr umożliwia użytkownikowi wykonywać przyrostowe kopie zapasowe, które wykonują kopie zapasowe plików tylko od czasu ostatniej kopii zapasowej.

Typ danych InputObject: Obiekt

Implementuje ten parametr, gdy polecenie cmdlet pobiera inne polecenia cmdlet. Podczas definiowania `InputObject` parametru zawsze określać `ValueFromPipeline` — słowo kluczowe, kiedy Deklarujesz **parametru** atrybutu. Aby uzyskać więcej informacji o korzystaniu z filtrów wejściowych, zobacz [wprowadzania parametrów filtru](./input-filter-parameters.md).

Wstaw — typ danych: SwitchParameter

Implementowanie tego parametru, jeśli parametr jest określony, polecenie cmdlet wstawia element.

Typ danych: SwitchParameter

Implementowanie tego parametru, polecenie cmdlet działa interaktywnie z użytkownikiem, gdy parametr jest określony.

Typ danych interwału: Tablica skrótów

Implementowanie tego parametru, użytkownik może określić tabeli mieszania słów kluczowych, która zawiera wartości. W poniższym przykładzie przedstawiono przykładowe wartości dla `Interval` parametru: `-interval @{ResumeScan=15; Retry=3}`.

Typ danych dziennika: SwitchParameter

Implementuje inspekcji tego parametru działania polecenia cmdlet, gdy określono parametr.

Typ danych NoClobber: SwitchParameter

Implementowanie tego parametru, zasób nie zostaną zastąpione, jeśli określono parametr. Ten parametr dotyczy poleceń cmdlet, które tworzyć nowych obiektów, dzięki czemu można zapobiec zastępowaniu istniejących obiektów o tej samej nazwie.

Powiadom — typ danych: SwitchParameter

Implementowanie tego parametru, użytkownik zostanie powiadomiony, że działanie została zakończona, gdy określono parametr.

Typ danych NotifyAddress: Adres e-mail

Implementowanie tego parametru, aby użytkownik może określić adres e-mail do wysłania powiadomienia po `Notify` określono parametr.

Zastąpienie — typ danych: SwitchParameter

Implementowanie tego parametru, polecenie cmdlet zastępuje wszelkie istniejące dane, gdy określono parametr.

Monituj — typ danych: Ciąg

Implementowanie tego parametru, użytkownik może określić w wierszu polecenia cmdlet.

Quiet — typ danych: SwitchParameter

Implementowanie tego parametru polecenia cmdlet pomija opinie użytkowników podczas jej działania, gdy określono parametr.

Recurse — typ danych: SwitchParameter

Implementowanie tego parametru rekursywnie polecenia cmdlet wykonuje swoje działania dotyczące zasobów, gdy parametr jest określony.

Dane naprawa, wpisz: SwitchParameter

Implementowanie tego parametru, polecenie cmdlet podejmie próbę Popraw coś w stanie uszkodzenia, gdy określono parametr.

Typ danych RepairString: Ciąg

Implementowanie tego parametru, aby użytkownik może określić ciąg do użycia podczas `Repair` określono parametr.

Ponów próbę — typ danych: Int32

Implementuje ten parametr, dzięki czemu użytkownik może określić, ile razy polecenie cmdlet podejmie akcję.

Wybierz typ danych: Array — słowo kluczowe

Implementowanie tego parametru, użytkownik może określić tablicę typów elementów.

Typ danych Stream: SwitchParameter

Implementuje ten parametr, dzięki czemu użytkownik może strumienia wielu obiektów danych wyjściowych przez potok, gdy określono parametr.

Typ danych: SwitchParameter

Implementowanie tego parametru, aby wszystkie błędy są obsługiwane jako błędy Trwa przerywanie działania, gdy określono parametr.

Typ danych TempLocation: Ciąg

Ten parametr należy zaimplementować, dzięki czemu użytkownik może określić lokalizację danych tymczasowych, który jest używany podczas działania polecenia cmdlet.

Typ danych limit czasu: Int32

Implementowanie tego parametru, użytkownik może określić interwał limitu czasu (w milisekundach).

Obciąć typ danych: SwitchParameter

Implementowanie tego parametru polecenia cmdlet obetnie swoje działania, gdy określono parametr. Jeśli parametr nie jest określony, polecenie cmdlet wykonuje kolejną akcję.

Sprawdź typ danych: SwitchParameter

Implementowanie tego parametru polecenia cmdlet zostanie test, aby ustalić, czy działanie miało miejsce, gdy określono parametr.

Poczekaj na typ danych: SwitchParameter

Implementowanie tego parametru, polecenie cmdlet będzie czekać na dane wejściowe użytkownika przed kontynuowaniem, gdy określono parametr.

Typ danych; czas oczekiwania: Int32

Implementowanie tego parametru, aby użytkownik może określić czas trwania (w sekundach), polecenia cmdlet będzie czekać użytkownika danych wejściowych podczas `Wait` określono parametr.

## <a name="see-also"></a>Zobacz też

[Parametry polecenia cmdlet](./cmdlet-parameters.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)
