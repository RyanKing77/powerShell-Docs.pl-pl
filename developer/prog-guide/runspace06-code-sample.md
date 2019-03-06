---
title: Przykładowy kod RunSpace06 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d71f86d5-eb62-4b16-aa95-5fd3f314ffd3
caps.latest.revision: 6
ms.openlocfilehash: d0330f082262b68486a582ed95c7a520be1e184c
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429537"
---
# <a name="runspace06-code-sample"></a>Przykładowy kod RunSpace06

Poniżej przedstawiono kod źródłowy dla przykładowych Runspace06 opisanego w [konfigurowania obszaru działania, za pomocą przystawki programu PowerShell Windows](http://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83). Ta przykładowa aplikacja tworzy obszar działania, w oparciu o przystawki programu Windows PowerShell, który jest następnie używany do uruchomienia potoku za pomocą jednego polecenia. Aby to zrobić, aplikacja tworzy informacji o konfiguracji obszaru działania, tworzy obszar działania, tworzy potok z jednym poleceniem i następnie uruchamia potok.

> [!NOTE]
> Możesz pobrać C# pliku źródłowego (runspace06.cs) przy użyciu Windows oprogramowania Development Kit dla Windows Vista i składników środowiska wykonawczego programu Microsoft .NET Framework 3.0. Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Pliki pobrane źródło są dostępne w  **\<przykłady programu PowerShell >** katalogu.

## <a name="code-sample"></a>Przykładowy kod

[!code-csharp[Runspace06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs#L11-L85 "Runspace06.cs")]

## <a name="see-also"></a>Zobacz też

[Windows PowerShell przewodnik](./windows-powershell-programmer-s-guide.md)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)