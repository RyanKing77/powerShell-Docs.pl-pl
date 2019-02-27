---
title: Importowanie i wywoływania przepływu pracy programu PowerShell Windows | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50e6f9b1-2678-4f53-9250-7c48843a9549
caps.latest.revision: 5
ms.openlocfilehash: 1113c0d1cd68bb97d2f96b529f755b62137d1f40
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845822"
---
# <a name="importing-and-invoking-a-windows-powershell-workflow"></a>Importowanie i wywoływanie przepływu pracy programu Windows PowerShell

Windows PowerShell 3, umożliwia importowanie i wywołania przepływu pracy, który jest spakowany jako moduł programu Windows PowerShell. Aby uzyskać informacji na temat modułów programu Windows PowerShell, zobacz [pisanie modułu programu Windows PowerShell](../module/writing-a-windows-powershell-module.md).

[System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)klasa jest używana jako serwer proxy po stronie klienta dla obiektów przepływu pracy na serwerze. Poniższa procedura wyjaśnia, jak używać [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)obiekt do wywołania przepływu pracy.

### <a name="creating-a-psjobproxy-object-to-execute-workflow-commands-on-a-remote-server"></a>Tworzenie obiektu PSJobProxy wykonywanie poleceń przepływu pracy na serwerze zdalnym.

1. Tworzenie [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)obiektu do utworzenia połączenia zdalnego obszaru działania.

2. Ustaw [System.Management.Automation.Runspaces.Wsmanconnectioninfo.Shelluri*](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ShellUri) właściwość [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)obiekt `Microsoft.PowerShell.Workflow` do Określ punkt końcowy programu Windows PowerShell.

3. Utwórz obszar działania, korzystającym z połączenia utworzony przez wykonanie poprzednich kroków.

4. Tworzenie [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell)obiektu i ustaw jego [System.Management.Automation.Powershell.Runspace*](/dotnet/api/System.Management.Automation.PowerShell.Runspace) właściwość obszarem działania utworzone w poprzednim kroku.

5. Zaimportuj moduł przepływu pracy i jego poleceń do [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell).

6. Tworzenie [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy) obiektu i używać go do wykonywania poleceń przepływu pracy na serwerze zdalnym.

## <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje, jak wywołać przepływu pracy przy użyciu programu Windows PowerShell.

W tym przykładzie wymaga programu Windows PowerShell 3.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;
using System.Management.Automation.Runspaces;

namespace WorkflowHostTest
{

class Program
    {
        static void Main(string[] args)
        {
            if (args.Length == 0)
            {
                Console.WriteLine("Specify path to Workflow module");
                return;
            }

            string moduleFile = args[0];

            Console.Write("Creating Remote runspace connection...");
            WSManConnectionInfo connectionInfo = new WSManConnectionInfo();

            //Set the shellURI to workflow endpoint Microsoft.PowerShell.Workflow
            connectionInfo.ShellUri = "Microsoft.PowerShell.Workflow";

            //Create and open a runspace.
            Runspace runspace = RunspaceFactory.CreateRunspace(connectionInfo);
            runspace.Open();
            Console.WriteLine("done");

            PowerShell powershell = PowerShell.Create();
            powershell.Runspace = runspace;
            Console.Write("Setting $VerbosePreference=\"Continue\"...");
            powershell.AddScript("$VerbosePreference=\"Continue\"");
            powershell.Invoke();
            Console.WriteLine("done");

            Console.Write("Importing Workflow module...");
            powershell.Commands.Clear();

            //Import the module in to the PowerShell runspace. A XAML file could also be imported directly by using Import-Module.
            powershell.AddCommand("Import-Module").AddArgument(moduleFile);
            powershell.Invoke();
            Console.WriteLine("done");

            Console.Write("Creating job proxy...");
            powershell.Commands.Clear();
            powershell.AddCommand("Get-Proc").AddArgument("*");
            PSJobProxy job = powershell.AsJobProxy();
            Console.WriteLine("done");

                Console.WriteLine();
                Console.WriteLine("Using job proxy and performing operations...");
                Console.WriteLine("State of Job :" + job.JobStateInfo.State.ToString());
                Console.WriteLine("Starting job...");
                job.StartJob();
                Console.WriteLine("State of Job :" + job.JobStateInfo.State.ToString());

                // use blocking enumerator to wait for objects until job finishes
                job.Output.BlockingEnumerator = true;
                foreach (PSObject o in job.Output)
                {
                    Console.WriteLine(o.Properties["ProcessName"].Value.ToString());
                }

                // wait for a random time before attempting to stop job
                Random random = new Random();
                int time = random.Next(1, 10);
                Console.Write("Sleeping for {0} seconds when job is running on another thread...", time);
                System.Threading.Thread.Sleep(time * 1000);
                Console.WriteLine("done");
                Console.WriteLine("Stopping job...");
                job.StopJob();
                Console.WriteLine("State of Job :" + job.JobStateInfo.State.ToString());
                Console.WriteLine();
                job.Finished.WaitOne();
                Console.WriteLine("Output from job");
                Console.WriteLine("---------------");

                foreach (PSObject o in job.Output)
                {
                    Console.WriteLine(o.Properties["ProcessName"].Value.ToString());
                }

                Console.WriteLine();
                Console.WriteLine("Verbose messages from job");
                Console.WriteLine("-------------------------");
                foreach (VerboseRecord v in job.Verbose)
                {
                    Console.WriteLine(v.Message);
                }

            runspace.Close();
        }
    }
}

```