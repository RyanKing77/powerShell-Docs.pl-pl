---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda SendConfigurationApplyAsync klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: acd8f380f1c49eb008563398c2c3de3fce5477f9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="8f084-103">Metoda SendConfigurationApplyAsync klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="8f084-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="8f084-104">Asynchronicznie wysyła dokument konfiguracji do węzła zarządzanego i używa konfiguracji agenta, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="8f084-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="8f084-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8f084-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="8f084-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8f084-106">Parameters</span></span>
----------

<span data-ttu-id="8f084-107">*ConfigurationData* \[w\] danych środowiska w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8f084-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="8f084-108">*Wymuś* \[w\] **true** wymusić konfigurację, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="8f084-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="8f084-109">*Identyfikator zadania* \[w\] identyfikator zadania, dla którego ma zostać wysłany w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8f084-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="8f084-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8f084-110">Return value</span></span>
------------

<span data-ttu-id="8f084-111">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="8f084-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8f084-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8f084-112">Remarks</span></span>

<span data-ttu-id="8f084-113">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="8f084-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8f084-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8f084-114">Requirements</span></span>
------------
><span data-ttu-id="8f084-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="8f084-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="8f084-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8f084-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="8f084-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8f084-117">See also</span></span>


[<span data-ttu-id="8f084-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="8f084-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)