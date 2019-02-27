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
ms.openlocfilehash: f7e5d4fb2f89bd6bc7036fdcff8f38e017d5d0e4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848804"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="9083d-102">Weryfikowanie danych wejściowych parametrów</span><span class="sxs-lookup"><span data-stu-id="9083d-102">Validating Parameter Input</span></span>

<span data-ttu-id="9083d-103">Program Windows PowerShell można sprawdzić poprawność Argumenty przekazane do parametrów polecenia cmdlet na kilka sposobów.</span><span class="sxs-lookup"><span data-stu-id="9083d-103">Windows PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span> <span data-ttu-id="9083d-104">Programu Windows PowerShell można sprawdzić poprawność, długość, zakresu i wzorzec znaków argumentu.</span><span class="sxs-lookup"><span data-stu-id="9083d-104">Windows PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span> <span data-ttu-id="9083d-105">Może on zweryfikować liczbę dostępnych argumentów (liczba).</span><span class="sxs-lookup"><span data-stu-id="9083d-105">It can validate the number of arguments available (the count).</span></span> <span data-ttu-id="9083d-106">Te reguły sprawdzania poprawności są definiowane przez atrybutów sprawdzania poprawności, które są zadeklarowane za pomocą atrybutu parametru właściwości publicznej klasy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9083d-106">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="9083d-107">Do sprawdzania poprawności argumentu parametru, środowisko wykonawcze programu Windows PowerShell korzysta z informacji dostarczonych przez atrybuty weryfikacji Aby potwierdzić wartość parametru, przed uruchomieniem polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9083d-107">To validate a parameter argument, the Windows PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span> <span data-ttu-id="9083d-108">Jeśli parametr wejściowy nie jest prawidłowy, użytkownik otrzymuje komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="9083d-108">If the parameter input is not valid, the user receives an error message.</span></span> <span data-ttu-id="9083d-109">Każdy parametr weryfikacji definiuje reguły sprawdzania poprawności, który jest wymuszany przez środowisko Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9083d-109">Each validation parameter defines a validation rule that is enforced by Windows PowerShell.</span></span>

<span data-ttu-id="9083d-110">Program Windows PowerShell wymusza reguły sprawdzania poprawności na podstawie następujących atrybutów.</span><span class="sxs-lookup"><span data-stu-id="9083d-110">Windows PowerShell enforces the validation rules based on the following attributes.</span></span>

<span data-ttu-id="9083d-111">ValidateCount określa minimalną i maksymalną liczbę argumentów, akceptujące parametr.</span><span class="sxs-lookup"><span data-stu-id="9083d-111">ValidateCount Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span> <span data-ttu-id="9083d-112">Aby uzyskać więcej informacji na temat składni, używane do deklarowania tego atrybutu, zobacz [deklaracji atrybutu ValidateCount](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="9083d-112">For more information about the syntax used to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

<span data-ttu-id="9083d-113">ValidateLength określa minimalną i maksymalną liczbę znaków w argumencie parametru.</span><span class="sxs-lookup"><span data-stu-id="9083d-113">ValidateLength Specifies the minimum and maximum number of characters in the parameter argument.</span></span> <span data-ttu-id="9083d-114">Aby uzyskać więcej informacji na temat składni, używane do deklarowania tego atrybutu, zobacz [deklaracji atrybutu ValidateLength](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="9083d-114">For more information about the syntax used to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

<span data-ttu-id="9083d-115">ValidatePattern określa wyrażenia regularnego weryfikującego argument parametru.</span><span class="sxs-lookup"><span data-stu-id="9083d-115">ValidatePattern Specifies a regular expression that validates the parameter argument.</span></span> <span data-ttu-id="9083d-116">Aby uzyskać więcej informacji na temat składni, używane do deklarowania tego atrybutu, zobacz [deklaracji atrybutu ValidatePattern](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="9083d-116">For more information about the syntax used to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

<span data-ttu-id="9083d-117">ValidateRange określa minimalne i maksymalne wartości argumentu parametru.</span><span class="sxs-lookup"><span data-stu-id="9083d-117">ValidateRange Specifies the minimum and maximum values of the parameter argument.</span></span> <span data-ttu-id="9083d-118">Aby uzyskać więcej informacji na temat składni, używane do deklarowania tego atrybutu, zobacz [deklaracji atrybutu ValidateRange](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="9083d-118">For more information about the syntax used to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

<span data-ttu-id="9083d-119">ValidateSet określa prawidłowe wartości dla argumentu parametru.</span><span class="sxs-lookup"><span data-stu-id="9083d-119">ValidateSet Specifies the valid values for the parameter argument.</span></span> <span data-ttu-id="9083d-120">Aby uzyskać więcej informacji na temat składni, używane do deklarowania tego atrybutu, zobacz [deklaracji atrybutu ValidateSet](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="9083d-120">For more information about the syntax used to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9083d-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9083d-121">See Also</span></span>

[<span data-ttu-id="9083d-122">Sposób sprawdzania poprawności wprowadzania parametrów</span><span class="sxs-lookup"><span data-stu-id="9083d-122">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

[<span data-ttu-id="9083d-123">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9083d-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
