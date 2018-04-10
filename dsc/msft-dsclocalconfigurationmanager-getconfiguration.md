---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda GetConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 07d7db9dcc4288e6b72d5df37d82e44eb6f72ad2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ef038-103">Metoda GetConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="ef038-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ef038-104">Wysyła dokument konfiguracji do węzła zarządzanego i używa **uzyskać** metody Agent konfiguracji, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="ef038-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="ef038-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ef038-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="ef038-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ef038-106">Parameters</span></span>
----------

<span data-ttu-id="ef038-107">*configurationData* \[w\] Określa dane konfiguracji do wysłania.</span><span class="sxs-lookup"><span data-stu-id="ef038-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="ef038-108">*konfiguracje* \[limit\] przy powrocie, zawiera osadzony wystąpienia konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ef038-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="ef038-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ef038-109">Return value</span></span>
------------

<span data-ttu-id="ef038-110">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="ef038-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ef038-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ef038-111">Remarks</span></span>

<span data-ttu-id="ef038-112">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="ef038-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ef038-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ef038-113">Requirements</span></span>
------------
><span data-ttu-id="ef038-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ef038-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="ef038-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ef038-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="ef038-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ef038-116">See also</span></span>


[<span data-ttu-id="ef038-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ef038-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)