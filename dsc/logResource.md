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
# <a name="dsc-log-resource"></a><span data-ttu-id="219dd-103">Zasób dziennika DSC</span><span class="sxs-lookup"><span data-stu-id="219dd-103">DSC Log Resource</span></span> 

> <span data-ttu-id="219dd-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="219dd-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="219dd-105">__Dziennika__ zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm mają być zapisywane w dzienniku zdarzeń Microsoft-Windows-żądany stan konfiguracji/analityczne.</span><span class="sxs-lookup"><span data-stu-id="219dd-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

<span data-ttu-id="219dd-106">Uwaga: Domyślnie tylko operacyjne dzienniki DSC są włączone.</span><span class="sxs-lookup"><span data-stu-id="219dd-106">NOTE: By default only the Operational logs for DSC are enabled.</span></span>
<span data-ttu-id="219dd-107">Przed analityczne dziennika będą dostępne ani widoczne, musi być włączony.</span><span class="sxs-lookup"><span data-stu-id="219dd-107">Before the Analytic log will be available or visible, it must be enabled.</span></span>
<span data-ttu-id="219dd-108">Zawiera następujący artykuł.</span><span class="sxs-lookup"><span data-stu-id="219dd-108">See the following article.</span></span>

[<span data-ttu-id="219dd-109">Gdzie są dzienniki zdarzeń usługi Konfiguracja DSC?</span><span class="sxs-lookup"><span data-stu-id="219dd-109">Where are DSC Event Logs?</span></span>](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs)

## <a name="properties"></a><span data-ttu-id="219dd-110">Właściwości</span><span class="sxs-lookup"><span data-stu-id="219dd-110">Properties</span></span>
|  <span data-ttu-id="219dd-111">Właściwość</span><span class="sxs-lookup"><span data-stu-id="219dd-111">Property</span></span>  |  <span data-ttu-id="219dd-112">Opis</span><span class="sxs-lookup"><span data-stu-id="219dd-112">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="219dd-113">Wiadomość</span><span class="sxs-lookup"><span data-stu-id="219dd-113">Message</span></span>| <span data-ttu-id="219dd-114">Określa komunikat, które mają zostać zapisane w dzienniku zdarzeń Microsoft-Windows-Desired stan konfiguracji/analityczne.</span><span class="sxs-lookup"><span data-stu-id="219dd-114">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>| 
| <span data-ttu-id="219dd-115">dependsOn</span><span class="sxs-lookup"><span data-stu-id="219dd-115">DependsOn</span></span> | <span data-ttu-id="219dd-116">Wskazuje, że konfiguracja inny zasób należy uruchomić przed zapisaniem pobiera ten komunikat dziennika.</span><span class="sxs-lookup"><span data-stu-id="219dd-116">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="219dd-117">Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="219dd-117">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="219dd-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="219dd-118">Example</span></span>

<span data-ttu-id="219dd-119">Poniższy przykład pokazuje, jak można uwzględnić komunikat w dzienniku zdarzeń Microsoft-Windows-Desired stan konfiguracji/analityczne.</span><span class="sxs-lookup"><span data-stu-id="219dd-119">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> <span data-ttu-id="219dd-120">**Uwaga**: po uruchomieniu [DscConfiguration testu](https://technet.microsoft.com/en-us/library/dn407382.aspx) z tym zasobem skonfigurowane, będzie ona zawsze zwrócić **$false**.</span><span class="sxs-lookup"><span data-stu-id="219dd-120">**Note**: if you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

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

