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
ms.openlocfilehash: 5b1f093de5db364ac806e58c4ed8dbf2948cb6c6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068236"
---
# <a name="date-and-time-parameters"></a>Parametry daty i godziny

W poniższej tabeli wymieniono nazwy zalecane i funkcje dotyczące parametrów, które obsługują informacji daty i godziny. Parametry Data i godzina zazwyczaj są używane do rejestrowania, gdy coś, co zostanie utworzony lub uzyskać dostępu do.

|Parametr|Funkcja|
|---|---|
|**Dostęp do**<br>Typ danych: SwitchParameter|Implementowanie tego parametru, jeśli jest określony, polecenie cmdlet będzie działać na zasoby, które były używane oparte na datę i godzinę, określonym przez **przed** i **po** parametrów. Jeśli ten parametr jest określony, **utworzono** i **zmodyfikowane** parametry muszą być nie można określić.|
|**Po**<br>Typ danych: DateTime|Implementuje ten parametr, aby określić datę i godzinę, po którym użyto polecenia cmdlet. Dla **po** parametru, aby działać, musi mieć również polecenia cmdlet **Accessed**, **utworzono**, lub **zmodyfikowane** parametru. A ten parametr musi być równa **true** po nosi nazwę polecenia cmdlet.|
|**Przed**<br>Typ danych: DateTime|Implementuje ten parametr, aby określić datę i godzinę, przed którym użyto polecenia cmdlet. Dla **przed** parametru, aby działać, musi mieć również polecenia cmdlet **Accessed**, **utworzono**, lub **zmodyfikowane** parametru. A ten parametr musi być równa **true** po nosi nazwę polecenia cmdlet.|
|**Utworzone**<br>Typ danych: SwitchParameter|Implementowanie tego parametru, gdy jest określony, polecenie cmdlet będzie działać na zasobach, które zostały utworzone na podstawie daty i czasu określonego przez **przed** i **po** parametrów. Jeśli ten parametr jest określony, **Accessed** i **zmodyfikowane** parametrów nie może być określony.|
|**Dokładny**<br>Typ danych: SwitchParameter|Implementowanie tego parametru, gdy określono wyrażenie zasobu musi być zgodny nazwy zasobu. Jeśli nie określono parametru termin zasobów i nazwy nie powinny być dokładnie.|
|**Zmodyfikowane**<br>Typ danych: DateTime|Implementowanie tego parametru, gdy jest określony, polecenie cmdlet będzie działać na zasobach, które zostały zmienione na podstawie daty i czas określony przez **przed** i **po** parametrów. Jeśli ten parametr jest określony, **Accessed** i **utworzono** parametrów nie może być określony.|
## <a name="see-also"></a>Zobacz też

[Parametry polecenia cmdlet](./cmdlet-parameters.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)
