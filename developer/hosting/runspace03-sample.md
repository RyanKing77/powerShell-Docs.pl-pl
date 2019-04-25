---
title: Przykładowe Runspace03 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 31df99d7-6954-4fdc-b6f5-06ecba094f43
caps.latest.revision: 8
ms.openlocfilehash: 39495f7813aecf5d0210866fc11f94557fdb0cd9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082621"
---
# <a name="runspace03-sample"></a><span data-ttu-id="e10b8-102">Przykład Runspace03</span><span class="sxs-lookup"><span data-stu-id="e10b8-102">Runspace03 Sample</span></span>

<span data-ttu-id="e10b8-103">Ten przykład ilustruje sposób używania [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) klasy, aby uruchomić skrypt synchronicznie i sposób obsługi błędy niepowodujące.</span><span class="sxs-lookup"><span data-stu-id="e10b8-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run a script synchronously, and how to handle non-terminating errors.</span></span> <span data-ttu-id="e10b8-104">Skrypt otrzymuje listę nazw procesu, a następnie pobierze te procesy.</span><span class="sxs-lookup"><span data-stu-id="e10b8-104">The script receives a list of process names and then retrieves those processes.</span></span> <span data-ttu-id="e10b8-105">Wyniki skryptu, między innymi niepowodujące błędy, które zostały wygenerowane podczas uruchamiania skryptu, są wyświetlane w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="e10b8-105">The results of the script, including any non-terminating errors that were generated when running the script, are displayed in a console window.</span></span>

## <a name="requirements"></a><span data-ttu-id="e10b8-106">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e10b8-106">Requirements</span></span>

<span data-ttu-id="e10b8-107">Ten przykładowy skrypt wymaga programu Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="e10b8-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="e10b8-108">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="e10b8-108">Demonstrates</span></span>

<span data-ttu-id="e10b8-109">W przykładzie pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="e10b8-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="e10b8-110">Tworzenie [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) obiektu, aby uruchomić skrypt.</span><span class="sxs-lookup"><span data-stu-id="e10b8-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run a script.</span></span>

- <span data-ttu-id="e10b8-111">Dodawanie skryptu do potoku [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) obiektu.</span><span class="sxs-lookup"><span data-stu-id="e10b8-111">Adding a script to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="e10b8-112">Przekazywanie danych wejściowych obiektów do skryptu z program wywołujący.</span><span class="sxs-lookup"><span data-stu-id="e10b8-112">Passing input objects to the script from the calling program.</span></span>

- <span data-ttu-id="e10b8-113">Uruchomienie skryptu synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="e10b8-113">Running the script synchronously.</span></span>

- <span data-ttu-id="e10b8-114">Za pomocą [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) obiektów, aby wyodrębnić i wyświetlić właściwości z obiektów zwróconych przez skrypt.</span><span class="sxs-lookup"><span data-stu-id="e10b8-114">Using [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects to extract and display properties from the objects returned by the script.</span></span>

- <span data-ttu-id="e10b8-115">Pobieranie i wyświetlanie rekordów błędów, które zostały wygenerowane, gdy skrypt był uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="e10b8-115">Retrieving and displaying error records that were generated when the script was run.</span></span>

## <a name="example"></a><span data-ttu-id="e10b8-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="e10b8-116">Example</span></span>

<span data-ttu-id="e10b8-117">W tym przykładzie uruchamia skrypt synchronicznie, w obszarze działania domyślne, dostarczone przez środowisko Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e10b8-117">This sample runs a script synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="e10b8-118">Dane wyjściowe skryptu i, które zostały wygenerowane błędy niepowodujące są wyświetlane w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="e10b8-118">The output of the script and any non-terminating errors that were generated are displayed in a console window.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace03
  {
    /// <summary>
    /// This sample shows how to use the PowerShell class to run a
    /// script that retrieves process information for the list of
    /// process names passed to the script. It shows how to pass input
    /// objects to a script and how to retrieve error objects as well
    /// as the output objects.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerSHell object to run a script.
    /// 2. Adding a script to the pipeline of the PowerShell object.
    /// 3. Passing input objects to the script from the calling program.
    /// 4. Running the script synchronously.
    /// 5. Using PSObject objects to extract and display properties from
    ///    the objects returned by the script.
    /// 6. Retrieving and displaying error records that were generated
    ///    when the script was run.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Define a list of processes to look for.
      string[] processNames = new string[]
      {
        "lsass", "nosuchprocess", "services", "nosuchprocess2"
      };

      // The script to run to get these processes. Input passed
      // to the script will be available in the $input variable.
      string script = "$input | get-process -name {$_}";

      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the script.
      using (PowerShell powershell = PowerShell.Create())
      {
        powershell.AddScript(script);

        Console.WriteLine("Process              HandleCount");
        Console.WriteLine("--------------------------------");

        // Invoke the script synchronously and display the
        // ProcessName and HandleCount properties of the
        // objects that are returned.
        foreach (PSObject result in powershell.Invoke(processNames))
        {
          Console.WriteLine(
                            "{0,-20} {1}",
                            result.Members["ProcessName"].Value,
                            result.Members["HandleCount"].Value);
        }

        // Process any error records that were generated while running
        //  the script.
        Console.WriteLine("\nThe following non-terminating errors occurred:\n");
        PSDataCollection<ErrorRecord> errors = powershell.Streams.Error;
        if (errors != null && errors.Count > 0)
        {
          foreach (ErrorRecord err in errors)
          {
            System.Console.WriteLine("    error: {0}", err.ToString());
          }
        }
      }

      System.Console.WriteLine("\nHit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="e10b8-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e10b8-119">See Also</span></span>

[<span data-ttu-id="e10b8-120">Pisanie aplikacji hosta programu PowerShell Windows</span><span class="sxs-lookup"><span data-stu-id="e10b8-120">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)