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
ms.openlocfilehash: 9a01f948c5b474b4f9068030907601543e13cc7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083029"
---
# <a name="adding-and-invoking-commands"></a>Dodawanie i wywoływanie poleceń

Po utworzeniu obszaru działania, można dodawać do potoku Windows PowerShellcommands i skrypty i synchronicznie lub asynchronicznie Wywołaj potoku.

## <a name="creating-a-pipeline"></a>Tworzenie potoku

 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) klasa udostępnia kilka metod dodawania polecenia, parametry i skrypty do potoku. Wywoływanie potoku synchronicznie poprzez wywołanie przeciążenia [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) metody lub asynchronicznie, wywołując przeciążenie [ System.Management.Automation.Powershell.Begininvoke*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) i następnie [System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) metody.

### <a name="addcommand"></a>Addcommand —

1. Tworzenie [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) obiektu.

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. Dodaj polecenie, które chcesz wykonać.

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. Wywołaj polecenie.

   ```csharp
   ps.Invoke();
   ```

 Jeśli wywołasz [System.Management.Automation.Powershell.Addcommand*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) więcej niż jeden raz przed wywołaniem metody [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) metody, wynik pierwsze polecenie w potoku do drugiej i tak dalej. Jeśli nie chcesz przekazać wynik poprzedniego polecenia do polecenia, dodaj go przez wywołanie metody [System.Management.Automation.Powershell.Addstatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) zamiast tego.

### <a name="addparameter"></a>AddParameter

 Poprzedni przykład wykonuje jednego polecenia bez parametrów. Można dodać parametry do polecenia przy użyciu [System.Management.Automation.Pscommand.Addparameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) metody na przykład, poniższy kod umożliwia pobranie listy wszystkich procesów, które są nazywane `PowerShell` systemem maszyny.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 Można dodać dodatkowe parametry, wywołując [System.Management.Automation.Pscommand.Addparameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) wielokrotnie.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 Możesz również dodać słownik nazw parametrów i wartości, wywołując [System.Management.Automation.Powershell.Addparameters*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) metody.

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

 Można symulować dzielenia na partie przy użyciu [System.Management.Automation.Powershell.Addstatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) metody, która dodaje dodatkowe oświadczenie na końcu potoku, poniższy kod umożliwia pobranie listy uruchomionych procesów o nazwie `PowerShell`, a następnie pobiera listę uruchomionych usług.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

 Istniejący skrypt można uruchomić, wywołując [System.Management.Automation.Powershell.Addscript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) metody. Poniższy przykład dodaje skrypt do potoku i uruchamia go. W tym przykładzie przyjęto założenie, skrypt o nazwie istnieje już `MyScript.ps1` w folderze o nazwie `D:\PSScripts`.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 Jest również wersja [System.Management.Automation.Powershell.Addscript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) metody, która przyjmuje parametr logiczny o nazwie `useLocalScope`. Jeśli ten parametr jest równa `true`, a następnie skrypt jest uruchamiany w zakresie lokalnym. Poniższy kod będzie uruchomić skrypt w zakresie lokalnym.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a>Wywoływanie potoku synchronicznie

 Po dodaniu elementów do potoku jego wywołaniu. Wywoływanie potoku synchronicznie, wywołanie przeciążenia [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) metody. Poniższy przykład pokazuje, jak synchronicznego wywoływania potoku.

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

### <a name="invoking-a-pipeline-asynchronously"></a>Asynchroniczne wywoływanie potoku

 Asynchroniczne wywoływanie potoku poprzez wywołanie przeciążenia [System.Management.Automation.Powershell.Begininvoke*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) utworzyć [IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) obiektu, a następnie wywołując [ System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) metody.

 Poniższy przykład pokazuje, jak asynchroniczne wywoływanie potoku.

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
      // Get-Process cmdlet. Do not include spaces immediately
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

## <a name="see-also"></a>Zobacz też

 [Tworzenie InitialSessionState](./creating-an-initialsessionstate.md)

 [Tworzenie ograniczonego obszaru działania](./creating-a-constrained-runspace.md)
