---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda GetConfigurationStatus
ms.openlocfilehash: 83b30ba2612d962fcf2fa658d07d18fb2d91ccc7
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734514"
---
# <a name="getconfigurationstatus-method"></a><span data-ttu-id="29116-103">Metoda GetConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="29116-103">GetConfigurationStatus method</span></span>

<span data-ttu-id="29116-104">Pobieranie historii stanu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="29116-104">Get the configuration status history.</span></span>

## <a name="syntax"></a><span data-ttu-id="29116-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="29116-105">Syntax</span></span>

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a><span data-ttu-id="29116-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="29116-106">Parameters</span></span>

<span data-ttu-id="29116-107">*Wszystkie* \[w\] **true** Jeśli ta metoda powinna zwrócić informacje na temat wszystkich konfiguracji jest uruchamiana na komputerze, łącznie z konfiguracji aplikacji i sprawdzanie spójności.</span><span class="sxs-lookup"><span data-stu-id="29116-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="29116-108">*configurationStatus* \[się\] przy powrocie, zawiera osadzony wystąpienia **MSFT_DSCConfigurationStatus** klasę, która definiuje ustawienia.</span><span class="sxs-lookup"><span data-stu-id="29116-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="29116-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="29116-109">Return value</span></span>

<span data-ttu-id="29116-110">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="29116-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="29116-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="29116-111">Remarks</span></span>

<span data-ttu-id="29116-112">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="29116-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="29116-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="29116-113">Requirements</span></span>

<span data-ttu-id="29116-114">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="29116-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="29116-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="29116-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="29116-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29116-116">See also</span></span>

[<span data-ttu-id="29116-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="29116-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
