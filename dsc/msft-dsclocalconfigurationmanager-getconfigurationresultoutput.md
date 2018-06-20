---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda GetConfigurationResultOutput klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 73d10a8b44e5056e3fce1598518630a84aff6ceb
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186810"
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="2b09a-103">Metoda GetConfigurationResultOutput klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="2b09a-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="2b09a-104">Pobiera dane wyjściowe Agent konfiguracji skojarzone z danego zadania.</span><span class="sxs-lookup"><span data-stu-id="2b09a-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="2b09a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b09a-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="2b09a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b09a-106">Parameters</span></span>
----------

<span data-ttu-id="2b09a-107">*Identyfikator zadania* \[w\] identyfikator zadania, dla którego można pobrać danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="2b09a-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="2b09a-108">*resumeOutputBookmark* \[w\] Określa, czy dane wyjściowe powinny być kontynuacja z poprzedniej zakładki.</span><span class="sxs-lookup"><span data-stu-id="2b09a-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="2b09a-109">*dane wyjściowe* \[limit\] produktu wyjściowego dla określonego zadania.</span><span class="sxs-lookup"><span data-stu-id="2b09a-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="2b09a-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2b09a-110">Return value</span></span>
------------

<span data-ttu-id="2b09a-111">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="2b09a-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2b09a-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2b09a-112">Remarks</span></span>

<span data-ttu-id="2b09a-113">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="2b09a-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2b09a-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2b09a-114">Requirements</span></span>
------------
><span data-ttu-id="2b09a-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="2b09a-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="2b09a-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2b09a-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="2b09a-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b09a-117">See also</span></span>


[<span data-ttu-id="2b09a-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2b09a-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)