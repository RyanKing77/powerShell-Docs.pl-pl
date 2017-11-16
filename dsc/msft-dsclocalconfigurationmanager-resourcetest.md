---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Metoda ResourceTest klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 73d7d543505a3768a0660084345d3858e055514f
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b0021-103">Metoda ResourceTest klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="b0021-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b0021-104">Bezpośrednio wywołuje **testu** metody zasobu usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="b0021-104">Directly calls the **Test** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="b0021-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0021-105">Syntax</span></span>
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a><span data-ttu-id="b0021-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b0021-106">Parameters</span></span>
----------

<span data-ttu-id="b0021-107">*Typ zasobu* \[w\]</span><span class="sxs-lookup"><span data-stu-id="b0021-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="b0021-108">Nazwa zasobu do wywołania.</span><span class="sxs-lookup"><span data-stu-id="b0021-108">The name of the resource to call.</span></span>

<span data-ttu-id="b0021-109">*Nazwa modułu* \[w\]</span><span class="sxs-lookup"><span data-stu-id="b0021-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="b0021-110">Nazwa modułu, który zawiera zasób do wywołania.</span><span class="sxs-lookup"><span data-stu-id="b0021-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="b0021-111">*Właściwość resourceProperty* \[w\]</span><span class="sxs-lookup"><span data-stu-id="b0021-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="b0021-112">Określa nazwę właściwości zasobów i jego wartość w tablicy skrótów klucz i wartość, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="b0021-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="b0021-113">Użyj [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) polecenia cmdlet, aby wykryć właściwości zasobów i ich typów.</span><span class="sxs-lookup"><span data-stu-id="b0021-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="b0021-114">*InDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="b0021-114">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="b0021-115">Przy powrocie, ta właściwość jest ustawiona na **true** Jeśli węzeł docelowy jest w żądanym stanie.</span><span class="sxs-lookup"><span data-stu-id="b0021-115">On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="b0021-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b0021-116">Return value</span></span>
------------

<span data-ttu-id="b0021-117">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="b0021-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b0021-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b0021-118">Remarks</span></span>

<span data-ttu-id="b0021-119">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="b0021-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b0021-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b0021-120">Requirements</span></span>
------------
><span data-ttu-id="b0021-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b0021-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="b0021-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b0021-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="b0021-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b0021-123">See also</span></span>


[<span data-ttu-id="b0021-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b0021-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



