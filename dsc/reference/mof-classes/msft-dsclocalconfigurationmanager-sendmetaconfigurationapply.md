---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda SendMetaConfigurationApply
ms.openlocfilehash: b2e420bafb8ea22aea43800f6e429d3ed785d1e8
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727044"
---
# <a name="sendmetaconfigurationapply-method"></a><span data-ttu-id="7d64d-103">Metoda SendMetaConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="7d64d-103">SendMetaConfigurationApply method</span></span>

<span data-ttu-id="7d64d-104">Ustawia ustawienia Local Configuration Manager, które są używane do kontrolowania przez agenta konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7d64d-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="7d64d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d64d-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="7d64d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d64d-106">Parameters</span></span>

<span data-ttu-id="7d64d-107">*ConfigurationData* \[w\] danych środowiska dla konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7d64d-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="7d64d-108">*Wymuś* \[w\] **true** wymusić konfigurację, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="7d64d-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="7d64d-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7d64d-109">Return value</span></span>

<span data-ttu-id="7d64d-110">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="7d64d-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7d64d-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7d64d-111">Remarks</span></span>

<span data-ttu-id="7d64d-112">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="7d64d-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7d64d-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7d64d-113">Requirements</span></span>

<span data-ttu-id="7d64d-114">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7d64d-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="7d64d-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7d64d-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="7d64d-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d64d-116">See also</span></span>

[<span data-ttu-id="7d64d-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7d64d-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
