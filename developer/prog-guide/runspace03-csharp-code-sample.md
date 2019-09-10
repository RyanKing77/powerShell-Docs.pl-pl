---
title: Przykład koduC#RunSpace03 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 9afdb97b8ae2919f091ca5bacccedbe37c2e1584
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848031"
---
# <a name="runspace03-c-code-sample"></a>Przykładowy kod RunSpace03 (C#)

Poniżej znajduje się C# kod źródłowy aplikacji konsolowej opisanej w temacie "Tworzenie aplikacji konsolowej, która uruchamia określony skrypt". Ten przykład używa klasy [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) do wykonywania skryptu pobierającego informacje o procesie przy użyciu listy nazw procesów przekazaną do skryptu. Pokazuje sposób przekazywania obiektów wejściowych do skryptu i sposobu pobierania obiektów błędów oraz obiektów wyjściowych.

> [!NOTE]
> Możesz pobrać plik C# źródłowy (runspace03.cs) dla tego przykładu, korzystając z zestawu Microsoft Windows Software Development Kit dla systemów Windows Vista i Microsoft .NET Framework 3,0 Runtime. Aby uzyskać instrukcje dotyczące pobierania, zobacz [jak zainstalować program Windows PowerShell i pobrać zestaw SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
> Pobrane pliki źródłowe są dostępne w  **\<przykładach programu PowerShell >** Directory.

## <a name="code-sample"></a>Przykładowy kod

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a>Zobacz też

[Przewodnik programisty programu Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)