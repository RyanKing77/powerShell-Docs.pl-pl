---
title: Tworzenie InitialSessionState | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ae707db-52e0-408c-87fa-b35c42eaaab1
caps.latest.revision: 5
ms.openlocfilehash: 9140d03e046def2fbbcc2a842b9ea1b9e1fa2985
ms.sourcegitcommit: 13f24786ed39ca1c07eff2b73a1974c366e31cb8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263835"
---
# <a name="creating-an-initialsessionstate"></a><span data-ttu-id="489b3-102">Tworzenie elementu InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="489b3-102">Creating an InitialSessionState</span></span>

<span data-ttu-id="489b3-103">Polecenia programu PowerShell są uruchamiane w obszarze działania.</span><span class="sxs-lookup"><span data-stu-id="489b3-103">PowerShell commands run in a runspace.</span></span>
<span data-ttu-id="489b3-104">Aby zapewnić obsługę programu PowerShell w aplikacji, należy utworzyć [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) obiektu.</span><span class="sxs-lookup"><span data-stu-id="489b3-104">To host PowerShell in your application, you must create a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span></span>
<span data-ttu-id="489b3-105">Każdy obszar działania ma [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) obiekt skojarzony z nim.</span><span class="sxs-lookup"><span data-stu-id="489b3-105">Every runspace has an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object associated with it.</span></span>
<span data-ttu-id="489b3-106">InitialSessionState określa właściwości obszaru działania, takich jak który polecenia, zmienne i moduły są dostępne dla tego obszaru działania.</span><span class="sxs-lookup"><span data-stu-id="489b3-106">The InitialSessionState specifies characteristics of the runspace, such as which commands, variables, and modules are available for that runspace.</span></span>

## <a name="create-a-default-initialsessionstate"></a><span data-ttu-id="489b3-107">Tworzy domyślny InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="489b3-107">Create a default InitialSessionState</span></span>

<span data-ttu-id="489b3-108">[CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) i [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) metody **InitialSessionState** klasy może służyć do tworzenia **InitialSessionState**obiektu.</span><span class="sxs-lookup"><span data-stu-id="489b3-108">The [CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) and [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) methods of the **InitialSessionState** class can be used to create an **InitialSessionState** object.</span></span>
<span data-ttu-id="489b3-109">**CreateDefault** metoda tworzy **InitialSessionState** ze wszystkimi wbudowanymi poleceniami załadowany, podczas **CreateDefault2** metoda ładuje tylko polecenia wymagane na hoście programu PowerShell (poleceń w module Microsoft.PowerShell.Core).</span><span class="sxs-lookup"><span data-stu-id="489b3-109">The **CreateDefault** method creates an **InitialSessionState** with all of the built-in commands loaded, while the **CreateDefault2** method loads only the commands required to host PowerShell (the commands from the Microsoft.PowerShell.Core module).</span></span>

<span data-ttu-id="489b3-110">Jeśli chcesz bardziej ograniczyć poleceń dostępnych w aplikacji należy utworzyć ograniczonego obszaru działania.</span><span class="sxs-lookup"><span data-stu-id="489b3-110">If you want to further limit the commands available in your host application you need to create a constrained runspace.</span></span>
<span data-ttu-id="489b3-111">Aby uzyskać informacje, zobacz [tworzenia ograniczonego obszaru działania](creating-a-constrained-runspace.md).</span><span class="sxs-lookup"><span data-stu-id="489b3-111">For information, see [Creating a constrained runspace](creating-a-constrained-runspace.md).</span></span>

<span data-ttu-id="489b3-112">Poniższy kod przedstawia sposób tworzenia **InitialSessionState**, przypisać go do obszaru działania, Dodaj polecenia do potoku w tym obszarze działania i wywołania polecenia.</span><span class="sxs-lookup"><span data-stu-id="489b3-112">The following code shows how to create an **InitialSessionState**, assign it to a runspace, add commands to the pipeline in that runspace, and invoke the commands.</span></span>
<span data-ttu-id="489b3-113">Aby uzyskać więcej informacji na temat dodawania i wywoływania poleceń, zobacz [Dodawanie i wywoływania poleceń](adding-and-invoking-commands.md).</span><span class="sxs-lookup"><span data-stu-id="489b3-113">For more information about adding and invoking commands, see [Adding and invoking commands](adding-and-invoking-commands.md).</span></span>

```csharp
namespace SampleHost
{
  using System;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;

  class HostP4b
  {
    static void Main(string[] args)
    {
      // Call the InitialSessionState.CreateDefault method to create
      // an empty InitialSessionState object, and then add the
      // elements that will be available when the runspace is opened.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      SessionStateVariableEntry var1 = new
          SessionStateVariableEntry("test1",
                                    "MyVar1",
                                    "Initial session state MyVar1 test");
      iss.Variables.Add(var1);

      SessionStateVariableEntry var2 = new
          SessionStateVariableEntry("test2",
                                    "MyVar2",
                                    "Initial session state MyVar2 test");
      iss.Variables.Add(var2);

      // Call the RunspaceFactory.CreateRunspace(InitialSessionState)
      // method to create the runspace where the pipeline is run.
      Runspace rs = RunspaceFactory.CreateRunspace(iss);
      rs.Open();

      // Call the PowerShell.Create() method to create the PowerShell object,
      // and then specify the runspace and commands to the pipeline.
      // and create the command pipeline.
      PowerShell ps = PowerShell.Create();
      ps.Runspace = rs;
      ps.AddCommand("Get-Variable");
      ps.AddArgument("test*");

      Console.WriteLine("Variable             Value");
      Console.WriteLine("--------------------------");

      // Call the PowerShell.Invoke() method to run
      // the pipeline synchronously.
      foreach (PSObject result in ps.Invoke())
      {
        Console.WriteLine("{0,-20}{1}",
            result.Members["Name"].Value,
            result.Members["Value"].Value);
      } // End foreach.

      // Close the runspace to free resources.
      rs.Close();

    } // End Main.
  } // End SampleHost.
}
```

## <a name="see-also"></a><span data-ttu-id="489b3-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="489b3-114">See Also</span></span>

[<span data-ttu-id="489b3-115">Tworzenie ograniczonego obszaru działania</span><span class="sxs-lookup"><span data-stu-id="489b3-115">Creating a constrained runspace</span></span>](creating-a-constrained-runspace.md)

[<span data-ttu-id="489b3-116">Dodawanie i wywoływania poleceń</span><span class="sxs-lookup"><span data-stu-id="489b3-116">Adding and invoking commands</span></span>](adding-and-invoking-commands.md)
