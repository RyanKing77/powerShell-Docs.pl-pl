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
ms.openlocfilehash: 1a7b5ea340fe5212d003c97a9017278d6c631355
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849021"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="ea6a8-102">ValidateCount, deklaracja atrybutu</span><span class="sxs-lookup"><span data-stu-id="ea6a8-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="ea6a8-103">Atrybut ValidateCount określa minimalną i maksymalną liczbę argumentów, które mogą uzyskać parametr polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ea6a8-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="ea6a8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ea6a8-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="ea6a8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea6a8-105">Parameters</span></span>

<span data-ttu-id="ea6a8-106">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) wymagane.</span><span class="sxs-lookup"><span data-stu-id="ea6a8-106">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="ea6a8-107">Określa minimalną liczbę argumentów.</span><span class="sxs-lookup"><span data-stu-id="ea6a8-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="ea6a8-108">`MaxLength`([System.Int32](/dotnet/api/System.Int32)) wymagane.</span><span class="sxs-lookup"><span data-stu-id="ea6a8-108">`MaxLength`([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="ea6a8-109">Określa maksymalną liczbę argumentów.</span><span class="sxs-lookup"><span data-stu-id="ea6a8-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="ea6a8-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ea6a8-110">Remarks</span></span>

- <span data-ttu-id="ea6a8-111">Aby uzyskać więcej informacji o tym, jak można zadeklarować tego atrybutu, zobacz [jak deklarować reguł sprawdzania poprawności danych wejściowych](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="ea6a8-111">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="ea6a8-112">Jeśli ten atrybut nie zostanie wywołany, z odpowiadającym mu parametrem polecenia cmdlet może mieć dowolną liczbę argumentów.</span><span class="sxs-lookup"><span data-stu-id="ea6a8-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="ea6a8-113">Środowisko wykonawcze programu Windows PowerShell zgłasza błąd w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="ea6a8-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="ea6a8-114">`MinLength` i `MaxLength` parametry atrybutów nie mają wartości typu [System.Int32](/dotnet/api/System.Int32).</span><span class="sxs-lookup"><span data-stu-id="ea6a8-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32](/dotnet/api/System.Int32).</span></span>

    - <span data-ttu-id="ea6a8-115">Wartość `MaxLength` parametru atrybutu jest mniejsza niż wartość `MinLength` parametr atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ea6a8-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="ea6a8-116">Atrybut ValidateCount jest definiowany przez [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) klasy.</span><span class="sxs-lookup"><span data-stu-id="ea6a8-116">The ValidateCount attribute is defined by the [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="ea6a8-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ea6a8-117">See Also</span></span>

[<span data-ttu-id="ea6a8-118">System.Management.Automation.Validatecount</span><span class="sxs-lookup"><span data-stu-id="ea6a8-118">System.Management.Automation.Validatecount</span></span>](/dotnet/api/System.Management.Automation.ValidateCount)

[<span data-ttu-id="ea6a8-119">Sposób deklarowania reguł sprawdzania poprawności danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="ea6a8-119">How to Declare Input Validation Rules</span></span>](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[<span data-ttu-id="ea6a8-120">Sposób deklarowania reguł sprawdzania poprawności danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="ea6a8-120">How to Declare Input Validation Rules</span></span>](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[<span data-ttu-id="ea6a8-121">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ea6a8-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
