---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Metoda GetConfigurationStatus klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e02ed81a7b8436323bc68aaa2587a445e6a5adf9
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="8d1e0-103">Metoda GetConfigurationStatus klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="8d1e0-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="8d1e0-104">Podgląd historii stanu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8d1e0-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="8d1e0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8d1e0-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="8d1e0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8d1e0-106">Parameters</span></span>
----------

<span data-ttu-id="8d1e0-107">*Wszystkie* \[w\]</span><span class="sxs-lookup"><span data-stu-id="8d1e0-107">*All* \[in\]</span></span>  
<span data-ttu-id="8d1e0-108">**wartość true,** Jeśli ta metoda powinna zwrócić informacje o wszystkich konfiguracji jest uruchamiana na komputerze, w tym aplikacji konfiguracji i sprawdzanie spójności.</span><span class="sxs-lookup"><span data-stu-id="8d1e0-108">**true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="8d1e0-109">*configurationStatus* \[out\]</span><span class="sxs-lookup"><span data-stu-id="8d1e0-109">*configurationStatus* \[out\]</span></span>  
<span data-ttu-id="8d1e0-110">Przy powrocie, zawiera osadzony wystąpienia **MSFT_DSCConfigurationStatus** klasa, która definiuje ustawienia.</span><span class="sxs-lookup"><span data-stu-id="8d1e0-110">On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="8d1e0-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8d1e0-111">Return value</span></span>
------------

<span data-ttu-id="8d1e0-112">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="8d1e0-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8d1e0-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8d1e0-113">Remarks</span></span>

<span data-ttu-id="8d1e0-114">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="8d1e0-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8d1e0-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8d1e0-115">Requirements</span></span>
------------
><span data-ttu-id="8d1e0-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="8d1e0-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="8d1e0-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8d1e0-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="8d1e0-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8d1e0-118">See also</span></span>


[<span data-ttu-id="8d1e0-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="8d1e0-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



