---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda StopConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 1cd887d205967c3d282143df4e6199027639230e
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893879"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="c068e-103">Metoda StopConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="c068e-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="c068e-104">Zatrzymuje zmian w konfiguracji, który jest w toku.</span><span class="sxs-lookup"><span data-stu-id="c068e-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="c068e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c068e-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="c068e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c068e-106">Parameters</span></span>

<span data-ttu-id="c068e-107">*Wymuś* \[w\] **true** wymusić konfigurację, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="c068e-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="c068e-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c068e-108">Return value</span></span>

<span data-ttu-id="c068e-109">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="c068e-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c068e-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c068e-110">Remarks</span></span>

<span data-ttu-id="c068e-111">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="c068e-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c068e-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c068e-112">Requirements</span></span>

<span data-ttu-id="c068e-113">**Plik MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c068e-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="c068e-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c068e-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="c068e-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c068e-115">See also</span></span>

[<span data-ttu-id="c068e-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c068e-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)