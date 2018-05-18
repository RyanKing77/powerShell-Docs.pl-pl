---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasób dziennika DSC
ms.openlocfilehash: c7e1957540da2fd85a30f739e0f69bdb6975a4d8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-log-resource"></a><span data-ttu-id="466e5-103">Zasób dziennika DSC</span><span class="sxs-lookup"><span data-stu-id="466e5-103">DSC Log Resource</span></span>

> <span data-ttu-id="466e5-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="466e5-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="466e5-105">__Dziennika__ zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm mają być zapisywane w dzienniku zdarzeń Microsoft-Windows-żądany stan konfiguracji/analityczne.</span><span class="sxs-lookup"><span data-stu-id="466e5-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

<span data-ttu-id="466e5-106">Uwaga: Domyślnie tylko operacyjne dzienniki DSC są włączone.</span><span class="sxs-lookup"><span data-stu-id="466e5-106">NOTE: By default only the Operational logs for DSC are enabled.</span></span>
<span data-ttu-id="466e5-107">Przed analityczne dziennika będą dostępne ani widoczne, musi być włączony.</span><span class="sxs-lookup"><span data-stu-id="466e5-107">Before the Analytic log will be available or visible, it must be enabled.</span></span>
<span data-ttu-id="466e5-108">Zawiera następujący artykuł.</span><span class="sxs-lookup"><span data-stu-id="466e5-108">See the following article.</span></span>

[<span data-ttu-id="466e5-109">Gdzie są dzienniki zdarzeń usługi Konfiguracja DSC?</span><span class="sxs-lookup"><span data-stu-id="466e5-109">Where are DSC Event Logs?</span></span>](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs)

## <a name="properties"></a><span data-ttu-id="466e5-110">Właściwości</span><span class="sxs-lookup"><span data-stu-id="466e5-110">Properties</span></span>
|  <span data-ttu-id="466e5-111">Właściwość</span><span class="sxs-lookup"><span data-stu-id="466e5-111">Property</span></span>  |  <span data-ttu-id="466e5-112">Opis</span><span class="sxs-lookup"><span data-stu-id="466e5-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="466e5-113">Wiadomość</span><span class="sxs-lookup"><span data-stu-id="466e5-113">Message</span></span>| <span data-ttu-id="466e5-114">Określa komunikat, które mają zostać zapisane w dzienniku zdarzeń Microsoft-Windows-Desired stan konfiguracji/analityczne.</span><span class="sxs-lookup"><span data-stu-id="466e5-114">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>|
| <span data-ttu-id="466e5-115">dependsOn</span><span class="sxs-lookup"><span data-stu-id="466e5-115">DependsOn</span></span> | <span data-ttu-id="466e5-116">Wskazuje, że konfiguracja inny zasób należy uruchomić przed zapisaniem pobiera ten komunikat dziennika.</span><span class="sxs-lookup"><span data-stu-id="466e5-116">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="466e5-117">Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="466e5-117">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="466e5-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="466e5-118">Example</span></span>

<span data-ttu-id="466e5-119">Poniższy przykład pokazuje, jak można uwzględnić komunikat w dzienniku zdarzeń Microsoft-Windows-Desired stan konfiguracji/analityczne.</span><span class="sxs-lookup"><span data-stu-id="466e5-119">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> <span data-ttu-id="466e5-120">**Uwaga**: po uruchomieniu [DscConfiguration testu](https://technet.microsoft.com/en-us/library/dn407382.aspx) z tym zasobem skonfigurowane, będzie ona zawsze zwrócić **$false**.</span><span class="sxs-lookup"><span data-stu-id="466e5-120">**Note**: if you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

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