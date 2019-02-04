---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób DSC dziennika
ms.openlocfilehash: 1f94a2d847a4ef63f81e2fb83d1a0f76f5677b09
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684241"
---
# <a name="dsc-log-resource"></a>Zasób DSC dziennika

> _Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0_

__Dziennika__ zasób w Windows PowerShell Desired State Configuration (DSC) zapewnia mechanizm aby zapisywać komunikaty w dzienniku zdarzeń Microsoft-Windows-Desired State Configuration / analityczne.

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> Domyślnie dzienniki operacyjne dla DSC są włączone. Zanim dziennik analityczny będą dostępne lub widoczne, musi być włączona. Aby uzyskać więcej informacji, zobacz [których dzienniki zdarzeń DSC?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).

## <a name="properties"></a>Właściwości

| Właściwość | Opis |
| --- | --- |
| Wiadomość| Wskazuje komunikat, który chcesz zapisać w dzienniku zdarzeń Microsoft-Windows-Desired stan konfiguracji/analityczne.|
| DependsOn | Wskazuje, że konfiguracja inny zasób należy uruchomić przed zapisaniem pobiera ten komunikat dziennika. Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest **ResourceName** a jej typ jest **ResourceType**, składnia przy użyciu tej właściwości jest `DependsOn = '[ResourceType]ResourceName'`.|

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak obejmujący komunikat w dzienniku zdarzeń Microsoft-Windows-Desired stan konfiguracji/analityczne.

> [!NOTE]
> Jeśli uruchamiasz [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) z tym zasobem jest skonfigurowany, która zawsze zwraca **$false**.

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Log LogExample
        {
            Message = 'This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log.'
        }
    }
}
```
