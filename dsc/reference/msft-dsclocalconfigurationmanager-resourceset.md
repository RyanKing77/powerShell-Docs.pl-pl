---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda ResourceSet klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 2712b7ff0a19e643c1f343d436c084f8970c9dd4
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405162"
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7d08b-103">Metoda ResourceSet klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="7d08b-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7d08b-104">Bezpośrednio wywołuje **ustaw** metod zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="7d08b-104">Directly calls the **Set** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="7d08b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d08b-105">Syntax</span></span>

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a><span data-ttu-id="7d08b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d08b-106">Parameters</span></span>

<span data-ttu-id="7d08b-107">*Typ zasobu* \[w\] nazwę zasobu do wywołania.</span><span class="sxs-lookup"><span data-stu-id="7d08b-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="7d08b-108">*ModuleName* \[w\] nazwę modułu, który zawiera zasób do wywołania.</span><span class="sxs-lookup"><span data-stu-id="7d08b-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="7d08b-109">*resourceProperty* \[w\] Określa nazwę właściwości zasobów i jego wartość w tabeli wyznaczania wartości skrótu jako klucza i wartości, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="7d08b-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="7d08b-110">Użyj [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) polecenia cmdlet, aby odnaleźć właściwości zasobów i ich typy.</span><span class="sxs-lookup"><span data-stu-id="7d08b-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="7d08b-111">*RebootRequired* \[się\] przy powrocie, właściwość ta jest równa **true** Jeśli węzeł docelowy musi zostać przeprowadzony ponowny rozruch.</span><span class="sxs-lookup"><span data-stu-id="7d08b-111">*RebootRequired* \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="7d08b-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7d08b-112">Return value</span></span>

<span data-ttu-id="7d08b-113">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="7d08b-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7d08b-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7d08b-114">Remarks</span></span>

<span data-ttu-id="7d08b-115">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="7d08b-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7d08b-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7d08b-116">Requirements</span></span>

<span data-ttu-id="7d08b-117">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7d08b-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="7d08b-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7d08b-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="7d08b-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d08b-119">See also</span></span>

[<span data-ttu-id="7d08b-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7d08b-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)