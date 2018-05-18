---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda StopConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: aaed29cb81e2079c4673b621b81c52e109aa7b48
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="1dafd-103">Metoda StopConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="1dafd-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="1dafd-104">Zatrzymuje zmian w konfiguracji jest w toku.</span><span class="sxs-lookup"><span data-stu-id="1dafd-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="1dafd-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1dafd-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="1dafd-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1dafd-106">Parameters</span></span>
----------

<span data-ttu-id="1dafd-107">*Wymuś* \[w\] **true** wymusić konfigurację, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="1dafd-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="1dafd-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1dafd-108">Return value</span></span>
------------

<span data-ttu-id="1dafd-109">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="1dafd-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="1dafd-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1dafd-110">Remarks</span></span>

<span data-ttu-id="1dafd-111">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="1dafd-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1dafd-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1dafd-112">Requirements</span></span>
------------
><span data-ttu-id="1dafd-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="1dafd-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="1dafd-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="1dafd-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="1dafd-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1dafd-115">See also</span></span>


[<span data-ttu-id="1dafd-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="1dafd-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)