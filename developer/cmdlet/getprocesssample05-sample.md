---
title: GetProcessSample05 Sample | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6aebd53f-0610-4959-88b2-42339588c859
caps.latest.revision: 6
ms.openlocfilehash: ad4300937c10652b677346a62c42fa4f6e8513cf
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056002"
---
# <a name="getprocesssample05-sample"></a><span data-ttu-id="85ad8-102">Przykład GetProcessSample05</span><span class="sxs-lookup"><span data-stu-id="85ad8-102">GetProcessSample05 Sample</span></span>

<span data-ttu-id="85ad8-103">Niniejszy przykład pokazuje pełną wersję polecenia cmdlet Get-Proc.</span><span class="sxs-lookup"><span data-stu-id="85ad8-103">This sample shows a complete version of the Get-Proc cmdlet.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="85ad8-104">Jak skompilować przykład za pomocą programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="85ad8-104">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="85ad8-105">Otwórz Eksploratora Windows i przejdź do katalogu GetProcessSample05 w katalogu przykładów.</span><span class="sxs-lookup"><span data-stu-id="85ad8-105">Open Windows Explorer and navigate to the GetProcessSample05 directory under the Samples directory.</span></span>

   <span data-ttu-id="85ad8-106">Za pomocą Windows PowerShell 2.0 zainstalowany zestaw SDK przejdź do folderu GetProcessSample05.</span><span class="sxs-lookup"><span data-stu-id="85ad8-106">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample05 folder.</span></span> <span data-ttu-id="85ad8-107">Domyślna lokalizacja to C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample05.</span><span class="sxs-lookup"><span data-stu-id="85ad8-107">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample05.</span></span>

2. <span data-ttu-id="85ad8-108">Kliknij dwukrotnie ikonę pliku rozwiązania (.sln).</span><span class="sxs-lookup"><span data-stu-id="85ad8-108">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="85ad8-109">Spowoduje to otwarcie z przykładowym projektem w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="85ad8-109">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="85ad8-110">W **kompilacji** menu, wybierz opcję **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="85ad8-110">In the **Build** menu, select **Build Solution**.</span></span>

   <span data-ttu-id="85ad8-111">Biblioteka dla przykładu, zostanie utworzona w katalogach \bin lub \bin\debug domyślny.</span><span class="sxs-lookup"><span data-stu-id="85ad8-111">The library for the sample will be built in the default \bin or \bin\debug directories.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="85ad8-112">Jak uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="85ad8-112">How to run the sample</span></span>

1. <span data-ttu-id="85ad8-113">Utwórz następujący folder modułu:</span><span class="sxs-lookup"><span data-stu-id="85ad8-113">Create the following module folder:</span></span>

   `[user]/documents/windowspowershell/modules/GetProcessSample05`

2. <span data-ttu-id="85ad8-114">Skopiuj przykładowy zestaw do folderu modułu.</span><span class="sxs-lookup"><span data-stu-id="85ad8-114">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="85ad8-115">Uruchom program Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="85ad8-115">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="85ad8-116">Uruchom następujące polecenie, aby załadować zestaw do programu Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="85ad8-116">Run the following command to load the assembly into Windows PowerShell:</span></span>

   `Import-module getprossessample05`

5. <span data-ttu-id="85ad8-117">Uruchom następujące polecenie, aby uruchomić polecenie cmdlet:</span><span class="sxs-lookup"><span data-stu-id="85ad8-117">Run the following command to run the cmdlet:</span></span>

   `get-proc`

## <a name="requirements"></a><span data-ttu-id="85ad8-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="85ad8-118">Requirements</span></span>

<span data-ttu-id="85ad8-119">Ten przykładowy skrypt wymaga programu Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="85ad8-119">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="85ad8-120">Przedstawiono</span><span class="sxs-lookup"><span data-stu-id="85ad8-120">Demonstrates</span></span>

<span data-ttu-id="85ad8-121">W przykładzie pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="85ad8-121">This sample demonstrates the following.</span></span>

- <span data-ttu-id="85ad8-122">Deklarowanie klasy polecenia cmdlet przy użyciu atrybutu polecenia Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="85ad8-122">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="85ad8-123">Deklarowanie parametrem polecenia cmdlet, za pomocą atrybutu parametru.</span><span class="sxs-lookup"><span data-stu-id="85ad8-123">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="85ad8-124">Określanie pozycje dla parametrów.</span><span class="sxs-lookup"><span data-stu-id="85ad8-124">Specifying positions for parameters.</span></span>

- <span data-ttu-id="85ad8-125">Określenie, czy parametry mogą zajmować danych wejściowych z potoku.</span><span class="sxs-lookup"><span data-stu-id="85ad8-125">Specifying that parameters can take input from the pipeline.</span></span> <span data-ttu-id="85ad8-126">Dane wejściowe, może zostać pobrany z obiektem lub wartości z właściwości obiektu, którego nazwa właściwości jest taka sama jak nazwa parametru.</span><span class="sxs-lookup"><span data-stu-id="85ad8-126">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="85ad8-127">Deklarowanie atrybut weryfikacji dla parametrów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="85ad8-127">Declaring a validation attribute for the parameter input.</span></span>

- <span data-ttu-id="85ad8-128">Obsługa błędów i wyjątków.</span><span class="sxs-lookup"><span data-stu-id="85ad8-128">Handling errors and exceptions.</span></span>

- <span data-ttu-id="85ad8-129">Zapisywanie komunikatów debugowania.</span><span class="sxs-lookup"><span data-stu-id="85ad8-129">Writing debug messages.</span></span>

## <a name="example"></a><span data-ttu-id="85ad8-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="85ad8-130">Example</span></span>

<span data-ttu-id="85ad8-131">W tym przykładzie przedstawiono sposób tworzenia polecenia cmdlet, które wyświetla listę określonych procesów.</span><span class="sxs-lookup"><span data-stu-id="85ad8-131">This sample shows how to create a cmdlet that displays a list of specified processes.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
    using System;
    using System.Collections.Generic;
    using System.Diagnostics;
    using System.Management.Automation;    // Windows PowerShell namespace.
    using System.Security.Permissions;
    using Win32Exception = System.ComponentModel.Win32Exception;
    #region GetProcCommand

    /// <summary>
   /// This class implements the get-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc",
      DefaultParameterSetName = "ProcessName")]
   public class GetProcCommand : PSCmdlet
   {
       #region Fields
       /// <summary>
       /// The names of the processes to act on.
       /// </summary>
       private string[] processNames;

       /// <summary>
       /// The identifiers of the processes to act on.
       /// </summary>
       private int[] processIds;

       /// <summary>
       /// The process objects to act on.
       /// </summary>
       private Process[] inputObjects;

       #endregion Fields

       #region Parameters

      /// <summary>
      /// Gets or sets the list of process names on
      /// which the Get-Proc cmdlet will work.
      /// </summary>
      [Parameter(
         Position = 0,
         ParameterSetName = "ProcessName",
         ValueFromPipeline = true,
         ValueFromPipelineByPropertyName = true)]
      [ValidateNotNullOrEmpty]
      public string[] Name
      {
         get { return this.processNames; }
         set { this.processNames = value; }
      }

      /// <summary>
      /// Gets or sets the list of process identifiers on
      /// which the Get-Proc cmdlet will work.
      /// </summary>
      [Parameter(
         ParameterSetName = "Id",
         Mandatory = true,
         ValueFromPipeline = true,
         ValueFromPipelineByPropertyName = true,
         HelpMessage = "The unique id of the process to get.")]
      public int[] Id
      {
         get { return this.processIds; }
         set { this.processIds = value; }
      }

      /// <summary>
      /// Gets or sets Process objects directly. If the input is a
      /// stream of [collection of] Process objects, the cmdlet bypasses the
      /// ProcessName and Id parameters and reads the Process objects
      /// directly.  This allows the cmdlet to deal with processes that have
      /// wildcard characters in their name.
      /// <value>Process objects</value>
      /// </summary>
      [Parameter(
         ParameterSetName = "InputObject",
         Mandatory = true,
         ValueFromPipeline = true)]
      public Process[] Input
      {
         get { return this.inputObjects; }
         set { this.inputObjects = value; }
      }

      #endregion Parameters

      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes. Then, the WriteObject
      /// method writes the associated processes to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
         List<Process> matchingProcesses;

         WriteDebug("Obtaining the list of matching process objects.");

         switch (ParameterSetName)
         {
            case "Id":
               matchingProcesses = this.GetMatchingProcessesById();
               break;
            case "ProcessName":
               matchingProcesses = this.GetMatchingProcessesByName();
               break;
            case "InputObject":
               matchingProcesses = this.GetProcessesByInput();
               break;
            default:
               ThrowTerminatingError(
                   new ErrorRecord(
                       new ArgumentException("Bad ParameterSetName"),
                       "UnableToAccessProcessList",
                       ErrorCategory.InvalidOperation,
                       null));
               return;
         } // switch (ParameterSetName)

         WriteDebug("Outputting the matching process objects.");

         matchingProcesses.Sort(ProcessComparison);

         foreach (Process process in matchingProcesses)
         {
            WriteObject(process);
         }
      } // ProcessRecord

      #endregion Overrides

      #region protected Methods and Data

      /// <summary>
      /// Retrieves the list of all processes matching the ProcessName
      /// parameter and generates a nonterminating error for each
      /// specified process name which is not found even though the name
      /// contains no wildcards.
      /// </summary>
      /// <returns>The matching processes.</returns>
      [EnvironmentPermissionAttribute(
         SecurityAction.LinkDemand,
         Unrestricted = true)]
      private List<Process> GetMatchingProcessesByName()
      {
         new EnvironmentPermission(
            PermissionState.Unrestricted).Assert();

         List<Process> allProcesses =
            new List<Process>(Process.GetProcesses());

         // The keys dictionary is used for rapid lookup of
         // processes that are already in the matchingProcesses list.
         Dictionary<int, byte> keys = new Dictionary<int, byte>();

         List<Process> matchingProcesses = new List<Process>();

         if (null == this.processNames)
         {
             matchingProcesses.AddRange(allProcesses);
         }
         else
         {
             foreach (string pattern in this.processNames)
             {
                 WriteVerbose("Finding matches for process name \""
                    + pattern + "\".");

                 // WildCard search on the available processes
                 WildcardPattern wildcard =
                    new WildcardPattern(
                        pattern,
                        WildcardOptions.IgnoreCase);

                 bool found = false;

                 foreach (Process process in allProcesses)
                 {
                     if (!keys.ContainsKey(process.Id))
                     {
                         string processName = SafeGetProcessName(process);

                         // Remove the process from the allProcesses list
                         // so that it is not tested again.
                         if (processName.Length == 0)
                         {
                             allProcesses.Remove(process);
                         }

                         // Perform a wildcard search on this particular
                         // process name and check whether it matches the
                         // pattern specified.
                         if (!wildcard.IsMatch(processName))
                         {
                             continue;
                         }

                         WriteDebug("Found matching process id "
                            + process.Id + ".");

                         // A match is found.
                         found = true;

                         // Store the process identifier so that the same process
                         // is not added twice.
                         keys.Add(process.Id, 0);

                         // Add the process to the processes list.
                         matchingProcesses.Add(process);
                     }
                 } // foreach (Process...

                 if (!found &&
                   !WildcardPattern.ContainsWildcardCharacters(pattern))
                 {
                     WriteError(new ErrorRecord(
                        new ArgumentException("Cannot find process name "
                           + "\"" + pattern + "\"."),
                        "ProcessNameNotFound",
                        ErrorCategory.ObjectNotFound,
                        pattern));
                 }
             } // foreach (string...
         } // if (null...

         return matchingProcesses;
      } // GetMatchingProcessesByName

      /// <summary>
      /// Returns the name of a process.  If an error occurs, a blank
      /// string is returned.
      /// </summary>
      /// <param name="process">The process whose name is
      /// returned.</param>
      /// <returns>The name of the process.</returns>
      [EnvironmentPermissionAttribute(
         SecurityAction.LinkDemand, Unrestricted = true)]
      protected static string SafeGetProcessName(Process process)
      {
         new EnvironmentPermission(PermissionState.Unrestricted).Assert();
         string name = String.Empty;

         if (process != null)
         {
            try
            {
                return process.ProcessName;
            }
            catch (Win32Exception)
            {
            }
            catch (InvalidOperationException)
            {
            }
         }

         return name;
     } // SafeGetProcessName

      #endregion Cmdlet Overrides

      #region Private Methods

      /// <summary>
      /// Function to sort by process name first, and then by
      /// the process identifier.
      /// </summary>
      /// <param name="x">First process object.</param>
      /// <param name="y">Second process object.</param>
      /// <returns>
      /// Returns less than zero if x is less than y,
      /// greater than 0 if x is greater than y, and 0 if x == y.
      /// </returns>
      private static int ProcessComparison(Process x, Process y)
      {
         int diff = String.Compare(
            SafeGetProcessName(x),
            SafeGetProcessName(y),
            StringComparison.CurrentCultureIgnoreCase);

         if (0 != diff)
         {
             return diff;
         }
         else
         {
             return x.Id.CompareTo(y.Id);
         }
      }

      /// <summary>
      /// Retrieves the list of all processes matching the Id
      /// parameter and generates a nonterminating error for
      /// each specified process identifier which is not found.
      /// </summary>
      /// <returns>
      /// An array of processes that match the given identifier.
      /// </returns>
      [EnvironmentPermissionAttribute(
         SecurityAction.LinkDemand,
         Unrestricted = true)]
      private List<Process> GetMatchingProcessesById()
      {
         new EnvironmentPermission(
            PermissionState.Unrestricted).Assert();

         List<Process> matchingProcesses = new List<Process>();

         if (null != this.processIds)
         {
            // The keys dictionary is used for rapid lookup of the
            // processes already in the matchingProcesses list.
            Dictionary<int, byte> keys = new Dictionary<int, byte>();

            foreach (int processId in this.processIds)
            {
               WriteVerbose("Finding match for process id "
                  + processId + ".");

               if (!keys.ContainsKey(processId))
               {
                  Process process;
                  try
                  {
                      process = Process.GetProcessById(processId);
                  }
                  catch (ArgumentException ex)
                  {
                     WriteError(new ErrorRecord(
                        ex,
                        "ProcessIdNotFound",
                        ErrorCategory.ObjectNotFound,
                        processId));
                     continue;
                  }

                  WriteDebug("Found matching process.");

                  matchingProcesses.Add(process);
                  keys.Add(processId, 0);
               }
            }
         }

         return matchingProcesses;
      } // GetMatchingProcessesById

      /// <summary>
      /// Retrieves the list of all processes matching the InputObject
      /// parameter.
      /// </summary>
      /// <returns>The matching processes.</returns>
      [EnvironmentPermissionAttribute(
         SecurityAction.LinkDemand,
         Unrestricted = true)]
      private List<Process> GetProcessesByInput()
      {
         new EnvironmentPermission(
            PermissionState.Unrestricted).Assert();

         List<Process> matchingProcesses = new List<Process>();

         if (null != this.Input)
         {
            // The keys dictionary is used for rapid lookup of the
            // processes already in the matchingProcesses list.
            Dictionary<int, byte> keys = new Dictionary<int, byte>();

            foreach (Process process in this.Input)
            {
               WriteVerbose("Refreshing process object.");

               if (!keys.ContainsKey(process.Id))
               {
                  try
                  {
                      process.Refresh();
                  }
                  catch (Win32Exception)
                  {
                  }
                  catch (InvalidOperationException)
                  {
                  }

                  matchingProcesses.Add(process);
               }
            }
         }

         return matchingProcesses;
      } // GetProcessesByInput
      #endregion Private Methods
    } // End GetProcCommand class.

    #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="85ad8-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="85ad8-132">See Also</span></span>

[<span data-ttu-id="85ad8-133">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="85ad8-133">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
