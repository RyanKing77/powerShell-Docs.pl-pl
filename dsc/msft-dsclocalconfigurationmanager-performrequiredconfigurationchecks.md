---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Metoda PerformRequiredConfigurationChecks klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: c3fdaa23875815b1cf5cbf0b6e21c633e00664aa
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186698"
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="79981-103">Metoda PerformRequiredConfigurationChecks klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="79981-103">PerformRequiredConfigurationChecks method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="79981-104">Uruchamia sprawdzanie spójności za pomocą harmonogramu zadań.</span><span class="sxs-lookup"><span data-stu-id="79981-104">Starts a consistency check by using the Task Scheduler.</span></span>

<a name="syntax"></a><span data-ttu-id="79981-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="79981-105">Syntax</span></span>
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a><span data-ttu-id="79981-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="79981-106">Parameters</span></span>
----------

<span data-ttu-id="79981-107">*Flagi* \[w\] maski, która określa typ Sprawdzanie spójności, aby uruchomić.</span><span class="sxs-lookup"><span data-stu-id="79981-107">*Flags* \[in\] A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="79981-108">Następujące wartości są prawidłowe i mogą być łączone przy użyciu bitowej **lub** operacji:</span><span class="sxs-lookup"><span data-stu-id="79981-108">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="79981-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="79981-109">Value</span></span> |<span data-ttu-id="79981-110">Opis</span><span class="sxs-lookup"><span data-stu-id="79981-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="79981-111">**1**</span><span class="sxs-lookup"><span data-stu-id="79981-111">**1**</span></span> | <span data-ttu-id="79981-112">Sprawdzanie spójności normalnego.</span><span class="sxs-lookup"><span data-stu-id="79981-112">A normal consistency check.</span></span> |
|<span data-ttu-id="79981-113">**2**</span><span class="sxs-lookup"><span data-stu-id="79981-113">**2**</span></span> | <span data-ttu-id="79981-114">Kontynuacja sprawdzania spójności po ponownym rozruchu.</span><span class="sxs-lookup"><span data-stu-id="79981-114">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="79981-115">Tej wartości nie powinny być połączone z innych wartości.</span><span class="sxs-lookup"><span data-stu-id="79981-115">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="79981-116">**4**</span><span class="sxs-lookup"><span data-stu-id="79981-116">**4**</span></span> | <span data-ttu-id="79981-117">Konfiguracja powinna pobierane z serwera ściągania określone w metakonfigurację dla węzła.</span><span class="sxs-lookup"><span data-stu-id="79981-117">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="79981-118">Ta wartość powinna być zawsze połączone z **1**, dla wartości **5**.</span><span class="sxs-lookup"><span data-stu-id="79981-118">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="79981-119">**8**</span><span class="sxs-lookup"><span data-stu-id="79981-119">**8**</span></span> | <span data-ttu-id="79981-120">Wyślij stanu na serwerze raportów.</span><span class="sxs-lookup"><span data-stu-id="79981-120">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="79981-121">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="79981-121">Return value</span></span>
------------

<span data-ttu-id="79981-122">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="79981-122">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="79981-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="79981-123">Remarks</span></span>

<span data-ttu-id="79981-124">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="79981-124">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="79981-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="79981-125">Requirements</span></span>
------------
><span data-ttu-id="79981-126">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="79981-126">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="79981-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="79981-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="79981-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="79981-128">See also</span></span>


[<span data-ttu-id="79981-129">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="79981-129">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)