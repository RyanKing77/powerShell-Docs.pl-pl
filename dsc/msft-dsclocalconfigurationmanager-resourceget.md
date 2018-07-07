---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda ResourceGet klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 1b74adf2327af2e0f9416f1d00eac4e3b75e9013
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893209"
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="80075-103">Metoda ResourceGet klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="80075-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="80075-104">Bezpośrednio wywołuje **uzyskać** metod zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="80075-104">Directly calls the **Get** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="80075-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="80075-105">Syntax</span></span>

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a><span data-ttu-id="80075-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="80075-106">Parameters</span></span>

<span data-ttu-id="80075-107">*Typ zasobu* \[w\] nazwę zasobu do wywołania.</span><span class="sxs-lookup"><span data-stu-id="80075-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="80075-108">*ModuleName* \[w\] nazwę modułu, który zawiera zasób do wywołania.</span><span class="sxs-lookup"><span data-stu-id="80075-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="80075-109">*resourceProperty* \[w\] Określa nazwę właściwości zasobów i jego wartość w tabeli wyznaczania wartości skrótu jako klucza i wartości, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="80075-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="80075-110">Użyj [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) polecenia cmdlet, aby odnaleźć właściwości zasobów i ich typy.</span><span class="sxs-lookup"><span data-stu-id="80075-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="80075-111">*konfiguracje* \[się\] przy powrocie, zawiera wystąpienie osadzony w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="80075-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="80075-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="80075-112">Return value</span></span>

<span data-ttu-id="80075-113">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="80075-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="80075-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="80075-114">Remarks</span></span>

<span data-ttu-id="80075-115">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="80075-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="80075-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="80075-116">Requirements</span></span>

<span data-ttu-id="80075-117">**Plik MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="80075-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="80075-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="80075-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="80075-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80075-119">See also</span></span>

[<span data-ttu-id="80075-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="80075-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)