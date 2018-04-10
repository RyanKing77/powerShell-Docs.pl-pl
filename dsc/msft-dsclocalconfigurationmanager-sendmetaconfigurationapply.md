---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda SendMetaConfigurationApply klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ab82b239ddfdb4075d9440cd66343266b3c08eda
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="66e8c-103">Metoda SendMetaConfigurationApply klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="66e8c-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="66e8c-104">Konfiguruje ustawienia lokalny program Configuration Manager, które są używane do sterowania agenta konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="66e8c-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="66e8c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="66e8c-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="66e8c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="66e8c-106">Parameters</span></span>
----------

<span data-ttu-id="66e8c-107">*ConfigurationData* \[w\] danych środowiska w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="66e8c-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="66e8c-108">*Wymuś* \[w\] **true** wymusić konfigurację, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="66e8c-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="66e8c-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="66e8c-109">Return value</span></span>
------------

<span data-ttu-id="66e8c-110">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="66e8c-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="66e8c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="66e8c-111">Remarks</span></span>

<span data-ttu-id="66e8c-112">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="66e8c-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="66e8c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="66e8c-113">Requirements</span></span>
------------
><span data-ttu-id="66e8c-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="66e8c-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="66e8c-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="66e8c-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="66e8c-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="66e8c-116">See also</span></span>


[<span data-ttu-id="66e8c-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="66e8c-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)