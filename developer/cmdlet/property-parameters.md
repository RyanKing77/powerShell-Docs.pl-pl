---
title: Parametry właściwości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d17e0d66-42ea-4e4c-a85b-3ca09b146492
caps.latest.revision: 6
ms.openlocfilehash: cc0742b86a7a36e5712707c077fd1952691f3f4b
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251425"
---
# <a name="property-parameters"></a>Parametry właściwości

W poniższej tabeli wymieniono nazwy zalecane i funkcje dotyczące parametrów właściwości.

|Parametr|Funkcja|
|---|---|
|**Liczba**<br>Typ danych: Int32|Implementowanie tego parametru, użytkownik może określić liczbę obiektów, które mają być przetwarzane.|
|**Opis**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić opis dla zasobu.|
|**From**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić obiekt odwołania, aby uzyskać informacji o.|
|**Identyfikator**<br>Typ danych: Zasób zależny|Implementowanie tego parametru, użytkownik może określić identyfikator zasobu.|
|**Dane wejściowe**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić specyfikacji pliku wejściowego.|
|**Lokalizacja**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić lokalizację zasobu.|
|**LogName**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić nazwę pliku dziennika, aby przetworzyć lub użycia.|
|**Nazwa**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić nazwę zasobu.|
|**Dane wyjściowe**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić pliku wyjściowego.|
|**Właściciel**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić nazwę właściciela zasobu.|
|**Property**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić nazwę lub nazwy właściwości do użycia.|
|**Przyczyna**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić, dlaczego to polecenie cmdlet jest wywoływana.|
|**Regex**<br>Typ danych: SwitchParameter|Implementowanie tego parametru, wyrażenia regularne są używane, gdy określono parametr. Jeśli ten parametr jest określony, symbole wieloznaczne nie są rozpoznawane.|
|**szybkość**<br>Typ danych: Int32|Implementowanie tego parametru, użytkownik może określić szybkość transmisji. Użytkownik ustawia szybkość zasobu tego parametru.|
|**State**<br>Typ danych: Array — słowo kluczowe|Implementowanie tego parametru, użytkownik może określić nazwy stanów, takich jak KEYDOWN.|
|**Wartość**<br>Typ danych: Obiekt|Implementowanie tego parametru, użytkownik może określić wartość, aby zapewnić do polecenia cmdlet.|
|**Wersja**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić wersji właściwości.|

## <a name="see-also"></a>Zobacz też

[Parametry polecenia cmdlet](./cmdlet-parameters.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)
