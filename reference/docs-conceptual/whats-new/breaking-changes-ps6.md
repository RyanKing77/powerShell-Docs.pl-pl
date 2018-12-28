---
ms.date: 05/17/2018
keywords: Program PowerShell, core
title: Istotne zmiany dotyczące programu PowerShell w wersji 6.0
ms.openlocfilehash: d477a9b27e8d5df6653ee40f8b606879b60a80c7
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655450"
---
# <a name="breaking-changes-for-powershell-60"></a>Istotne zmiany dotyczące programu PowerShell w wersji 6.0

## <a name="features-no-longer-available-in-powershell-core"></a>Funkcje nie będą już dostępne w programie PowerShell Core

### <a name="powershell-workflow"></a>Przepływ pracy programu PowerShell

[Przepływ pracy programu PowerShell] [ workflow] to funkcja w programie Windows PowerShell, który tworzy w górnej części [Windows Workflow Foundation (WF)] [ workflow-foundation] umożliwiającej tworzenie niezawodne elementów runbook dla zadań długotrwałych lub równoległego.

Ze względu na brak obsługi Windows Workflow Foundation w programie .NET Core firma Microsoft nie będzie obsługiwać przepływu pracy programu PowerShell w programie PowerShell Core.

W przyszłości prosimy o poświęcenie włączyć równoległość/współbieżności natywne w języku programu PowerShell, bez konieczności stosowania przepływu pracy programu PowerShell.

[workflow]: https://docs.microsoft.com/powershell/scripting/core-powershell/workflows-guide
[workflow-foundation]: https://docs.microsoft.com/dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a>Niestandardowe przystawek

[Przystawki programu PowerShell] [ snapin] są poprzednika modułów programu PowerShell, które nie mają je w społeczności programu PowerShell.

Ze względu na złożoność obsługi przystawki i ich braku użycie w społeczności nie jest już obsługiwana w programie PowerShell Core niestandardowe przystawek.

Już dziś, spowoduje to podzielenie `ActiveDirectory` i `DnsClient` moduły Windows i systemu Windows Server.

[snapin]: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a>Polecenia cmdlet usługi WMI w wersji 1

Ze względu na złożoność obsługi dwóch zestawów modułów usługi WMI firma Microsoft usunęła poleceń cmdlet w wersji 1 usługi WMI z programu PowerShell Core:

- `Get-WmiObject`
- `Invoke-WmiMethod`
- `Register-WmiEvent`
- `Set-WmiInstance`

Zamiast tego zaleca się, że użytkownik, użyj polecenia cmdlet CIM (zwane również WMI w wersji 2), które zawierają te same funkcje za pomocą nowych funkcji i przeprojektowana składni:

- `Get-CimAssociatedInstance`
- `Get-CimClass`
- `Get-CimInstance`
- `Get-CimSession`
- `Invoke-CimMethod`
- `New-CimInstance`
- `New-CimSession`
- `New-CimSessionOption`
- `Register-CimIndicationEvent`
- `Remove-CimInstance`
- `Remove-CimSession`
- `Set-CimInstance`

### <a name="microsoftpowershelllocalaccounts"></a>Microsoft.PowerShell.LocalAccounts

Ze względu na użycie nieobsługiwanego interfejsów API `Microsoft.PowerShell.LocalAccounts` została usunięta z programu PowerShell Core aż do znalezienia lepszym rozwiązaniem.

### <a name="-counter-cmdlets"></a>Polecenia cmdlet środowiska `*-Counter`

Ze względu na użycie nieobsługiwanego interfejsów API `*-Counter` została usunięta z programu PowerShell Core aż do znalezienia lepszym rozwiązaniem.

## <a name="enginelanguage-changes"></a>Aparat/języka ustawionego zmiany

### <a name="rename-powershellexe-to-pwshexe-5101httpsgithubcompowershellpowershellissues5101"></a>Zmień nazwę `powershell.exe` do `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)

Aby udostępnić użytkownikom w sposób deterministyczny może wywołać program PowerShell Core Windows (w przeciwieństwie do programu Windows PowerShell), plik binarny programu PowerShell Core została zmieniona na `pwsh.exe` na Windows i `pwsh` na platformach innych niż Windows.

Skrócona nazwa jest również zgodne z nazewnictwem powłoki na platformach innych niż Windows.

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193httpsgithubcompowershellpowershellissues5193"></a>Nie wstawiaj podziały wierszy w danych wyjściowych (z wyjątkiem tabele) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)

Wcześniej dane wyjściowe był wyrównany do szerokość konsoli i podziały wierszy zostały dodane w szerokość końcowa konsoli, co oznacza, że dane wyjściowe nie uzyskać ponownie sformatowany zgodnie z oczekiwaniami, jeśli terminalu został zmieniony. Ta zmiana nie została zastosowana do tabel, podziały wiersza jest potrzebnych do zachowania kolumny wyrównane.

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432httpsgithubcompowershellpowershellissues5432"></a>Pomiń sprawdzanie elementu o wartości null w przypadku kolekcji z wartości typu elementu [#5432](https://github.com/PowerShell/PowerShell/issues/5432)

Dla `Mandatory` parametru i `ValidateNotNull` i `ValidateNotNullOrEmpty` atrybutów, Pomiń sprawdzanie elementu o wartości null, jeśli typ elementu kolekcji jest typem wartości.

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369httpsgithubcompowershellpowershellissues5369"></a>Zmiana `$OutputEncoding` używać `UTF-8 NoBOM` kodowanie zamiast ASCII [#5369](https://github.com/PowerShell/PowerShell/issues/5369)

Poprzednie kodowanie ASCII (7-bitowym) mogłoby spowodować niepoprawne zmiany w danych wyjściowych w niektórych przypadkach. Ta zmiana jest zapewnienie `UTF-8 NoBOM` domyślna, która zachowuje dane wyjściowe Unicode z kodowaniem obsługiwane przez większość narzędzi i systemów operacyjnych.

### <a name="remove-allscope-from-most-default-aliases-5268httpsgithubcompowershellpowershellissues5268"></a>Usuń `AllScope` z większości domyślne aliasy [#5268](https://github.com/PowerShell/PowerShell/issues/5268)

Aby przyspieszyć tworzenie zakresu `AllScope` został usunięty z większości domyślne aliasy. `AllScope` pozostawało przez kilka często używanych aliasy tam, gdzie wyszukiwania nie szybciej.

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113httpsgithubcompowershellpowershellissues5113"></a>`-Verbose` i `-Debug` nie jest już zastępuje `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)

Wcześniej Jeśli `-Verbose` lub `-Debug` zostały określone jego overrode zachowanie `$ErrorActionPreference`. Dzięki tej zmianie `-Verbose` i `-Debug` nie będzie mieć wpływ na zachowanie `$ErrorActionPreference`.

## <a name="cmdlet-changes"></a>Zmiany poleceń cmdlet

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320httpsgithubcompowershellpowershellissues5320"></a>Wywołania RestMethod nie zwraca przydatnych informacji, gdy są zwracane żadne dane. [#5320](https://github.com/PowerShell/PowerShell/issues/5320)

Gdy interfejs API zwraca tylko `null`, Invoke RestMethod została to serializowania w postaci ciągu `"null"` zamiast `$null`. Ta zmiana rozwiązuje logikę `Invoke-RestMethod` prawidłowo serializować prawidłowej wartości pojedynczej JSON `null` literału jako `$null`.

### <a name="remove--computername-from--computer-cmdlets-5277httpsgithubcompowershellpowershellissues5277"></a>Usuń `-ComputerName` z `*-Computer` poleceń cmdlet [#5277](https://github.com/PowerShell/PowerShell/issues/5277)

Z powodu problemów z wywołaniem funkcji zdalnych RPC, CoreFX (szczególnie na platformach innych niż Windows) i zapewnienie środowisku spójne komunikacji zdalnej w programie PowerShell `-ComputerName` parametr został usunięty z `\*-Computer` polecenia cmdlet. Użyj `Invoke-Command` zamiast jako sposób wykonania poleceń cmdlet zdalnie.

### <a name="remove--computername-from--service-cmdlets-5090httpsgithubcompowershellpowershellissues5094"></a>Usuń `-ComputerName` z `*-Service` poleceń cmdlet [#5090](https://github.com/PowerShell/PowerShell/issues/5094)

Aby zachęcać do spójnego stosowania PSRP, `-ComputerName` parametr został usunięty z `*-Service` polecenia cmdlet.

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197httpsgithubcompowershellpowershellissues5197"></a>Napraw `Get-Item -LiteralPath a*b` Jeśli `a*b` faktycznie nie istnieje na zwrócenie błędu [#5197](https://github.com/PowerShell/PowerShell/issues/5197)

Wcześniej `-LiteralPath` podany symbol wieloznaczny będzie jej traktowała taka sama jako `-Path` i jeśli symbol wieloznaczny znalezione żadne pliki, dyskretnie będzie zamknąć. Poprawne zachowanie powinien odpowiadać `-LiteralPath` jest literałem, więc jeśli plik nie istnieje, powinien on błędu. Zmiana jest używany z symbolami wieloznacznymi `-Literal` jako literał.

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134httpsgithubcompowershellpowershellissues5134"></a>`Import-Csv` należy zastosować `PSTypeNames` po zaimportowaniu, gdy informacje o typie jest obecna w woluminie CSV [#5134](https://github.com/PowerShell/PowerShell/issues/5134)

Wcześniej, obiekty wyeksportowane przy użyciu `Export-CSV` z `TypeInformation` zaimportowane wraz z `ConvertFrom-Csv` nie zostały zachowywanie informacji o typie. Ta zmiana dodaje informacje o typie, aby `PSTypeNames` członka, jeśli jest dostępny z pliku CSV.

### <a name="-notypeinformation-should-be-default-on-export-csv-5131httpsgithubcompowershellpowershellissues5131"></a>`-NoTypeInformation` powinna być wartością domyślną na `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)

Ta zmiana została wprowadzona, aby zareagować na opinie klientów na domyślne zachowanie `Export-CSV` obejmujący informacje o typie.

Wcześniej polecenia cmdlet będą dane wyjściowe komentarz jako pierwszy wiersz zawierający nazwę typu obiektu. Zmiana jest aby pominąć to domyślnie, ponieważ nie jest rozpoznawany przez większość narzędzi. Użyj `-IncludeTypeInformation` zachować poprzednie zachowanie.

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112httpsgithubcompowershellpowershellissues5112"></a>Polecenia cmdlet programu Web ostrzega, gdy `-Credential` są przesyłane za pośrednictwem połączenia nieszyfrowanego [#5112](https://github.com/PowerShell/PowerShell/issues/5112)

Podczas korzystania z protokołu HTTP zawartości w tym hasła są wysyłane jako zwykłego tekstu. Ta zmiana ma na celu nie zezwalają na to domyślnie i zwraca błędu, jeśli poświadczenia są są przekazywane w niezabezpieczony sposób. Użytkownicy mogą obejść to za pomocą `-AllowUnencryptedAuthentication` przełącznika.

## <a name="api-changes"></a>Zmiany interfejsu API

### <a name="remove-addtypecommandbase-class-5407httpsgithubcompowershellpowershellissues5407"></a>Usuń `AddTypeCommandBase` klasy [#5407](https://github.com/PowerShell/PowerShell/issues/5407)

`AddTypeCommandBase` Klasy został usunięty z `Add-Type` poprawić wydajność. Ta klasa jest używana tylko przez polecenie cmdlet Add-Type i nie powinny mieć wpływu na użytkowników.

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080httpsgithubcompowershellpowershellissues5080"></a>Ujednolicenie poleceń cmdlet z parametrem `-Encoding` typu `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)

`-Encoding` Wartość `Byte` został usunięty z polecenia cmdlet dostawcy systemu plików. Nowy parametr `-AsByteStream`, obecnie jest używany do określenia, czy strumień bajtów są wymagane jako dane wejściowe lub danych wyjściowych jest strumień bajtów.

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055httpsgithubcompowershellpowershellissues5055"></a>Dodaj lepsze komunikat o błędzie dla pusta i null `-UFormat` parametru [#5055](https://github.com/PowerShell/PowerShell/issues/5055)

Wcześniej, gdy przekazywanie formie pusty ciąg, który ma `-UFormat`, zostanie wyświetlony komunikat o błędzie zbędny. Dodano bardziej opisowe błędu.

### <a name="clean-up-console-code-4995httpsgithubcompowershellpowershellissues4995"></a>Czyszczenie kodu konsoli [#4995](https://github.com/PowerShell/PowerShell/issues/4995)

Następujące funkcje zostały usunięte, ponieważ nie są obsługiwane w programie PowerShell Core i nie ma żadnych planów, aby dodać obsługę istniejących dla starszych powodów, dla środowiska Windows PowerShell: `-psconsolefile` przełącznika i kod, `-importsystemmodules` przełącznika kodu oraz czcionki, zmiany kodu.

### <a name="removed-runspaceconfiguration-support-4942httpsgithubcompowershellpowershellissues4942"></a>Usunięte `RunspaceConfiguration` obsługuje [#4942](https://github.com/PowerShell/PowerShell/issues/4942)

Wcześniej podczas tworzenia działania programu PowerShell programowo przy użyciu interfejsu API można użyć starszego [ `RunspaceConfiguration` ] [ runspaceconfig] lub nowszego [ `InitialSessionState` ] [ iss]. Ta zmiana usunięto obsługę dla `RunspaceConfiguration` i obsługuje tylko `InitialSessionState`.

[runspaceconfig]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923httpsgithubcompowershellpowershellissues4923"></a>`CommandInvocationIntrinsics.InvokeScript` Powiąż argumenty `$input` zamiast `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)

Nieprawidłowe położenie parametr spowodowało argumenty przekazywane jako dane wejściowe, a nie jako argumenty.

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903httpsgithubcompowershellpowershellissues4903"></a>Usuń nieobsługiwane `-showwindow` przełączyć się z `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)

`-showwindow` opiera się na WPF, która nie jest obsługiwana w środowisku CoreCLR.

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866httpsgithubcompowershellpowershellissues4866"></a>Zezwalaj na * do użycia w ścieżce rejestru dla `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)

Wcześniej `-LiteralPath` podany symbol wieloznaczny będzie jej traktowała taka sama jako `-Path` i jeśli symbol wieloznaczny znalezione żadne pliki, dyskretnie będzie zamknąć. Poprawne zachowanie powinien odpowiadać `-LiteralPath` jest literałem, więc jeśli plik nie istnieje, powinien on błędu. Zmiana jest używany z symbolami wieloznacznymi `-Literal` jako literał.

### <a name="fix-set-service-failing-test-4802httpsgithubcompowershellpowershellissues4802"></a>Napraw `Set-Service` kończy się niepowodzeniem testu [#4802](https://github.com/PowerShell/PowerShell/issues/4802)

Wcześniej Jeśli `New-Service -StartupType foo` było używane, `foo` został zignorowany, a usługa została utworzona za pomocą niektórych domyślny typ uruchamiania. Ta zmiana jest jawnie sygnalizować błąd dla typu uruchamiania nieprawidłowy.

### <a name="rename-isosx-to-ismacos-4700httpsgithubcompowershellpowershellissues4700"></a>Zmień nazwę `$IsOSX` do `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)

Nazewnictwa w programie PowerShell powinny być zgodne z naszych nazewnictwa i jest zgodna z zastosowaniem firmy Apple z systemem macOS zamiast OSX. Jednak aby zwiększyć czytelność i spójne możemy przebywają z Pascal wielkość liter w wyrazie.

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573httpsgithubcompowershellpowershellissues4573"></a>Wprowadź komunikat o błędzie spójne gdy Nieprawidłowy skrypt jest przekazywany: plik, Lepsza błąd podczas przekazywania argumentu niejednoznaczne [#4573](https://github.com/PowerShell/PowerShell/issues/4573)

Zmień kody zakończenia z `pwsh.exe` aby było zgodne z konwencjami systemu Unix

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302httpsgithubcompowershellpowershellissues4302-4303httpsgithubcompowershellpowershellissues4303"></a>Usuwanie `LocalAccount` i polecenia cmdlet z `Diagnostics` modułów. [#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)

Z powodu nieobsługiwanego interfejsów API `LocalAccounts` modułu i `Counter` polecenia cmdlet w `Diagnostics` modułu zostały usunięte, aż do znalezienia lepszym rozwiązaniem.

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036httpsgithubcompowershellpowershellissues4036"></a>Wykonywanie skryptu programu powershell z parametrem bool działa [#4036](https://github.com/PowerShell/PowerShell/issues/4036)

Wcześniej przy użyciu powershell.exe (teraz `pwsh.exe`) można wykonać skryptu środowiska PowerShell przy użyciu `-File` podać sposób przekazywania $true/$false jako wartości parametrów. Obsługa $true/dodano $false jako przeanalizowaną wartości parametrów. Przełącznik wartości również są obsługiwane, ponieważ obecnie udokumentowanego składni nie działa.

### <a name="remove-clrversion-property-from-psversiontable-4027httpsgithubcompowershellpowershellissues4027"></a>Usuń `ClrVersion` właściwość `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)

`ClrVersion` Właściwość `$PSVersionTable` jest nie jest przydatne przy użyciu programów CoreCLR, użytkownicy końcowi nie powinny używać tej wartości można określić zgodność.

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019httpsgithubcompowershellpowershellissues4019"></a>Zmień parametr pozycyjne `powershell.exe` z `-Command` do `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)

Włącz shebang użycie programu PowerShell na platformach innych niż Windows. Oznacza to, w systemach Unix, na podstawie ułatwia wykonywalny skrypt, który powodowałoby wywołanie pliku wykonywalnego programu PowerShell automatycznie zamiast jawne wywołanie `pwsh`. Oznacza to również, że teraz można wykonywać takie czynności, takich jak `powershell foo.ps1` lub `powershell fooScript` bez określania `-File`. Jednak ta zmiana wymaga teraz czy jawnie określasz `-c` lub `-Command` podczas próby wykonania elementów, takich jak `powershell.exe Get-Command`.

### <a name="implement-unicode-escape-parsing-3958httpsgithubcompowershellpowershellissues3958"></a>Implementowanie analizy ucieczki Unicode [#3958](https://github.com/PowerShell/PowerShell/issues/3958)

`` `u#### `` lub `` `u{####} `` jest konwertowana do odpowiedniego znaku Unicode. W danych wyjściowych literału `` `u ``, ucieczki początkowych: ``` ``u ```.

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940httpsgithubcompowershellpowershellissues3940"></a>Zmiana `New-ModuleManifest` kodowanie `UTF8NoBOM` na platformach innych niż Windows [#3940](https://github.com/PowerShell/PowerShell/issues/3940)

Wcześniej `New-ModuleManifest` tworzy manifesty psd1 w UTF-16 z BOM, to problem dla narzędzi systemu Linux. Tej istotnej zmiany zmienia kodowanie `New-ModuleManifest` jako UTF (nie BOM) na platformach innych niż Windows.

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780httpsgithubcompowershellpowershellissues3780"></a>Zapobiegaj `Get-ChildItem` z recursing do łączy symbolicznych (#1875). [#3780](https://github.com/PowerShell/PowerShell/issues/3780)

Ta zmiana powoduje `Get-ChildItem` bardziej zgodne z systemem Unix `ls -r` i Windows `dir /s` natywnych poleceń. Podobnie jak już wspomniano polecenia polecenie cmdlet wyświetla linki symboliczne podczas rekursji katalogów, ale nie wracać do nich.

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706httpsgithubcompowershellpowershellissues3706"></a>Napraw `Get-Content -Delimiter` wykluczającą ogranicznik w wierszy zwracanych [#3706](https://github.com/PowerShell/PowerShell/issues/3706)

Wcześniej, dane wyjściowe podczas korzystania z `Get-Content -Delimiter` niespójne i wygodne, ponieważ wymagane dalsze przetwarzanie danych do usunięcia ogranicznik. Ta zmiana spowoduje usunięcie ogranicznik wierszy zwracanych.

### <a name="implement-format-hex-in-c-3320httpsgithubcompowershellpowershellissues3320"></a>Implementowanie Hex Format, w C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320)

`-Raw` Parametru jest teraz "pusta" (w tym nic nie robi). Idąc dalej, zostaną wyświetlone wszystkie dane wyjściowe z rzeczywistej reprezentacji liczb, które obejmuje wszystkie bajtów dla jego typu (co `-Raw` parametru formalnego wykonywanych przed tą zmianą).

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319httpsgithubcompowershellpowershellissues3319"></a>Program PowerShell jako domyślnej powłoki nie działa z polecenia skryptu [#3319](https://github.com/PowerShell/PowerShell/issues/3319)

W systemie Unix, jest Konwencji powłoki zaakceptować `-i` dla interakcyjnej powłoki oraz wielu narzędzi oczekiwało tego zachowania (`script` na przykład i ustawienie środowiska PowerShell jako domyślnej powłoki) i wywołuje shell przy użyciu `-i` przełącznika. Ta zmiana jest istotne, w tym `-i` wcześniej można było używać jako krótki ręcznie do dopasowania `-inputformat`, które jest teraz musi być `-in`.

### <a name="typo-fix-in-get-computerinfo-property-name-3167httpsgithubcompowershellpowershellissues3167"></a>Napraw błąd pisowni w nazwie właściwości Get-ComputerInfo [#3167](https://github.com/PowerShell/PowerShell/issues/3167)

`BiosSerialNumber` została błędnie napisana jako `BiosSeralNumber` i został zmieniony na prawidłowo.

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024httpsgithubcompowershellpowershellissues3024"></a>Dodaj `Get-StringHash` i `Get-FileHash` poleceń cmdlet [#3024](https://github.com/PowerShell/PowerShell/issues/3024)

Ta zmiana jest, że niektóre algorytmy wyznaczania wartości skrótu nie są obsługiwane przez CoreFX, dlatego nie są już dostępne:

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672httpsgithubcompowershellpowershellissues2672"></a>Dodawanie sprawdzania poprawności na `Get-*` poleceń cmdlet, gdzie przekazywanie $null zwraca wszystkie obiekty zamiast błędu [#2672](https://github.com/PowerShell/PowerShell/issues/2672)

Przekazywanie `$null` do dowolnego z następujących zgłasza teraz błąd:

- `Get-Credential -UserName`
- `Get-Event -SourceIdentifier`
- `Get-EventSubscriber -SourceIdentifier`
- `Get-Help -Name`
- `Get-PSBreakpoint -Script`
- `Get-PSProvider -PSProvider`
- `Get-PSSessionConfiguration -Name`
- `Get-PSSnapin -Name`
- `Get-Runspace -Name`
- `Get-RunspaceDebug -RunspaceName`
- `Get-Service -Name`
- `Get-TraceSource -Name`
- `Get-Variable -Name`
- `Get-WmiObject -Class`
- `Get-WmiObject -Property`

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482httpsgithubcompowershellpowershellissues2482"></a>Dodawanie obsługi rozszerzony Format W3C pliku dziennika w `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)

Wcześniej `Import-Csv` polecenia cmdlet, nie można bezpośrednio importować pliki dziennika w rozszerzonym formacie W3C dziennika oraz dodatkowych akcji jest wymagana. Dzięki tej zmianie rozszerzonym formacie W3C dziennika jest obsługiwane.

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035httpsgithubcompowershellpowershellissues2035"></a>Problem z powiązaniem parametru za pomocą `ValueFromRemainingArguments` w funkcjach PS [#2035](https://github.com/PowerShell/PowerShell/issues/2035)

`ValueFromRemainingArguments` teraz zwraca wartości jako tablicę zamiast pojedynczej wartości, która sama jest tablicą.

### <a name="buildversion-is-removed-from-psversiontable-1415httpsgithubcompowershellpowershellissues1415"></a>`BuildVersion` zostanie usunięty z `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)

Usuń `BuildVersion` właściwość `$PSVersionTable`. Ta właściwość powiązanej z wersji kompilacji Windows. Zamiast tego zaleca się używanie `GitCommitId` można pobrać kompilacji dokładną wersję programu PowerShell Core.

### <a name="changes-to-web-cmdlets"></a>Zmiany w poleceniach cmdlet usługi sieci Web

Podstawowy interfejs API .NET poleceń cmdlet sieci Web został zmieniony na `System.Net.Http.HttpClient`. Ta zmiana oferuje wiele korzyści. Jednak powoduje powstanie kilka przełomowe zmiany w ramach tej zmiany wraz z braku współdziałania z programem Internet Explorer `Invoke-WebRequest` i `Invoke-RestMethod`.

- `Invoke-WebRequest` obsługuje teraz podstawowe HTML podczas analizowania tylko. `Invoke-WebRequest` zawsze zwraca `BasicHtmlWebResponseObject` obiektu. `ParsedHtml` i `Forms` właściwości zostały usunięte.
- `BasicHtmlWebResponseObject.Headers` wartości są teraz `String[]` zamiast `String`.
- `BasicHtmlWebResponseObject.BaseResponse` jest teraz `System.Net.Http.HttpResponseMessage` obiektu.
- `Response` Właściwość na wyjątkach polecenia Cmdlet w sieci Web jest obecnie `System.Net.Http.HttpResponseMessage` obiektu.
- Strict RFC nagłówka analiza jest teraz domyślnym `-Headers` i `-UserAgent` parametru. To, co może prowadzić z `-SkipHeaderValidation`.
- `file://` i `ftp://` schematy identyfikatorów URI nie są już obsługiwane.
- `System.Net.ServicePointManager` ustawienia nie są uznawane.
- Brak dostępnej obecnie bez uwierzytelniania opartego na certyfikatach w systemie macOS.
- Korzystanie z `-Credential` za pośrednictwem `http://` URI spowoduje wystąpienie błędu. Użyj `https://` identyfikatora URI lub podać `-AllowUnencryptedAuthentication` parametru, aby pominąć ten błąd.
- `-MaximumRedirection` teraz generuje błąd powodujący zakończenie, podczas próby przekierowania przekraczają limit podana zamiast zwracać wyniki ostatniego przekierowania.
