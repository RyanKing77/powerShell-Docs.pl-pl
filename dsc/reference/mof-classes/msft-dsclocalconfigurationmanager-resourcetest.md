---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda ResourceTest klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e7645b0c6b93b96cb01f72c1c92d468f7642ea13
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685991"
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0e7b2-103">Metoda ResourceTest klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="0e7b2-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0e7b2-104">Bezpośrednio wywołuje **testu** metod zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="0e7b2-104">Directly calls the **Test** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="0e7b2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0e7b2-105">Syntax</span></span>

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a><span data-ttu-id="0e7b2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0e7b2-106">Parameters</span></span>

<span data-ttu-id="0e7b2-107">*Typ zasobu* \[w\] nazwę zasobu do wywołania.</span><span class="sxs-lookup"><span data-stu-id="0e7b2-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="0e7b2-108">*ModuleName* \[w\] nazwę modułu, który zawiera zasób do wywołania.</span><span class="sxs-lookup"><span data-stu-id="0e7b2-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="0e7b2-109">*resourceProperty* \[w\] Określa nazwę właściwości zasobów i jego wartość w tabeli wyznaczania wartości skrótu jako klucza i wartości, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="0e7b2-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="0e7b2-110">Użyj [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) polecenia cmdlet, aby odnaleźć właściwości zasobów i ich typy.</span><span class="sxs-lookup"><span data-stu-id="0e7b2-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="0e7b2-111">*InDesiredState* \[się\] przy powrocie, właściwość ta jest równa **true** Jeśli węzeł docelowy jest w żądanym stanie.</span><span class="sxs-lookup"><span data-stu-id="0e7b2-111">*InDesiredState* \[out\] On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="0e7b2-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0e7b2-112">Return value</span></span>

<span data-ttu-id="0e7b2-113">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="0e7b2-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0e7b2-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0e7b2-114">Remarks</span></span>

<span data-ttu-id="0e7b2-115">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="0e7b2-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0e7b2-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0e7b2-116">Requirements</span></span>

<span data-ttu-id="0e7b2-117">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0e7b2-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="0e7b2-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0e7b2-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="0e7b2-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0e7b2-119">See also</span></span>

[<span data-ttu-id="0e7b2-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0e7b2-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)