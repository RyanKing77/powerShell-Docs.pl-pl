---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Metoda SendConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 8457189538ceb0181a8e65b57a9fc3e911cbcec4
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="bd057-103">Metoda SendConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="bd057-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="bd057-104">Wysyła dokument konfiguracji do węzła zarządzanego i zapisuje go jako oczekujące zmiany.</span><span class="sxs-lookup"><span data-stu-id="bd057-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="bd057-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="bd057-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="bd057-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bd057-106">Parameters</span></span>
----------

<span data-ttu-id="bd057-107">*ConfigurationData* \[w\]</span><span class="sxs-lookup"><span data-stu-id="bd057-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="bd057-108">Dane konfiguracji środowiska.</span><span class="sxs-lookup"><span data-stu-id="bd057-108">The environment data for the configuration.</span></span>

<span data-ttu-id="bd057-109">*Wymuś* \[w\]</span><span class="sxs-lookup"><span data-stu-id="bd057-109">*force* \[in\]</span></span>  
<span data-ttu-id="bd057-110">**wartość true,** wymusić konfigurację, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="bd057-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="bd057-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bd057-111">Return value</span></span>
------------

<span data-ttu-id="bd057-112">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="bd057-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="bd057-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bd057-113">Remarks</span></span>

<span data-ttu-id="bd057-114">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="bd057-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bd057-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bd057-115">Requirements</span></span>
------------
><span data-ttu-id="bd057-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="bd057-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="bd057-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="bd057-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="bd057-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bd057-118">See also</span></span>


[<span data-ttu-id="bd057-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="bd057-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



