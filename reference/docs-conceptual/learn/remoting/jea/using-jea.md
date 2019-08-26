---
ms.date: 07/10/2019
keywords: jea, PowerShell, zabezpieczenia
title: Korzystanie z usługi JEA
ms.openlocfilehash: 8f3cc9186c61a2ae5b64eb3dc4f72ca83f1a58c5
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017895"
---
# <a name="using-jea"></a>Korzystanie z usługi JEA

W tym artykule opisano różne sposoby nawiązywania połączenia z punktem końcowym JEA i korzystania z niego.

## <a name="using-jea-interactively"></a>Korzystanie z usługi JEA interaktywnie

Jeśli testujesz konfigurację usługi JEA lub masz proste zadania dla użytkowników, możesz użyć JEA w taki sam sposób jak w przypadku zwykłej sesji komunikacji zdalnej programu PowerShell. W przypadku złożonych zadań komunikacji zdalnej zaleca się użycie niejawnych [usług zdalnych](#using-jea-with-implicit-remoting). Niejawne komunikacja zdalna pozwala użytkownikom na pracę z obiektami danych lokalnie.

Aby korzystać z usługi JEA w sposób interaktywny, potrzebne są:

- Nazwa komputera, z którym nawiązujesz połączenie (może to być komputer lokalny)
- Nazwa punktu końcowego JEA zarejestrowanego na tym komputerze
- Poświadczenia, które mają dostęp do punktu końcowego JEA na tym komputerze

Uwzględniając te informacje, można uruchomić sesję JEA przy użyciu polecenia cmdlet [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) lub [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) .

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

Jeśli bieżące konto użytkownika ma dostęp do punktu końcowego JEA, możesz pominąć parametr **Credential** .

Po wyświetleniu monitu `[localhost]: PS>` programu PowerShell z informacją o tym, że teraz korzystasz z sesji zdalnej jea. Można uruchomić `Get-Command` polecenie, aby sprawdzić, które polecenia są dostępne. Skontaktuj się z administratorem, aby dowiedzieć się, czy istnieją jakiekolwiek ograniczenia dotyczące dostępnych parametrów lub dozwolonych wartości parametrów.

Należy pamiętać, że sesje JEA działają w trybie NoLanguage. Niektóre ze sposobów, z których zazwyczaj korzystasz z programu PowerShell, mogą nie być dostępne. Na przykład nie można używać zmiennych do przechowywania danych ani inspekcji właściwości obiektów zwróconych z poleceń cmdlet. Poniższy przykład przedstawia dwa podejścia do uzyskania tych samych poleceń w trybie NoLanguage.

```powershell
# Using variables is prohibited in NoLanguage mode. The following will not work:
# $vm = Get-VM -Name 'SQL01'
# Start-VM -VM $vm

# You can use pipes to pass data through to commands that accept input from the pipeline
Get-VM -Name 'SQL01' | Start-VM

# You can also wrap subcommands in parentheses and enter them inline as arguments
Start-VM -VM (Get-VM -Name 'SQL01')

# You can also use parameter sets that don't require extra data to be passed in
Start-VM -VMName 'SQL01'
```

W przypadku bardziej złożonych wywołań poleceń, które sprawiają, że ta metoda jest trudna, należy rozważyć użycie niejawnej [komunikacji zdalnej](#using-jea-with-implicit-remoting) lub [utworzenie funkcji niestandardowych](role-capabilities.md#creating-custom-functions) , które zawijają wymaganą funkcjonalność.

## <a name="using-jea-with-implicit-remoting"></a>Korzystanie z JEA z niejawnymi usługami zdalnymi

Program PowerShell ma niejawny model komunikacji zdalnej, który umożliwia importowanie poleceń cmdlet serwera proxy z maszyny zdalnej i korzystanie z nich w taki sposób, jakby były poleceniami lokalnymi. Niejawne komunikacji zdalnej wyjaśniono w tym **Hej, obsługa skryptów Guy!** [wpis w blogu](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).
Niejawne komunikacji zdalnej są przydatne podczas pracy z usługą JEA, ponieważ umożliwia pracę z poleceniami cmdlet JEA w trybie pełnego języka. Możesz użyć uzupełniania kart, zmiennych, manipulowania obiektami, a nawet używać lokalnych skryptów do automatyzowania zadań względem punktu końcowego JEA. Za każdym razem, gdy wywołasz polecenie proxy, dane są wysyłane do punktu końcowego JEA na maszynie zdalnej i wykonywane w tym miejscu.

Niejawne wykonanie komunikacji zdalnej przez zaimportowanie poleceń cmdlet z istniejącej sesji programu PowerShell. Opcjonalnie możesz wybrać opcję przedrostka rzeczowników każdego polecenia cmdlet serwera proxy z wybranym ciągiem. Prefiks umożliwia odróżnienie poleceń dla systemu zdalnego. Tymczasowy moduł skryptu zawierający wszystkie polecenia proxy jest tworzony i zaimportowany na czas trwania lokalnej sesji programu PowerShell.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> Niektóre systemy mogą nie być w stanie zaimportować całej sesji JEA ze względu na ograniczenia w domyślnych poleceniach cmdlet JEA. Aby to zrobić, należy zaimportować tylko potrzebne polecenia z sesji jea, jawnie dostarczając ich nazwy do `-CommandName` parametru. Przyszła aktualizacja umożliwi rozwiązanie problemu z importowaniem całych sesji JEA w systemach, których to dotyczy.

Jeśli nie możesz zaimportować sesji JEA ze względu na ograniczenia JEA dla parametrów domyślnych, wykonaj poniższe kroki, aby odfiltrować domyślne polecenia z zaimportowanego zestawu. Możesz nadal używać poleceń takich jak `Select-Object`, ale po prostu użyjesz lokalnej wersji zainstalowanej na komputerze zamiast zaimportowanej ze zdalnej sesji jea.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Get a list of all the commands on the JEA endpoint
$commands = Invoke-Command -Session $jeasession -ScriptBlock { Get-Command }

# Filter out the default cmdlets
$jeaDefaultCmdlets = 'Clear-Host', 'Exit-PSSession', 'Get-Command', 'Get-FormatData', 'Get-Help', 'Measure-Object', 'Out-Default', 'Select-Object'
$filteredCommands = $commands.Name | Where-Object { $jeaDefaultCmdlets -notcontains $_ }

# Import only commands explicitly added in role capabilities and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA' -CommandName $filteredCommands
```

Polecenia cmdlet serwera proxy można również utrwalać z niejawnych usług zdalnych przy użyciu polecenia [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).
Aby uzyskać więcej informacji na temat niejawnych usług zdalnych, zobacz dokumentację dotyczącą [importu-PSSession](/powershell/microsoft.powershell.utility/import-pssession) i [importu-modułu](/powershell/microsoft.powershell.core/import-module).

## <a name="using-jea-programmatically"></a>Korzystanie z JEA programowo

JEA można także używać w systemach automatyzacji i w aplikacjach użytkowników, takich jak aplikacje i witryny pomocy technicznej w firmie. Podejście jest takie samo, jak w przypadku kompilowania aplikacji, które komunikują się z nieskonfigurowanymi punktami końcowymi programu PowerShell. Upewnij się, że program jest przeznaczony do pracy z ograniczeniami narzuconymi przez JEA.

W przypadku prostych, jednorazowych zadań można użyć [polecenia Invoke](/powershell/module/microsoft.powershell.core/invoke-command) , aby uruchomić polecenia w sesji jea.

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

Aby sprawdzić, które polecenia są dostępne do użycia podczas łączenia się z sesją jea, `Get-Command` Uruchom i wykonaj iterację w wynikach, aby sprawdzić, czy są dozwolone parametry.

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

Jeśli tworzysz C# aplikację, możesz utworzyć obszar działania programu PowerShell, który nawiązuje połączenie z sesją jea, określając nazwę konfiguracji w obiekcie [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) .

```csharp
// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
// See https://docs.microsoft.com/dotnet/api/system.management.automation.pscredential
var creds        = // create a PSCredential object here

WSManConnectionInfo connectionInfo = new WSManConnectionInfo(
    false,                 // Use SSL
    computerName,          // Computer name
    5985,                  // WSMan Port
    "/wsman",              // WSMan Path
                           // Connection URI with config name
    string.Format(CultureInfo.InvariantCulture, "http://schemas.microsoft.com/powershell/{0}", configName),
    creds);                // Credentials

// Now, use the connection info to create a runspace where you can run the commands
using (Runspace runspace = RunspaceFactory.CreateRunspace(connectionInfo))
{
    // Open the runspace
    runspace.Open();

    using (PowerShell ps = PowerShell.Create())
    {
        // Set the PowerShell object to use the JEA runspace
        ps.Runspace = runspace;

        // Now you can add and invoke commands
        ps.AddCommand("Get-Command");
        foreach (var result in ps.Invoke())
        {
            Console.WriteLine(result);
        }
    }

    // Close the runspace
    runspace.Close();
}
```

## <a name="using-jea-with-powershell-direct"></a>Używanie JEA z programem PowerShell Direct

Funkcja Hyper-V w systemie Windows 10 i Windows Server 2016 oferuje [bezpośrednie środowisko PowerShell](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), funkcję, która umożliwia administratorom funkcji Hyper-V zarządzanie maszynami wirtualnymi za pomocą programu PowerShell niezależnie od konfiguracji sieci lub ustawień zarządzania zdalnego w wirtualnej maszynie.

Za pomocą programu PowerShell Direct with JEA można udzielić administratorowi funkcji Hyper-V ograniczonego dostępu do maszyny wirtualnej.
Może to być przydatne, Jeśli utracisz łączność sieciową z maszyną wirtualną i potrzebujesz administratora centrum danych w celu naprawy ustawień sieci.

Do korzystania z JEA za pośrednictwem programu PowerShell Direct nie jest wymagana dodatkowa konfiguracja. Jednak system operacyjny gościa działający na maszynie wirtualnej musi być w systemie Windows 10, Windows Server 2016 lub nowszym. Administrator funkcji Hyper-V może nawiązać połączenie z punktem końcowym usługi `-VMName` jea `-VMId` za pomocą parametrów lub w poleceniach cmdlet PSRemoting:

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

Zaleca się utworzenie dedykowanego konta użytkownika z minimalnymi prawami wymaganymi do zarządzania systemem w celu użycia przez administratora funkcji Hyper-V. Należy pamiętać, że nawet nieuprzywilejowany użytkownik może zalogować się do komputera z systemem Windows domyślnie, w tym przy użyciu nieograniczonego programu PowerShell. Dzięki temu można przeglądać system plików i dowiedzieć się więcej o środowisku systemu operacyjnego. Aby zablokować administratora funkcji Hyper-V i ograniczyć dostęp do maszyny wirtualnej przy użyciu programu PowerShell Direct z JEA, należy odmówić uprawnień lokalnego logowania do konta JEA administratora funkcji Hyper-V.
