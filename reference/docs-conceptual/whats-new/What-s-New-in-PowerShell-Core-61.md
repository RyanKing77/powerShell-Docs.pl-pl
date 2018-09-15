---
title: Co nowego w programie PowerShell Core 6.1
description: Nowe funkcje i zmiany w programie PowerShell Core 6.1
ms.date: 09/13/2018
ms.openlocfilehash: b95b9dd504ea2a165a4689a3b28d2298644e5e68
ms.sourcegitcommit: aa41249f153bbc6e11667ade60c878980c15abc6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45611526"
---
# <a name="whats-new-in-powershell-core-61"></a>Co nowego w programie PowerShell Core 6.1

Poniżej przedstawiono niektóre główne nowe funkcje i zmiany, które zostały wprowadzone w programie PowerShell Core 6.1 wyboru.

Istnieje również **tonach** "nudnych dostępu", które ułatwiają programu PowerShell, szybsze i bardziej stabilne (plus partii i wiele poprawek)!
Aby uzyskać pełną listę zmian, zapoznaj się z naszym [dziennika zmian w witrynie GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).

I gdy czy powinniśmy zwołać kilka nazw poniżej, aby [wszystkie uczestnicy społeczności](https://github.com/PowerShell/PowerShell/graphs/contributors) , wprowadzonych w tej wersji możliwe.

## <a name="net-core-21"></a>.NET core 2.1

PowerShell Core 6.1 przeniesione do platformy .NET Core 2.1, po [wydane w maju](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), dając w efekcie w szereg ulepszeń w programie PowerShell, w tym:

- ulepszenia wydajności (zobacz [poniżej](#performance-improvements))
- Firma Alpine pomoc techniczna Linux support (wersja zapoznawcza)
- [Obsługa narzędzia globalnej platformy .NET](/dotnet/core/tools/global-tools) — najbliższych wkrótce do programu PowerShell
- [`Span<T>`](/dotnet/api/system.span-1?view=netcore-2.1)

## <a name="windows-compatibility-pack-for-net-core"></a>Windows Compatibility Pack dla programu .NET Core

W Windows, dostarczane przez zespół .NET [systemie Windows Compatibility Pack dla platformy .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), zbiór zestawów, które dodać szereg usunięte interfejsów API do platformy .NET Core w Windows.

Dodaliśmy pakiet Windows do wersji programu PowerShell Core 6.1, aby wszystkie moduły lub skrypty, które używają tych interfejsów API można polegać na nich dostępne.

Pakiet Windows umożliwia programu PowerShell Core do użycia **więcej niż 1900 poleceń cmdlet, które są dostarczane z systemem Windows 10 października 2018 Update i Windows Server 2019**.

## <a name="support-for-application-whitelisting"></a>Obsługa listy dozwolonych aplikacji

PowerShell Core 6.1 ma parzystości przy użyciu programu Windows PowerShell 5.1 obsługi [funkcji AppLocker](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) i [funkcji Device Guard](https://docs.microsoft.com/en-us/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) listy dozwolonych aplikacji.
Listy dozwolonych aplikacji umożliwia szczegółową kontrolę, z których plików binarnych mogą być wykonywane używany przy użyciu programu PowerShell [Tryb ograniczonego języka](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/).

## <a name="performance-improvements"></a>Ulepszenia wydajności

PowerShell Core 6.0 wprowadzone pewne znaczne ulepszenia wydajności.
PowerShell Core 6.1 w dalszym ciągu przyspieszyć niektóre operacje.

Na przykład `Group-Object` przyspieszyło o 66%:

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|              | Program Windows PowerShell 5.1 | Program PowerShell Core 6.0 | Program PowerShell Core 6.1 |
|--------------|------------------------|---------------------|---------------------|
| Czas (s)   | 25.178                 | 19.653              | 6.641               |
| Przyspiesz (%) | Brak                    | 21.9%               | 66.2%               |

Podobnie przez więcej niż 15% ulepszyła scenariusze sortowania podobny do poniższego:

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|              | Program Windows PowerShell 5.1 | Program PowerShell Core 6.0 | Program PowerShell Core 6.1 |
|--------------|------------------------|---------------------|---------------------|
| Czas (s)   | 12.170                 | 8.493               | 7.08                |
| Przyspiesz (%) | Brak                    | 30.2%               | 16.6%               |

`Import-Csv` ma również zostały przyspieszyło znacznie po regresji za pomocą programu Windows PowerShell.
W poniższym przykładzie użyto testu CSV z 26,616 wierszami i kolumnami sześć:

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|              | Program Windows PowerShell 5.1 | Program PowerShell Core 6.0 | Program PowerShell Core 6.1    |
|--------------|------------------------|---------------------|------------------------|
| Czas (s)   | 0.441                  | 1.069               | 0.268                  |
| Przyspiesz (%) | Brak                    | -142.4%             | 74.9% (% 39.2 z WPS) |

Na koniec konwersji z formatu JSON do `PSObject` ma zostały przyspieszyło przez więcej niż 50% od środowiska Windows PowerShell.
W poniższym przykładzie użyto pliku JSON testu ~ 2MB:

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|              | Program Windows PowerShell 5.1 | Program PowerShell Core 6.0 | Program PowerShell Core 6.1    |
|--------------|------------------------|---------------------|------------------------|
| Czas (s)   | 0.259                  | 0.577               | 0,125                  |
| Przyspiesz (%) | Brak                    | -122.8%             | 78.3% (% 51.7 z WPS) |

## <a name="check-system32-for-compatible-inbox-modules-on-windows"></a>Sprawdź `system32` dla modułów zgodne skrzynki odbiorczej w Windows

W Windows Server 2019 i aktualizacji systemu Windows 10 1809 Zaktualizowaliśmy liczbę modułów programu PowerShell skrzynki odbiorczej, aby oznaczyć je jako niezgodne z programu PowerShell Core.

Podczas uruchamiania programu PowerShell Core 6.1, automatycznie zostanie dołączony `$windir\System32` jako część `PSModulePath` zmiennej środowiskowej.
Jednak tylko udostępnia ona moduły `Get-Module` i `Import-Module` jeśli jego `CompatiblePSEdition` jest oznaczona jako zgodna z `Core`.


```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> Może zostać wyświetlony różnych dostępnych modułów, w zależności od tego, jakie role i funkcje są zainstalowane.

```Output
...
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, Get-AppxPackage, Get-AppxPacka...
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, Suspend-BitLocker, Resume-Bit...
Manifest   1.0.0.0    DnsClient                           Core,Desk {Resolve-DnsName, Clear-DnsClientCache, Get-DnsC...
Manifest   1.0.0.0    HgsDiagnostics                      Core,Desk {New-HgsTraceTarget, Get-HgsTrace, Get-HgsTraceF...
Binary     2.0.0.0    Hyper-V                             Core,Desk {Add-VMAssignableDevice, Add-VMDvdDrive, Add-VMF...
Binary     1.1        Hyper-V                             Core,Desk {Add-VMDvdDrive, Add-VMFibreChannelHba, Add-VMHa...
Manifest   2.0.0.0    NetAdapter                          Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetEventPacketCapture               Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                             Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                              Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                              Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                         Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam                       Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetWNV                              Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   2.0.0.0    TrustedPlatformModule               Core,Desk {Get-Tpm, Initialize-Tpm, Clear-Tpm, Unblock-Tpm...
...
```

Można zastąpić to zachowanie, aby pokazać wszystkie moduły przy użyciu `-SkipEditionCheck` parametr przełącznika.
Dodaliśmy także `PSEdition` właściwości do danych wyjściowych tabeli.

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Desk      {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Desk      {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Desk      {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Desk      {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Desk      {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

Aby uzyskać więcej informacji na temat tego zachowania, zapoznaj się z [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).

## <a name="markdown-cmdlets-and-rendering"></a>Polecenia cmdlet języka znaczników markdown i renderowanie

Markdown to standardowe rozwiązanie dla tworzenia dokumentów zwykłego podstawowe formatowanie może być renderowany w kodzie HTML.

Dodaliśmy niektórych poleceń cmdlet w 6.1, pozwalających konwersji i renderowania dokumentów języka znaczników Markdown w konsoli, w tym:

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

Na przykład `Show-Markdown` renderuje plik języka znaczników Markdown, w konsoli:

![Przykład kodu Markdown show](./images/markdown_example.png)

Aby uzyskać więcej informacji na temat działania tych poleceń cmdlet zapoznaj się z [tej specyfikacji RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).

## <a name="experimental-feature-flags"></a>Flagi funkcji eksperymentalnych

Flagi funkcji eksperymentalnych pozwalają użytkownikom na włączanie funkcji, które jeszcze nie został sfinalizowany.
Funkcje eksperymentalne nie są obsługiwane i mogą mieć usterek.

Dowiedz się więcej na temat tej funkcji w [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).

## <a name="web-cmdlet-improvements"></a>Ulepszenia dotyczące polecenia cmdlet w sieci Web

Dzięki @markekraus, całe slew ulepszeń zostały wprowadzone do naszych poleceń cmdlet w sieci web: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)
i [ `Invoke-RestMethod` ](/powershell/module/microsoft.powershell.utility/invoke-restmethod).

- [6109 # żądania Ściągnięcia](https://github.com/PowerShell/PowerShell/pull/6109) — domyślny zestaw kodowania na UTF-8 dla `application-json` odpowiedzi
- [Żądania Ściągnięcia #6018](https://github.com/PowerShell/PowerShell/pull/6018)  -  `-SkipHeaderValidation` parametru, aby umożliwić `Content-Type` nagłówki, które nie są zgodne z normami
- [Żądania Ściągnięcia #5972](https://github.com/PowerShell/PowerShell/pull/5972)  -  `Form` uproszczony parametr w celu obsługi `multipart/form-data` pomocy technicznej
- [Żądania Ściągnięcia #6338](https://github.com/PowerShell/PowerShell/pull/6338) — zgodne, bez uwzględniania wielkości liter Obsługa kluczy relacji
- [Żądania Ściągnięcia #6447](https://github.com/PowerShell/PowerShell/pull/6447) — Dodaj `-Resume` parametr dla polecenia cmdlet sieci web

## <a name="remoting-improvements"></a>Ulepszenia usług zdalnych

### <a name="powershell-direct-tries-to-use-powershell-core-first"></a>Bezpośrednie PowerShell spróbuje najpierw użyć programu PowerShell Core

[Bezpośrednie PowerShell](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) jest funkcją programu PowerShell i funkcji Hyper-V, która umożliwia łączenie z maszyną Wirtualną funkcji Hyper-V, bez łączności sieciowej lub innych usług zarządzania zdalnego.

W przeszłości połączone bezpośrednio z programu PowerShell jest używane wystąpienie skrzynki odbiorczej programu Windows PowerShell na maszynie Wirtualnej.
Teraz, programu PowerShell Direct najpierw próbuje nawiązać połączenie przy użyciu wszystkie dostępne `pwsh.exe` na `PATH` zmiennej środowiskowej.
Jeśli `pwsh.exe` nie jest dostępna, programu PowerShell Direct powraca do użycia `powershell.exe`.

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a>`Enable-PSRemoting` utworzy teraz punkty końcowe komunikacji zdalnej w oddzielnych wersji zapoznawczych

`Enable-PSRemoting` teraz tworzy dwie konfiguracje sesji komunikacji zdalnej:

- Jeden dla wersji głównej programu PowerShell. Na przykład`PowerShell.6`. Ten punkt końcowy, które mogą być powoływane między aktualizacjami wersji pomocniczej konfiguracji sesji programu PowerShell 6 "systemowe"
- Jedna konfiguracja sesji specyficzny dla wersji, na przykład: `PowerShell.6.1.0`

To zachowanie jest przydatne, jeśli chcesz mieć wiele wersji programu PowerShell 6 zainstalowana i jest dostępna na tym samym komputerze.

Ponadto wersji zapoznawczych programu PowerShell teraz uzyskać własnych usług zdalnych konfiguracjami sesji po uruchomieniu `Enable-PSRemoting` polecenia cmdlet:

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

Dane wyjściowe mogą się różnić, jeśli nie skonfigurowano usługi WinRM przed.

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

Następnie możesz zobaczyć oddzielne konfiguracje sesji programu PowerShell w wersji zapoznawczej i stabilny kompilacje z programu PowerShell 6 i dla każdej określonej wersji.

```powershell
Get-PSSessionConfiguration
```

```Output
Name          : PowerShell.6.2-preview.1
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6-preview
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6.1.0
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

### <a name="userhostport-syntax-supported-for-ssh"></a>`user@host:port` Składnia obsługiwanych przez protokół SSH

SSH klientów zwykle obsługują parametry połączenia w formacie `user@host:port`.
Z dodatkiem SSH jako protokół dla niego komunikacji zdalnej programu PowerShell Dodaliśmy obsługę tego formatu ciągu połączenia:

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a>Opcja MSI można dodać menu kontekstowego powłoki Eksploratora Windows

Dzięki @bergmeister, teraz można włączyć menu kontekstowego na Windows. Teraz można otworzyć instalacja systemowe 6.1 programu PowerShell z dowolnego folderu w Eksploratorze Windows:

![Menu kontekstowe powłoki PowerShell 6](./images/shell_context_menu.png)

## <a name="goodies"></a>Dodatki

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a>"Uruchom jako Administrator", w skrócie Windows przejdź do listy

Dzięki @bergmeister, listy szybkiego dostępu skrótu programu PowerShell Core zawiera teraz "Uruchom jako Administrator":

![Uruchom jako administrator program PowerShell 6 listy szybkiego dostępu](./images/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a>`cd -` Powrót do poprzedniego katalogu

```powershell
C:\Windows\System32> cd C:\
C:\> cd -
C:\Windows\System32>
```

Lub w systemie Linux:

```ShellSession
PS /etc> cd /usr/bin
PS /usr/bin> cd -
PS /etc>
```

Ponadto `cd --` zmieni się na `$HOME`.

### `Test-Connection`

Dzięki @iSazonov, [ `Test-Connection` ](/powershell/module/microsoft.powershell.management/test-connection) ma wydajnej polecenia cmdlet programu PowerShell Core.

### <a name="update-help-as-non-admin"></a>`Update-Help` jako bez uprawnień administratora

Popularne popytem `Update-Help` nie musi już być uruchomiony z uprawnieniami administratora.
`Update-Help` teraz domyślnie zapisywania pomocy do folderu o określonym zakresie użytkownika.

### <a name="new-methodsproperties-on-pscustomobject"></a>Nowe metody/właściwości na `PSCustomObject`

Dzięki @iSazonov, dodaliśmy nowe metody i właściwości w celu `PSCustomObject`.
`PSCustomObject` zawiera teraz `Count` / `Length` właściwość, która podaje liczbę elementów.

Oba te przykłady zwracają `2` jako liczba `PSCustomObjects` w kolekcji.

```powershell
@(
[pscustomobject]@{foo = '1'},
[pscustomobject]@{bar = '2' }).Length
```

```powershell
@(
[pscustomobject]@{foo = '1'},
[pscustomobject]@{bar = '2' }).Count
```

Praca ta obejmuje również `ForEach` i `Where` metody, które umożliwiają działanie i przefiltruj `PSCustomObject` elementy:

```powershell
@(
>> [pscustomobject]@{foo = 1},
>> [pscustomobject]@{foo = 2 }).ForEach({$_.foo+1})
```

```Output
2
3
```

```powershell
@(
>> [pscustomobject]@{foo = 1},
>> [pscustomobject]@{foo = 2 }).Where({$_.foo -gt 1})
```

```Output
foo
---
  2
```

### `Where-Object -Not`

Dzięki @SimonWahlin, dodaliśmy `-Not` parametr `Where-Object`.
Teraz można filtrować obiekt w potoku, który nie istnieje właściwość lub wartość właściwości o wartości null lub być pusty.

Na przykład to polecenie zwraca wszystkie usługi, które nie mają zdefiniowanych żadnych usług zależnych:

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a>`New-ModuleManifest` Tworzy dokument bez BOM UTF-8

Zaktualizowaliśmy udzielone naszego przejścia bez BOM UTF-8 w programie PowerShell w wersji 6.0, `New-ModuleManifest` polecenia cmdlet, aby utworzyć dokument bez BOM UTF-8 zamiast UTF-16, jeden.

### <a name="conversions-from-psmethod-to-delegate"></a>Konwersje z PSMethod delegata

Dzięki @powercode, zapewniamy obecnie obsługę konwersji `PSMethod` do delegata.
Dzięki temu można wykonywać następujące czynności przekazywanie `PSMethod` `[M]::DoubleStrLen` jako wartość delegata do `[M]::AggregateString`:

```powershell
class M {
    static [int] DoubleStrLen([string] $value) { return 2 * $value.Length }

    static [long] AggregateString([string[]] $values, [func[string, int]] $selector) {
        [long] $res = 0
        foreach($s in $values){
            $res += $selector.Invoke($s)
        }
        return $res
    }
}

[M]::AggregateString((gci).Name, [M]::DoubleStrLen)
```

Aby uzyskać więcej informacji na temat tej zmiany, zapoznaj się z [5287 # żądania Ściągnięcia](https://github.com/PowerShell/PowerShell/pull/5287).

### <a name="standard-deviation-in-measure-object"></a>Odchylenie standardowe `Measure-Object`

Dzięki @CloudyDino, dodaliśmy `StandardDeviation` właściwości `Measure-Object`:

```powershell
Get-Process | Measure-Object -Property CPU -AllStats
```

```Output
Count             : 308
Average           : 31.3720576298701
Sum               : 9662.59375
Maximum           : 4416.046875
Minimum           :
StandardDeviation : 264.389544720926
Property          : CPU
```

### `GetPfxCertificate -Password`

Dzięki @maybe-hello-world, `Get-PfxCertificate` ma teraz `Password` parametr, który przyjmuje `SecureString`. Dzięki temu można używać go w trybie nieinteraktywnym:

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a>Usuwanie `more` — funkcja

W przeszłości, programu PowerShell dostarczanych funkcja na Windows o nazwie `more` który opakowany `more.com`.
Ta funkcja została usunięta.

Również `help` zmienione, aby używać funkcji `more.com` Windows lub systemu domyślne pagera, określony przez `$env:PAGER` na platformach innych niż Windows.

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a>`cd DriveName:` teraz zwraca użytkowników do bieżącego katalogu roboczego na tym dysku

Wcześniej przy użyciu `Set-Location` lub `cd` aby powrócić do PSDrive, wysyłane użytkowników do domyślnej lokalizacji dla tego dysku.

Dzięki @mcbobke, użytkownicy są teraz wysyłane do ostatniej znanej bieżący katalog roboczy dla tej sesji.

### <a name="windows-powershell-type-accelerators"></a>Akceleratory typu środowiska Windows PowerShell

W programie Windows PowerShell dodaliśmy następujące akceleratorów typu w celu ułatwienia pracy z ich odpowiednich typów:

- `[adsi]`: `System.DirectoryServices.DirectoryEntry`
- `[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`
- `[wmi]`: `System.Management.ManagementObject`
- `[wmiclass]`: `System.Management.ManagementClass`
- `[wmisearcher]`: `System.Management.ManagementObjectSearcher`

Te skróty klawiaturowe typu nie zostały uwzględnione w programie PowerShell 6, ale zostały dodane do 6.1 programu PowerShell w systemie Windows.

Te typy są przydatne w prosty sposób tworzenia usługi AD i obiektów WMI.

Można na przykład zapytania przy użyciu protokołu LDAP:

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

Obu tych przykładach Utwórz obiekt Win32_OperatingSystem CIM:

```powershell
[wmi]"win32_operatingsystem=@"
[wmiclass]"win32_operatingsystem"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a>`-lp` alias dla wszystkich `-LiteralPath` parametrów

Dzięki @kvprasoon, mamy teraz aliasu parametru `-lp` dla wszystkich wbudowanych poleceń cmdlet programu PowerShell, które mają `-LiteralPath` parametru.

## <a name="breaking-changes"></a>Fundamentalne zmiany

### <a name="msi-based-installation-paths-on-windows"></a>Instalacja wykonywana przy użyciu pliku MSI ścieżek na Windows

Na Windows pakiet MSI instaluje teraz w następującej ścieżce:

- `$env:ProgramFiles\PowerShell\6\` stabilna instalacji w wersji 6.x
- `$env:ProgramFiles\PowerShell\6-preview\` dla instalacji w wersji 6.x (wersja zapoznawcza)

Ta zmiana zapewnia program PowerShell Core można zaktualizować/obsługiwanych przez usługi Microsoft Update.

Aby uzyskać więcej informacji, zapoznaj się z [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a>Telemetrię można wyłączyć tylko za pomocą zmiennej środowiskowej

Program PowerShell Core wysyła dane telemetryczne podstawowe do firmy Microsoft, po jego uruchomieniu. Dane obejmują nazwę systemu operacyjnego, wersji systemu operacyjnego i wersji programu PowerShell. Te dane, pozwala lepiej zrozumieć środowisk, w których program PowerShell jest używany i pozwala nam określić priorytety nowe funkcje i poprawki.

Aby zrezygnować z tych danych telemetrycznych, ustaw zmienną środowiskową `POWERSHELL_TELEMETRY_OPTOUT` do `true`, `yes`, lub `1`. Nie obsługujemy już usunięcia pliku `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` można wyłączyć na telemetrię.

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a>Niedozwolone uwierzytelniania podstawowego, za pośrednictwem protokołu HTTP w komunikacji zdalnej programu PowerShell na platformach Unix

Aby uniknąć użycia nieszyfrowanego ruchu, komunikacji zdalnej programu PowerShell na platformach Unix wymaga użycia uwierzytelniania NTLM/Negotiate lub HTTPS.

Aby uzyskać więcej informacji na temat tych zmian, zapoznaj się z [6799 # żądania Ściągnięcia](https://github.com/PowerShell/PowerShell/pull/6799).

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a>Usunięte `VisualBasic` jako obsługiwanego języka w Add-Type

W przeszłości można skompilować przy użyciu kodu języka Visual Basic `Add-Type` polecenia cmdlet.
Rzadko używany Visual Basic z `Add-Type`. Firma Microsoft usunęła tę funkcję, aby zmniejszyć rozmiar środowiska PowerShell.

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a>Wyczyszczone zastosowań `CommandTypes.Workflow` i `WorkflowInfoCleaned`

Aby uzyskać więcej informacji na temat tych zmian, zapoznaj się z [6708 # żądania Ściągnięcia](https://github.com/PowerShell/PowerShell/pull/6708).
