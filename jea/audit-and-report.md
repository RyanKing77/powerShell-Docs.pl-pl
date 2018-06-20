---
ms.date: 06/12/2017
keywords: jea, programu powershell, zabezpieczeń
title: Inspekcja i raportowania JEA
ms.openlocfilehash: e68206cd6fe94c51507f42ae2c3e6702f6fd4e0f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188856"
---
# <a name="auditing-and-reporting-on-jea"></a>Inspekcja i raportowania JEA

> Dotyczy: środowiska Windows PowerShell 5.0

Po wdrożeniu JEA, należy regularnie inspekcji JEA konfiguracji.
Dzięki temu łatwiej ocenić, jeśli osobom mają dostęp do punktu końcowego JEA i przypisane im role będą nadal odpowiednie.

W tym temacie opisano różne sposoby, można przeprowadzić inspekcję punktu końcowego JEA.

## <a name="find-registered-jea-sessions-on-a-machine"></a>Znajdź zarejestrowanych JEA sesji na komputerze

Aby sprawdzić, które sesje JEA są rejestrowane na komputerze, użyj [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) polecenia cmdlet.

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

Skuteczne prawa dla punktu końcowego są wyświetlane we właściwości "Uprawnienia".
Ci użytkownicy mają prawo do nawiązywania połączenia z punktem końcowym JEA, ale które role (i przez rozszerzenie, poleceń) mają dostęp, jest określany przez pole "RoleDefinitions" w [pliku konfiguracji sesji](session-configurations.md) użytą do zarejestrowania punkt końcowy.

Mapowania roli w zarejestrowany endpoint JEA można ocenić, rozwijając danych we właściwości "RoleDefinitions".

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a>Znajdź możliwości roli dostępnej na komputerze

JEA tylko będzie używać plikach możliwości roli, jeśli są one przechowywane w folderze "RoleCapabilities" wewnątrz prawidłowy moduł programu PowerShell.
Wszystkie funkcje roli można znaleźć na komputerze przez przeszukiwanie listy dostępnych modułów.

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
> Kolejność wyników z tej funkcji nie jest zawsze kolejność, w którym zostanie wybrany możliwości roli, jeśli wiele możliwości Rola o tej samej nazwie.

## <a name="check-effective-rights-for-a-specific-user"></a>Sprawdź skuteczne prawa dla określonego użytkownika

Po skonfigurowaniu punktu końcowego JEA można sprawdzić, które polecenia są dostępne dla określonego użytkownika w sesji JEA.
Można użyć [Get PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) wylicza wszystkie polecenia mające zastosowanie do użytkownika, jeśli ich rozpocząć sesję JEA z ich bieżącego członkostwa w grupach.
Dane wyjściowe `Get-PSSessionCapability` jest identyczna jak określony użytkownik uruchamiający `Get-Command -CommandType All` w sesji JEA.

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

Jeśli użytkownicy nie są trwałe członkami grup, do których przyznano im dodatkowe prawa JEA, to polecenie cmdlet nie mogą uwzględniać te dodatkowe uprawnienia.
Jest to zazwyczaj wielkość liter, używając uprzywilejowanego dostępu just in time systemy zarządzania do użytkownicy mogą tymczasowo należą do grupy zabezpieczeń.
Zawsze starannie oszacować mapowanie użytkowników do ról i zawartości każdej roli, aby upewnić się, że użytkownicy są tylko uzyskiwanie dostępu do minimalnej liczbie polecenia wymagane do wykonania swoich zadań pomyślnie.

## <a name="powershell-event-logs"></a>Dzienniki zdarzeń programu PowerShell

Jeśli włączono bloku modułu i/lub skryptu logowania w systemie można znaleźć zdarzenia w dzienniku zdarzeń systemu Windows dla każdego polecenia, które użytkownik były uruchamiane w ich sesje JEA.
Aby znaleźć te zdarzenia, otwórz Podgląd zdarzeń systemu Windows, przejdź do **Microsoft-Windows-PowerShell/Operational** dziennika zdarzeń, a następnie wyszukaj zdarzenia o identyfikatorze zdarzenia **4104**.

Każdy wpis dziennika zdarzeń będzie zawierać informacje o sesji, w którym zostało uruchomione polecenie.
Sesje JEA to zawiera ważne informacje dotyczące **ConnectedUser**, czyli rzeczywistego użytkownika, który utworzył sesję JEA, jak również **nazwa_użytkownika** identyfikujący konto JEA używane do Wykonaj polecenie.
Dzienniki zdarzeń aplikacji wyświetli zmian przez nazwa_użytkownika, więc o zapisy lub włączone rejestrowanie skryptu lub moduł jest niezwykle ważny móc śledzić wywołanie polecenia do użytkownika.

## <a name="application-event-logs"></a>Dzienniki zdarzeń aplikacji

Po uruchomieniu polecenia w sesji JEA, która współdziała z zewnętrznych aplikacji lub usługi, te aplikacje mogą rejestrować zdarzenia do ich własnych dzienników zdarzeń.
W odróżnieniu od dzienniki programu PowerShell i zapisy innych mechanizmów rejestrowania nie będzie przechwytywać podłączonego użytkownika sesji JEA i zamiast tego zostanie tylko dziennika wirtualnego użytkownika Uruchom jako lub konto usługi zarządzane przez grupę.
Aby ustalić, który uruchomił polecenie, należy skontaktować się [wykaz sesji](#session-transcripts) lub skorelowania dzienników zdarzeń programu PowerShell z czasem i wyświetlane w dzienniku zdarzeń aplikacji użytkownika.

WinRM dziennika też pomóc Ci skorelowania Uruchom jako użytkownikom użytkownik nawiązujący połączenie z dziennika zdarzeń aplikacji.
Identyfikator zdarzenia **193** w **Microsoft-Windows-Windows zdalnego zarządzania/Operational** rejestrowania rekordów identyfikator zabezpieczeń (SID) i konto nazwy użytkownik nawiązujący połączenie i Uruchom jako użytkownik zawsze JEA zostanie utworzona sesja.

## <a name="session-transcripts"></a>Zapisy sesji

Jeśli skonfigurowano JEA utworzyć zapisu dla każdej sesji użytkownika, kopię tekstu akcje każdego użytkownika będą przechowywane w określonym folderze.

Znajdź wszystkie katalogi wykaz, uruchom następujące polecenie z uprawnieniami administratora na komputerze skonfigurowano JEA:

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
```

Każdy zapis rozpoczyna się od informacji o czas rozpoczęcia sesji, które użytkownik podłączony do sesji, a tożsamość JEA przypisano do nich.

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

W treści wykaz rejestrowania informacji o każdym poleceniu użytkownik wywołał.
Dokładna Składnia polecenia, które użytkownik uruchomi jest niedostępna w sesji JEA ze względu na sposób polecenia są przekształcane komunikację zdalną programu PowerShell, ale nadal można określić polecenie skuteczne, które zostało wykonane.
Poniżej znajduje się przykład wykaz fragmencie użytkownik, który uruchomił `Get-Service Dns` w sesji JEA:

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

Dla każdego polecenia przez użytkownika wiersza "CommandInvocation" będą zapisywane, opisujący polecenia cmdlet lub funkcji użytkownika wywołany.
ParameterBindings postępuj zgodnie z każdym CommandInvocation informujące o każdego parametru i wartość, która została dostarczona z poleceniem.
W powyższym przykładzie widać, że parametr, który "Name" została podana wartość "Dns" dla polecenia cmdlet "Get-Service".

Dane wyjściowe każdego polecenia również wyzwoli CommandInvocation, zwykle wyjściowego domyślne.
InputObject Out-Default jest obiekt programu PowerShell zwrócił polecenia.
Szczegóły tego obiektu są podane kilka wierszy poniżej, ściśle mimicking, co użytkownik może umieścić.

## <a name="see-also"></a>Zobacz też

- [Akcje inspekcji użytkownika w sesji JEA](audit-and-report.md)
- [*PowerShell ♥ niebieski zespołu* wpis w blogu dotyczące zabezpieczeń](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)