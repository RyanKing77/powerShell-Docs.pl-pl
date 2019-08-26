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
# <a name="using-jea"></a><span data-ttu-id="b3518-103">Korzystanie z usługi JEA</span><span class="sxs-lookup"><span data-stu-id="b3518-103">Using JEA</span></span>

<span data-ttu-id="b3518-104">W tym artykule opisano różne sposoby nawiązywania połączenia z punktem końcowym JEA i korzystania z niego.</span><span class="sxs-lookup"><span data-stu-id="b3518-104">This article describes the various ways you can connect to and use a JEA endpoint.</span></span>

## <a name="using-jea-interactively"></a><span data-ttu-id="b3518-105">Korzystanie z usługi JEA interaktywnie</span><span class="sxs-lookup"><span data-stu-id="b3518-105">Using JEA interactively</span></span>

<span data-ttu-id="b3518-106">Jeśli testujesz konfigurację usługi JEA lub masz proste zadania dla użytkowników, możesz użyć JEA w taki sam sposób jak w przypadku zwykłej sesji komunikacji zdalnej programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b3518-106">If you're testing your JEA configuration or have simple tasks for users, you can use JEA the same way you would a regular PowerShell remoting session.</span></span> <span data-ttu-id="b3518-107">W przypadku złożonych zadań komunikacji zdalnej zaleca się użycie niejawnych [usług zdalnych](#using-jea-with-implicit-remoting).</span><span class="sxs-lookup"><span data-stu-id="b3518-107">For complex remoting tasks, it's recommended to use [implicit remoting](#using-jea-with-implicit-remoting).</span></span> <span data-ttu-id="b3518-108">Niejawne komunikacja zdalna pozwala użytkownikom na pracę z obiektami danych lokalnie.</span><span class="sxs-lookup"><span data-stu-id="b3518-108">Implicit remoting allows users to operate with the data objects locally.</span></span>

<span data-ttu-id="b3518-109">Aby korzystać z usługi JEA w sposób interaktywny, potrzebne są:</span><span class="sxs-lookup"><span data-stu-id="b3518-109">To use JEA interactively, you need:</span></span>

- <span data-ttu-id="b3518-110">Nazwa komputera, z którym nawiązujesz połączenie (może to być komputer lokalny)</span><span class="sxs-lookup"><span data-stu-id="b3518-110">The name of the computer you're connecting to (can be the local machine)</span></span>
- <span data-ttu-id="b3518-111">Nazwa punktu końcowego JEA zarejestrowanego na tym komputerze</span><span class="sxs-lookup"><span data-stu-id="b3518-111">The name of the JEA endpoint registered on that computer</span></span>
- <span data-ttu-id="b3518-112">Poświadczenia, które mają dostęp do punktu końcowego JEA na tym komputerze</span><span class="sxs-lookup"><span data-stu-id="b3518-112">Credentials that have access to the JEA endpoint on that computer</span></span>

<span data-ttu-id="b3518-113">Uwzględniając te informacje, można uruchomić sesję JEA przy użyciu polecenia cmdlet [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) lub [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) .</span><span class="sxs-lookup"><span data-stu-id="b3518-113">Given that information, you can start a JEA session using the [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) or [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlets.</span></span>

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

<span data-ttu-id="b3518-114">Jeśli bieżące konto użytkownika ma dostęp do punktu końcowego JEA, możesz pominąć parametr **Credential** .</span><span class="sxs-lookup"><span data-stu-id="b3518-114">If the current user account has access to the JEA endpoint, you can omit the **Credential** parameter.</span></span>

<span data-ttu-id="b3518-115">Po wyświetleniu monitu `[localhost]: PS>` programu PowerShell z informacją o tym, że teraz korzystasz z sesji zdalnej jea.</span><span class="sxs-lookup"><span data-stu-id="b3518-115">When the PowerShell prompt changes to `[localhost]: PS>` you know that you're now interacting with the remote JEA session.</span></span> <span data-ttu-id="b3518-116">Można uruchomić `Get-Command` polecenie, aby sprawdzić, które polecenia są dostępne.</span><span class="sxs-lookup"><span data-stu-id="b3518-116">You can run `Get-Command` to check which commands are available.</span></span> <span data-ttu-id="b3518-117">Skontaktuj się z administratorem, aby dowiedzieć się, czy istnieją jakiekolwiek ograniczenia dotyczące dostępnych parametrów lub dozwolonych wartości parametrów.</span><span class="sxs-lookup"><span data-stu-id="b3518-117">Consult with your administrator to learn if there are any restrictions on the available parameters or allowed parameter values.</span></span>

<span data-ttu-id="b3518-118">Należy pamiętać, że sesje JEA działają w trybie NoLanguage.</span><span class="sxs-lookup"><span data-stu-id="b3518-118">Remember, JEA sessions operate in NoLanguage mode.</span></span> <span data-ttu-id="b3518-119">Niektóre ze sposobów, z których zazwyczaj korzystasz z programu PowerShell, mogą nie być dostępne.</span><span class="sxs-lookup"><span data-stu-id="b3518-119">Some of the ways you typically use PowerShell may not be available.</span></span> <span data-ttu-id="b3518-120">Na przykład nie można używać zmiennych do przechowywania danych ani inspekcji właściwości obiektów zwróconych z poleceń cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b3518-120">For instance, you can't use variables to store data or inspect the properties on objects returned from cmdlets.</span></span> <span data-ttu-id="b3518-121">Poniższy przykład przedstawia dwa podejścia do uzyskania tych samych poleceń w trybie NoLanguage.</span><span class="sxs-lookup"><span data-stu-id="b3518-121">The following example shows two approaches to get the same commands to work in NoLanguage mode.</span></span>

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

<span data-ttu-id="b3518-122">W przypadku bardziej złożonych wywołań poleceń, które sprawiają, że ta metoda jest trudna, należy rozważyć użycie niejawnej [komunikacji zdalnej](#using-jea-with-implicit-remoting) lub [utworzenie funkcji niestandardowych](role-capabilities.md#creating-custom-functions) , które zawijają wymaganą funkcjonalność.</span><span class="sxs-lookup"><span data-stu-id="b3518-122">For more complex command invocations that make this approach difficult, consider using [implicit remoting](#using-jea-with-implicit-remoting) or [creating custom functions](role-capabilities.md#creating-custom-functions) that wrap the functionality you require.</span></span>

## <a name="using-jea-with-implicit-remoting"></a><span data-ttu-id="b3518-123">Korzystanie z JEA z niejawnymi usługami zdalnymi</span><span class="sxs-lookup"><span data-stu-id="b3518-123">Using JEA with implicit remoting</span></span>

<span data-ttu-id="b3518-124">Program PowerShell ma niejawny model komunikacji zdalnej, który umożliwia importowanie poleceń cmdlet serwera proxy z maszyny zdalnej i korzystanie z nich w taki sposób, jakby były poleceniami lokalnymi.</span><span class="sxs-lookup"><span data-stu-id="b3518-124">PowerShell has an implicit remoting model that lets you import proxy cmdlets from a remote machine and interact with them as if they were local commands.</span></span> <span data-ttu-id="b3518-125">Niejawne komunikacji zdalnej wyjaśniono w tym **Hej, obsługa skryptów Guy!**</span><span class="sxs-lookup"><span data-stu-id="b3518-125">Implicit remoting is explained in this **Hey, Scripting Guy!**</span></span> <span data-ttu-id="b3518-126">[wpis w blogu](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).</span><span class="sxs-lookup"><span data-stu-id="b3518-126">[blog post](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).</span></span>
<span data-ttu-id="b3518-127">Niejawne komunikacji zdalnej są przydatne podczas pracy z usługą JEA, ponieważ umożliwia pracę z poleceniami cmdlet JEA w trybie pełnego języka.</span><span class="sxs-lookup"><span data-stu-id="b3518-127">Implicit remoting is useful when working with JEA because it allows you to work with JEA cmdlets in a full language mode.</span></span> <span data-ttu-id="b3518-128">Możesz użyć uzupełniania kart, zmiennych, manipulowania obiektami, a nawet używać lokalnych skryptów do automatyzowania zadań względem punktu końcowego JEA.</span><span class="sxs-lookup"><span data-stu-id="b3518-128">You can use tab completion, variables, manipulate objects, and even use local scripts to automate tasks against a JEA endpoint.</span></span> <span data-ttu-id="b3518-129">Za każdym razem, gdy wywołasz polecenie proxy, dane są wysyłane do punktu końcowego JEA na maszynie zdalnej i wykonywane w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="b3518-129">Anytime you invoke a proxy command, the data is sent to the JEA endpoint on the remote machine and executed there.</span></span>

<span data-ttu-id="b3518-130">Niejawne wykonanie komunikacji zdalnej przez zaimportowanie poleceń cmdlet z istniejącej sesji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b3518-130">Implicit remoting works by importing cmdlets from an existing PowerShell session.</span></span> <span data-ttu-id="b3518-131">Opcjonalnie możesz wybrać opcję przedrostka rzeczowników każdego polecenia cmdlet serwera proxy z wybranym ciągiem.</span><span class="sxs-lookup"><span data-stu-id="b3518-131">You can optionally choose to prefix the nouns of each proxy cmdlet with a string of your choosing.</span></span> <span data-ttu-id="b3518-132">Prefiks umożliwia odróżnienie poleceń dla systemu zdalnego.</span><span class="sxs-lookup"><span data-stu-id="b3518-132">The prefix allows you to distinguish the commands that are for the remote system.</span></span> <span data-ttu-id="b3518-133">Tymczasowy moduł skryptu zawierający wszystkie polecenia proxy jest tworzony i zaimportowany na czas trwania lokalnej sesji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b3518-133">A temporary script module containing all the proxy commands is created and imported for the duration of your local PowerShell session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> <span data-ttu-id="b3518-134">Niektóre systemy mogą nie być w stanie zaimportować całej sesji JEA ze względu na ograniczenia w domyślnych poleceniach cmdlet JEA.</span><span class="sxs-lookup"><span data-stu-id="b3518-134">Some systems may not be able to import an entire JEA session due to constraints in the default JEA cmdlets.</span></span> <span data-ttu-id="b3518-135">Aby to zrobić, należy zaimportować tylko potrzebne polecenia z sesji jea, jawnie dostarczając ich nazwy do `-CommandName` parametru.</span><span class="sxs-lookup"><span data-stu-id="b3518-135">To get around this, only import the commands you need from the JEA session by explicitly providing their names to the `-CommandName` parameter.</span></span> <span data-ttu-id="b3518-136">Przyszła aktualizacja umożliwi rozwiązanie problemu z importowaniem całych sesji JEA w systemach, których to dotyczy.</span><span class="sxs-lookup"><span data-stu-id="b3518-136">A future update will address the issue with importing entire JEA sessions on affected systems.</span></span>

<span data-ttu-id="b3518-137">Jeśli nie możesz zaimportować sesji JEA ze względu na ograniczenia JEA dla parametrów domyślnych, wykonaj poniższe kroki, aby odfiltrować domyślne polecenia z zaimportowanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="b3518-137">If you're unable to import a JEA session because of JEA constraints on the default parameters, follow the steps below to filter out the default commands from the imported set.</span></span> <span data-ttu-id="b3518-138">Możesz nadal używać poleceń takich jak `Select-Object`, ale po prostu użyjesz lokalnej wersji zainstalowanej na komputerze zamiast zaimportowanej ze zdalnej sesji jea.</span><span class="sxs-lookup"><span data-stu-id="b3518-138">You can continue use commands like `Select-Object`, but you'll just use the local version installed on your computer instead of the one imported from the remote JEA session.</span></span>

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

<span data-ttu-id="b3518-139">Polecenia cmdlet serwera proxy można również utrwalać z niejawnych usług zdalnych przy użyciu polecenia [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).</span><span class="sxs-lookup"><span data-stu-id="b3518-139">You can also persist the proxied cmdlets from implicit remoting using [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).</span></span>
<span data-ttu-id="b3518-140">Aby uzyskać więcej informacji na temat niejawnych usług zdalnych, zobacz dokumentację dotyczącą [importu-PSSession](/powershell/microsoft.powershell.utility/import-pssession) i [importu-modułu](/powershell/microsoft.powershell.core/import-module).</span><span class="sxs-lookup"><span data-stu-id="b3518-140">For more information about implicit remoting, see the documentation for [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) and [Import-Module](/powershell/microsoft.powershell.core/import-module).</span></span>

## <a name="using-jea-programmatically"></a><span data-ttu-id="b3518-141">Korzystanie z JEA programowo</span><span class="sxs-lookup"><span data-stu-id="b3518-141">Using JEA programmatically</span></span>

<span data-ttu-id="b3518-142">JEA można także używać w systemach automatyzacji i w aplikacjach użytkowników, takich jak aplikacje i witryny pomocy technicznej w firmie.</span><span class="sxs-lookup"><span data-stu-id="b3518-142">JEA can also be used in automation systems and in user applications, such as in-house helpdesk apps and websites.</span></span> <span data-ttu-id="b3518-143">Podejście jest takie samo, jak w przypadku kompilowania aplikacji, które komunikują się z nieskonfigurowanymi punktami końcowymi programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b3518-143">The approach is the same as that for building apps that talk to unconstrained PowerShell endpoints.</span></span> <span data-ttu-id="b3518-144">Upewnij się, że program jest przeznaczony do pracy z ograniczeniami narzuconymi przez JEA.</span><span class="sxs-lookup"><span data-stu-id="b3518-144">Ensure the program is designed to work with limitation imposed by JEA.</span></span>

<span data-ttu-id="b3518-145">W przypadku prostych, jednorazowych zadań można użyć [polecenia Invoke](/powershell/module/microsoft.powershell.core/invoke-command) , aby uruchomić polecenia w sesji jea.</span><span class="sxs-lookup"><span data-stu-id="b3518-145">For simple, one-off tasks, you can use [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) to run commands in a JEA session.</span></span>

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

<span data-ttu-id="b3518-146">Aby sprawdzić, które polecenia są dostępne do użycia podczas łączenia się z sesją jea, `Get-Command` Uruchom i wykonaj iterację w wynikach, aby sprawdzić, czy są dozwolone parametry.</span><span class="sxs-lookup"><span data-stu-id="b3518-146">To check which commands are available for use when you connect to a JEA session, run `Get-Command` and iterate through the results to check for the allowed parameters.</span></span>

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

<span data-ttu-id="b3518-147">Jeśli tworzysz C# aplikację, możesz utworzyć obszar działania programu PowerShell, który nawiązuje połączenie z sesją jea, określając nazwę konfiguracji w obiekcie [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) .</span><span class="sxs-lookup"><span data-stu-id="b3518-147">If you're building a C# app, you can create a PowerShell runspace that connects to a JEA session by specifying the configuration name in a [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) object.</span></span>

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

## <a name="using-jea-with-powershell-direct"></a><span data-ttu-id="b3518-148">Używanie JEA z programem PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="b3518-148">Using JEA with PowerShell Direct</span></span>

<span data-ttu-id="b3518-149">Funkcja Hyper-V w systemie Windows 10 i Windows Server 2016 oferuje [bezpośrednie środowisko PowerShell](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), funkcję, która umożliwia administratorom funkcji Hyper-V zarządzanie maszynami wirtualnymi za pomocą programu PowerShell niezależnie od konfiguracji sieci lub ustawień zarządzania zdalnego w wirtualnej maszynie.</span><span class="sxs-lookup"><span data-stu-id="b3518-149">Hyper-V in Windows 10 and Windows Server 2016 offers [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), a feature that allows Hyper-V administrators to manage virtual machines with PowerShell regardless of the network configuration or remote management settings on the virtual machine.</span></span>

<span data-ttu-id="b3518-150">Za pomocą programu PowerShell Direct with JEA można udzielić administratorowi funkcji Hyper-V ograniczonego dostępu do maszyny wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="b3518-150">You can use PowerShell Direct with JEA to give a Hyper-V administrator limited access to your VM.</span></span>
<span data-ttu-id="b3518-151">Może to być przydatne, Jeśli utracisz łączność sieciową z maszyną wirtualną i potrzebujesz administratora centrum danych w celu naprawy ustawień sieci.</span><span class="sxs-lookup"><span data-stu-id="b3518-151">This can be useful if you lose network connectivity to your VM and need a datacenter admin to fix the network settings.</span></span>

<span data-ttu-id="b3518-152">Do korzystania z JEA za pośrednictwem programu PowerShell Direct nie jest wymagana dodatkowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="b3518-152">No additional configuration is required to use JEA over PowerShell Direct.</span></span> <span data-ttu-id="b3518-153">Jednak system operacyjny gościa działający na maszynie wirtualnej musi być w systemie Windows 10, Windows Server 2016 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="b3518-153">However, the guest operating system running inside the virtual machine must be Windows 10, Windows Server 2016, or higher.</span></span> <span data-ttu-id="b3518-154">Administrator funkcji Hyper-V może nawiązać połączenie z punktem końcowym usługi `-VMName` jea `-VMId` za pomocą parametrów lub w poleceniach cmdlet PSRemoting:</span><span class="sxs-lookup"><span data-stu-id="b3518-154">The Hyper-V admin can connect to the JEA endpoint by using the `-VMName` or `-VMId` parameters on PSRemoting cmdlets:</span></span>

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

<span data-ttu-id="b3518-155">Zaleca się utworzenie dedykowanego konta użytkownika z minimalnymi prawami wymaganymi do zarządzania systemem w celu użycia przez administratora funkcji Hyper-V.</span><span class="sxs-lookup"><span data-stu-id="b3518-155">It's recommended you create a dedicated user account with the minimum rights needed to manage the system for use by a Hyper-V administrator.</span></span> <span data-ttu-id="b3518-156">Należy pamiętać, że nawet nieuprzywilejowany użytkownik może zalogować się do komputera z systemem Windows domyślnie, w tym przy użyciu nieograniczonego programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b3518-156">Remember, even an unprivileged user can sign into a Windows machine by default, including using unconstrained PowerShell.</span></span> <span data-ttu-id="b3518-157">Dzięki temu można przeglądać system plików i dowiedzieć się więcej o środowisku systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="b3518-157">That allows them to browse the file system and learn more about your OS environment.</span></span> <span data-ttu-id="b3518-158">Aby zablokować administratora funkcji Hyper-V i ograniczyć dostęp do maszyny wirtualnej przy użyciu programu PowerShell Direct z JEA, należy odmówić uprawnień lokalnego logowania do konta JEA administratora funkcji Hyper-V.</span><span class="sxs-lookup"><span data-stu-id="b3518-158">To lock down a Hyper-V administrator and limit them to only access a VM using PowerShell Direct with JEA, you must deny local logon rights to the Hyper-V admin's JEA account.</span></span>
