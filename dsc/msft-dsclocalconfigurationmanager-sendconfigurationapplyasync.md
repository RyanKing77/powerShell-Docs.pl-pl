---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda SendConfigurationApplyAsync klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 7ff821a277a548869862741551ee9897e417ea45
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ae0d2-103">Metoda SendConfigurationApplyAsync klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="ae0d2-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ae0d2-104">Asynchronicznie wysyła dokument konfiguracji do węzła zarządzanego i używa konfiguracji agenta, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="ae0d2-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="ae0d2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae0d2-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="ae0d2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ae0d2-106">Parameters</span></span>
----------

<span data-ttu-id="ae0d2-107">*ConfigurationData* \[w\] danych środowiska w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ae0d2-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="ae0d2-108">*Wymuś* \[w\] **true** wymusić konfigurację, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="ae0d2-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="ae0d2-109">*Identyfikator zadania* \[w\] identyfikator zadania, dla którego ma zostać wysłany w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ae0d2-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="ae0d2-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ae0d2-110">Return value</span></span>
------------

<span data-ttu-id="ae0d2-111">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="ae0d2-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ae0d2-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ae0d2-112">Remarks</span></span>

<span data-ttu-id="ae0d2-113">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="ae0d2-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ae0d2-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ae0d2-114">Requirements</span></span>
------------
><span data-ttu-id="ae0d2-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ae0d2-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="ae0d2-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ae0d2-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="ae0d2-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae0d2-117">See also</span></span>


[<span data-ttu-id="ae0d2-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ae0d2-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)