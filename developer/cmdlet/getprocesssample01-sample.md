---
title: GetProcessSample01 Sample | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b48bf80-cbf0-4cb1-8d5b-3b8d06196598
caps.latest.revision: 10
ms.openlocfilehash: 00190c7350cb0f1cfc5c389b56e48e9397480446
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849497"
---
# <a name="getprocesssample01-sample"></a>Przykład GetProcessSample01

Niniejszy przykład pokazuje sposób implementacji polecenia cmdlet, które pobiera procesów na komputerze lokalnym. To polecenie cmdlet jest uproszczoną wersję `Get-Process` polecenia cmdlet, które są dostarczane przez program Windows PowerShell 2.0.

## <a name="how-to-build-the-sample-by-using-visual-studio"></a>Jak skompilować przykład za pomocą programu Visual Studio.

1. Za pomocą Windows PowerShell 2.0 zainstalowany zestaw SDK przejdź do folderu GetProcessSample01. Domyślna lokalizacja to C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.

2. Kliknij dwukrotnie ikonę pliku rozwiązania (.sln). Spowoduje to otwarcie z przykładowym projektem w programie Microsoft Visual Studio.

3. W **kompilacji** menu, wybierz opcję **Kompiluj rozwiązanie**.

  Biblioteka dla przykładu, zostanie utworzona w folderze \bin lub \bin\debug domyślny.

### <a name="how-to-run-the-sample"></a>Jak uruchomić przykład

1. Otwórz wiersz polecenia.

2. Przejdź do katalogu zawierającego przykładowy plik .dll.

3. Run installutil "GetProcessSample01.dll".

4. Uruchom program Windows PowerShell.

5. Uruchom następujące polecenie, aby dodać przystawkę powłoki.

   `Add-PSSnapin GetProcPSSnapIn01`

6. Wprowadź następujące polecenie, aby uruchomić polecenie cmdlet. `get-proc`

   `get-proc`

   To przykładowe dane wyjściowe, będącą wynikiem, wykonaj następujące kroki.

   ```output
   Id              Name            State      HasMoreData     Location             Command
   --              ----            -----      -----------     --------             -------
   1               26932870-d3b... NotStarted False                                 Write-Host "A f...

   ```

   ```powershell
   Set-Content $env:temp\test.txt "This is a test file"
   ```

   ```output
   A file was created in the TEMP directory
   ```

## <a name="requirements"></a>Wymagania

Ten przykładowy skrypt wymaga programu Windows PowerShell 1.0 lub nowszej.

## <a name="demonstrates"></a>Przedstawiono

W przykładzie pokazano poniżej.

- Tworzenie podstawowego przykładowe polecenie cmdlet.

- Definiowanie klasy polecenia cmdlet, za pomocą atrybutu polecenia Cmdlet.

- Tworzenie przystawki, która współdziała z programu Windows PowerShell w wersji 1.0 i programu Windows PowerShell 2.0. Kolejne próbki używać modułów zamiast przystawki, więc wymagają one programu Windows PowerShell 2.0.

## <a name="example"></a>Przykład

W tym przykładzie przedstawiono sposób tworzenia prostego polecenia cmdlet i jego przystawki.

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;             //Windows PowerShell namespace
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{

   #region GetProcCommand

   /// <summary>
   /// This class implements the Get-Proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes of the local computer.
      /// Then, the WriteObject method writes the associated processes
      /// to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
         // Retrieve the current processes.
         Process[] processes = Process.GetProcesses();

         // Write the processes to the pipeline to make them available
         // to the next cmdlet. The second argument (true) tells Windows
         // PowerShell to enumerate the array and to send one process
         // object at a time to the pipeline.
         WriteObject(processes, true);
      }

      #endregion Overrides

   } //GetProcCommand

   #endregion GetProcCommand

   #region PowerShell snap-in

   /// <summary>
   /// Create this sample as an PowerShell snap-in
   /// </summary>
   [RunInstaller(true)]
   public class GetProcPSSnapIn01 : PSSnapIn
   {
       /// <summary>
       /// Create an instance of the GetProcPSSnapIn01
       /// </summary>
       public GetProcPSSnapIn01()
           : base()
       {
       }

       /// <summary>
       /// Get a name for this PowerShell snap-in. This name will be used in registering
       /// this PowerShell snap-in.
       /// </summary>
       public override string Name
       {
           get
           {
               return "GetProcPSSnapIn01";
           }
       }

       /// <summary>
       /// Vendor information for this PowerShell snap-in.
       /// </summary>
       public override string Vendor
       {
           get
           {
               return "Microsoft";
           }
       }

       /// <summary>
       /// Gets resource information for vendor. This is a string of format:
       /// resourceBaseName,resourceName.
       /// </summary>
       public override string VendorResource
       {
           get
           {
               return "GetProcPSSnapIn01,Microsoft";
           }
       }

       /// <summary>
       /// Description of this PowerShell snap-in.
       /// </summary>
       public override string Description
       {
           get
           {
               return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
           }
       }
   }

   #endregion PowerShell snap-in
}
```

## <a name="see-also"></a>Zobacz też

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)