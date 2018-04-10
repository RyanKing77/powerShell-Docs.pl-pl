---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda SendConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 07ae48dd456e68be4ad0b09127ba9801359fd101
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9adb9-103">Metoda SendConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="9adb9-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9adb9-104">Wysyła dokument konfiguracji do węzła zarządzanego i zapisuje go jako oczekujące zmiany.</span><span class="sxs-lookup"><span data-stu-id="9adb9-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="9adb9-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9adb9-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="9adb9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9adb9-106">Parameters</span></span>
----------

<span data-ttu-id="9adb9-107">*ConfigurationData* \[w\] danych środowiska w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9adb9-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="9adb9-108">*Wymuś* \[w\] **true** wymusić konfigurację, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="9adb9-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="9adb9-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9adb9-109">Return value</span></span>
------------

<span data-ttu-id="9adb9-110">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="9adb9-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9adb9-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9adb9-111">Remarks</span></span>

<span data-ttu-id="9adb9-112">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="9adb9-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9adb9-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9adb9-113">Requirements</span></span>
------------
><span data-ttu-id="9adb9-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9adb9-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="9adb9-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9adb9-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="9adb9-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9adb9-116">See also</span></span>


[<span data-ttu-id="9adb9-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9adb9-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)