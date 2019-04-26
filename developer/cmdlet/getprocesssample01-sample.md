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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068066"
---
# <a name="getprocesssample01-sample"></a><span data-ttu-id="eb865-102">Przykład GetProcessSample01</span><span class="sxs-lookup"><span data-stu-id="eb865-102">GetProcessSample01 Sample</span></span>

<span data-ttu-id="eb865-103">Niniejszy przykład pokazuje sposób implementacji polecenia cmdlet, które pobiera procesów na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="eb865-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="eb865-104">To polecenie cmdlet jest uproszczoną wersję `Get-Process` polecenia cmdlet, które są dostarczane przez program Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="eb865-104">This cmdlet is a simplified version of the `Get-Process` cmdlet that is provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="eb865-105">Jak skompilować przykład za pomocą programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="eb865-105">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="eb865-106">Za pomocą Windows PowerShell 2.0 zainstalowany zestaw SDK przejdź do folderu GetProcessSample01.</span><span class="sxs-lookup"><span data-stu-id="eb865-106">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample01 folder.</span></span> <span data-ttu-id="eb865-107">Domyślna lokalizacja to C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.</span><span class="sxs-lookup"><span data-stu-id="eb865-107">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.</span></span>

2. <span data-ttu-id="eb865-108">Kliknij dwukrotnie ikonę pliku rozwiązania (.sln).</span><span class="sxs-lookup"><span data-stu-id="eb865-108">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="eb865-109">Spowoduje to otwarcie z przykładowym projektem w programie Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="eb865-109">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="eb865-110">W **kompilacji** menu, wybierz opcję **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="eb865-110">In the **Build** menu, select **Build Solution**.</span></span>

  <span data-ttu-id="eb865-111">Biblioteka dla przykładu, zostanie utworzona w folderze \bin lub \bin\debug domyślny.</span><span class="sxs-lookup"><span data-stu-id="eb865-111">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="eb865-112">Jak uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="eb865-112">How to run the sample</span></span>

1. <span data-ttu-id="eb865-113">Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="eb865-113">Open a Command Prompt window.</span></span>

2. <span data-ttu-id="eb865-114">Przejdź do katalogu zawierającego przykładowy plik .dll.</span><span class="sxs-lookup"><span data-stu-id="eb865-114">Navigate to the directory containing the sample .dll file.</span></span>

3. <span data-ttu-id="eb865-115">Run installutil "GetProcessSample01.dll".</span><span class="sxs-lookup"><span data-stu-id="eb865-115">Run installutil "GetProcessSample01.dll".</span></span>

4. <span data-ttu-id="eb865-116">Uruchom program Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb865-116">Start Windows PowerShell.</span></span>

5. <span data-ttu-id="eb865-117">Uruchom następujące polecenie, aby dodać przystawkę powłoki.</span><span class="sxs-lookup"><span data-stu-id="eb865-117">Run the following command to add the snap-in to the shell.</span></span>

   `Add-PSSnapin GetProcPSSnapIn01`

6. <span data-ttu-id="eb865-118">Wprowadź następujące polecenie, aby uruchomić polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eb865-118">Enter the following command to run the cmdlet.</span></span> `get-proc`

   `get-proc`

   <span data-ttu-id="eb865-119">To przykładowe dane wyjściowe, będącą wynikiem, wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="eb865-119">This is a sample output that results from following these steps.</span></span>

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

## <a name="requirements"></a><span data-ttu-id="eb865-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eb865-120">Requirements</span></span>

<span data-ttu-id="eb865-121">Ten przykładowy skrypt wymaga programu Windows PowerShell 1.0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="eb865-121">This sample requires Windows PowerShell 1.0 or later.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="eb865-122">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="eb865-122">Demonstrates</span></span>

<span data-ttu-id="eb865-123">W przykładzie pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="eb865-123">This sample demonstrates the following.</span></span>

- <span data-ttu-id="eb865-124">Tworzenie podstawowego przykładowe polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eb865-124">Creating a basic sample cmdlet.</span></span>

- <span data-ttu-id="eb865-125">Definiowanie klasy polecenia cmdlet, za pomocą atrybutu polecenia Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eb865-125">Defining a cmdlet class by using the Cmdlet attribute.</span></span>

- <span data-ttu-id="eb865-126">Tworzenie przystawki, która współdziała z programu Windows PowerShell w wersji 1.0 i programu Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="eb865-126">Creating a snap-in that works with both Windows PowerShell 1.0 and Windows PowerShell 2.0.</span></span> <span data-ttu-id="eb865-127">Kolejne próbki używać modułów zamiast przystawki, więc wymagają one programu Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="eb865-127">Subsequent samples use modules instead of snap-ins so they require Windows PowerShell 2.0.</span></span>

## <a name="example"></a><span data-ttu-id="eb865-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="eb865-128">Example</span></span>

<span data-ttu-id="eb865-129">W tym przykładzie przedstawiono sposób tworzenia prostego polecenia cmdlet i jego przystawki.</span><span class="sxs-lookup"><span data-stu-id="eb865-129">This sample shows how to create a simple cmdlet and its snap-in.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="eb865-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb865-130">See Also</span></span>

[<span data-ttu-id="eb865-131">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eb865-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)