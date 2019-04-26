---
title: Parametry polecenia cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- optional parameters [PowerShell SDK]
- aliases [PowerShell SDK]
- parameter sets [PowerShell SDK]
- parameters [PowerShell SDK]
- mandatory parameters [PowerShell SDK]
- positional parameters [PowerShell SDK]
- cmdlets [PowerShell SDK], parameters
ms.assetid: 3f1cca5f-5b95-4bce-94a6-a22db1aefd47
caps.latest.revision: 23
ms.openlocfilehash: 914a10907bcf980eed8d7e2f819c382fe6b341ad
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068406"
---
# <a name="cmdlet-parameters"></a><span data-ttu-id="a8c87-102">Parametry poleceń cmdlet</span><span class="sxs-lookup"><span data-stu-id="a8c87-102">Cmdlet Parameters</span></span>

<span data-ttu-id="a8c87-103">Parametry polecenia cmdlet zawierają mechanizm, który umożliwia polecenia cmdlet, aby akceptować dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="a8c87-103">Cmdlet parameters provide the mechanism that allows a cmdlet to accept input.</span></span> <span data-ttu-id="a8c87-104">Parametry może akceptować dane wejściowe bezpośrednio z poziomu wiersza polecenia lub z obiektów przekazywane do polecenia cmdlet potoku, a argumenty (znany także jako *wartości*) te parametry można określić danych wejściowych, które polecenie cmdlet przyjmuje się, jak polecenia cmdlet należy wykonywać swoje działania i dane, które polecenie cmdlet zwraca do potoku.</span><span class="sxs-lookup"><span data-stu-id="a8c87-104">Parameters can accept input directly from the command line, or from objects passed to the cmdlet through the pipeline, The arguments (also known as *values*) of these parameters can specify the input that the cmdlet accepts, how the cmdlet should perform its actions, and the data that the cmdlet returns to the pipeline.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a8c87-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="a8c87-105">In This Section</span></span>

<span data-ttu-id="a8c87-106">[Deklarowanie właściwości jako parametry](./declaring-properties-as-parameters.md) zawiera podstawowe informacje, które należy zrozumieć przed możesz deklarować parametry polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a8c87-106">[Declaring Properties as Parameters](./declaring-properties-as-parameters.md) Provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="a8c87-107">[Typy parametrów polecenia Cmdlet](./types-of-cmdlet-parameters.md) opisano różne typy parametrów, które można zadeklarować w poleceniach cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a8c87-107">[Types of Cmdlet Parameters](./types-of-cmdlet-parameters.md) Describes the different types of parameters that you can declare in cmdlets.</span></span>

<span data-ttu-id="a8c87-108">[Nazwa parametru polecenia cmdlet i wskazówki dotyczące funkcji](./standard-cmdlet-parameter-names-and-types.md) dyski nazw, zaleca się typ danych i funkcje standardowe parametry.</span><span class="sxs-lookup"><span data-stu-id="a8c87-108">[Cmdlet Parameter Name and Functionality Guidelines](./standard-cmdlet-parameter-names-and-types.md) Discuses the names, recommended data type, and functionality of standard parameters.</span></span>

<span data-ttu-id="a8c87-109">[Aliasy parametr](./parameter-aliases.md) w tym artykule omówiono aliasy, które można zdefiniować dla parametrów.</span><span class="sxs-lookup"><span data-stu-id="a8c87-109">[Parameter Aliases](./parameter-aliases.md) Discusses the aliases that you can define for parameters.</span></span>

<span data-ttu-id="a8c87-110">[Nazwy wspólnych parametrów](./common-parameter-names.md) w tym temacie opisano parametry, które dodaje poleceń cmdlet programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a8c87-110">[Common Parameter Names](./common-parameter-names.md) This topic describes the parameters that Windows PowerShell adds to cmdlets.</span></span>

<span data-ttu-id="a8c87-111">[Zestawy parametrów polecenia cmdlet](./cmdlet-parameter-sets.md) w tym artykule omówiono, jak zestawy parametrów umożliwiają pisanie jednej polecenia cmdlet, które można wykonywać różne akcje dla różnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="a8c87-111">[Cmdlet Parameter Sets](./cmdlet-parameter-sets.md) Discusses how parameter sets enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span>

<span data-ttu-id="a8c87-112">[Parametry dynamiczne polecenia cmdlet](./cmdlet-dynamic-parameters.md) opisano parametry, które są dostępne dla użytkownika na warunkach specjalnych.</span><span class="sxs-lookup"><span data-stu-id="a8c87-112">[Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md) Discusses parameters that are available to the user under special conditions.</span></span>

<span data-ttu-id="a8c87-113">[Obsługa symboli wieloznacznych w parametry polecenia Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md) opisano, jak w celu zapewnienia obsługi symboli wieloznacznych podczas projektowania polecenia cmdlet, które będą uruchamiane w odniesieniu do grupy zasobów.</span><span class="sxs-lookup"><span data-stu-id="a8c87-113">[Supporting Wildcard Characters in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md) Describes how to provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

<span data-ttu-id="a8c87-114">[Walidacja danych wejściowych parametr](./validating-parameter-input.md) w tym artykule opisano, jak sprawdza, argumenty przekazane do parametrów polecenia cmdlet programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a8c87-114">[Validating Parameter Input](./validating-parameter-input.md) Describes how Windows PowerShell validates the arguments passed to cmdlet parameters.</span></span>

<span data-ttu-id="a8c87-115">[Filtr parametrów wejściowych](./input-filter-parameters.md) Discusses `Filter`, `Include`, i `Exclude` parametry, które filtrowania zestawu danych wejściowych obiektów, które ma wpływ na polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a8c87-115">[Input Filter Parameters](./input-filter-parameters.md) Discusses the `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

## <a name="related-sections"></a><span data-ttu-id="a8c87-116">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="a8c87-116">Related Sections</span></span>

[<span data-ttu-id="a8c87-117">Sposób sprawdzania poprawności wprowadzania parametrów</span><span class="sxs-lookup"><span data-stu-id="a8c87-117">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

## <a name="see-also"></a><span data-ttu-id="a8c87-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a8c87-118">See Also</span></span>

[<span data-ttu-id="a8c87-119">Deklaracji atrybutu parametru</span><span class="sxs-lookup"><span data-stu-id="a8c87-119">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="a8c87-120">Polecenia cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a8c87-120">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)
