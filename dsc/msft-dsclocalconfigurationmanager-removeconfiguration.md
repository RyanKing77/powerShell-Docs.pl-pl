---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Metoda RemoveConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: fed45836293adedbce18f01cfe53cdfa1a474975
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0dfe4-103">Metoda RemoveConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="0dfe4-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0dfe4-104">Usuwa pliki konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0dfe4-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="0dfe4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0dfe4-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="0dfe4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0dfe4-106">Parameters</span></span>
----------

<span data-ttu-id="0dfe4-107">*Etap* \[w\]</span><span class="sxs-lookup"><span data-stu-id="0dfe4-107">*Stage* \[in\]</span></span>  
<span data-ttu-id="0dfe4-108">Określa, który dokument konfiguracji do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="0dfe4-108">Specifies which configuration document to remove.</span></span> <span data-ttu-id="0dfe4-109">Prawidłowe są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="0dfe4-109">The following values are valid:</span></span>

|<span data-ttu-id="0dfe4-110">Wartość</span><span class="sxs-lookup"><span data-stu-id="0dfe4-110">Value</span></span> |<span data-ttu-id="0dfe4-111">Opis</span><span class="sxs-lookup"><span data-stu-id="0dfe4-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="0dfe4-112">**1**</span><span class="sxs-lookup"><span data-stu-id="0dfe4-112">**1**</span></span> | <span data-ttu-id="0dfe4-113">**Bieżącego** dokumentu konfiguracji (current.mof).</span><span class="sxs-lookup"><span data-stu-id="0dfe4-113">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="0dfe4-114">**2**</span><span class="sxs-lookup"><span data-stu-id="0dfe4-114">**2**</span></span> | <span data-ttu-id="0dfe4-115">**Oczekujące** dokumentu konfiguracji (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="0dfe4-115">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="0dfe4-116">**4**</span><span class="sxs-lookup"><span data-stu-id="0dfe4-116">**4**</span></span> | <span data-ttu-id="0dfe4-117">**Wstecz** dokumentu konfiguracji (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="0dfe4-117">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="0dfe4-118">*Wymuś* \[w\]</span><span class="sxs-lookup"><span data-stu-id="0dfe4-118">*Force* \[in\]</span></span>  
<span data-ttu-id="0dfe4-119">**wartość true,** wymuszenie usunięcia konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0dfe4-119">**true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="0dfe4-120">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0dfe4-120">Return value</span></span>
------------

<span data-ttu-id="0dfe4-121">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="0dfe4-121">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0dfe4-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0dfe4-122">Remarks</span></span>

<span data-ttu-id="0dfe4-123">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="0dfe4-123">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0dfe4-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0dfe4-124">Requirements</span></span>
------------
><span data-ttu-id="0dfe4-125">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0dfe4-125">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="0dfe4-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0dfe4-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="0dfe4-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0dfe4-127">See also</span></span>


[<span data-ttu-id="0dfe4-128">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0dfe4-128">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



