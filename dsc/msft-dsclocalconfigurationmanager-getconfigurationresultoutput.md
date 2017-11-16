---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Metoda GetConfigurationResultOutput klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 09862fd3c19e1e517c9bf5df878113ba3f10d8a6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="8d3f1-103">Metoda GetConfigurationResultOutput klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="8d3f1-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="8d3f1-104">Pobiera dane wyjściowe Agent konfiguracji skojarzone z danego zadania.</span><span class="sxs-lookup"><span data-stu-id="8d3f1-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="8d3f1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8d3f1-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="8d3f1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8d3f1-106">Parameters</span></span>
----------

<span data-ttu-id="8d3f1-107">*Identyfikator zadania* \[w\]</span><span class="sxs-lookup"><span data-stu-id="8d3f1-107">*jobId* \[in\]</span></span>  
<span data-ttu-id="8d3f1-108">Identyfikator zadania, dla którego można pobrać danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="8d3f1-108">The ID of the job for which to get output data.</span></span>

<span data-ttu-id="8d3f1-109">*resumeOutputBookmark* \[w\]</span><span class="sxs-lookup"><span data-stu-id="8d3f1-109">*resumeOutputBookmark* \[in\]</span></span>  
<span data-ttu-id="8d3f1-110">Określa, czy dane wyjściowe powinny być kontynuacja z poprzedniej zakładki.</span><span class="sxs-lookup"><span data-stu-id="8d3f1-110">Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="8d3f1-111">*dane wyjściowe* \[out\]</span><span class="sxs-lookup"><span data-stu-id="8d3f1-111">*output* \[out\]</span></span>  
<span data-ttu-id="8d3f1-112">Dane wyjściowe dla określonego zadania.</span><span class="sxs-lookup"><span data-stu-id="8d3f1-112">The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="8d3f1-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8d3f1-113">Return value</span></span>
------------

<span data-ttu-id="8d3f1-114">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="8d3f1-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8d3f1-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8d3f1-115">Remarks</span></span>

<span data-ttu-id="8d3f1-116">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="8d3f1-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8d3f1-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8d3f1-117">Requirements</span></span>
------------
><span data-ttu-id="8d3f1-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="8d3f1-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="8d3f1-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8d3f1-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="8d3f1-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8d3f1-120">See also</span></span>


[<span data-ttu-id="8d3f1-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="8d3f1-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



