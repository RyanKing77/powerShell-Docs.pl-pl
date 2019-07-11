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
# <a name="using-jea"></a><span data-ttu-id="93602-103">Korzystanie z usługi JEA</span><span class="sxs-lookup"><span data-stu-id="93602-103">Using JEA</span></span>

<span data-ttu-id="93602-104">W tym artykule opisano różne sposoby, można połączyć się i używać punktu końcowego JEA.</span><span class="sxs-lookup"><span data-stu-id="93602-104">This article describes the various ways you can connect to and use a JEA endpoint.</span></span>

## <a name="using-jea-interactively"></a><span data-ttu-id="93602-105">Interakcyjne korzystanie z usługi JEA</span><span class="sxs-lookup"><span data-stu-id="93602-105">Using JEA interactively</span></span>

<span data-ttu-id="93602-106">Jeśli testujesz konfigurację usługi JEA lub proste zadania dla użytkowników, można użyć technologii JEA taki sam sposób jak w przypadku regularnego sesji komunikacji zdalnej programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="93602-106">If you're testing your JEA configuration or have simple tasks for users, you can use JEA the same way you would a regular PowerShell remoting session.</span></span> <span data-ttu-id="93602-107">Remoting złożonych zadań, zaleca się używać [niejawne remoting](#using-jea-with-implicit-remoting).</span><span class="sxs-lookup"><span data-stu-id="93602-107">For complex remoting tasks, it's recommended to use [implicit remoting](#using-jea-with-implicit-remoting).</span></span> <span data-ttu-id="93602-108">Niejawne remoting umożliwia użytkownikom do pracy z obiektami danych lokalnie.</span><span class="sxs-lookup"><span data-stu-id="93602-108">Implicit remoting allows users to operate with the data objects locally.</span></span>

<span data-ttu-id="93602-109">Aby używać technologii JEA interakcyjnie, potrzebne są:</span><span class="sxs-lookup"><span data-stu-id="93602-109">To use JEA interactively, you need:</span></span>

- <span data-ttu-id="93602-110">Nazwa komputera, na którym chcesz się połączyć (może być komputer lokalny)</span><span class="sxs-lookup"><span data-stu-id="93602-110">The name of the computer you're connecting to (can be the local machine)</span></span>
- <span data-ttu-id="93602-111">Nazwa punktu końcowego JEA zarejestrowane na tym komputerze</span><span class="sxs-lookup"><span data-stu-id="93602-111">The name of the JEA endpoint registered on that computer</span></span>
- <span data-ttu-id="93602-112">Poświadczenia, które mają dostęp do punktu końcowego JEA na tym komputerze</span><span class="sxs-lookup"><span data-stu-id="93602-112">Credentials that have access to the JEA endpoint on that computer</span></span>

<span data-ttu-id="93602-113">Biorąc pod uwagę te informacje, można uruchomić sesji JEA przy użyciu [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) lub [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="93602-113">Given that information, you can start a JEA session using the [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) or [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlets.</span></span>

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

<span data-ttu-id="93602-114">Jeśli konto ma dostęp do punktu końcowego JEA, można pominąć **poświadczeń** parametru.</span><span class="sxs-lookup"><span data-stu-id="93602-114">If the current user account has access to the JEA endpoint, you can omit the **Credential** parameter.</span></span>

<span data-ttu-id="93602-115">Gdy programu PowerShell Monituj zmiany `[localhost]: PS>` wiesz, że możesz teraz niekorzystające z sesji zdalnej usługi JEA.</span><span class="sxs-lookup"><span data-stu-id="93602-115">When the PowerShell prompt changes to `[localhost]: PS>` you know that you're now interacting with the remote JEA session.</span></span> <span data-ttu-id="93602-116">Możesz uruchomić `Get-Command` do sprawdzenia, jakie polecenia są dostępne.</span><span class="sxs-lookup"><span data-stu-id="93602-116">You can run `Get-Command` to check which commands are available.</span></span> <span data-ttu-id="93602-117">Zapoznaj się z administratorem, aby dowiedzieć się, czy istnieją jakieś ograniczenia dotyczące dostępnych parametrów lub wartości parametrów dozwolone.</span><span class="sxs-lookup"><span data-stu-id="93602-117">Consult with your administrator to learn if there are any restrictions on the available parameters or allowed parameter values.</span></span>

<span data-ttu-id="93602-118">Należy pamiętać, że w sesji JEA działają w trybie NoLanguage.</span><span class="sxs-lookup"><span data-stu-id="93602-118">Remember, JEA sessions operate in NoLanguage mode.</span></span> <span data-ttu-id="93602-119">Niektóre metody, zazwyczaj przy użyciu programu PowerShell mogą nie być dostępne.</span><span class="sxs-lookup"><span data-stu-id="93602-119">Some of the ways you typically use PowerShell may not be available.</span></span> <span data-ttu-id="93602-120">Na przykład nie można używać zmiennych do przechowywania danych lub sprawdzić właściwości na obiekty zwrócone przez polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="93602-120">For instance, you can't use variables to store data or inspect the properties on objects returned from cmdlets.</span></span> <span data-ttu-id="93602-121">Poniższy przykład przedstawia dwa podejścia do tego samego polecenia do pracy w trybie NoLanguage get.</span><span class="sxs-lookup"><span data-stu-id="93602-121">The following example shows two approaches to get the same commands to work in NoLanguage mode.</span></span>

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

<span data-ttu-id="93602-122">Dla bardziej złożonych wywołania polecenia, które utrudniają takie podejście, należy wziąć pod uwagę przy użyciu [niejawne remoting](#using-jea-with-implicit-remoting) lub [tworzenia niestandardowych funkcji](role-capabilities.md#creating-custom-functions) , opakowywanie funkcji wymaganych.</span><span class="sxs-lookup"><span data-stu-id="93602-122">For more complex command invocations that make this approach difficult, consider using [implicit remoting](#using-jea-with-implicit-remoting) or [creating custom functions](role-capabilities.md#creating-custom-functions) that wrap the functionality you require.</span></span>

## <a name="using-jea-with-implicit-remoting"></a><span data-ttu-id="93602-123">Korzystanie z usługi JEA przy użyciu komunikacji zdalnej niejawne</span><span class="sxs-lookup"><span data-stu-id="93602-123">Using JEA with implicit remoting</span></span>

<span data-ttu-id="93602-124">Program PowerShell ma modelu niejawne komunikacji zdalnej, którego można zaimportować polecenia cmdlet serwera proxy z komputera zdalnego i wchodzić w interakcje z nimi tak, jakby były one poleceń lokalnych.</span><span class="sxs-lookup"><span data-stu-id="93602-124">PowerShell has an implicit remoting model that lets you import proxy cmdlets from a remote machine and interact with them as if they were local commands.</span></span> <span data-ttu-id="93602-125">Niejawne remoting zostało wyjaśnione w tym **Hey, Scripting Guy!**</span><span class="sxs-lookup"><span data-stu-id="93602-125">Implicit remoting is explained in this **Hey, Scripting Guy!**</span></span> <span data-ttu-id="93602-126">[wpis w blogu](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).</span><span class="sxs-lookup"><span data-stu-id="93602-126">[blog post](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).</span></span>
<span data-ttu-id="93602-127">Niejawne komunikacji zdalnej jest przydatne podczas pracy z JEA, ponieważ umożliwia pracę z poleceniami cmdlet usługi JEA, w trybie pełną obsługą języka.</span><span class="sxs-lookup"><span data-stu-id="93602-127">Implicit remoting is useful when working with JEA because it allows you to work with JEA cmdlets in a full language mode.</span></span> <span data-ttu-id="93602-128">Można użyć uzupełniania po naciśnięciu tabulatora, zmienne, manipulowania obiektami, a nawet w celu zautomatyzowania zadań w odniesieniu do punktu końcowego JEA za pomocą skryptów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="93602-128">You can use tab completion, variables, manipulate objects, and even use local scripts to automate tasks against a JEA endpoint.</span></span> <span data-ttu-id="93602-129">W dowolnym momencie możesz wywołać polecenie proxy, dane są wysyłane do punktu końcowego JEA na komputerze zdalnym i tam wykonywane.</span><span class="sxs-lookup"><span data-stu-id="93602-129">Anytime you invoke a proxy command, the data is sent to the JEA endpoint on the remote machine and executed there.</span></span>

<span data-ttu-id="93602-130">Niejawne remoting działa przez zaimportowanie poleceń cmdlet z istniejącej sesji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="93602-130">Implicit remoting works by importing cmdlets from an existing PowerShell session.</span></span> <span data-ttu-id="93602-131">Można opcjonalnie prefiksów rzeczowników każdego polecenia cmdlet serwera proxy z ciągiem wybrane.</span><span class="sxs-lookup"><span data-stu-id="93602-131">You can optionally choose to prefix the nouns of each proxy cmdlet with a string of your choosing.</span></span> <span data-ttu-id="93602-132">Prefiks umożliwia rozróżnianie poleceń, które służą do systemu zdalnego.</span><span class="sxs-lookup"><span data-stu-id="93602-132">The prefix allows you to distinguish the commands that are for the remote system.</span></span> <span data-ttu-id="93602-133">Moduł tymczasowy skrypt zawierający wszystkie polecenia serwera proxy jest tworzony i zaimportować przez okres lokalnej sesji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="93602-133">A temporary script module containing all the proxy commands is created and imported for the duration of your local PowerShell session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> <span data-ttu-id="93602-134">Niektóre systemy nie można zaimportować całej sesji usługi JEA ze względu na ograniczenia w poleceniach cmdlet usługi JEA domyślne.</span><span class="sxs-lookup"><span data-stu-id="93602-134">Some systems may not be able to import an entire JEA session due to constraints in the default JEA cmdlets.</span></span> <span data-ttu-id="93602-135">Aby obejść ten problem, importować tylko polecenia, które należy z sesji JEA, podając jawnie ich nazwy do `-CommandName` parametru.</span><span class="sxs-lookup"><span data-stu-id="93602-135">To get around this, only import the commands you need from the JEA session by explicitly providing their names to the `-CommandName` parameter.</span></span> <span data-ttu-id="93602-136">Przyszła aktualizacja będzie dotyczyć problem z importowaniem całej sesji usługi JEA w systemach.</span><span class="sxs-lookup"><span data-stu-id="93602-136">A future update will address the issue with importing entire JEA sessions on affected systems.</span></span>

<span data-ttu-id="93602-137">Jeśli nie możesz zaimportować sesji JEA ze względu na ograniczenia JEA w domyślnych parametrach, wykonaj poniższe kroki, aby odfiltrować domyślnych poleceń z zaimportowanych zestawu.</span><span class="sxs-lookup"><span data-stu-id="93602-137">If you're unable to import a JEA session because of JEA constraints on the default parameters, follow the steps below to filter out the default commands from the imported set.</span></span> <span data-ttu-id="93602-138">Możesz kontynuować używanie poleceń, takich jak `Select-Object`, ale po prostu użyjemy lokalna wersja zainstalowana na danym komputerze zamiast zaimportowane z sesji zdalnej usługi JEA.</span><span class="sxs-lookup"><span data-stu-id="93602-138">You can continue use commands like `Select-Object`, but you'll just use the local version installed on your computer instead of the one imported from the remote JEA session.</span></span>

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

<span data-ttu-id="93602-139">Można również utrwalić serwerem proxy poleceń cmdlet z przy użyciu komunikacji zdalnej niejawne [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).</span><span class="sxs-lookup"><span data-stu-id="93602-139">You can also persist the proxied cmdlets from implicit remoting using [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).</span></span>
<span data-ttu-id="93602-140">Aby uzyskać więcej informacji dotyczących niejawnych komunikacji zdalnej, zobacz dokumentację dla [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) i [Import-Module](/powershell/microsoft.powershell.core/import-module).</span><span class="sxs-lookup"><span data-stu-id="93602-140">For more information about implicit remoting, see the documentation for [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) and [Import-Module](/powershell/microsoft.powershell.core/import-module).</span></span>

## <a name="using-jea-programmatically"></a><span data-ttu-id="93602-141">Programowe korzystanie z usługi JEA</span><span class="sxs-lookup"><span data-stu-id="93602-141">Using JEA programmatically</span></span>

<span data-ttu-id="93602-142">JEA umożliwia także w systemach automatyzacji oraz w aplikacji użytkownika, takich jak aplikacje wewnętrznej pomocy technicznej i witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="93602-142">JEA can also be used in automation systems and in user applications, such as in-house helpdesk apps and websites.</span></span> <span data-ttu-id="93602-143">To podejście jest takie samo, jak podczas tworzenia aplikacji, którzy komunikują się z użyciem środowiska PowerShell punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="93602-143">The approach is the same as that for building apps that talk to unconstrained PowerShell endpoints.</span></span> <span data-ttu-id="93602-144">Upewnij się, że program jest przeznaczona do pracy z ograniczenia nakładane przez usługi JEA.</span><span class="sxs-lookup"><span data-stu-id="93602-144">Ensure the program is designed to work with limitation imposed by JEA.</span></span>

<span data-ttu-id="93602-145">W przypadku prostych, jednorazowych zadań, można użyć [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) do uruchamiania poleceń w sesji JEA.</span><span class="sxs-lookup"><span data-stu-id="93602-145">For simple, one-off tasks, you can use [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) to run commands in a JEA session.</span></span>

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

<span data-ttu-id="93602-146">Aby sprawdzić, jakie polecenia są dostępne do użycia podczas łączenia z sesją usługi JEA, uruchom `Get-Command` i iteracyjnego przeglądania wyników, aby sprawdzić, czy są dozwolone parametry.</span><span class="sxs-lookup"><span data-stu-id="93602-146">To check which commands are available for use when you connect to a JEA session, run `Get-Command` and iterate through the results to check for the allowed parameters.</span></span>

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

<span data-ttu-id="93602-147">Jeśli tworzysz C# aplikacji, można utworzyć obszaru działania programu PowerShell, który nawiązuje połączenie z sesją usługi JEA, określając nazwę konfiguracji w [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) obiektu.</span><span class="sxs-lookup"><span data-stu-id="93602-147">If you're building a C# app, you can create a PowerShell runspace that connects to a JEA session by specifying the configuration name in a [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) object.</span></span>

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

## <a name="using-jea-with-powershell-direct"></a><span data-ttu-id="93602-148">Korzystanie z usługi JEA przy użyciu programu PowerShell bezpośrednio</span><span class="sxs-lookup"><span data-stu-id="93602-148">Using JEA with PowerShell Direct</span></span>

<span data-ttu-id="93602-149">Funkcji Hyper-V w systemie Windows 10 i Windows Server 2016 oferuje [programu PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), funkcja, która umożliwia administratorom funkcji Hyper-V do zarządzania maszynami wirtualnymi przy użyciu programu PowerShell niezależnie od konfiguracji sieci lub zdalnego zarządzania ustawienia na maszynie wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="93602-149">Hyper-V in Windows 10 and Windows Server 2016 offers [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), a feature that allows Hyper-V administrators to manage virtual machines with PowerShell regardless of the network configuration or remote management settings on the virtual machine.</span></span>

<span data-ttu-id="93602-150">Za pomocą programu PowerShell bezpośrednio i JEA oferowanie dostęp ograniczony administrator funkcji Hyper-V maszyny Wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="93602-150">You can use PowerShell Direct with JEA to give a Hyper-V administrator limited access to your VM.</span></span>
<span data-ttu-id="93602-151">Może to być przydatne, jeśli utracić łączność sieciową z maszyną wirtualną i potrzebujesz administratora sieci centrów danych o poprawienie ustawień sieci.</span><span class="sxs-lookup"><span data-stu-id="93602-151">This can be useful if you lose network connectivity to your VM and need a datacenter admin to fix the network settings.</span></span>

<span data-ttu-id="93602-152">Żadne dodatkowe czynności konfiguracyjne wymagane jest wprowadzenie JEA za pośrednictwem programu PowerShell Direct.</span><span class="sxs-lookup"><span data-stu-id="93602-152">No additional configuration is required to use JEA over PowerShell Direct.</span></span> <span data-ttu-id="93602-153">Jednak system operacyjny gościa, które są uruchomione na maszynie wirtualnej musi być systemu Windows 10, Windows Server 2016 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="93602-153">However, the guest operating system running inside the virtual machine must be Windows 10, Windows Server 2016, or higher.</span></span> <span data-ttu-id="93602-154">Administrator funkcji Hyper-V można połączyć z punktem końcowym usługi JEA przy użyciu `-VMName` lub `-VMId` parametry PSRemoting poleceń cmdlet:</span><span class="sxs-lookup"><span data-stu-id="93602-154">The Hyper-V admin can connect to the JEA endpoint by using the `-VMName` or `-VMId` parameters on PSRemoting cmdlets:</span></span>

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

<span data-ttu-id="93602-155">Zalecane jest, że Utwórz dedykowane konto użytkownika z minimalnych uprawnień niezbędnych do zarządzania systemem do użytku przez administratora funkcji Hyper-V.</span><span class="sxs-lookup"><span data-stu-id="93602-155">It's recommended you create a dedicated user account with the minimum rights needed to manage the system for use by a Hyper-V administrator.</span></span> <span data-ttu-id="93602-156">Należy pamiętać, że nawet nieuprawnionego użytkownika może zalogować się do maszyny Windows domyślnie, w tym o korzystaniu z użyciem programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="93602-156">Remember, even an unprivileged user can sign into a Windows machine by default, including using unconstrained PowerShell.</span></span> <span data-ttu-id="93602-157">Umożliwiające im Przeglądaj system plików i Dowiedz się więcej o środowisku systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="93602-157">That allows them to browse the file system and learn more about your OS environment.</span></span> <span data-ttu-id="93602-158">Aby zablokować administratora funkcji Hyper-V i ograniczyć ich dostęp tylko do maszyny Wirtualnej przy użyciu programu PowerShell bezpośrednio z usługi JEA, możesz odmówić uprawnień logowania do konta usługi JEA administratora funkcji Hyper-V.</span><span class="sxs-lookup"><span data-stu-id="93602-158">To lock down a Hyper-V administrator and limit them to only access a VM using PowerShell Direct with JEA, you must deny local logon rights to the Hyper-V admin's JEA account.</span></span>
