---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda PerformRequiredConfigurationChecks klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b92eefb7fbea6d96afa31f6b802ba10fe20d4103
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687496"
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="923d6-103">Metoda PerformRequiredConfigurationChecks klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="923d6-103">PerformRequiredConfigurationChecks method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="923d6-104">Uruchamia kontrolę spójności przy użyciu harmonogramu zadań.</span><span class="sxs-lookup"><span data-stu-id="923d6-104">Starts a consistency check by using the Task Scheduler.</span></span>

## <a name="syntax"></a><span data-ttu-id="923d6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="923d6-105">Syntax</span></span>

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a><span data-ttu-id="923d6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="923d6-106">Parameters</span></span>

<span data-ttu-id="923d6-107">*Flagi* \[w\] maski bitów, który określa typ uruchamianie sprawdzania spójności.</span><span class="sxs-lookup"><span data-stu-id="923d6-107">*Flags* \[in\] A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="923d6-108">Następujące wartości są prawidłowe i mogą być połączone za pomocą bitowej **lub** operacji:</span><span class="sxs-lookup"><span data-stu-id="923d6-108">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="923d6-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="923d6-109">Value</span></span> |<span data-ttu-id="923d6-110">Opis</span><span class="sxs-lookup"><span data-stu-id="923d6-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="923d6-111">**1**</span><span class="sxs-lookup"><span data-stu-id="923d6-111">**1**</span></span> | <span data-ttu-id="923d6-112">Sprawdzanie spójności normalny.</span><span class="sxs-lookup"><span data-stu-id="923d6-112">A normal consistency check.</span></span> |
|<span data-ttu-id="923d6-113">**2**</span><span class="sxs-lookup"><span data-stu-id="923d6-113">**2**</span></span> | <span data-ttu-id="923d6-114">Kontynuacja sprawdzania spójności po ponownym uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="923d6-114">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="923d6-115">Ta wartość nie powinny być połączone z inne wartości.</span><span class="sxs-lookup"><span data-stu-id="923d6-115">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="923d6-116">**4**</span><span class="sxs-lookup"><span data-stu-id="923d6-116">**4**</span></span> | <span data-ttu-id="923d6-117">Konfigurację powinny zostać pobrane z serwera ściągania określone w metaconfiguration dla węzła.</span><span class="sxs-lookup"><span data-stu-id="923d6-117">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="923d6-118">Wartość ta zawsze powinny być połączone z **1**, dla wartości **5**.</span><span class="sxs-lookup"><span data-stu-id="923d6-118">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="923d6-119">**8**</span><span class="sxs-lookup"><span data-stu-id="923d6-119">**8**</span></span> | <span data-ttu-id="923d6-120">Wyślij stanu na serwerze raportów.</span><span class="sxs-lookup"><span data-stu-id="923d6-120">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="923d6-121">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="923d6-121">Return value</span></span>

<span data-ttu-id="923d6-122">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="923d6-122">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="923d6-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="923d6-123">Remarks</span></span>

<span data-ttu-id="923d6-124">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="923d6-124">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="923d6-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="923d6-125">Requirements</span></span>

<span data-ttu-id="923d6-126">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="923d6-126">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="923d6-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="923d6-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="923d6-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="923d6-128">See also</span></span>

[<span data-ttu-id="923d6-129">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="923d6-129">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)