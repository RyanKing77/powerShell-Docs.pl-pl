---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda GetConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 46eec896df643996bea5f2c371a9294034caae6b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="a2887-103">Metoda GetConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="a2887-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a2887-104">Wysyła dokument konfiguracji do węzła zarządzanego i używa **uzyskać** metody Agent konfiguracji, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="a2887-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="a2887-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2887-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="a2887-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2887-106">Parameters</span></span>
----------

<span data-ttu-id="a2887-107">*configurationData* \[w\] Określa dane konfiguracji do wysłania.</span><span class="sxs-lookup"><span data-stu-id="a2887-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="a2887-108">*konfiguracje* \[limit\] przy powrocie, zawiera osadzony wystąpienia konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a2887-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="a2887-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a2887-109">Return value</span></span>
------------

<span data-ttu-id="a2887-110">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="a2887-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a2887-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a2887-111">Remarks</span></span>

<span data-ttu-id="a2887-112">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="a2887-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a2887-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a2887-113">Requirements</span></span>
------------
><span data-ttu-id="a2887-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a2887-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="a2887-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a2887-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="a2887-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2887-116">See also</span></span>


[<span data-ttu-id="a2887-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a2887-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)