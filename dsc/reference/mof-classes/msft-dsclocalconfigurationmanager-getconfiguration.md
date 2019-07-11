---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Getconfiguration — metoda
ms.openlocfilehash: eabc536cfe69abe1144ff031a6f64c09a772e638
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734521"
---
# <a name="getconfiguration-method"></a><span data-ttu-id="c3a2c-103">Getconfiguration — metoda</span><span class="sxs-lookup"><span data-stu-id="c3a2c-103">GetConfiguration method</span></span>

<span data-ttu-id="c3a2c-104">Wysyła dokument konfiguracji do zarządzanego węzła i używa **uzyskać** metoda przez agenta konfiguracji, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="c3a2c-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="c3a2c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c3a2c-105">Syntax</span></span>

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a><span data-ttu-id="c3a2c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3a2c-106">Parameters</span></span>

<span data-ttu-id="c3a2c-107">*configurationData* \[w\] Określa dane konfiguracji do wysłania.</span><span class="sxs-lookup"><span data-stu-id="c3a2c-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="c3a2c-108">*konfiguracje* \[się\] przy powrocie, zawiera wystąpienie osadzony w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c3a2c-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="c3a2c-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c3a2c-109">Return value</span></span>

<span data-ttu-id="c3a2c-110">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="c3a2c-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c3a2c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c3a2c-111">Remarks</span></span>

<span data-ttu-id="c3a2c-112">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="c3a2c-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c3a2c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c3a2c-113">Requirements</span></span>

<span data-ttu-id="c3a2c-114">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c3a2c-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="c3a2c-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c3a2c-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="c3a2c-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c3a2c-116">See also</span></span>

[<span data-ttu-id="c3a2c-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c3a2c-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
