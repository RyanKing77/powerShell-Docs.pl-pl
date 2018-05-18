---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda RemoveConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: c68d17d38336dec08e078366ea5f2071fcf7c5a8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="3c412-103">Metoda RemoveConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="3c412-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="3c412-104">Usuwa pliki konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3c412-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="3c412-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3c412-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="3c412-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3c412-106">Parameters</span></span>
----------

<span data-ttu-id="3c412-107">*Etap* \[w\] Określa, który dokument konfiguracji do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="3c412-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="3c412-108">Prawidłowe są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="3c412-108">The following values are valid:</span></span>

|<span data-ttu-id="3c412-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="3c412-109">Value</span></span> |<span data-ttu-id="3c412-110">Opis</span><span class="sxs-lookup"><span data-stu-id="3c412-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="3c412-111">**1**</span><span class="sxs-lookup"><span data-stu-id="3c412-111">**1**</span></span> | <span data-ttu-id="3c412-112">**Bieżącego** dokumentu konfiguracji (current.mof).</span><span class="sxs-lookup"><span data-stu-id="3c412-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="3c412-113">**2**</span><span class="sxs-lookup"><span data-stu-id="3c412-113">**2**</span></span> | <span data-ttu-id="3c412-114">**Oczekujące** dokumentu konfiguracji (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="3c412-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="3c412-115">**4**</span><span class="sxs-lookup"><span data-stu-id="3c412-115">**4**</span></span> | <span data-ttu-id="3c412-116">**Wstecz** dokumentu konfiguracji (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="3c412-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="3c412-117">*Wymuś* \[w\] **true** wymuszenie usunięcia konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3c412-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="3c412-118">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3c412-118">Return value</span></span>
------------

<span data-ttu-id="3c412-119">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="3c412-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3c412-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3c412-120">Remarks</span></span>

<span data-ttu-id="3c412-121">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="3c412-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3c412-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3c412-122">Requirements</span></span>
------------
><span data-ttu-id="3c412-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="3c412-123">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="3c412-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3c412-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="3c412-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3c412-125">See also</span></span>


[<span data-ttu-id="3c412-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3c412-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)