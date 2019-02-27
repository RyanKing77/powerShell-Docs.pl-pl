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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850925"
---
# <a name="getprocesssample04-sample"></a>Przykład GetProcessSample04

Niniejszy przykład pokazuje sposób implementacji polecenia cmdlet, które pobiera procesów na komputerze lokalnym. Generuje on niekończące błąd, jeśli wystąpi błąd podczas pobierania procesu. To polecenie cmdlet jest uproszczoną wersję `Get-Process` polecenia cmdlet, dostarczone przez program Windows PowerShell 2.0.

## <a name="how-to-build-the-sample-using-visual-studio"></a>Jak skompilować przykład za pomocą programu Visual Studio.

1. Za pomocą Windows PowerShell 2.0 zainstalowany zestaw SDK przejdź do folderu GetProcessSample04. Domyślna lokalizacja to C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.

2. Kliknij dwukrotnie ikonę pliku rozwiązania (.sln). Spowoduje to otwarcie z przykładowym projektem w programie Visual Studio.

3. W **kompilacji** menu, wybierz opcję **Kompiluj rozwiązanie**.

    Biblioteka dla przykładu, zostanie utworzona w folderze \bin lub \bin\debug domyślny.

### <a name="how-to-run-the-sample"></a>Jak uruchomić przykład

1. Utwórz następujący folder modułu:

    `[user]/documents/windowspowershell/modules/GetProcessSample04`

2. Skopiuj przykładowy zestaw do folderu modułu.

3. Uruchom program Windows PowerShell.

4. Uruchom następujące polecenie, aby załadować zestaw do programu Windows PowerShell:

    `Import-module getprossessample04`

5. Uruchom następujące polecenie, aby uruchomić polecenie cmdlet:

    `get-proc`

## <a name="requirements"></a>Wymagania

Ten przykładowy skrypt wymaga programu Windows PowerShell 2.0.

## <a name="demonstrates"></a>Przedstawiono

W przykładzie pokazano poniżej.

- Deklarowanie klasy polecenia cmdlet przy użyciu atrybutu polecenia Cmdlet.

- Deklarowanie parametrem polecenia cmdlet, za pomocą atrybutu parametru.

- Określanie pozycja parametru.

- Określanie, czy parametr pobiera danych wejściowych z potoku. Dane wejściowe, może zostać pobrany z obiektem lub wartości z właściwości obiektu, którego nazwa właściwości jest taka sama jak nazwa parametru.

- Deklarowanie atrybut weryfikacji dla parametrów wejściowych.

- Generują pułapki niekończące błąd i zapisywanie komunikat o błędzie do strumienia błędów.

## <a name="example"></a>Przykład

W tym przykładzie przedstawiono sposób tworzenia polecenia cmdlet, które obsługuje błędy niekończące i zapisuje komunikaty o błędach w strumieniu błędów.

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

## <a name="see-also"></a>Zobacz też

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
