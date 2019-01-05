---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda GetConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ae31ac30c152c96707b764ddaf00c924806afcfc
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048565"
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="60893-103">Metoda GetConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="60893-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="60893-104">Wysyła dokument konfiguracji do zarządzanego węzła i używa **uzyskać** metoda przez agenta konfiguracji, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="60893-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="60893-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="60893-105">Syntax</span></span>

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a><span data-ttu-id="60893-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="60893-106">Parameters</span></span>

<span data-ttu-id="60893-107">*configurationData* \[w\] Określa dane konfiguracji do wysłania.</span><span class="sxs-lookup"><span data-stu-id="60893-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="60893-108">*konfiguracje* \[się\] przy powrocie, zawiera wystąpienie osadzony w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="60893-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="60893-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="60893-109">Return value</span></span>

<span data-ttu-id="60893-110">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="60893-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="60893-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="60893-111">Remarks</span></span>

<span data-ttu-id="60893-112">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="60893-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="60893-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="60893-113">Requirements</span></span>

<span data-ttu-id="60893-114">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="60893-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="60893-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="60893-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="60893-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="60893-116">See also</span></span>

[<span data-ttu-id="60893-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="60893-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)