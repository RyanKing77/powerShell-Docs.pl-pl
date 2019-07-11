---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda ResourceGet
ms.openlocfilehash: dbe610dfcef5ef6c79783801ecb6fdb7408bdfa5
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727115"
---
# <a name="resourceget-method"></a><span data-ttu-id="c6296-103">Metoda ResourceGet</span><span class="sxs-lookup"><span data-stu-id="c6296-103">ResourceGet method</span></span>

<span data-ttu-id="c6296-104">Bezpośrednio wywołuje **uzyskać** metod zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="c6296-104">Directly calls the **Get** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="c6296-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c6296-105">Syntax</span></span>

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a><span data-ttu-id="c6296-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c6296-106">Parameters</span></span>

<span data-ttu-id="c6296-107">*Typ zasobu* \[w\] nazwę zasobu do wywołania.</span><span class="sxs-lookup"><span data-stu-id="c6296-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="c6296-108">*ModuleName* \[w\] nazwę modułu, który zawiera zasób do wywołania.</span><span class="sxs-lookup"><span data-stu-id="c6296-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="c6296-109">*resourceProperty* \[w\] Określa nazwę właściwości zasobów i jego wartość w tabeli wyznaczania wartości skrótu jako klucza i wartości, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="c6296-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="c6296-110">Użyj [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) polecenia cmdlet, aby odnaleźć właściwości zasobów i ich typy.</span><span class="sxs-lookup"><span data-stu-id="c6296-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="c6296-111">*konfiguracje* \[się\] przy powrocie, zawiera wystąpienie osadzony w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c6296-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="c6296-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c6296-112">Return value</span></span>

<span data-ttu-id="c6296-113">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="c6296-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c6296-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c6296-114">Remarks</span></span>

<span data-ttu-id="c6296-115">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="c6296-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c6296-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c6296-116">Requirements</span></span>

<span data-ttu-id="c6296-117">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c6296-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="c6296-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c6296-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="c6296-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c6296-119">See also</span></span>

[<span data-ttu-id="c6296-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c6296-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
