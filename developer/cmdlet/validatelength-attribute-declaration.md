---
title: Deklaracji atrybutu ValidateLength | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.assetid: 82fe3a35-a94b-4bc1-ad9e-dfc5f1e788b3
caps.latest.revision: 13
ms.openlocfilehash: 3a4c5f279ce8587eeb5d583376ea3d2286210b83
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067165"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="f5935-102">ValidateLength, deklaracja atrybutu</span><span class="sxs-lookup"><span data-stu-id="f5935-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="f5935-103">Atrybut ValidateLength określa minimalną i maksymalną liczbę znaków dla parametru w argumencie polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f5935-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="f5935-104">Ten atrybut umożliwia także przez funkcje programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f5935-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="f5935-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f5935-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="f5935-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5935-106">Parameters</span></span>

<span data-ttu-id="f5935-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) wymagane.</span><span class="sxs-lookup"><span data-stu-id="f5935-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="f5935-108">Określa minimalną liczbę znaków.</span><span class="sxs-lookup"><span data-stu-id="f5935-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="f5935-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) wymagane.</span><span class="sxs-lookup"><span data-stu-id="f5935-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="f5935-110">Określa maksymalną liczbę znaków.</span><span class="sxs-lookup"><span data-stu-id="f5935-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="f5935-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f5935-111">Remarks</span></span>

- <span data-ttu-id="f5935-112">Aby uzyskać więcej informacji o tym, jak można zadeklarować tego atrybutu, zobacz [jak deklarować reguł sprawdzania poprawności danych wejściowych](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="f5935-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="f5935-113">Jeśli ten atrybut nie jest używana, odpowiedni argument parametru może być o dowolnej długości.</span><span class="sxs-lookup"><span data-stu-id="f5935-113">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="f5935-114">Środowisko wykonawcze programu Windows PowerShell zgłasza błąd w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="f5935-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="f5935-115">Gdy wartość `MaxLength` parametru atrybutu jest mniejsza niż wartość `MinLength` parametr atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f5935-115">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

    - <span data-ttu-id="f5935-116">Gdy `MaxLength` parametru atrybutu jest równa 0.</span><span class="sxs-lookup"><span data-stu-id="f5935-116">When the `MaxLength` attribute parameter is set to 0.</span></span>

    - <span data-ttu-id="f5935-117">Jeśli argument nie jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="f5935-117">When the argument is not a string.</span></span>

- <span data-ttu-id="f5935-118">Atrybut ValidateLength jest definiowany przez [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) klasy.</span><span class="sxs-lookup"><span data-stu-id="f5935-118">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5935-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f5935-119">See Also</span></span>

[<span data-ttu-id="f5935-120">System.Management.Automation.Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="f5935-120">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="f5935-121">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f5935-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
