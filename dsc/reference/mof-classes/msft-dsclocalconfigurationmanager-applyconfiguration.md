---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda ApplyConfiguration
ms.openlocfilehash: 0425b9a7db37e421830ba37da8f5c0a4877a1b72
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727181"
---
# <a name="applyconfiguration-method"></a><span data-ttu-id="93a1b-103">Metoda ApplyConfiguration</span><span class="sxs-lookup"><span data-stu-id="93a1b-103">ApplyConfiguration method</span></span>

<span data-ttu-id="93a1b-104">Używa agenta konfiguracji, aby zastosować konfigurację, która jest w stanie oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="93a1b-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="93a1b-105">Jeśli nie ma nic do czasu, ta metoda przywrócenie bieżącej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="93a1b-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="93a1b-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="93a1b-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="93a1b-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="93a1b-107">Parameters</span></span>

<span data-ttu-id="93a1b-108">*Wymuś* \[w\] Jeśli jest to **true**, bieżąca konfiguracja jest ponownie stosowana, nawet jeśli istnieje oczekująca konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="93a1b-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="93a1b-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="93a1b-109">Return value</span></span>

<span data-ttu-id="93a1b-110">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="93a1b-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="93a1b-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="93a1b-111">Remarks</span></span>

<span data-ttu-id="93a1b-112">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="93a1b-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="93a1b-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="93a1b-113">Requirements</span></span>

<span data-ttu-id="93a1b-114">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="93a1b-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="93a1b-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="93a1b-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="93a1b-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="93a1b-116">See also</span></span>

[<span data-ttu-id="93a1b-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="93a1b-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
