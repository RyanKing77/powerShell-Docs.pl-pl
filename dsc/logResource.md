---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Zasób dziennika DSC"
ms.openlocfilehash: 3bc4bf38b376cc62e42107eee1024eaabc93485a
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
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

