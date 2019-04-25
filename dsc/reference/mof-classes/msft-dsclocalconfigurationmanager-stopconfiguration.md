---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda StopConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 1cd887d205967c3d282143df4e6199027639230e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078247"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="3e92f-103">Metoda StopConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="3e92f-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="3e92f-104">Zatrzymuje zmian w konfiguracji, który jest w toku.</span><span class="sxs-lookup"><span data-stu-id="3e92f-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="3e92f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e92f-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="3e92f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3e92f-106">Parameters</span></span>

<span data-ttu-id="3e92f-107">*Wymuś* \[w\] **true** wymusić konfigurację, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="3e92f-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="3e92f-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3e92f-108">Return value</span></span>

<span data-ttu-id="3e92f-109">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="3e92f-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3e92f-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3e92f-110">Remarks</span></span>

<span data-ttu-id="3e92f-111">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="3e92f-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3e92f-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3e92f-112">Requirements</span></span>

<span data-ttu-id="3e92f-113">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="3e92f-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="3e92f-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3e92f-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="3e92f-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3e92f-115">See also</span></span>

[<span data-ttu-id="3e92f-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3e92f-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)