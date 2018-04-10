---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda GetMetaConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ddc016402239bcdea060a717fbac9ab7ea42698c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="c1935-103">Metoda GetMetaConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="c1935-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="c1935-104">Pobiera ustawienia lokalne programu Configuration Manager, które są używane do sterowania agenta konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c1935-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="c1935-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c1935-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="c1935-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c1935-106">Parameters</span></span>
----------

<span data-ttu-id="c1935-107">*Metakonfigurację* \[limit\] przy powrocie, zawiera osadzony wystąpienia **MSFT_DSCMetaConfiguration** klasa, która definiuje ustawienia.</span><span class="sxs-lookup"><span data-stu-id="c1935-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="c1935-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c1935-108">Return value</span></span>
------------

<span data-ttu-id="c1935-109">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="c1935-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c1935-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c1935-110">Remarks</span></span>

<span data-ttu-id="c1935-111">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="c1935-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c1935-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c1935-112">Requirements</span></span>
------------
><span data-ttu-id="c1935-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c1935-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="c1935-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c1935-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="c1935-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c1935-115">See also</span></span>


[<span data-ttu-id="c1935-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c1935-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)