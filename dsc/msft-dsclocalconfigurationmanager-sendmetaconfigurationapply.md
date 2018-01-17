---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Metoda SendMetaConfigurationApply klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 350555220757b1939b1de34ab423e963635eb53c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d2c34-103">Metoda SendMetaConfigurationApply klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="d2c34-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d2c34-104">Konfiguruje ustawienia lokalny program Configuration Manager, które są używane do sterowania agenta konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d2c34-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="d2c34-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d2c34-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="d2c34-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d2c34-106">Parameters</span></span>
----------

<span data-ttu-id="d2c34-107">*ConfigurationData* \[w\]</span><span class="sxs-lookup"><span data-stu-id="d2c34-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="d2c34-108">Dane konfiguracji środowiska.</span><span class="sxs-lookup"><span data-stu-id="d2c34-108">The environment data for the configuration.</span></span>

<span data-ttu-id="d2c34-109">*Wymuś* \[w\]</span><span class="sxs-lookup"><span data-stu-id="d2c34-109">*force* \[in\]</span></span>  
<span data-ttu-id="d2c34-110">**wartość true,** wymusić konfigurację, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="d2c34-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="d2c34-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d2c34-111">Return value</span></span>
------------

<span data-ttu-id="d2c34-112">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="d2c34-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d2c34-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d2c34-113">Remarks</span></span>

<span data-ttu-id="d2c34-114">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="d2c34-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d2c34-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d2c34-115">Requirements</span></span>
------------
><span data-ttu-id="d2c34-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d2c34-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="d2c34-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d2c34-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="d2c34-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2c34-118">See also</span></span>


[<span data-ttu-id="d2c34-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d2c34-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



