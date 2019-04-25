---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda ResourceSet klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 2712b7ff0a19e643c1f343d436c084f8970c9dd4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078405"
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="3984d-103">Metoda ResourceSet klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="3984d-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="3984d-104">Bezpośrednio wywołuje **ustaw** metod zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="3984d-104">Directly calls the **Set** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="3984d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3984d-105">Syntax</span></span>

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a><span data-ttu-id="3984d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3984d-106">Parameters</span></span>

<span data-ttu-id="3984d-107">*Typ zasobu* \[w\] nazwę zasobu do wywołania.</span><span class="sxs-lookup"><span data-stu-id="3984d-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="3984d-108">*ModuleName* \[w\] nazwę modułu, który zawiera zasób do wywołania.</span><span class="sxs-lookup"><span data-stu-id="3984d-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="3984d-109">*resourceProperty* \[w\] Określa nazwę właściwości zasobów i jego wartość w tabeli wyznaczania wartości skrótu jako klucza i wartości, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="3984d-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="3984d-110">Użyj [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) polecenia cmdlet, aby odnaleźć właściwości zasobów i ich typy.</span><span class="sxs-lookup"><span data-stu-id="3984d-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="3984d-111">*RebootRequired* \[się\] przy powrocie, właściwość ta jest równa **true** Jeśli węzeł docelowy musi zostać przeprowadzony ponowny rozruch.</span><span class="sxs-lookup"><span data-stu-id="3984d-111">*RebootRequired* \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="3984d-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3984d-112">Return value</span></span>

<span data-ttu-id="3984d-113">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="3984d-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3984d-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3984d-114">Remarks</span></span>

<span data-ttu-id="3984d-115">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="3984d-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3984d-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3984d-116">Requirements</span></span>

<span data-ttu-id="3984d-117">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="3984d-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="3984d-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3984d-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="3984d-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3984d-119">See also</span></span>

[<span data-ttu-id="3984d-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3984d-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)