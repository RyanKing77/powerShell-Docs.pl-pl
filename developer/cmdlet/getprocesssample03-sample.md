---
title: GetProcessSample03 Sample | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc9d80ee-6ebd-48cd-a7ea-53cb2b442a22
caps.latest.revision: 6
ms.openlocfilehash: ec5a8c284dd3fa772261099281aba1fb68c49118
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847145"
---
# <a name="getprocesssample03-sample"></a><span data-ttu-id="bb478-102">Przykład GetProcessSample03</span><span class="sxs-lookup"><span data-stu-id="bb478-102">GetProcessSample03 Sample</span></span>

<span data-ttu-id="bb478-103">Niniejszy przykład pokazuje sposób implementacji polecenia cmdlet, które pobiera procesów na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="bb478-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="bb478-104">Zapewnia `Name` parametr, który może akceptować wartości z właściwości obiektu, którego nazwa właściwości jest taka sama jak nazwa parametru lub obiektu z potoku.</span><span class="sxs-lookup"><span data-stu-id="bb478-104">It provides a `Name` parameter that can accept an object from the pipeline or a value from a property of an object whose property name is the same as the parameter name.</span></span> <span data-ttu-id="bb478-105">To polecenie cmdlet jest uproszczoną wersję `Get-Process` polecenia cmdlet, dostarczone przez program Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="bb478-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="bb478-106">Jak skompilować przykład za pomocą programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bb478-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="bb478-107">Za pomocą Windows PowerShell 2.0 zainstalowany zestaw SDK przejdź do folderu GetProcessSample03.</span><span class="sxs-lookup"><span data-stu-id="bb478-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample03 folder.</span></span> <span data-ttu-id="bb478-108">Domyślna lokalizacja to C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03.</span><span class="sxs-lookup"><span data-stu-id="bb478-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03.</span></span>

2. <span data-ttu-id="bb478-109">Kliknij dwukrotnie ikonę pliku rozwiązania (.sln).</span><span class="sxs-lookup"><span data-stu-id="bb478-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="bb478-110">Spowoduje to otwarcie z przykładowym projektem w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bb478-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="bb478-111">W **kompilacji** menu, wybierz opcję **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="bb478-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="bb478-112">Biblioteka dla przykładu, zostanie utworzona w folderze \bin lub \bin\debug domyślny.</span><span class="sxs-lookup"><span data-stu-id="bb478-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="bb478-113">Jak uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="bb478-113">How to run the sample</span></span>

1. <span data-ttu-id="bb478-114">Utwórz następujący folder modułu:</span><span class="sxs-lookup"><span data-stu-id="bb478-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample03`

2. <span data-ttu-id="bb478-115">Skopiuj przykładowy zestaw do folderu modułu.</span><span class="sxs-lookup"><span data-stu-id="bb478-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="bb478-116">Uruchom program Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bb478-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="bb478-117">Uruchom następujące polecenie, aby załadować zestaw do programu Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="bb478-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `Import-module getprossessample03`

5. <span data-ttu-id="bb478-118">Uruchom następujące polecenie, aby uruchomić polecenie cmdlet:</span><span class="sxs-lookup"><span data-stu-id="bb478-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="bb478-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bb478-119">Requirements</span></span>

<span data-ttu-id="bb478-120">Ten przykładowy skrypt wymaga programu Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="bb478-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="bb478-121">Przedstawiono</span><span class="sxs-lookup"><span data-stu-id="bb478-121">Demonstrates</span></span>

<span data-ttu-id="bb478-122">W przykładzie pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="bb478-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="bb478-123">Deklarowanie klasy polecenia cmdlet przy użyciu atrybutu polecenia Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bb478-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="bb478-124">Deklarowanie parametrem polecenia cmdlet, za pomocą atrybutu parametru.</span><span class="sxs-lookup"><span data-stu-id="bb478-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="bb478-125">Określanie pozycja parametru.</span><span class="sxs-lookup"><span data-stu-id="bb478-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="bb478-126">Określanie, czy parametr pobiera danych wejściowych z potoku.</span><span class="sxs-lookup"><span data-stu-id="bb478-126">Specifying that the parameter takes input from the pipeline.</span></span> <span data-ttu-id="bb478-127">Dane wejściowe, może zostać pobrany z obiektem lub wartości z właściwości obiektu, którego nazwa właściwości jest taka sama jak nazwa parametru.</span><span class="sxs-lookup"><span data-stu-id="bb478-127">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="bb478-128">Deklarowanie atrybut weryfikacji dla parametrów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="bb478-128">Declaring a validation attribute for the parameter input.</span></span>

## <a name="example"></a><span data-ttu-id="bb478-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="bb478-129">Example</span></span>

<span data-ttu-id="bb478-130">W tym przykładzie pokazano implementację polecenia cmdlet Get-Proc, które obejmuje `Name` parametr, który akceptuje dane wejściowe z potoku.</span><span class="sxs-lookup"><span data-stu-id="bb478-130">This sample shows an implementation of the Get-Proc cmdlet that includes a `Name` parameter that accepts input from the pipeline.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;           // Windows PowerShell namespace
  #region GetProcCommand

  /// <summary>
  /// This class implements the get-proc cmdlet.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Parameters

    /// <summary>
    /// The names of the processes retrieved by the cmdlet.
    /// </summary>
    private string[] processNames;

    /// <summary>
    /// Gets or sets the names of the
    /// process that the cmdlet will retrieve.
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
      // If no process names are passed to the cmdlet, get all
      // processes.
      if (this.processNames == null)
      {
        WriteObject(Process.GetProcesses(), true);
      }
      else
      {
        // If process names are passed to the cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames ...)
    } // End ProcessRecord.

    #endregion Overrides
  } // End GetProcCommand.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="bb478-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bb478-131">See Also</span></span>

[<span data-ttu-id="bb478-132">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="bb478-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
