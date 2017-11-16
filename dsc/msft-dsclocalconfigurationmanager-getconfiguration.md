---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "GetConfiguration — metoda klasy MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 96676a76a0302543e5e4a214c82ed952d7f52a71
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="943aa-103">GetConfiguration — metoda klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="943aa-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="943aa-104">Wysyła dokument konfiguracji do węzła zarządzanego i używa **uzyskać** metody Agent konfiguracji, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="943aa-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="943aa-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="943aa-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="943aa-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="943aa-106">Parameters</span></span>
----------

<span data-ttu-id="943aa-107">*configurationData* \[w\]</span><span class="sxs-lookup"><span data-stu-id="943aa-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="943aa-108">Określa dane konfiguracji do wysłania.</span><span class="sxs-lookup"><span data-stu-id="943aa-108">Specifies the configuration data to send.</span></span>

<span data-ttu-id="943aa-109">*konfiguracje* \[out\]</span><span class="sxs-lookup"><span data-stu-id="943aa-109">*configurations* \[out\]</span></span>  
<span data-ttu-id="943aa-110">Przy powrocie zawiera osadzony wystąpienia konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="943aa-110">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="943aa-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="943aa-111">Return value</span></span>
------------

<span data-ttu-id="943aa-112">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="943aa-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="943aa-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="943aa-113">Remarks</span></span>

<span data-ttu-id="943aa-114">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="943aa-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="943aa-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="943aa-115">Requirements</span></span>
------------
><span data-ttu-id="943aa-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="943aa-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="943aa-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="943aa-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="943aa-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="943aa-118">See also</span></span>


[<span data-ttu-id="943aa-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="943aa-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



