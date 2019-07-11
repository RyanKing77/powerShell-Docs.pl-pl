---
ms.date: 07/10/2019
keywords: jea, programu powershell, zabezpieczeń
title: Inspekcja i raporty dotyczące technologii JEA
ms.openlocfilehash: 2afefe83acecc1fc3643d49766120ffecc25378f
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726760"
---
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="3a307-103">Inspekcja i raporty dotyczące technologii JEA</span><span class="sxs-lookup"><span data-stu-id="3a307-103">Auditing and Reporting on JEA</span></span>

<span data-ttu-id="3a307-104">Po wdrożeniu usługi JEA, należy regularnie inspekcji konfiguracji JEA.</span><span class="sxs-lookup"><span data-stu-id="3a307-104">After you've deployed JEA, you need to regularly audit the JEA configuration.</span></span> <span data-ttu-id="3a307-105">Inspekcja pomaga ocenić czy poprawny osoby mają dostęp do punktu końcowego JEA i ich przypisane role są nadal odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="3a307-105">Auditing helps you assess that the correct people have access to the JEA endpoint and their assigned roles are still appropriate.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="3a307-106">Znajdź zarejestrowany technologii JEA sesji na komputerze</span><span class="sxs-lookup"><span data-stu-id="3a307-106">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="3a307-107">Aby sprawdzić, które sesje JEA są rejestrowane na komputerze, użyj [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3a307-107">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

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

<span data-ttu-id="3a307-108">Obowiązujące prawa dla punktu końcowego są wymienione w **uprawnienie** właściwości.</span><span class="sxs-lookup"><span data-stu-id="3a307-108">The effective rights for the endpoint are listed in the **Permission** property.</span></span> <span data-ttu-id="3a307-109">Tacy użytkownicy mają prawo do nawiązywania połączenia punktu końcowego JEA.</span><span class="sxs-lookup"><span data-stu-id="3a307-109">These users have the right to connect to the JEA endpoint.</span></span> <span data-ttu-id="3a307-110">Jednak role i mają dostęp do poleceń jest określana przez **RoleDefinitions** właściwość [plik konfiguracji sesji](session-configurations.md) który został użyty do zarejestrowania punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="3a307-110">However, the roles and commands they have access to is determined by the **RoleDefinitions** property in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span> <span data-ttu-id="3a307-111">Rozwiń **RoleDefinitions** właściwości do oceny mapowań ról w punkcie końcowym programu zarejestrowany technologii JEA.</span><span class="sxs-lookup"><span data-stu-id="3a307-111">Expand the **RoleDefinitions** property to evaluate the role mappings in a registered JEA endpoint.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="3a307-112">Znajdowanie możliwości roli dostępne na komputerze</span><span class="sxs-lookup"><span data-stu-id="3a307-112">Find available role capabilities on the machine</span></span>

<span data-ttu-id="3a307-113">JEA pobiera możliwości roli z `.psrc` plików przechowywanych w **RoleCapabilities** folder wewnątrz modułu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3a307-113">JEA gets role capabilities from the `.psrc` files stored in the **RoleCapabilities** folder inside a PowerShell module.</span></span> <span data-ttu-id="3a307-114">Poniższa funkcja znajduje wszystkie funkcje roli na komputerze.</span><span class="sxs-lookup"><span data-stu-id="3a307-114">The following function finds all role capabilities available on a computer.</span></span>

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
> <span data-ttu-id="3a307-115">Kolejność wyników z tej funkcji nie jest koniecznie kolejność, w którym zostanie wybrany możliwości roli, jeśli wiele możliwości roli o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="3a307-115">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="3a307-116">Sprawdź obowiązujące prawa dla określonego użytkownika</span><span class="sxs-lookup"><span data-stu-id="3a307-116">Check effective rights for a specific user</span></span>

<span data-ttu-id="3a307-117">[Get PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) polecenia cmdlet wylicza wszystkich poleceń dostępnych w punkcie końcowym usługi JEA oparte na członkostwie grupy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3a307-117">The [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) cmdlet enumerates all the commands available on a JEA endpoint based on a user's group memberships.</span></span>
<span data-ttu-id="3a307-118">Dane wyjściowe `Get-PSSessionCapability` jest taka sama jak w przypadku określonego użytkownika uruchamiającego `Get-Command -CommandType All` w ramach sesji usługi JEA.</span><span class="sxs-lookup"><span data-stu-id="3a307-118">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="3a307-119">Jeśli użytkownicy nie są stałe elementy członkowskie grup, które może przyznać im dodatkowe prawa JEA, to polecenie cmdlet może nie odzwierciedlać te dodatkowe uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="3a307-119">If your users aren't permanent members of groups that would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span> <span data-ttu-id="3a307-120">Dzieje się po użyciu just-in-time uprzywilejowanego dostępu do systemów zarządzania, aby umożliwić użytkownikom tymczasowo należeć do grupy zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="3a307-120">This happens when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span> <span data-ttu-id="3a307-121">Należy wnikliwie zastanowić się mapowanie użytkowników do ról i funkcji, aby upewnić się, że użytkownicy pobierają tylko poziom dostępu wymagane do wykonywania ich zadań pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="3a307-121">Carefully evaluate the mapping of users to roles and capabilities to ensure that users only get the level of access needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="3a307-122">Dzienniki zdarzeń programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="3a307-122">PowerShell event logs</span></span>

<span data-ttu-id="3a307-123">Jeśli został włączony moduł lub skrypt bloku rejestrowania w systemie, zostanie wyświetlony zdarzeń w dzienniku zdarzeń Windows dla każdego polecenia, które użytkownik, który jest uruchamiany w ramach sesji usługi JEA.</span><span class="sxs-lookup"><span data-stu-id="3a307-123">If you enabled module or script block logging on the system, you can see events in the Windows event logs for each command a user runs in a JEA session.</span></span> <span data-ttu-id="3a307-124">Aby znaleźć te zdarzenia, otwórz **Microsoft-Windows-PowerShell/Operational** dziennika zdarzeń i wyszukać zdarzenia o identyfikatorze zdarzenia **4104**.</span><span class="sxs-lookup"><span data-stu-id="3a307-124">To find these events, open **Microsoft-Windows-PowerShell/Operational** event log and look for events with event ID **4104**.</span></span>

<span data-ttu-id="3a307-125">Każdy wpis dziennika zdarzeń zawiera informacje o sesji, w którym zostało uruchomione polecenie.</span><span class="sxs-lookup"><span data-stu-id="3a307-125">Each event log entry includes information about the session in which the command was run.</span></span> <span data-ttu-id="3a307-126">Sesje usługi JEA zdarzenia zawiera informacje o **ConnectedUser** i **nazwa_użytkownika**.</span><span class="sxs-lookup"><span data-stu-id="3a307-126">For JEA sessions, the event includes information about the **ConnectedUser** and the **RunAsUser**.</span></span> <span data-ttu-id="3a307-127">**ConnectedUser** jest rzeczywisty użytkownik, który utworzył sesję JEA.</span><span class="sxs-lookup"><span data-stu-id="3a307-127">The **ConnectedUser** is the actual user who created the JEA session.</span></span> <span data-ttu-id="3a307-128">**Nazwa_użytkownika** to konto usługi JEA służącego do wykonania polecenia.</span><span class="sxs-lookup"><span data-stu-id="3a307-128">The **RunAsUser** is the account JEA used to execute the command.</span></span>

<span data-ttu-id="3a307-129">Dzienniki zdarzeń aplikacji Pokaż zmian wprowadzanych przez **nazwa_użytkownika**.</span><span class="sxs-lookup"><span data-stu-id="3a307-129">Application event logs show changes being made by the **RunAsUser**.</span></span> <span data-ttu-id="3a307-130">Dlatego moduł i włączone rejestrowanie skryptu jest wymagane do śledzenia z powrotem do wywołania określonego polecenia **ConnectedUser**.</span><span class="sxs-lookup"><span data-stu-id="3a307-130">So having module and script logging enabled is required to trace a specific command invocation back to the **ConnectedUser**.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="3a307-131">Dzienniki zdarzeń aplikacji</span><span class="sxs-lookup"><span data-stu-id="3a307-131">Application event logs</span></span>

<span data-ttu-id="3a307-132">Polecenia są uruchamiane w sesji JEA, która wchodzić w interakcje z aplikacjami zewnętrznymi lub usługi mogą rejestrować zdarzenia do ich własnych dzienników zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="3a307-132">Commands run in a JEA session that interact with external applications or services may log events to their own event logs.</span></span> <span data-ttu-id="3a307-133">W przeciwieństwie do dzienników programu PowerShell i zapisy innych mechanizmów rejestrowania nie należy przechwytywać połączonego użytkownika sesji JEA.</span><span class="sxs-lookup"><span data-stu-id="3a307-133">Unlike PowerShell logs and transcripts, other logging mechanisms don't capture the connected user of the JEA session.</span></span> <span data-ttu-id="3a307-134">Zamiast tego te aplikacje dziennika wirtualnego użytkownika Uruchom jako.</span><span class="sxs-lookup"><span data-stu-id="3a307-134">Instead, those applications only log the virtual run-as user.</span></span>
<span data-ttu-id="3a307-135">Aby ustalić, który uruchomił polecenie, należy zapoznać się [transkrypcji sesji](#session-transcripts) lub skorelowania dzienników zdarzeń programu PowerShell z czasem i użytkownika, przedstawione w dzienniku zdarzeń aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3a307-135">To determine who ran the command, you need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="3a307-136">Dziennik usługi WinRM można również ułatwić skorelować użytkowników Uruchom jako użytkownik nawiązujący połączenie z dziennika zdarzeń aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3a307-136">The WinRM log can also help you correlate run-as users to the connecting user in an application event log.</span></span> <span data-ttu-id="3a307-137">Identyfikator zdarzenia **193** w **Microsoft-Windows-Windows zdalnego zarządzania/Operational** dziennika rejestruje identyfikator zabezpieczeń (SID) i nazwa konta zarówno dla połączenia użytkownika i Uruchom jako użytkownik dla każdej nowej usługi JEA sesji.</span><span class="sxs-lookup"><span data-stu-id="3a307-137">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user for every new JEA session.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="3a307-138">Zapisy sesji</span><span class="sxs-lookup"><span data-stu-id="3a307-138">Session transcripts</span></span>

<span data-ttu-id="3a307-139">Jeśli skonfigurowano JEA, aby utworzyć transkrypcję dla każdej sesji użytkownika kopię tekstu działania każdego z użytkowników są przechowywane we wskazanym folderze.</span><span class="sxs-lookup"><span data-stu-id="3a307-139">If you configured JEA to create a transcript for each user session, a text copy of every user's actions are stored in the specified folder.</span></span>

<span data-ttu-id="3a307-140">Następujące polecenie (jako administrator) umożliwia znalezienie wszystkich katalogów transkrypcji.</span><span class="sxs-lookup"><span data-stu-id="3a307-140">The following command (as an administrator) finds all transcript directories.</span></span>

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="3a307-141">Każdy transkrypcji rozpoczyna się od informacji o czasie rozpoczęcia sesji, który użytkownik podłączonego do sesji i tożsamość usługi JEA przypisano do nich.</span><span class="sxs-lookup"><span data-stu-id="3a307-141">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="3a307-142">Treść tej transkrypcji zawiera informacje o każdym poleceniu użytkownik wywołał.</span><span class="sxs-lookup"><span data-stu-id="3a307-142">The body of the transcript contains information about each command the user invoked.</span></span> <span data-ttu-id="3a307-143">Dokładna Składnia polecenia używane jest niedostępna w sesji JEA ze względu na sposób, w jaki polecenia są przekształcane do komunikacji zdalnej programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3a307-143">The exact syntax of the command used is unavailable in JEA sessions because of the way commands are transformed for PowerShell remoting.</span></span> <span data-ttu-id="3a307-144">Można jednak nadal określić skuteczne polecenia, który został wykonany.</span><span class="sxs-lookup"><span data-stu-id="3a307-144">However, you can still determine the effective command that was executed.</span></span> <span data-ttu-id="3a307-145">Poniżej przedstawiono fragment transkrypcji przykład od użytkownika uruchamiania `Get-Service Dns` w ramach sesji usługi JEA:</span><span class="sxs-lookup"><span data-stu-id="3a307-145">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="3a307-146">A **CommandInvocation** wiersz jest przeznaczony dla każdego polecenia, gdy użytkownik uruchamia.</span><span class="sxs-lookup"><span data-stu-id="3a307-146">A **CommandInvocation** line is written for each command a user runs.</span></span> <span data-ttu-id="3a307-147">**ParameterBindings** zarejestrować każdy parametr i wartość dostarczona z poleceniem.</span><span class="sxs-lookup"><span data-stu-id="3a307-147">**ParameterBindings** record each parameter and value supplied with the command.</span></span> <span data-ttu-id="3a307-148">W poprzednim przykładzie możesz zobaczyć, że parametr **nazwa** została podana z wartością **Dns** dla `Get-Service` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3a307-148">In the previous example, you can see that the parameter **Name** was supplied the with value **Dns** for the `Get-Service` cmdlet.</span></span>

<span data-ttu-id="3a307-149">Dane wyjściowe każdego polecenia także wyzwalacze **CommandInvocation**, zwykle `Out-Default`.</span><span class="sxs-lookup"><span data-stu-id="3a307-149">The output of each command also triggers a **CommandInvocation**, usually to `Out-Default`.</span></span> <span data-ttu-id="3a307-150">**InputObject** z `Out-Default` polecenie zostanie zwrócony obiekt programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3a307-150">The **InputObject** of `Out-Default` is the PowerShell object returned from the command.</span></span> <span data-ttu-id="3a307-151">Szczegóły tego obiektu, wydrukowaniu kilka wierszy poniżej, ściśle naśladując, co użytkownik będzie mieć widoczne.</span><span class="sxs-lookup"><span data-stu-id="3a307-151">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="3a307-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3a307-152">See also</span></span>

[<span data-ttu-id="3a307-153">*Program PowerShell ♥ zespołem niebieskim* wpis w blogu dotyczący zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="3a307-153">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
