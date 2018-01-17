---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Metoda PerformRequiredConfigurationChecks klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 687c92f2dac5e8855731713e81390ac67615231e
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="75436-103">Metoda PerformRequiredConfigurationChecks klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="75436-103">PerformRequiredConfigurationChecks method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="75436-104">Uruchamia sprawdzanie spójności za pomocą harmonogramu zadań.</span><span class="sxs-lookup"><span data-stu-id="75436-104">Starts a consistency check by using the Task Scheduler.</span></span>

<a name="syntax"></a><span data-ttu-id="75436-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="75436-105">Syntax</span></span>
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a><span data-ttu-id="75436-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="75436-106">Parameters</span></span>
----------

<span data-ttu-id="75436-107">*Flagi* \[w\]</span><span class="sxs-lookup"><span data-stu-id="75436-107">*Flags* \[in\]</span></span>  
<span data-ttu-id="75436-108">Maska bitowa określający typ uruchamianie sprawdzania spójności.</span><span class="sxs-lookup"><span data-stu-id="75436-108">A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="75436-109">Następujące wartości są prawidłowe i mogą być łączone przy użyciu bitowej **lub** operacji:</span><span class="sxs-lookup"><span data-stu-id="75436-109">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="75436-110">Wartość</span><span class="sxs-lookup"><span data-stu-id="75436-110">Value</span></span> |<span data-ttu-id="75436-111">Opis</span><span class="sxs-lookup"><span data-stu-id="75436-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="75436-112">**1**</span><span class="sxs-lookup"><span data-stu-id="75436-112">**1**</span></span> | <span data-ttu-id="75436-113">Sprawdzanie spójności normalnego.</span><span class="sxs-lookup"><span data-stu-id="75436-113">A normal consistency check.</span></span> |
|<span data-ttu-id="75436-114">**2**</span><span class="sxs-lookup"><span data-stu-id="75436-114">**2**</span></span> | <span data-ttu-id="75436-115">Kontynuacja sprawdzania spójności po ponownym rozruchu.</span><span class="sxs-lookup"><span data-stu-id="75436-115">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="75436-116">Tej wartości nie powinny być połączone z innych wartości.</span><span class="sxs-lookup"><span data-stu-id="75436-116">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="75436-117">**4**</span><span class="sxs-lookup"><span data-stu-id="75436-117">**4**</span></span> | <span data-ttu-id="75436-118">Konfiguracja powinna pobierane z serwera ściągania określone w metakonfigurację dla węzła.</span><span class="sxs-lookup"><span data-stu-id="75436-118">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="75436-119">Ta wartość powinna być zawsze połączone z **1**, dla wartości **5**.</span><span class="sxs-lookup"><span data-stu-id="75436-119">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="75436-120">**8**</span><span class="sxs-lookup"><span data-stu-id="75436-120">**8**</span></span> | <span data-ttu-id="75436-121">Wyślij stanu na serwerze raportów.</span><span class="sxs-lookup"><span data-stu-id="75436-121">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="75436-122">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="75436-122">Return value</span></span>
------------

<span data-ttu-id="75436-123">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="75436-123">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="75436-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="75436-124">Remarks</span></span>

<span data-ttu-id="75436-125">To jest metodą statyczną.</span><span class="sxs-lookup"><span data-stu-id="75436-125">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="75436-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="75436-126">Requirements</span></span>
------------
><span data-ttu-id="75436-127">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="75436-127">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="75436-128">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="75436-128">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="75436-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="75436-129">See also</span></span>


[<span data-ttu-id="75436-130">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="75436-130">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



