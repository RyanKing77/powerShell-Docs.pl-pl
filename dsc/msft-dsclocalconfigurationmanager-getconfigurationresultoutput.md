---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Metoda GetConfigurationResultOutput klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: f6106bb28dc20004b5bbb6df2d8e719cf0c453f0
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="dc199-103">Metoda GetConfigurationResultOutput klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="dc199-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="dc199-104">Pobiera dane wyjściowe Agent konfiguracji skojarzone z danego zadania.</span><span class="sxs-lookup"><span data-stu-id="dc199-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="dc199-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="dc199-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="dc199-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="dc199-106">Parameters</span></span>
----------

<span data-ttu-id="dc199-107">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="dc199-107">*jobId* \[in\]</span></span>  
<span data-ttu-id="dc199-108">Identyfikator zadania, dla którego można pobrać danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="dc199-108">The ID of the job for which to get output data.</span></span>

<span data-ttu-id="dc199-109">*resumeOutputBookmark* \[w\]</span><span class="sxs-lookup"><span data-stu-id="dc199-109">*resumeOutputBookmark* \[in\]</span></span>  
<span data-ttu-id="dc199-110">Określa, czy dane wyjściowe powinny być kontynuacja z poprzedniej zakładki.</span><span class="sxs-lookup"><span data-stu-id="dc199-110">Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="dc199-111">*dane wyjściowe* \[out\]</span><span class="sxs-lookup"><span data-stu-id="dc199-111">*output* \[out\]</span></span>  
<span data-ttu-id="dc199-112">Dane wyjściowe dla określonego zadania.</span><span class="sxs-lookup"><span data-stu-id="dc199-112">The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="dc199-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dc199-113">Return value</span></span>
------------

<span data-ttu-id="dc199-114">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="dc199-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="dc199-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dc199-115">Remarks</span></span>

<span data-ttu-id="dc199-116">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="dc199-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="dc199-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dc199-117">Requirements</span></span>
------------
><span data-ttu-id="dc199-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="dc199-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="dc199-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="dc199-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="dc199-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dc199-120">See also</span></span>


[<span data-ttu-id="dc199-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="dc199-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



