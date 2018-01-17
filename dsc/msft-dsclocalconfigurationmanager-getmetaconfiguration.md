---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Metoda GetMetaConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 695be4ee6490567295fda0cc44635870362d24b8
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="a5c9f-103">Metoda GetMetaConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="a5c9f-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a5c9f-104">Pobiera ustawienia lokalne programu Configuration Manager, które są używane do sterowania agenta konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a5c9f-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="a5c9f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a5c9f-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="a5c9f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a5c9f-106">Parameters</span></span>
----------

<span data-ttu-id="a5c9f-107">*Metakonfigurację* \[out\]</span><span class="sxs-lookup"><span data-stu-id="a5c9f-107">*MetaConfiguration* \[out\]</span></span>  
<span data-ttu-id="a5c9f-108">Przy powrocie, zawiera osadzony wystąpienia **MSFT_DSCMetaConfiguration** klasa, która definiuje ustawienia.</span><span class="sxs-lookup"><span data-stu-id="a5c9f-108">On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="a5c9f-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a5c9f-109">Return value</span></span>
------------

<span data-ttu-id="a5c9f-110">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="a5c9f-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a5c9f-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a5c9f-111">Remarks</span></span>

<span data-ttu-id="a5c9f-112">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="a5c9f-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a5c9f-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a5c9f-113">Requirements</span></span>
------------
><span data-ttu-id="a5c9f-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a5c9f-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="a5c9f-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a5c9f-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="a5c9f-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5c9f-116">See also</span></span>


[<span data-ttu-id="a5c9f-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a5c9f-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



