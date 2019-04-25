---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda ApplyConfiguration klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 559ff1793a18e28dad2f176bdb20eb53bc08630d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079170"
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="fea2c-103">Metoda ApplyConfiguration klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="fea2c-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="fea2c-104">Używa agenta konfiguracji, aby zastosować konfigurację, która jest w stanie oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="fea2c-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="fea2c-105">Jeśli nie ma nic do czasu, ta metoda przywrócenie bieżącej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="fea2c-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="fea2c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="fea2c-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="fea2c-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="fea2c-107">Parameters</span></span>

<span data-ttu-id="fea2c-108">*Wymuś* \[w\] Jeśli jest to **true**, bieżąca konfiguracja jest ponownie stosowana, nawet jeśli istnieje oczekująca konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="fea2c-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="fea2c-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fea2c-109">Return value</span></span>

<span data-ttu-id="fea2c-110">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="fea2c-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="fea2c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fea2c-111">Remarks</span></span>

<span data-ttu-id="fea2c-112">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="fea2c-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="fea2c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fea2c-113">Requirements</span></span>

<span data-ttu-id="fea2c-114">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="fea2c-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="fea2c-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="fea2c-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="fea2c-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fea2c-116">See also</span></span>

[<span data-ttu-id="fea2c-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="fea2c-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)