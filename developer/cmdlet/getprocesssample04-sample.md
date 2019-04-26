---
title: GetProcessSample04 Sample | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa2aa4c4-3457-4601-806a-801afe3dcc80
caps.latest.revision: 6
ms.openlocfilehash: 095bebf868efd00f8eeaec979a5606f140714cb1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068032"
---
# <a name="getprocesssample04-sample"></a><span data-ttu-id="99c47-102">Przykład GetProcessSample04</span><span class="sxs-lookup"><span data-stu-id="99c47-102">GetProcessSample04 Sample</span></span>

<span data-ttu-id="99c47-103">Niniejszy przykład pokazuje sposób implementacji polecenia cmdlet, które pobiera procesów na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="99c47-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="99c47-104">Generuje on niekończące błąd, jeśli wystąpi błąd podczas pobierania procesu.</span><span class="sxs-lookup"><span data-stu-id="99c47-104">It generates a nonterminating error if an error occurs while retrieving a process.</span></span> <span data-ttu-id="99c47-105">To polecenie cmdlet jest uproszczoną wersję `Get-Process` polecenia cmdlet, dostarczone przez program Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="99c47-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="99c47-106">Jak skompilować przykład za pomocą programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="99c47-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="99c47-107">Za pomocą Windows PowerShell 2.0 zainstalowany zestaw SDK przejdź do folderu GetProcessSample04.</span><span class="sxs-lookup"><span data-stu-id="99c47-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample04 folder.</span></span> <span data-ttu-id="99c47-108">Domyślna lokalizacja to C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.</span><span class="sxs-lookup"><span data-stu-id="99c47-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.</span></span>

2. <span data-ttu-id="99c47-109">Kliknij dwukrotnie ikonę pliku rozwiązania (.sln).</span><span class="sxs-lookup"><span data-stu-id="99c47-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="99c47-110">Spowoduje to otwarcie z przykładowym projektem w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="99c47-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="99c47-111">W **kompilacji** menu, wybierz opcję **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="99c47-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="99c47-112">Biblioteka dla przykładu, zostanie utworzona w folderze \bin lub \bin\debug domyślny.</span><span class="sxs-lookup"><span data-stu-id="99c47-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="99c47-113">Jak uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="99c47-113">How to run the sample</span></span>

1. <span data-ttu-id="99c47-114">Utwórz następujący folder modułu:</span><span class="sxs-lookup"><span data-stu-id="99c47-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample04`

2. <span data-ttu-id="99c47-115">Skopiuj przykładowy zestaw do folderu modułu.</span><span class="sxs-lookup"><span data-stu-id="99c47-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="99c47-116">Uruchom program Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="99c47-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="99c47-117">Uruchom następujące polecenie, aby załadować zestaw do programu Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="99c47-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `Import-module getprossessample04`

5. <span data-ttu-id="99c47-118">Uruchom następujące polecenie, aby uruchomić polecenie cmdlet:</span><span class="sxs-lookup"><span data-stu-id="99c47-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="99c47-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="99c47-119">Requirements</span></span>

<span data-ttu-id="99c47-120">Ten przykładowy skrypt wymaga programu Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="99c47-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="99c47-121">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="99c47-121">Demonstrates</span></span>

<span data-ttu-id="99c47-122">W przykładzie pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="99c47-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="99c47-123">Deklarowanie klasy polecenia cmdlet przy użyciu atrybutu polecenia Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="99c47-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="99c47-124">Deklarowanie parametrem polecenia cmdlet, za pomocą atrybutu parametru.</span><span class="sxs-lookup"><span data-stu-id="99c47-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="99c47-125">Określanie pozycja parametru.</span><span class="sxs-lookup"><span data-stu-id="99c47-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="99c47-126">Określanie, czy parametr pobiera danych wejściowych z potoku.</span><span class="sxs-lookup"><span data-stu-id="99c47-126">Specifying that the parameter takes input from the pipeline.</span></span> <span data-ttu-id="99c47-127">Dane wejściowe, może zostać pobrany z obiektem lub wartości z właściwości obiektu, którego nazwa właściwości jest taka sama jak nazwa parametru.</span><span class="sxs-lookup"><span data-stu-id="99c47-127">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="99c47-128">Deklarowanie atrybut weryfikacji dla parametrów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="99c47-128">Declaring a validation attribute for the parameter input.</span></span>

- <span data-ttu-id="99c47-129">Generują pułapki niekończące błąd i zapisywanie komunikat o błędzie do strumienia błędów.</span><span class="sxs-lookup"><span data-stu-id="99c47-129">Trapping a nonterminating error and writing an error message to the error stream.</span></span>

## <a name="example"></a><span data-ttu-id="99c47-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="99c47-130">Example</span></span>

<span data-ttu-id="99c47-131">W tym przykładzie przedstawiono sposób tworzenia polecenia cmdlet, które obsługuje błędy niekończące i zapisuje komunikaty o błędach w strumieniu błędów.</span><span class="sxs-lookup"><span data-stu-id="99c47-131">This sample shows how to create a cmdlet that handles nonterminating errors and writes error messages to the error stream.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
    using System;
    using System.Diagnostics;
    using System.Management.Automation;      // Windows PowerShell namespace.
   #region GetProcCommand

   /// <summary>
   /// This class implements the get-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Parameters

       /// <summary>
       /// The names of the processes to act on.
       /// </summary>
       private string[] processNames;

      /// <summary>
      /// Gets or sets the list of process names on
      /// which the Get-Proc cmdlet will work.
      /// </summary>
      [Parameter(
         Position = 0,
         ValueFromPipeline = true,
         ValueFromPipelineByPropertyName = true)]
      [ValidateNotNullOrEmpty]
      public string[] Name
      {
         get { return this.processNames; }
         set { this.processNames = value; }
      }

      #endregion Parameters

      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes specified by the Name
      /// parameter. Then, the WriteObject method writes the
      /// associated processes to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
          // If no process names are passed to cmdlet, get all
          // processes.
          if (this.processNames == null)
          {
              WriteObject(Process.GetProcesses(), true);
          }
          else
          {
              // If process names are passed to the cmdlet, get and write
              // the associated processes.
              // If a nonterminating error occurs while retrieving processes,
              // call the WriteError method to send an error record to the
              // error stream.
              foreach (string name in this.processNames)
              {
                  Process[] processes;

                  try
                  {
                      processes = Process.GetProcessesByName(name);
                  }
                  catch (InvalidOperationException ex)
                  {
                      WriteError(new ErrorRecord(
                         ex,
                         "UnableToAccessProcessByName",
                         ErrorCategory.InvalidOperation,
                         name));
                      continue;
                  }

                  WriteObject(processes, true);
              } // foreach (string name...
          } // else
      } // ProcessRecord

      #endregion Overrides
    } // End GetProcCommand class.

   #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="99c47-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="99c47-132">See Also</span></span>

[<span data-ttu-id="99c47-133">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="99c47-133">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
