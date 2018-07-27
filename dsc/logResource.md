---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób DSC dziennika
ms.openlocfilehash: 50fd6cd31ba426108830fcf124a767318060a95d
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268436"
---
# <a name="dsc-log-resource"></a><span data-ttu-id="07561-103">Zasób DSC dziennika</span><span class="sxs-lookup"><span data-stu-id="07561-103">DSC Log Resource</span></span>

<span data-ttu-id="07561-104">_Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="07561-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="07561-105">__Dziennika__ zasób w Windows PowerShell Desired State Configuration (DSC) zapewnia mechanizm aby zapisywać komunikaty w dzienniku zdarzeń Microsoft-Windows-Desired State Configuration / analityczne.</span><span class="sxs-lookup"><span data-stu-id="07561-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> <span data-ttu-id="07561-106">Domyślnie dzienniki operacyjne dla DSC są włączone.</span><span class="sxs-lookup"><span data-stu-id="07561-106">By default only the Operational logs for DSC are enabled.</span></span> <span data-ttu-id="07561-107">Zanim dziennik analityczny będą dostępne lub widoczne, musi być włączona.</span><span class="sxs-lookup"><span data-stu-id="07561-107">Before the Analytic log will be available or visible, it must be enabled.</span></span> <span data-ttu-id="07561-108">Aby uzyskać więcej informacji, zobacz [których dzienniki zdarzeń DSC?](troubleshooting.md#where-are-dsc-event-logs).</span><span class="sxs-lookup"><span data-stu-id="07561-108">For more information, see [Where are DSC Event Logs?](troubleshooting.md#where-are-dsc-event-logs).</span></span>

## <a name="properties"></a><span data-ttu-id="07561-109">Właściwości</span><span class="sxs-lookup"><span data-stu-id="07561-109">Properties</span></span>

| <span data-ttu-id="07561-110">Właściwość</span><span class="sxs-lookup"><span data-stu-id="07561-110">Property</span></span> | <span data-ttu-id="07561-111">Opis</span><span class="sxs-lookup"><span data-stu-id="07561-111">Description</span></span> |
| --- | --- |
| <span data-ttu-id="07561-112">Wiadomość</span><span class="sxs-lookup"><span data-stu-id="07561-112">Message</span></span>| <span data-ttu-id="07561-113">Wskazuje komunikat, który chcesz zapisać w dzienniku zdarzeń Microsoft-Windows-Desired stan konfiguracji/analityczne.</span><span class="sxs-lookup"><span data-stu-id="07561-113">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>|
| <span data-ttu-id="07561-114">DependsOn</span><span class="sxs-lookup"><span data-stu-id="07561-114">DependsOn</span></span> | <span data-ttu-id="07561-115">Wskazuje, że konfiguracja inny zasób należy uruchomić przed zapisaniem pobiera ten komunikat dziennika.</span><span class="sxs-lookup"><span data-stu-id="07561-115">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="07561-116">Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest **ResourceName** a jej typ jest **ResourceType**, składnia przy użyciu tej właściwości jest `DependsOn = '[ResourceType]ResourceName'`.</span><span class="sxs-lookup"><span data-stu-id="07561-116">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = '[ResourceType]ResourceName'`.</span></span>|

## <a name="example"></a><span data-ttu-id="07561-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="07561-117">Example</span></span>

<span data-ttu-id="07561-118">Poniższy przykład pokazuje, jak obejmujący komunikat w dzienniku zdarzeń Microsoft-Windows-Desired stan konfiguracji/analityczne.</span><span class="sxs-lookup"><span data-stu-id="07561-118">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> [!NOTE]
> <span data-ttu-id="07561-119">Jeśli uruchamiasz [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) z tym zasobem jest skonfigurowany, która zawsze zwraca **$false**.</span><span class="sxs-lookup"><span data-stu-id="07561-119">If you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

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