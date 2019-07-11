---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda TestConfiguration
ms.openlocfilehash: 384134212e3b29b63dc045aee4b708c87c970302
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726963"
---
# <a name="testconfiguration-method"></a><span data-ttu-id="16aed-103">Metoda TestConfiguration</span><span class="sxs-lookup"><span data-stu-id="16aed-103">TestConfiguration method</span></span>

<span data-ttu-id="16aed-104">Wysyła dokument konfiguracji w węźle zarządzanym i sprawdza bieżącą konfigurację dla dokumentu.</span><span class="sxs-lookup"><span data-stu-id="16aed-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

## <a name="syntax"></a><span data-ttu-id="16aed-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="16aed-105">Syntax</span></span>

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a><span data-ttu-id="16aed-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="16aed-106">Parameters</span></span>

<span data-ttu-id="16aed-107">*configurationData* \[w\] confuguration dane środowisko.</span><span class="sxs-lookup"><span data-stu-id="16aed-107">*configurationData* \[in\] Environment data for the confuguration.</span></span>

<span data-ttu-id="16aed-108">*InDesiredState* \[się\] przy powrocie, określa, czy zarządzany węzeł jest w stanie określone przez dokumentu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="16aed-108">*InDesiredState* \[out\] On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="16aed-109">*ResourcesInDesiredState* \[się\] przy powrocie, zawiera osadzony wystąpienia **MSFT_ResourceInDesiredState** klasę, która określa zasoby, które znajdują się w żądanym stanie.</span><span class="sxs-lookup"><span data-stu-id="16aed-109">*ResourcesInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="16aed-110">*ResourcesNotInDesiredState* \[się\] przy powrocie, zawiera osadzony wystąpienia **MSFT_ResourceNotInDesiredState** klasę, która określa zasoby, które nie znajdują się w żądanym stanie.</span><span class="sxs-lookup"><span data-stu-id="16aed-110">*ResourcesNotInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="16aed-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="16aed-111">Return value</span></span>

<span data-ttu-id="16aed-112">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="16aed-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="16aed-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="16aed-113">Remarks</span></span>

<span data-ttu-id="16aed-114">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="16aed-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="16aed-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="16aed-115">Requirements</span></span>

<span data-ttu-id="16aed-116">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="16aed-116">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="16aed-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="16aed-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="16aed-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16aed-118">See also</span></span>

[<span data-ttu-id="16aed-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="16aed-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
