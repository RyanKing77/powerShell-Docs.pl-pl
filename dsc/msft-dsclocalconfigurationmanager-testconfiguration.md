---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Metoda TestConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 8e9986837aaf41b1396a2399c58675bc51b0b708
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0ae38-103">Metoda TestConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="0ae38-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0ae38-104">Wysyła dokument konfiguracji do węzła zarządzanego i sprawdza bieżącą konfigurację względem dokumentu.</span><span class="sxs-lookup"><span data-stu-id="0ae38-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

<a name="syntax"></a><span data-ttu-id="0ae38-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0ae38-105">Syntax</span></span>
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a><span data-ttu-id="0ae38-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0ae38-106">Parameters</span></span>
----------

<span data-ttu-id="0ae38-107">*configurationData* \[w\]</span><span class="sxs-lookup"><span data-stu-id="0ae38-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="0ae38-108">Dane środowisko confuguration.</span><span class="sxs-lookup"><span data-stu-id="0ae38-108">Environment data for the confuguration.</span></span>

<span data-ttu-id="0ae38-109">*InDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="0ae38-109">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="0ae38-110">Przy powrocie Określa, czy węzeł zarządzany jest w stanie określony dokument konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0ae38-110">On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="0ae38-111">*ResourcesInDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="0ae38-111">*ResourcesInDesiredState* \[out\]</span></span>  
<span data-ttu-id="0ae38-112">Przy powrocie, zawiera osadzony wystąpienia **MSFT_ResourceInDesiredState** klasy, która określa zasoby, które są w żądanym stanie.</span><span class="sxs-lookup"><span data-stu-id="0ae38-112">On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="0ae38-113">*ResourcesNotInDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="0ae38-113">*ResourcesNotInDesiredState* \[out\]</span></span>  
<span data-ttu-id="0ae38-114">Przy powrocie, zawiera osadzony wystąpienia **MSFT_ResourceNotInDesiredState** klasy, która określa zasoby, które nie są w żądanym stanie.</span><span class="sxs-lookup"><span data-stu-id="0ae38-114">On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="0ae38-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0ae38-115">Return value</span></span>
------------

<span data-ttu-id="0ae38-116">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="0ae38-116">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0ae38-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0ae38-117">Remarks</span></span>

<span data-ttu-id="0ae38-118">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="0ae38-118">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0ae38-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0ae38-119">Requirements</span></span>
------------
><span data-ttu-id="0ae38-120">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0ae38-120">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="0ae38-121">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0ae38-121">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="0ae38-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0ae38-122">See also</span></span>


[<span data-ttu-id="0ae38-123">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0ae38-123">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



