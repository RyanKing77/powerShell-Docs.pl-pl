---
title: Deklaracji atrybutu parametru | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, Parameter
- Parameter attribute, described
- Parameter attribute
ms.assetid: 08433d0b-169b-42c8-9335-2881d9034698
caps.latest.revision: 13
ms.openlocfilehash: 81b1ed95669f51ba554f6f99031d098e239f02e0
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735139"
---
# <a name="parameter-attribute-declaration"></a><span data-ttu-id="a31e5-102">Parameter, deklaracja atrybutu</span><span class="sxs-lookup"><span data-stu-id="a31e5-102">Parameter Attribute Declaration</span></span>

<span data-ttu-id="a31e5-103">Atrybut parametru identyfikuje właściwość publiczna klasy polecenia cmdlet jako parametr polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a31e5-103">The Parameter attribute identifies a public property of the cmdlet class as a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="a31e5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a31e5-104">Syntax</span></span>

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="a31e5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a31e5-105">Parameters</span></span>

<span data-ttu-id="a31e5-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) o nazwie parametr opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a31e5-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="a31e5-107">`True` Wskazuje, że parametr polecenia cmdlet jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="a31e5-107">`True` indicates the cmdlet parameter is required.</span></span> <span data-ttu-id="a31e5-108">Jeśli wymagany parametr nie zostanie podany, po wywołaniu polecenia cmdlet, programu Windows PowerShell monitu o wartości parametru.</span><span class="sxs-lookup"><span data-stu-id="a31e5-108">If a required parameter is not provided when the cmdlet is invoked, Windows PowerShell prompts the user for a parameter value.</span></span> <span data-ttu-id="a31e5-109">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="a31e5-109">The default is `false`.</span></span>

<span data-ttu-id="a31e5-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) o nazwie parametr opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a31e5-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) Optional named parameter.</span></span> <span data-ttu-id="a31e5-111">Określa, że parametr wartość, należy dla tego parametru polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a31e5-111">Specifies the parameter set that this cmdlet parameter belongs to.</span></span> <span data-ttu-id="a31e5-112">Jeśli nie ustawiono parametru jest określona, parametr należy do wszystkich zestawów parametrów.</span><span class="sxs-lookup"><span data-stu-id="a31e5-112">If no parameter set is specified, the parameter belongs to all parameter sets.</span></span>

<span data-ttu-id="a31e5-113">`Position` ([System.Int32](/dotnet/api/System.Int32)) o nazwie parametr opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a31e5-113">`Position` ([System.Int32](/dotnet/api/System.Int32)) Optional named parameter.</span></span> <span data-ttu-id="a31e5-114">Określa pozycję parametru w ramach polecenia programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a31e5-114">Specifies the position of the parameter within a Windows PowerShell command.</span></span>

<span data-ttu-id="a31e5-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) o nazwie parametr opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a31e5-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="a31e5-116">`True` Wskazuje, że parametr polecenia cmdlet trwa jego wartość z obiektu procesu.</span><span class="sxs-lookup"><span data-stu-id="a31e5-116">`True` indicates that the cmdlet parameter takes its value from a pipeline object.</span></span> <span data-ttu-id="a31e5-117">Określ to słowo kluczowe, jeśli polecenie cmdlet uzyskuje dostęp do pełnego obiektu i nie tylko właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="a31e5-117">Specify this keyword if the cmdlet accesses the complete object, not just a property of the object.</span></span> <span data-ttu-id="a31e5-118">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="a31e5-118">The default is `false`.</span></span>

<span data-ttu-id="a31e5-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) o nazwie parametr opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a31e5-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="a31e5-120">`True` Wskazuje, że parametr polecenia cmdlet trwa jego wartość z właściwości obiektu potoku, który ma taką samą nazwę lub tego samego aliasu jako parametr.</span><span class="sxs-lookup"><span data-stu-id="a31e5-120">`True` indicates that the cmdlet parameter takes its value from a property of a pipeline object that has either the same name or the same alias as this parameter.</span></span> <span data-ttu-id="a31e5-121">Na przykład, jeśli polecenie cmdlet ma `Name` parametr oraz obiekt potoku ma również `Name` właściwości, wartość `Name` właściwość jest przypisany do `Name` parametru polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a31e5-121">For example, if the cmdlet has a `Name` parameter and the pipeline object also has a `Name` property, the value of the `Name` property is assigned to the `Name` parameter of the cmdlet.</span></span> <span data-ttu-id="a31e5-122">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="a31e5-122">The default is `false`.</span></span>

<span data-ttu-id="a31e5-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) o nazwie parametr opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a31e5-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="a31e5-124">`True` Wskazuje, że parametr polecenia cmdlet akceptuje wszystkie pozostałe argumenty, które są przekazywane do polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a31e5-124">`True` indicates that the cmdlet parameter accepts all remaining arguments that are passed to the cmdlet.</span></span> <span data-ttu-id="a31e5-125">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="a31e5-125">The default is `false`.</span></span>

<span data-ttu-id="a31e5-126">`HelpMessage` Opcjonalne, o nazwie parametru.</span><span class="sxs-lookup"><span data-stu-id="a31e5-126">`HelpMessage` Optional named parameter.</span></span> <span data-ttu-id="a31e5-127">Określa krótki opis parametru.</span><span class="sxs-lookup"><span data-stu-id="a31e5-127">Specifies a short description of the parameter.</span></span> <span data-ttu-id="a31e5-128">Po uruchomieniu polecenia cmdlet i obowiązkowy parametr nie zostanie określony, program Windows PowerShell wyświetla ten komunikat.</span><span class="sxs-lookup"><span data-stu-id="a31e5-128">Windows PowerShell displays this message when a cmdlet is run and a mandatory parameter is not specified.</span></span>

<span data-ttu-id="a31e5-129">`HelpMessageBaseName` Opcjonalne, o nazwie parametru. Określa lokalizację, w którym są przechowywane identyfikatory zasobów.</span><span class="sxs-lookup"><span data-stu-id="a31e5-129">`HelpMessageBaseName` Optional named parameter.Specifies the location where resource identifiers reside.</span></span> <span data-ttu-id="a31e5-130">Na przykład ten parametr można określić zestaw zasobów, który zawiera komunikaty Pomocy, które chcesz zlokalizować.</span><span class="sxs-lookup"><span data-stu-id="a31e5-130">For example, this parameter could specify a resource assembly that contains Help messages that you want to localize.</span></span>

<span data-ttu-id="a31e5-131">`HelpMessageResourceId` Opcjonalne, o nazwie parametru. Określa identyfikator zasobu komunikat pomocy.</span><span class="sxs-lookup"><span data-stu-id="a31e5-131">`HelpMessageResourceId` Optional named parameter.Specifies the resource identifier for a Help message.</span></span>

## <a name="remarks"></a><span data-ttu-id="a31e5-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a31e5-132">Remarks</span></span>

- <span data-ttu-id="a31e5-133">Aby uzyskać więcej informacji o tym, jak można zadeklarować tego atrybutu, zobacz [jak deklarować parametry polecenia Cmdlet](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="a31e5-133">For more information about how to declare this attribute, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="a31e5-134">Polecenie cmdlet może mieć dowolną liczbę parametrów.</span><span class="sxs-lookup"><span data-stu-id="a31e5-134">A cmdlet can have any number of parameters.</span></span> <span data-ttu-id="a31e5-135">Jednak dla wygody użytkowników, należy ograniczyć liczbę tych parametrów.</span><span class="sxs-lookup"><span data-stu-id="a31e5-135">However, for a better user experience, limit the number of parameters.</span></span>

- <span data-ttu-id="a31e5-136">Parametry musi być zadeklarowany w publicznych niestatycznego pola lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="a31e5-136">Parameters must be declared on public non-static fields or properties.</span></span> <span data-ttu-id="a31e5-137">Parametry powinny być zadeklarowane we właściwościach.</span><span class="sxs-lookup"><span data-stu-id="a31e5-137">Parameters should be declared on properties.</span></span> <span data-ttu-id="a31e5-138">Właściwość musi mieć metodę dostępu publicznego zestawu i, jeśli `ValueFromPipeline` lub `ValueFromPipelineByPropertyName` — słowo kluczowe jest określony, właściwość musi mieć metodę dostępu get publicznych.</span><span class="sxs-lookup"><span data-stu-id="a31e5-138">The property must have a public set accessor, and if the `ValueFromPipeline` or `ValueFromPipelineByPropertyName` keyword is specified, the property must have a public get accessor.</span></span>

- <span data-ttu-id="a31e5-139">Po określeniu parametry pozycyjne, należy ograniczyć liczbę parametry pozycyjne w parametrze mniej niż pięć.</span><span class="sxs-lookup"><span data-stu-id="a31e5-139">When you specify positional parameters,  limit the number of positional parameters in a parameter set to less than five.</span></span> <span data-ttu-id="a31e5-140">I parametry pozycyjne nie muszą być ciągłe.</span><span class="sxs-lookup"><span data-stu-id="a31e5-140">And, positional parameters do not have to be contiguous.</span></span> <span data-ttu-id="a31e5-141">Pozycje 5, 100 i 250 działać tak samo, jak pozycje 0, 1 i 2.</span><span class="sxs-lookup"><span data-stu-id="a31e5-141">Positions 5, 100, and 250 work the same as positions 0, 1, and 2.</span></span>

- <span data-ttu-id="a31e5-142">Gdy `Position` — słowo kluczowe nie zostanie określona, parametr polecenia cmdlet muszą być przywoływane przez jego nazwę.</span><span class="sxs-lookup"><span data-stu-id="a31e5-142">When the `Position` keyword is not specified, the cmdlet parameter must be referenced by its name.</span></span>

- <span data-ttu-id="a31e5-143">Korzystając z zestawów parametrów, pamiętaj o następujących kwestiach:</span><span class="sxs-lookup"><span data-stu-id="a31e5-143">When you use parameter sets, note the following:</span></span>

    - <span data-ttu-id="a31e5-144">Każdy zestaw parametrów musi mieć co najmniej jeden parametr unikatowy.</span><span class="sxs-lookup"><span data-stu-id="a31e5-144">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="a31e5-145">Projekt dobre polecenia cmdlet oznacza, że ten unikatowy parametr należy również wymagane, jeśli jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="a31e5-145">Good cmdlet design indicates this unique parameter should also be mandatory if possible.</span></span> <span data-ttu-id="a31e5-146">Jeśli Twojego polecenia cmdlet jest przeznaczony do uruchamiania bez parametrów, unikatowy parametr nie może być wymagane.</span><span class="sxs-lookup"><span data-stu-id="a31e5-146">If your cmdlet is designed to be run without parameters, the unique parameter cannot be mandatory.</span></span>

    - <span data-ttu-id="a31e5-147">Nie ustawiono parametru może zawierać więcej niż jeden parametr pozycyjne, z tym samym położeniu.</span><span class="sxs-lookup"><span data-stu-id="a31e5-147">No parameter set should contain more than one positional parameter with the same position.</span></span>

    - <span data-ttu-id="a31e5-148">Tylko jeden parametr w zestawie parametrów powinny deklarować `ValueFromPipeline = true`.</span><span class="sxs-lookup"><span data-stu-id="a31e5-148">Only one parameter in a parameter set should declare `ValueFromPipeline = true`.</span></span> <span data-ttu-id="a31e5-149">Można zdefiniować wiele parametrów `ValueFromPipelineByPropertyName = true`.</span><span class="sxs-lookup"><span data-stu-id="a31e5-149">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

    - <span data-ttu-id="a31e5-150">Można zdefiniować wiele parametrów `ValueFromPipelineByPropertyName = true`.</span><span class="sxs-lookup"><span data-stu-id="a31e5-150">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

- <span data-ttu-id="a31e5-151">Aby uzyskać więcej informacji na temat wytycznych dotyczących nazwy parametrów, zobacz [nazwy parametrów polecenia Cmdlet](standard-cmdlet-parameter-names-and-types.md).</span><span class="sxs-lookup"><span data-stu-id="a31e5-151">For more information about the guidelines for parameter names, see [Cmdlet Parameter Names](standard-cmdlet-parameter-names-and-types.md).</span></span>

- <span data-ttu-id="a31e5-152">Atrybut parametru jest definiowany przez [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) klasy.</span><span class="sxs-lookup"><span data-stu-id="a31e5-152">The parameter attribute is defined by the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="a31e5-153">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a31e5-153">See Also</span></span>

[<span data-ttu-id="a31e5-154">System.Management.Automation.Parameterattribute</span><span class="sxs-lookup"><span data-stu-id="a31e5-154">System.Management.Automation.Parameterattribute</span></span>](/dotnet/api/System.Management.Automation.ParameterAttribute)

[<span data-ttu-id="a31e5-155">Nazwy parametrów polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="a31e5-155">Cmdlet Parameter Names</span></span>](standard-cmdlet-parameter-names-and-types.md)

[<span data-ttu-id="a31e5-156">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a31e5-156">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
