---
title: Przykładowy kod RunSpace08 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f286201-8a02-4b00-9a2c-1b833ccdbdbf
caps.latest.revision: 7
ms.openlocfilehash: ec6aae544eafea1dedc1379dab00beeed2c7c436
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734915"
---
# <a name="runspace08-code-sample"></a>Przykładowy kod RunSpace08

Poniżej przedstawiono kod źródłowy dla przykładowych Runspace08 opisanego w [tworzyć konsoli aplikacji, dodaje parametry do polecenia](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba). Ta przykładowa aplikacja tworzy obszar działania, tworzy potok, dodaje dwa polecenia do potoku, dodaje dwa parametry do drugiego polecenia i następnie uruchamia potok. Polecenia, które są dodawane do potoku znajdują się `Get-Process` i `Sort-Object` polecenia cmdlet.

## <a name="code-sample"></a>Przykładowy kod

[!code-csharp[Runspace08.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a>Zobacz też

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)