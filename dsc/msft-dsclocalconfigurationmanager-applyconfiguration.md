---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda ApplyConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 2844e354e0d054b13b92267ce314536d88a1c33e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="84fac-103">Metoda ApplyConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="84fac-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="84fac-104">Używa agenta konfiguracji umożliwiają zastosowanie konfiguracji, który jest w stanie oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="84fac-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="84fac-105">Jeśli nie istnieje konfiguracja oczekujących, ta metoda przywrócenie bieżącej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="84fac-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>


## <a name="syntax"></a><span data-ttu-id="84fac-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="84fac-106">Syntax</span></span>
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="84fac-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="84fac-107">Parameters</span></span>
----------

<span data-ttu-id="84fac-108">*Wymuś* \[w\] Jeśli jest to **true**, stosowana bieżącej konfiguracji, nawet jeśli istnieje oczekująca konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="84fac-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="84fac-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="84fac-109">Return value</span></span>
------------

<span data-ttu-id="84fac-110">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="84fac-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="84fac-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="84fac-111">Remarks</span></span>

<span data-ttu-id="84fac-112">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="84fac-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="84fac-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="84fac-113">Requirements</span></span>
------------
><span data-ttu-id="84fac-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="84fac-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="84fac-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="84fac-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="84fac-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="84fac-116">See also</span></span>


[<span data-ttu-id="84fac-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="84fac-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)