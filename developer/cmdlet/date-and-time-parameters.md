---
title: Data i godzina parametry | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71da921b-7c32-4155-b2f8-b19f30ec774d
caps.latest.revision: 7
ms.openlocfilehash: 49f6c667b0fd9678586559af39a33f982de0a68c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846711"
---
# <a name="date-and-time-parameters"></a>Parametry daty i godziny

W poniższej tabeli wymieniono nazwy zalecane i funkcje dotyczące parametrów, które obsługują informacji daty i godziny. Parametry Data i godzina zazwyczaj są używane do rejestrowania, gdy coś, co zostanie utworzony lub uzyskać dostępu do.

Dostęp do danych, wpisz: SwitchParameter

Implementowanie tego parametru, jeśli jest określony, polecenie cmdlet będzie działać na zasoby, które były używane oparte na datę i godzinę, określonym przez `Before` i `After` parametrów.

Jeśli ten parametr jest określony, `Created` i `Modified` parametry muszą być nie można określić.

Po typ danych: DateTime

Implementuje ten parametr, aby określić datę i godzinę, po którym użyto polecenia cmdlet. Dla `After` parametru, aby działać, musi mieć również polecenia cmdlet `Accessed`, `Created`, lub `Modified` parametru. A ten parametr musi być równa `true` po nosi nazwę polecenia cmdlet.

Przed typ danych: DateTime

Implementuje ten parametr, aby określić datę i godzinę, przed którym użyto polecenia cmdlet. Dla `Before` parametru, aby działać, musi mieć również polecenia cmdlet `Accessed`, `Created`, lub `Modified` parametru. A ten parametr musi być równa `true` po nosi nazwę polecenia cmdlet.

Utworzony typ danych: SwitchParameter

Implementowanie tego parametru, gdy jest określony, polecenie cmdlet będzie działać na zasobach, które zostały utworzone na podstawie daty i czasu określonego przez `Before` i `After` parametrów.

Jeśli ten parametr jest określony, `Accessed` i `Modified` parametrów nie może być określony.

Dokładne dane, wpisz: SwitchParameter

Implementowanie tego parametru, gdy określono wyrażenie zasobu musi być zgodny nazwy zasobu. Jeśli nie określono parametru termin zasobów i nazwy nie powinny być dokładnie.

Zmodyfikowane dane, wpisz: DateTime

Implementowanie tego parametru, gdy jest określony, polecenie cmdlet będzie działać na zasobach, które zostały zmienione na podstawie daty i czas określony przez `Before` i `After` parametrów.

Jeśli ten parametr jest określony, `Accessed` i `Created` parametrów nie może być określony.

## <a name="see-also"></a>Zobacz też

[Parametry polecenia cmdlet](./cmdlet-parameters.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)
