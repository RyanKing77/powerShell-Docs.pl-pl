---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Metoda StopConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: f0b550615b20f07f99c8ed7009805c45794bfe22
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e61c5-103">Metoda StopConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="e61c5-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e61c5-104">Zatrzymuje zmian w konfiguracji jest w toku.</span><span class="sxs-lookup"><span data-stu-id="e61c5-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="e61c5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e61c5-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="e61c5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e61c5-106">Parameters</span></span>
----------

<span data-ttu-id="e61c5-107">*Wymuś* \[w\]</span><span class="sxs-lookup"><span data-stu-id="e61c5-107">*force* \[in\]</span></span>  
<span data-ttu-id="e61c5-108">**wartość true,** wymusić konfigurację, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="e61c5-108">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="e61c5-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e61c5-109">Return value</span></span>
------------

<span data-ttu-id="e61c5-110">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="e61c5-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e61c5-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e61c5-111">Remarks</span></span>

<span data-ttu-id="e61c5-112">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="e61c5-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e61c5-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e61c5-113">Requirements</span></span>
------------
><span data-ttu-id="e61c5-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e61c5-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="e61c5-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e61c5-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="e61c5-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e61c5-116">See also</span></span>


[<span data-ttu-id="e61c5-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e61c5-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



