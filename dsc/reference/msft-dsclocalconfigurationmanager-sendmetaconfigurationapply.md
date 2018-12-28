---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda SendMetaConfigurationApply klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b372a6c0ab9d4561dcf67026275e7d3ca6aa2584
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404783"
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d11c3-103">Metoda SendMetaConfigurationApply klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="d11c3-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d11c3-104">Ustawia ustawienia Local Configuration Manager, które są używane do kontrolowania przez agenta konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d11c3-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="d11c3-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d11c3-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="d11c3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d11c3-106">Parameters</span></span>

<span data-ttu-id="d11c3-107">*ConfigurationData* \[w\] danych środowiska dla konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d11c3-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="d11c3-108">*Wymuś* \[w\] **true** wymusić konfigurację, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="d11c3-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="d11c3-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d11c3-109">Return value</span></span>

<span data-ttu-id="d11c3-110">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="d11c3-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d11c3-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d11c3-111">Remarks</span></span>

<span data-ttu-id="d11c3-112">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="d11c3-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d11c3-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d11c3-113">Requirements</span></span>

<span data-ttu-id="d11c3-114">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d11c3-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d11c3-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d11c3-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d11c3-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d11c3-116">See also</span></span>

[<span data-ttu-id="d11c3-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d11c3-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)