---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda GetConfigurationResultOutput klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: f4c2ddaa37cdafeff1a442f3f1fa656788a1c6c8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d2c84-103">Metoda GetConfigurationResultOutput klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="d2c84-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d2c84-104">Pobiera dane wyjściowe Agent konfiguracji skojarzone z danego zadania.</span><span class="sxs-lookup"><span data-stu-id="d2c84-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="d2c84-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d2c84-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="d2c84-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d2c84-106">Parameters</span></span>
----------

<span data-ttu-id="d2c84-107">*Identyfikator zadania* \[w\] identyfikator zadania, dla którego można pobrać danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="d2c84-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="d2c84-108">*resumeOutputBookmark* \[w\] Określa, czy dane wyjściowe powinny być kontynuacja z poprzedniej zakładki.</span><span class="sxs-lookup"><span data-stu-id="d2c84-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="d2c84-109">*dane wyjściowe* \[limit\] produktu wyjściowego dla określonego zadania.</span><span class="sxs-lookup"><span data-stu-id="d2c84-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="d2c84-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d2c84-110">Return value</span></span>
------------

<span data-ttu-id="d2c84-111">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="d2c84-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d2c84-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d2c84-112">Remarks</span></span>

<span data-ttu-id="d2c84-113">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="d2c84-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d2c84-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d2c84-114">Requirements</span></span>
------------
><span data-ttu-id="d2c84-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d2c84-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="d2c84-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d2c84-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="d2c84-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2c84-117">See also</span></span>


[<span data-ttu-id="d2c84-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d2c84-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)