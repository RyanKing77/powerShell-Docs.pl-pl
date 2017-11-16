---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "RollBack — metoda klasy MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: b8597e3eb7872d9894863fb02d927c9f475da44c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7c271-103">RollBack — metoda klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="7c271-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7c271-104">Przywraca konfigurację do poprzedniej wersji.</span><span class="sxs-lookup"><span data-stu-id="7c271-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="7c271-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c271-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="7c271-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c271-106">Parameters</span></span>
----------

<span data-ttu-id="7c271-107">*configurationNumber* \[w\]</span><span class="sxs-lookup"><span data-stu-id="7c271-107">*configurationNumber* \[in\]</span></span>  
<span data-ttu-id="7c271-108">Określa żądanej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7c271-108">Specifies the requested configuration.</span></span> 

## <a name="return-value"></a><span data-ttu-id="7c271-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7c271-109">Return value</span></span>
------------

<span data-ttu-id="7c271-110">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="7c271-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7c271-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7c271-111">Remarks</span></span>

<span data-ttu-id="7c271-112">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="7c271-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7c271-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7c271-113">Requirements</span></span>
------------
><span data-ttu-id="7c271-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7c271-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="7c271-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7c271-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="7c271-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7c271-116">See also</span></span>


[<span data-ttu-id="7c271-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7c271-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



