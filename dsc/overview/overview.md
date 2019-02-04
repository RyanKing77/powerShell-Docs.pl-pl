---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Program Windows PowerShell Desired State Configuration — omówienie
ms.openlocfilehash: 3e4f0afa17ab60bfa98f1b86b9830462a7c8e1cf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686313"
---
# <a name="windows-powershell-desired-state-configuration-overview"></a><span data-ttu-id="ea5b9-103">Program Windows PowerShell Desired State Configuration — omówienie</span><span class="sxs-lookup"><span data-stu-id="ea5b9-103">Windows PowerShell Desired State Configuration Overview</span></span>

> <span data-ttu-id="ea5b9-104">Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ea5b9-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="ea5b9-105">DSC to platforma zarządzania w programie PowerShell, który pozwala na zarządzanie IT i rozwój infrastruktury za pomocą konfiguracji jako kodu.</span><span class="sxs-lookup"><span data-stu-id="ea5b9-105">DSC is a management platform in PowerShell that enables you to manage your IT and development infrastructure with configuration as code.</span></span>

- <span data-ttu-id="ea5b9-106">Aby uzyskać ogólne korzyści dla firm za pomocą DSC, zobacz [Przegląd Desired State Configuration dla osób podejmujących](decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="ea5b9-106">For an overview of the business benefits of using DSC, see [Desired State Configuration Overview for Decision Makers](decisionMaker.md).</span></span>
- <span data-ttu-id="ea5b9-107">Omówienie zalet engineering za pomocą DSC, zobacz [Przegląd Desired State Configuration dla inżynierów](DscForEngineers.md).</span><span class="sxs-lookup"><span data-stu-id="ea5b9-107">For an overview of the engineering benefits of using DSC, see [Desired State Configuration Overview for Engineers](DscForEngineers.md).</span></span>
- <span data-ttu-id="ea5b9-108">Aby rozpocząć korzystanie z DSC szybko, zobacz [DSC — szybki start](../quickstarts/website-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="ea5b9-108">To start using DSC quickly, see [DSC quick start](../quickstarts/website-quickstart.md).</span></span>

## <a name="key-concepts"></a><span data-ttu-id="ea5b9-109">Kluczowe pojęcia</span><span class="sxs-lookup"><span data-stu-id="ea5b9-109">Key Concepts</span></span>

<span data-ttu-id="ea5b9-110">DSC to platforma deklaracyjne używane do konfiguracji, wdrażania i zarządzania systemami.</span><span class="sxs-lookup"><span data-stu-id="ea5b9-110">DSC is a declarative platform used for configuration, deployment, and management of systems.</span></span> <span data-ttu-id="ea5b9-111">Składa się z trzech podstawowych składników:</span><span class="sxs-lookup"><span data-stu-id="ea5b9-111">It consists of three primary components:</span></span>

- <span data-ttu-id="ea5b9-112">[Konfiguracje](../configurations/configurations.md) to deklaratywne skrypty programu PowerShell, które zdefiniować i skonfigurować wystąpień zasobów.</span><span class="sxs-lookup"><span data-stu-id="ea5b9-112">[Configurations](../configurations/configurations.md) are declarative PowerShell scripts which define and configure instances of resources.</span></span>
    <span data-ttu-id="ea5b9-113">Podczas uruchamiania konfiguracji DSC (i zasoby wywoływane przez tę konfigurację) będą po prostu "Przechowuj je tak", sprawdzanie, czy system istnieje w stanie rozmieszczony w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ea5b9-113">Upon running the configuration, DSC (and the resources being called by the configuration) will simply “make it so”, ensuring that the system exists in the state laid out by the configuration.</span></span>
    <span data-ttu-id="ea5b9-114">Konfiguracje DSC są również idempotentne: lokalne Configuration Manager (LCM) będzie w dalszym ciągu upewnij się, czy maszyny są skonfigurowane w stanie niezależnie od konfiguracji deklaruje.</span><span class="sxs-lookup"><span data-stu-id="ea5b9-114">DSC configurations are also idempotent: the Local Configuration Manager (LCM) will continue to ensure that machines are configured in whatever state the configuration declares.</span></span>
- <span data-ttu-id="ea5b9-115">[Zasoby](../resources/resources.md) są częścią "Przechowuj je więc" DSC.</span><span class="sxs-lookup"><span data-stu-id="ea5b9-115">[Resources](../resources/resources.md) are the "make it so" part of DSC.</span></span> <span data-ttu-id="ea5b9-116">Zawierają one kod, który umieścić i utrzymania docelowej konfiguracji w określonym stanie.</span><span class="sxs-lookup"><span data-stu-id="ea5b9-116">They contain the code that put and keep the target of a configuration in the specified state.</span></span>
    <span data-ttu-id="ea5b9-117">Zasoby znajdują się w modułach programu PowerShell i mogą być zapisywane do modelowania wystąpił ogólny jako plik lub proces Windows lub tak dokładnie, jak serwer usług IIS lub maszyny Wirtualnej działającej na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="ea5b9-117">Resources reside in PowerShell modules and can be written to model something as generic as a file or a Windows process, or as specific as an IIS server or a VM running in Azure.</span></span>
- <span data-ttu-id="ea5b9-118">[Lokalnego Configuration Manager (LCM)](../managing-nodes/metaConfig.md) to aparat za pomocą którego ułatwia tworzenie interakcji między zasobami i konfiguracje DSC.</span><span class="sxs-lookup"><span data-stu-id="ea5b9-118">The [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md) is the engine by which DSC facilitates the interaction between resources and configurations.</span></span>
    <span data-ttu-id="ea5b9-119">LCM sonduje regularnie systemu, zapewni, że stan zdefiniowane przez konfigurację przy użyciu przepływu sterowania implementowany przez zasoby.</span><span class="sxs-lookup"><span data-stu-id="ea5b9-119">The LCM regularly polls the system using the control flow implemented by resources to ensure that the state defined by a configuration is maintained.</span></span>
    <span data-ttu-id="ea5b9-120">W przypadku systemu ze stanu LCM wykonywania wywołań do kodu w zasobach być "tak" zgodnie z konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="ea5b9-120">If the system is out of state, the LCM makes calls to the code in resources to “make it so” according to the configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="ea5b9-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ea5b9-121">See Also</span></span>

- [<span data-ttu-id="ea5b9-122">Konfiguracje DSC</span><span class="sxs-lookup"><span data-stu-id="ea5b9-122">DSC Configurations</span></span>](../configurations/configurations.md)
- [<span data-ttu-id="ea5b9-123">Zasoby DSC</span><span class="sxs-lookup"><span data-stu-id="ea5b9-123">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="ea5b9-124">Konfigurowanie programu Local Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="ea5b9-124">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
