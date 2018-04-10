---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda GetConfigurationStatus klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: dde4ac003b346018561481e05ca7374475f9ff1d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="09ca6-103">Metoda GetConfigurationStatus klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="09ca6-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="09ca6-104">Podgląd historii stanu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="09ca6-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="09ca6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="09ca6-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="09ca6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="09ca6-106">Parameters</span></span>
----------

<span data-ttu-id="09ca6-107">*Wszystkie* \[w\] **true** Jeśli ta metoda powinna zwrócić informacje o wszystkich konfiguracji jest uruchamiana na komputerze, w tym aplikacji konfiguracji i sprawdzanie spójności.</span><span class="sxs-lookup"><span data-stu-id="09ca6-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="09ca6-108">*configurationStatus* \[limit\] przy powrocie, zawiera osadzony wystąpienia **MSFT_DSCConfigurationStatus** klasa, która definiuje ustawienia.</span><span class="sxs-lookup"><span data-stu-id="09ca6-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="09ca6-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="09ca6-109">Return value</span></span>
------------

<span data-ttu-id="09ca6-110">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="09ca6-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="09ca6-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="09ca6-111">Remarks</span></span>

<span data-ttu-id="09ca6-112">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="09ca6-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="09ca6-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="09ca6-113">Requirements</span></span>
------------
><span data-ttu-id="09ca6-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="09ca6-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="09ca6-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="09ca6-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="09ca6-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="09ca6-116">See also</span></span>


[<span data-ttu-id="09ca6-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="09ca6-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)