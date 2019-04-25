---
title: Przykładowe Runspace02 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7630bb63-ef39-4abd-b795-8000f984c1e5
caps.latest.revision: 9
ms.openlocfilehash: 6352169cffbb8a8bf59a42f79979f5003c150fa4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082723"
---
# <a name="runspace02-sample"></a><span data-ttu-id="bcbb2-102">Przykład Runspace02</span><span class="sxs-lookup"><span data-stu-id="bcbb2-102">Runspace02 Sample</span></span>

<span data-ttu-id="bcbb2-103">Ten przykład ilustruje sposób używania [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) klasy, aby uruchomić [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) i [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) poleceń cmdlet synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="bcbb2-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously.</span></span> <span data-ttu-id="bcbb2-104">[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) polecenie cmdlet zwraca [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektów dla wszystkich procesów działających na komputerze lokalnym i `Sort-Object` sortuje obiekty, w zależności od ich [ System.Diagnostics.Process.Id\*](/dotnet/api/System.Diagnostics.Process.Id) właściwości.</span><span class="sxs-lookup"><span data-stu-id="bcbb2-104">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects for each process running on the local computer, and the `Sort-Object` sorts the objects based on their [System.Diagnostics.Process.Id\*](/dotnet/api/System.Diagnostics.Process.Id) property.</span></span> <span data-ttu-id="bcbb2-105">Wyniki tych poleceń jest wyświetlana przy użyciu [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) kontroli.</span><span class="sxs-lookup"><span data-stu-id="bcbb2-105">The results of these commands is displayed by using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.</span></span>

## <a name="requirements"></a><span data-ttu-id="bcbb2-106">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bcbb2-106">Requirements</span></span>

<span data-ttu-id="bcbb2-107">Ten przykładowy skrypt wymaga programu Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="bcbb2-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="bcbb2-108">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="bcbb2-108">Demonstrates</span></span>

<span data-ttu-id="bcbb2-109">W przykładzie pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="bcbb2-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="bcbb2-110">Tworzenie [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) obiektu, aby uruchamiać polecenia.</span><span class="sxs-lookup"><span data-stu-id="bcbb2-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run commands.</span></span>

- <span data-ttu-id="bcbb2-111">Dodawanie poleceń do potoku [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) obiektu.</span><span class="sxs-lookup"><span data-stu-id="bcbb2-111">Adding commands to the pipeline of [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="bcbb2-112">Uruchamianie polecenia synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="bcbb2-112">Running the commands synchronously.</span></span>

- <span data-ttu-id="bcbb2-113">Za pomocą [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) formantu, aby wyświetlić dane wyjściowe polecenia w aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="bcbb2-113">Using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control to display the output of the commands in a Windows Forms application.</span></span>

## <a name="example"></a><span data-ttu-id="bcbb2-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="bcbb2-114">Example</span></span>

<span data-ttu-id="bcbb2-115">W tym przykładzie jest uruchamiany [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) i [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) polecenia cmdlet synchronicznie w obszarze działania domyślne, dostarczone przez środowisko Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bcbb2-115">This sample runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="bcbb2-116">Dane wyjściowe są wyświetlane w formularzu za pomocą [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) kontroli.</span><span class="sxs-lookup"><span data-stu-id="bcbb2-116">The output is displayed in a form using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using System.Windows.Forms;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace02
  {
    /// <summary>
    /// This method creates the form where the output is displayed.
    /// </summary>
    private static void CreateForm()
    {
      Form form = new Form();
      DataGridView grid = new DataGridView();
      form.Controls.Add(grid);
      grid.Dock = DockStyle.Fill;

      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the command.
      using (PowerShell powershell = PowerShell.Create())
      {
        powershell.AddCommand("get-process").AddCommand("sort-object").AddArgument("ID");
        if (Runspace.DefaultRunspace == null)
        {
          Runspace.DefaultRunspace = powershell.Runspace;
        }

        Collection<PSObject> results = powershell.Invoke();

        // The generic collection needs to be re-wrapped in an ArrayList
        // for data-binding to work.
        ArrayList objects = new ArrayList();
        objects.AddRange(results);

        // The DataGridView will use the PSObjectTypeDescriptor type
        // to retrieve the properties.
        grid.DataSource = objects;
      }

      form.ShowDialog();
    }

    /// <summary>
    /// This sample uses a PowerShell object to run the Get-Process
    /// and Sort-Object cmdlets synchronously. Windows Forms and
    /// data binding are then used to display the results in a
    /// DataGridView control.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object.
    /// 2. Adding commands and arguments to the pipeline of
    ///    the PowerShell object.
    /// 3. Running the commands synchronously.
    /// 4. Using a DataGridView control to display the output
    ///    of the commands in a Windows Forms application.
    /// </remarks>
    private static void Main(string[] args)
    {
      Runspace02.CreateForm();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="bcbb2-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bcbb2-117">See Also</span></span>

[<span data-ttu-id="bcbb2-118">Pisanie aplikacji hosta programu PowerShell Windows</span><span class="sxs-lookup"><span data-stu-id="bcbb2-118">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)