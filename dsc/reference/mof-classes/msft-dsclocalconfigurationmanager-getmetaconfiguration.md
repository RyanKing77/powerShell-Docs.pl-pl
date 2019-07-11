---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda GetMetaConfiguration
ms.openlocfilehash: bd280cb8ebd7b0522e4e01cbd24bd9bdcfddf4c2
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734447"
---
# <a name="getmetaconfiguration-method"></a><span data-ttu-id="e5887-103">Metoda GetMetaConfiguration</span><span class="sxs-lookup"><span data-stu-id="e5887-103">GetMetaConfiguration method</span></span>

<span data-ttu-id="e5887-104">Pobiera lokalne ustawienia programu Configuration Manager, które są używane do kontrolowania przez agenta konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e5887-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="e5887-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5887-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="e5887-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5887-106">Parameters</span></span>

<span data-ttu-id="e5887-107">*MetaConfiguration* \[się\] przy powrocie, zawiera osadzony wystąpienia **MSFT_DSCMetaConfiguration** klasę, która definiuje ustawienia.</span><span class="sxs-lookup"><span data-stu-id="e5887-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="e5887-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e5887-108">Return value</span></span>

<span data-ttu-id="e5887-109">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="e5887-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e5887-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5887-110">Remarks</span></span>

<span data-ttu-id="e5887-111">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="e5887-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e5887-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e5887-112">Requirements</span></span>

<span data-ttu-id="e5887-113">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e5887-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e5887-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e5887-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e5887-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e5887-115">See also</span></span>

[<span data-ttu-id="e5887-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e5887-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
