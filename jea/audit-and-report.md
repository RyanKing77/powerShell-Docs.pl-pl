---
ms.date: 06/12/2017
keywords: jea, programu powershell, zabezpieczeń
title: Inspekcja i raporty dotyczące technologii JEA
ms.openlocfilehash: 2388c735840d8d3683aa8bc9869b9fb0371e5902
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084083"
---
# <a name="auditing-and-reporting-on-jea"></a>Inspekcja i raporty dotyczące technologii JEA

> Dotyczy: Windows PowerShell 5.0

Po wdrożeniu usługi JEA, należy regularnie inspekcji konfiguracji JEA.
To pomoże Ci ocenić, jeśli poprawne osoby mają dostęp do punktu końcowego JEA i ich przypisane role są nadal odpowiednie.

W tym temacie opisano różne sposoby, które można przeprowadzać ich inspekcje punktu końcowego JEA.

## <a name="find-registered-jea-sessions-on-a-machine"></a>Znajdź zarejestrowany technologii JEA sesji na komputerze

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

Skuteczne prawa dla punktu końcowego są wymienione w właściwość "Uprawnienia".
Tacy użytkownicy mają prawo do nawiązywania połączenia punktu końcowego JEA, ale które role (i według rozszerzeń poleceń) mają dostęp, jest określany przez pole "RoleDefinitions" [plik konfiguracji sesji](session-configurations.md) który został użyty do zarejestrowania punkt końcowy.

Możesz ocenić mapowań ról w punkcie końcowym programu zarejestrowany technologii JEA, rozwijając danych we właściwości "RoleDefinitions".

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a>Znajdowanie możliwości roli dostępne na komputerze

Pliki możliwości roli tylko będzie używana przez usługi JEA, jeśli są one przechowywane w folderze "RoleCapabilities" wewnątrz prawidłowy modułu programu PowerShell.
Wszystkie funkcje roli na komputerze można znaleźć, przeszukując listę dostępnych modułów.

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
> Kolejność wyników z tej funkcji nie jest koniecznie kolejność, w którym zostanie wybrany możliwości roli, jeśli wiele możliwości roli o tej samej nazwie.

## <a name="check-effective-rights-for-a-specific-user"></a>Sprawdź obowiązujące prawa dla określonego użytkownika

Po skonfigurowaniu punktu końcowego JEA można sprawdzić, jakie polecenia są dostępne dla określonego użytkownika w ramach sesji usługi JEA.
Możesz użyć [Get PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) można wyliczyć wszystkie polecenia, które są stosowane do użytkownika, gdyby można uruchomić sesji JEA z ich bieżącego członkostwa w grupach.
Dane wyjściowe `Get-PSSessionCapability` jest taka sama jak w przypadku określonego użytkownika uruchamiającego `Get-Command -CommandType All` w ramach sesji usługi JEA.

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

Jeśli użytkownicy nie są stałe elementy członkowskie grup, które może przyznać im dodatkowe prawa JEA, to polecenie cmdlet może nie odzwierciedlać te dodatkowe uprawnienia.
Zazwyczaj jest to przypadek, korzystając z systemów zarządzania uprzywilejowany dostęp just in time umożliwiające użytkownikom tymczasowo należeć do grupy zabezpieczeń.
Zawsze należy wnikliwie zastanowić się, mapowanie użytkowników do ról i zawartość każdej roli, aby upewnić się, że użytkownicy otrzymują tylko dostęp do minimalnej liczbie polecenia są potrzebne do wykonywania ich zadań pomyślnie.

## <a name="powershell-event-logs"></a>Dzienniki zdarzeń programu PowerShell

Jeśli włączono modułu i/lub skrypt bloku rejestrowania w systemie można znaleźć zdarzenia w dzienniku zdarzeń Windows dla każdego polecenia, które użytkownik został uruchomiony w ich sesji usługi JEA.
Aby znaleźć te zdarzenia, otwórz Podgląd zdarzeń Windows, przejdź do **Microsoft-Windows-PowerShell/Operational** dziennika zdarzeń, a następnie sprawdź zdarzenia o identyfikatorze zdarzenia **4104**.

Każdy wpis dziennika zdarzeń będzie zawierać informacje o sesji, w którym zostało uruchomione polecenie.
Sesje usługi JEA to zawiera ważne informacje o **ConnectedUser**, czyli rzeczywisty użytkownik, który utworzył sesję JEA, jak również **nazwa_użytkownika** identyfikujący konto usługi JEA używane do Wykonaj polecenie.
Dzienniki zdarzeń aplikacji pokaże zmian wprowadzanych przez nazwa_użytkownika, więc o transkrypcji lub włączone rejestrowanie modułu/skrypt jest niezwykle istotne można było śledzić wywołanie określonego polecenia do użytkownika.

## <a name="application-event-logs"></a>Dzienniki zdarzeń aplikacji

Po uruchomieniu polecenia w sesji JEA, która wchodzi w interakcję z zewnętrznych aplikacji lub usługi te aplikacje mogą rejestrować zdarzenia własne dzienniki zdarzeń.
W przeciwieństwie do dzienników programu PowerShell i zapisy innych mechanizmów rejestrowania nie będzie przechwytywać połączonego użytkownika sesji JEA i będzie zamiast tego zalogować się wyłącznie wirtualnego użytkownika Uruchom jako i kont usług zarządzanych przez grupę.
Aby ustalić, który uruchomił polecenie, należy zapoznać się z [transkrypcji sesji](#session-transcripts) lub skorelowania dzienników zdarzeń programu PowerShell z czasem i użytkownika, przedstawione w dzienniku zdarzeń aplikacji.

WinRM dziennika może też pomóc skorelować Uruchom jako użytkownikom w dzienniku zdarzeń aplikacji użytkownik nawiązujący połączenie.
Identyfikator zdarzenia **193** w **Microsoft-Windows-Windows zdalnego zarządzania/Operational** rejestrowania rekordów identyfikator zabezpieczeń (SID) i konto nazwy użytkownik nawiązujący połączenie i jako użytkownika co czas wykonywania usługi JEA zostanie utworzona sesja.

## <a name="session-transcripts"></a>Zapisy sesji

Jeśli skonfigurowano JEA, aby utworzyć transkrypcję dla każdej sesji użytkownika kopię tekstu akcji każdego użytkownika będą przechowywane we wskazanym folderze.

Aby znaleźć wszystkie katalogi transkrypcji, uruchom następujące polecenie jako administrator na komputerze skonfigurowany przy użyciu technologii JEA:

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
```

Każdy transkrypcji rozpoczyna się od informacji o czasie rozpoczęcia sesji, który użytkownik podłączonego do sesji i tożsamość usługi JEA przypisano do nich.

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

W treści transkrypcję rejestrowane są informacje dotyczące każdego polecenia, które użytkownik wywołał.
Dokładna Składnia polecenia, które użytkownik uruchomi jest niedostępna w sesji JEA ze względu na sposób polecenia są przekształcane do komunikacji zdalnej programu PowerShell, ale nadal można określić skuteczne polecenia, który został wykonany.
Poniżej przedstawiono fragment transkrypcji przykład od użytkownika uruchamiania `Get-Service Dns` w ramach sesji usługi JEA:

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

Dla każdego polecenia, które użytkownik uruchamia wiersz "CommandInvocation" zostanie zapisany, zawierająca opis polecenia cmdlet lub użytkownika, wywoływana funkcja.
ParameterBindings postępuj zgodnie z każdym CommandInvocation informujące o każdego parametru i wartości, która została dostarczona z poleceniem.
W powyższym przykładzie widać, że parametr, który został "Name" podana wartość "Dns" dla polecenia cmdlet "Get-Usługa".

Dane wyjściowe każdego polecenia będzie również wyzwalać CommandInvocation zwykle wyjściowego domyślną.
InputObject Out-Default jest obiekt programu PowerShell, w zwróconym w poleceniu.
Szczegóły tego obiektu, wydrukowaniu kilka wierszy poniżej, ściśle naśladując, co użytkownik będzie mieć widoczne.

## <a name="see-also"></a>Zobacz też

- [*Program PowerShell ♥ zespołem niebieskim* wpis w blogu dotyczący zabezpieczeń](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)
