---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda TestConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 2df04d317bd5e7a5c2a713d92be57c5c9a9f5e8c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="f6a5a-103">Metoda TestConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="f6a5a-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="f6a5a-104">Wysyła dokument konfiguracji do węzła zarządzanego i sprawdza bieżącą konfigurację względem dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f6a5a-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

<a name="syntax"></a><span data-ttu-id="f6a5a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f6a5a-105">Syntax</span></span>
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a><span data-ttu-id="f6a5a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6a5a-106">Parameters</span></span>
----------

<span data-ttu-id="f6a5a-107">*configurationData* \[w\] danych środowiska dla confuguration.</span><span class="sxs-lookup"><span data-stu-id="f6a5a-107">*configurationData* \[in\] Environment data for the confuguration.</span></span>

<span data-ttu-id="f6a5a-108">*InDesiredState* \[limit\] przy powrocie, określa, czy węzeł zarządzany w stan określony w dokumencie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f6a5a-108">*InDesiredState* \[out\] On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="f6a5a-109">*ResourcesInDesiredState* \[limit\] przy powrocie, zawiera osadzony wystąpienia **MSFT_ResourceInDesiredState** klasy, która określa zasoby, które są w żądanym stanie.</span><span class="sxs-lookup"><span data-stu-id="f6a5a-109">*ResourcesInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="f6a5a-110">*ResourcesNotInDesiredState* \[limit\] przy powrocie, zawiera osadzony wystąpienia **MSFT_ResourceNotInDesiredState** klasy, która określa zasoby, które nie są w żądanym stanie.</span><span class="sxs-lookup"><span data-stu-id="f6a5a-110">*ResourcesNotInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="f6a5a-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f6a5a-111">Return value</span></span>
------------

<span data-ttu-id="f6a5a-112">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="f6a5a-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f6a5a-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f6a5a-113">Remarks</span></span>

<span data-ttu-id="f6a5a-114">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="f6a5a-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f6a5a-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f6a5a-115">Requirements</span></span>
------------
><span data-ttu-id="f6a5a-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f6a5a-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="f6a5a-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f6a5a-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="f6a5a-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f6a5a-118">See also</span></span>


[<span data-ttu-id="f6a5a-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f6a5a-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)