---
ms.date: 03/15/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Korzystanie z platformy DSC na platformie Microsoft Azure
ms.openlocfilehash: 54a317a415ff12c3d270897f414cba88716f0728
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404652"
---
# <a name="using-dsc-on-microsoft-azure"></a><span data-ttu-id="c6cac-103">Korzystanie z platformy DSC na platformie Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="c6cac-103">Using DSC on Microsoft Azure</span></span>

<span data-ttu-id="c6cac-104">Desired State Configuration (DSC) jest obsługiwana w systemie Microsoft Azure za pośrednictwem [procedury obsługi rozszerzenia Azure Desired State Configuration](/azure/virtual-machines/extensions/dsc-overview) i [usługi Azure Automation DSC](/azure/automation/automation-dsc-overview).</span><span class="sxs-lookup"><span data-stu-id="c6cac-104">Desired State Configuration (DSC) is supported in Microsoft Azure through the [Azure Desired State Configuration extension handler](/azure/virtual-machines/extensions/dsc-overview) and through [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span></span>

## <a name="azure-desired-state-configuration-extension-handler"></a><span data-ttu-id="c6cac-105">Obsługa rozszerzenia Azure Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="c6cac-105">Azure Desired State Configuration extension handler</span></span>

<span data-ttu-id="c6cac-106">Rozszerzenie DSC na platformie Azure umożliwia maszyn wirtualnych hostowanych na platformie Microsoft Azure były zarządzane za pomocą DSC.</span><span class="sxs-lookup"><span data-stu-id="c6cac-106">The Azure DSC extension allows VMs hosted in Microsoft Azure to be managed with DSC.</span></span>
<span data-ttu-id="c6cac-107">Aby uzyskać więcej informacji, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="c6cac-107">For more information, see the following topics:</span></span>

- [<span data-ttu-id="c6cac-108">Obsługa rozszerzenia Azure Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="c6cac-108">Azure Desired State Configuration extension handler</span></span>](/azure/virtual-machines/extensions/dsc-overview)
- [<span data-ttu-id="c6cac-109">Windows skalowania maszyn wirtualnych i Desired State Configuration przy użyciu szablonów usługi Azure Resource Manager</span><span class="sxs-lookup"><span data-stu-id="c6cac-109">Windows VMSS and Desired State Configuration with Azure Resource Manager templates</span></span>](/azure/virtual-machines/extensions/dsc-template)
- [<span data-ttu-id="c6cac-110">Przekazywanie poświadczeń do obsługi rozszerzenia DSC na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="c6cac-110">Passing credentials to the Azure DSC extension handler</span></span>](/azure/virtual-machines/extensions/dsc-credentials)
- [<span data-ttu-id="c6cac-111">Historia rozszerzenia platformy Azure Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="c6cac-111">Azure Desired State Configuration extension history</span></span>](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a><span data-ttu-id="c6cac-112">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="c6cac-112">Azure Automation DSC</span></span>

<span data-ttu-id="c6cac-113">[Usługi Azure Automation](https://azure.microsoft.com/en-us/services/automation/) umożliwia zarządzanie konfiguracjami DSC, zasoby i węzły zarządzane z w obrębie platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="c6cac-113">The [Azure Automation service](https://azure.microsoft.com/en-us/services/automation/) allows you to manage DSC configurations, resources, and managed nodes from within Azure.</span></span> <span data-ttu-id="c6cac-114">Aby uzyskać więcej informacji, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="c6cac-114">For more information, see the following topics:</span></span>

- [<span data-ttu-id="c6cac-115">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="c6cac-115">Azure Automation DSC</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="c6cac-116">Wprowadzenie do usługi Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="c6cac-116">Getting started with Azure Automation DSC</span></span>](/azure/automation/automation-dsc-getting-started)
- [<span data-ttu-id="c6cac-117">Dołączanie maszyn w celu zarządzania przez usługi Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="c6cac-117">Onboarding machines for management by Azure Automation DSC</span></span>](/azure/automation/automation-dsc-onboarding)