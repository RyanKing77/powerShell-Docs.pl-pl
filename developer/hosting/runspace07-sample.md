---
title: Przykładowe Runspace07 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4f7bf81e-4f95-4150-afc3-c0872b24d026
caps.latest.revision: 7
ms.openlocfilehash: 3205286fbbc823d21e29a328b3ba9c4c1459d9ff
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082686"
---
# <a name="runspace07-sample"></a><span data-ttu-id="ef43e-102">Przykład Runspace07</span><span class="sxs-lookup"><span data-stu-id="ef43e-102">Runspace07 Sample</span></span>

<span data-ttu-id="ef43e-103">W tym przykładzie pokazano, jak utworzyć obszar działania, a następnie użyj tego obszaru działania na dwa polecenia cmdlet były uruchamiane synchronicznie przy użyciu [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) obiektu.</span><span class="sxs-lookup"><span data-stu-id="ef43e-103">This sample shows how to create a runspace, and then use that runspace to run two cmdlets synchronously by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

## <a name="requirements"></a><span data-ttu-id="ef43e-104">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ef43e-104">Requirements</span></span>

<span data-ttu-id="ef43e-105">Ten przykładowy skrypt wymaga programu Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="ef43e-105">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="ef43e-106">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="ef43e-106">Demonstrates</span></span>

<span data-ttu-id="ef43e-107">W przykładzie pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="ef43e-107">This sample demonstrates the following.</span></span>

- <span data-ttu-id="ef43e-108">Tworzenie [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) obiektu za pomocą [System.Management.Automation.Runspaces.Runspacefactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) klasy.</span><span class="sxs-lookup"><span data-stu-id="ef43e-108">Creating a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object by using the [System.Management.Automation.Runspaces.Runspacefactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) class.</span></span>

- <span data-ttu-id="ef43e-109">Tworzenie [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) obiektu, który używa obszarze działania.</span><span class="sxs-lookup"><span data-stu-id="ef43e-109">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the runspace.</span></span>

- <span data-ttu-id="ef43e-110">Dodanie polecenia cmdlet do potoku [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) obiektu.</span><span class="sxs-lookup"><span data-stu-id="ef43e-110">Adding cmdlets to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="ef43e-111">Uruchamiać polecenia cmdlet synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="ef43e-111">Running the cmdlets synchronously.</span></span>

- <span data-ttu-id="ef43e-112">Trwa wyodrębnianie właściwości z [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) obiektów zwróconych przez polecenie.</span><span class="sxs-lookup"><span data-stu-id="ef43e-112">Extracting properties from the [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="ef43e-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="ef43e-113">Example</span></span>

<span data-ttu-id="ef43e-114">Ta aplikacja przykładowa tworzy obszar działania używane przez [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) obiektu, aby uruchomić [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) i [obiektu miary](/powershell/module/microsoft.powershell.utility/measure-object) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ef43e-114">This sample creates a runspace that used by a [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) object to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Measure-Object](/powershell/module/microsoft.powershell.utility/measure-object) cmdlets.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace07
  {
    /// <summary>
    /// This sample shows how to create a runspace and how to run commands
    /// using a PowerShell object. It builds a pipeline that runs the
    /// get-process cmdlet, which is piped to the measure-object
    /// cmdlet to count the number of processes running on the system.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a runspace using the RunspaceFactory class.
    /// 2. Creating a PowerShell object that uses the runspace.
    /// 3. Adding cmdlets to the pipeline of the PowerShell object.
    /// 4. Running the cmdlets synchronously.
    /// 5. Working with PSObject objects to extract properties
    ///    from the objects returned by the cmdlets.
    /// </remarks>
    private static void Main(string[] args)
    {
      Collection<PSObject> result;     // Will hold the result
                                       // of running the cmdlets.

      // Create a runspace. We can not use the RunspaceInvoke class
      // because we need to get at the underlying runspace to
      // explicitly add the commands. Notice that no PSHost object is
      // supplied to the CreateRunspace method so the default host is
      // used. See the Host samples for more information on creating
      // your own custom host.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace())
      {
        myRunSpace.Open();

        // Create a PowerShell object and specify the runspace.
        PowerShell powershell = PowerShell.Create();
        powershell.Runspace = myRunSpace;

        // Use the using statement so we dispose of the PowerShell object
        // when we're done.
        using (powershell)
        {
          // Add the get-process cmdlet to the PowerShell object. Notice
          // we are specify the name of the cmdlet, not a script.
          powershell.AddCommand("get-process");

          // Add the measure-object cmdlet to count the number
          // of objects being returned. Commands are always added to the end
          // of the pipeline.
          powershell.AddCommand("measure-object");

          // Run the cmdlets synchronously and save the objects returned.
          result = powershell.Invoke();
        }

        // Even after disposing of the pipeLine, we still need to set
        // the powershell variable to null so that the garbage collector
        // can clean it up.
        powershell = null;

        // Display the results of running the commands (checking that
        // everything is ok first.
        if (result == null || result.Count != 1)
        {
          throw new InvalidOperationException(
                    "pipeline.Invoke() returned the wrong number of objects");
        }

        PSMemberInfo count = result[0].Properties["Count"];
        if (count == null)
        {
          throw new InvalidOperationException(
                    "The object returned doesn't have a 'count' property");
        }

        Console.WriteLine(
                   "Runspace07: The Get-Process cmdlet returned {0} objects",
                   count.Value);

        // Close the runspace to release any resources.
        myRunSpace.Close();
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="ef43e-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ef43e-115">See Also</span></span>

[<span data-ttu-id="ef43e-116">Pisanie aplikacji hosta programu PowerShell Windows</span><span class="sxs-lookup"><span data-stu-id="ef43e-116">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)