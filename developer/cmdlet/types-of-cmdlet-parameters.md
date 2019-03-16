---
title: Typy parametrów polecenia Cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: f5781c0c03aca41d01a44598a9a8c00d6d21d2fd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059579"
---
# <a name="types-of-cmdlet-parameters"></a><span data-ttu-id="d85f0-102">Typy parametrów poleceń cmdlet</span><span class="sxs-lookup"><span data-stu-id="d85f0-102">Types of Cmdlet Parameters</span></span>

<span data-ttu-id="d85f0-103">W tym temacie opisano różne typy parametrów, które można zadeklarować w poleceniach cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d85f0-103">This topic describes the different types of parameters that you can declare in cmdlets.</span></span> <span data-ttu-id="d85f0-104">Parametry polecenia cmdlet można być pozycyjne, nazwanych, wymagane, opcjonalne lub parametry przełączników.</span><span class="sxs-lookup"><span data-stu-id="d85f0-104">Cmdlet parameters can be positional, named, required, optional, or switch parameters.</span></span>

## <a name="positional-and-named-parameters"></a><span data-ttu-id="d85f0-105">Parametry pozycyjne i nazwane</span><span class="sxs-lookup"><span data-stu-id="d85f0-105">Positional and Named Parameters</span></span>

<span data-ttu-id="d85f0-106">Wszystkie parametry polecenia cmdlet są parametrów nazwanych i pozycyjnych.</span><span class="sxs-lookup"><span data-stu-id="d85f0-106">All cmdlet parameters are either named or positional parameters.</span></span> <span data-ttu-id="d85f0-107">Parametr o nazwie wymaga, wpisz nazwę parametru i argumentów podczas wywoływania polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d85f0-107">A named parameter requires that you type the parameter name and argument when calling the cmdlet.</span></span> <span data-ttu-id="d85f0-108">Parametr pozycyjne wymaga jedynie, wpisz argumenty w kolejności względnej.</span><span class="sxs-lookup"><span data-stu-id="d85f0-108">A positional parameter requires only that you type the arguments in relative order.</span></span> <span data-ttu-id="d85f0-109">System następnie mapuje pierwszy parametr pozycyjne pierwszy argument bez nazwy.</span><span class="sxs-lookup"><span data-stu-id="d85f0-109">The system then maps the first unnamed argument to the first positional parameter.</span></span> <span data-ttu-id="d85f0-110">System mapuje drugi nienazwany argument do drugiego parametru nienazwanego i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="d85f0-110">The system maps the second unnamed argument to the second unnamed parameter, and so on.</span></span> <span data-ttu-id="d85f0-111">Domyślnie wszystkie parametry polecenia cmdlet są nazwanych parametrów.</span><span class="sxs-lookup"><span data-stu-id="d85f0-111">By default, all cmdlet parameters are named parameters.</span></span>

<span data-ttu-id="d85f0-112">Aby zdefiniować nazwany parametr, Pomiń `Position` — słowo kluczowe w **parametru** atrybutu deklaracji, jak pokazano w poniższej deklaracji parametru.</span><span class="sxs-lookup"><span data-stu-id="d85f0-112">To define a named parameter, omit the `Position` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="d85f0-113">Aby zdefiniować parametr pozycyjne, Dodaj `Position` — słowo kluczowe w parametrze deklaracji atrybutu, a następnie określić położenie.</span><span class="sxs-lookup"><span data-stu-id="d85f0-113">To define a positional parameter, add the `Position` keyword in the Parameter attribute declaration, and then specify a position.</span></span> <span data-ttu-id="d85f0-114">W poniższym przykładzie `UserName` parametru jest zadeklarowany jako parametr pozycyjne od pozycji 0.</span><span class="sxs-lookup"><span data-stu-id="d85f0-114">In the following sample, the `UserName` parameter is declared as a positional parameter with position 0.</span></span> <span data-ttu-id="d85f0-115">Oznacza to, że pierwszy argument wywołania będą automatycznie powiązane tego parametru.</span><span class="sxs-lookup"><span data-stu-id="d85f0-115">This means that the first argument of the call will be automatically bound to this parameter.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

> [!NOTE]
> <span data-ttu-id="d85f0-116">Polecenia cmdlet dobrej projekcie są zalecane, parametry używane przez większość może być zadeklarowana jako parametry pozycyjne, tak, aby użytkownik nie musiał po uruchomieniu polecenia cmdlet, wprowadź nazwę parametru.</span><span class="sxs-lookup"><span data-stu-id="d85f0-116">Good cmdlet design recommends that the most-used parameters be declared as positional parameters so that the user does not have to enter the parameter name when the cmdlet is run.</span></span>

<span data-ttu-id="d85f0-117">Parametry pozycyjne i nazwane akceptuje żadnych argumentów jednego lub wielu argumentów rozdzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="d85f0-117">Positional and named parameters accept single arguments or multiple arguments separated by commas.</span></span> <span data-ttu-id="d85f0-118">Wiele argumentów są dozwolone tylko wtedy, gdy parametr akceptuje kolekcja przykład tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="d85f0-118">Multiple arguments are allowed only if the parameter accepts a collection such as an array of strings.</span></span> <span data-ttu-id="d85f0-119">Może mieszać parametry pozycyjne i nazwane, w tym samym poleceniu cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d85f0-119">You may mix positional and named parameters in the same cmdlet.</span></span> <span data-ttu-id="d85f0-120">W takim przypadku system pobiera argumenty nazwane najpierw, a następnie próbuje zamapować pozostałe nienazwane argumenty pozycyjne parametrów.</span><span class="sxs-lookup"><span data-stu-id="d85f0-120">In this case, the system retrieves the named arguments first, and then attempts to map the remaining unnamed arguments to the positional parameters.</span></span>

<span data-ttu-id="d85f0-121">W następujących poleceniach pokazano różne sposoby, w którym można określić pojedynczych i wielu argumenty dla parametrów `Get-Command` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d85f0-121">The following commands show the different ways in which you can specify single and multiple arguments for the parameters of the `Get-Command` cmdlet.</span></span> <span data-ttu-id="d85f0-122">Należy zauważyć, że w ostatnich dwóch próbek **— nazwa** nie musi być określona, ponieważ `Name` parametr jest zdefiniowany jako parametr pozycyjne.</span><span class="sxs-lookup"><span data-stu-id="d85f0-122">Notice that in the last two samples, **-name** does not need to be specified because the `Name` parameter is defined as a positional parameter.</span></span>

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a><span data-ttu-id="d85f0-123">Obowiązkowych i opcjonalnych parametrów</span><span class="sxs-lookup"><span data-stu-id="d85f0-123">Mandatory and Optional Parameters</span></span>

<span data-ttu-id="d85f0-124">Parametry polecenia cmdlet można także zdefiniować jako wymagane lub opcjonalne parametry.</span><span class="sxs-lookup"><span data-stu-id="d85f0-124">You can also define cmdlet parameters as mandatory or optional parameters.</span></span> <span data-ttu-id="d85f0-125">(To parametr obowiązkowy przed należy określić w czasie wykonywania programu Windows PowerShell wywołuje polecenie cmdlet.)  Domyślnie parametry są definiowane jako opcjonalną.</span><span class="sxs-lookup"><span data-stu-id="d85f0-125">(A mandatory parameter must be specified before the Windows PowerShell runtime invokes the cmdlet.)  By default, parameters are defined as optional.</span></span>

<span data-ttu-id="d85f0-126">Aby zdefiniować to parametr obowiązkowy, należy dodać `Mandatory` — słowo kluczowe w parametrze atrybutu deklaracji i ustaw ją na `true`, jak pokazano w poniższej deklaracji parametru.</span><span class="sxs-lookup"><span data-stu-id="d85f0-126">To define a mandatory parameter, add the `Mandatory` keyword in the Parameter attribute declaration, and set it to `true`, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="d85f0-127">Aby zdefiniować parametr opcjonalny, Pomiń `Mandatory` — słowo kluczowe w **parametru** atrybutu deklaracji, jak pokazano w poniższej deklaracji parametru.</span><span class="sxs-lookup"><span data-stu-id="d85f0-127">To define an optional parameter, omit the `Mandatory` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a><span data-ttu-id="d85f0-128">Parametry przełączników</span><span class="sxs-lookup"><span data-stu-id="d85f0-128">Switch Parameters</span></span>

<span data-ttu-id="d85f0-129">Program Windows PowerShell udostępnia [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) typ, który pozwala na zdefiniowanie parametru którego wartość jest automatycznie ustawiana na `false` Jeśli parametr nie zostanie określony, gdy polecenie cmdlet jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="d85f0-129">Windows PowerShell provides a [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type that allows you to define a parameter whose value is automatically set to `false` if the parameter is not specified when the cmdlet is called.</span></span> <span data-ttu-id="d85f0-130">Zawsze, gdy jest to możliwe, należy użyć parametrów przełącznika zamiast logiczna parametrów.</span><span class="sxs-lookup"><span data-stu-id="d85f0-130">Whenever possible, use switch parameters in place of Boolean parameters.</span></span>

<span data-ttu-id="d85f0-131">Należy wziąć pod uwagę poniższego przykładu.</span><span class="sxs-lookup"><span data-stu-id="d85f0-131">Consider the following sample.</span></span> <span data-ttu-id="d85f0-132">Domyślnie kilka poleceń cmdlet programu Windows PowerShell nie przekazuj obiekt danych wyjściowych w dół do potoku.</span><span class="sxs-lookup"><span data-stu-id="d85f0-132">By default, several Windows PowerShell cmdlets do not pass an output object down the pipeline.</span></span> <span data-ttu-id="d85f0-133">Jednak te polecenia cmdlet mają `PassThru` Przełącz parametr, który zastępuje domyślne zachowanie.</span><span class="sxs-lookup"><span data-stu-id="d85f0-133">However, these cmdlets have a `PassThru` switch parameter that overrides the default behavior.</span></span> <span data-ttu-id="d85f0-134">Jeśli `PassThru` parametr jest określony, wywołanego tych poleceń cmdlet, polecenie cmdlet zwraca obiekt danych wyjściowych do potoku.</span><span class="sxs-lookup"><span data-stu-id="d85f0-134">If the `PassThru` parameter is specified when these cmdlets are called, the cmdlet returns an output object to the pipeline.</span></span>

<span data-ttu-id="d85f0-135">Jeśli potrzebujesz parametr ma wartość domyślną `true` gdy parametr nie jest określony w wywołaniu, należy wziąć pod uwagę wycofywanie sense parametru.</span><span class="sxs-lookup"><span data-stu-id="d85f0-135">If you need the parameter to have a default value of `true` when the parameter is not specified in the call, consider reversing the sense of the parameter.</span></span> <span data-ttu-id="d85f0-136">Dla przykładu, zamiast ustawiać atrybutu parametru na wartość logiczną `true`, zadeklarować właściwości jako [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) typu, a następnie ustaw wartość domyślna parametru `false`.</span><span class="sxs-lookup"><span data-stu-id="d85f0-136">For sample, instead of setting the parameter attribute to a Boolean value of `true`, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, and then set the default value of the parameter to `false`.</span></span>

<span data-ttu-id="d85f0-137">Aby zdefiniować parametr przełącznika, należy zadeklarować właściwości jako [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) typ, jak pokazano w następującym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d85f0-137">To define a switch parameter, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, as shown in the following sample.</span></span>

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

<span data-ttu-id="d85f0-138">Aby polecenie cmdlet działa w parametrze, jeśli nie zostanie określony, użyj następującej struktury w ramach jednej metody przetwarzania danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="d85f0-138">To make the cmdlet act on the parameter when it is specified, use the following structure within one of the input processing methods.</span></span>

```csharp
protected override void ProcessRecord()
{
  WriteObject("Switch parameter test: " + userName + ".");
  if(goodbye)
  {
    WriteObject(" Goodbye!");
  }
} // End ProcessRecord
```

## <a name="see-also"></a><span data-ttu-id="d85f0-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d85f0-139">See Also</span></span>

[<span data-ttu-id="d85f0-140">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d85f0-140">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
