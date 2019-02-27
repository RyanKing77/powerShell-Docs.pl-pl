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
ms.openlocfilehash: f58e8ecb67238939e90d4c5650bddd03da3c9409
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851751"
---
# <a name="resource-parameters"></a>Parametry zasobów

W poniższej tabeli wymieniono nazwy zalecane i funkcje dotyczące parametrów zasobów. Dla tych parametrów zasobów może być zestaw, który zawiera klasę polecenia cmdlet lub aplikacji hosta, na którym uruchomiono polecenie cmdlet.

Typ danych aplikacji: Ciąg

Implementowanie tego parametru, użytkownik może określić aplikację.

Typ zestawu danych: Ciąg

Implementowanie tego parametru, użytkownik może określić zestaw.

Typ danych atrybutu: Ciąg

Implementowanie tego parametru, użytkownik może określić atrybut.

Typ danych klasy: Ciąg

Implementowanie tego parametru, użytkownik może określić klasy programu Microsoft .NET Framework.

Typ danych klastra: Ciąg

Implementowanie tego parametru, użytkownik może określić klastra.

Typ danych kultury: Ciąg

Implementowanie tego parametru, użytkownik może określić kulturę, w którym należy uruchomić polecenie cmdlet.

Typ danych domeny: Ciąg

Implementowanie tego parametru, użytkownik może określić nazwę domeny.

Typ danych dysku: Ciąg

Implementowanie tego parametru, użytkownik może określić nazwę dysku.

Typ danych zdarzenia: Ciąg

Implementowanie tego parametru, użytkownik może określić nazwą zdarzenia.

Typ danych interfejsu: Ciąg

Implementowanie tego parametru, użytkownik może określić nazwę interfejsu sieciowego.

Typ danych adres IP: Ciąg

Implementowanie tego parametru, użytkownik może określić adresu IP.

Typ danych zadania: Ciąg

Implementowanie tego parametru, użytkownik może określić zadania.

Typ danych LiteralPath: Ciąg

Implementowanie tego parametru, użytkownik może określić ścieżkę do zasobu, gdy symbole wieloznaczne nie są obsługiwane. (Użyj `Path` parametrem w przypadku symbole wieloznaczne są obsługiwane.)

Typ danych dla komputerów Mac: Ciąg

Implementowanie tego parametru, użytkownik może określić adres kontrolera (MAC) dostępu do nośnika.

Typ danych ParentId: Ciąg

Implementowanie tego parametru, użytkownik może określić identyfikatorem elementu nadrzędnego.

Typ danych ścieżki: Ciąg, ciąg]

Implementuje ten parametr, dzięki czemu użytkownik może wskazać ścieżki do zasobu, gdy symbole wieloznaczne są obsługiwane. (Użyj `LiteralPath` parametrem w przypadku symbole wieloznaczne nie są obsługiwane.)

Firma Microsoft zaleca tworzenie tego parametru, tak aby obsługuje składnię pełna "dostawca: ścieżka" używana przez dostawców. Firma Microsoft zaleca, Opracuj go tak, aby go pracuje z dostawcami tyle, jak to możliwe.

Typ danych portu: Liczba całkowita, ciąg

Implementowanie tego parametru, użytkownik może określić wartość całkowitą dla sieci lub wartości ciągu, takich jak "biztalk" w przypadku innych typów portu.

Typ danych drukarki: Liczba całkowita, ciąg

Implementowanie tego parametru, użytkownik może określić drukarki dla polecenia cmdlet do użycia.

Rozmiar danych, wpisz: Int32

Implementowanie tego parametru, użytkownik może określić rozmiar.

Typ identyfikatora TID danych: Ciąg

Implementowanie tego parametru, użytkownik może określić identyfikator transakcji (TID), polecenia cmdlet.

Dane typu: Ciąg

Implementowanie tego parametru, użytkownik może określić typu zasobu, na którym będą wykonywane.

Typ danych adresu URL: Ciąg

Implementowanie tego parametru, użytkownik może określić Uniform Resource Locator (URL).

Typ danych użytkownika: Ciąg

Implementowanie tego parametru, użytkownik może określić jego nazwę lub nazwę innego użytkownika.

## <a name="see-also"></a>Zobacz też

[Parametry polecenia cmdlet](./cmdlet-parameters.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)
