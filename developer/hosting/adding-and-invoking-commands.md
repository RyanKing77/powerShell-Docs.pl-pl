---
title: Dodawanie i wywoływania poleceń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62be8432-28c1-4ca2-bcdb-d0350163fa8c
caps.latest.revision: 5
ms.openlocfilehash: 31371797ee57f07075da3436e0b42b2ca01aaffd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847754"
---
# <a name="adding-and-invoking-commands"></a><span data-ttu-id="3c2d6-102">Dodawanie i wywoływanie poleceń</span><span class="sxs-lookup"><span data-stu-id="3c2d6-102">Adding and invoking commands</span></span>

<span data-ttu-id="3c2d6-103">Po utworzeniu obszaru działania, można dodawać do potoku Windows PowerShellcommands i skrypty i synchronicznie lub asynchronicznie Wywołaj potoku.</span><span class="sxs-lookup"><span data-stu-id="3c2d6-103">After creating a runspace, you can add Windows PowerShellcommands and scripts to a pipeline, and then invoke the pipeline synchronously or asynchronously.</span></span>

## <a name="creating-a-pipeline"></a><span data-ttu-id="3c2d6-104">Tworzenie potoku</span><span class="sxs-lookup"><span data-stu-id="3c2d6-104">Creating a pipeline</span></span>

 <span data-ttu-id="3c2d6-105">[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) klasa udostępnia kilka metod dodawania polecenia, parametry i skrypty do potoku.</span><span class="sxs-lookup"><span data-stu-id="3c2d6-105">The [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class provides several methods to add commands, parameters, and scripts to the pipeline.</span></span> <span data-ttu-id="3c2d6-106">Wywoływanie potoku synchronicznie poprzez wywołanie przeciążenia [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) metody lub asynchronicznie, wywołując przeciążenie [ System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) i następnie [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) metody.</span><span class="sxs-lookup"><span data-stu-id="3c2d6-106">You can invoke the pipeline synchronously by calling an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, or asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) and then the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

### <a name="addcommand"></a><span data-ttu-id="3c2d6-107">Addcommand —</span><span class="sxs-lookup"><span data-stu-id="3c2d6-107">AddCommand</span></span>

1. <span data-ttu-id="3c2d6-108">Tworzenie [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) obiektu.</span><span class="sxs-lookup"><span data-stu-id="3c2d6-108">Create a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="3c2d6-109">Dodaj polecenie, które chcesz wykonać.</span><span class="sxs-lookup"><span data-stu-id="3c2d6-109">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="3c2d6-110">Wywołaj polecenie.</span><span class="sxs-lookup"><span data-stu-id="3c2d6-110">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

 <span data-ttu-id="3c2d6-111">Jeśli wywołasz [System.Management.Automation.Powershell.Addcommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) więcej niż jeden raz przed wywołaniem metody [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) metody, wynik pierwsze polecenie w potoku do drugiej i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="3c2d6-111">If you call the [System.Management.Automation.Powershell.Addcommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method more than once before you call the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span> <span data-ttu-id="3c2d6-112">Jeśli nie chcesz przekazać wynik poprzedniego polecenia do polecenia, dodaj go przez wywołanie metody [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="3c2d6-112">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="3c2d6-113">AddParameter</span><span class="sxs-lookup"><span data-stu-id="3c2d6-113">AddParameter</span></span>

 <span data-ttu-id="3c2d6-114">Poprzedni przykład wykonuje jednego polecenia bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="3c2d6-114">The previous example executes a single command without any parameters.</span></span> <span data-ttu-id="3c2d6-115">Można dodać parametry do polecenia przy użyciu [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) metody na przykład, poniższy kod umożliwia pobranie listy wszystkich procesów, które są nazywane `PowerShell` systemem maszyny.</span><span class="sxs-lookup"><span data-stu-id="3c2d6-115">You can add parameters to the command by using the [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 <span data-ttu-id="3c2d6-116">Można dodać dodatkowe parametry, wywołując [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) wielokrotnie.</span><span class="sxs-lookup"><span data-stu-id="3c2d6-116">You can add additional parameters by calling [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repeatedly.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 <span data-ttu-id="3c2d6-117">Możesz również dodać słownik nazw parametrów i wartości, wywołując [System.Management.Automation.Powershell.Addparameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) metody.</span><span class="sxs-lookup"><span data-stu-id="3c2d6-117">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.Powershell.Addparameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="3c2d6-118">AddStatement</span><span class="sxs-lookup"><span data-stu-id="3c2d6-118">AddStatement</span></span>

 <span data-ttu-id="3c2d6-119">Można symulować dzielenia na partie przy użyciu [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) metody, która dodaje dodatkowe oświadczenie na końcu potoku, poniższy kod umożliwia pobranie listy uruchomionych procesów o nazwie `PowerShell`, a następnie pobiera listę uruchomionych usług.</span><span class="sxs-lookup"><span data-stu-id="3c2d6-119">You can simulate batching by using the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="3c2d6-120">AddScript</span><span class="sxs-lookup"><span data-stu-id="3c2d6-120">AddScript</span></span>

 <span data-ttu-id="3c2d6-121">Istniejący skrypt można uruchomić, wywołując [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) metody.</span><span class="sxs-lookup"><span data-stu-id="3c2d6-121">You can run an existing script by calling the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span> <span data-ttu-id="3c2d6-122">Poniższy przykład dodaje skrypt do potoku i uruchamia go.</span><span class="sxs-lookup"><span data-stu-id="3c2d6-122">The following example adds a script to the pipeline and runs it.</span></span> <span data-ttu-id="3c2d6-123">W tym przykładzie przyjęto założenie, skrypt o nazwie istnieje już `MyScript.ps1` w folderze o nazwie `D:\PSScripts`.</span><span class="sxs-lookup"><span data-stu-id="3c2d6-123">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 <span data-ttu-id="3c2d6-124">Jest również wersja [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) metody, która przyjmuje parametr logiczny o nazwie `useLocalScope`.</span><span class="sxs-lookup"><span data-stu-id="3c2d6-124">There is also a version of the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method that takes a boolean parameter named `useLocalScope`.</span></span> <span data-ttu-id="3c2d6-125">Jeśli ten parametr jest równa `true`, a następnie skrypt jest uruchamiany w zakresie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="3c2d6-125">If this parameter is set to `true`, then the script is run in the local scope.</span></span> <span data-ttu-id="3c2d6-126">Poniższy kod będzie uruchomić skrypt w zakresie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="3c2d6-126">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a><span data-ttu-id="3c2d6-127">Wywoływanie potoku synchronicznie</span><span class="sxs-lookup"><span data-stu-id="3c2d6-127">Invoking a pipeline synchronously</span></span>

 <span data-ttu-id="3c2d6-128">Po dodaniu elementów do potoku jego wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="3c2d6-128">After you add elements to the pipeline, you invoke it.</span></span> <span data-ttu-id="3c2d6-129">Wywoływanie potoku synchronicznie, wywołanie przeciążenia [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) metody.</span><span class="sxs-lookup"><span data-stu-id="3c2d6-129">To invoke the pipeline synchronously, you call an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method.</span></span> <span data-ttu-id="3c2d6-130">Poniższy przykład pokazuje, jak synchronicznego wywoływania potoku.</span><span class="sxs-lookup"><span data-stu-id="3c2d6-130">The following example shows how to synchronously invoke a pipeline.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS1e
{
  class HostPS1e
  {
    static void Main(string[] args)
    {
      // Using the PowerShell.Create and AddCommand
      // methods, create a command pipeline.
      PowerShell ps = PowerShell.Create().AddCommand ("Sort-Object");

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the supplied input.
      foreach (PSObject result in ps.Invoke(new int[] { 3, 1, 6, 2, 5, 4 }))
      {
          Console.WriteLine("{0}", result);
      } // End foreach.
    } // End Main.
  } // End HostPS1e.
}
```

### <a name="invoking-a-pipeline-asynchronously"></a><span data-ttu-id="3c2d6-131">Asynchroniczne wywoływanie potoku</span><span class="sxs-lookup"><span data-stu-id="3c2d6-131">Invoking a pipeline asynchronously</span></span>

 <span data-ttu-id="3c2d6-132">Asynchroniczne wywoływanie potoku poprzez wywołanie przeciążenia [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) utworzyć [IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) obiektu, a następnie wywołując [ System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) metody.</span><span class="sxs-lookup"><span data-stu-id="3c2d6-132">You invoke a pipeline asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) to create an [IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) object, and then calling the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

 <span data-ttu-id="3c2d6-133">Poniższy przykład przedstawia sposób wywołania asynchronoulsy potoku.</span><span class="sxs-lookup"><span data-stu-id="3c2d6-133">The following example shows how to invoke a pipeline asynchronoulsy.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS3
{
  class HostPS3
  {
    static void Main(string[] args)
    {
      // Use the PowerShell.Create and PowerShell.AddCommand
      // methods to create a command pipeline that includes
      // Get-Process cmdlet. Do not include spaces immediatly
      // before or after the cmdlet name as that will cause
      // the command to fail.
      PowerShell ps = PowerShell.Create().AddCommand("Get-Process");

      // Create an IAsyncResult object and call the
      // BeginInvoke method to start running the
      // command pipeline asynchronously.
      IAsyncResult async = ps.BeginInvoke();

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the default runspace.
      foreach (PSObject result in ps.EndInvoke(async))
      {
        Console.WriteLine("{0,-20}{1}",
                result.Members["ProcessName"].Value,
                result.Members["Id"].Value);
      } // End foreach.
      System.Console.WriteLine("Hit any key to exit.");
      System.Console.ReadKey();
    } // End Main.
  } // End HostPS3.
}
```

## <a name="see-also"></a><span data-ttu-id="3c2d6-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3c2d6-134">See Also</span></span>

 [<span data-ttu-id="3c2d6-135">Tworzenie InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="3c2d6-135">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

 [<span data-ttu-id="3c2d6-136">Tworzenie ograniczonego obszaru działania</span><span class="sxs-lookup"><span data-stu-id="3c2d6-136">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)
