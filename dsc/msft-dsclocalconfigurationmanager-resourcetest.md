---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Metoda ResourceTest klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 3c88f74c5f623502e8cbe0d7aa7390fca75569a9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="c3230-103">Metoda ResourceTest klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="c3230-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="c3230-104">Bezpośrednio wywołuje **testu** metody zasobu usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="c3230-104">Directly calls the **Test** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="c3230-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c3230-105">Syntax</span></span>
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a><span data-ttu-id="c3230-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3230-106">Parameters</span></span>
----------

<span data-ttu-id="c3230-107">*Typ zasobu* \[w\]</span><span class="sxs-lookup"><span data-stu-id="c3230-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="c3230-108">Nazwa zasobu do wywołania.</span><span class="sxs-lookup"><span data-stu-id="c3230-108">The name of the resource to call.</span></span>

<span data-ttu-id="c3230-109">*Nazwa modułu* \[w\]</span><span class="sxs-lookup"><span data-stu-id="c3230-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="c3230-110">Nazwa modułu, który zawiera zasób do wywołania.</span><span class="sxs-lookup"><span data-stu-id="c3230-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="c3230-111">*Właściwość resourceProperty* \[w\]</span><span class="sxs-lookup"><span data-stu-id="c3230-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="c3230-112">Określa nazwę właściwości zasobów i jego wartość w tablicy skrótów klucz i wartość, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="c3230-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="c3230-113">Użyj [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) polecenia cmdlet, aby wykryć właściwości zasobów i ich typów.</span><span class="sxs-lookup"><span data-stu-id="c3230-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="c3230-114">*InDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="c3230-114">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="c3230-115">Przy powrocie, ta właściwość jest ustawiona na **true** Jeśli węzeł docelowy jest w żądanym stanie.</span><span class="sxs-lookup"><span data-stu-id="c3230-115">On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="c3230-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c3230-116">Return value</span></span>
------------

<span data-ttu-id="c3230-117">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="c3230-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c3230-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c3230-118">Remarks</span></span>

<span data-ttu-id="c3230-119">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="c3230-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c3230-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c3230-120">Requirements</span></span>
------------
><span data-ttu-id="c3230-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c3230-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="c3230-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c3230-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="c3230-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c3230-123">See also</span></span>


[<span data-ttu-id="c3230-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c3230-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



