---
title: Przykładowe PowerShell02 Windows | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: 89ad17257ebac56105a93672317a149515e80d32
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082519"
---
# <a name="windows-powershell02-sample"></a>Przykład Windows PowerShell02

Niniejszy przykład pokazuje sposób uruchamiania poleceń asynchronicznie przy użyciu obszary działania puli obszaru działania. Przykład generuje listę poleceń, a następnie uruchomić tych poleceń, podczas gdy aparatu programu Windows PowerShell otwiera obszarem działania z puli, gdy jest to konieczne.

## <a name="requirements"></a>Wymagania

- Ten przykładowy skrypt wymaga programu Windows PowerShell 2.0.

## <a name="demonstrates"></a>Demonstracje

W tym przykładzie pokazano poniżej:

- Tworzenie obiektu RunspacePool z minimalną i maksymalną liczbą obszary działania mogą zostać otwarte w tym samym czasie.

- Tworzenie listy poleceń.

- Uruchamianie polecenia asynchronicznie.

- Wywoływanie [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) metodę, aby zobaczyć, ile obszary działania są bezpłatne.

- Przechwytywanie danych wyjściowych polecenia za pomocą [System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) metody.

## <a name="example"></a>Przykład

Niniejszy przykład pokazuje, jak otworzyć obszary działania puli obszarem działania i jak asynchronicznie uruchamiać polecenia w tych obszarach działania.

[!code-csharp[PowerShell02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a>Zobacz też

[Pisanie aplikacji hosta programu PowerShell Windows](./writing-a-windows-powershell-host-application.md)