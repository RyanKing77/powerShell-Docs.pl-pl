---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Zasób dziennika DSC"
ms.openlocfilehash: 72c9c5a9b8e2a4ed4ce43cfd792572ce95b502b3
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-log-resource"></a>Zasób dziennika DSC 

> Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0

__Dziennika__ zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm mają być zapisywane w dzienniku zdarzeń Microsoft-Windows-żądany stan konfiguracji/analityczne.

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

Uwaga: Domyślnie tylko operacyjne dzienniki DSC są włączone.
Przed analityczne dziennika będą dostępne ani widoczne, musi być włączony.
Zawiera następujący artykuł.

[Gdzie są dzienniki zdarzeń usługi Konfiguracja DSC?](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs)

## <a name="properties"></a>Właściwości
|  Właściwość  |  Opis   | 
|---|---| 
| Wiadomość| Określa komunikat, które mają zostać zapisane w dzienniku zdarzeń Microsoft-Windows-Desired stan konfiguracji/analityczne.| 
| dependsOn | Wskazuje, że konfiguracja inny zasób należy uruchomić przed zapisaniem pobiera ten komunikat dziennika. Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.| 

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak można uwzględnić komunikat w dzienniku zdarzeń Microsoft-Windows-Desired stan konfiguracji/analityczne.

> **Uwaga**: po uruchomieniu [DscConfiguration testu](https://technet.microsoft.com/en-us/library/dn407382.aspx) z tym zasobem skonfigurowane, będzie ona zawsze zwrócić **$false**.

```powershell 
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost

    {
        Log LogExample
        {
            Message = "This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log."
        }
    }
}
```

