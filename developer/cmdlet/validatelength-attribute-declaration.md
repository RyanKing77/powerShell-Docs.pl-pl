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
ms.openlocfilehash: 4d3cdccc0fe3e24b1221e41beef4821b613aab93
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855157"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="c91fa-102">ValidateLength, deklaracja atrybutu</span><span class="sxs-lookup"><span data-stu-id="c91fa-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="c91fa-103">Atrybut ValidateLength określa minimalną i maksymalną liczbę znaków dla parametru w argumencie polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c91fa-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="c91fa-104">Ten atrybut umożliwia także przez funkcje programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c91fa-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="c91fa-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c91fa-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="c91fa-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c91fa-106">Parameters</span></span>

<span data-ttu-id="c91fa-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) wymagane.</span><span class="sxs-lookup"><span data-stu-id="c91fa-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="c91fa-108">Określa minimalną liczbę znaków.</span><span class="sxs-lookup"><span data-stu-id="c91fa-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="c91fa-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) wymagane.</span><span class="sxs-lookup"><span data-stu-id="c91fa-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="c91fa-110">Określa maksymalną liczbę znaków.</span><span class="sxs-lookup"><span data-stu-id="c91fa-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="c91fa-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c91fa-111">Remarks</span></span>

- <span data-ttu-id="c91fa-112">Aby uzyskać więcej informacji o tym, jak można zadeklarować tego atrybutu, zobacz [jak deklarować reguł sprawdzania poprawności danych wejściowych](./how-to-validate-parameter-input.md).</span><span class="sxs-lookup"><span data-stu-id="c91fa-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](./how-to-validate-parameter-input.md).</span></span>

- <span data-ttu-id="c91fa-113">Jeśli ten atrybut nie jest używana, odpowiedni argument parametru może być o dowolnej długości.</span><span class="sxs-lookup"><span data-stu-id="c91fa-113">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="c91fa-114">Środowisko wykonawcze programu Windows PowerShell zgłasza błąd w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="c91fa-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="c91fa-115">Gdy wartość `MaxLength` parametru atrybutu jest mniejsza niż wartość `MinLength` parametr atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c91fa-115">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

    - <span data-ttu-id="c91fa-116">Gdy `MaxLength` parametru atrybutu jest równa 0.</span><span class="sxs-lookup"><span data-stu-id="c91fa-116">When the `MaxLength` attribute parameter is set to 0.</span></span>

    - <span data-ttu-id="c91fa-117">Jeśli argument nie jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="c91fa-117">When the argument is not a string.</span></span>

- <span data-ttu-id="c91fa-118">Atrybut ValidateLength jest definiowany przez [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) klasy.</span><span class="sxs-lookup"><span data-stu-id="c91fa-118">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="c91fa-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c91fa-119">See Also</span></span>

[<span data-ttu-id="c91fa-120">System.Management.Automation.Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="c91fa-120">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="c91fa-121">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c91fa-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
