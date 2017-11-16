---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Metoda GetMetaConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 4f209014e9fde5841a9bce743f5364e6677d1e41
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="80ca4-103">Metoda GetMetaConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="80ca4-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="80ca4-104">Pobiera ustawienia lokalne programu Configuration Manager, które są używane do sterowania agenta konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="80ca4-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="80ca4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="80ca4-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="80ca4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="80ca4-106">Parameters</span></span>
----------

<span data-ttu-id="80ca4-107">*Metakonfigurację* \[out\]</span><span class="sxs-lookup"><span data-stu-id="80ca4-107">*MetaConfiguration* \[out\]</span></span>  
<span data-ttu-id="80ca4-108">Przy powrocie, zawiera osadzony wystąpienia **MSFT_DSCMetaConfiguration** klasa, która definiuje ustawienia.</span><span class="sxs-lookup"><span data-stu-id="80ca4-108">On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="80ca4-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="80ca4-109">Return value</span></span>
------------

<span data-ttu-id="80ca4-110">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="80ca4-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="80ca4-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="80ca4-111">Remarks</span></span>

<span data-ttu-id="80ca4-112">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="80ca4-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="80ca4-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="80ca4-113">Requirements</span></span>
------------
><span data-ttu-id="80ca4-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="80ca4-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="80ca4-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="80ca4-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="80ca4-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80ca4-116">See also</span></span>


[<span data-ttu-id="80ca4-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="80ca4-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



