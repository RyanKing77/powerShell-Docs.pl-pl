---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Metoda SendMetaConfigurationApply klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: d8ddc9d99f0d74ad907a6e39ae0e8ac14159be16
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7866d-103">Metoda SendMetaConfigurationApply klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="7866d-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7866d-104">Konfiguruje ustawienia lokalny program Configuration Manager, które są używane do sterowania agenta konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7866d-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="7866d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7866d-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="7866d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7866d-106">Parameters</span></span>
----------

<span data-ttu-id="7866d-107">*ConfigurationData* \[w\]</span><span class="sxs-lookup"><span data-stu-id="7866d-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="7866d-108">Dane konfiguracji środowiska.</span><span class="sxs-lookup"><span data-stu-id="7866d-108">The environment data for the configuration.</span></span>

<span data-ttu-id="7866d-109">*Wymuś* \[w\]</span><span class="sxs-lookup"><span data-stu-id="7866d-109">*force* \[in\]</span></span>  
<span data-ttu-id="7866d-110">**wartość true,** wymusić konfigurację, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="7866d-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="7866d-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7866d-111">Return value</span></span>
------------

<span data-ttu-id="7866d-112">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="7866d-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7866d-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7866d-113">Remarks</span></span>

<span data-ttu-id="7866d-114">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="7866d-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7866d-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7866d-115">Requirements</span></span>
------------
><span data-ttu-id="7866d-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7866d-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="7866d-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7866d-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="7866d-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7866d-118">See also</span></span>


[<span data-ttu-id="7866d-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7866d-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



