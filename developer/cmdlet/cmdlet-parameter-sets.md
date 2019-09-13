---
title: Zestawy parametrów poleceń cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: d8c00c7ffd369a32af151836785a2c5f47b05a68
ms.sourcegitcommit: 889b93d170aeb3d444288e7ccf67e62ce822cb7c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70936200"
---
# <a name="cmdlet-parameter-sets"></a><span data-ttu-id="57bb1-102">Zestawy parametrów poleceń cmdlet</span><span class="sxs-lookup"><span data-stu-id="57bb1-102">Cmdlet parameter sets</span></span>

<span data-ttu-id="57bb1-103">Program PowerShell używa zestawów parametrów, aby umożliwić pisanie pojedynczego polecenia cmdlet, które może wykonywać różne akcje dla różnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="57bb1-103">PowerShell uses parameter sets to enable you to write a single cmdlet that can do different actions for different scenarios.</span></span> <span data-ttu-id="57bb1-104">Zestawy parametrów umożliwiają udostępnienie użytkownikowi różnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="57bb1-104">Parameter sets enable you to expose different parameters to the user.</span></span> <span data-ttu-id="57bb1-105">I, aby zwrócić różne informacje na podstawie parametrów określonych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="57bb1-105">And, to return different information based on the parameters specified by the user.</span></span>

## <a name="examples-of-parameter-sets"></a><span data-ttu-id="57bb1-106">Przykłady zestawów parametrów</span><span class="sxs-lookup"><span data-stu-id="57bb1-106">Examples of parameter sets</span></span>

<span data-ttu-id="57bb1-107">Na przykład polecenie cmdlet programu `Get-EventLog` PowerShell zwraca różne informacje w zależności od tego, czy użytkownik określa **listę** lub parametr **Nazwa** .</span><span class="sxs-lookup"><span data-stu-id="57bb1-107">For example, the PowerShell `Get-EventLog` cmdlet returns different information depending on whether the user specifies the **List** or **LogName** parameter.</span></span> <span data-ttu-id="57bb1-108">Jeśli parametr **listy** jest określony, polecenie cmdlet zwraca informacje o plikach dziennika, ale nie informacje o zdarzeniach, które zawierają.</span><span class="sxs-lookup"><span data-stu-id="57bb1-108">If the **List** parameter is specified, the cmdlet returns information about the log files themselves but not the event information they contain.</span></span> <span data-ttu-id="57bb1-109">Jeśli parametr **Nazwa** jest określony, polecenie cmdlet zwraca informacje o zdarzeniach w określonym dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="57bb1-109">If the **LogName** parameter is specified, the cmdlet returns information about the events in a specific event log.</span></span> <span data-ttu-id="57bb1-110">Parametry **list** i **Nazwa** identyfikują dwa oddzielne zestawy parametrów.</span><span class="sxs-lookup"><span data-stu-id="57bb1-110">The **List** and **LogName** parameters identify two separate parameter sets.</span></span>

## <a name="unique-parameter"></a><span data-ttu-id="57bb1-111">Unikatowy parametr</span><span class="sxs-lookup"><span data-stu-id="57bb1-111">Unique parameter</span></span>

<span data-ttu-id="57bb1-112">Każdy zestaw parametrów musi mieć unikatowy parametr, którego środowisko uruchomieniowe programu PowerShell używa do uwidocznienia odpowiedniego zestawu parametrów.</span><span class="sxs-lookup"><span data-stu-id="57bb1-112">Each parameter set must have a unique parameter that the PowerShell runtime uses to expose the appropriate parameter set.</span></span> <span data-ttu-id="57bb1-113">Jeśli to możliwe, unikatowy parametr powinien być obowiązkowym parametrem.</span><span class="sxs-lookup"><span data-stu-id="57bb1-113">If possible, the unique parameter should be a mandatory parameter.</span></span> <span data-ttu-id="57bb1-114">Gdy parametr jest obowiązkowy, użytkownik musi określić parametr, a środowisko uruchomieniowe programu PowerShell używa tego parametru do identyfikacji zestawu parametrów.</span><span class="sxs-lookup"><span data-stu-id="57bb1-114">When a parameter is mandatory, the user must specify the parameter, and the PowerShell runtime uses that parameter to identify the parameter set.</span></span> <span data-ttu-id="57bb1-115">Nie można określić unikatowego parametru, jeśli polecenie cmdlet zostało zaprojektowane do uruchomienia bez określenia żadnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="57bb1-115">The unique parameter can't be mandatory if your cmdlet is designed to run without specifying any parameters.</span></span>

## <a name="multiple-parameter-sets"></a><span data-ttu-id="57bb1-116">Wiele zestawów parametrów</span><span class="sxs-lookup"><span data-stu-id="57bb1-116">Multiple parameter sets</span></span>

<span data-ttu-id="57bb1-117">Na poniższej ilustracji w lewej kolumnie są wyświetlane trzy prawidłowe zestawy parametrów.</span><span class="sxs-lookup"><span data-stu-id="57bb1-117">In the following illustration, the left column shows three valid parameter sets.</span></span> <span data-ttu-id="57bb1-118">**Parametr A** jest unikatowy dla pierwszego zestawu parametrów **parametr B** jest unikatowy dla drugiego zestawu parametrów, a **parametr C** jest unikatowy dla trzeciego zestawu parametrów.</span><span class="sxs-lookup"><span data-stu-id="57bb1-118">**Parameter A** is unique to the first parameter set, **parameter B** is unique to the second parameter set, and **parameter C** is unique to the third parameter set.</span></span> <span data-ttu-id="57bb1-119">W prawej kolumnie zestawy parametrów nie mają unikatowego parametru.</span><span class="sxs-lookup"><span data-stu-id="57bb1-119">In the right column, the parameter sets don't have a unique parameter.</span></span>

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a><span data-ttu-id="57bb1-121">Wymagania dotyczące zestawu parametrów</span><span class="sxs-lookup"><span data-stu-id="57bb1-121">Parameter set requirements</span></span>

<span data-ttu-id="57bb1-122">Poniższe wymagania dotyczą wszystkich zestawów parametrów.</span><span class="sxs-lookup"><span data-stu-id="57bb1-122">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="57bb1-123">Każdy zestaw parametrów musi mieć co najmniej jeden unikatowy parametr.</span><span class="sxs-lookup"><span data-stu-id="57bb1-123">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="57bb1-124">Jeśli to możliwe, ustaw ten parametr jako obowiązkowy.</span><span class="sxs-lookup"><span data-stu-id="57bb1-124">If possible, make this parameter a mandatory parameter.</span></span>

- <span data-ttu-id="57bb1-125">Zestaw parametrów, który zawiera wiele parametrów pozycyjnych, musi definiować unikatowe położenia dla każdego parametru.</span><span class="sxs-lookup"><span data-stu-id="57bb1-125">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="57bb1-126">Dwa parametry pozycyjne nie mogą określać tego samego położenia.</span><span class="sxs-lookup"><span data-stu-id="57bb1-126">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="57bb1-127">Tylko jeden parametr w zestawie może deklarować `ValueFromPipeline` słowo kluczowe z `true`wartością.</span><span class="sxs-lookup"><span data-stu-id="57bb1-127">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span>
  <span data-ttu-id="57bb1-128">Wiele parametrów może definiować `ValueFromPipelineByPropertyName` słowo kluczowe o `true`wartości.</span><span class="sxs-lookup"><span data-stu-id="57bb1-128">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="57bb1-129">Jeśli nie określono zestawu parametrów dla parametru, parametr należy do wszystkich zestawów parametrów.</span><span class="sxs-lookup"><span data-stu-id="57bb1-129">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

> [!NOTE]
> <span data-ttu-id="57bb1-130">W przypadku polecenia cmdlet lub funkcji istnieje limit 32 zestawów parametrów.</span><span class="sxs-lookup"><span data-stu-id="57bb1-130">For a cmdlet or function, there is a limit of 32 parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="57bb1-131">Domyślne zestawy parametrów</span><span class="sxs-lookup"><span data-stu-id="57bb1-131">Default parameter sets</span></span>

<span data-ttu-id="57bb1-132">Jeśli zdefiniowano wiele zestawów parametrów, można użyć `DefaultParameterSetName` słowa kluczowego **polecenia cmdlet** w celu określenia domyślnego zestawu parametrów.</span><span class="sxs-lookup"><span data-stu-id="57bb1-132">When multiple parameter sets are defined, you can use the `DefaultParameterSetName` keyword of the **Cmdlet** attribute to specify the default parameter set.</span></span> <span data-ttu-id="57bb1-133">Program PowerShell używa domyślnego parametru ustawionego, jeśli nie może ustalić parametru ustawionego do użycia na podstawie informacji podanych przez polecenie.</span><span class="sxs-lookup"><span data-stu-id="57bb1-133">PowerShell uses the default parameter set if it can't determine the parameter set to use based on the information provided by the command.</span></span> <span data-ttu-id="57bb1-134">Aby uzyskać więcej informacji o atrybucie **polecenia cmdlet** , zobacz [polecenie cmdlet Attribute deklaracji](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="57bb1-134">For more information about the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="57bb1-135">Deklarowanie zestawów parametrów</span><span class="sxs-lookup"><span data-stu-id="57bb1-135">Declaring parameter sets</span></span>

<span data-ttu-id="57bb1-136">Aby utworzyć zestaw parametrów, należy określić `ParameterSetName` słowo kluczowe przy deklarowaniu atrybutu **Parameter** dla każdego parametru w zestawie parametrów.</span><span class="sxs-lookup"><span data-stu-id="57bb1-136">To create a parameter set, you must specify the `ParameterSetName` keyword when you declare the **Parameter** attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="57bb1-137">Dla parametrów, które należą do wielu zestawów parametrów, Dodaj atrybut **parametrów** dla każdego zestawu parametrów.</span><span class="sxs-lookup"><span data-stu-id="57bb1-137">For parameters that belong to multiple parameter sets, add a **Parameter** attribute for each parameter set.</span></span> <span data-ttu-id="57bb1-138">Ten atrybut umożliwia definiowanie parametru inaczej dla każdego zestawu parametrów.</span><span class="sxs-lookup"><span data-stu-id="57bb1-138">This attribute enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="57bb1-139">Na przykład można zdefiniować parametr jako obowiązkowy w jednym zestawie i opcjonalny w innym.</span><span class="sxs-lookup"><span data-stu-id="57bb1-139">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="57bb1-140">Jednak każdy zestaw parametrów musi zawierać jeden unikatowy parametr.</span><span class="sxs-lookup"><span data-stu-id="57bb1-140">However, each parameter set must contain one unique parameter.</span></span> <span data-ttu-id="57bb1-141">Aby uzyskać więcej informacji, zobacz [Deklaracja atrybutu parametru](parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="57bb1-141">For more information, see [Parameter Attribute Declaration](parameter-attribute-declaration.md).</span></span>

<span data-ttu-id="57bb1-142">W poniższym przykładzie parametr **username** jest unikatowym parametrem `Test01` zestawu parametrów, a parametr **ComputerName** `Test02` jest unikatowym parametrem zestawu parametrów.</span><span class="sxs-lookup"><span data-stu-id="57bb1-142">In the following example, the **UserName** parameter is the unique parameter of the `Test01` parameter set, and the **ComputerName** parameter is the unique parameter of the `Test02` parameter set.</span></span> <span data-ttu-id="57bb1-143">Parametr **SharedParam** należy do obu zestawów i jest obowiązkowy dla `Test01` zestawu parametrów, `Test02` ale opcjonalny dla zestawu parametrów.</span><span class="sxs-lookup"><span data-stu-id="57bb1-143">The **SharedParam** parameter belongs to both sets and is mandatory for the `Test01` parameter set but optional for the `Test02` parameter set.</span></span>

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
private string sharedParam;
```
