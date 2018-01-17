---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Metoda StopConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 66d00cb40750e91e4b369a2e8cebb449697406d9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="dbd0b-103">Metoda StopConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="dbd0b-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="dbd0b-104">Zatrzymuje zmian w konfiguracji jest w toku.</span><span class="sxs-lookup"><span data-stu-id="dbd0b-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="dbd0b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="dbd0b-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="dbd0b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="dbd0b-106">Parameters</span></span>
----------

<span data-ttu-id="dbd0b-107">*Wymuś* \[w\]</span><span class="sxs-lookup"><span data-stu-id="dbd0b-107">*force* \[in\]</span></span>  
<span data-ttu-id="dbd0b-108">**wartość true,** wymusić konfigurację, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="dbd0b-108">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="dbd0b-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dbd0b-109">Return value</span></span>
------------

<span data-ttu-id="dbd0b-110">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="dbd0b-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="dbd0b-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dbd0b-111">Remarks</span></span>

<span data-ttu-id="dbd0b-112">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="dbd0b-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="dbd0b-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dbd0b-113">Requirements</span></span>
------------
><span data-ttu-id="dbd0b-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="dbd0b-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="dbd0b-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="dbd0b-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="dbd0b-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dbd0b-116">See also</span></span>


[<span data-ttu-id="dbd0b-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="dbd0b-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



