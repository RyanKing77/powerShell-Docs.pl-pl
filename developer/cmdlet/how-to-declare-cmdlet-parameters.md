---
title: Sposób deklarowania parametry polecenia Cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c0509cc-5a50-49ad-a74f-5527023d0270
caps.latest.revision: 10
ms.openlocfilehash: d6613889ebd2ba139ce0b3de1b8d24e4aec37d2a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850589"
---
# <a name="how-to-declare-cmdlet-parameters"></a><span data-ttu-id="1ca87-102">Jak zadeklarować parametry polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="1ca87-102">How to Declare Cmdlet Parameters</span></span>

<span data-ttu-id="1ca87-103">Te przykłady przedstawiają sposób deklaruje nazwanych pozycyjne, wymagane, opcjonalne i parametry przełączników.</span><span class="sxs-lookup"><span data-stu-id="1ca87-103">These examples show how to declare named, positional, required, optional, and switch parameters.</span></span> <span data-ttu-id="1ca87-104">Te przykłady przedstawiają także sposób definiowania aliasów parametrów.</span><span class="sxs-lookup"><span data-stu-id="1ca87-104">These examples also show how to define a parameter alias.</span></span>

## <a name="how-to-declare-a-named-parameter"></a><span data-ttu-id="1ca87-105">Sposób deklarowania nazwany parametr</span><span class="sxs-lookup"><span data-stu-id="1ca87-105">How to Declare a Named Parameter</span></span>

- <span data-ttu-id="1ca87-106">Zdefiniuj właściwość publiczną, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1ca87-106">Define a public property as shown in the following code.</span></span> <span data-ttu-id="1ca87-107">Po dodaniu atrybut Parameter, Pomiń `Position` — słowo kluczowe z atrybutu.</span><span class="sxs-lookup"><span data-stu-id="1ca87-107">When you add the Parameter attribute, omit the `Position` keyword from the attribute.</span></span>

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="1ca87-108">Aby uzyskać więcej informacji na temat atrybut Parameter, zobacz [deklaracji atrybutu parametru](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="1ca87-108">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-positional-parameter"></a><span data-ttu-id="1ca87-109">Jak zadeklarować parametr pozycyjne</span><span class="sxs-lookup"><span data-stu-id="1ca87-109">How to Declare a Positional Parameter</span></span>

- <span data-ttu-id="1ca87-110">Zdefiniuj właściwość publiczną, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1ca87-110">Define a public property as shown in the following code.</span></span> <span data-ttu-id="1ca87-111">Po dodaniu atrybut Parameter, ustaw `Position` słowa kluczowego pozycja argumentu.</span><span class="sxs-lookup"><span data-stu-id="1ca87-111">When you add the Parameter attribute, set the `Position` keyword to the argument position.</span></span> <span data-ttu-id="1ca87-112">Wartość 0 wskazuje pierwszą pozycję.</span><span class="sxs-lookup"><span data-stu-id="1ca87-112">A value of 0 indicates the first position.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="1ca87-113">Aby uzyskać więcej informacji na temat atrybut Parameter, zobacz [deklaracji atrybutu parametru](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="1ca87-113">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-mandatory-parameter"></a><span data-ttu-id="1ca87-114">Sposób deklarowania obowiązkowy parametr</span><span class="sxs-lookup"><span data-stu-id="1ca87-114">How to Declare a Mandatory Parameter</span></span>

- <span data-ttu-id="1ca87-115">Zdefiniuj właściwość publiczną, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1ca87-115">Define a public property as shown in the following code.</span></span> <span data-ttu-id="1ca87-116">Po dodaniu atrybut Parameter, ustaw `Mandatory` słowa kluczowego `true`.</span><span class="sxs-lookup"><span data-stu-id="1ca87-116">When you add the Parameter attribute, set the `Mandatory` keyword to `true`.</span></span>

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="1ca87-117">Aby uzyskać więcej informacji na temat atrybut Parameter, zobacz [deklaracji atrybutu parametru](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="1ca87-117">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-an-optional-parameter"></a><span data-ttu-id="1ca87-118">Jak zadeklarować parametr opcjonalny</span><span class="sxs-lookup"><span data-stu-id="1ca87-118">How to Declare an Optional Parameter</span></span>

- <span data-ttu-id="1ca87-119">Zdefiniuj właściwość publiczną, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1ca87-119">Define a public property as shown in the following code.</span></span> <span data-ttu-id="1ca87-120">Po dodaniu atrybut Parameter, Pomiń `Mandatory` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="1ca87-120">When you add the Parameter attribute, omit the `Mandatory` keyword.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a><span data-ttu-id="1ca87-121">Jak zadeklarować parametr przełącznika</span><span class="sxs-lookup"><span data-stu-id="1ca87-121">How to Declare a Switch Parameter</span></span>

- <span data-ttu-id="1ca87-122">Zdefiniuj właściwość publiczną typu [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter), a następnie deklarować atrybutu parametru.</span><span class="sxs-lookup"><span data-stu-id="1ca87-122">Define a public property as type [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter), and then declare the Parameter attribute.</span></span>

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

<span data-ttu-id="1ca87-123">Aby uzyskać więcej informacji na temat atrybut Parameter, zobacz [deklaracji atrybutu parametru](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="1ca87-123">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-parameter-with-aliases"></a><span data-ttu-id="1ca87-124">Sposób deklarowania parametrem aliasów</span><span class="sxs-lookup"><span data-stu-id="1ca87-124">How to Declare a Parameter with Aliases</span></span>

- <span data-ttu-id="1ca87-125">Zdefiniuj właściwość publiczną, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1ca87-125">Define a public property as shown in the following code.</span></span> <span data-ttu-id="1ca87-126">Dodaj atrybut Alias, który zawiera listę aliasów dla parametru.</span><span class="sxs-lookup"><span data-stu-id="1ca87-126">Add an Alias attribute that lists the aliases for the parameter.</span></span> <span data-ttu-id="1ca87-127">W tym przykładzie trzy aliasy są zdefiniowane dla tego samego parametru.</span><span class="sxs-lookup"><span data-stu-id="1ca87-127">In this example, three aliases are defined for the same parameter.</span></span> <span data-ttu-id="1ca87-128">Pierwszy aliasu zawiera skrót.</span><span class="sxs-lookup"><span data-stu-id="1ca87-128">The first alias provides a shortcut.</span></span> <span data-ttu-id="1ca87-129">Drugi i trzeci aliasy zawierają nazwy, którego używasz dla różnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="1ca87-129">The second and third aliases provide names you can use for different scenarios.</span></span>

    ```csharp
    [Alias("UN","Writer","Editor")]
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="1ca87-130">Aby uzyskać więcej informacji o atrybucie Alias, zobacz [deklaracji atrybutu Alias](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="1ca87-130">For more information about the Alias attribute, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1ca87-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ca87-131">See Also</span></span>

[<span data-ttu-id="1ca87-132">System.Management.Automation.Switchparameter</span><span class="sxs-lookup"><span data-stu-id="1ca87-132">System.Management.Automation.Switchparameter</span></span>](/dotnet/api/System.Management.Automation.SwitchParameter)

[<span data-ttu-id="1ca87-133">Deklaracji atrybutu parametru</span><span class="sxs-lookup"><span data-stu-id="1ca87-133">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="1ca87-134">Deklaracji atrybutu aliasu</span><span class="sxs-lookup"><span data-stu-id="1ca87-134">Alias Attribute Declaration</span></span>](./alias-attribute-declaration.md)

[<span data-ttu-id="1ca87-135">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1ca87-135">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
