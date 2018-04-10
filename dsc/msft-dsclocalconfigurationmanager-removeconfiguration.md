---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda RemoveConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e0ae8a50212b70841d210d7b2d666a2855218d1a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="6256f-103">Metoda RemoveConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="6256f-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="6256f-104">Usuwa pliki konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6256f-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="6256f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6256f-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="6256f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6256f-106">Parameters</span></span>
----------

<span data-ttu-id="6256f-107">*Etap* \[w\] Określa, który dokument konfiguracji do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="6256f-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="6256f-108">Prawidłowe są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="6256f-108">The following values are valid:</span></span>

|<span data-ttu-id="6256f-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="6256f-109">Value</span></span> |<span data-ttu-id="6256f-110">Opis</span><span class="sxs-lookup"><span data-stu-id="6256f-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="6256f-111">**1**</span><span class="sxs-lookup"><span data-stu-id="6256f-111">**1**</span></span> | <span data-ttu-id="6256f-112">**Bieżącego** dokumentu konfiguracji (current.mof).</span><span class="sxs-lookup"><span data-stu-id="6256f-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="6256f-113">**2**</span><span class="sxs-lookup"><span data-stu-id="6256f-113">**2**</span></span> | <span data-ttu-id="6256f-114">**Oczekujące** dokumentu konfiguracji (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="6256f-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="6256f-115">**4**</span><span class="sxs-lookup"><span data-stu-id="6256f-115">**4**</span></span> | <span data-ttu-id="6256f-116">**Wstecz** dokumentu konfiguracji (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="6256f-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="6256f-117">*Wymuś* \[w\] **true** wymuszenie usunięcia konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6256f-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="6256f-118">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6256f-118">Return value</span></span>
------------

<span data-ttu-id="6256f-119">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="6256f-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="6256f-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6256f-120">Remarks</span></span>

<span data-ttu-id="6256f-121">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="6256f-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="6256f-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6256f-122">Requirements</span></span>
------------
><span data-ttu-id="6256f-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="6256f-123">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="6256f-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="6256f-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="6256f-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6256f-125">See also</span></span>


[<span data-ttu-id="6256f-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="6256f-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)