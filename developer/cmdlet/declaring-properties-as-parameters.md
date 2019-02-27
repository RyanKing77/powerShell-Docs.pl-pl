---
title: Deklarowanie właściwości jako parametry | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f71ea35d-cff5-4e44-a5c6-3a747ed4c4d9
caps.latest.revision: 9
ms.openlocfilehash: 6f6640afb15b3608669538f9b5f53d7a8a5c380d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850575"
---
# <a name="declaring-properties-as-parameters"></a><span data-ttu-id="9939c-102">Deklarowanie właściwości jako parametrów</span><span class="sxs-lookup"><span data-stu-id="9939c-102">Declaring Properties as Parameters</span></span>

<span data-ttu-id="9939c-103">Ten temat zawiera podstawowe informacje, które należy zrozumieć przed możesz deklarować parametry polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9939c-103">This topic provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="9939c-104">Aby zadeklarować parametry polecenia cmdlet w swojej klasie polecenia cmdlet, zdefiniuj właściwości publiczne, które reprezentują każdego parametru, a następnie dodaj jeden lub więcej atrybutów parametr do każdej właściwości.</span><span class="sxs-lookup"><span data-stu-id="9939c-104">To declare the parameters of a cmdlet within your cmdlet class, define the public properties that represent each parameter, and then add one or more Parameter attributes to each property.</span></span> <span data-ttu-id="9939c-105">Środowisko wykonawcze programu Windows PowerShell używa atrybuty parametru do identyfikacji właściwość jako parametr polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9939c-105">The Windows PowerShell runtime uses the Parameter attributes to identify the property as a cmdlet parameter.</span></span> <span data-ttu-id="9939c-106">Podstawowa składnia do deklarowania atrybutu parametru jest `[Parameter()]`.</span><span class="sxs-lookup"><span data-stu-id="9939c-106">The basic syntax for declaring the Parameter attribute is `[Parameter()]`.</span></span>

<span data-ttu-id="9939c-107">Oto przykład właściwości zdefiniowane jako wymaganego parametru.</span><span class="sxs-lookup"><span data-stu-id="9939c-107">Here is an example of a property defined as a required parameter.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="9939c-108">Poniżej przedstawiono niektóre kwestie, pamiętaj o parametrach.</span><span class="sxs-lookup"><span data-stu-id="9939c-108">Here are some things to remember about parameters.</span></span>

- <span data-ttu-id="9939c-109">Parametr musi być jawnie oznaczone jako publiczne.</span><span class="sxs-lookup"><span data-stu-id="9939c-109">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="9939c-110">Parametry, które nie są oznaczane jako publicznego domyślnego wewnętrznego i nie zostanie znaleziony w czasie wykonywania programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9939c-110">Parameters that are not marked as public default to internal and will not be found by the Windows PowerShell runtime.</span></span>

- <span data-ttu-id="9939c-111">Parametry powinna być zdefiniowana jako typy Microsoft .NET Framework w celu zapewnienia lepszej Walidacja parametru.</span><span class="sxs-lookup"><span data-stu-id="9939c-111">Parameters should be defined as Microsoft .NET Framework types to provide better parameter validation.</span></span> <span data-ttu-id="9939c-112">Na przykład parametry, które są ograniczone do jednej wartości z zestawu wartości powinna być zdefiniowana jako typ wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="9939c-112">For example, parameters that are restricted to one value out of a set of values should be defined as an enumeration type.</span></span> <span data-ttu-id="9939c-113">Parametry, które przyjmują wartość identyfikatora URI (Uniform Resource) powinny być typu [System.Uri](/dotnet/api/System.Uri).</span><span class="sxs-lookup"><span data-stu-id="9939c-113">Parameters that take a Uniform Resource Identifier (URI) value should be of type [System.Uri](/dotnet/api/System.Uri).</span></span>

- <span data-ttu-id="9939c-114">Unikaj parametrów ciągu podstawowe właściwości wszystkie elementy oprócz dowolnego tekstu.</span><span class="sxs-lookup"><span data-stu-id="9939c-114">Avoid basic string parameters for all but free-form text properties.</span></span>

- <span data-ttu-id="9939c-115">Możesz dodać parametr do dowolnej liczby zestawów parametrów.</span><span class="sxs-lookup"><span data-stu-id="9939c-115">You can add a parameter to any number of parameter sets.</span></span> <span data-ttu-id="9939c-116">Aby uzyskać więcej informacji na temat zestawów parametrów, zobacz [zestawy parametrów polecenia Cmdlet](./cmdlet-parameter-sets.md).</span><span class="sxs-lookup"><span data-stu-id="9939c-116">For more information about parameter sets, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

<span data-ttu-id="9939c-117">Program Windows PowerShell udostępnia również zestaw wspólnych parametrów, które są automatycznie dostępne dla każdego polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9939c-117">Windows PowerShell also provides a set of common parameters that are automatically available to every cmdlet.</span></span> <span data-ttu-id="9939c-118">Aby uzyskać więcej informacji na temat tych parametrów i ich aliasy, zobacz [wspólne parametry polecenia Cmdlet](./common-parameter-names.md).</span><span class="sxs-lookup"><span data-stu-id="9939c-118">For more information about these parameters and their aliases, see [Cmdlet Common Parameters](./common-parameter-names.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9939c-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9939c-119">See Also</span></span>

[<span data-ttu-id="9939c-120">Polecenia cmdlet typowych parametrów</span><span class="sxs-lookup"><span data-stu-id="9939c-120">Cmdlet Common Parameters</span></span>](./common-parameter-names.md)

[<span data-ttu-id="9939c-121">Typy parametrów polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9939c-121">Types of Cmdlet Parameter</span></span>](./types-of-cmdlet-parameters.md)

[<span data-ttu-id="9939c-122">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9939c-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
