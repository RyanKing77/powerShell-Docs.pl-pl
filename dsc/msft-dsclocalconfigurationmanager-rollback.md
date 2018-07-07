---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Metoda RollBack klasy MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 4956900ecd2c9cb7f2e2b5bcab94616f9f5d5565
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893022"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7dde0-103">Metoda RollBack klasy MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="7dde0-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7dde0-104">Nastąpi powrót do wcześniejszej konfiguracji do poprzedniej wersji.</span><span class="sxs-lookup"><span data-stu-id="7dde0-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="7dde0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7dde0-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="7dde0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7dde0-106">Parameters</span></span>

<span data-ttu-id="7dde0-107">*configurationNumber* \[w\] określa żądanej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7dde0-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="7dde0-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7dde0-108">Return value</span></span>

<span data-ttu-id="7dde0-109">Zwraca wartość zero w przypadku powodzenia; w przeciwnym razie zwraca kod błędu.</span><span class="sxs-lookup"><span data-stu-id="7dde0-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7dde0-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7dde0-110">Remarks</span></span>

<span data-ttu-id="7dde0-111">Jest to metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="7dde0-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7dde0-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7dde0-112">Requirements</span></span>

<span data-ttu-id="7dde0-113">**Plik MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7dde0-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="7dde0-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7dde0-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="7dde0-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7dde0-115">See also</span></span>

[<span data-ttu-id="7dde0-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7dde0-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)