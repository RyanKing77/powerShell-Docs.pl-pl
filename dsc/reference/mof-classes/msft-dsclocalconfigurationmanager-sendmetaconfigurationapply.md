---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda SendMetaConfigurationApply klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b372a6c0ab9d4561dcf67026275e7d3ca6aa2584
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048554"
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="05a4f-103">Metoda SendMetaConfigurationApply klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="05a4f-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="05a4f-104">Ustawia ustawienia Local Configuration Manager, które są używane do kontrolowania przez agenta konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="05a4f-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="05a4f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="05a4f-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="05a4f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="05a4f-106">Parameters</span></span>

<span data-ttu-id="05a4f-107">*ConfigurationData* \[w\] danych środowiska dla konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="05a4f-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="05a4f-108">*Wymuś* \[w\] **true** wymusić konfigurację, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="05a4f-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="05a4f-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="05a4f-109">Return value</span></span>

<span data-ttu-id="05a4f-110">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="05a4f-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="05a4f-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="05a4f-111">Remarks</span></span>

<span data-ttu-id="05a4f-112">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="05a4f-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="05a4f-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="05a4f-113">Requirements</span></span>

<span data-ttu-id="05a4f-114">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="05a4f-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="05a4f-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="05a4f-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="05a4f-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05a4f-116">See also</span></span>

[<span data-ttu-id="05a4f-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="05a4f-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)