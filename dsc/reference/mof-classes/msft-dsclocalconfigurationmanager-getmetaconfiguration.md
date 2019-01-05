---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda GetMetaConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e14237ef68b95d68e2f14071aa1fa6ba0717f39f
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048537"
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ffe8d-103">Metoda GetMetaConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="ffe8d-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ffe8d-104">Pobiera lokalne ustawienia programu Configuration Manager, które są używane do kontrolowania przez agenta konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ffe8d-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="ffe8d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ffe8d-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="ffe8d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ffe8d-106">Parameters</span></span>

<span data-ttu-id="ffe8d-107">*MetaConfiguration* \[się\] przy powrocie, zawiera osadzony wystąpienia **MSFT_DSCMetaConfiguration** klasę, która definiuje ustawienia.</span><span class="sxs-lookup"><span data-stu-id="ffe8d-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="ffe8d-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ffe8d-108">Return value</span></span>

<span data-ttu-id="ffe8d-109">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="ffe8d-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ffe8d-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ffe8d-110">Remarks</span></span>

<span data-ttu-id="ffe8d-111">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="ffe8d-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ffe8d-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ffe8d-112">Requirements</span></span>

<span data-ttu-id="ffe8d-113">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ffe8d-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="ffe8d-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ffe8d-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="ffe8d-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ffe8d-115">See also</span></span>

[<span data-ttu-id="ffe8d-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ffe8d-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)