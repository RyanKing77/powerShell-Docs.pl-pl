---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda GetConfigurationResultOutput
ms.openlocfilehash: 480e710ce1a208253f0e664474c3e9bab296066a
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727135"
---
# <a name="getconfigurationresultoutput-method"></a><span data-ttu-id="05ba7-103">Metoda GetConfigurationResultOutput</span><span class="sxs-lookup"><span data-stu-id="05ba7-103">GetConfigurationResultOutput method</span></span>

<span data-ttu-id="05ba7-104">Pobiera dane wyjściowe agenta konfiguracji skojarzone z określonego zadania.</span><span class="sxs-lookup"><span data-stu-id="05ba7-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="05ba7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="05ba7-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="05ba7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="05ba7-106">Parameters</span></span>

<span data-ttu-id="05ba7-107">*jobId* \[w\] identyfikator zadania, dla którego należy pobrać dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="05ba7-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="05ba7-108">*resumeOutputBookmark* \[w\] Określa, że dane wyjściowe powinny być kontynuacji poprzedniej zakładki.</span><span class="sxs-lookup"><span data-stu-id="05ba7-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="05ba7-109">*dane wyjściowe* \[się\] danych wyjściowych dla określonego zadania.</span><span class="sxs-lookup"><span data-stu-id="05ba7-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="05ba7-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="05ba7-110">Return value</span></span>

<span data-ttu-id="05ba7-111">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="05ba7-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="05ba7-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="05ba7-112">Remarks</span></span>

<span data-ttu-id="05ba7-113">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="05ba7-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="05ba7-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="05ba7-114">Requirements</span></span>

<span data-ttu-id="05ba7-115">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="05ba7-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="05ba7-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="05ba7-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="05ba7-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05ba7-117">See also</span></span>

[<span data-ttu-id="05ba7-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="05ba7-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
