---
ms.date: 06/12/2017
keywords: jea, programu powershell, zabezpieczeń
title: Inspekcja i raporty dotyczące technologii JEA
ms.openlocfilehash: 2388c735840d8d3683aa8bc9869b9fb0371e5902
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688602"
---
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="d54e2-103">Inspekcja i raporty dotyczące technologii JEA</span><span class="sxs-lookup"><span data-stu-id="d54e2-103">Auditing and Reporting on JEA</span></span>

> <span data-ttu-id="d54e2-104">Dotyczy: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d54e2-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="d54e2-105">Po wdrożeniu usługi JEA, należy regularnie inspekcji konfiguracji JEA.</span><span class="sxs-lookup"><span data-stu-id="d54e2-105">After you've deployed JEA, you will want to regularly audit the JEA configuration.</span></span>
<span data-ttu-id="d54e2-106">To pomoże Ci ocenić, jeśli poprawne osoby mają dostęp do punktu końcowego JEA i ich przypisane role są nadal odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="d54e2-106">This will help you assess if the correct people have access to the JEA endpoint and if their assigned roles are still appropriate.</span></span>

<span data-ttu-id="d54e2-107">W tym temacie opisano różne sposoby, które można przeprowadzać ich inspekcje punktu końcowego JEA.</span><span class="sxs-lookup"><span data-stu-id="d54e2-107">This topic describes the various ways you can audit a JEA endpoint.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="d54e2-108">Znajdź zarejestrowany technologii JEA sesji na komputerze</span><span class="sxs-lookup"><span data-stu-id="d54e2-108">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="d54e2-109">Aby sprawdzić, które sesje JEA są rejestrowane na komputerze, użyj [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d54e2-109">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

<span data-ttu-id="d54e2-110">Skuteczne prawa dla punktu końcowego są wymienione w właściwość "Uprawnienia".</span><span class="sxs-lookup"><span data-stu-id="d54e2-110">The effective rights for the endpoint are listed in the "Permission" property.</span></span>
<span data-ttu-id="d54e2-111">Tacy użytkownicy mają prawo do nawiązywania połączenia punktu końcowego JEA, ale które role (i według rozszerzeń poleceń) mają dostęp, jest określany przez pole "RoleDefinitions" [plik konfiguracji sesji](session-configurations.md) który został użyty do zarejestrowania punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="d54e2-111">These users have the right to connect to the JEA endpoint, but which roles (and, by extension, commands) they have access to is determined by the "RoleDefinitions" field in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span>

<span data-ttu-id="d54e2-112">Możesz ocenić mapowań ról w punkcie końcowym programu zarejestrowany technologii JEA, rozwijając danych we właściwości "RoleDefinitions".</span><span class="sxs-lookup"><span data-stu-id="d54e2-112">You can evaluate the role mappings in a registered JEA endpoint by expanding the data in the "RoleDefinitions" property.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="d54e2-113">Znajdowanie możliwości roli dostępne na komputerze</span><span class="sxs-lookup"><span data-stu-id="d54e2-113">Find available role capabilities on the machine</span></span>

<span data-ttu-id="d54e2-114">Pliki możliwości roli tylko będzie używana przez usługi JEA, jeśli są one przechowywane w folderze "RoleCapabilities" wewnątrz prawidłowy modułu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d54e2-114">Role capability files will only be used by JEA if they are stored in a "RoleCapabilities" folder inside a valid PowerShell module.</span></span>
<span data-ttu-id="d54e2-115">Wszystkie funkcje roli na komputerze można znaleźć, przeszukując listę dostępnych modułów.</span><span class="sxs-lookup"><span data-stu-id="d54e2-115">You can find all role capabilities available on a computer by searching the list of available modules.</span></span>

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
> <span data-ttu-id="d54e2-116">Kolejność wyników z tej funkcji nie jest koniecznie kolejność, w którym zostanie wybrany możliwości roli, jeśli wiele możliwości roli o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="d54e2-116">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="d54e2-117">Sprawdź obowiązujące prawa dla określonego użytkownika</span><span class="sxs-lookup"><span data-stu-id="d54e2-117">Check effective rights for a specific user</span></span>

<span data-ttu-id="d54e2-118">Po skonfigurowaniu punktu końcowego JEA można sprawdzić, jakie polecenia są dostępne dla określonego użytkownika w ramach sesji usługi JEA.</span><span class="sxs-lookup"><span data-stu-id="d54e2-118">Once you have set up a JEA endpoint, you may want to check which commands are available to a specific user in a JEA session.</span></span>
<span data-ttu-id="d54e2-119">Możesz użyć [Get PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) można wyliczyć wszystkie polecenia, które są stosowane do użytkownika, gdyby można uruchomić sesji JEA z ich bieżącego członkostwa w grupach.</span><span class="sxs-lookup"><span data-stu-id="d54e2-119">You can use [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) to enumerate all of the commands applicable to a user if they were to start a JEA session with their current group memberships.</span></span>
<span data-ttu-id="d54e2-120">Dane wyjściowe `Get-PSSessionCapability` jest taka sama jak w przypadku określonego użytkownika uruchamiającego `Get-Command -CommandType All` w ramach sesji usługi JEA.</span><span class="sxs-lookup"><span data-stu-id="d54e2-120">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="d54e2-121">Jeśli użytkownicy nie są stałe elementy członkowskie grup, które może przyznać im dodatkowe prawa JEA, to polecenie cmdlet może nie odzwierciedlać te dodatkowe uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="d54e2-121">If your users are not permanent members of groups which would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span>
<span data-ttu-id="d54e2-122">Zazwyczaj jest to przypadek, korzystając z systemów zarządzania uprzywilejowany dostęp just in time umożliwiające użytkownikom tymczasowo należeć do grupy zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="d54e2-122">This is typically the case when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span>
<span data-ttu-id="d54e2-123">Zawsze należy wnikliwie zastanowić się, mapowanie użytkowników do ról i zawartość każdej roli, aby upewnić się, że użytkownicy otrzymują tylko dostęp do minimalnej liczbie polecenia są potrzebne do wykonywania ich zadań pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d54e2-123">Always carefully evaluate the mapping of users to roles and the contents of each role to ensure users are only getting access to the least amount of commands needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="d54e2-124">Dzienniki zdarzeń programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="d54e2-124">PowerShell event logs</span></span>

<span data-ttu-id="d54e2-125">Jeśli włączono modułu i/lub skrypt bloku rejestrowania w systemie można znaleźć zdarzenia w dzienniku zdarzeń Windows dla każdego polecenia, które użytkownik został uruchomiony w ich sesji usługi JEA.</span><span class="sxs-lookup"><span data-stu-id="d54e2-125">If you enabled module and/or script block logging on the system, you will be able to find events in the Windows event logs for each command a user ran in their JEA sessions.</span></span>
<span data-ttu-id="d54e2-126">Aby znaleźć te zdarzenia, otwórz Podgląd zdarzeń Windows, przejdź do **Microsoft-Windows-PowerShell/Operational** dziennika zdarzeń, a następnie sprawdź zdarzenia o identyfikatorze zdarzenia **4104**.</span><span class="sxs-lookup"><span data-stu-id="d54e2-126">To find these events, open the Windows Event Viewer, navigate to the **Microsoft-Windows-PowerShell/Operational** event log, and look for events with event ID **4104**.</span></span>

<span data-ttu-id="d54e2-127">Każdy wpis dziennika zdarzeń będzie zawierać informacje o sesji, w którym zostało uruchomione polecenie.</span><span class="sxs-lookup"><span data-stu-id="d54e2-127">Each event log entry will include information about the session in which the command was run.</span></span>
<span data-ttu-id="d54e2-128">Sesje usługi JEA to zawiera ważne informacje o **ConnectedUser**, czyli rzeczywisty użytkownik, który utworzył sesję JEA, jak również **nazwa_użytkownika** identyfikujący konto usługi JEA używane do Wykonaj polecenie.</span><span class="sxs-lookup"><span data-stu-id="d54e2-128">For JEA sessions, this includes important information about the **ConnectedUser**, which is the actual user who created the JEA session, as well as the **RunAsUser** which identifies the account JEA used to execute the command.</span></span>
<span data-ttu-id="d54e2-129">Dzienniki zdarzeń aplikacji pokaże zmian wprowadzanych przez nazwa_użytkownika, więc o transkrypcji lub włączone rejestrowanie modułu/skrypt jest niezwykle istotne można było śledzić wywołanie określonego polecenia do użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d54e2-129">Application event logs will show changes being made by the RunAsUser, so having transcripts or module/script logging enabled is crucial to be able to trace a specific command invocation back to a user.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="d54e2-130">Dzienniki zdarzeń aplikacji</span><span class="sxs-lookup"><span data-stu-id="d54e2-130">Application event logs</span></span>

<span data-ttu-id="d54e2-131">Po uruchomieniu polecenia w sesji JEA, która wchodzi w interakcję z zewnętrznych aplikacji lub usługi te aplikacje mogą rejestrować zdarzenia własne dzienniki zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d54e2-131">When you run a command in a JEA session that interacts with an external application or service, those applications may log events to their own event logs.</span></span>
<span data-ttu-id="d54e2-132">W przeciwieństwie do dzienników programu PowerShell i zapisy innych mechanizmów rejestrowania nie będzie przechwytywać połączonego użytkownika sesji JEA i będzie zamiast tego zalogować się wyłącznie wirtualnego użytkownika Uruchom jako i kont usług zarządzanych przez grupę.</span><span class="sxs-lookup"><span data-stu-id="d54e2-132">Unlike PowerShell logs and transcripts, other logging mechanisms will not capture the connected user of the JEA session, and will instead only log the virtual run-as user or group managed service account.</span></span>
<span data-ttu-id="d54e2-133">Aby ustalić, który uruchomił polecenie, należy zapoznać się z [transkrypcji sesji](#session-transcripts) lub skorelowania dzienników zdarzeń programu PowerShell z czasem i użytkownika, przedstawione w dzienniku zdarzeń aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d54e2-133">In order to determine who ran the command, you will need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="d54e2-134">WinRM dziennika może też pomóc skorelować Uruchom jako użytkownikom w dzienniku zdarzeń aplikacji użytkownik nawiązujący połączenie.</span><span class="sxs-lookup"><span data-stu-id="d54e2-134">The WinRM log can also help you correlate run as users in an application event log with the connecting user.</span></span>
<span data-ttu-id="d54e2-135">Identyfikator zdarzenia **193** w **Microsoft-Windows-Windows zdalnego zarządzania/Operational** rejestrowania rekordów identyfikator zabezpieczeń (SID) i konto nazwy użytkownik nawiązujący połączenie i jako użytkownika co czas wykonywania usługi JEA zostanie utworzona sesja.</span><span class="sxs-lookup"><span data-stu-id="d54e2-135">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user every time a JEA session is created.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="d54e2-136">Zapisy sesji</span><span class="sxs-lookup"><span data-stu-id="d54e2-136">Session transcripts</span></span>

<span data-ttu-id="d54e2-137">Jeśli skonfigurowano JEA, aby utworzyć transkrypcję dla każdej sesji użytkownika kopię tekstu akcji każdego użytkownika będą przechowywane we wskazanym folderze.</span><span class="sxs-lookup"><span data-stu-id="d54e2-137">If you configured JEA to create a transcript for each user session, a text copy of every user's actions will be stored in the specified folder.</span></span>

<span data-ttu-id="d54e2-138">Aby znaleźć wszystkie katalogi transkrypcji, uruchom następujące polecenie jako administrator na komputerze skonfigurowany przy użyciu technologii JEA:</span><span class="sxs-lookup"><span data-stu-id="d54e2-138">To find all transcript directories, run the following command as an administrator on the computer configured with JEA:</span></span>

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="d54e2-139">Każdy transkrypcji rozpoczyna się od informacji o czasie rozpoczęcia sesji, który użytkownik podłączonego do sesji i tożsamość usługi JEA przypisano do nich.</span><span class="sxs-lookup"><span data-stu-id="d54e2-139">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="d54e2-140">W treści transkrypcję rejestrowane są informacje dotyczące każdego polecenia, które użytkownik wywołał.</span><span class="sxs-lookup"><span data-stu-id="d54e2-140">In the body of the transcript, information is logged about each command the user invoked.</span></span>
<span data-ttu-id="d54e2-141">Dokładna Składnia polecenia, które użytkownik uruchomi jest niedostępna w sesji JEA ze względu na sposób polecenia są przekształcane do komunikacji zdalnej programu PowerShell, ale nadal można określić skuteczne polecenia, który został wykonany.</span><span class="sxs-lookup"><span data-stu-id="d54e2-141">The exact syntax of the command the user ran is unavailable in JEA sessions due to the way commands are transformed for PowerShell remoting, however you can still determine the effective command that was executed.</span></span>
<span data-ttu-id="d54e2-142">Poniżej przedstawiono fragment transkrypcji przykład od użytkownika uruchamiania `Get-Service Dns` w ramach sesji usługi JEA:</span><span class="sxs-lookup"><span data-stu-id="d54e2-142">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="d54e2-143">Dla każdego polecenia, które użytkownik uruchamia wiersz "CommandInvocation" zostanie zapisany, zawierająca opis polecenia cmdlet lub użytkownika, wywoływana funkcja.</span><span class="sxs-lookup"><span data-stu-id="d54e2-143">For each command a user runs, a "CommandInvocation" line will be written, describing the cmdlet or function the user invoked.</span></span>
<span data-ttu-id="d54e2-144">ParameterBindings postępuj zgodnie z każdym CommandInvocation informujące o każdego parametru i wartości, która została dostarczona z poleceniem.</span><span class="sxs-lookup"><span data-stu-id="d54e2-144">ParameterBindings follow each CommandInvocation to tell you about each parameter and value that was supplied with the command.</span></span>
<span data-ttu-id="d54e2-145">W powyższym przykładzie widać, że parametr, który został "Name" podana wartość "Dns" dla polecenia cmdlet "Get-Usługa".</span><span class="sxs-lookup"><span data-stu-id="d54e2-145">In the above example, you can see that the parameter "Name" was supplied the value "Dns" for the "Get-Service" cmdlet.</span></span>

<span data-ttu-id="d54e2-146">Dane wyjściowe każdego polecenia będzie również wyzwalać CommandInvocation zwykle wyjściowego domyślną.</span><span class="sxs-lookup"><span data-stu-id="d54e2-146">The output of each command will also trigger a CommandInvocation, usually to Out-Default.</span></span>
<span data-ttu-id="d54e2-147">InputObject Out-Default jest obiekt programu PowerShell, w zwróconym w poleceniu.</span><span class="sxs-lookup"><span data-stu-id="d54e2-147">The InputObject of Out-Default is the PowerShell object returned from the command.</span></span>
<span data-ttu-id="d54e2-148">Szczegóły tego obiektu, wydrukowaniu kilka wierszy poniżej, ściśle naśladując, co użytkownik będzie mieć widoczne.</span><span class="sxs-lookup"><span data-stu-id="d54e2-148">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="d54e2-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d54e2-149">See also</span></span>

- [<span data-ttu-id="d54e2-150">*Program PowerShell ♥ zespołem niebieskim* wpis w blogu dotyczący zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="d54e2-150">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)
