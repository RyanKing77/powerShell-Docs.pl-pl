---
ms.date: 06/12/2017
author: rpsqrd
ms.topic: conceptual
keywords: jea, programu powershell, zabezpieczeń
title: Inspekcja i raportowania JEA
ms.openlocfilehash: 7fc670c77b5fbf9bce8fb55dd99a2f9a984100d2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="113d3-103">Inspekcja i raportowania JEA</span><span class="sxs-lookup"><span data-stu-id="113d3-103">Auditing and Reporting on JEA</span></span>

> <span data-ttu-id="113d3-104">Dotyczy: środowiska Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="113d3-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="113d3-105">Po wdrożeniu JEA, należy regularnie inspekcji JEA konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="113d3-105">After you've deployed JEA, you will want to regularly audit the JEA configuration.</span></span>
<span data-ttu-id="113d3-106">Dzięki temu łatwiej ocenić, jeśli osobom mają dostęp do punktu końcowego JEA i przypisane im role będą nadal odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="113d3-106">This will help you assess if the correct people have access to the JEA endpoint and if their assigned roles are still appropriate.</span></span>

<span data-ttu-id="113d3-107">W tym temacie opisano różne sposoby, można przeprowadzić inspekcję punktu końcowego JEA.</span><span class="sxs-lookup"><span data-stu-id="113d3-107">This topic describes the various ways you can audit a JEA endpoint.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="113d3-108">Znajdź zarejestrowanych JEA sesji na komputerze</span><span class="sxs-lookup"><span data-stu-id="113d3-108">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="113d3-109">Aby sprawdzić, które sesje JEA są rejestrowane na komputerze, użyj [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="113d3-109">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

<span data-ttu-id="113d3-110">Skuteczne prawa dla punktu końcowego są wyświetlane we właściwości "Uprawnienia".</span><span class="sxs-lookup"><span data-stu-id="113d3-110">The effective rights for the endpoint are listed in the "Permission" property.</span></span>
<span data-ttu-id="113d3-111">Ci użytkownicy mają prawo do nawiązywania połączenia z punktem końcowym JEA, ale które role (i przez rozszerzenie, poleceń) mają dostęp, jest określany przez pole "RoleDefinitions" w [pliku konfiguracji sesji](session-configurations.md) użytą do zarejestrowania punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="113d3-111">These users have the right to connect to the JEA endpoint, but which roles (and, by extension, commands) they have access to is determined by the "RoleDefinitions" field in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span>

<span data-ttu-id="113d3-112">Mapowania roli w zarejestrowany endpoint JEA można ocenić, rozwijając danych we właściwości "RoleDefinitions".</span><span class="sxs-lookup"><span data-stu-id="113d3-112">You can evaluate the role mappings in a registered JEA endpoint by expanding the data in the "RoleDefinitions" property.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="113d3-113">Znajdź możliwości roli dostępnej na komputerze</span><span class="sxs-lookup"><span data-stu-id="113d3-113">Find available role capabilities on the machine</span></span>

<span data-ttu-id="113d3-114">JEA tylko będzie używać plikach możliwości roli, jeśli są one przechowywane w folderze "RoleCapabilities" wewnątrz prawidłowy moduł programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="113d3-114">Role capability files will only be used by JEA if they are stored in a "RoleCapabilities" folder inside a valid PowerShell module.</span></span>
<span data-ttu-id="113d3-115">Wszystkie funkcje roli można znaleźć na komputerze przez przeszukiwanie listy dostępnych modułów.</span><span class="sxs-lookup"><span data-stu-id="113d3-115">You can find all role capabilities available on a computer by searching the list of available modules.</span></span>

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
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{ Name = 'Path'; Expression = { $_.FullName }} | Sort-Object Name
}
```

> [!NOTE]
> <span data-ttu-id="113d3-116">Kolejność wyników z tej funkcji nie jest zawsze kolejność, w którym zostanie wybrany możliwości roli, jeśli wiele możliwości Rola o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="113d3-116">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="113d3-117">Sprawdź skuteczne prawa dla określonego użytkownika</span><span class="sxs-lookup"><span data-stu-id="113d3-117">Check effective rights for a specific user</span></span>

<span data-ttu-id="113d3-118">Po skonfigurowaniu punktu końcowego JEA można sprawdzić, które polecenia są dostępne dla określonego użytkownika w sesji JEA.</span><span class="sxs-lookup"><span data-stu-id="113d3-118">Once you have set up a JEA endpoint, you may want to check which commands are available to a specific user in a JEA session.</span></span>
<span data-ttu-id="113d3-119">Można użyć [Get PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) wylicza wszystkie polecenia mające zastosowanie do użytkownika, jeśli ich rozpocząć sesję JEA z ich bieżącego członkostwa w grupach.</span><span class="sxs-lookup"><span data-stu-id="113d3-119">You can use [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) to enumerate all of the commands applicable to a user if they were to start a JEA session with their current group memberships.</span></span>
<span data-ttu-id="113d3-120">Dane wyjściowe `Get-PSSessionCapability` jest identyczna jak określony użytkownik uruchamiający `Get-Command -CommandType All` w sesji JEA.</span><span class="sxs-lookup"><span data-stu-id="113d3-120">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="113d3-121">Jeśli użytkownicy nie są trwałe członkami grup, do których przyznano im dodatkowe prawa JEA, to polecenie cmdlet nie mogą uwzględniać te dodatkowe uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="113d3-121">If your users are not permanent members of groups which would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span>
<span data-ttu-id="113d3-122">Jest to zazwyczaj wielkość liter, używając uprzywilejowanego dostępu just in time systemy zarządzania do użytkownicy mogą tymczasowo należą do grupy zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="113d3-122">This is typically the case when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span>
<span data-ttu-id="113d3-123">Zawsze starannie oszacować mapowanie użytkowników do ról i zawartości każdej roli, aby upewnić się, że użytkownicy są tylko uzyskiwanie dostępu do minimalnej liczbie polecenia wymagane do wykonania swoich zadań pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="113d3-123">Always carefully evaluate the mapping of users to roles and the contents of each role to ensure users are only getting access to the least amount of commands needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="113d3-124">Dzienniki zdarzeń programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="113d3-124">PowerShell event logs</span></span>

<span data-ttu-id="113d3-125">Jeśli włączono bloku modułu i/lub skryptu logowania w systemie można znaleźć zdarzenia w dzienniku zdarzeń systemu Windows dla każdego polecenia, które użytkownik były uruchamiane w ich sesje JEA.</span><span class="sxs-lookup"><span data-stu-id="113d3-125">If you enabled module and/or script block logging on the system, you will be able to find events in the Windows event logs for each command a user ran in their JEA sessions.</span></span>
<span data-ttu-id="113d3-126">Aby znaleźć te zdarzenia, otwórz Podgląd zdarzeń systemu Windows, przejdź do **Microsoft-Windows-PowerShell/Operational** dziennika zdarzeń, a następnie wyszukaj zdarzenia o identyfikatorze zdarzenia **4104**.</span><span class="sxs-lookup"><span data-stu-id="113d3-126">To find these events, open the Windows Event Viewer, navigate to the **Microsoft-Windows-PowerShell/Operational** event log, and look for events with event ID **4104**.</span></span>

<span data-ttu-id="113d3-127">Każdy wpis dziennika zdarzeń będzie zawierać informacje o sesji, w którym zostało uruchomione polecenie.</span><span class="sxs-lookup"><span data-stu-id="113d3-127">Each event log entry will include information about the session in which the command was run.</span></span>
<span data-ttu-id="113d3-128">Sesje JEA to zawiera ważne informacje dotyczące **ConnectedUser**, czyli rzeczywistego użytkownika, który utworzył sesję JEA, jak również **nazwa_użytkownika** identyfikujący konto JEA używane do Wykonaj polecenie.</span><span class="sxs-lookup"><span data-stu-id="113d3-128">For JEA sessions, this includes important information about the **ConnectedUser**, which is the actual user who created the JEA session, as well as the **RunAsUser** which identifies the account JEA used to execute the command.</span></span>
<span data-ttu-id="113d3-129">Dzienniki zdarzeń aplikacji wyświetli zmian przez nazwa_użytkownika, więc o zapisy lub włączone rejestrowanie skryptu lub moduł jest niezwykle ważny móc śledzić wywołanie polecenia do użytkownika.</span><span class="sxs-lookup"><span data-stu-id="113d3-129">Application event logs will show changes being made by the RunAsUser, so having transcripts or module/script logging enabled is crucial to be able to trace a specific command invocation back to a user.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="113d3-130">Dzienniki zdarzeń aplikacji</span><span class="sxs-lookup"><span data-stu-id="113d3-130">Application event logs</span></span>

<span data-ttu-id="113d3-131">Po uruchomieniu polecenia w sesji JEA, która współdziała z zewnętrznych aplikacji lub usługi, te aplikacje mogą rejestrować zdarzenia do ich własnych dzienników zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="113d3-131">When you run a command in a JEA session that interacts with an external application or service, those applications may log events to their own event logs.</span></span>
<span data-ttu-id="113d3-132">W odróżnieniu od dzienniki programu PowerShell i zapisy innych mechanizmów rejestrowania nie będzie przechwytywać podłączonego użytkownika sesji JEA i zamiast tego zostanie tylko dziennika wirtualnego użytkownika Uruchom jako lub konto usługi zarządzane przez grupę.</span><span class="sxs-lookup"><span data-stu-id="113d3-132">Unlike PowerShell logs and transcripts, other logging mechanisms will not capture the connected user of the JEA session, and will instead only log the virtual run-as user or group managed service account.</span></span>
<span data-ttu-id="113d3-133">Aby ustalić, który uruchomił polecenie, należy skontaktować się [wykaz sesji](#session-transcripts) lub skorelowania dzienników zdarzeń programu PowerShell z czasem i wyświetlane w dzienniku zdarzeń aplikacji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="113d3-133">In order to determine who ran the command, you will need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="113d3-134">WinRM dziennika też pomóc Ci skorelowania Uruchom jako użytkownikom użytkownik nawiązujący połączenie z dziennika zdarzeń aplikacji.</span><span class="sxs-lookup"><span data-stu-id="113d3-134">The WinRM log can also help you correlate run as users in an application event log with the connecting user.</span></span>
<span data-ttu-id="113d3-135">Identyfikator zdarzenia **193** w **Microsoft-Windows-Windows zdalnego zarządzania/Operational** rejestrowania rekordów identyfikator zabezpieczeń (SID) i konto nazwy użytkownik nawiązujący połączenie i Uruchom jako użytkownik zawsze JEA zostanie utworzona sesja.</span><span class="sxs-lookup"><span data-stu-id="113d3-135">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user every time a JEA session is created.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="113d3-136">Zapisy sesji</span><span class="sxs-lookup"><span data-stu-id="113d3-136">Session transcripts</span></span>

<span data-ttu-id="113d3-137">Jeśli skonfigurowano JEA utworzyć zapisu dla każdej sesji użytkownika, kopię tekstu akcje każdego użytkownika będą przechowywane w określonym folderze.</span><span class="sxs-lookup"><span data-stu-id="113d3-137">If you configured JEA to create a transcript for each user session, a text copy of every user's actions will be stored in the specified folder.</span></span>

<span data-ttu-id="113d3-138">Znajdź wszystkie katalogi wykaz, uruchom następujące polecenie z uprawnieniami administratora na komputerze skonfigurowano JEA:</span><span class="sxs-lookup"><span data-stu-id="113d3-138">To find all transcript directories, run the following command as an administrator on the computer configured with JEA:</span></span>

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="113d3-139">Każdy zapis rozpoczyna się od informacji o czas rozpoczęcia sesji, które użytkownik podłączony do sesji, a tożsamość JEA przypisano do nich.</span><span class="sxs-lookup"><span data-stu-id="113d3-139">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="113d3-140">W treści wykaz rejestrowania informacji o każdym poleceniu użytkownik wywołał.</span><span class="sxs-lookup"><span data-stu-id="113d3-140">In the body of the transcript, information is logged about each command the user invoked.</span></span>
<span data-ttu-id="113d3-141">Dokładna Składnia polecenia, które użytkownik uruchomi jest niedostępna w sesji JEA ze względu na sposób polecenia są przekształcane komunikację zdalną programu PowerShell, ale nadal można określić polecenie skuteczne, które zostało wykonane.</span><span class="sxs-lookup"><span data-stu-id="113d3-141">The exact syntax of the command the user ran is unavailable in JEA sessions due to the way commands are transformed for PowerShell remoting, however you can still determine the effective command that was executed.</span></span>
<span data-ttu-id="113d3-142">Poniżej znajduje się przykład wykaz fragmencie użytkownik, który uruchomił `Get-Service Dns` w sesji JEA:</span><span class="sxs-lookup"><span data-stu-id="113d3-142">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="113d3-143">Dla każdego polecenia przez użytkownika wiersza "CommandInvocation" będą zapisywane, opisujący polecenia cmdlet lub funkcji użytkownika wywołany.</span><span class="sxs-lookup"><span data-stu-id="113d3-143">For each command a user runs, a "CommandInvocation" line will be written, describing the cmdlet or function the user invoked.</span></span>
<span data-ttu-id="113d3-144">ParameterBindings postępuj zgodnie z każdym CommandInvocation informujące o każdego parametru i wartość, która została dostarczona z poleceniem.</span><span class="sxs-lookup"><span data-stu-id="113d3-144">ParameterBindings follow each CommandInvocation to tell you about each parameter and value that was supplied with the command.</span></span>
<span data-ttu-id="113d3-145">W powyższym przykładzie widać, że parametr, który "Name" została podana wartość "Dns" dla polecenia cmdlet "Get-Service".</span><span class="sxs-lookup"><span data-stu-id="113d3-145">In the above example, you can see that the parameter "Name" was supplied the value "Dns" for the "Get-Service" cmdlet.</span></span>

<span data-ttu-id="113d3-146">Dane wyjściowe każdego polecenia również wyzwoli CommandInvocation, zwykle wyjściowego domyślne.</span><span class="sxs-lookup"><span data-stu-id="113d3-146">The output of each command will also trigger a CommandInvocation, usually to Out-Default.</span></span>
<span data-ttu-id="113d3-147">InputObject Out-Default jest obiekt programu PowerShell zwrócił polecenia.</span><span class="sxs-lookup"><span data-stu-id="113d3-147">The InputObject of Out-Default is the PowerShell object returned from the command.</span></span>
<span data-ttu-id="113d3-148">Szczegóły tego obiektu są podane kilka wierszy poniżej, ściśle mimicking, co użytkownik może umieścić.</span><span class="sxs-lookup"><span data-stu-id="113d3-148">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="113d3-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="113d3-149">See also</span></span>

- [<span data-ttu-id="113d3-150">Akcje inspekcji użytkownika w sesji JEA</span><span class="sxs-lookup"><span data-stu-id="113d3-150">Audit user actions in a JEA session</span></span>](audit-and-report.md)
- [<span data-ttu-id="113d3-151">*PowerShell ♥ niebieski zespołu* wpis w blogu dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="113d3-151">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)