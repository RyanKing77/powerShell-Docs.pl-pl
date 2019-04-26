---
title: Sposób deklarowania zestawów parametrów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46905eb9-64d7-4c55-9c2a-7bc7bf04e14b
caps.latest.revision: 10
ms.openlocfilehash: 6c2e5891a8e3f24969c12a2e57dc5ae8caa68e41
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067896"
---
# <a name="how-to-declare-parameter-sets"></a><span data-ttu-id="40aba-102">Jak zadeklarować zestawy parametrów</span><span class="sxs-lookup"><span data-stu-id="40aba-102">How to Declare Parameter Sets</span></span>

<span data-ttu-id="40aba-103">W tym przykładzie pokazano, jak zdefiniować dwa zestawy parametrów, kiedy Deklarujesz parametry polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="40aba-103">This example shows how to define two parameter sets when you declare the parameters for a cmdlet.</span></span> <span data-ttu-id="40aba-104">Każdy zestaw parametrów ma unikatowy parametr i udostępniony parametr, który jest używany przez oba zestawy parametrów.</span><span class="sxs-lookup"><span data-stu-id="40aba-104">Each parameter set has both a unique parameter and a shared parameter that is used by both parameter sets.</span></span> <span data-ttu-id="40aba-105">Aby uzyskać więcej informacji na temat zestawów parametrów, w tym jak określić domyślny zestaw parametrów, zobacz [zestawy parametrów polecenia Cmdlet](./cmdlet-parameter-sets.md).</span><span class="sxs-lookup"><span data-stu-id="40aba-105">For more information about parameters sets, including how to specify the default parameter set, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="40aba-106">Jeśli to możliwe, należy zdefiniować unikatowy parametr parametrem, który został ustawiony jako wymaganego parametru.</span><span class="sxs-lookup"><span data-stu-id="40aba-106">Whenever possible, define the unique parameter of a parameter set as a required parameter.</span></span> <span data-ttu-id="40aba-107">Jednak jeśli chcesz, aby Twoje polecenie cmdlet do uruchomienia bez określenia wszystkich parametrów, unikatowy parametr może być opcjonalny parametr.</span><span class="sxs-lookup"><span data-stu-id="40aba-107">However, if you want your cmdlet to run without specifying any parameters, the unique parameter can be an optional parameter.</span></span> <span data-ttu-id="40aba-108">Na przykład, unikatową wartość parametru `Get-Command` polecenia cmdlet jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="40aba-108">For example, the unique parameter of the `Get-Command` cmdlet is optional.</span></span>

## <a name="how-to-define-two-parameter-sets"></a><span data-ttu-id="40aba-109">Jak zdefiniować dwa zestawy parametrów</span><span class="sxs-lookup"><span data-stu-id="40aba-109">How to Define Two Parameter Sets</span></span>

1. <span data-ttu-id="40aba-110">Dodaj `ParameterSet` — słowo kluczowe do atrybutu parametru dla parametru unikatowy pierwszy zestaw parametrów.</span><span class="sxs-lookup"><span data-stu-id="40aba-110">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the first parameter set.</span></span>

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test01")]
   public string UserName
   {
     get { return userName; }
     set { userName = value; }
   }
   private string userName;
   ```

2. <span data-ttu-id="40aba-111">Dodaj `ParameterSet` — słowo kluczowe do atrybutu parametru dla parametru unikatowy drugi zestaw parametrów.</span><span class="sxs-lookup"><span data-stu-id="40aba-111">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the second parameter set.</span></span>

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test02")]
   public string ComputerName
   {
     get { return computerName; }
     set { computerName = value; }
   }
   private string computerName;
   ```

3. <span data-ttu-id="40aba-112">Dla parametru, który należy do obu zestawów parametrów, Dodaj atrybut parametr, dla każdego zestawu parametrów, a następnie dodaj `ParameterSet` — słowo kluczowe do każdej grupy.</span><span class="sxs-lookup"><span data-stu-id="40aba-112">For the parameter that belongs to both parameter sets, add a Parameter attribute for each parameter set and then add the `ParameterSet` keyword to each set.</span></span> <span data-ttu-id="40aba-113">Każdy atrybut parametru można określić, jak ten parametr jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="40aba-113">In each Parameter attribute, you can specify how that parameter is defined.</span></span> <span data-ttu-id="40aba-114">Parametr może być opcjonalny w jednym zestawie i obowiązkowe w innym.</span><span class="sxs-lookup"><span data-stu-id="40aba-114">A parameter can be optional in one set and mandatory in another.</span></span>

   ```csharp
   [Parameter(Mandatory= true, ParameterSetName = "Test01")]
   [Parameter(ParameterSetName = "Test02")]
   public string SharedParam
   {
       get { return sharedParam; }
       set { sharedParam = value; }
   }
   private string sharedParam;
   ```

## <a name="see-also"></a><span data-ttu-id="40aba-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="40aba-115">See Also</span></span>

[<span data-ttu-id="40aba-116">Zestawy parametrów polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="40aba-116">Cmdlet Parameter Sets</span></span>](./cmdlet-parameter-sets.md)

[<span data-ttu-id="40aba-117">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="40aba-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
