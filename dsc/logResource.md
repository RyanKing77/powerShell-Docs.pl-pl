---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób DSC dziennika
ms.openlocfilehash: fade94efd8133ae0172737e4bb1aed89fc0f97d9
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093480"
---
# <a name="dsc-log-resource"></a>Zasób DSC dziennika

> Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0

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
> Domyślnie dzienniki operacyjne dla DSC są włączone. Zanim dziennik analityczny będą dostępne lub widoczne, musi być włączona. Aby uzyskać więcej informacji, zobacz [których dzienniki zdarzeń DSC?](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs).

## <a name="properties"></a>Właściwości

|  Właściwość  |  Opis   |
|---|---|
| Wiadomość| Wskazuje komunikat, który chcesz zapisać w dzienniku zdarzeń Microsoft-Windows-Desired stan konfiguracji/analityczne.|
| DependsOn | Wskazuje, że konfiguracja inny zasób należy uruchomić przed zapisaniem pobiera ten komunikat dziennika. Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest __ResourceName__ a jej typ jest __ResourceType__, składnia przy użyciu tej właściwości jest `DependsOn = '[ResourceType]ResourceName'`.|

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