---
title: Parametry zasobu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 460c43aa-f5c5-4a1a-a6f2-5e07db143de1
caps.latest.revision: 5
ms.openlocfilehash: 9752570e5c997ef4da56a08df14f39b77ba37a4a
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251204"
---
# <a name="resource-parameters"></a>Parametry zasobów

W poniższej tabeli wymieniono nazwy zalecane i funkcje dotyczące parametrów zasobów. Dla tych parametrów zasobów może być zestaw, który zawiera klasę polecenia cmdlet lub aplikacji hosta, na którym uruchomiono polecenie cmdlet.

|Parametr|Funkcja|
|---|---|
|**Aplikacja**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić aplikację.|
|**Zestaw**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić zestaw.|
|**Atrybut**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić atrybut.|
|**Class**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić klasy programu Microsoft .NET Framework.|
|**Klastra**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić klastra.|
|**Kultury**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić kulturę, w którym należy uruchomić polecenie cmdlet.|
|**Domeny**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić nazwę domeny.|
|**Dysk**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić nazwę dysku.|
|**Event**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić nazwą zdarzenia.|
|**Interface**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić nazwę interfejsu sieciowego.|
|**IpAddress**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić adresu IP.|
|**Zadania**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić zadania.|
|**LiteralPath**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić ścieżkę do zasobu, gdy symbole wieloznaczne nie są obsługiwane. (Użyj **ścieżki** parametrem w przypadku symbole wieloznaczne są obsługiwane.)|
|**Mac**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić adres kontrolera (MAC) dostępu do nośnika.|
|**ParentId**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić identyfikatorem elementu nadrzędnego.|
|**Path**<br>Typ danych: Ciąg, ciąg]|Implementuje ten parametr, dzięki czemu użytkownik może wskazać ścieżki do zasobu, gdy symbole wieloznaczne są obsługiwane. (Użyj **LiteralPath** parametrem w przypadku symbole wieloznaczne nie są obsługiwane.) Firma Microsoft zaleca tworzenie tego parametru, więc, że obsługuje ona pełnego `provider:path` składnią używaną przez dostawców. Firma Microsoft zaleca, Opracuj go tak, aby go pracuje z dostawcami tyle, jak to możliwe.|
|**Port**<br>Typ danych: Liczba całkowita, ciąg|Implementowanie tego parametru, użytkownik może określić wartość całkowitą dla sieci lub wartości ciągu, takich jak "biztalk" w przypadku innych typów portu.|
|**Drukarki**<br>Typ danych: Liczba całkowita, ciąg|Implementowanie tego parametru, użytkownik może określić drukarki dla polecenia cmdlet do użycia.|
|**Rozmiar**<br>Typ danych: Int32|Implementowanie tego parametru, użytkownik może określić rozmiar.|
|**IDENTYFIKATORA TID**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić identyfikator transakcji (TID), polecenia cmdlet.|
|**Typ**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić typu zasobu, na którym będą wykonywane.|
|**Adres URL**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić Uniform Resource Locator (URL).|
|**Użytkownik**<br>Typ danych: Ciąg|Implementowanie tego parametru, użytkownik może określić jego nazwę lub nazwę innego użytkownika.|

## <a name="see-also"></a>Zobacz też

[Parametry polecenia cmdlet](./cmdlet-parameters.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)
