---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Metoda ResourceGet klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: df90cb6859413c94be992c8cbc30171e9bd3d6de
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4d339-103">Metoda ResourceGet klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="4d339-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4d339-104">Bezpośrednio wywołuje **uzyskać** metody zasobu usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="4d339-104">Directly calls the **Get** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="4d339-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d339-105">Syntax</span></span>
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a><span data-ttu-id="4d339-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d339-106">Parameters</span></span>
----------

<span data-ttu-id="4d339-107">*Typ zasobu* \[w\]</span><span class="sxs-lookup"><span data-stu-id="4d339-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="4d339-108">Nazwa zasobu do wywołania.</span><span class="sxs-lookup"><span data-stu-id="4d339-108">The name of the resource to call.</span></span>

<span data-ttu-id="4d339-109">*Nazwa modułu* \[w\]</span><span class="sxs-lookup"><span data-stu-id="4d339-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="4d339-110">Nazwa modułu, który zawiera zasób do wywołania.</span><span class="sxs-lookup"><span data-stu-id="4d339-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="4d339-111">*Właściwość resourceProperty* \[w\]</span><span class="sxs-lookup"><span data-stu-id="4d339-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="4d339-112">Określa nazwę właściwości zasobów i jego wartość w tablicy skrótów klucz i wartość, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="4d339-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="4d339-113">Użyj [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) polecenia cmdlet, aby wykryć właściwości zasobów i ich typów.</span><span class="sxs-lookup"><span data-stu-id="4d339-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="4d339-114">*konfiguracje* \[out\]</span><span class="sxs-lookup"><span data-stu-id="4d339-114">*configurations* \[out\]</span></span>  
<span data-ttu-id="4d339-115">Przy powrocie zawiera osadzony wystąpienia konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4d339-115">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="4d339-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4d339-116">Return value</span></span>
------------

<span data-ttu-id="4d339-117">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="4d339-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4d339-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4d339-118">Remarks</span></span>

<span data-ttu-id="4d339-119">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="4d339-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4d339-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4d339-120">Requirements</span></span>
------------
><span data-ttu-id="4d339-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4d339-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="4d339-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4d339-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="4d339-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d339-123">See also</span></span>


[<span data-ttu-id="4d339-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4d339-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



