---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda TestConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: d746832b01310f43a7aae33dd0fa70c0928bb3e0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078082"
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e979e-103">Metoda TestConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="e979e-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e979e-104">Wysyła dokument konfiguracji w węźle zarządzanym i sprawdza bieżącą konfigurację dla dokumentu.</span><span class="sxs-lookup"><span data-stu-id="e979e-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

## <a name="syntax"></a><span data-ttu-id="e979e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e979e-105">Syntax</span></span>

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a><span data-ttu-id="e979e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e979e-106">Parameters</span></span>

<span data-ttu-id="e979e-107">*configurationData* \[w\] confuguration dane środowisko.</span><span class="sxs-lookup"><span data-stu-id="e979e-107">*configurationData* \[in\] Environment data for the confuguration.</span></span>

<span data-ttu-id="e979e-108">*InDesiredState* \[się\] przy powrocie, określa, czy zarządzany węzeł jest w stanie określone przez dokumentu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e979e-108">*InDesiredState* \[out\] On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="e979e-109">*ResourcesInDesiredState* \[się\] przy powrocie, zawiera osadzony wystąpienia **MSFT_ResourceInDesiredState** klasę, która określa zasoby, które znajdują się w żądanym stanie.</span><span class="sxs-lookup"><span data-stu-id="e979e-109">*ResourcesInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="e979e-110">*ResourcesNotInDesiredState* \[się\] przy powrocie, zawiera osadzony wystąpienia **MSFT_ResourceNotInDesiredState** klasę, która określa zasoby, które nie znajdują się w żądanym stanie.</span><span class="sxs-lookup"><span data-stu-id="e979e-110">*ResourcesNotInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="e979e-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e979e-111">Return value</span></span>

<span data-ttu-id="e979e-112">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="e979e-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e979e-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e979e-113">Remarks</span></span>

<span data-ttu-id="e979e-114">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="e979e-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e979e-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e979e-115">Requirements</span></span>

<span data-ttu-id="e979e-116">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e979e-116">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e979e-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e979e-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e979e-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e979e-118">See also</span></span>

[<span data-ttu-id="e979e-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e979e-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)