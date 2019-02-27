---
title: GetProcessSample02 Sample | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 481f557d-3344-4d33-b2da-4736a0165181
caps.latest.revision: 7
ms.openlocfilehash: fa4cd8a724793e71b615c84a5c5a833aa92c93fc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849511"
---
# <a name="getprocesssample02-sample"></a><span data-ttu-id="3b633-102">Przykład GetProcessSample02</span><span class="sxs-lookup"><span data-stu-id="3b633-102">GetProcessSample02 Sample</span></span>

<span data-ttu-id="3b633-103">Ten przykład pokazuje jak napisać polecenia cmdlet, które pobiera procesów na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="3b633-103">This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="3b633-104">Zapewnia `Name` parametr, który może służyć do określania procesy, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="3b633-104">It provides a `Name` parameter that can be used to specify the processes to be retrieved.</span></span> <span data-ttu-id="3b633-105">To polecenie cmdlet jest uproszczoną wersję `Get-Process` polecenia cmdlet, dostarczone przez program Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="3b633-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="3b633-106">Jak skompilować przykład za pomocą programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3b633-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="3b633-107">Za pomocą Windows PowerShell 2.0 zainstalowany zestaw SDK przejdź do folderu GetProcessSample02.</span><span class="sxs-lookup"><span data-stu-id="3b633-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample02 folder.</span></span> <span data-ttu-id="3b633-108">Domyślna lokalizacja to C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.</span><span class="sxs-lookup"><span data-stu-id="3b633-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.</span></span>

2. <span data-ttu-id="3b633-109">Kliknij dwukrotnie ikonę pliku rozwiązania (.sln).</span><span class="sxs-lookup"><span data-stu-id="3b633-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="3b633-110">Spowoduje to otwarcie z przykładowym projektem w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3b633-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="3b633-111">W **kompilacji** menu, wybierz opcję **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="3b633-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="3b633-112">Biblioteka dla przykładu, zostanie utworzona w folderze \bin lub \bin\debug domyślny.</span><span class="sxs-lookup"><span data-stu-id="3b633-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="3b633-113">Jak uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="3b633-113">How to run the sample</span></span>

1. <span data-ttu-id="3b633-114">Utwórz następujący folder modułu:</span><span class="sxs-lookup"><span data-stu-id="3b633-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample02`

2. <span data-ttu-id="3b633-115">Skopiuj przykładowy zestaw do folderu modułu.</span><span class="sxs-lookup"><span data-stu-id="3b633-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="3b633-116">Uruchom program Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3b633-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="3b633-117">Uruchom następujące polecenie, aby załadować zestaw do programu Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="3b633-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `import-module getprossessample02`

5. <span data-ttu-id="3b633-118">Uruchom następujące polecenie, aby uruchomić polecenie cmdlet:</span><span class="sxs-lookup"><span data-stu-id="3b633-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="3b633-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3b633-119">Requirements</span></span>

<span data-ttu-id="3b633-120">Ten przykładowy skrypt wymaga programu Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="3b633-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="3b633-121">Przedstawiono</span><span class="sxs-lookup"><span data-stu-id="3b633-121">Demonstrates</span></span>

<span data-ttu-id="3b633-122">W przykładzie pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="3b633-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="3b633-123">Deklarowanie klasy polecenia cmdlet przy użyciu atrybutu polecenia Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3b633-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="3b633-124">Deklarowanie parametrem polecenia cmdlet, za pomocą atrybutu parametru.</span><span class="sxs-lookup"><span data-stu-id="3b633-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="3b633-125">Określanie pozycja parametru.</span><span class="sxs-lookup"><span data-stu-id="3b633-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="3b633-126">Deklarowanie atrybut weryfikacji dla parametrów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="3b633-126">Declaring a validation attribute for the parameter input.</span></span>

## <a name="example"></a><span data-ttu-id="3b633-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="3b633-127">Example</span></span>

<span data-ttu-id="3b633-128">W tym przykładzie pokazano implementację polecenia cmdlet Get-Proc, które obejmuje `Name` parametru.</span><span class="sxs-lookup"><span data-stu-id="3b633-128">This sample shows an implementation of the Get-Proc cmdlet that includes a `Name` parameter.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;     // Windows PowerShell namespace

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
    /// Gets or sets the list of process names on which
    /// the Get-Proc cmdlet will work.
    /// </summary>
    [Parameter(Position = 0)]
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
    /// associated process objects to the pipeline.
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
        // If process names are passed to cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames...).
    } // End ProcessRecord.
    #endregion Cmdlet Overrides
  } // End GetProcCommand class.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="3b633-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3b633-129">See Also</span></span>

[<span data-ttu-id="3b633-130">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3b633-130">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
