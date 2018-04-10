---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda ResourceGet klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 3fd7ae54eb3ae782156dc4619ee0b6905dfb1212
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="c4af6-103">Metoda ResourceGet klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="c4af6-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="c4af6-104">Bezpośrednio wywołuje **uzyskać** metody zasobu usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="c4af6-104">Directly calls the **Get** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="c4af6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c4af6-105">Syntax</span></span>
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a><span data-ttu-id="c4af6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c4af6-106">Parameters</span></span>
----------

<span data-ttu-id="c4af6-107">*Typ zasobu* \[w\] nazwę zasobu do wywołania.</span><span class="sxs-lookup"><span data-stu-id="c4af6-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="c4af6-108">*Nazwa modułu* \[w\] nazwę modułu, który zawiera zasób do wywołania.</span><span class="sxs-lookup"><span data-stu-id="c4af6-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="c4af6-109">*Właściwość resourceProperty* \[w\] Określa nazwę właściwości zasobów i jego wartość w tablicy skrótów jako klucz i wartość, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="c4af6-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="c4af6-110">Użyj [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) polecenia cmdlet, aby wykryć właściwości zasobów i ich typów.</span><span class="sxs-lookup"><span data-stu-id="c4af6-110">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="c4af6-111">*konfiguracje* \[limit\] przy powrocie, zawiera osadzony wystąpienia konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c4af6-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="c4af6-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c4af6-112">Return value</span></span>
------------

<span data-ttu-id="c4af6-113">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="c4af6-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c4af6-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c4af6-114">Remarks</span></span>

<span data-ttu-id="c4af6-115">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="c4af6-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c4af6-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c4af6-116">Requirements</span></span>
------------
><span data-ttu-id="c4af6-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c4af6-117">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="c4af6-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c4af6-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="c4af6-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c4af6-119">See also</span></span>


[<span data-ttu-id="c4af6-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c4af6-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)