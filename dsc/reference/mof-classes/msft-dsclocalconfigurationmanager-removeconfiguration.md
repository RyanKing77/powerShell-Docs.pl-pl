---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda RemoveConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 03555cc73da1272bdebebc3d93b26aaf8fabc18e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078694"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="cdfab-103">Metoda RemoveConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="cdfab-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="cdfab-104">Usuwa pliki konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cdfab-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="cdfab-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="cdfab-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="cdfab-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="cdfab-106">Parameters</span></span>

<span data-ttu-id="cdfab-107">*Etap* \[w\] Określa, które dokumentu konfiguracji do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="cdfab-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="cdfab-108">Następujące wartości są prawidłowe:</span><span class="sxs-lookup"><span data-stu-id="cdfab-108">The following values are valid:</span></span>

|<span data-ttu-id="cdfab-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="cdfab-109">Value</span></span> |<span data-ttu-id="cdfab-110">Opis</span><span class="sxs-lookup"><span data-stu-id="cdfab-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="cdfab-111">**1**</span><span class="sxs-lookup"><span data-stu-id="cdfab-111">**1**</span></span> | <span data-ttu-id="cdfab-112">**Bieżącego** dokumentu konfiguracji (current.mof).</span><span class="sxs-lookup"><span data-stu-id="cdfab-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="cdfab-113">**2**</span><span class="sxs-lookup"><span data-stu-id="cdfab-113">**2**</span></span> | <span data-ttu-id="cdfab-114">**Oczekujące** dokumentu konfiguracji (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="cdfab-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="cdfab-115">**4**</span><span class="sxs-lookup"><span data-stu-id="cdfab-115">**4**</span></span> | <span data-ttu-id="cdfab-116">**Wstecz** dokumentu konfiguracji (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="cdfab-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="cdfab-117">*Wymuś* \[w\] **true** wymusić usunięcie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cdfab-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="cdfab-118">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cdfab-118">Return value</span></span>

<span data-ttu-id="cdfab-119">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="cdfab-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="cdfab-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cdfab-120">Remarks</span></span>

<span data-ttu-id="cdfab-121">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="cdfab-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="cdfab-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cdfab-122">Requirements</span></span>

<span data-ttu-id="cdfab-123">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="cdfab-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="cdfab-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="cdfab-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="cdfab-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cdfab-125">See also</span></span>

[<span data-ttu-id="cdfab-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="cdfab-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)