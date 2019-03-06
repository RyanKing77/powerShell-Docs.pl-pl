---
title: RunSpace03 (C#) przykładowego kodu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 0e80f4d850a7c6dc044526a56b92f16eea4040b5
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429911"
---
# <a name="runspace03-c-code-sample"></a>Przykładowy kod RunSpace03 (C#)

Oto C# źródła kodu dla aplikacji konsoli, opisanego w [tworzenia działa konsola aplikacji czy określony skrypt](http://msdn.microsoft.com/en-us/a93e6006-36db-4bcc-b9da-c5bebf4ffd68). W tym przykładzie użyto [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) klasy do uruchomienia skryptu, który pobiera przetwarzania informacji przy użyciu listy nazw procesów przekazywane do skryptu. Pokazuje, jak przekazać obiekty wejściowe do skryptu oraz jak pobierać obiektów błędu, a także obiekty danych wyjściowych.

> [!NOTE]
> Możesz pobrać C# pliku źródłowego (runspace03.cs) omawiany w tym przykładzie za pomocą programu Microsoft Windows oprogramowania Development Kit dla Windows Vista i składników środowiska wykonawczego programu Microsoft .NET Framework 3.0. Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Pliki pobrane źródło są dostępne w  **\<przykłady programu PowerShell >** katalogu.

## <a name="code-sample"></a>Przykładowy kod

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a>Zobacz też

[Windows PowerShell przewodnik](./windows-powershell-programmer-s-guide.md)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)