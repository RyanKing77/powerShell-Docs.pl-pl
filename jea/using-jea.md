---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: "jea, programu powershell, zabezpieczeń"
title: "Przy użyciu JEA"
ms.openlocfilehash: 9996a432bca27240e0f08adf932126ced116985d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="using-jea"></a><span data-ttu-id="08d3a-103">Przy użyciu JEA</span><span class="sxs-lookup"><span data-stu-id="08d3a-103">Using JEA</span></span>

> <span data-ttu-id="08d3a-104">Dotyczy: środowiska Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="08d3a-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="08d3a-105">W tym temacie opisano różne sposoby, można połączyć się i używać punktu końcowego JEA.</span><span class="sxs-lookup"><span data-stu-id="08d3a-105">This topic describes the various ways you can connect to and use a JEA endpoint.</span></span>

## <a name="using-jea-interactively"></a><span data-ttu-id="08d3a-106">Używanie JEA interakcyjne</span><span class="sxs-lookup"><span data-stu-id="08d3a-106">Using JEA interactively</span></span>

<span data-ttu-id="08d3a-107">Jeśli testujesz konfigurację JEA lub masz prostych zadań użytkownikom wykonywanie, można użyć JEA tak samo jak regularne sesji komunikacji zdalnej programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="08d3a-107">If you are testing your JEA configuration or have simple tasks for users to perform, you can use JEA the same way you would a regular PowerShell remoting session.</span></span>
<span data-ttu-id="08d3a-108">Remoting złożonych zadań, zaleca się używania [niejawne remoting](#using-jea-with-implicit-remoting) zamiast tego w celu ułatwienia dla użytkowników przez, dzięki czemu użytkownicy mogą pracować z obiektów danych lokalnie.</span><span class="sxs-lookup"><span data-stu-id="08d3a-108">For complex remoting tasks, it is recommended to use [implicit remoting](#using-jea-with-implicit-remoting) instead to make it easier for your users by allowing users to operate with the data objects locally.</span></span>

<span data-ttu-id="08d3a-109">Aby używać JEA interakcyjnie, będą potrzebne:</span><span class="sxs-lookup"><span data-stu-id="08d3a-109">To use JEA interactively, you will need:</span></span>
- <span data-ttu-id="08d3a-110">Nazwa komputera jest nawiązywane (może być komputer lokalny)</span><span class="sxs-lookup"><span data-stu-id="08d3a-110">The name of the computer you are connecting to (can be the local machine)</span></span>
- <span data-ttu-id="08d3a-111">Nazwa punktu końcowego JEA zarejestrowane na tym komputerze</span><span class="sxs-lookup"><span data-stu-id="08d3a-111">The name of the JEA endpoint registered on that computer</span></span>
- <span data-ttu-id="08d3a-112">Poświadczenia dla komputera, które mają dostęp do punktu końcowego JEA</span><span class="sxs-lookup"><span data-stu-id="08d3a-112">Credentials for the computer that have access to the JEA endpoint</span></span>

<span data-ttu-id="08d3a-113">Dane zapasów, można rozpocząć sesji JEA przy użyciu [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) lub [Enter-PSSession](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).</span><span class="sxs-lookup"><span data-stu-id="08d3a-113">With that information in hand, you can start a JEA session using [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) or [Enter-PSSession](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).</span></span>

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

<span data-ttu-id="08d3a-114">Jeśli konto, obecnie zalogowano jako ma dostęp do punktu końcowego JEA, można pominąć `-Credential` parametru.</span><span class="sxs-lookup"><span data-stu-id="08d3a-114">If the account you're currently logged in as has access to the JEA endpoint, you can omit the `-Credential` parameter.</span></span>

<span data-ttu-id="08d3a-115">Gdy programu PowerShell Monituj zmiany `[localhost]: PS>` będzie wiadomo, że możesz teraz współpracuje z sesji zdalnej JEA.</span><span class="sxs-lookup"><span data-stu-id="08d3a-115">When the PowerShell prompt changes to `[localhost]: PS>` you will know that you are now interacting with the remote JEA session.</span></span>
<span data-ttu-id="08d3a-116">Można uruchomić `Get-Command` do sprawdzenia, które polecenia są dostępne.</span><span class="sxs-lookup"><span data-stu-id="08d3a-116">You can run `Get-Command` to check which commands are available.</span></span>
<span data-ttu-id="08d3a-117">Należy skontaktować się z administratorem, aby dowiedzieć się, czy ma żadnych ograniczeń dotyczących dostępnych parametrów lub wartości parametrów dozwolony.</span><span class="sxs-lookup"><span data-stu-id="08d3a-117">You will need to consult with your administrator to learn if there are any restrictions on the available parameters or allowable parameter values.</span></span>

<span data-ttu-id="08d3a-118">Dla przypomnienia JEA sesji działają w trybie NoLanguage, więc niektóre metody należy zwykle użyć programu PowerShell nie mogą być dostępne.</span><span class="sxs-lookup"><span data-stu-id="08d3a-118">As a reminder, JEA sessions operate in NoLanguage mode, so some of the ways you typically use PowerShell may not be available.</span></span>
<span data-ttu-id="08d3a-119">Na przykład nie można używać zmiennych do przechowywania danych lub sprawdź właściwości na obiekty zwrócone przez polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="08d3a-119">For instance, you cannot use variables to store data or inspect the properties on objects returned from cmdlets.</span></span>
<span data-ttu-id="08d3a-120">Poniżej przedstawiono przykład przykład używasz programu PowerShell dzisiaj i dwa podejścia, aby uzyskać takie same polecenie pracy w trybie NoLanguage.</span><span class="sxs-lookup"><span data-stu-id="08d3a-120">The below example shows an example of how you may be using PowerShell today, and two approaches to get the same command working in NoLanguage mode.</span></span>

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

<span data-ttu-id="08d3a-121">W przypadku bardziej złożonych wywołania polecenia, które utrudnić takie podejście, rozważ zastosowanie [niejawne remoting](#using-jea-with-implicit-remoting) lub [Tworzenie funkcji niestandardowej](role-capabilities.md#creating-custom-functions) zawijać się funkcje wymagane.</span><span class="sxs-lookup"><span data-stu-id="08d3a-121">For more complex command invocations that make this approach difficult, consider using [implicit remoting](#using-jea-with-implicit-remoting) or [creating custom functions](role-capabilities.md#creating-custom-functions) that wrap the functionality you desire.</span></span>

## <a name="using-jea-with-implicit-remoting"></a><span data-ttu-id="08d3a-122">Przy użyciu JEA z niejawnych komunikacji zdalnej</span><span class="sxs-lookup"><span data-stu-id="08d3a-122">Using JEA with implicit remoting</span></span>

<span data-ttu-id="08d3a-123">PowerShell obsługuje model alternatywnych usług zdalnych gdzie możesz zaimportować polecenia cmdlet serwera proxy z komputera zdalnego na komputerze lokalnym i interakcji z nimi, tak jakby były lokalne polecenia.</span><span class="sxs-lookup"><span data-stu-id="08d3a-123">PowerShell supports an alternative remoting model where you can import proxy cmdlets from a remote machine on your local computer and interact with them as if they were local commands.</span></span>
<span data-ttu-id="08d3a-124">To jest nazywana niejawne zdalnych i znajduje się również w [to *Witaj, Twórco skryptów!* wpis w blogu](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).</span><span class="sxs-lookup"><span data-stu-id="08d3a-124">This is called implicit remoting, and is explained well in [this *Hey, Scripting Guy!* blog post](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).</span></span>
<span data-ttu-id="08d3a-125">Niejawne zdalnych jest szczególnie przydatne podczas pracy z JEA, ponieważ umożliwia pracę z poleceniami cmdlet JEA w trybie pełną obsługą języka.</span><span class="sxs-lookup"><span data-stu-id="08d3a-125">Implicit remoting is particularly useful when working with JEA because it allows you to work with JEA cmdlets in a full language mode.</span></span>
<span data-ttu-id="08d3a-126">Oznacza to, można używać uzupełniania po naciśnięciu tabulatora, zmienne, manipulowanie obiektami i nawet za pomocą skryptów lokalnych można łatwo automatyzować względem punktu końcowego JEA.</span><span class="sxs-lookup"><span data-stu-id="08d3a-126">This means you can use tab completion, variables, manipulate objects, and even use local scripts to more easily automate against a JEA endpoint.</span></span>
<span data-ttu-id="08d3a-127">W dowolnym momencie Wywołaj polecenie serwera proxy, dane zostaną wysłane do punktu końcowego JEA na komputerze zdalnym i tam wykonywane.</span><span class="sxs-lookup"><span data-stu-id="08d3a-127">Anytime you invoke a proxy command, the data will be sent to the JEA endpoint on the remote machine and executed there.</span></span>

<span data-ttu-id="08d3a-128">Niejawne remoting działa przez zaimportowanie poleceń cmdlet z istniejącej sesji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="08d3a-128">Implicit remoting works by importing cmdlets from an existing PowerShell session.</span></span>
<span data-ttu-id="08d3a-129">Można opcjonalnie prefiksu rzeczowniki każde polecenie cmdlet serwera proxy z ciągiem wybrania rozróżniania, które polecenia są systemu zdalnego.</span><span class="sxs-lookup"><span data-stu-id="08d3a-129">You can optionally choose to prefix the nouns of each proxy cmdlet with a string of your choosing to distinguish which commands are for the remote system.</span></span>
<span data-ttu-id="08d3a-130">Moduł tymczasowy skrypt zawierający wszystkie polecenia proxy zostanie utworzona i można używać w czasie trwania lokalnej sesji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="08d3a-130">A temporary script module containing all of the proxy commands will be created and can be used for the duration of your local PowerShell session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> <span data-ttu-id="08d3a-131">Niektóre systemy nie można zaimportować całej sesji JEA ze względu na ograniczenia w poleceniach cmdlet JEA domyślne.</span><span class="sxs-lookup"><span data-stu-id="08d3a-131">Some systems may not be able to import an entire JEA session due to constraints in the default JEA cmdlets.</span></span>
> <span data-ttu-id="08d3a-132">Aby tego, importować tylko polecenia należy z sesji JEA jawnie zapewniając ich nazwy do `-CommandName` parametru.</span><span class="sxs-lookup"><span data-stu-id="08d3a-132">To get around this, only import the commands you need from the JEA session by explicitly providing their names to the `-CommandName` parameter.</span></span>
> <span data-ttu-id="08d3a-133">Przyszłej aktualizacji będzie dotyczyć problem z importowaniem całej sesji JEA w systemach.</span><span class="sxs-lookup"><span data-stu-id="08d3a-133">A future update will address the issue with importing entire JEA sessions on affected systems.</span></span>

<span data-ttu-id="08d3a-134">Jeśli nie można zaimportować sesji JEA ze względu na ograniczenia dotyczące parametrów JEA domyślne, można wykonaj poniższe kroki, aby odfiltrować polecenia domyślne z zaimportowany zestaw.</span><span class="sxs-lookup"><span data-stu-id="08d3a-134">If you are unable to import a JEA session due to constraints on the default JEA parameters, you can follow the steps below to filter out the default commands from the imported set.</span></span>
<span data-ttu-id="08d3a-135">Nadal będzie można używać poleceń, takich jak `Select-Object` — wystarczy użyjesz lokalnej wersji zainstalowanej na komputerze w sesji JEA zamiast zdalnego.</span><span class="sxs-lookup"><span data-stu-id="08d3a-135">You will still be able to use commands like `Select-Object` -- you'll just use the local version installed on your computer instead of the remote one in the JEA session.</span></span>

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

<span data-ttu-id="08d3a-136">Można również utrwalić proxy poleceń cmdlet z niejawnych zdalnych przy użyciu [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).</span><span class="sxs-lookup"><span data-stu-id="08d3a-136">You can also persist the proxied cmdlets from implicit remoting using [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).</span></span>
<span data-ttu-id="08d3a-137">Aby uzyskać więcej informacji o niejawne remoting, zapoznaj się w dokumentacji pomocy [Import-PSSession](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) i [Import-Module](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/import-module).</span><span class="sxs-lookup"><span data-stu-id="08d3a-137">For more information about implicit remoting, check out the help documentation for [Import-PSSession](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) and [Import-Module](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/import-module).</span></span>

## <a name="using-jea-programatically"></a><span data-ttu-id="08d3a-138">Programowo przy użyciu JEA</span><span class="sxs-lookup"><span data-stu-id="08d3a-138">Using JEA programatically</span></span>

<span data-ttu-id="08d3a-139">JEA można również w systemach automatyzacji i użytkownika aplikacji, takich jak pomoc techniczna wewnętrznych aplikacji i witryn sieci web.</span><span class="sxs-lookup"><span data-stu-id="08d3a-139">JEA can also be used in automation systems and in user applications, such as in-house helpdesk apps and web sites.</span></span>
<span data-ttu-id="08d3a-140">Podejście jest taki sam, jak w przypadku tworzenia aplikacji, która zwróć się do nieograniczonego PowerShell punktów końcowych, ale należy pamiętać, że program należy zwrócić uwagę, że JEA jest ograniczanie poleceń, które mogą być uruchamiane w sesji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="08d3a-140">The approach is the same as that for building apps that talk to unconstrained PowerShell endpoints, with the caveat that the program should be aware that JEA is limiting the commands that can be run in the remote session.</span></span>

<span data-ttu-id="08d3a-141">W przypadku prostych, jednorazowych zadań, można użyć [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command) do uruchomienia zestawu poleceń za pomocą JEA.</span><span class="sxs-lookup"><span data-stu-id="08d3a-141">For simple, one-off tasks, you can use [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command) to run a set of commands using JEA.</span></span>

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

<span data-ttu-id="08d3a-142">Aby sprawdzić, które polecenia są dostępne do użycia podczas łączenia z sesją JEA, uruchom `Get-Command` i iterację wyników, aby sprawdzić, czy są dozwolone parametry.</span><span class="sxs-lookup"><span data-stu-id="08d3a-142">To check which commands are available for use when you connect to a JEA session, run `Get-Command` and iterate through the results to check for the allowed parameters.</span></span>

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

<span data-ttu-id="08d3a-143">Jeśli tworzysz aplikację C#, można utworzyć obszaru działania programu PowerShell, który nawiązuje połączenie z sesją JEA, określając nazwę konfiguracji w [WSManConnectionInfo](https://msdn.microsoft.com/en-us/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) obiektu.</span><span class="sxs-lookup"><span data-stu-id="08d3a-143">If you are building a C# app, you can create a PowerShell runspace that connects to a JEA session by specifying the configuration name in a [WSManConnectionInfo](https://msdn.microsoft.com/en-us/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) object.</span></span>

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

## <a name="using-jea-with-powershell-direct"></a><span data-ttu-id="08d3a-144">Przy użyciu JEA bezpośrednio programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="08d3a-144">Using JEA with PowerShell Direct</span></span>

<span data-ttu-id="08d3a-145">Zapewnia funkcji Hyper-V w systemie Windows 10 i Windows Server 2016 [PowerShell bezpośrednio](https://msdn.microsoft.com/en-us/virtualization/hyperv_on_windows/user_guide/vmsession), funkcji, która pozwala administratorom funkcji Hyper-V do zarządzania maszynami wirtualnymi przy użyciu programu PowerShell, niezależnie od konfiguracji sieci lub do zdalnego zarządzania ustawienia na maszynie wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="08d3a-145">Hyper-V in Windows 10 and Windows Server 2016 offers [PowerShell Direct](https://msdn.microsoft.com/en-us/virtualization/hyperv_on_windows/user_guide/vmsession), a feature which allows Hyper-V administrators to manage virtual machines with PowerShell regardless of the network configuration or remote management settings on the virtual machine.</span></span>

<span data-ttu-id="08d3a-146">Za pomocą programu PowerShell bezpośrednio i JEA udzielenia dostępu administratora ograniczone funkcji Hyper-V do maszyny Wirtualnej, które mogą być przydatne jeśli utratę łączności sieciowej do maszyny Wirtualnej i należy poprawić ustawienia sieciowe admin centrum danych.</span><span class="sxs-lookup"><span data-stu-id="08d3a-146">You can use PowerShell Direct with JEA to give a Hyper-V administrator limited access to your VM, which can be useful if you lose network connectivity to your VM and need a datacenter admin to fix the network settings.</span></span>

<span data-ttu-id="08d3a-147">Nie jest dodatkowa konfiguracja wymagane do używania JEA za pośrednictwem programu PowerShell bezpośrednio, ale systemu operacyjnego działającego na maszynie wirtualnej musi należeć do systemu Windows 10 lub Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="08d3a-147">No additional configuration is required to use JEA over PowerShell Direct, however the operating system running inside the virtual machine must be Windows 10 or Windows Server 2016.</span></span>
<span data-ttu-id="08d3a-148">Administrator funkcji Hyper-V można połączyć z punktem końcowym JEA przy użyciu `-VMName` lub `-VMId` parametrów polecenia cmdlet PSRemoting:</span><span class="sxs-lookup"><span data-stu-id="08d3a-148">The Hyper-V admin can connect to the JEA endpoint by using the `-VMName` or `-VMId` parameters on PSRemoting cmdlets:</span></span>

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

<span data-ttu-id="08d3a-149">Zdecydowanie zaleca się utworzenie dedykowanego użytkownika lokalnego z nie innych uprawnień do zarządzania systemem dla administratorów sieci funkcji Hyper-V do użycia.</span><span class="sxs-lookup"><span data-stu-id="08d3a-149">It is strongly recommended that you create a dedicated local user with no other rights to manage the system for your Hyper-V administrators to use.</span></span>
<span data-ttu-id="08d3a-150">Należy pamiętać, że nawet nieuprawnionego użytkownika nadal zalogować się do komputera z systemem Windows domyślnie, w tym przy użyciu nieograniczonego programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="08d3a-150">Remember that even an unprivileged user can still log into a Windows machine by default, including using unconstrained PowerShell.</span></span>
<span data-ttu-id="08d3a-151">Które umożliwią jej Przeglądaj (niektóre) system plików i Dowiedz się więcej na temat środowiska systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="08d3a-151">That will allow them to browse (some of) the file system and learn more about your OS environment.</span></span>
<span data-ttu-id="08d3a-152">Zablokowanie administratora funkcji Hyper-V, aby uzyskiwać dostęp tylko do maszyny Wirtualnej przy użyciu programu PowerShell bezpośrednio z JEA, konieczne będzie Odmowa logowania lokalnego uprawnień do konta JEA administratora funkcji Hyper-V.</span><span class="sxs-lookup"><span data-stu-id="08d3a-152">To lock down a Hyper-V administrator to only access a VM using PowerShell Direct with JEA, you will need to deny local logon rights to the Hyper-V admin's JEA account.</span></span>

