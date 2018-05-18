---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda SendMetaConfigurationApply klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 46acd86ac52b7b6b39f06fc65af2498b4f5348ed
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="944f3-103">Metoda SendMetaConfigurationApply klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="944f3-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="944f3-104">Konfiguruje ustawienia lokalny program Configuration Manager, które są używane do sterowania agenta konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="944f3-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="944f3-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="944f3-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="944f3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="944f3-106">Parameters</span></span>
----------

<span data-ttu-id="944f3-107">*ConfigurationData* \[w\] danych środowiska w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="944f3-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="944f3-108">*Wymuś* \[w\] **true** wymusić konfigurację, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="944f3-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="944f3-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="944f3-109">Return value</span></span>
------------

<span data-ttu-id="944f3-110">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="944f3-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="944f3-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="944f3-111">Remarks</span></span>

<span data-ttu-id="944f3-112">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="944f3-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="944f3-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="944f3-113">Requirements</span></span>
------------
><span data-ttu-id="944f3-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="944f3-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="944f3-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="944f3-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="944f3-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="944f3-116">See also</span></span>


[<span data-ttu-id="944f3-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="944f3-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)