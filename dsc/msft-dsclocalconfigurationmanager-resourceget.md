---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Metoda ResourceGet klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 2c055b3fab468f85c9e2f91cf1eaf1a4353b4660
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="455db-103">Metoda ResourceGet klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="455db-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="455db-104">Bezpośrednio wywołuje **uzyskać** metody zasobu usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="455db-104">Directly calls the **Get** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="455db-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="455db-105">Syntax</span></span>
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a><span data-ttu-id="455db-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="455db-106">Parameters</span></span>
----------

<span data-ttu-id="455db-107">*Typ zasobu* \[w\]</span><span class="sxs-lookup"><span data-stu-id="455db-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="455db-108">Nazwa zasobu do wywołania.</span><span class="sxs-lookup"><span data-stu-id="455db-108">The name of the resource to call.</span></span>

<span data-ttu-id="455db-109">*Nazwa modułu* \[w\]</span><span class="sxs-lookup"><span data-stu-id="455db-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="455db-110">Nazwa modułu, który zawiera zasób do wywołania.</span><span class="sxs-lookup"><span data-stu-id="455db-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="455db-111">*Właściwość resourceProperty* \[w\]</span><span class="sxs-lookup"><span data-stu-id="455db-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="455db-112">Określa nazwę właściwości zasobów i jego wartość w tablicy skrótów klucz i wartość, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="455db-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="455db-113">Użyj [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) polecenia cmdlet, aby wykryć właściwości zasobów i ich typów.</span><span class="sxs-lookup"><span data-stu-id="455db-113">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="455db-114">*konfiguracje* \[out\]</span><span class="sxs-lookup"><span data-stu-id="455db-114">*configurations* \[out\]</span></span>  
<span data-ttu-id="455db-115">Przy powrocie zawiera osadzony wystąpienia konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="455db-115">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="455db-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="455db-116">Return value</span></span>
------------

<span data-ttu-id="455db-117">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="455db-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="455db-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="455db-118">Remarks</span></span>

<span data-ttu-id="455db-119">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="455db-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="455db-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="455db-120">Requirements</span></span>
------------
><span data-ttu-id="455db-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="455db-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="455db-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="455db-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="455db-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="455db-123">See also</span></span>


[<span data-ttu-id="455db-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="455db-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



