---
title: Błędy do niepowodujące | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 468dabd6-bfeb-448d-8e09-0996db516edd
caps.latest.revision: 8
ms.openlocfilehash: 5f804756e0e3e867832f15f50967fd6987f160a5
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054361"
---
# <a name="non-terminating-errors"></a>Błędy niepowodujące przerwania działania

W tym temacie omówiono metody używane do zgłaszania błędy niepowodujące. Omawia także sposób wywoływania metody z w ramach polecenia cmdlet.

Gdy wystąpi błąd niepowodujący, polecenia cmdlet należy zgłosić ten błąd przez wywołanie metody [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metody. Gdy polecenie cmdlet zgłasza błąd niepowodujący, polecenia cmdlet mogą w dalszym ciągu działać na ten obiekt danych wejściowych i dalsze przychodzące potoku obiektów. Jeśli polecenie cmdlet nie wywoła [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metody, polecenie cmdlet może zapisywać rekord błędu, który opisuje warunek, który spowodował błąd niepowodujący. Aby uzyskać więcej informacji na temat rekordów błędów, zobacz [rekordów błędów programu Windows PowerShell](./windows-powershell-error-records.md).

Polecenia cmdlet można wywołać [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) gdy jest to konieczne z ich dane wejściowe metody przetwarzania. Jednak można wywoływać polecenia cmdlet [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) tylko z wątku, który wywołał [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), lub [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) przetwarzania metody wejściowej. Nie wywołuj [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) z innego wątku. Zamiast tego komunikują się błędy, wróć do głównego wątku.

## <a name="see-also"></a>Zobacz też

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[Windows PowerShell błąd rekordów](./windows-powershell-error-records.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
