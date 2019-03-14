---
title: Deklaracji atrybutu ValidateCount | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: 4e0be34b6f7a56dcf02a4381de4d2a5d08db14df
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794449"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="847e2-102">ValidateCount, deklaracja atrybutu</span><span class="sxs-lookup"><span data-stu-id="847e2-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="847e2-103">Atrybut ValidateCount określa minimalną i maksymalną liczbę argumentów, które mogą uzyskać parametr polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="847e2-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="847e2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="847e2-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="847e2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="847e2-105">Parameters</span></span>

<span data-ttu-id="847e2-106">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) wymagane.</span><span class="sxs-lookup"><span data-stu-id="847e2-106">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="847e2-107">Określa minimalną liczbę argumentów.</span><span class="sxs-lookup"><span data-stu-id="847e2-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="847e2-108">`MaxLength`([System.Int32](/dotnet/api/System.Int32)) wymagane.</span><span class="sxs-lookup"><span data-stu-id="847e2-108">`MaxLength`([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="847e2-109">Określa maksymalną liczbę argumentów.</span><span class="sxs-lookup"><span data-stu-id="847e2-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="847e2-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="847e2-110">Remarks</span></span>

- <span data-ttu-id="847e2-111">Aby uzyskać więcej informacji o tym, jak można zadeklarować tego atrybutu, zobacz [jak deklarować reguł sprawdzania poprawności danych wejściowych](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="847e2-111">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="847e2-112">Jeśli ten atrybut nie zostanie wywołany, z odpowiadającym mu parametrem polecenia cmdlet może mieć dowolną liczbę argumentów.</span><span class="sxs-lookup"><span data-stu-id="847e2-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="847e2-113">Środowisko wykonawcze programu Windows PowerShell zgłasza błąd w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="847e2-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="847e2-114">`MinLength` i `MaxLength` parametry atrybutów nie mają wartości typu [System.Int32](/dotnet/api/System.Int32).</span><span class="sxs-lookup"><span data-stu-id="847e2-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32](/dotnet/api/System.Int32).</span></span>

    - <span data-ttu-id="847e2-115">Wartość `MaxLength` parametru atrybutu jest mniejsza niż wartość `MinLength` parametr atrybutu.</span><span class="sxs-lookup"><span data-stu-id="847e2-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="847e2-116">Atrybut ValidateCount jest definiowany przez [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) klasy.</span><span class="sxs-lookup"><span data-stu-id="847e2-116">The ValidateCount attribute is defined by the [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="847e2-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="847e2-117">See Also</span></span>

[<span data-ttu-id="847e2-118">System.Management.Automation.Validatecount</span><span class="sxs-lookup"><span data-stu-id="847e2-118">System.Management.Automation.Validatecount</span></span>](/dotnet/api/System.Management.Automation.ValidateCount)

[<span data-ttu-id="847e2-119">Sposób deklarowania reguł sprawdzania poprawności danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="847e2-119">How to Declare Input Validation Rules</span></span>](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[<span data-ttu-id="847e2-120">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="847e2-120">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
