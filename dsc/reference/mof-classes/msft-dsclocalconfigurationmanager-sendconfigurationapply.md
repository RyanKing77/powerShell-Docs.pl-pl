---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda SendConfigurationApply klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: da3a08307122ab38ee4a6fd5d4a9b97579a988f7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685389"
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="8a5de-103">Metoda SendConfigurationApply klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="8a5de-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="8a5de-104">Wysyła dokument konfiguracji do zarządzanego węzła i używa agenta konfiguracji, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="8a5de-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="8a5de-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8a5de-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="8a5de-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8a5de-106">Parameters</span></span>

<span data-ttu-id="8a5de-107">*ConfigurationData* \[w\] danych środowiska dla konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8a5de-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="8a5de-108">*Wymuś* \[w\] **true** wymusić konfigurację, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="8a5de-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="8a5de-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8a5de-109">Return value</span></span>

<span data-ttu-id="8a5de-110">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="8a5de-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8a5de-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8a5de-111">Remarks</span></span>

<span data-ttu-id="8a5de-112">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="8a5de-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8a5de-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8a5de-113">Requirements</span></span>

<span data-ttu-id="8a5de-114">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="8a5de-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="8a5de-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8a5de-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="8a5de-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8a5de-116">See also</span></span>

[<span data-ttu-id="8a5de-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="8a5de-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)