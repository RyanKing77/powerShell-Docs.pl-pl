---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "GetConfiguration — metoda klasy MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 60f4b49575dbb28ce74af0500e6982ec5d2e7a66
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="a83a9-103">GetConfiguration — metoda klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="a83a9-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a83a9-104">Wysyła dokument konfiguracji do węzła zarządzanego i używa **uzyskać** metody Agent konfiguracji, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="a83a9-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="a83a9-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a83a9-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="a83a9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a83a9-106">Parameters</span></span>
----------

<span data-ttu-id="a83a9-107">*configurationData* \[w\]</span><span class="sxs-lookup"><span data-stu-id="a83a9-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="a83a9-108">Określa dane konfiguracji do wysłania.</span><span class="sxs-lookup"><span data-stu-id="a83a9-108">Specifies the configuration data to send.</span></span>

<span data-ttu-id="a83a9-109">*konfiguracje* \[out\]</span><span class="sxs-lookup"><span data-stu-id="a83a9-109">*configurations* \[out\]</span></span>  
<span data-ttu-id="a83a9-110">Przy powrocie zawiera osadzony wystąpienia konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a83a9-110">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="a83a9-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a83a9-111">Return value</span></span>
------------

<span data-ttu-id="a83a9-112">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="a83a9-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a83a9-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a83a9-113">Remarks</span></span>

<span data-ttu-id="a83a9-114">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="a83a9-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a83a9-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a83a9-115">Requirements</span></span>
------------
><span data-ttu-id="a83a9-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a83a9-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="a83a9-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a83a9-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="a83a9-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a83a9-118">See also</span></span>


[<span data-ttu-id="a83a9-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a83a9-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



