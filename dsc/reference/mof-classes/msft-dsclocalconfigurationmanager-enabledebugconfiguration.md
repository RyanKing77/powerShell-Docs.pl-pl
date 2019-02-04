---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda EnableDebugConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b2eaebfa901cb5d93fd0183287073e6b31f975d1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684808"
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="3ede4-103">Metoda EnableDebugConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="3ede4-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="3ede4-104">Włącza debugowanie zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="3ede4-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="3ede4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3ede4-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="3ede4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3ede4-106">Parameters</span></span>

<span data-ttu-id="3ede4-107">*BreakAll* \[w\] ustawia punkt przerwania na każdy wiersz w pliku skryptu zasobu.</span><span class="sxs-lookup"><span data-stu-id="3ede4-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="3ede4-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3ede4-108">Return value</span></span>

<span data-ttu-id="3ede4-109">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="3ede4-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3ede4-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3ede4-110">Remarks</span></span>

<span data-ttu-id="3ede4-111">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="3ede4-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3ede4-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3ede4-112">Requirements</span></span>

<span data-ttu-id="3ede4-113">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="3ede4-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="3ede4-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3ede4-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="3ede4-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ede4-115">See also</span></span>

[<span data-ttu-id="3ede4-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3ede4-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)