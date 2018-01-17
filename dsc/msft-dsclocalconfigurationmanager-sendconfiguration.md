---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Metoda SendConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 72c59b5aad293fa561146e5ad6822f27f40f321f
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0c3b0-103">Metoda SendConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="0c3b0-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0c3b0-104">Wysyła dokument konfiguracji do węzła zarządzanego i zapisuje go jako oczekujące zmiany.</span><span class="sxs-lookup"><span data-stu-id="0c3b0-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="0c3b0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0c3b0-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="0c3b0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c3b0-106">Parameters</span></span>
----------

<span data-ttu-id="0c3b0-107">*ConfigurationData* \[w\]</span><span class="sxs-lookup"><span data-stu-id="0c3b0-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="0c3b0-108">Dane konfiguracji środowiska.</span><span class="sxs-lookup"><span data-stu-id="0c3b0-108">The environment data for the configuration.</span></span>

<span data-ttu-id="0c3b0-109">*Wymuś* \[w\]</span><span class="sxs-lookup"><span data-stu-id="0c3b0-109">*force* \[in\]</span></span>  
<span data-ttu-id="0c3b0-110">**wartość true,** wymusić konfigurację, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="0c3b0-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="0c3b0-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0c3b0-111">Return value</span></span>
------------

<span data-ttu-id="0c3b0-112">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="0c3b0-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0c3b0-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0c3b0-113">Remarks</span></span>

<span data-ttu-id="0c3b0-114">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="0c3b0-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0c3b0-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0c3b0-115">Requirements</span></span>
------------
><span data-ttu-id="0c3b0-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0c3b0-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="0c3b0-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0c3b0-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="0c3b0-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0c3b0-118">See also</span></span>


[<span data-ttu-id="0c3b0-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0c3b0-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



