---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda EnableDebugConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 9e2a978f9d16abaed959be022229db4da5fd65bd
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7573e-103">Metoda EnableDebugConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="7573e-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7573e-104">Włącza debugowanie zasobów usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="7573e-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="7573e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7573e-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="7573e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7573e-106">Parameters</span></span>
----------

<span data-ttu-id="7573e-107">*BreakAll* \[w\] ustawia punkt przerwania w każdym wierszu skrypt zasobu.</span><span class="sxs-lookup"><span data-stu-id="7573e-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="7573e-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7573e-108">Return value</span></span>
------------

<span data-ttu-id="7573e-109">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="7573e-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7573e-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7573e-110">Remarks</span></span>

<span data-ttu-id="7573e-111">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="7573e-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7573e-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7573e-112">Requirements</span></span>
------------
><span data-ttu-id="7573e-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7573e-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="7573e-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7573e-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="7573e-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7573e-115">See also</span></span>


[<span data-ttu-id="7573e-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7573e-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)