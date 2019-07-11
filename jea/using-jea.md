---
ms.date: 07/10/2019
keywords: jea, programu powershell, zabezpieczeń
title: Korzystanie z usługi JEA
ms.openlocfilehash: 8f3cc9186c61a2ae5b64eb3dc4f72ca83f1a58c5
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734221"
---
# <a name="using-jea"></a>Korzystanie z usługi JEA

W tym artykule opisano różne sposoby, można połączyć się i używać punktu końcowego JEA.

## <a name="using-jea-interactively"></a>Interakcyjne korzystanie z usługi JEA

Jeśli testujesz konfigurację usługi JEA lub proste zadania dla użytkowników, można użyć technologii JEA taki sam sposób jak w przypadku regularnego sesji komunikacji zdalnej programu PowerShell. Remoting złożonych zadań, zaleca się używać [niejawne remoting](#using-jea-with-implicit-remoting). Niejawne remoting umożliwia użytkownikom do pracy z obiektami danych lokalnie.

Aby używać technologii JEA interakcyjnie, potrzebne są:

- Nazwa komputera, na którym chcesz się połączyć (może być komputer lokalny)
- Nazwa punktu końcowego JEA zarejestrowane na tym komputerze
- Poświadczenia, które mają dostęp do punktu końcowego JEA na tym komputerze

Biorąc pod uwagę te informacje, można uruchomić sesji JEA przy użyciu [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) lub [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) polecenia cmdlet.

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

Jeśli konto ma dostęp do punktu końcowego JEA, można pominąć **poświadczeń** parametru.

Gdy programu PowerShell Monituj zmiany `[localhost]: PS>` wiesz, że możesz teraz niekorzystające z sesji zdalnej usługi JEA. Możesz uruchomić `Get-Command` do sprawdzenia, jakie polecenia są dostępne. Zapoznaj się z administratorem, aby dowiedzieć się, czy istnieją jakieś ograniczenia dotyczące dostępnych parametrów lub wartości parametrów dozwolone.

Należy pamiętać, że w sesji JEA działają w trybie NoLanguage. Niektóre metody, zazwyczaj przy użyciu programu PowerShell mogą nie być dostępne. Na przykład nie można używać zmiennych do przechowywania danych lub sprawdzić właściwości na obiekty zwrócone przez polecenia cmdlet. Poniższy przykład przedstawia dwa podejścia do tego samego polecenia do pracy w trybie NoLanguage get.

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

Dla bardziej złożonych wywołania polecenia, które utrudniają takie podejście, należy wziąć pod uwagę przy użyciu [niejawne remoting](#using-jea-with-implicit-remoting) lub [tworzenia niestandardowych funkcji](role-capabilities.md#creating-custom-functions) , opakowywanie funkcji wymaganych.

## <a name="using-jea-with-implicit-remoting"></a>Korzystanie z usługi JEA przy użyciu komunikacji zdalnej niejawne

Program PowerShell ma modelu niejawne komunikacji zdalnej, którego można zaimportować polecenia cmdlet serwera proxy z komputera zdalnego i wchodzić w interakcje z nimi tak, jakby były one poleceń lokalnych. Niejawne remoting zostało wyjaśnione w tym **Hey, Scripting Guy!** [wpis w blogu](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).
Niejawne komunikacji zdalnej jest przydatne podczas pracy z JEA, ponieważ umożliwia pracę z poleceniami cmdlet usługi JEA, w trybie pełną obsługą języka. Można użyć uzupełniania po naciśnięciu tabulatora, zmienne, manipulowania obiektami, a nawet w celu zautomatyzowania zadań w odniesieniu do punktu końcowego JEA za pomocą skryptów lokalnych. W dowolnym momencie możesz wywołać polecenie proxy, dane są wysyłane do punktu końcowego JEA na komputerze zdalnym i tam wykonywane.

Niejawne remoting działa przez zaimportowanie poleceń cmdlet z istniejącej sesji programu PowerShell. Można opcjonalnie prefiksów rzeczowników każdego polecenia cmdlet serwera proxy z ciągiem wybrane. Prefiks umożliwia rozróżnianie poleceń, które służą do systemu zdalnego. Moduł tymczasowy skrypt zawierający wszystkie polecenia serwera proxy jest tworzony i zaimportować przez okres lokalnej sesji programu PowerShell.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> Niektóre systemy nie można zaimportować całej sesji usługi JEA ze względu na ograniczenia w poleceniach cmdlet usługi JEA domyślne. Aby obejść ten problem, importować tylko polecenia, które należy z sesji JEA, podając jawnie ich nazwy do `-CommandName` parametru. Przyszła aktualizacja będzie dotyczyć problem z importowaniem całej sesji usługi JEA w systemach.

Jeśli nie możesz zaimportować sesji JEA ze względu na ograniczenia JEA w domyślnych parametrach, wykonaj poniższe kroki, aby odfiltrować domyślnych poleceń z zaimportowanych zestawu. Możesz kontynuować używanie poleceń, takich jak `Select-Object`, ale po prostu użyjemy lokalna wersja zainstalowana na danym komputerze zamiast zaimportowane z sesji zdalnej usługi JEA.

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

Można również utrwalić serwerem proxy poleceń cmdlet z przy użyciu komunikacji zdalnej niejawne [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).
Aby uzyskać więcej informacji dotyczących niejawnych komunikacji zdalnej, zobacz dokumentację dla [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) i [Import-Module](/powershell/microsoft.powershell.core/import-module).

## <a name="using-jea-programmatically"></a>Programowe korzystanie z usługi JEA

JEA umożliwia także w systemach automatyzacji oraz w aplikacji użytkownika, takich jak aplikacje wewnętrznej pomocy technicznej i witryn sieci Web. To podejście jest takie samo, jak podczas tworzenia aplikacji, którzy komunikują się z użyciem środowiska PowerShell punktów końcowych. Upewnij się, że program jest przeznaczona do pracy z ograniczenia nakładane przez usługi JEA.

W przypadku prostych, jednorazowych zadań, można użyć [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) do uruchamiania poleceń w sesji JEA.

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

Aby sprawdzić, jakie polecenia są dostępne do użycia podczas łączenia z sesją usługi JEA, uruchom `Get-Command` i iteracyjnego przeglądania wyników, aby sprawdzić, czy są dozwolone parametry.

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

Jeśli tworzysz C# aplikacji, można utworzyć obszaru działania programu PowerShell, który nawiązuje połączenie z sesją usługi JEA, określając nazwę konfiguracji w [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) obiektu.

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

## <a name="using-jea-with-powershell-direct"></a>Korzystanie z usługi JEA przy użyciu programu PowerShell bezpośrednio

Funkcji Hyper-V w systemie Windows 10 i Windows Server 2016 oferuje [programu PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), funkcja, która umożliwia administratorom funkcji Hyper-V do zarządzania maszynami wirtualnymi przy użyciu programu PowerShell niezależnie od konfiguracji sieci lub zdalnego zarządzania ustawienia na maszynie wirtualnej.

Za pomocą programu PowerShell bezpośrednio i JEA oferowanie dostęp ograniczony administrator funkcji Hyper-V maszyny Wirtualnej.
Może to być przydatne, jeśli utracić łączność sieciową z maszyną wirtualną i potrzebujesz administratora sieci centrów danych o poprawienie ustawień sieci.

Żadne dodatkowe czynności konfiguracyjne wymagane jest wprowadzenie JEA za pośrednictwem programu PowerShell Direct. Jednak system operacyjny gościa, które są uruchomione na maszynie wirtualnej musi być systemu Windows 10, Windows Server 2016 lub nowszej. Administrator funkcji Hyper-V można połączyć z punktem końcowym usługi JEA przy użyciu `-VMName` lub `-VMId` parametry PSRemoting poleceń cmdlet:

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

Zalecane jest, że Utwórz dedykowane konto użytkownika z minimalnych uprawnień niezbędnych do zarządzania systemem do użytku przez administratora funkcji Hyper-V. Należy pamiętać, że nawet nieuprawnionego użytkownika może zalogować się do maszyny Windows domyślnie, w tym o korzystaniu z użyciem programu PowerShell. Umożliwiające im Przeglądaj system plików i Dowiedz się więcej o środowisku systemu operacyjnego. Aby zablokować administratora funkcji Hyper-V i ograniczyć ich dostęp tylko do maszyny Wirtualnej przy użyciu programu PowerShell bezpośrednio z usługi JEA, możesz odmówić uprawnień logowania do konta usługi JEA administratora funkcji Hyper-V.
