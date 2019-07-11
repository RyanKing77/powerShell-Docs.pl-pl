---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda EnableDebugConfiguration
ms.openlocfilehash: f1290e4d898332361850ffc85aa0a8d79863c8f7
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727150"
---
# <a name="enabledebugconfiguration-method"></a><span data-ttu-id="7f77f-103">Metoda EnableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="7f77f-103">EnableDebugConfiguration method</span></span>

<span data-ttu-id="7f77f-104">Włącza debugowanie zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="7f77f-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="7f77f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7f77f-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="7f77f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f77f-106">Parameters</span></span>

<span data-ttu-id="7f77f-107">*BreakAll* \[w\] ustawia punkt przerwania na każdy wiersz w pliku skryptu zasobu.</span><span class="sxs-lookup"><span data-stu-id="7f77f-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="7f77f-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7f77f-108">Return value</span></span>

<span data-ttu-id="7f77f-109">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="7f77f-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7f77f-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7f77f-110">Remarks</span></span>

<span data-ttu-id="7f77f-111">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="7f77f-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7f77f-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7f77f-112">Requirements</span></span>

<span data-ttu-id="7f77f-113">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7f77f-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="7f77f-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7f77f-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="7f77f-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7f77f-115">See also</span></span>

[<span data-ttu-id="7f77f-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7f77f-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
