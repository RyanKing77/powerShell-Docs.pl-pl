---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda StopConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: dadb6912af2e4450381958ed465799056da49946
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="615e5-103">Metoda StopConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="615e5-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="615e5-104">Zatrzymuje zmian w konfiguracji jest w toku.</span><span class="sxs-lookup"><span data-stu-id="615e5-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="615e5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="615e5-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="615e5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="615e5-106">Parameters</span></span>
----------

<span data-ttu-id="615e5-107">*Wymuś* \[w\] **true** wymusić konfigurację, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="615e5-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="615e5-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="615e5-108">Return value</span></span>
------------

<span data-ttu-id="615e5-109">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="615e5-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="615e5-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="615e5-110">Remarks</span></span>

<span data-ttu-id="615e5-111">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="615e5-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="615e5-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="615e5-112">Requirements</span></span>
------------
><span data-ttu-id="615e5-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="615e5-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="615e5-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="615e5-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="615e5-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="615e5-115">See also</span></span>


[<span data-ttu-id="615e5-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="615e5-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)