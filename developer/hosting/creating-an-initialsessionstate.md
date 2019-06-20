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
# <a name="creating-an-initialsessionstate"></a>Tworzenie elementu InitialSessionState

Polecenia programu PowerShell są uruchamiane w obszarze działania.
Aby zapewnić obsługę programu PowerShell w aplikacji, należy utworzyć [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) obiektu.
Każdy obszar działania ma [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) obiekt skojarzony z nim.
InitialSessionState określa właściwości obszaru działania, takich jak który polecenia, zmienne i moduły są dostępne dla tego obszaru działania.

## <a name="create-a-default-initialsessionstate"></a>Tworzy domyślny InitialSessionState

[CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) i [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) metody **InitialSessionState** klasy może służyć do tworzenia **InitialSessionState**obiektu.
**CreateDefault** metoda tworzy **InitialSessionState** ze wszystkimi wbudowanymi poleceniami załadowany, podczas **CreateDefault2** metoda ładuje tylko polecenia wymagane na hoście programu PowerShell (poleceń w module Microsoft.PowerShell.Core).

Jeśli chcesz bardziej ograniczyć poleceń dostępnych w aplikacji należy utworzyć ograniczonego obszaru działania.
Aby uzyskać informacje, zobacz [tworzenia ograniczonego obszaru działania](creating-a-constrained-runspace.md).

Poniższy kod przedstawia sposób tworzenia **InitialSessionState**, przypisać go do obszaru działania, Dodaj polecenia do potoku w tym obszarze działania i wywołania polecenia.
Aby uzyskać więcej informacji na temat dodawania i wywoływania poleceń, zobacz [Dodawanie i wywoływania poleceń](adding-and-invoking-commands.md).

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

## <a name="see-also"></a>Zobacz też

[Tworzenie ograniczonego obszaru działania](creating-a-constrained-runspace.md)

[Dodawanie i wywoływania poleceń](adding-and-invoking-commands.md)
