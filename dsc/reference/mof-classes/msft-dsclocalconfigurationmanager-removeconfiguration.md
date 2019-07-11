---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda RemoveConfiguration
ms.openlocfilehash: aacbed96beb960d7e0d449423a4de9a27f0a287e
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734389"
---
# <a name="removeconfiguration-method"></a><span data-ttu-id="fc32a-103">Metoda RemoveConfiguration</span><span class="sxs-lookup"><span data-stu-id="fc32a-103">RemoveConfiguration method</span></span>

<span data-ttu-id="fc32a-104">Usuwa pliki konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="fc32a-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="fc32a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc32a-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="fc32a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc32a-106">Parameters</span></span>

<span data-ttu-id="fc32a-107">*Etap* \[w\] Określa, które dokumentu konfiguracji do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="fc32a-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="fc32a-108">Następujące wartości są prawidłowe:</span><span class="sxs-lookup"><span data-stu-id="fc32a-108">The following values are valid:</span></span>

|<span data-ttu-id="fc32a-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="fc32a-109">Value</span></span> |<span data-ttu-id="fc32a-110">Opis</span><span class="sxs-lookup"><span data-stu-id="fc32a-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="fc32a-111">**1**</span><span class="sxs-lookup"><span data-stu-id="fc32a-111">**1**</span></span> | <span data-ttu-id="fc32a-112">**Bieżącego** dokumentu konfiguracji (current.mof).</span><span class="sxs-lookup"><span data-stu-id="fc32a-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="fc32a-113">**2**</span><span class="sxs-lookup"><span data-stu-id="fc32a-113">**2**</span></span> | <span data-ttu-id="fc32a-114">**Oczekujące** dokumentu konfiguracji (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="fc32a-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="fc32a-115">**4**</span><span class="sxs-lookup"><span data-stu-id="fc32a-115">**4**</span></span> | <span data-ttu-id="fc32a-116">**Wstecz** dokumentu konfiguracji (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="fc32a-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="fc32a-117">*Wymuś* \[w\] **true** wymusić usunięcie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="fc32a-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="fc32a-118">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fc32a-118">Return value</span></span>

<span data-ttu-id="fc32a-119">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="fc32a-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="fc32a-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fc32a-120">Remarks</span></span>

<span data-ttu-id="fc32a-121">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="fc32a-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="fc32a-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fc32a-122">Requirements</span></span>

<span data-ttu-id="fc32a-123">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="fc32a-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="fc32a-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="fc32a-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="fc32a-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fc32a-125">See also</span></span>

[<span data-ttu-id="fc32a-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="fc32a-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
