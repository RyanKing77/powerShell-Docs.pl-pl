---
ms.date: 06/12/2017
keywords: jea, programu powershell, zabezpieczeń
title: Korzystanie z usługi JEA
ms.openlocfilehash: 539d280aff0b2656a5e9c710acfa468057753027
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686859"
---
# <a name="using-jea"></a>Korzystanie z usługi JEA

> Dotyczy: Windows PowerShell 5.0

W tym temacie opisano różne sposoby, można połączyć się i używać punktu końcowego JEA.

## <a name="using-jea-interactively"></a>Interakcyjne korzystanie z usługi JEA

Jeśli testujesz konfigurację usługi JEA lub proste zadania dla użytkowników do wykonania, można użyć technologii JEA taki sam sposób jak w przypadku regularnego sesji komunikacji zdalnej programu PowerShell.
Remoting złożonych zadań, zaleca się używanie [niejawne remoting](#using-jea-with-implicit-remoting) zamiast ułatwienia dla użytkowników, umożliwiając użytkownikowi korzystanie z danych obiekty lokalnie.

Aby używać technologii JEA interakcyjnie, należy:
- Nazwa komputera, którą jest nawiązywane połączenie (może być komputer lokalny)
- Nazwa punktu końcowego JEA zarejestrowane na tym komputerze
- Poświadczenia dla komputera, które mają dostęp do punktu końcowego usługi JEA

Dysponując tą informacją w kasie, można uruchomić sesji JEA przy użyciu [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) lub [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

Jeśli to konto jest obecnie zalogowano, ma dostęp do punktu końcowego usługi JEA, można pominąć `-Credential` parametru.

Gdy programu PowerShell Monituj zmiany `[localhost]: PS>` będzie wiadomo, że możesz teraz współpracuje z sesji zdalnej usługi JEA.
Możesz uruchomić `Get-Command` do sprawdzenia, jakie polecenia są dostępne.
Należy skontaktować się z administratorem, aby dowiedzieć się, czy istnieją jakieś ograniczenia dotyczące dostępnych parametrów lub wartości parametrów dozwolony.

Przypominamy sesje JEA działają w trybie NoLanguage, więc niektóre metody, zazwyczaj przy użyciu programu PowerShell mogą być niedostępne.
Na przykład nie można używać zmiennych do przechowywania danych lub sprawdzić właściwości na obiekty zwrócone przez polecenia cmdlet.
Poniżej przedstawiono przykład, na przykład używasz programu PowerShell już dziś i dwie metody, aby uzyskać takie same polecenie pracy w trybie NoLanguage.

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

Dla bardziej złożonych wywołania polecenia, które utrudniają takie podejście, należy wziąć pod uwagę przy użyciu [niejawne remoting](#using-jea-with-implicit-remoting) lub [tworzenia niestandardowych funkcji](role-capabilities.md#creating-custom-functions) , opakowywanie funkcji wygodną pracę.

## <a name="using-jea-with-implicit-remoting"></a>Korzystanie z usługi JEA przy użyciu komunikacji zdalnej niejawne

PowerShell obsługuje model alternatywnych wywołaniem funkcji zdalnych, gdzie można zaimportować polecenia cmdlet serwera proxy z komputera zdalnego na komputerze lokalnym i wchodzić w interakcje z nimi tak, jakby były one poleceń lokalnych.
To jest nazywana niejawne wywołaniem funkcji zdalnych, a została wyjaśniona w programie [to *Hey, Scripting Guy!* wpis w blogu](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).
Niejawne komunikacji zdalnej jest szczególnie przydatne podczas pracy z JEA, ponieważ umożliwia pracę z poleceniami cmdlet usługi JEA, w trybie pełną obsługą języka.
Oznacza to, użyj uzupełniania po naciśnięciu tabulatora, zmienne, manipulowania obiektami i nawet łatwiej zautomatyzować względem punktu końcowego JEA za pomocą skryptów lokalnych.
W dowolnym momencie możesz wywołać polecenie proxy, dane będą wysyłane do punktu końcowego JEA na komputerze zdalnym i tam wykonywane.

Niejawne remoting działa przez zaimportowanie poleceń cmdlet z istniejącej sesji programu PowerShell.
Można opcjonalnie poprzedzić rzeczowniki każdego polecenia cmdlet serwera proxy z ciągu do odróżniania poleceń, które służą do systemu zdalnego.
Moduł tymczasowy skrypt zawierający wszystkie polecenia proxy zostanie utworzony i może służyć do czasu trwania swojej lokalnej sesji programu PowerShell.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> Niektóre systemy nie można zaimportować całej sesji usługi JEA ze względu na ograniczenia w poleceniach cmdlet usługi JEA domyślne.
> Aby obejść ten problem, importować tylko polecenia, które należy z sesji JEA, podając jawnie ich nazwy do `-CommandName` parametru.
> Przyszła aktualizacja będzie dotyczyć problem z importowaniem całej sesji usługi JEA w systemach.

Jeśli nie można zaimportować sesję JEA ze względu na ograniczenia dotyczące parametrów JEA domyślne można postępuj zgodnie z instrukcjami poniżej, aby odfiltrować domyślnych poleceń z zaimportowanych zestawu.
Nadal będzie można używać poleceń, takich jak `Select-Object` — po prostu użyjesz lokalna wersja zainstalowana na danym komputerze zamiast zdalnego podczas sesji JEA.

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

Można również utrwalić serwerem proxy poleceń cmdlet z przy użyciu komunikacji zdalnej niejawne [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).
Aby uzyskać więcej informacji na temat niejawne komunikacji zdalnej Sprawdź w dokumentacji pomocy [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) i [Import-Module](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/import-module).

## <a name="using-jea-programatically"></a>Programowo przy użyciu usługi JEA

JEA umożliwia także w systemach automatyzacji oraz w aplikacji użytkownika, takich jak witryny sieci web i aplikacji wewnętrznej pomocy technicznej.
To podejście jest taki sam, jak w przypadku tworzenia aplikacji komunikować się z nieograniczonego punkty końcowe programu PowerShell, ale należy pamiętać, że program należy pamiętać, że JEA jest ograniczenie poleceń, które mogą być uruchamiane w sesji zdalnej.

W przypadku prostych, jednorazowych zadań, można użyć [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) do uruchomienia zestawu poleceń przy użyciu technologii JEA.

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

Aby sprawdzić, jakie polecenia są dostępne do użycia podczas łączenia z sesją usługi JEA, uruchom `Get-Command` i iteracyjnego przeglądania wyników, aby sprawdzić, czy są dozwolone parametry.

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

Jeśli kompilujesz aplikację C#, można utworzyć obszaru działania programu PowerShell, który nawiązuje połączenie z sesją usługi JEA, określając nazwę konfiguracji w [WSManConnectionInfo](https://msdn.microsoft.com/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) obiektu.

```csharp

// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
var creds        = // create a PSCredential object here (https://msdn.microsoft.com/library/system.management.automation.pscredential(v=vs.85).aspx)

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

## <a name="using-jea-with-powershell-direct"></a>Korzystanie z usługi JEA przy użyciu programu PowerShell bezpośrednio

Funkcji Hyper-V w systemie Windows 10 i Windows Server 2016 oferuje [programu PowerShell Direct](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/vmsession), funkcji, która umożliwia administratorom funkcji Hyper-V do zarządzania maszynami wirtualnymi przy użyciu programu PowerShell niezależnie od konfiguracji sieci lub zdalnego zarządzania ustawienia na maszynie wirtualnej.

Za pomocą programu PowerShell bezpośrednio i JEA oferowanie dostęp ograniczony administrator funkcji Hyper-V maszyny Wirtualnej, które mogą być przydatne jeśli utracić łączność sieciową z maszyną wirtualną, a konieczne naprawienie ustawień sieci przez administratora sieci centrum danych.

Dodatkowa konfiguracja nie jest wymagane do używania usługi JEA za pośrednictwem programu PowerShell Direct, ale system operacyjny działający na maszynie wirtualnej musi należeć do systemu Windows 10 lub Windows Server 2016.
Administrator funkcji Hyper-V można połączyć z punktem końcowym usługi JEA przy użyciu `-VMName` lub `-VMId` parametry PSRemoting poleceń cmdlet:

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

Zdecydowanie zaleca się utworzenie dedykowanego użytkownika lokalnego z żadnych innych praw do zarządzania systemem dla administratorów funkcji Hyper-V użyć.
Należy pamiętać, że nawet nieuprawnionego użytkownika nadal logować się do maszyny Windows domyślnie, w tym o korzystaniu z użyciem programu PowerShell.
Która umożliwi im Przeglądaj (część) w systemie plików i Dowiedz się więcej o środowisku systemu operacyjnego.
Zablokować tylko administrator funkcji Hyper-V może uzyskiwać dostęp tylko do maszyny Wirtualnej przy użyciu programu PowerShell bezpośrednio przy użyciu technologii JEA, należy zablokować prawa logowania lokalnego na konto usługi JEA administratora funkcji Hyper-V.