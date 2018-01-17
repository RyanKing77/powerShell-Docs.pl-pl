---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Metoda SendConfigurationApplyAsync klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e680d510aaac097f4f0de80660274230e028ed45
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="59925-103">Metoda SendConfigurationApplyAsync klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="59925-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="59925-104">Asynchronicznie wysyła dokument konfiguracji do węzła zarządzanego i używa konfiguracji agenta, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="59925-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="59925-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="59925-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="59925-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="59925-106">Parameters</span></span>
----------

<span data-ttu-id="59925-107">*ConfigurationData* \[w\]</span><span class="sxs-lookup"><span data-stu-id="59925-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="59925-108">Dane konfiguracji środowiska.</span><span class="sxs-lookup"><span data-stu-id="59925-108">The environment data for the configuration.</span></span>

<span data-ttu-id="59925-109">*Wymuś* \[w\]</span><span class="sxs-lookup"><span data-stu-id="59925-109">*force* \[in\]</span></span>  
<span data-ttu-id="59925-110">**wartość true,** wymusić konfigurację, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="59925-110">**true** to force the configuration to stop.</span></span>

<span data-ttu-id="59925-111">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="59925-111">*jobId* \[in\]</span></span>  
<span data-ttu-id="59925-112">Identyfikator zadania, dla którego ma zostać wysłany w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="59925-112">The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="59925-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="59925-113">Return value</span></span>
------------

<span data-ttu-id="59925-114">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="59925-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="59925-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="59925-115">Remarks</span></span>

<span data-ttu-id="59925-116">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="59925-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="59925-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="59925-117">Requirements</span></span>
------------
><span data-ttu-id="59925-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="59925-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="59925-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="59925-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="59925-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59925-120">See also</span></span>


[<span data-ttu-id="59925-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="59925-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



