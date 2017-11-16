---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Metoda SendConfigurationApply klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 9552fd5b5feb862fbe8ef95a7746776e7fe2f5c8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4993d-103">Metoda SendConfigurationApply klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="4993d-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4993d-104">Wysyła dokument konfiguracji do węzła zarządzanego i używa konfiguracji agenta, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="4993d-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="4993d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4993d-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="4993d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4993d-106">Parameters</span></span>
----------

<span data-ttu-id="4993d-107">*ConfigurationData* \[w\]</span><span class="sxs-lookup"><span data-stu-id="4993d-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="4993d-108">Dane konfiguracji środowiska.</span><span class="sxs-lookup"><span data-stu-id="4993d-108">The environment data for the configuration.</span></span>

<span data-ttu-id="4993d-109">*Wymuś* \[w\]</span><span class="sxs-lookup"><span data-stu-id="4993d-109">*force* \[in\]</span></span>  
<span data-ttu-id="4993d-110">**wartość true,** wymusić konfigurację, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="4993d-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="4993d-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4993d-111">Return value</span></span>
------------

<span data-ttu-id="4993d-112">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="4993d-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4993d-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4993d-113">Remarks</span></span>

<span data-ttu-id="4993d-114">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="4993d-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4993d-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4993d-115">Requirements</span></span>
------------
><span data-ttu-id="4993d-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4993d-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="4993d-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4993d-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="4993d-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4993d-118">See also</span></span>


[<span data-ttu-id="4993d-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4993d-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



