---
ms.date: 07/10/2019
keywords: jea, PowerShell, zabezpieczenia
title: Inspekcja i raportowanie w usłudze JEA
ms.openlocfilehash: 2afefe83acecc1fc3643d49766120ffecc25378f
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017923"
---
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="98fc9-103">Inspekcja i raportowanie w usłudze JEA</span><span class="sxs-lookup"><span data-stu-id="98fc9-103">Auditing and Reporting on JEA</span></span>

<span data-ttu-id="98fc9-104">Po wdrożeniu JEA należy regularnie przeprowadzać inspekcję konfiguracji JEA.</span><span class="sxs-lookup"><span data-stu-id="98fc9-104">After you've deployed JEA, you need to regularly audit the JEA configuration.</span></span> <span data-ttu-id="98fc9-105">Inspekcja pomaga ocenić, że poprawne osoby mają dostęp do punktu końcowego JEA, a przypisane do nich role nadal są odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="98fc9-105">Auditing helps you assess that the correct people have access to the JEA endpoint and their assigned roles are still appropriate.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="98fc9-106">Znajdowanie zarejestrowanych sesji JEA na maszynie</span><span class="sxs-lookup"><span data-stu-id="98fc9-106">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="98fc9-107">Aby sprawdzić, które sesje JEA są zarejestrowane na komputerze, użyj polecenia cmdlet [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="98fc9-107">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }
```

```Output
Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed,
                CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

<span data-ttu-id="98fc9-108">Obowiązujące prawa dla punktu końcowego są wymienione we właściwości **uprawnienia** .</span><span class="sxs-lookup"><span data-stu-id="98fc9-108">The effective rights for the endpoint are listed in the **Permission** property.</span></span> <span data-ttu-id="98fc9-109">Ci użytkownicy mają prawo do nawiązywania połączenia z punktem końcowym JEA.</span><span class="sxs-lookup"><span data-stu-id="98fc9-109">These users have the right to connect to the JEA endpoint.</span></span> <span data-ttu-id="98fc9-110">Jednak role i polecenia, do których mają dostęp, są określane przez właściwość **RoleDefinitions** w [pliku konfiguracji sesji](session-configurations.md) , który został użyty do zarejestrowania punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="98fc9-110">However, the roles and commands they have access to is determined by the **RoleDefinitions** property in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span> <span data-ttu-id="98fc9-111">Rozwiń Właściwość **RoleDefinitions** , aby oszacować mapowania ról w zarejestrowanym punkcie końcowym jea.</span><span class="sxs-lookup"><span data-stu-id="98fc9-111">Expand the **RoleDefinitions** property to evaluate the role mappings in a registered JEA endpoint.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="98fc9-112">Znajdź dostępne możliwości roli na komputerze</span><span class="sxs-lookup"><span data-stu-id="98fc9-112">Find available role capabilities on the machine</span></span>

<span data-ttu-id="98fc9-113">JEA pobiera możliwości roli z `.psrc` plików przechowywanych w folderze **RoleCapabilities** w module programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="98fc9-113">JEA gets role capabilities from the `.psrc` files stored in the **RoleCapabilities** folder inside a PowerShell module.</span></span> <span data-ttu-id="98fc9-114">Poniższa funkcja znajduje wszystkie możliwości roli dostępne na komputerze.</span><span class="sxs-lookup"><span data-stu-id="98fc9-114">The following function finds all role capabilities available on a computer.</span></span>

```powershell
function Find-LocalRoleCapability {
    $results = @()

    # Find modules with a "RoleCapabilities" subfolder and add any PSRC files to the result set
    Get-Module -ListAvailable | ForEach-Object {
        $psrcpath = Join-Path -Path $_.ModuleBase -ChildPath 'RoleCapabilities'
        if (Test-Path $psrcpath) {
            $results += Get-ChildItem -Path $psrcpath -Filter *.psrc
        }
    }

    # Format the results nicely to make it easier to read
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{
        Name = 'Path'; Expression = { $_.FullName }
    } | Sort-Object Name
}
```

> [!NOTE]
> <span data-ttu-id="98fc9-115">Kolejność wyników z tej funkcji nie musi być kolejnością, w której można wybrać możliwości roli, jeśli wiele możliwości roli ma taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="98fc9-115">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="98fc9-116">Sprawdź czynne prawa dla określonego użytkownika</span><span class="sxs-lookup"><span data-stu-id="98fc9-116">Check effective rights for a specific user</span></span>

<span data-ttu-id="98fc9-117">Polecenie cmdlet [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) wylicza wszystkie polecenia dostępne w punkcie KOŃCOWYm jea w oparciu o członkostwo w grupach użytkowników.</span><span class="sxs-lookup"><span data-stu-id="98fc9-117">The [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) cmdlet enumerates all the commands available on a JEA endpoint based on a user's group memberships.</span></span>
<span data-ttu-id="98fc9-118">Dane wyjściowe `Get-PSSessionCapability` są identyczne z określonym użytkownikiem uruchomionym `Get-Command -CommandType All` w sesji jea.</span><span class="sxs-lookup"><span data-stu-id="98fc9-118">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="98fc9-119">Jeśli użytkownicy nie są stałymi członkami grup, które przyznają im dodatkowe prawa JEA, to polecenie cmdlet może nie odzwierciedlać tych dodatkowych uprawnień.</span><span class="sxs-lookup"><span data-stu-id="98fc9-119">If your users aren't permanent members of groups that would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span> <span data-ttu-id="98fc9-120">Dzieje się tak w przypadku korzystania z systemów dostępu uprzywilejowanego "just in Time" w celu umożliwienia użytkownikom tymczasowego należeć do grupy zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="98fc9-120">This happens when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span> <span data-ttu-id="98fc9-121">Należy dokładnie oszacować Mapowanie użytkowników do ról i możliwości, aby zapewnić, że użytkownicy będą mieli tylko poziom dostępu wymagany do pomyślnego wykonania zadań.</span><span class="sxs-lookup"><span data-stu-id="98fc9-121">Carefully evaluate the mapping of users to roles and capabilities to ensure that users only get the level of access needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="98fc9-122">Dzienniki zdarzeń programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="98fc9-122">PowerShell event logs</span></span>

<span data-ttu-id="98fc9-123">Jeśli włączono rejestrowanie bloków modułu lub skryptu w systemie, można zobaczyć zdarzenia w dziennikach zdarzeń systemu Windows dla każdego polecenia uruchamianego przez użytkownika w sesji JEA.</span><span class="sxs-lookup"><span data-stu-id="98fc9-123">If you enabled module or script block logging on the system, you can see events in the Windows event logs for each command a user runs in a JEA session.</span></span> <span data-ttu-id="98fc9-124">Aby znaleźć te zdarzenia, Otwórz dziennik zdarzeń **Microsoft-Windows-PowerShell/operacyjnego** i Wyszukaj zdarzenia o identyfikatorze **4104**.</span><span class="sxs-lookup"><span data-stu-id="98fc9-124">To find these events, open **Microsoft-Windows-PowerShell/Operational** event log and look for events with event ID **4104**.</span></span>

<span data-ttu-id="98fc9-125">Każdy wpis dziennika zdarzeń zawiera informacje o sesji, w której uruchomiono polecenie.</span><span class="sxs-lookup"><span data-stu-id="98fc9-125">Each event log entry includes information about the session in which the command was run.</span></span> <span data-ttu-id="98fc9-126">W przypadku sesji JEA zdarzenie obejmuje informacje o **ConnectedUser** i **RunAsUser**.</span><span class="sxs-lookup"><span data-stu-id="98fc9-126">For JEA sessions, the event includes information about the **ConnectedUser** and the **RunAsUser**.</span></span> <span data-ttu-id="98fc9-127">**ConnectedUser** jest bieżącym użytkownikiem, który UTWORZYŁ sesję jea.</span><span class="sxs-lookup"><span data-stu-id="98fc9-127">The **ConnectedUser** is the actual user who created the JEA session.</span></span> <span data-ttu-id="98fc9-128">**RunAsUser** jest kontem jea używanym do wykonywania polecenia.</span><span class="sxs-lookup"><span data-stu-id="98fc9-128">The **RunAsUser** is the account JEA used to execute the command.</span></span>

<span data-ttu-id="98fc9-129">Dzienniki zdarzeń aplikacji pokazują zmiany wprowadzane przez **RunAsUser**.</span><span class="sxs-lookup"><span data-stu-id="98fc9-129">Application event logs show changes being made by the **RunAsUser**.</span></span> <span data-ttu-id="98fc9-130">W celu śledzenia określonego wywołania polecenia z powrotem do **ConnectedUser**wymagane jest włączenie rejestrowania modułu i skryptu.</span><span class="sxs-lookup"><span data-stu-id="98fc9-130">So having module and script logging enabled is required to trace a specific command invocation back to the **ConnectedUser**.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="98fc9-131">Dzienniki zdarzeń aplikacji</span><span class="sxs-lookup"><span data-stu-id="98fc9-131">Application event logs</span></span>

<span data-ttu-id="98fc9-132">Polecenia uruchamiane w sesji JEA, które współdziałają z zewnętrznymi aplikacjami lub usługami, mogą rejestrować zdarzenia do własnych dzienników zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="98fc9-132">Commands run in a JEA session that interact with external applications or services may log events to their own event logs.</span></span> <span data-ttu-id="98fc9-133">W przeciwieństwie do dzienników i transkrypcji programu PowerShell, inne mechanizmy rejestrowania nie przechwytuje połączonego użytkownika sesji JEA.</span><span class="sxs-lookup"><span data-stu-id="98fc9-133">Unlike PowerShell logs and transcripts, other logging mechanisms don't capture the connected user of the JEA session.</span></span> <span data-ttu-id="98fc9-134">Zamiast tego aplikacje te rejestrują tylko wirtualnego użytkownika "Uruchom jako".</span><span class="sxs-lookup"><span data-stu-id="98fc9-134">Instead, those applications only log the virtual run-as user.</span></span>
<span data-ttu-id="98fc9-135">Aby określić, kto uruchomił polecenie, należy zapoznać się z [transkrypcją sesji](#session-transcripts) lub skorelować dzienników zdarzeń programu PowerShell z czasem i użytkownikiem wyświetlanym w dzienniku zdarzeń aplikacji.</span><span class="sxs-lookup"><span data-stu-id="98fc9-135">To determine who ran the command, you need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="98fc9-136">Dziennik usługi WinRM może również pomóc w skorelowaniu użytkowników z połączeniem Uruchom jako z zalogowanym użytkownikiem w dzienniku zdarzeń aplikacji.</span><span class="sxs-lookup"><span data-stu-id="98fc9-136">The WinRM log can also help you correlate run-as users to the connecting user in an application event log.</span></span> <span data-ttu-id="98fc9-137">Identyfikator zdarzenia **193** w dzienniku **systemu Microsoft Windows-Windows Remote Management/operacyjnego** REJESTRUJE identyfikator zabezpieczeń (SID) i nazwę konta dla użytkownika łączącego i Uruchom jako dla każdej nowej sesji jea.</span><span class="sxs-lookup"><span data-stu-id="98fc9-137">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user for every new JEA session.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="98fc9-138">Transkrypcje sesji</span><span class="sxs-lookup"><span data-stu-id="98fc9-138">Session transcripts</span></span>

<span data-ttu-id="98fc9-139">Jeśli skonfigurowano JEA do tworzenia transkrypcji dla każdej sesji użytkownika, kopia tekstowa akcji każdego użytkownika jest przechowywana w określonym folderze.</span><span class="sxs-lookup"><span data-stu-id="98fc9-139">If you configured JEA to create a transcript for each user session, a text copy of every user's actions are stored in the specified folder.</span></span>

<span data-ttu-id="98fc9-140">Następujące polecenie (jako administrator) znajduje wszystkie katalogi transkrypcji.</span><span class="sxs-lookup"><span data-stu-id="98fc9-140">The following command (as an administrator) finds all transcript directories.</span></span>

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="98fc9-141">Każdy transkrypcja rozpoczyna się od informacji o czasie uruchomienia sesji, który użytkownik połączył się z sesją oraz do której przypisano tożsamość JEA.</span><span class="sxs-lookup"><span data-stu-id="98fc9-141">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="98fc9-142">Treść transkrypcji zawiera informacje o każdym z poleceń wywoływanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="98fc9-142">The body of the transcript contains information about each command the user invoked.</span></span> <span data-ttu-id="98fc9-143">Dokładna składnia użytego polecenia jest niedostępna w sesjach JEA ze względu na sposób przekształcania poleceń na potrzeby komunikacji zdalnej programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="98fc9-143">The exact syntax of the command used is unavailable in JEA sessions because of the way commands are transformed for PowerShell remoting.</span></span> <span data-ttu-id="98fc9-144">Można jednak nadal określić efektywne polecenie, które zostało wykonane.</span><span class="sxs-lookup"><span data-stu-id="98fc9-144">However, you can still determine the effective command that was executed.</span></span> <span data-ttu-id="98fc9-145">Poniżej znajduje się przykładowy fragment kodu dotyczący użytkownika działającego `Get-Service Dns` w sesji jea:</span><span class="sxs-lookup"><span data-stu-id="98fc9-145">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="98fc9-146">Wiersz **CommandInvocation** jest zapisywana dla każdego polecenia uruchomionego przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="98fc9-146">A **CommandInvocation** line is written for each command a user runs.</span></span> <span data-ttu-id="98fc9-147">**ParameterBindings** rejestruje każdy parametr i wartość dostarczoną z poleceniem.</span><span class="sxs-lookup"><span data-stu-id="98fc9-147">**ParameterBindings** record each parameter and value supplied with the command.</span></span> <span data-ttu-id="98fc9-148">W poprzednim przykładzie można zobaczyć, że **Nazwa** parametru została podana wartość **DNS** dla `Get-Service` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="98fc9-148">In the previous example, you can see that the parameter **Name** was supplied the with value **Dns** for the `Get-Service` cmdlet.</span></span>

<span data-ttu-id="98fc9-149">Dane wyjściowe każdego polecenia wyzwalają także **CommandInvocation**, zwykle do `Out-Default`.</span><span class="sxs-lookup"><span data-stu-id="98fc9-149">The output of each command also triggers a **CommandInvocation**, usually to `Out-Default`.</span></span> <span data-ttu-id="98fc9-150">**Inputobject** of `Out-Default` to obiekt programu PowerShell zwrócony z polecenia.</span><span class="sxs-lookup"><span data-stu-id="98fc9-150">The **InputObject** of `Out-Default` is the PowerShell object returned from the command.</span></span> <span data-ttu-id="98fc9-151">Poniżej znajdują się szczegółowe informacje o tym obiekcie, które są widoczne poniżej. dokładnie naśladując się, co widzi użytkownik.</span><span class="sxs-lookup"><span data-stu-id="98fc9-151">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="98fc9-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="98fc9-152">See also</span></span>

[<span data-ttu-id="98fc9-153">*Program PowerShell ♥ niebieskiego* wpisu w blogu zespołu na stronie zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="98fc9-153">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
