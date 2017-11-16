---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Metoda RemoveConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: faa113c442b80eea3ac474220b098b7d80ec50a8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="1f2c3-103">Metoda RemoveConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="1f2c3-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="1f2c3-104">Usuwa pliki konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1f2c3-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="1f2c3-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f2c3-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="1f2c3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f2c3-106">Parameters</span></span>
----------

<span data-ttu-id="1f2c3-107">*Etap* \[w\]</span><span class="sxs-lookup"><span data-stu-id="1f2c3-107">*Stage* \[in\]</span></span>  
<span data-ttu-id="1f2c3-108">Określa, który dokument konfiguracji do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="1f2c3-108">Specifies which configuration document to remove.</span></span> <span data-ttu-id="1f2c3-109">Prawidłowe są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="1f2c3-109">The following values are valid:</span></span>

|<span data-ttu-id="1f2c3-110">Wartość</span><span class="sxs-lookup"><span data-stu-id="1f2c3-110">Value</span></span> |<span data-ttu-id="1f2c3-111">Opis</span><span class="sxs-lookup"><span data-stu-id="1f2c3-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="1f2c3-112">**1**</span><span class="sxs-lookup"><span data-stu-id="1f2c3-112">**1**</span></span> | <span data-ttu-id="1f2c3-113">**Bieżącego** dokumentu konfiguracji (current.mof).</span><span class="sxs-lookup"><span data-stu-id="1f2c3-113">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="1f2c3-114">**2**</span><span class="sxs-lookup"><span data-stu-id="1f2c3-114">**2**</span></span> | <span data-ttu-id="1f2c3-115">**Oczekujące** dokumentu konfiguracji (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="1f2c3-115">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="1f2c3-116">**4**</span><span class="sxs-lookup"><span data-stu-id="1f2c3-116">**4**</span></span> | <span data-ttu-id="1f2c3-117">**Wstecz** dokumentu konfiguracji (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="1f2c3-117">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="1f2c3-118">*Wymuś* \[w\]</span><span class="sxs-lookup"><span data-stu-id="1f2c3-118">*Force* \[in\]</span></span>  
<span data-ttu-id="1f2c3-119">**wartość true,** wymuszenie usunięcia konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1f2c3-119">**true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="1f2c3-120">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1f2c3-120">Return value</span></span>
------------

<span data-ttu-id="1f2c3-121">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="1f2c3-121">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="1f2c3-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1f2c3-122">Remarks</span></span>

<span data-ttu-id="1f2c3-123">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="1f2c3-123">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1f2c3-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1f2c3-124">Requirements</span></span>
------------
><span data-ttu-id="1f2c3-125">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="1f2c3-125">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="1f2c3-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="1f2c3-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="1f2c3-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f2c3-127">See also</span></span>


[<span data-ttu-id="1f2c3-128">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="1f2c3-128">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



