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
# <a name="getprocesssample02-sample"></a>Przykład GetProcessSample02

Ten przykład pokazuje jak napisać polecenia cmdlet, które pobiera procesów na komputerze lokalnym. Zapewnia `Name` parametr, który może służyć do określania procesy, które mają zostać pobrane. To polecenie cmdlet jest uproszczoną wersję `Get-Process` polecenia cmdlet, dostarczone przez program Windows PowerShell 2.0.

## <a name="how-to-build-the-sample-using-visual-studio"></a>Jak skompilować przykład za pomocą programu Visual Studio.

1. Za pomocą Windows PowerShell 2.0 zainstalowany zestaw SDK przejdź do folderu GetProcessSample02. Domyślna lokalizacja to C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.

2. Kliknij dwukrotnie ikonę pliku rozwiązania (.sln). Spowoduje to otwarcie z przykładowym projektem w programie Visual Studio.

3. W **kompilacji** menu, wybierz opcję **Kompiluj rozwiązanie**.

    Biblioteka dla przykładu, zostanie utworzona w folderze \bin lub \bin\debug domyślny.

### <a name="how-to-run-the-sample"></a>Jak uruchomić przykład

1. Utwórz następujący folder modułu:

    `[user]/documents/windowspowershell/modules/GetProcessSample02`

2. Skopiuj przykładowy zestaw do folderu modułu.

3. Uruchom program Windows PowerShell.

4. Uruchom następujące polecenie, aby załadować zestaw do programu Windows PowerShell:

    `import-module getprossessample02`

5. Uruchom następujące polecenie, aby uruchomić polecenie cmdlet:

    `get-proc`

## <a name="requirements"></a>Wymagania

Ten przykładowy skrypt wymaga programu Windows PowerShell 2.0.

## <a name="demonstrates"></a>Przedstawiono

W przykładzie pokazano poniżej.

- Deklarowanie klasy polecenia cmdlet przy użyciu atrybutu polecenia Cmdlet.

- Deklarowanie parametrem polecenia cmdlet, za pomocą atrybutu parametru.

- Określanie pozycja parametru.

- Deklarowanie atrybut weryfikacji dla parametrów wejściowych.

## <a name="example"></a>Przykład

W tym przykładzie pokazano implementację polecenia cmdlet Get-Proc, które obejmuje `Name` parametru.

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

## <a name="see-also"></a>Zobacz też

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
