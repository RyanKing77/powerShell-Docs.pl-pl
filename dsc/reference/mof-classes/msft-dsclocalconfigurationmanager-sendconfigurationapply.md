---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda SendConfigurationApply
ms.openlocfilehash: 11b9d435bbaac1600d25ff074b6c55b236a8378b
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727002"
---
# <a name="sendconfigurationapply-method"></a><span data-ttu-id="3b7c6-103">Metoda SendConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="3b7c6-103">SendConfigurationApply method</span></span>

<span data-ttu-id="3b7c6-104">Wysyła dokument konfiguracji do zarządzanego węzła i używa agenta konfiguracji, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="3b7c6-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="3b7c6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3b7c6-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="3b7c6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3b7c6-106">Parameters</span></span>

<span data-ttu-id="3b7c6-107">*ConfigurationData* \[w\] danych środowiska dla konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3b7c6-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="3b7c6-108">*Wymuś* \[w\] **true** wymusić konfigurację, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="3b7c6-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="3b7c6-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3b7c6-109">Return value</span></span>

<span data-ttu-id="3b7c6-110">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="3b7c6-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3b7c6-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3b7c6-111">Remarks</span></span>

<span data-ttu-id="3b7c6-112">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="3b7c6-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3b7c6-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3b7c6-113">Requirements</span></span>

<span data-ttu-id="3b7c6-114">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="3b7c6-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="3b7c6-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3b7c6-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="3b7c6-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3b7c6-116">See also</span></span>

[<span data-ttu-id="3b7c6-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3b7c6-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
