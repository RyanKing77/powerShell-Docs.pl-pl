---
title: Opis wywoływania polecenia Cmdlet w ramach polecenia Cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efa4dc9c-ddee-46a3-978a-9dbb61e9bb6f
caps.latest.revision: 12
ms.openlocfilehash: d4564b51b74422cdaec3878b227ffc6be7c97949
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846732"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Jak wywołać polecenie cmdlet z poziomu polecenia cmdlet

W tym przykładzie przedstawiono sposób wywołania polecenia cmdlet w ramach innego polecenia cmdlet, co pozwala na dodawanie funkcji wywoływanej polecenia cmdlet do polecenia cmdlet, które tworzysz. W tym przykładzie `Get-Process` polecenia cmdlet jest wywołana w celu pobrania procesów, które są uruchomione na komputerze lokalnym. Wywołanie `Get-Process` polecenie cmdlet jest odpowiednikiem następującego polecenia. To polecenie umożliwia pobranie wszystkich procesów, których nazwy rozpoczynają się od znaków "" do "t".

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> Można wywołać tylko tych poleceń cmdlet, które pochodzą bezpośrednio z [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klasy. Nie można wywołać polecenia cmdlet, która pochodzi od klasy [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) klasy.

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Do wywołania polecenia cmdlet w ramach polecenia cmdlet

1. Upewnij się, że odwołuje się do zestawu, który definiuje polecenie cmdlet do wywołania i odpowiednie `using` instrukcji zostanie dodany. W tym przykładzie są dodawane następujące przestrzenie nazw.

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. W danych wejściowych przetwarzania metody polecenia cmdlet należy utworzyć nowe wystąpienie klasy polecenia cmdlet do wywołania. W tym przykładzie obiekt typu [Microsoft.Powershell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) jest tworzony wraz z ciągiem, który zawiera argumenty, które są używane podczas wywoływania polecenia cmdlet.

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. Wywołaj [System.Management.Automation.Cmdlet.Invoke*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) metody do wywołania `Get-Process` polecenia cmdlet.

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a>Przykład

W tym przykładzie `Get-Process` polecenia cmdlet jest wywoływana z poziomu [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metoda polecenia cmdlet.

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;   // Windows PowerShell assembly.
using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify an
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "GreetingInvoke")]
  public class SendGreetingInvokeCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory = true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the BeginProcessing method to invoke
    // the Get-Process cmdlet.
    protected override void BeginProcessing()
    {
      GetProcessCommand gp = new GetProcessCommand();
      gp.Name = new string[] { "[a-t]*" };
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }

    // Override the ProcessRecord method to process
    // the supplied user name and write out a
    // greeting to the user by calling the WriteObject
    // method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "!");
    }
  }
}
```

## <a name="see-also"></a>Zobacz też

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
