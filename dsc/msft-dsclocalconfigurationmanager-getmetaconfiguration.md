---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda GetMetaConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ebf2b65f152c622ccf42e12545b0048a0b96d963
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="5e4d4-103">Metoda GetMetaConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="5e4d4-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="5e4d4-104">Pobiera ustawienia lokalne programu Configuration Manager, które są używane do sterowania agenta konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5e4d4-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="5e4d4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e4d4-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="5e4d4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e4d4-106">Parameters</span></span>
----------

<span data-ttu-id="5e4d4-107">*Metakonfigurację* \[limit\] przy powrocie, zawiera osadzony wystąpienia **MSFT_DSCMetaConfiguration** klasa, która definiuje ustawienia.</span><span class="sxs-lookup"><span data-stu-id="5e4d4-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="5e4d4-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5e4d4-108">Return value</span></span>
------------

<span data-ttu-id="5e4d4-109">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="5e4d4-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5e4d4-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5e4d4-110">Remarks</span></span>

<span data-ttu-id="5e4d4-111">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="5e4d4-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5e4d4-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5e4d4-112">Requirements</span></span>
------------
><span data-ttu-id="5e4d4-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5e4d4-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="5e4d4-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5e4d4-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="5e4d4-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e4d4-115">See also</span></span>


[<span data-ttu-id="5e4d4-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5e4d4-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)