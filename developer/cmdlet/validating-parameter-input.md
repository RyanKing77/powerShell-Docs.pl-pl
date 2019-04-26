---
title: Walidacja danych wejściowych parametr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.assetid: 3f15bf20-a068-4a7d-a170-bc43f755d1fe
caps.latest.revision: 14
ms.openlocfilehash: 171e3e974619e197a0bcc9dfc759297005e34568
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067148"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="16c58-102">Weryfikowanie danych wejściowych parametrów</span><span class="sxs-lookup"><span data-stu-id="16c58-102">Validating Parameter Input</span></span>

<span data-ttu-id="16c58-103">Program PowerShell można sprawdzić poprawność Argumenty przekazane do parametrów polecenia cmdlet na kilka sposobów.</span><span class="sxs-lookup"><span data-stu-id="16c58-103">PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span>
<span data-ttu-id="16c58-104">PowerShell można sprawdzić poprawność, długość, zakresu i wzorzec znaków argumentu.</span><span class="sxs-lookup"><span data-stu-id="16c58-104">PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span>
<span data-ttu-id="16c58-105">Może on zweryfikować liczbę dostępnych argumentów (liczba).</span><span class="sxs-lookup"><span data-stu-id="16c58-105">It can validate the number of arguments available (the count).</span></span>
<span data-ttu-id="16c58-106">Te reguły sprawdzania poprawności są definiowane przez atrybutów sprawdzania poprawności, które są zadeklarowane za pomocą atrybutu parametru właściwości publicznej klasy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="16c58-106">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="16c58-107">Do sprawdzania poprawności argumentu parametru, w czasie wykonywania programu PowerShell używa informacji dostarczonych przez atrybuty weryfikacji, aby potwierdzić wartość parametru, przed uruchomieniem polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="16c58-107">To validate a parameter argument, the PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span>
<span data-ttu-id="16c58-108">Jeśli parametr wejściowy nie jest prawidłowy, użytkownik otrzymuje komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="16c58-108">If the parameter input is not valid, the user receives an error message.</span></span>
<span data-ttu-id="16c58-109">Każdy parametr weryfikacji definiuje reguły sprawdzania poprawności, który jest wymuszany przez program PowerShell.</span><span class="sxs-lookup"><span data-stu-id="16c58-109">Each validation parameter defines a validation rule that is enforced by PowerShell.</span></span>

<span data-ttu-id="16c58-110">Program PowerShell wymusza reguły sprawdzania poprawności na podstawie następujących atrybutów.</span><span class="sxs-lookup"><span data-stu-id="16c58-110">PowerShell enforces the validation rules based on the following attributes.</span></span>

### <a name="validatecount"></a><span data-ttu-id="16c58-111">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="16c58-111">ValidateCount</span></span>

<span data-ttu-id="16c58-112">Określa minimalną i maksymalną liczbę argumentów, akceptujące parametr.</span><span class="sxs-lookup"><span data-stu-id="16c58-112">Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span>
<span data-ttu-id="16c58-113">Aby uzyskać więcej informacji, zobacz [deklaracji atrybutu ValidateCount](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="16c58-113">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="16c58-114">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="16c58-114">ValidateLength</span></span>

<span data-ttu-id="16c58-115">Określa minimalną i maksymalną liczbę znaków w argumencie parametru.</span><span class="sxs-lookup"><span data-stu-id="16c58-115">Specifies the minimum and maximum number of characters in the parameter argument.</span></span>
<span data-ttu-id="16c58-116">Aby uzyskać więcej informacji, zobacz [deklaracji atrybutu ValidateLength](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="16c58-116">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="16c58-117">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="16c58-117">ValidatePattern</span></span>

<span data-ttu-id="16c58-118">Określa wyrażenie regularne, która weryfikuje argument parametru.</span><span class="sxs-lookup"><span data-stu-id="16c58-118">Specifies a regular expression that validates the parameter argument.</span></span>
<span data-ttu-id="16c58-119">Aby uzyskać więcej informacji, zobacz [deklaracji atrybutu ValidatePattern](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="16c58-119">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="16c58-120">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="16c58-120">ValidateRange</span></span>

<span data-ttu-id="16c58-121">Określa minimalne i maksymalne wartości argumentu parametru.</span><span class="sxs-lookup"><span data-stu-id="16c58-121">Specifies the minimum and maximum values of the parameter argument.</span></span>
<span data-ttu-id="16c58-122">Aby uzyskać więcej informacji, zobacz [deklaracji atrybutu ValidateRange](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="16c58-122">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="16c58-123">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="16c58-123">ValidateSet</span></span>

<span data-ttu-id="16c58-124">Określa prawidłowe wartości dla argumentu parametru.</span><span class="sxs-lookup"><span data-stu-id="16c58-124">Specifies the valid values for the parameter argument.</span></span>
<span data-ttu-id="16c58-125">Aby uzyskać więcej informacji, zobacz [deklaracji atrybutu ValidateSet](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="16c58-125">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="16c58-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16c58-126">See Also</span></span>

[<span data-ttu-id="16c58-127">Sposób sprawdzania poprawności wprowadzania parametrów</span><span class="sxs-lookup"><span data-stu-id="16c58-127">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

[<span data-ttu-id="16c58-128">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="16c58-128">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
