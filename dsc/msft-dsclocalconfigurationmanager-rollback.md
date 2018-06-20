---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda RollBack klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: d2f9b7025d611912e119800408e25fcb66bc0228
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219882"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e359b-103">Metoda RollBack klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="e359b-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e359b-104">Przywraca konfigurację do poprzedniej wersji.</span><span class="sxs-lookup"><span data-stu-id="e359b-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="e359b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e359b-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="e359b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e359b-106">Parameters</span></span>
----------

<span data-ttu-id="e359b-107">*configurationNumber* \[w\] określa żądanej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e359b-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="e359b-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e359b-108">Return value</span></span>
------------

<span data-ttu-id="e359b-109">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="e359b-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e359b-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e359b-110">Remarks</span></span>

<span data-ttu-id="e359b-111">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="e359b-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e359b-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e359b-112">Requirements</span></span>
------------
><span data-ttu-id="e359b-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e359b-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="e359b-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e359b-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="e359b-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e359b-115">See also</span></span>


[<span data-ttu-id="e359b-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e359b-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)