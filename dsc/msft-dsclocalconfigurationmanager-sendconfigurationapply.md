---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda SendConfigurationApply klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 8edf8c55089e767394ba21b42fe74072777a45c9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="36cbc-103">Metoda SendConfigurationApply klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="36cbc-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="36cbc-104">Wysyła dokument konfiguracji do węzła zarządzanego i używa konfiguracji agenta, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="36cbc-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="36cbc-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="36cbc-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="36cbc-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="36cbc-106">Parameters</span></span>
----------

<span data-ttu-id="36cbc-107">*ConfigurationData* \[w\] danych środowiska w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="36cbc-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="36cbc-108">*Wymuś* \[w\] **true** wymusić konfigurację, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="36cbc-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="36cbc-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="36cbc-109">Return value</span></span>
------------

<span data-ttu-id="36cbc-110">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="36cbc-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="36cbc-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="36cbc-111">Remarks</span></span>

<span data-ttu-id="36cbc-112">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="36cbc-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="36cbc-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="36cbc-113">Requirements</span></span>
------------
><span data-ttu-id="36cbc-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="36cbc-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="36cbc-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="36cbc-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="36cbc-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="36cbc-116">See also</span></span>


[<span data-ttu-id="36cbc-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="36cbc-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)