---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda TestConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: d746832b01310f43a7aae33dd0fa70c0928bb3e0
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405341"
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="27395-103">Metoda TestConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="27395-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="27395-104">Wysyła dokument konfiguracji w węźle zarządzanym i sprawdza bieżącą konfigurację dla dokumentu.</span><span class="sxs-lookup"><span data-stu-id="27395-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

## <a name="syntax"></a><span data-ttu-id="27395-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="27395-105">Syntax</span></span>

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a><span data-ttu-id="27395-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="27395-106">Parameters</span></span>

<span data-ttu-id="27395-107">*configurationData* \[w\] confuguration dane środowisko.</span><span class="sxs-lookup"><span data-stu-id="27395-107">*configurationData* \[in\] Environment data for the confuguration.</span></span>

<span data-ttu-id="27395-108">*InDesiredState* \[się\] przy powrocie, określa, czy zarządzany węzeł jest w stanie określone przez dokumentu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="27395-108">*InDesiredState* \[out\] On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="27395-109">*ResourcesInDesiredState* \[się\] przy powrocie, zawiera osadzony wystąpienia **MSFT_ResourceInDesiredState** klasę, która określa zasoby, które znajdują się w żądanym stanie.</span><span class="sxs-lookup"><span data-stu-id="27395-109">*ResourcesInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="27395-110">*ResourcesNotInDesiredState* \[się\] przy powrocie, zawiera osadzony wystąpienia **MSFT_ResourceNotInDesiredState** klasę, która określa zasoby, które nie znajdują się w żądanym stanie.</span><span class="sxs-lookup"><span data-stu-id="27395-110">*ResourcesNotInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="27395-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="27395-111">Return value</span></span>

<span data-ttu-id="27395-112">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="27395-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="27395-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="27395-113">Remarks</span></span>

<span data-ttu-id="27395-114">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="27395-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="27395-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="27395-115">Requirements</span></span>

<span data-ttu-id="27395-116">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="27395-116">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="27395-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="27395-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="27395-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="27395-118">See also</span></span>

[<span data-ttu-id="27395-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="27395-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)