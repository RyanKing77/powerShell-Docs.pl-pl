---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda GetConfigurationStatus klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: c66ccc4eefaef2d0c3a68fa8a96c5abb9bda6e4c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686642"
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="33bd9-103">Metoda GetConfigurationStatus klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="33bd9-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="33bd9-104">Pobieranie historii stanu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="33bd9-104">Get the configuration status history.</span></span>

## <a name="syntax"></a><span data-ttu-id="33bd9-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="33bd9-105">Syntax</span></span>

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a><span data-ttu-id="33bd9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="33bd9-106">Parameters</span></span>

<span data-ttu-id="33bd9-107">*Wszystkie* \[w\] **true** Jeśli ta metoda powinna zwrócić informacje na temat wszystkich konfiguracji jest uruchamiana na komputerze, łącznie z konfiguracji aplikacji i sprawdzanie spójności.</span><span class="sxs-lookup"><span data-stu-id="33bd9-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="33bd9-108">*configurationStatus* \[się\] przy powrocie, zawiera osadzony wystąpienia **MSFT_DSCConfigurationStatus** klasę, która definiuje ustawienia.</span><span class="sxs-lookup"><span data-stu-id="33bd9-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="33bd9-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="33bd9-109">Return value</span></span>

<span data-ttu-id="33bd9-110">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="33bd9-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="33bd9-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="33bd9-111">Remarks</span></span>

<span data-ttu-id="33bd9-112">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="33bd9-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="33bd9-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33bd9-113">Requirements</span></span>

<span data-ttu-id="33bd9-114">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="33bd9-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="33bd9-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="33bd9-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="33bd9-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="33bd9-116">See also</span></span>

[<span data-ttu-id="33bd9-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="33bd9-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)