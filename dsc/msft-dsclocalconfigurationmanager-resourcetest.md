---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda ResourceTest klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 714bbb286ebbe4ed0f1faa15e03ac4b51a3ee87f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="36059-103">Metoda ResourceTest klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="36059-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="36059-104">Bezpośrednio wywołuje **testu** metody zasobu usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="36059-104">Directly calls the **Test** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="36059-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="36059-105">Syntax</span></span>
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a><span data-ttu-id="36059-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="36059-106">Parameters</span></span>
----------

<span data-ttu-id="36059-107">*Typ zasobu* \[w\] nazwę zasobu do wywołania.</span><span class="sxs-lookup"><span data-stu-id="36059-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="36059-108">*Nazwa modułu* \[w\] nazwę modułu, który zawiera zasób do wywołania.</span><span class="sxs-lookup"><span data-stu-id="36059-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="36059-109">*Właściwość resourceProperty* \[w\] Określa nazwę właściwości zasobów i jego wartość w tablicy skrótów jako klucz i wartość, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="36059-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="36059-110">Użyj [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) polecenia cmdlet, aby wykryć właściwości zasobów i ich typów.</span><span class="sxs-lookup"><span data-stu-id="36059-110">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="36059-111">*InDesiredState* \[limit\] przy powrocie, ta właściwość jest ustawiona na **true** Jeśli węzeł docelowy jest w żądanym stanie.</span><span class="sxs-lookup"><span data-stu-id="36059-111">*InDesiredState* \[out\] On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="36059-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="36059-112">Return value</span></span>
------------

<span data-ttu-id="36059-113">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="36059-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="36059-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="36059-114">Remarks</span></span>

<span data-ttu-id="36059-115">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="36059-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="36059-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="36059-116">Requirements</span></span>
------------
><span data-ttu-id="36059-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="36059-117">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="36059-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="36059-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="36059-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="36059-119">See also</span></span>


[<span data-ttu-id="36059-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="36059-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)