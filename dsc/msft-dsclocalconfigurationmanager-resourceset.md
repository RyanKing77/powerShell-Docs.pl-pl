---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda ResourceSet klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b5f437a123bd38df21f30d11e71d2c3b36bc9f3a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="c9af8-103">Metoda ResourceSet klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="c9af8-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="c9af8-104">Bezpośrednio wywołuje **ustawić** metody zasobu usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="c9af8-104">Directly calls the **Set** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="c9af8-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c9af8-105">Syntax</span></span>
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

<a name="parameters"></a><span data-ttu-id="c9af8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c9af8-106">Parameters</span></span>
----------

<span data-ttu-id="c9af8-107">*Typ zasobu* \[w\] nazwę zasobu do wywołania.</span><span class="sxs-lookup"><span data-stu-id="c9af8-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="c9af8-108">*Nazwa modułu* \[w\] nazwę modułu, który zawiera zasób do wywołania.</span><span class="sxs-lookup"><span data-stu-id="c9af8-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="c9af8-109">*Właściwość resourceProperty* \[w\] Określa nazwę właściwości zasobów i jego wartość w tablicy skrótów jako klucz i wartość, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="c9af8-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="c9af8-110">Użyj [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) polecenia cmdlet, aby wykryć właściwości zasobów i ich typów.</span><span class="sxs-lookup"><span data-stu-id="c9af8-110">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="c9af8-111">*RebootRequired* \[limit\] przy powrocie, ta właściwość jest ustawiona na **true** Jeśli węzeł docelowy musi zostać uruchomiony ponownie.</span><span class="sxs-lookup"><span data-stu-id="c9af8-111">*RebootRequired* \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="c9af8-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c9af8-112">Return value</span></span>
------------

<span data-ttu-id="c9af8-113">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="c9af8-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c9af8-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c9af8-114">Remarks</span></span>

<span data-ttu-id="c9af8-115">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="c9af8-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c9af8-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c9af8-116">Requirements</span></span>
------------
><span data-ttu-id="c9af8-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c9af8-117">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="c9af8-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c9af8-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="c9af8-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c9af8-119">See also</span></span>


[<span data-ttu-id="c9af8-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c9af8-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)