---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda StopConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 1cd887d205967c3d282143df4e6199027639230e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405257"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="be92c-103">Metoda StopConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="be92c-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="be92c-104">Zatrzymuje zmian w konfiguracji, który jest w toku.</span><span class="sxs-lookup"><span data-stu-id="be92c-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="be92c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="be92c-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="be92c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="be92c-106">Parameters</span></span>

<span data-ttu-id="be92c-107">*Wymuś* \[w\] **true** wymusić konfigurację, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="be92c-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="be92c-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="be92c-108">Return value</span></span>

<span data-ttu-id="be92c-109">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="be92c-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="be92c-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="be92c-110">Remarks</span></span>

<span data-ttu-id="be92c-111">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="be92c-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="be92c-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="be92c-112">Requirements</span></span>

<span data-ttu-id="be92c-113">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="be92c-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="be92c-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="be92c-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="be92c-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="be92c-115">See also</span></span>

[<span data-ttu-id="be92c-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="be92c-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)