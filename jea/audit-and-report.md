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
# <a name="auditing-and-reporting-on-jea"></a>Inspekcja i raporty dotyczące technologii JEA

Po wdrożeniu usługi JEA, należy regularnie inspekcji konfiguracji JEA. Inspekcja pomaga ocenić czy poprawny osoby mają dostęp do punktu końcowego JEA i ich przypisane role są nadal odpowiednie.

## <a name="find-registered-jea-sessions-on-a-machine"></a>Znajdź zarejestrowany technologii JEA sesji na komputerze

Aby sprawdzić, które sesje JEA są rejestrowane na komputerze, użyj [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) polecenia cmdlet.

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

Obowiązujące prawa dla punktu końcowego są wymienione w **uprawnienie** właściwości. Tacy użytkownicy mają prawo do nawiązywania połączenia punktu końcowego JEA. Jednak role i mają dostęp do poleceń jest określana przez **RoleDefinitions** właściwość [plik konfiguracji sesji](session-configurations.md) który został użyty do zarejestrowania punktu końcowego. Rozwiń **RoleDefinitions** właściwości do oceny mapowań ról w punkcie końcowym programu zarejestrowany technologii JEA.

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a>Znajdowanie możliwości roli dostępne na komputerze

JEA pobiera możliwości roli z `.psrc` plików przechowywanych w **RoleCapabilities** folder wewnątrz modułu programu PowerShell. Poniższa funkcja znajduje wszystkie funkcje roli na komputerze.

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
> Kolejność wyników z tej funkcji nie jest koniecznie kolejność, w którym zostanie wybrany możliwości roli, jeśli wiele możliwości roli o tej samej nazwie.

## <a name="check-effective-rights-for-a-specific-user"></a>Sprawdź obowiązujące prawa dla określonego użytkownika

[Get PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) polecenia cmdlet wylicza wszystkich poleceń dostępnych w punkcie końcowym usługi JEA oparte na członkostwie grupy użytkownika.
Dane wyjściowe `Get-PSSessionCapability` jest taka sama jak w przypadku określonego użytkownika uruchamiającego `Get-Command -CommandType All` w ramach sesji usługi JEA.

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

Jeśli użytkownicy nie są stałe elementy członkowskie grup, które może przyznać im dodatkowe prawa JEA, to polecenie cmdlet może nie odzwierciedlać te dodatkowe uprawnienia. Dzieje się po użyciu just-in-time uprzywilejowanego dostępu do systemów zarządzania, aby umożliwić użytkownikom tymczasowo należeć do grupy zabezpieczeń. Należy wnikliwie zastanowić się mapowanie użytkowników do ról i funkcji, aby upewnić się, że użytkownicy pobierają tylko poziom dostępu wymagane do wykonywania ich zadań pomyślnie.

## <a name="powershell-event-logs"></a>Dzienniki zdarzeń programu PowerShell

Jeśli został włączony moduł lub skrypt bloku rejestrowania w systemie, zostanie wyświetlony zdarzeń w dzienniku zdarzeń Windows dla każdego polecenia, które użytkownik, który jest uruchamiany w ramach sesji usługi JEA. Aby znaleźć te zdarzenia, otwórz **Microsoft-Windows-PowerShell/Operational** dziennika zdarzeń i wyszukać zdarzenia o identyfikatorze zdarzenia **4104**.

Każdy wpis dziennika zdarzeń zawiera informacje o sesji, w którym zostało uruchomione polecenie. Sesje usługi JEA zdarzenia zawiera informacje o **ConnectedUser** i **nazwa_użytkownika**. **ConnectedUser** jest rzeczywisty użytkownik, który utworzył sesję JEA. **Nazwa_użytkownika** to konto usługi JEA służącego do wykonania polecenia.

Dzienniki zdarzeń aplikacji Pokaż zmian wprowadzanych przez **nazwa_użytkownika**. Dlatego moduł i włączone rejestrowanie skryptu jest wymagane do śledzenia z powrotem do wywołania określonego polecenia **ConnectedUser**.

## <a name="application-event-logs"></a>Dzienniki zdarzeń aplikacji

Polecenia są uruchamiane w sesji JEA, która wchodzić w interakcje z aplikacjami zewnętrznymi lub usługi mogą rejestrować zdarzenia do ich własnych dzienników zdarzeń. W przeciwieństwie do dzienników programu PowerShell i zapisy innych mechanizmów rejestrowania nie należy przechwytywać połączonego użytkownika sesji JEA. Zamiast tego te aplikacje dziennika wirtualnego użytkownika Uruchom jako.
Aby ustalić, który uruchomił polecenie, należy zapoznać się [transkrypcji sesji](#session-transcripts) lub skorelowania dzienników zdarzeń programu PowerShell z czasem i użytkownika, przedstawione w dzienniku zdarzeń aplikacji.

Dziennik usługi WinRM można również ułatwić skorelować użytkowników Uruchom jako użytkownik nawiązujący połączenie z dziennika zdarzeń aplikacji. Identyfikator zdarzenia **193** w **Microsoft-Windows-Windows zdalnego zarządzania/Operational** dziennika rejestruje identyfikator zabezpieczeń (SID) i nazwa konta zarówno dla połączenia użytkownika i Uruchom jako użytkownik dla każdej nowej usługi JEA sesji.

## <a name="session-transcripts"></a>Zapisy sesji

Jeśli skonfigurowano JEA, aby utworzyć transkrypcję dla każdej sesji użytkownika kopię tekstu działania każdego z użytkowników są przechowywane we wskazanym folderze.

Następujące polecenie (jako administrator) umożliwia znalezienie wszystkich katalogów transkrypcji.

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
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

Treść tej transkrypcji zawiera informacje o każdym poleceniu użytkownik wywołał. Dokładna Składnia polecenia używane jest niedostępna w sesji JEA ze względu na sposób, w jaki polecenia są przekształcane do komunikacji zdalnej programu PowerShell. Można jednak nadal określić skuteczne polecenia, który został wykonany. Poniżej przedstawiono fragment transkrypcji przykład od użytkownika uruchamiania `Get-Service Dns` w ramach sesji usługi JEA:

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

A **CommandInvocation** wiersz jest przeznaczony dla każdego polecenia, gdy użytkownik uruchamia. **ParameterBindings** zarejestrować każdy parametr i wartość dostarczona z poleceniem. W poprzednim przykładzie możesz zobaczyć, że parametr **nazwa** została podana z wartością **Dns** dla `Get-Service` polecenia cmdlet.

Dane wyjściowe każdego polecenia także wyzwalacze **CommandInvocation**, zwykle `Out-Default`. **InputObject** z `Out-Default` polecenie zostanie zwrócony obiekt programu PowerShell. Szczegóły tego obiektu, wydrukowaniu kilka wierszy poniżej, ściśle naśladując, co użytkownik będzie mieć widoczne.

## <a name="see-also"></a>Zobacz też

[*Program PowerShell ♥ zespołem niebieskim* wpis w blogu dotyczący zabezpieczeń](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
