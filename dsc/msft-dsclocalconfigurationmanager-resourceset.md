---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda ResourceSet klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 0c9c1d33117067d76d61036d5839f0b676eb4a97
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219620"
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="5117e-103">Metoda ResourceSet klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="5117e-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="5117e-104">Bezpośrednio wywołuje **ustawić** metody zasobu usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="5117e-104">Directly calls the **Set** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="5117e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5117e-105">Syntax</span></span>
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

<a name="parameters"></a><span data-ttu-id="5117e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5117e-106">Parameters</span></span>
----------

<span data-ttu-id="5117e-107">*Typ zasobu* \[w\] nazwę zasobu do wywołania.</span><span class="sxs-lookup"><span data-stu-id="5117e-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="5117e-108">*Nazwa modułu* \[w\] nazwę modułu, który zawiera zasób do wywołania.</span><span class="sxs-lookup"><span data-stu-id="5117e-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="5117e-109">*Właściwość resourceProperty* \[w\] Określa nazwę właściwości zasobów i jego wartość w tablicy skrótów jako klucz i wartość, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="5117e-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="5117e-110">Użyj [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) polecenia cmdlet, aby wykryć właściwości zasobów i ich typów.</span><span class="sxs-lookup"><span data-stu-id="5117e-110">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="5117e-111">*RebootRequired* \[limit\] przy powrocie, ta właściwość jest ustawiona na **true** Jeśli węzeł docelowy musi zostać uruchomiony ponownie.</span><span class="sxs-lookup"><span data-stu-id="5117e-111">*RebootRequired* \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="5117e-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5117e-112">Return value</span></span>
------------

<span data-ttu-id="5117e-113">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="5117e-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5117e-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5117e-114">Remarks</span></span>

<span data-ttu-id="5117e-115">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="5117e-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5117e-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5117e-116">Requirements</span></span>
------------
><span data-ttu-id="5117e-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5117e-117">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="5117e-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5117e-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="5117e-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5117e-119">See also</span></span>


[<span data-ttu-id="5117e-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5117e-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)