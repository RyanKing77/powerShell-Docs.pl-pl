---
title: Zestawy parametrów polecenia cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: a5822ef1ed3c9efb5957c20255783d515de8957a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847698"
---
# <a name="cmdlet-parameter-sets"></a><span data-ttu-id="93eaa-102">Zestawy parametrów poleceń cmdlet</span><span class="sxs-lookup"><span data-stu-id="93eaa-102">Cmdlet Parameter Sets</span></span>

<span data-ttu-id="93eaa-103">Programu Windows PowerShell używa zestawów parametrów, aby umożliwić pisanie jednego polecenia cmdlet, które może wykonywać różne akcje dla różnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="93eaa-103">Windows PowerShell uses parameter sets to enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span> <span data-ttu-id="93eaa-104">Zestawy parametrów pozwalają do udostępnienia różne parametry dla użytkownika i zwracać różne informacje, w oparciu o parametry określone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="93eaa-104">Parameter sets enable you to expose different parameters to the user and to return different information based on the parameters specified by the user.</span></span>

## <a name="examples-of-parameter-sets"></a><span data-ttu-id="93eaa-105">Przykłady zestawy parametrów</span><span class="sxs-lookup"><span data-stu-id="93eaa-105">Examples of Parameter Sets</span></span>

<span data-ttu-id="93eaa-106">Na przykład `Get-EventLog` (udostępnione przez środowisko Windows PowerShell) polecenie cmdlet zwraca różne informacje w zależności od tego, czy użytkownik określi `List` lub `LogName` parametru.</span><span class="sxs-lookup"><span data-stu-id="93eaa-106">For example, the `Get-EventLog` cmdlet (provided by Windows PowerShell) returns different information depending on whether the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="93eaa-107">Jeśli `List` parametr jest określony, polecenie cmdlet zwraca informacje o plikach dzienników samodzielnie, ale nie dane zdarzenia zawierają.</span><span class="sxs-lookup"><span data-stu-id="93eaa-107">If the `List` parameter is specified, the cmdlet returns information about the log files themselves but not the event information they contain.</span></span> <span data-ttu-id="93eaa-108">Jeśli `LogName` parametr jest określony, polecenie cmdlet zwraca informacje o zdarzeniach w określonym dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="93eaa-108">If the `LogName` parameter is specified, the cmdlet returns information about the events in a specific event log.</span></span> <span data-ttu-id="93eaa-109">`List` i `LogName` parametry zidentyfikować dwa zestawy oddzielny parametr.</span><span class="sxs-lookup"><span data-stu-id="93eaa-109">The `List` and `LogName` parameters identify two separate parameter sets.</span></span>

## <a name="unique-parameter"></a><span data-ttu-id="93eaa-110">Unikatowy parametr</span><span class="sxs-lookup"><span data-stu-id="93eaa-110">Unique Parameter</span></span>

<span data-ttu-id="93eaa-111">Każdy zestaw parametrów musi mieć unikatowy parametr, który w czasie wykonywania programu Windows PowerShell można użyć do udostępnienia zestaw odpowiednich parametrów.</span><span class="sxs-lookup"><span data-stu-id="93eaa-111">Each parameter set must have a unique parameter that the Windows PowerShell runtime can use to expose the appropriate parameter set.</span></span> <span data-ttu-id="93eaa-112">Jeśli to możliwe unikatowy parametr powinien być to parametr obowiązkowy.</span><span class="sxs-lookup"><span data-stu-id="93eaa-112">If possible, the unique parameter should be a mandatory parameter.</span></span> <span data-ttu-id="93eaa-113">Jeśli parametr jest obowiązkowy, użytkownik jest zmuszony do określenia parametru, a środowisko wykonawcze programu Windows PowerShell można używać tego parametru do identyfikacji parametr, który został skonfigurowany do używania.</span><span class="sxs-lookup"><span data-stu-id="93eaa-113">When a parameter is mandatory, the user is forced to specify the parameter, and the Windows PowerShell runtime can use that parameter to identify the parameter set to use.</span></span> <span data-ttu-id="93eaa-114">Unikatowy parametr nie może być wymagane, jeśli Twojego polecenia cmdlet jest przeznaczony do uruchamiania bez określenia wszystkich parametrów.</span><span class="sxs-lookup"><span data-stu-id="93eaa-114">The unique parameter cannot be mandatory if your cmdlet is designed to be run without specifying any parameters.</span></span>

## <a name="multiple-parameter-sets"></a><span data-ttu-id="93eaa-115">Wiele zestawów parametrów</span><span class="sxs-lookup"><span data-stu-id="93eaa-115">Multiple Parameter Sets</span></span>

<span data-ttu-id="93eaa-116">Na poniższej ilustracji w kolumnie po lewej stronie jest wyświetlana trzech zestawów prawidłowego parametru.</span><span class="sxs-lookup"><span data-stu-id="93eaa-116">In the following illustration, the left column shows three valid parameter sets.</span></span> <span data-ttu-id="93eaa-117">Parametr A jest unikatowy dla pierwszego zestawu parametrów, parametr B jest unikatowy dla drugiego zestawu parametrów i parametr C jest unikatowy dla trzeciego zestaw parametrów.</span><span class="sxs-lookup"><span data-stu-id="93eaa-117">Parameter A is unique to the first parameter set, parameter B is unique to the second parameter set, and parameter C is unique to the third parameter set.</span></span> <span data-ttu-id="93eaa-118">Jednak w prawej kolumnie zestawów parametrów ma unikatowy parametr.</span><span class="sxs-lookup"><span data-stu-id="93eaa-118">However, in the right column, the parameter sets do not have a unique parameter.</span></span>

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a><span data-ttu-id="93eaa-120">Wymagania dotyczące zestawu parametrów</span><span class="sxs-lookup"><span data-stu-id="93eaa-120">Parameter Set Requirements</span></span>

<span data-ttu-id="93eaa-121">Poniższe wymagania dotyczą wszystkich zestawów parametrów.</span><span class="sxs-lookup"><span data-stu-id="93eaa-121">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="93eaa-122">Każdy zestaw parametrów musi mieć co najmniej jeden parametr unikatowy.</span><span class="sxs-lookup"><span data-stu-id="93eaa-122">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="93eaa-123">Jeśli to możliwe należy ten parametr to parametr obowiązkowy.</span><span class="sxs-lookup"><span data-stu-id="93eaa-123">If possible, make this parameter a mandatory parameter.</span></span>

- <span data-ttu-id="93eaa-124">Zestaw parametrów, który zawiera wiele parametry pozycyjne, należy zdefiniować pozycji unikatowy dla każdego parametru.</span><span class="sxs-lookup"><span data-stu-id="93eaa-124">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="93eaa-125">Nie dwa parametry pozycyjne, można określić taką samą pozycję.</span><span class="sxs-lookup"><span data-stu-id="93eaa-125">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="93eaa-126">Można zadeklarować tylko jeden parametr w zestawie `ValueFromPipeline` — słowo kluczowe z wartością `true`.</span><span class="sxs-lookup"><span data-stu-id="93eaa-126">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span> <span data-ttu-id="93eaa-127">Można zdefiniować wiele parametrów `ValueFromPipelineByPropertyName` — słowo kluczowe z wartością `true`.</span><span class="sxs-lookup"><span data-stu-id="93eaa-127">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="93eaa-128">Jeśli nie ustawiono parametru jest określona dla parametru, parametr należy do wszystkich zestawów parametrów.</span><span class="sxs-lookup"><span data-stu-id="93eaa-128">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="93eaa-129">Domyślne zestawy parametrów</span><span class="sxs-lookup"><span data-stu-id="93eaa-129">Default Parameter Sets</span></span>

<span data-ttu-id="93eaa-130">Jeśli zdefiniowano wiele zestawów parametrów, możesz użyć `DefaultParameterSetName` słowa kluczowego atrybutu polecenia Cmdlet, aby określić domyślny zestaw parametrów.</span><span class="sxs-lookup"><span data-stu-id="93eaa-130">When multiple parameter sets are defined, you can use the `DefaultParameterSetName` keyword of the Cmdlet attribute to specify the default parameter set.</span></span> <span data-ttu-id="93eaa-131">Korzysta z domyślnego parametru, jeśli nie można określić, parametr, który został skonfigurowany do używania na podstawie informacji dostępnych za pomocą polecenia programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="93eaa-131">Windows PowerShell uses the default parameter set if it cannot determine the parameter set to use based on the information provided by the command.</span></span> <span data-ttu-id="93eaa-132">Aby uzyskać więcej informacji o atrybucie polecenia Cmdlet, zobacz [deklaracji atrybutu polecenia Cmdlet](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="93eaa-132">For more information about the Cmdlet attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="93eaa-133">Deklarowanie zestawy parametrów</span><span class="sxs-lookup"><span data-stu-id="93eaa-133">Declaring Parameter Sets</span></span>

<span data-ttu-id="93eaa-134">Aby utworzyć zestaw parametrów, należy określić `ParameterSetName` — słowo kluczowe, kiedy Deklarujesz atrybut Parameter dla każdego parametru w zestaw parametrów.</span><span class="sxs-lookup"><span data-stu-id="93eaa-134">To create a parameter set, you must specify the `ParameterSetName` keyword when you declare the Parameter attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="93eaa-135">Dla parametrów, które należą do wiele zestawów parametrów należy dodać atrybut parametru dla każdego zestawu parametrów.</span><span class="sxs-lookup"><span data-stu-id="93eaa-135">For parameters that belong to multiple parameter sets, add a Parameter attribute for each parameter set.</span></span> <span data-ttu-id="93eaa-136">Dzięki temu można zdefiniować parametr w różny sposób dla każdego zestawu parametrów.</span><span class="sxs-lookup"><span data-stu-id="93eaa-136">This enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="93eaa-137">Na przykład można zdefiniować parametr jako obowiązkowe w jednym zestawie i opcjonalnych w innym.</span><span class="sxs-lookup"><span data-stu-id="93eaa-137">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="93eaa-138">Jednak każdy zestaw parametrów musi zawierać jeden parametr unikatowy.</span><span class="sxs-lookup"><span data-stu-id="93eaa-138">However, each parameter set must contain one unique parameter.</span></span>

<span data-ttu-id="93eaa-139">W poniższym przykładzie `UserName` parametr jest unikatowy parametr Test01 zestaw parametrów, a `ComputerName` parametr jest unikatowy parametr Test02 zestaw parametrów.</span><span class="sxs-lookup"><span data-stu-id="93eaa-139">In the following example, the `UserName` parameter is the unique parameter of the Test01 parameter set, and the `ComputerName` parameter is the unique parameter of the Test02 parameter set.</span></span> <span data-ttu-id="93eaa-140">`SharedParam` Parametr należy do obu zestawów i jest wymagane dla parametru Test01 ustawić, ale opcjonalny w przypadku Test02 zestaw parametrów.</span><span class="sxs-lookup"><span data-stu-id="93eaa-140">The `SharedParam` parameter belongs to both sets and is mandatory for the Test01 parameter set but optional for the Test02 parameter set.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test02")]
public string ComputerName
{
  get { return computerName; }
  set { computerName = value; }
}
private string computerName;

[Parameter(Mandatory= true, ParameterSetName = "Test01")]
[Parameter(ParameterSetName = "Test02")]
public string SharedParam
{
    get { return sharedParam; }
    set { sharedParam = value; }
}
private string sharedParam;    [Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```