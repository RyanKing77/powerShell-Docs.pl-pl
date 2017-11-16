---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Metoda ResourceSet klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 9cd9c1b3f58a5862db6c4eea0488423b8dfe7310
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="924e1-103">Metoda ResourceSet klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="924e1-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="924e1-104">Bezpośrednio wywołuje **ustawić** metody zasobu usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="924e1-104">Directly calls the **Set** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="924e1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="924e1-105">Syntax</span></span>
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

<a name="parameters"></a><span data-ttu-id="924e1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="924e1-106">Parameters</span></span>
----------

<span data-ttu-id="924e1-107">*Typ zasobu* \[w\]</span><span class="sxs-lookup"><span data-stu-id="924e1-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="924e1-108">Nazwa zasobu do wywołania.</span><span class="sxs-lookup"><span data-stu-id="924e1-108">The name of the resource to call.</span></span>

<span data-ttu-id="924e1-109">*Nazwa modułu* \[w\]</span><span class="sxs-lookup"><span data-stu-id="924e1-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="924e1-110">Nazwa modułu, który zawiera zasób do wywołania.</span><span class="sxs-lookup"><span data-stu-id="924e1-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="924e1-111">*Właściwość resourceProperty* \[w\]</span><span class="sxs-lookup"><span data-stu-id="924e1-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="924e1-112">Określa nazwę właściwości zasobów i jego wartość w tablicy skrótów klucz i wartość, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="924e1-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="924e1-113">Użyj [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) polecenia cmdlet, aby wykryć właściwości zasobów i ich typów.</span><span class="sxs-lookup"><span data-stu-id="924e1-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="924e1-114">*RebootRequired* \[out\]</span><span class="sxs-lookup"><span data-stu-id="924e1-114">*RebootRequired* \[out\]</span></span>  
<span data-ttu-id="924e1-115">Przy powrocie, ta właściwość jest ustawiona na **true** Jeśli węzeł docelowy musi zostać uruchomiony ponownie.</span><span class="sxs-lookup"><span data-stu-id="924e1-115">On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="924e1-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="924e1-116">Return value</span></span>
------------

<span data-ttu-id="924e1-117">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="924e1-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="924e1-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="924e1-118">Remarks</span></span>

<span data-ttu-id="924e1-119">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="924e1-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="924e1-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="924e1-120">Requirements</span></span>
------------
><span data-ttu-id="924e1-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="924e1-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="924e1-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="924e1-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="924e1-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="924e1-123">See also</span></span>


[<span data-ttu-id="924e1-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="924e1-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



