---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Metoda SendConfigurationApplyAsync klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e680bfd1c5b39d364c90cf5ef6b43d0a568af23a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ed18e-103">Metoda SendConfigurationApplyAsync klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="ed18e-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ed18e-104">Asynchronicznie wysyła dokument konfiguracji do węzła zarządzanego i używa konfiguracji agenta, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="ed18e-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="ed18e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ed18e-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="ed18e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ed18e-106">Parameters</span></span>
----------

<span data-ttu-id="ed18e-107">*ConfigurationData* \[w\]</span><span class="sxs-lookup"><span data-stu-id="ed18e-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="ed18e-108">Dane konfiguracji środowiska.</span><span class="sxs-lookup"><span data-stu-id="ed18e-108">The environment data for the configuration.</span></span>

<span data-ttu-id="ed18e-109">*Wymuś* \[w\]</span><span class="sxs-lookup"><span data-stu-id="ed18e-109">*force* \[in\]</span></span>  
<span data-ttu-id="ed18e-110">**wartość true,** wymusić konfigurację, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="ed18e-110">**true** to force the configuration to stop.</span></span>

<span data-ttu-id="ed18e-111">*Identyfikator zadania* \[w\]</span><span class="sxs-lookup"><span data-stu-id="ed18e-111">*jobId* \[in\]</span></span>  
<span data-ttu-id="ed18e-112">Identyfikator zadania, dla którego ma zostać wysłany w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ed18e-112">The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="ed18e-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ed18e-113">Return value</span></span>
------------

<span data-ttu-id="ed18e-114">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="ed18e-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ed18e-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ed18e-115">Remarks</span></span>

<span data-ttu-id="ed18e-116">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="ed18e-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ed18e-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ed18e-117">Requirements</span></span>
------------
><span data-ttu-id="ed18e-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ed18e-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="ed18e-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ed18e-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="ed18e-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ed18e-120">See also</span></span>


[<span data-ttu-id="ed18e-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ed18e-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



