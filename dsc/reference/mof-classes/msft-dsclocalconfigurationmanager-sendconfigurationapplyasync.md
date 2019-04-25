---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda SendConfigurationApplyAsync klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b028079cf826719967858f50e357b441ba8f9d79
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078281"
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="471c5-103">Metoda SendConfigurationApplyAsync klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="471c5-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="471c5-104">Wysyła asynchronicznie zarządzany węzeł dokumentu konfiguracji i używa agenta konfiguracji, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="471c5-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="471c5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="471c5-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="471c5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="471c5-106">Parameters</span></span>

<span data-ttu-id="471c5-107">*ConfigurationData* \[w\] danych środowiska dla konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="471c5-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="471c5-108">*Wymuś* \[w\] **true** wymusić konfigurację, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="471c5-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="471c5-109">*jobId* \[w\] identyfikator zadania, dla którego ma zostać wysłany w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="471c5-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="471c5-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="471c5-110">Return value</span></span>

<span data-ttu-id="471c5-111">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="471c5-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="471c5-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="471c5-112">Remarks</span></span>

<span data-ttu-id="471c5-113">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="471c5-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="471c5-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="471c5-114">Requirements</span></span>

<span data-ttu-id="471c5-115">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="471c5-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="471c5-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="471c5-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="471c5-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="471c5-117">See also</span></span>

[<span data-ttu-id="471c5-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="471c5-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)