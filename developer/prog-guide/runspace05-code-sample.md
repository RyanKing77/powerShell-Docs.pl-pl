---
title: Przykładowy kod RunSpace05 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: b16ee45383059c52ce3433699c6b8d2120992431
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081346"
---
# <a name="runspace05-code-sample"></a>Przykładowy kod RunSpace05

Poniżej przedstawiono kod źródłowy przykładowej Runspace05 opisaną w [konfigurowania obszaru działania przy użyciu RunspaceConfiguration](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2). W tym przykładzie przedstawiono sposób tworzenia informacji o konfiguracji obszaru działania, Utwórz obszar działania, tworzenie potoku za pomocą jednego polecenia, a następnie wykonywania potoku. Polecenia, który jest wykonywany jest `Get-Process` polecenia cmdlet.

> [!NOTE]
> Możesz pobrać C# pliku źródłowego (runspace05.cs) przy użyciu programu Microsoft Windows oprogramowania Development Kit dla Windows Vista i składników środowiska wykonawczego programu Microsoft .NET Framework 3.0. Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Pliki pobrane źródło są dostępne w  **\<przykłady programu PowerShell >** katalogu.

## <a name="code-sample"></a>Przykładowy kod

[!code-csharp[Runspace05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a>Zobacz też

[Windows PowerShell przewodnik](./windows-powershell-programmer-s-guide.md)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)