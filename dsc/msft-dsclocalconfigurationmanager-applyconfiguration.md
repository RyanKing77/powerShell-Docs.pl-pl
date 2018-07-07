---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda ApplyConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 559ff1793a18e28dad2f176bdb20eb53bc08630d
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892618"
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="24de2-103">Metoda ApplyConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="24de2-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="24de2-104">Używa agenta konfiguracji, aby zastosować konfigurację, która jest w stanie oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="24de2-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="24de2-105">Jeśli nie ma nic do czasu, ta metoda przywrócenie bieżącej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="24de2-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="24de2-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="24de2-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="24de2-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="24de2-107">Parameters</span></span>

<span data-ttu-id="24de2-108">*Wymuś* \[w\] Jeśli jest to **true**, bieżąca konfiguracja jest ponownie stosowana, nawet jeśli istnieje oczekująca konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="24de2-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="24de2-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="24de2-109">Return value</span></span>

<span data-ttu-id="24de2-110">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="24de2-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="24de2-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="24de2-111">Remarks</span></span>

<span data-ttu-id="24de2-112">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="24de2-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="24de2-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="24de2-113">Requirements</span></span>

<span data-ttu-id="24de2-114">**Plik MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="24de2-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="24de2-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="24de2-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="24de2-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24de2-116">See also</span></span>

[<span data-ttu-id="24de2-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="24de2-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)