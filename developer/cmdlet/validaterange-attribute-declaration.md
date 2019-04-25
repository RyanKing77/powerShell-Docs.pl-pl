---
title: Deklaracji atrybutu ValidateRange | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.assetid: 1f8066e6-e5d3-4f4e-8948-a90af5dace82
caps.latest.revision: 11
ms.openlocfilehash: 155a406b9855c435041fe175ac7d983a4b4eb8b7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067114"
---
# <a name="validaterange-attribute-declaration"></a><span data-ttu-id="42e47-102">ValidateRange, deklaracja atrybutu</span><span class="sxs-lookup"><span data-stu-id="42e47-102">ValidateRange Attribute Declaration</span></span>

<span data-ttu-id="42e47-103">Atrybut ValidateRange określa minimalne i maksymalne wartości (zakres) dla argumentu parametru polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="42e47-103">The ValidateRange attribute specifies the minimum and maximum values (the range) for the cmdlet parameter argument.</span></span> <span data-ttu-id="42e47-104">Ten atrybut umożliwia także przez funkcje programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="42e47-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="42e47-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="42e47-105">Syntax</span></span>

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a><span data-ttu-id="42e47-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="42e47-106">Parameters</span></span>

<span data-ttu-id="42e47-107">`MinRange` ([System.Object](/dotnet/api/system.object)) wymagane.</span><span class="sxs-lookup"><span data-stu-id="42e47-107">`MinRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="42e47-108">Określa minimalna dozwolona wartość.</span><span class="sxs-lookup"><span data-stu-id="42e47-108">Specifies the minimum value allowed.</span></span>

<span data-ttu-id="42e47-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) wymagane.</span><span class="sxs-lookup"><span data-stu-id="42e47-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="42e47-110">Określa maksymalną dozwoloną wartość.</span><span class="sxs-lookup"><span data-stu-id="42e47-110">Specifies the maximum value allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="42e47-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="42e47-111">Remarks</span></span>

- <span data-ttu-id="42e47-112">Środowisko wykonawcze programu Windows PowerShell zgłasza błąd budowy po wartości `MinRange` parametru jest większa niż wartość `MaxRange` parametru.</span><span class="sxs-lookup"><span data-stu-id="42e47-112">The Windows PowerShell runtime throws a construction error when the value of the `MinRange` parameter is greater than the value of the `MaxRange` parameter.</span></span>

- <span data-ttu-id="42e47-113">Środowisko wykonawcze programu Windows PowerShell zgłasza błąd sprawdzania poprawności w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="42e47-113">The Windows PowerShell runtime throws a validation error under the following conditions:</span></span>

    - <span data-ttu-id="42e47-114">Gdy wartość argumentu jest mniejsza niż `MinRange` limit lub większa niż `MaxRange` limit.</span><span class="sxs-lookup"><span data-stu-id="42e47-114">When the value of the argument is less than the `MinRange` limit or greater than the `MaxRange` limit.</span></span>

    - <span data-ttu-id="42e47-115">Jeśli argument nie jest tego samego typu co `MinRange` i `MaxRange` parametrów.</span><span class="sxs-lookup"><span data-stu-id="42e47-115">When the argument is not of the same type as the `MinRange` and the `MaxRange` parameters.</span></span>

- <span data-ttu-id="42e47-116">Atrybut ValidateRange jest definiowany przez [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) klasy.</span><span class="sxs-lookup"><span data-stu-id="42e47-116">The ValidateRange attribute is defined by the [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="42e47-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="42e47-117">See Also</span></span>

[<span data-ttu-id="42e47-118">System.Management.Automation.Validaterangeattribute</span><span class="sxs-lookup"><span data-stu-id="42e47-118">System.Management.Automation.Validaterangeattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[<span data-ttu-id="42e47-119">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="42e47-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
