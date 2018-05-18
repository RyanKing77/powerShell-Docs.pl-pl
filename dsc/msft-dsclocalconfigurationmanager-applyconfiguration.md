---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda ApplyConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ef8488246b2c8614452d32009e45535f0ff2e184
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="f8a04-103">Metoda ApplyConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="f8a04-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="f8a04-104">Używa agenta konfiguracji umożliwiają zastosowanie konfiguracji, który jest w stanie oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="f8a04-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="f8a04-105">Jeśli nie istnieje konfiguracja oczekujących, ta metoda przywrócenie bieżącej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f8a04-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>


## <a name="syntax"></a><span data-ttu-id="f8a04-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="f8a04-106">Syntax</span></span>
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="f8a04-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8a04-107">Parameters</span></span>
----------

<span data-ttu-id="f8a04-108">*Wymuś* \[w\] Jeśli jest to **true**, stosowana bieżącej konfiguracji, nawet jeśli istnieje oczekująca konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="f8a04-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="f8a04-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f8a04-109">Return value</span></span>
------------

<span data-ttu-id="f8a04-110">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="f8a04-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f8a04-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f8a04-111">Remarks</span></span>

<span data-ttu-id="f8a04-112">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="f8a04-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f8a04-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f8a04-113">Requirements</span></span>
------------
><span data-ttu-id="f8a04-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f8a04-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="f8a04-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f8a04-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="f8a04-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f8a04-116">See also</span></span>


[<span data-ttu-id="f8a04-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f8a04-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)