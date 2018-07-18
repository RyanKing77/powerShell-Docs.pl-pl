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
# <a name="dsc-log-resource"></a><span data-ttu-id="e050c-103">Zasób DSC dziennika</span><span class="sxs-lookup"><span data-stu-id="e050c-103">DSC Log Resource</span></span>

> <span data-ttu-id="e050c-104">Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e050c-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="e050c-105">__Dziennika__ zasób w Windows PowerShell Desired State Configuration (DSC) zapewnia mechanizm aby zapisywać komunikaty w dzienniku zdarzeń Microsoft-Windows-Desired State Configuration / analityczne.</span><span class="sxs-lookup"><span data-stu-id="e050c-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> <span data-ttu-id="e050c-106">Domyślnie dzienniki operacyjne dla DSC są włączone.</span><span class="sxs-lookup"><span data-stu-id="e050c-106">By default only the Operational logs for DSC are enabled.</span></span> <span data-ttu-id="e050c-107">Zanim dziennik analityczny będą dostępne lub widoczne, musi być włączona.</span><span class="sxs-lookup"><span data-stu-id="e050c-107">Before the Analytic log will be available or visible, it must be enabled.</span></span> <span data-ttu-id="e050c-108">Aby uzyskać więcej informacji, zobacz [których dzienniki zdarzeń DSC?](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs).</span><span class="sxs-lookup"><span data-stu-id="e050c-108">For more information, see [Where are DSC Event Logs?](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs).</span></span>

## <a name="properties"></a><span data-ttu-id="e050c-109">Właściwości</span><span class="sxs-lookup"><span data-stu-id="e050c-109">Properties</span></span>

|  <span data-ttu-id="e050c-110">Właściwość</span><span class="sxs-lookup"><span data-stu-id="e050c-110">Property</span></span>  |  <span data-ttu-id="e050c-111">Opis</span><span class="sxs-lookup"><span data-stu-id="e050c-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="e050c-112">Wiadomość</span><span class="sxs-lookup"><span data-stu-id="e050c-112">Message</span></span>| <span data-ttu-id="e050c-113">Wskazuje komunikat, który chcesz zapisać w dzienniku zdarzeń Microsoft-Windows-Desired stan konfiguracji/analityczne.</span><span class="sxs-lookup"><span data-stu-id="e050c-113">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>|
| <span data-ttu-id="e050c-114">DependsOn</span><span class="sxs-lookup"><span data-stu-id="e050c-114">DependsOn</span></span> | <span data-ttu-id="e050c-115">Wskazuje, że konfiguracja inny zasób należy uruchomić przed zapisaniem pobiera ten komunikat dziennika.</span><span class="sxs-lookup"><span data-stu-id="e050c-115">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="e050c-116">Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest __ResourceName__ a jej typ jest __ResourceType__, składnia przy użyciu tej właściwości jest `DependsOn = '[ResourceType]ResourceName'`.</span><span class="sxs-lookup"><span data-stu-id="e050c-116">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = '[ResourceType]ResourceName'`.</span></span>|

## <a name="example"></a><span data-ttu-id="e050c-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="e050c-117">Example</span></span>

<span data-ttu-id="e050c-118">Poniższy przykład pokazuje, jak obejmujący komunikat w dzienniku zdarzeń Microsoft-Windows-Desired stan konfiguracji/analityczne.</span><span class="sxs-lookup"><span data-stu-id="e050c-118">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> [!NOTE]
> <span data-ttu-id="e050c-119">Jeśli uruchamiasz [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) z tym zasobem jest skonfigurowany, która zawsze zwraca **$false**.</span><span class="sxs-lookup"><span data-stu-id="e050c-119">If you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

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