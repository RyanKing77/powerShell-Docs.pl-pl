---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda SendConfigurationApplyAsync klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b028079cf826719967858f50e357b441ba8f9d79
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688833"
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="2ff87-103">Metoda SendConfigurationApplyAsync klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="2ff87-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="2ff87-104">Wysyła asynchronicznie zarządzany węzeł dokumentu konfiguracji i używa agenta konfiguracji, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="2ff87-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="2ff87-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2ff87-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="2ff87-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ff87-106">Parameters</span></span>

<span data-ttu-id="2ff87-107">*ConfigurationData* \[w\] danych środowiska dla konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2ff87-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="2ff87-108">*Wymuś* \[w\] **true** wymusić konfigurację, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="2ff87-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="2ff87-109">*jobId* \[w\] identyfikator zadania, dla którego ma zostać wysłany w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2ff87-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="2ff87-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2ff87-110">Return value</span></span>

<span data-ttu-id="2ff87-111">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="2ff87-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2ff87-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2ff87-112">Remarks</span></span>

<span data-ttu-id="2ff87-113">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="2ff87-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2ff87-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2ff87-114">Requirements</span></span>

<span data-ttu-id="2ff87-115">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="2ff87-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="2ff87-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2ff87-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="2ff87-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ff87-117">See also</span></span>

[<span data-ttu-id="2ff87-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2ff87-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)