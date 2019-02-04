---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda RemoveConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 03555cc73da1272bdebebc3d93b26aaf8fabc18e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683905"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="fe3f3-103">Metoda RemoveConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="fe3f3-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="fe3f3-104">Usuwa pliki konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="fe3f3-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="fe3f3-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="fe3f3-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="fe3f3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="fe3f3-106">Parameters</span></span>

<span data-ttu-id="fe3f3-107">*Etap* \[w\] Określa, które dokumentu konfiguracji do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="fe3f3-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="fe3f3-108">Następujące wartości są prawidłowe:</span><span class="sxs-lookup"><span data-stu-id="fe3f3-108">The following values are valid:</span></span>

|<span data-ttu-id="fe3f3-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="fe3f3-109">Value</span></span> |<span data-ttu-id="fe3f3-110">Opis</span><span class="sxs-lookup"><span data-stu-id="fe3f3-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="fe3f3-111">**1**</span><span class="sxs-lookup"><span data-stu-id="fe3f3-111">**1**</span></span> | <span data-ttu-id="fe3f3-112">**Bieżącego** dokumentu konfiguracji (current.mof).</span><span class="sxs-lookup"><span data-stu-id="fe3f3-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="fe3f3-113">**2**</span><span class="sxs-lookup"><span data-stu-id="fe3f3-113">**2**</span></span> | <span data-ttu-id="fe3f3-114">**Oczekujące** dokumentu konfiguracji (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="fe3f3-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="fe3f3-115">**4**</span><span class="sxs-lookup"><span data-stu-id="fe3f3-115">**4**</span></span> | <span data-ttu-id="fe3f3-116">**Wstecz** dokumentu konfiguracji (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="fe3f3-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="fe3f3-117">*Wymuś* \[w\] **true** wymusić usunięcie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="fe3f3-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="fe3f3-118">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fe3f3-118">Return value</span></span>

<span data-ttu-id="fe3f3-119">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="fe3f3-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="fe3f3-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fe3f3-120">Remarks</span></span>

<span data-ttu-id="fe3f3-121">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="fe3f3-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="fe3f3-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fe3f3-122">Requirements</span></span>

<span data-ttu-id="fe3f3-123">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="fe3f3-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="fe3f3-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="fe3f3-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="fe3f3-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe3f3-125">See also</span></span>

[<span data-ttu-id="fe3f3-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="fe3f3-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)