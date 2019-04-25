---
title: Przykładowy kod RunSpace09 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 136e451f-767b-42e0-bd6f-6486693abd5e
caps.latest.revision: 6
ms.openlocfilehash: e21ef8685598db9a1ae0fcd86051386af526f2a5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081227"
---
# <a name="runspace09-code-sample"></a>Przykładowy kod RunSpace09

Poniżej przedstawiono kod źródłowy dla przykładowych Runspace09 opisanego w [tworzenia konsoli aplikacji, wywołuje potok asynchronicznie](http://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47). Ta przykładowa aplikacja tworzy i otwiera obszar działania, tworzy i asynchronicznie wywołuje potok, a następnie używa potoku zdarzeń w celu asynchronicznego przetwarzania skryptu. Skrypt, który jest uruchamiany przez tę aplikację tworzy liczb całkowitych od 1 do 10 w 0,5 sekund (500 ms).

## <a name="code-sample"></a>Przykładowy kod

[!code-csharp[Runspace09.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs#L11-L113 "Runspace09.cs")]

## <a name="see-also"></a>Zobacz też

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)