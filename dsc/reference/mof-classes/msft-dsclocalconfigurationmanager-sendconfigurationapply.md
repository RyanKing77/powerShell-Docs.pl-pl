---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda SendConfigurationApply klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: da3a08307122ab38ee4a6fd5d4a9b97579a988f7
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048365"
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="56079-103">Metoda SendConfigurationApply klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="56079-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="56079-104">Wysyła dokument konfiguracji do zarządzanego węzła i używa agenta konfiguracji, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="56079-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="56079-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="56079-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="56079-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="56079-106">Parameters</span></span>

<span data-ttu-id="56079-107">*ConfigurationData* \[w\] danych środowiska dla konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="56079-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="56079-108">*Wymuś* \[w\] **true** wymusić konfigurację, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="56079-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="56079-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="56079-109">Return value</span></span>

<span data-ttu-id="56079-110">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="56079-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="56079-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="56079-111">Remarks</span></span>

<span data-ttu-id="56079-112">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="56079-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="56079-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="56079-113">Requirements</span></span>

<span data-ttu-id="56079-114">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="56079-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="56079-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="56079-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="56079-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="56079-116">See also</span></span>

[<span data-ttu-id="56079-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="56079-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)