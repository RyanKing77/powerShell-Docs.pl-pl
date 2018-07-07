---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda EnableDebugConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b2eaebfa901cb5d93fd0183287073e6b31f975d1
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892403"
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="00ef5-103">Metoda EnableDebugConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="00ef5-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="00ef5-104">Włącza debugowanie zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="00ef5-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="00ef5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="00ef5-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="00ef5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="00ef5-106">Parameters</span></span>

<span data-ttu-id="00ef5-107">*BreakAll* \[w\] ustawia punkt przerwania na każdy wiersz w pliku skryptu zasobu.</span><span class="sxs-lookup"><span data-stu-id="00ef5-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="00ef5-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="00ef5-108">Return value</span></span>

<span data-ttu-id="00ef5-109">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="00ef5-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="00ef5-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="00ef5-110">Remarks</span></span>

<span data-ttu-id="00ef5-111">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="00ef5-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="00ef5-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="00ef5-112">Requirements</span></span>

<span data-ttu-id="00ef5-113">**Plik MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="00ef5-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="00ef5-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="00ef5-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="00ef5-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="00ef5-115">See also</span></span>

[<span data-ttu-id="00ef5-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="00ef5-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)