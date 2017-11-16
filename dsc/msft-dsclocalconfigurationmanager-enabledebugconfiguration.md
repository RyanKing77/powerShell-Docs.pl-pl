---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Metoda EnableDebugConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 7220c972b3f43b4697cf71df54d2d43881938367
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="61091-103">Metoda EnableDebugConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="61091-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="61091-104">Włącza debugowanie zasobów usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="61091-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="61091-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="61091-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="61091-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="61091-106">Parameters</span></span>
----------

<span data-ttu-id="61091-107">*BreakAll* \[w\]</span><span class="sxs-lookup"><span data-stu-id="61091-107">*BreakAll* \[in\]</span></span>  
<span data-ttu-id="61091-108">Ustawia punkt przerwania w każdym wierszu skrypt zasobu.</span><span class="sxs-lookup"><span data-stu-id="61091-108">Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="61091-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="61091-109">Return value</span></span>
------------

<span data-ttu-id="61091-110">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="61091-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="61091-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="61091-111">Remarks</span></span>

<span data-ttu-id="61091-112">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="61091-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="61091-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="61091-113">Requirements</span></span>
------------
><span data-ttu-id="61091-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="61091-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="61091-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="61091-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="61091-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="61091-116">See also</span></span>


[<span data-ttu-id="61091-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="61091-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



