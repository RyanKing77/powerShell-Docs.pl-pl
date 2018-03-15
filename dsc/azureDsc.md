---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Przy użyciu usługi Konfiguracja DSC na platformie Microsoft Azure"
ms.openlocfilehash: d164fc107ec9fecbb8e399d0089501cababde8c4
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="using-dsc-on-microsoft-azure"></a><span data-ttu-id="fc97e-103">Przy użyciu usługi Konfiguracja DSC na platformie Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="fc97e-103">Using DSC on Microsoft Azure</span></span>

<span data-ttu-id="fc97e-104">Pożądanej konfiguracji stanu (DSC) jest obsługiwana na platformie Microsoft Azure za pośrednictwem [Azure konfiguracji żądanego stanu rozszerzenia obsługi](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview) i za pomocą [Konfiguracja DSC automatyzacji Azure](/azure/automation/automation-dsc-overview).</span><span class="sxs-lookup"><span data-stu-id="fc97e-104">Desired State Configuration (DSC) is supported in Microsoft Azure through the [Azure Desired State Configuration extension handler](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview) and through [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span></span>

## <a name="azure-desired-state-configuration-extension-handler"></a><span data-ttu-id="fc97e-105">Azure żądany stan konfiguracji rozszerzenia obsługi</span><span class="sxs-lookup"><span data-stu-id="fc97e-105">Azure Desired State Configuration extension handler</span></span>

<span data-ttu-id="fc97e-106">Rozszerzenia usługi Konfiguracja DSC Azure umożliwia maszyn wirtualnych hostowanych na platformie Microsoft Azure mają być zarządzane w usłudze Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="fc97e-106">The Azure DSC extension allows VMs hosted in Microsoft Azure to be managed with DSC.</span></span> <span data-ttu-id="fc97e-107">Aby uzyskać więcej informacji, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="fc97e-107">For more information, see the following topics:</span></span>

- [<span data-ttu-id="fc97e-108">Azure żądany stan konfiguracji rozszerzenia obsługi</span><span class="sxs-lookup"><span data-stu-id="fc97e-108">Azure Desired State Configuration extension handler</span></span>](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview)
- [<span data-ttu-id="fc97e-109">VMSS systemu Windows i konfiguracji żądanego stanu przy użyciu szablonów usługi Azure Resource Manager</span><span class="sxs-lookup"><span data-stu-id="fc97e-109">Windows VMSS and Desired State Configuration with Azure Resource Manager templates</span></span>](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-template)
- [<span data-ttu-id="fc97e-110">Przekazywania poświadczeń do obsługi rozszerzenia usługi Konfiguracja DSC Azure</span><span class="sxs-lookup"><span data-stu-id="fc97e-110">Passing credentials to the Azure DSC extension handler</span></span>](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-credentials)
- [<span data-ttu-id="fc97e-111">Historia rozszerzenia konfiguracji Azure żądany stan</span><span class="sxs-lookup"><span data-stu-id="fc97e-111">Azure Desired State Configuration extension history</span></span>](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a><span data-ttu-id="fc97e-112">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="fc97e-112">Azure Automation DSC</span></span>

<span data-ttu-id="fc97e-113">[Usługi Automatyzacja Azure](/services/automation/) umożliwia zarządzanie konfiguracji DSC, zasobów i węzły zarządzane przy użyciu w obrębie platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="fc97e-113">The [Azure Automation service](/services/automation/) allows you to manage DSC configurations, resources, and managed nodes from within Azure.</span></span> <span data-ttu-id="fc97e-114">Aby uzyskać więcej informacji, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="fc97e-114">For more information, see the following topics:</span></span>

- [<span data-ttu-id="fc97e-115">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="fc97e-115">Azure Automation DSC</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="fc97e-116">Wprowadzenie do korzystania z usługi Konfiguracja DSC automatyzacji Azure</span><span class="sxs-lookup"><span data-stu-id="fc97e-116">Getting started with Azure Automation DSC</span></span>](/azure/automation/automation-dsc-getting-started)
- [<span data-ttu-id="fc97e-117">Dołączania komputerów do zarządzania przez Konfiguracja DSC automatyzacji Azure</span><span class="sxs-lookup"><span data-stu-id="fc97e-117">Onboarding machines for management by Azure Automation DSC</span></span>](/azure/automation/automation-dsc-onboarding)

