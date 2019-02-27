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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845612"
---
# <a name="runspace02-sample"></a>Przykład Runspace02

Ten przykład ilustruje sposób używania [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) klasy, aby uruchomić [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) i [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) poleceń cmdlet synchronicznie. [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) polecenie cmdlet zwraca [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektów dla wszystkich procesów działających na komputerze lokalnym i `Sort-Object` sortuje obiekty, w zależności od ich [ System.Diagnostics.Process.Id*](/dotnet/api/System.Diagnostics.Process.Id) właściwości. Wyniki tych poleceń jest wyświetlana przy użyciu [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) kontroli.

## <a name="requirements"></a>Wymagania

Ten przykładowy skrypt wymaga programu Windows PowerShell 2.0.

## <a name="demonstrates"></a>Przedstawiono

W przykładzie pokazano poniżej.

- Tworzenie [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) obiektu, aby uruchamiać polecenia.

- Dodawanie poleceń do potoku [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) obiektu.

- Uruchamianie polecenia synchronicznie.

- Za pomocą [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) formantu, aby wyświetlić dane wyjściowe polecenia w aplikacji Windows Forms.

## <a name="example"></a>Przykład

W tym przykładzie jest uruchamiany [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) i [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) polecenia cmdlet synchronicznie w obszarze działania domyślne, dostarczone przez środowisko Windows PowerShell. Dane wyjściowe są wyświetlane w formularzu za pomocą [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) kontroli.

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

## <a name="see-also"></a>Zobacz też

[Pisanie aplikacji hosta programu PowerShell Windows](./writing-a-windows-powershell-host-application.md)