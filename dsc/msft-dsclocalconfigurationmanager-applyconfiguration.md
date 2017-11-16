---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Metoda ApplyConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: febaf972a2a452eb9aaf3ec7fbc5e41f3f463a58
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="5a75f-103">Metoda ApplyConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="5a75f-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="5a75f-104">Używa agenta konfiguracji umożliwiają zastosowanie konfiguracji, który jest w stanie oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="5a75f-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span> 

<span data-ttu-id="5a75f-105">Jeśli nie istnieje konfiguracja oczekujących, ta metoda przywrócenie bieżącej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5a75f-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>


## <a name="syntax"></a><span data-ttu-id="5a75f-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a75f-106">Syntax</span></span>
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="5a75f-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="5a75f-107">Parameters</span></span>
----------

<span data-ttu-id="5a75f-108">*Wymuś* \[w\]</span><span class="sxs-lookup"><span data-stu-id="5a75f-108">*force* \[in\]</span></span>  
<span data-ttu-id="5a75f-109">Jeśli jest to **true**, stosowana bieżącej konfiguracji, nawet jeśli istnieje oczekująca konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="5a75f-109">If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="5a75f-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5a75f-110">Return value</span></span>
------------

<span data-ttu-id="5a75f-111">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="5a75f-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5a75f-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5a75f-112">Remarks</span></span>

<span data-ttu-id="5a75f-113">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="5a75f-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5a75f-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5a75f-114">Requirements</span></span>
------------
><span data-ttu-id="5a75f-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5a75f-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="5a75f-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5a75f-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="5a75f-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a75f-117">See also</span></span>


[<span data-ttu-id="5a75f-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5a75f-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



