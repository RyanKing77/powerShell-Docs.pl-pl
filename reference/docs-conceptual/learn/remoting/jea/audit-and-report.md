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
# <a name="auditing-and-reporting-on-jea"></a>Inspekcja i raportowanie w usłudze JEA

Po wdrożeniu JEA należy regularnie przeprowadzać inspekcję konfiguracji JEA. Inspekcja pomaga ocenić, że poprawne osoby mają dostęp do punktu końcowego JEA, a przypisane do nich role nadal są odpowiednie.

## <a name="find-registered-jea-sessions-on-a-machine"></a>Znajdowanie zarejestrowanych sesji JEA na maszynie

Aby sprawdzić, które sesje JEA są zarejestrowane na komputerze, użyj polecenia cmdlet [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) .

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

Obowiązujące prawa dla punktu końcowego są wymienione we właściwości **uprawnienia** . Ci użytkownicy mają prawo do nawiązywania połączenia z punktem końcowym JEA. Jednak role i polecenia, do których mają dostęp, są określane przez właściwość **RoleDefinitions** w [pliku konfiguracji sesji](session-configurations.md) , który został użyty do zarejestrowania punktu końcowego. Rozwiń Właściwość **RoleDefinitions** , aby oszacować mapowania ról w zarejestrowanym punkcie końcowym jea.

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a>Znajdź dostępne możliwości roli na komputerze

JEA pobiera możliwości roli z `.psrc` plików przechowywanych w folderze **RoleCapabilities** w module programu PowerShell. Poniższa funkcja znajduje wszystkie możliwości roli dostępne na komputerze.

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
> Kolejność wyników z tej funkcji nie musi być kolejnością, w której można wybrać możliwości roli, jeśli wiele możliwości roli ma taką samą nazwę.

## <a name="check-effective-rights-for-a-specific-user"></a>Sprawdź czynne prawa dla określonego użytkownika

Polecenie cmdlet [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) wylicza wszystkie polecenia dostępne w punkcie KOŃCOWYm jea w oparciu o członkostwo w grupach użytkowników.
Dane wyjściowe `Get-PSSessionCapability` są identyczne z określonym użytkownikiem uruchomionym `Get-Command -CommandType All` w sesji jea.

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

Jeśli użytkownicy nie są stałymi członkami grup, które przyznają im dodatkowe prawa JEA, to polecenie cmdlet może nie odzwierciedlać tych dodatkowych uprawnień. Dzieje się tak w przypadku korzystania z systemów dostępu uprzywilejowanego "just in Time" w celu umożliwienia użytkownikom tymczasowego należeć do grupy zabezpieczeń. Należy dokładnie oszacować Mapowanie użytkowników do ról i możliwości, aby zapewnić, że użytkownicy będą mieli tylko poziom dostępu wymagany do pomyślnego wykonania zadań.

## <a name="powershell-event-logs"></a>Dzienniki zdarzeń programu PowerShell

Jeśli włączono rejestrowanie bloków modułu lub skryptu w systemie, można zobaczyć zdarzenia w dziennikach zdarzeń systemu Windows dla każdego polecenia uruchamianego przez użytkownika w sesji JEA. Aby znaleźć te zdarzenia, Otwórz dziennik zdarzeń **Microsoft-Windows-PowerShell/operacyjnego** i Wyszukaj zdarzenia o identyfikatorze **4104**.

Każdy wpis dziennika zdarzeń zawiera informacje o sesji, w której uruchomiono polecenie. W przypadku sesji JEA zdarzenie obejmuje informacje o **ConnectedUser** i **RunAsUser**. **ConnectedUser** jest bieżącym użytkownikiem, który UTWORZYŁ sesję jea. **RunAsUser** jest kontem jea używanym do wykonywania polecenia.

Dzienniki zdarzeń aplikacji pokazują zmiany wprowadzane przez **RunAsUser**. W celu śledzenia określonego wywołania polecenia z powrotem do **ConnectedUser**wymagane jest włączenie rejestrowania modułu i skryptu.

## <a name="application-event-logs"></a>Dzienniki zdarzeń aplikacji

Polecenia uruchamiane w sesji JEA, które współdziałają z zewnętrznymi aplikacjami lub usługami, mogą rejestrować zdarzenia do własnych dzienników zdarzeń. W przeciwieństwie do dzienników i transkrypcji programu PowerShell, inne mechanizmy rejestrowania nie przechwytuje połączonego użytkownika sesji JEA. Zamiast tego aplikacje te rejestrują tylko wirtualnego użytkownika "Uruchom jako".
Aby określić, kto uruchomił polecenie, należy zapoznać się z [transkrypcją sesji](#session-transcripts) lub skorelować dzienników zdarzeń programu PowerShell z czasem i użytkownikiem wyświetlanym w dzienniku zdarzeń aplikacji.

Dziennik usługi WinRM może również pomóc w skorelowaniu użytkowników z połączeniem Uruchom jako z zalogowanym użytkownikiem w dzienniku zdarzeń aplikacji. Identyfikator zdarzenia **193** w dzienniku **systemu Microsoft Windows-Windows Remote Management/operacyjnego** REJESTRUJE identyfikator zabezpieczeń (SID) i nazwę konta dla użytkownika łączącego i Uruchom jako dla każdej nowej sesji jea.

## <a name="session-transcripts"></a>Transkrypcje sesji

Jeśli skonfigurowano JEA do tworzenia transkrypcji dla każdej sesji użytkownika, kopia tekstowa akcji każdego użytkownika jest przechowywana w określonym folderze.

Następujące polecenie (jako administrator) znajduje wszystkie katalogi transkrypcji.

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
```

Każdy transkrypcja rozpoczyna się od informacji o czasie uruchomienia sesji, który użytkownik połączył się z sesją oraz do której przypisano tożsamość JEA.

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

Treść transkrypcji zawiera informacje o każdym z poleceń wywoływanych przez użytkownika. Dokładna składnia użytego polecenia jest niedostępna w sesjach JEA ze względu na sposób przekształcania poleceń na potrzeby komunikacji zdalnej programu PowerShell. Można jednak nadal określić efektywne polecenie, które zostało wykonane. Poniżej znajduje się przykładowy fragment kodu dotyczący użytkownika działającego `Get-Service Dns` w sesji jea:

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

Wiersz **CommandInvocation** jest zapisywana dla każdego polecenia uruchomionego przez użytkownika. **ParameterBindings** rejestruje każdy parametr i wartość dostarczoną z poleceniem. W poprzednim przykładzie można zobaczyć, że **Nazwa** parametru została podana wartość **DNS** dla `Get-Service` polecenia cmdlet.

Dane wyjściowe każdego polecenia wyzwalają także **CommandInvocation**, zwykle do `Out-Default`. **Inputobject** of `Out-Default` to obiekt programu PowerShell zwrócony z polecenia. Poniżej znajdują się szczegółowe informacje o tym obiekcie, które są widoczne poniżej. dokładnie naśladując się, co widzi użytkownik.

## <a name="see-also"></a>Zobacz też

[*Program PowerShell ♥ niebieskiego* wpisu w blogu zespołu na stronie zabezpieczenia](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
