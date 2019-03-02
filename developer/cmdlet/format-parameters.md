---
title: Format parametrów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251187"
---
# <a name="format-parameters"></a>Parametry formatu

W poniższej tabeli wymieniono nazwy zalecane i funkcje dotyczące parametrów, które są używane do formatowania lub do generowania danych.

|Parametr|Funkcja|
|---|---|
|**As**<br>Typ danych: Słowo kluczowe|Implementowanie tego parametru, aby określić format danych wyjściowych polecenia cmdlet. Możliwe wartości można na przykład tekstu lub skryptu.|
|**Binary**<br>Typ danych: SwitchParameter|Implementowanie tego parametru, aby wskazać, że polecenie cmdlet obsługuje wartości binarnych.|
|**Kodowanie**<br>Typ danych: Słowo kluczowe|Implementowanie tego parametru, aby określić typu kodowania, która jest obsługiwana. Możliwe wartości można na przykład ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, bajt i ciąg.|
|**Nowy wiersz**<br>Typ danych: SwitchParameter|Implementowanie tego parametru i znaki nowego wiersza są obsługiwane, jeśli parametr jest określony.|
|**ShortName**<br>Typ danych: SwitchParameter|Implementowanie tego parametru, krótkich nazw są obsługiwane, jeśli parametr jest określony.|
|**Szerokość**<br>Typ danych: Int32|Implementowanie tego parametru, użytkownik może określić szerokość urządzenia wyjściowego.|
|**OPAKOWYWANIE**<br>Typ danych: SwitchParameter|Implementowanie tego parametru, zawijania tekstu jest obsługiwana, gdy określono parametr.|
## <a name="see-also"></a>Zobacz też

[Parametry polecenia cmdlet](./cmdlet-parameters.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)
