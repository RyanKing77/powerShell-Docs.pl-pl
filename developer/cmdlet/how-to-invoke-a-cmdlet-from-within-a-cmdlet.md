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
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="3d627-102">Jak wywołać polecenie cmdlet z poziomu polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="3d627-102">How to Invoke a Cmdlet from Within a Cmdlet</span></span>

<span data-ttu-id="3d627-103">W tym przykładzie przedstawiono sposób wywołania polecenia cmdlet w ramach innego polecenia cmdlet, co pozwala na dodawanie funkcji wywoływanej polecenia cmdlet do polecenia cmdlet, które tworzysz.</span><span class="sxs-lookup"><span data-stu-id="3d627-103">This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span> <span data-ttu-id="3d627-104">W tym przykładzie `Get-Process` polecenia cmdlet jest wywołana w celu pobrania procesów, które są uruchomione na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="3d627-104">In this example, the `Get-Process` cmdlet is invoked to get the processes that are running on the local computer.</span></span> <span data-ttu-id="3d627-105">Wywołanie `Get-Process` polecenie cmdlet jest odpowiednikiem następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="3d627-105">The call to the `Get-Process` cmdlet is equivalent to the following command.</span></span> <span data-ttu-id="3d627-106">To polecenie umożliwia pobranie wszystkich procesów, których nazwy rozpoczynają się od znaków "" do "t".</span><span class="sxs-lookup"><span data-stu-id="3d627-106">This command retrieves all the processes whose names start with the characters "a" through "t".</span></span>

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> <span data-ttu-id="3d627-107">Można wywołać tylko tych poleceń cmdlet, które pochodzą bezpośrednio z [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klasy.</span><span class="sxs-lookup"><span data-stu-id="3d627-107">You can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="3d627-108">Nie można wywołać polecenia cmdlet, która pochodzi od klasy [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) klasy.</span><span class="sxs-lookup"><span data-stu-id="3d627-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="3d627-109">Do wywołania polecenia cmdlet w ramach polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="3d627-109">To invoke a cmdlet from within a cmdlet</span></span>

1. <span data-ttu-id="3d627-110">Upewnij się, że odwołuje się do zestawu, który definiuje polecenie cmdlet do wywołania i odpowiednie `using` instrukcji zostanie dodany.</span><span class="sxs-lookup"><span data-stu-id="3d627-110">Ensure that the assembly that defines the cmdlet to be invoked is referenced and that the appropriate `using` statement is added.</span></span> <span data-ttu-id="3d627-111">W tym przykładzie są dodawane następujące przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="3d627-111">In this example, the following namespaces are added.</span></span>

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. <span data-ttu-id="3d627-112">W danych wejściowych przetwarzania metody polecenia cmdlet należy utworzyć nowe wystąpienie klasy polecenia cmdlet do wywołania.</span><span class="sxs-lookup"><span data-stu-id="3d627-112">In the input processing method of the cmdlet, create a new instance of the cmdlet to be invoked.</span></span> <span data-ttu-id="3d627-113">W tym przykładzie obiekt typu [Microsoft.Powershell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) jest tworzony wraz z ciągiem, który zawiera argumenty, które są używane podczas wywoływania polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3d627-113">In this example, an object of type [Microsoft.Powershell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) is created along with the string that contains the arguments that are used when the cmdlet is invoked.</span></span>

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. <span data-ttu-id="3d627-114">Wywołaj [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) metody do wywołania `Get-Process` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3d627-114">Call the [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method to invoke the `Get-Process` cmdlet.</span></span>

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a><span data-ttu-id="3d627-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="3d627-115">Example</span></span>

<span data-ttu-id="3d627-116">W tym przykładzie `Get-Process` polecenia cmdlet jest wywoływana z poziomu [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metoda polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3d627-116">In this example, the `Get-Process` cmdlet is invoked from within the [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method of a cmdlet.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3d627-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3d627-117">See Also</span></span>

[<span data-ttu-id="3d627-118">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3d627-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
