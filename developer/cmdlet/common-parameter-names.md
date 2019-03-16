---
title: Nazwy wspólnych parametrów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0db9f54c-4014-4450-9e81-c9f5fe562a0e
caps.latest.revision: 12
ms.openlocfilehash: c65deeda6b2ef1b52de55035dc606259a7f2d232
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059664"
---
# <a name="common-parameter-names"></a>Typowe nazwy parametrów

Parametry opisane w tym temacie są określane jako *wspólnych parametrów*. One są dodawane do poleceń cmdlet w czasie wykonywania programu Windows PowerShell i nie może być zadeklarowana przy użyciu polecenia cmdlet.

> [!NOTE]
> Te parametry są również dodawane do polecenia cmdlet dostawcy i funkcje, które są oznaczone za pomocą `CmdletBinding` atrybutu.

## <a name="general-common-parameters"></a>Ogólne typowych parametrów

Następujące parametry są dodawane do wszystkich poleceń cmdlet i można uzyskać dostęp po każdym uruchomieniu polecenia cmdlet. Te parametry są definiowane przez [System.Management.Automation.Internal.Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters) klasy.

### <a name="debug-alias-db"></a>Debugowanie (alias: bazy danych)

Typ danych: SwitchParameter

Ten parametr określa, czy debugowanie na poziomie programisty wiadomości, które mogą być wyświetlane w wierszu polecenia. Te komunikaty są przeznaczone do rozwiązywania problemów dla działania polecenia cmdlet i są generowane przez wywołania [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) metody. Komunikaty debugowania musi być lokalizowany.

### <a name="erroraction-alias-ea"></a>ErrorAction (alias: atrybutów rozszerzonych)

Typ danych: Wyliczanie

Ten parametr określa, jakie działania powinny zostać wykonane po wystąpieniu błędu. Możliwe wartości dla tego parametru są definiowane przez [System.Management.Automation.Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference) wyliczenia.

### <a name="errorvariable-alias-ev"></a>ErrorVariable (alias: weryfikacją)

Typ danych: Ciąg

Ten parametr określa zmienną, w której chcesz umieścić obiekty, gdy wystąpi błąd. Aby dołączyć do tej zmiennej, należy użyć +*nazwa_zmiennej* zamiast czyszczenie i ustawienie zmiennej.

### <a name="outvariable-alias-ov"></a>OutVariable (alias: ov)

Typ danych: Ciąg

Ten parametr określa zmienną, w którym ma zostać umieszczony wyjściowy obiektów wygenerowanych danych wyjściowych polecenia cmdlet. Aby dołączyć do tej zmiennej, należy użyć +*nazwa_zmiennej* zamiast czyszczenie i ustawienie zmiennej.

### <a name="outbuffer-alias-ob"></a>OutBuffer (alias: ob)

Typ danych: Int32

Ten parametr określa liczbę obiektów do przechowywania w buforze danych wyjściowych, zanim wszystkie obiekty są przekazywane w dół do potoku. Domyślnie obiekty są przekazywane bezpośrednio w dół do potoku.

### <a name="verbose-alias-vb"></a>Pełne (alias: vb)

Typ danych: SwitchParameter

Ten parametr określa, czy polecenie cmdlet zapisuje objaśnienia komunikatów, które mogą być wyświetlane w wierszu polecenia. Te komunikaty są przeznaczone do zapewnienia dodatkowej pomocy dla użytkownika i są generowane przez wywołania [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) metody.

### <a name="warningaction-alias-wa"></a>WarningAction (alias: wa)

Typ danych: Wyliczanie

Ten parametr określa, jakie działanie powinno mieć miejsce, gdy polecenie cmdlet zapisuje komunikat ostrzegawczy. Możliwe wartości dla tego parametru są definiowane przez [System.Management.Automation.Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference) wyliczenia.

### <a name="warningvariable-alias-wv"></a>WarningVariable (alias: wv)

Typ danych: Ciąg

Ten parametr określa zmienną, w którym można zapisywać komunikaty ostrzegawcze. Aby dołączyć do tej zmiennej, należy użyć +*nazwa_zmiennej* zamiast czyszczenie i ustawienie zmiennej.

## <a name="risk-mitigation-parameters"></a>Parametry ograniczenia ryzyka

Następujące parametry są dodawane do poleceń cmdlet, które zażąda potwierdzenia przed wykonują swoje działania. Aby uzyskać więcej informacji na temat żądania potwierdzenia zobacz [żądania potwierdzenia](./requesting-confirmation-from-cmdlets.md). Te parametry są definiowane przez [System.Management.Automation.Internal.Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters) klasy.

### <a name="confirm-alias-cf"></a>Potwierdzenie (alias: cf)

Typ danych: SwitchParameter

Ten parametr określa, czy polecenie cmdlet wyświetli monit z pytaniem, czy użytkownik jest się upewnić, że chce kontynuować.

### <a name="whatif-alias-wi"></a>WhatIf (alias: wi)

Typ danych: SwitchParameter

Ten parametr określa, czy polecenie cmdlet zapisuje komunikat, który opisuje skutki uruchomienie tego polecenia cmdlet bez rzeczywistego wykonania żadnych czynności.

## <a name="transaction-parameters"></a>Parametry transakcji

Następujący parametr jest dodawany do poleceń cmdlet, które obsługuje transakcji. Te parametry są definiowane przez [System.Management.Automation.Internal.Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters) klasy.

### <a name="usetransaction-alias-usetx"></a>UseTransaction (alias: usetx)

Typ danych: SwitchParameter

Ten parametr określa, czy przeprowadzić jego działania polecenia cmdlet będą używać bieżącej transakcji.

## <a name="see-also"></a>Zobacz też

[System.Management.Automation.Internal.Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters)

[System.Management.Automation.Internal.Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters)

[System.Management.Automation.Internal.Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)
