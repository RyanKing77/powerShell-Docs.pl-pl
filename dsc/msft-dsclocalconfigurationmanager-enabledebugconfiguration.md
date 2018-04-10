---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda EnableDebugConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 9fe41fa806a6abff1d36dadd0c041a5cf0e78caf
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="41ae0-103">Metoda EnableDebugConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="41ae0-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="41ae0-104">Włącza debugowanie zasobów usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="41ae0-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="41ae0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="41ae0-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="41ae0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="41ae0-106">Parameters</span></span>
----------

<span data-ttu-id="41ae0-107">*BreakAll* \[w\] ustawia punkt przerwania w każdym wierszu skrypt zasobu.</span><span class="sxs-lookup"><span data-stu-id="41ae0-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="41ae0-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="41ae0-108">Return value</span></span>
------------

<span data-ttu-id="41ae0-109">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="41ae0-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="41ae0-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41ae0-110">Remarks</span></span>

<span data-ttu-id="41ae0-111">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="41ae0-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="41ae0-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="41ae0-112">Requirements</span></span>
------------
><span data-ttu-id="41ae0-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="41ae0-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="41ae0-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="41ae0-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="41ae0-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="41ae0-115">See also</span></span>


[<span data-ttu-id="41ae0-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="41ae0-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)