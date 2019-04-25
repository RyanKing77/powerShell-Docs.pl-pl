---
ms.date: 03/15/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Korzystanie z platformy DSC na platformie Microsoft Azure
ms.openlocfilehash: 54a317a415ff12c3d270897f414cba88716f0728
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079884"
---
# <a name="using-dsc-on-microsoft-azure"></a><span data-ttu-id="708d7-103">Korzystanie z platformy DSC na platformie Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="708d7-103">Using DSC on Microsoft Azure</span></span>

<span data-ttu-id="708d7-104">Desired State Configuration (DSC) jest obsługiwana w systemie Microsoft Azure za pośrednictwem [procedury obsługi rozszerzenia Azure Desired State Configuration](/azure/virtual-machines/extensions/dsc-overview) i [usługi Azure Automation DSC](/azure/automation/automation-dsc-overview).</span><span class="sxs-lookup"><span data-stu-id="708d7-104">Desired State Configuration (DSC) is supported in Microsoft Azure through the [Azure Desired State Configuration extension handler](/azure/virtual-machines/extensions/dsc-overview) and through [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span></span>

## <a name="azure-desired-state-configuration-extension-handler"></a><span data-ttu-id="708d7-105">Obsługa rozszerzenia Azure Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="708d7-105">Azure Desired State Configuration extension handler</span></span>

<span data-ttu-id="708d7-106">Rozszerzenie DSC na platformie Azure umożliwia maszyn wirtualnych hostowanych na platformie Microsoft Azure były zarządzane za pomocą DSC.</span><span class="sxs-lookup"><span data-stu-id="708d7-106">The Azure DSC extension allows VMs hosted in Microsoft Azure to be managed with DSC.</span></span>
<span data-ttu-id="708d7-107">Aby uzyskać więcej informacji, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="708d7-107">For more information, see the following topics:</span></span>

- [<span data-ttu-id="708d7-108">Obsługa rozszerzenia Azure Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="708d7-108">Azure Desired State Configuration extension handler</span></span>](/azure/virtual-machines/extensions/dsc-overview)
- [<span data-ttu-id="708d7-109">Windows skalowania maszyn wirtualnych i Desired State Configuration przy użyciu szablonów usługi Azure Resource Manager</span><span class="sxs-lookup"><span data-stu-id="708d7-109">Windows VMSS and Desired State Configuration with Azure Resource Manager templates</span></span>](/azure/virtual-machines/extensions/dsc-template)
- [<span data-ttu-id="708d7-110">Przekazywanie poświadczeń do obsługi rozszerzenia DSC na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="708d7-110">Passing credentials to the Azure DSC extension handler</span></span>](/azure/virtual-machines/extensions/dsc-credentials)
- [<span data-ttu-id="708d7-111">Historia rozszerzenia platformy Azure Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="708d7-111">Azure Desired State Configuration extension history</span></span>](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a><span data-ttu-id="708d7-112">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="708d7-112">Azure Automation DSC</span></span>

<span data-ttu-id="708d7-113">[Usługi Azure Automation](https://azure.microsoft.com/en-us/services/automation/) umożliwia zarządzanie konfiguracjami DSC, zasoby i węzły zarządzane z w obrębie platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="708d7-113">The [Azure Automation service](https://azure.microsoft.com/en-us/services/automation/) allows you to manage DSC configurations, resources, and managed nodes from within Azure.</span></span> <span data-ttu-id="708d7-114">Aby uzyskać więcej informacji, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="708d7-114">For more information, see the following topics:</span></span>

- [<span data-ttu-id="708d7-115">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="708d7-115">Azure Automation DSC</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="708d7-116">Wprowadzenie do usługi Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="708d7-116">Getting started with Azure Automation DSC</span></span>](/azure/automation/automation-dsc-getting-started)
- [<span data-ttu-id="708d7-117">Dołączanie maszyn w celu zarządzania przez usługi Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="708d7-117">Onboarding machines for management by Azure Automation DSC</span></span>](/azure/automation/automation-dsc-onboarding)