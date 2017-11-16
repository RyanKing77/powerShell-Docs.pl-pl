---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Omówienie stanu konfiguracji żądanego programu Windows PowerShell"
ms.openlocfilehash: 154a3c78a9bf2a029577ca6862f333b6bfe69878
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="windows-powershell-desired-state-configuration-overview"></a><span data-ttu-id="52c19-103">Omówienie stanu konfiguracji żądanego programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="52c19-103">Windows PowerShell Desired State Configuration Overview</span></span> 

> <span data-ttu-id="52c19-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="52c19-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="52c19-105">DSC jest platformy do zarządzania w programie PowerShell, który umożliwia zarządzanie dział IT i Projektowanie infrastruktury z konfiguracją w kodzie.</span><span class="sxs-lookup"><span data-stu-id="52c19-105">DSC is a management platform in PowerShell that enables you to manage your IT and development infrastructure with configuration as code.</span></span>

- <span data-ttu-id="52c19-106">Omówienie korzyści biznesowe przy użyciu usługi Konfiguracja DSC, zobacz [żądany przegląd stanu konfiguracji dla inne osoby podejmujące decyzje](decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="52c19-106">For an overview of the business benefits of using DSC, see [Desired State Configuration Overview for Decision Makers](decisionMaker.md).</span></span>
- <span data-ttu-id="52c19-107">Omówienie engineering korzyści wynikające ze stosowania DSC, zobacz [żądany przegląd stanu konfiguracji dla inżynierów](DscForEngineers.md).</span><span class="sxs-lookup"><span data-stu-id="52c19-107">For an overview of the engineering benefits of using DSC, see [Desired State Configuration Overview for Engineers](DscForEngineers.md).</span></span>
- <span data-ttu-id="52c19-108">Aby rozpocząć korzystanie z usługi Konfiguracja DSC szybkie, zobacz [szybki start DSC](quickStart.md).</span><span class="sxs-lookup"><span data-stu-id="52c19-108">To start using DSC quickly, see [DSC quick start](quickStart.md).</span></span>

## <a name="key-concepts"></a><span data-ttu-id="52c19-109">Podstawowe pojęcia</span><span class="sxs-lookup"><span data-stu-id="52c19-109">Key Concepts</span></span>

<span data-ttu-id="52c19-110">DSC to platforma deklaratywne używany do konfiguracji, wdrażania i zarządzania systemów.</span><span class="sxs-lookup"><span data-stu-id="52c19-110">DSC is a declarative platform used for configuration, deployment, and management of systems.</span></span> <span data-ttu-id="52c19-111">Zawiera trzy główne składniki:</span><span class="sxs-lookup"><span data-stu-id="52c19-111">It consists of three primary components:</span></span>

- <span data-ttu-id="52c19-112">[Konfiguracje](configurations.md) są deklaratywne skryptów programu PowerShell, które zdefiniować i skonfigurować wystąpień zasobów.</span><span class="sxs-lookup"><span data-stu-id="52c19-112">[Configurations](configurations.md) are declarative PowerShell scripts which define and configure instances of resources.</span></span>
    <span data-ttu-id="52c19-113">Podczas uruchamiania konfiguracji (DSC i zasobów, wywoływana przez konfigurację) będzie po prostu "był to", sprawdzanie, czy system istnieje w stanie, którego układ określa się w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="52c19-113">Upon running the configuration, DSC (and the resources being called by the configuration) will simply “make it so”, ensuring that the system exists in the state laid out by the configuration.</span></span> 
    <span data-ttu-id="52c19-114">Konfiguracji DSC są również idempotentności: lokalnego Menedżera konfiguracji (LCM) będą w dalszym ciągu upewnij się, czy maszyny są skonfigurowane w stanie niezależnie od konfiguracji deklaruje.</span><span class="sxs-lookup"><span data-stu-id="52c19-114">DSC configurations are also idempotent: the Local Configuration Manager (LCM) will continue to ensure that machines are configured in whatever state the configuration declares.</span></span>
- <span data-ttu-id="52c19-115">[Zasoby](resources.md) są częścią "był to" DSC.</span><span class="sxs-lookup"><span data-stu-id="52c19-115">[Resources](resources.md) are the "make it so" part of DSC.</span></span> <span data-ttu-id="52c19-116">Zawierają one kod umieścić i przechowywać element docelowy w konfiguracji w określonym stanie.</span><span class="sxs-lookup"><span data-stu-id="52c19-116">They contain the code that put and keep the target of a configuration in the specified state.</span></span> 
    <span data-ttu-id="52c19-117">Zasoby znajdują się w modułach programu PowerShell i mogą być zapisywane na model coś jako ogólnego jako pliku lub procesu systemu Windows lub jako określone jako serwer usług IIS lub maszynie Wirtualnej działają na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="52c19-117">Resources reside in PowerShell modules and can be written to model something as generic as a file or a Windows process, or as specific as an IIS server or a VM running in Azure.</span></span>
- <span data-ttu-id="52c19-118">[Lokalnego Configuration Manager (LCM)](metaConfig.md) jest aparatem, przez którą DSC ułatwia interakcji między zasobami i konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="52c19-118">The [Local Configuration Manager (LCM)](metaConfig.md) is the engine by which DSC facilitates the interaction between resources and configurations.</span></span> 
    <span data-ttu-id="52c19-119">LCM sonduje regularnie systemu przy użyciu przepływu sterowania zaimplementowana przez zasoby do zapewni, że stan zdefiniowane przez konfigurację.</span><span class="sxs-lookup"><span data-stu-id="52c19-119">The LCM regularly polls the system using the control flow implemented by resources to ensure that the state defined by a configuration is maintained.</span></span> 
    <span data-ttu-id="52c19-120">W przypadku systemu ze stanu, LCM wykonywania wywołań do kodu w zasobach umożliwia "tak" zgodnie z konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="52c19-120">If the system is out of state, the LCM makes calls to the code in resources to “make it so” according to the configuration.</span></span> 

## <a name="see-also"></a><span data-ttu-id="52c19-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="52c19-121">See Also</span></span>

- [<span data-ttu-id="52c19-122">Konfiguracji DSC</span><span class="sxs-lookup"><span data-stu-id="52c19-122">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="52c19-123">Zasoby usługi Konfiguracja DSC</span><span class="sxs-lookup"><span data-stu-id="52c19-123">DSC Resources</span></span>](resources.md)
- [<span data-ttu-id="52c19-124">Konfigurowanie lokalny program Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="52c19-124">Configuring The Local Configuration Manager</span></span>](metaConfig.md)

