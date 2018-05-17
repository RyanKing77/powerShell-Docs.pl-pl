---
ms.date: 06/12/2017
keywords: jea, programu powershell, zabezpieczeń
title: Korzystanie z usługi JEA
ms.openlocfilehash: 891e4be4c3fadceeff5ede7ac5cab04a5f80e5c1
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="using-jea"></a>Korzystanie z usługi JEA

> Dotyczy: środowiska Windows PowerShell 5.0

W tym temacie opisano różne sposoby, można połączyć się i używać punktu końcowego JEA.

## <a name="using-jea-interactively"></a>Używanie JEA interakcyjne

Jeśli testujesz konfigurację JEA lub masz prostych zadań użytkownikom wykonywanie, można użyć JEA tak samo jak regularne sesji komunikacji zdalnej programu PowerShell.
Remoting złożonych zadań, zaleca się używania [niejawne remoting](#using-jea-with-implicit-remoting) zamiast tego w celu ułatwienia dla użytkowników przez, dzięki czemu użytkownicy mogą pracować z obiektów danych lokalnie.

Aby używać JEA interakcyjnie, będą potrzebne:
- Nazwa komputera jest nawiązywane (może być komputer lokalny)
- Nazwa punktu końcowego JEA zarejestrowane na tym komputerze
- Poświadczenia dla komputera, które mają dostęp do punktu końcowego JEA

Dane zapasów, można rozpocząć sesji JEA przy użyciu [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) lub [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

Jeśli konto, obecnie zalogowano jako ma dostęp do punktu końcowego JEA, można pominąć `-Credential` parametru.

Gdy programu PowerShell Monituj zmiany `[localhost]: PS>` będzie wiadomo, że możesz teraz współpracuje z sesji zdalnej JEA.
Można uruchomić `Get-Command` do sprawdzenia, które polecenia są dostępne.
Należy skontaktować się z administratorem, aby dowiedzieć się, czy ma żadnych ograniczeń dotyczących dostępnych parametrów lub wartości parametrów dozwolony.

Dla przypomnienia JEA sesji działają w trybie NoLanguage, więc niektóre metody należy zwykle użyć programu PowerShell nie mogą być dostępne.
Na przykład nie można używać zmiennych do przechowywania danych lub sprawdź właściwości na obiekty zwrócone przez polecenia cmdlet.
Poniżej przedstawiono przykład przykład używasz programu PowerShell dzisiaj i dwa podejścia, aby uzyskać takie same polecenie pracy w trybie NoLanguage.

```powershell
# Using variables in NoLanguage mode is disallowed, so the following will not work
# $vm = Get-VM -Name 'SQL01'
# Start-VM -VM $vm

# You can use pipes to pass data through to commands that accept input from the pipeline
Get-VM -Name 'SQL01' | Start-VM

# You can also wrap subcommands in parentheses and enter them inline as arguments
Start-VM -VM (Get-VM -Name 'SQL01')

# Better yet, use parameter sets that don't require extra data to be passed in when possible
Start-VM -VMName 'SQL01'
```

W przypadku bardziej złożonych wywołania polecenia, które utrudnić takie podejście, rozważ zastosowanie [niejawne remoting](#using-jea-with-implicit-remoting) lub [Tworzenie funkcji niestandardowej](role-capabilities.md#creating-custom-functions) zawijać się funkcje wymagane.

## <a name="using-jea-with-implicit-remoting"></a>Przy użyciu JEA z niejawnych komunikacji zdalnej

PowerShell obsługuje model alternatywnych usług zdalnych gdzie możesz zaimportować polecenia cmdlet serwera proxy z komputera zdalnego na komputerze lokalnym i interakcji z nimi, tak jakby były lokalne polecenia.
To jest nazywana niejawne zdalnych i znajduje się również w [to *Witaj, Twórco skryptów!* wpis w blogu](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).
Niejawne zdalnych jest szczególnie przydatne podczas pracy z JEA, ponieważ umożliwia pracę z poleceniami cmdlet JEA w trybie pełną obsługą języka.
Oznacza to, można używać uzupełniania po naciśnięciu tabulatora, zmienne, manipulowanie obiektami i nawet za pomocą skryptów lokalnych można łatwo automatyzować względem punktu końcowego JEA.
W dowolnym momencie Wywołaj polecenie serwera proxy, dane zostaną wysłane do punktu końcowego JEA na komputerze zdalnym i tam wykonywane.

Niejawne remoting działa przez zaimportowanie poleceń cmdlet z istniejącej sesji programu PowerShell.
Można opcjonalnie prefiksu rzeczowniki każde polecenie cmdlet serwera proxy z ciągiem wybrania rozróżniania, które polecenia są systemu zdalnego.
Moduł tymczasowy skrypt zawierający wszystkie polecenia proxy zostanie utworzona i można używać w czasie trwania lokalnej sesji programu PowerShell.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> Niektóre systemy nie można zaimportować całej sesji JEA ze względu na ograniczenia w poleceniach cmdlet JEA domyślne.
> Aby tego, importować tylko polecenia należy z sesji JEA jawnie zapewniając ich nazwy do `-CommandName` parametru.
> Przyszłej aktualizacji będzie dotyczyć problem z importowaniem całej sesji JEA w systemach.

Jeśli nie można zaimportować sesji JEA ze względu na ograniczenia dotyczące parametrów JEA domyślne, można wykonaj poniższe kroki, aby odfiltrować polecenia domyślne z zaimportowany zestaw.
Nadal będzie można używać poleceń, takich jak `Select-Object` — wystarczy użyjesz lokalnej wersji zainstalowanej na komputerze w sesji JEA zamiast zdalnego.

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

Można również utrwalić proxy poleceń cmdlet z niejawnych zdalnych przy użyciu [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).
Aby uzyskać więcej informacji o niejawne remoting, zapoznaj się w dokumentacji pomocy [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) i [Import-Module](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/import-module).

## <a name="using-jea-programatically"></a>Programowo przy użyciu JEA

JEA można również w systemach automatyzacji i użytkownika aplikacji, takich jak pomoc techniczna wewnętrznych aplikacji i witryn sieci web.
Podejście jest taki sam, jak w przypadku tworzenia aplikacji, która zwróć się do nieograniczonego PowerShell punktów końcowych, ale należy pamiętać, że program należy zwrócić uwagę, że JEA jest ograniczanie poleceń, które mogą być uruchamiane w sesji zdalnej.

W przypadku prostych, jednorazowych zadań, można użyć [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command) do uruchomienia zestawu poleceń za pomocą JEA.

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

Aby sprawdzić, które polecenia są dostępne do użycia podczas łączenia z sesją JEA, uruchom `Get-Command` i iterację wyników, aby sprawdzić, czy są dozwolone parametry.

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

Jeśli tworzysz aplikację C#, można utworzyć obszaru działania programu PowerShell, który nawiązuje połączenie z sesją JEA, określając nazwę konfiguracji w [WSManConnectionInfo](https://msdn.microsoft.com/en-us/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) obiektu.

```csharp

// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
var creds        = // create a PSCredential object here (https://msdn.microsoft.com/en-us/library/system.management.automation.pscredential(v=vs.85).aspx)

WSManConnectionInfo connectionInfo = new WSManConnectionInfo(
                    false,                 // Use SSL
                    computerName,          // Computer name
                    5985,                  // WSMan Port
                    "/wsman",              // WSMan Path
                    string.Format(CultureInfo.InvariantCulture, "http://schemas.microsoft.com/powershell/{0}", configName),  // Connection URI with config name
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

## <a name="using-jea-with-powershell-direct"></a>Przy użyciu JEA bezpośrednio programu PowerShell

Zapewnia funkcji Hyper-V w systemie Windows 10 i Windows Server 2016 [PowerShell bezpośrednio](https://msdn.microsoft.com/en-us/virtualization/hyperv_on_windows/user_guide/vmsession), funkcji, która pozwala administratorom funkcji Hyper-V do zarządzania maszynami wirtualnymi przy użyciu programu PowerShell, niezależnie od konfiguracji sieci lub do zdalnego zarządzania ustawienia na maszynie wirtualnej.

Za pomocą programu PowerShell bezpośrednio i JEA udzielenia dostępu administratora ograniczone funkcji Hyper-V do maszyny Wirtualnej, które mogą być przydatne jeśli utratę łączności sieciowej do maszyny Wirtualnej i należy poprawić ustawienia sieciowe admin centrum danych.

Nie jest dodatkowa konfiguracja wymagane do używania JEA za pośrednictwem programu PowerShell bezpośrednio, ale systemu operacyjnego działającego na maszynie wirtualnej musi należeć do systemu Windows 10 lub Windows Server 2016.
Administrator funkcji Hyper-V można połączyć z punktem końcowym JEA przy użyciu `-VMName` lub `-VMId` parametrów polecenia cmdlet PSRemoting:

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

Zdecydowanie zaleca się utworzenie dedykowanego użytkownika lokalnego z nie innych uprawnień do zarządzania systemem dla administratorów sieci funkcji Hyper-V do użycia.
Należy pamiętać, że nawet nieuprawnionego użytkownika nadal zalogować się do komputera z systemem Windows domyślnie, w tym przy użyciu nieograniczonego programu PowerShell.
Które umożliwią jej Przeglądaj (niektóre) system plików i Dowiedz się więcej na temat środowiska systemu operacyjnego.
Zablokowanie administratora funkcji Hyper-V, aby uzyskiwać dostęp tylko do maszyny Wirtualnej przy użyciu programu PowerShell bezpośrednio z JEA, konieczne będzie Odmowa logowania lokalnego uprawnień do konta JEA administratora funkcji Hyper-V.