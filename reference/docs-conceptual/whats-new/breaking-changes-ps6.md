---
ms.date: 05/17/2018
keywords: środowiska PowerShell, podstawowe
title: Zmiany krytyczne 6.0 środowiska PowerShell
ms.openlocfilehash: 60ce7a1676403bb08b57bf852ba725acde86a30c
ms.sourcegitcommit: 2d9cf1ccb9a653db7726a408ebcb65530dcb1522
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2018
---
# <a name="breaking-changes-for-powershell-60"></a>Zmiany krytyczne 6.0 środowiska PowerShell

## <a name="features-no-longer-available-in-powershell-core"></a>Funkcje nie są już dostępne główną programu PowerShell

### <a name="powershell-workflow"></a>Przepływ pracy programu PowerShell

[Przepływ pracy programu PowerShell] [ workflow] jest funkcją w programie Windows PowerShell, która tworzy nad [Windows Workflow Foundation (WF)] [ workflow-foundation] , umożliwia tworzenie niezawodna runbook długotrwałe lub zrównoleglone zadań.

Ze względu na brak obsługi systemu Windows Workflow Foundation w .NET Core firma Microsoft nie będzie kontynuowane do obsługi przepływu pracy programu PowerShell w podstawowej programu PowerShell.

W przyszłości Chcielibyśmy włączyć natywnego równoległości/współbieżność w języku środowiska PowerShell bez konieczności przepływu pracy programu PowerShell.

[workflow]: https://docs.microsoft.com/powershell/scripting/core-powershell/workflows-guide
[workflow-foundation]: https://docs.microsoft.com/dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a>Niestandardowe przystawek

[Przystawki programu PowerShell] [ snapin] są poprzednik modułów środowiska PowerShell, które nie mają powszechnie przyjęcia w społeczności programu PowerShell.

Ze względu na złożoność obsługi przystawek i ich braku użycia w społeczności nie obsługujemy niestandardowych przystawki główną programu PowerShell.

Obecnie dzieli `ActiveDirectory` i `DnsClient` modułów w systemie Windows i Windows Server.

[snapin]: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a>Polecenia cmdlet w wersji 1 usługi WMI

Z powodu złożoności obsługi dwóch zestawów modułów opartych na infrastrukturze WMI firma Microsoft usunęła poleceń cmdlet w wersji 1 usługi WMI z podstawowych programu PowerShell:

- `Get-WmiObject`
- `Invoke-WmiMethod`
- `Register-WmiEvent`
- `Set-WmiInstance`

Zamiast tego zaleca się, że użytkownik, użyj polecenia cmdlet modelu wspólnych informacji (alias WMI w wersji 2), które mają te same funkcje z nowych funkcji i zmienioną składni:

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

Z powodu używania interfejsów API nieobsługiwany `Microsoft.PowerShell.LocalAccounts` został usunięty z programu PowerShell Core aż do znalezienia lepszym rozwiązaniem.

### <a name="-counter-cmdlets"></a>Polecenia cmdlet środowiska `*-Counter`

Z powodu używania interfejsów API nieobsługiwany `*-Counter` został usunięty z programu PowerShell Core aż do znalezienia lepszym rozwiązaniem.

## <a name="enginelanguage-changes"></a>Zmiany aparat/języka

### <a name="rename-powershellexe-to-pwshexe-5101httpsgithubcompowershellpowershellissues5101"></a>Zmień nazwę `powershell.exe` do `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)

Aby udostępnić użytkownikom deterministyczne sposób wywołania Core programu PowerShell w systemie Windows (w przeciwieństwie do programu Windows PowerShell), plik binarny programu PowerShell Core została zmieniona na `pwsh.exe` w systemie Windows i `pwsh` na platformach z systemem innym niż Windows.

Skrócona nazwa również jest zgodna z nazewnictwem powłok na platformach z systemem innym niż Windows.

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193httpsgithubcompowershellpowershellissues5193"></a>Podziały wierszy do wyjściowego (z wyjątkiem tabele) nie zostały wstawione [#5193](https://github.com/PowerShell/PowerShell/issues/5193)

Wcześniej dane wyjściowe został wyrównany do szerokość konsoli, a podziały wiersza zostały dodane w szerokość zakończenia konsoli, co oznacza, że dane wyjściowe nie Pobierz ponownie sformatowany zgodnie z oczekiwaniami, jeśli zmiany rozmiaru terminala. Ta zmiana nie została zastosowana do tabel, podziały wierszy są muszą być wyrównane kolumny.

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432httpsgithubcompowershellpowershellissues5432"></a>Pomijania sprawdzania elementu null w przypadku kolekcji z wartości typu elementu [#5432](https://github.com/PowerShell/PowerShell/issues/5432)

Aby uzyskać `Mandatory` parametru i `ValidateNotNull` i `ValidateNotNullOrEmpty` atrybuty, pomijania sprawdzania elementu null, jeśli typ elementu kolekcji jest typ wartości.

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369httpsgithubcompowershellpowershellissues5369"></a>Zmień `$OutputEncoding` do używania `UTF-8 NoBOM` kodowanie zamiast ASCII [#5369](https://github.com/PowerShell/PowerShell/issues/5369)

Poprzednie kodowanie ASCII (7-bitowy), spowoduje nieprawidłowe zmiany w danych wyjściowych w niektórych przypadkach. Ta zmiana jest zapewnienie `UTF-8 NoBOM` domyślny, który zachowuje danych wyjściowych Unicode z kodowaniem obsługiwane przez większość narzędzi i systemów operacyjnych.

### <a name="remove-allscope-from-most-default-aliases-5268httpsgithubcompowershellpowershellissues5268"></a>Usuń `AllScope` z większości domyślne aliasy [#5268](https://github.com/PowerShell/PowerShell/issues/5268)

Aby przyspieszyć tworzenie zakresu `AllScope` został usunięty z większości domyślne aliasy. `AllScope` pozostawało przez kilka aliasów często używane tam, gdzie nie szybsze wyszukiwania.

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113httpsgithubcompowershellpowershellissues5113"></a>`-Verbose` i `-Debug` nie zastępuje `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)

Wcześniej Jeśli `-Verbose` lub `-Debug` zostały określone jego overrode zachowanie `$ErrorActionPreference`. Dzięki tej zmianie `-Verbose` i `-Debug` nie ma wpływu na zachowanie `$ErrorActionPreference`.

## <a name="cmdlet-changes"></a>Polecenia cmdlet zmiany

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320httpsgithubcompowershellpowershellissues5320"></a>Wywołania RestMethod nie zwraca przydatne informacje, gdy żadne dane nie zwrócone. [#5320](https://github.com/PowerShell/PowerShell/issues/5320)

Gdy interfejs API zwraca tylko `null`, Invoke RestMethod został serializacji to jako ciąg `"null"` zamiast `$null`. Ta zmiana poprawki logikę `Invoke-RestMethod` prawidłowo serializować prawidłowej wartości pojedynczej JSON `null` literałów jako `$null`.

### <a name="remove--computername-from--computer-cmdlets-5277httpsgithubcompowershellpowershellissues5277"></a>Usuń `-ComputerName` z `*-Computer` poleceń cmdlet [#5277](https://github.com/PowerShell/PowerShell/issues/5277)

Z powodu problemów dotyczących usług RPC zdalnych w CoreFX (szczególnie na platformach z systemem innym niż Windows) oraz zapewnienie obsługi spójne zdalnych w programie PowerShell `-ComputerName` parametr został usunięty z `\*-Computer` polecenia cmdlet. Użyj `Invoke-Command` zamiast tego w sposób wykonywania poleceń cmdlet zdalnie.

### <a name="remove--computername-from--service-cmdlets-5090httpsgithubcompowershellpowershellissues5094"></a>Usuń `-ComputerName` z `*-Service` poleceń cmdlet [#5090](https://github.com/PowerShell/PowerShell/issues/5094)

W celu wsparcia spójne używanie PSRP, `-ComputerName` parametr został usunięty z `*-Service` polecenia cmdlet.

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197httpsgithubcompowershellpowershellissues5197"></a>Napraw `Get-Item -LiteralPath a*b` Jeśli `a*b` faktycznie nie istnieje na zwrócenie błędu [#5197](https://github.com/PowerShell/PowerShell/issues/5197)

Wcześniej `-LiteralPath` dany symbol wieloznaczny będzie je traktować takie same jak `-Path` i jeśli symbolu wieloznacznego nie znaleziono żadnych plików, czy zamknąć trybie dyskretnym. Poprawne działanie powinno być `-LiteralPath` jest literałem, jeśli plik nie istnieje, powinien on błędu. Zmiana ma na celu Traktuj używane z symboli wieloznacznych `-Literal` jako literał.

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134httpsgithubcompowershellpowershellissues5134"></a>`Import-Csv` należy stosować `PSTypeNames` podczas importu, jeśli występuje w woluminie CSV informacji o typie [#5134](https://github.com/PowerShell/PowerShell/issues/5134)

Wcześniej, obiekty wyeksportowane za pomocą `Export-CSV` z `TypeInformation` zaimportowane z `ConvertFrom-Csv` nie zostały zachowywanie informacji o typie. Ta zmiana dodaje informacje o typie do `PSTypeNames` członka, jeśli jest dostępny z pliku CSV.

### <a name="-notypeinformation-should-be-default-on-export-csv-5131httpsgithubcompowershellpowershellissues5131"></a>`-NoTypeInformation` powinien być domyślnie na `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)

Ta zmiana została wprowadzona zareagować na opinie klientów na domyślne zachowanie `Export-CSV` do uwzględnienia informacji o typie.

Wcześniej polecenia cmdlet spowoduje wyjściowej komentarz jako pierwszy wiersz zawierający nazwę typu obiektu. Zmiana jest aby pominąć to domyślnie, ponieważ nie jest rozpoznawany przez większość narzędzi. Użyj `-IncludeTypeInformation` Aby zachować poprzednie.

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112httpsgithubcompowershellpowershellissues5112"></a>Polecenia cmdlet sieci Web powinien Ostrzegaj przy `-Credential` był wysyłany za pośrednictwem nieszyfrowanego połączenia [#5112](https://github.com/PowerShell/PowerShell/issues/5112)

Przy użyciu protokołu HTTP, zawartość w tym hasła są wysyłane jako zwykłego tekstu. Ta zmiana jest nie zezwalaj domyślnie i zwraca błąd, jeśli poświadczenia są przekazano niezabezpieczony sposób. Użytkownicy mogą obejść to przy użyciu `-AllowUnencryptedAuthentication` przełącznika.

## <a name="api-changes"></a>Zmiany interfejsu API

### <a name="remove-addtypecommandbase-class-5407httpsgithubcompowershellpowershellissues5407"></a>Usuń `AddTypeCommandBase` klasy [#5407](https://github.com/PowerShell/PowerShell/issues/5407)

`AddTypeCommandBase` Klasy został usunięty z `Add-Type` do zwiększenia wydajności. Ta klasa jest używana tylko przez polecenie cmdlet Add-Type i powinna mieć wpływu na użytkowników.

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080httpsgithubcompowershellpowershellissues5080"></a>Ujednolicenie poleceń cmdlet z parametrem `-Encoding` typu `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)

`-Encoding` Wartość `Byte` został usunięty z polecenia cmdlet dostawcy filesystem. Nowy parametr `-AsByteStream`, teraz służy do określania, czy strumień bajtów jest wymaganych jako dane wejściowe lub dane wyjściowe jest strumieniem bajtów.

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055httpsgithubcompowershellpowershellissues5055"></a>Dodaj lepsze komunikat o błędzie dla pusta i null `-UFormat` parametru [#5055](https://github.com/PowerShell/PowerShell/issues/5055)

Wcześniej, gdy przekazywanie formatu pusty ciąg, który ma `-UFormat`, która nie jest pomocna błąd pojawiały się. Dodano więcej opisem błędu.

### <a name="clean-up-console-code-4995httpsgithubcompowershellpowershellissues4995"></a>Oczyszczanie kodu konsoli [#4995](https://github.com/PowerShell/PowerShell/issues/4995)

Następujące funkcje zostały usunięte, ponieważ nie są obsługiwane w podstawowej programu PowerShell, a nie ma żadnych planów, aby dodać obsługę istniejących przyczyn starszej wersji środowiska Windows PowerShell: `-psconsolefile` przełącznika i kod, `-importsystemmodules` przełącznika kodu oraz czcionki zmiana kodu.

### <a name="removed-runspaceconfiguration-support-4942httpsgithubcompowershellpowershellissues4942"></a>Usunięte `RunspaceConfiguration` obsługuje [#4942](https://github.com/PowerShell/PowerShell/issues/4942)

Wcześniej, podczas tworzenia działania programu PowerShell programowo przy użyciu interfejsu API można użyć starszego [ `RunspaceConfiguration` ] [ runspaceconfig] lub nowszej [ `InitialSessionState` ] [ iss]. Ta zmiana usunięta obsługa `RunspaceConfiguration` i obsługuje tylko `InitialSessionState`.

[runspaceconfig]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923httpsgithubcompowershellpowershellissues4923"></a>`CommandInvocationIntrinsics.InvokeScript` Powiąż argumenty `$input` zamiast `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)

Niepoprawna pozycja parametru spowodowała argumentów przekazany jako dane wejściowe, a nie jako argumenty.

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903httpsgithubcompowershellpowershellissues4903"></a>Usuń nieobsługiwane `-showwindow` przejść z `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)

`-showwindow` zależy od WPF, która nie jest obsługiwana na środowisko CoreCLR.

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866httpsgithubcompowershellpowershellissues4866"></a>Zezwalaj na * do użycia w ścieżce rejestru dla `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)

Wcześniej `-LiteralPath` dany symbol wieloznaczny będzie je traktować takie same jak `-Path` i jeśli symbolu wieloznacznego nie znaleziono żadnych plików, czy zamknąć trybie dyskretnym. Poprawne działanie powinno być `-LiteralPath` jest literałem, jeśli plik nie istnieje, powinien on błędu. Zmiana ma na celu Traktuj używane z symboli wieloznacznych `-Literal` jako literał.

### <a name="fix-set-service-failing-test-4802httpsgithubcompowershellpowershellissues4802"></a>Napraw `Set-Service` niepowodzenia testu [#4802](https://github.com/PowerShell/PowerShell/issues/4802)

Wcześniej Jeśli `New-Service -StartupType foo` została użyta `foo` został zignorowany, a usługa została utworzona z niektórych domyślny typ uruchamiania. Ta zmiana jest jawnie zgłosić błąd typ uruchomienia nieprawidłowy.

### <a name="rename-isosx-to-ismacos-4700httpsgithubcompowershellpowershellissues4700"></a>Zmień nazwę `$IsOSX` do `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)

Nazewnictwa w programie PowerShell powinny być zgodne z naszych nazewnictwa i jest zgodna z wykorzystaniem macOS zamiast OS x firmy Apple. Jednak aby można było czytać i spójnej możemy przebywają z Pascal wielkości liter.

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573httpsgithubcompowershellpowershellissues4573"></a>Błąd komunikatu spójne podczas podjąć Nieprawidłowy skrypt jest przekazywany do - pliku, błąd podczas przekazywania argumentu niejednoznaczne lepsze [#4573](https://github.com/PowerShell/PowerShell/issues/4573)

Zmień kody zakończenia `pwsh.exe` , aby były wyrównane z konwencjami systemu Unix

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302httpsgithubcompowershellpowershellissues4302-4303httpsgithubcompowershellpowershellissues4303"></a>Usunięcie `LocalAccount` i poleceń cmdlet z `Diagnostics` modułów. [#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)

Z powodu nieobsługiwanego interfejsów API `LocalAccounts` modułu i `Counter` polecenia cmdlet w `Diagnostics` modułu zostały usunięte, aż do znalezienia lepszym rozwiązaniem.

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036httpsgithubcompowershellpowershellissues4036"></a>Wykonywanie skryptu programu powershell z parametrem bool nie działa [#4036](https://github.com/PowerShell/PowerShell/issues/4036)

Wcześniej, przy użyciu powershell.exe (teraz `pwsh.exe`) można wykonać skryptu programu PowerShell przy użyciu `-File` podać sposób przekazywania $true/$false jako wartości parametrów. Obsługa $true/dodano $false jako przeanalizowane wartości parametrów. Wartości przełącznika są również obsługiwane zgodnie z obecnie udokumentowane składni nie działa.

### <a name="remove-clrversion-property-from-psversiontable-4027httpsgithubcompowershellpowershellissues4027"></a>Usuń `ClrVersion` właściwość z `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)

`ClrVersion` Właściwość `$PSVersionTable` jest nie przydatne w przypadku środowisko CoreCLR, użytkownicy końcowi nie używaj tej wartości można określić zgodność.

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019httpsgithubcompowershellpowershellissues4019"></a>Zmiana parametrów pozycyjnych dla `powershell.exe` z `-Command` do `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)

Zezwalaj na używanie shebang programu PowerShell na platformach z systemem innym niż Windows. Oznacza to, na komputerach z systemem Unix, na podstawie, możesz wprowadzić skryptu plik wykonywalny, który powodowałoby wywołanie pliku wykonywalnego programu PowerShell automatycznie zamiast jawnie wywoływania `pwsh`. Oznacza to również, że możesz można teraz wykonywać następujące czynności `powershell foo.ps1` lub `powershell fooScript` bez określania `-File`. Jednak ta zmiana teraz wymaga jawnego określenia `-c` lub `-Command` podczas próby wykonywać następujące czynności `powershell.exe Get-Command`.

### <a name="implement-unicode-escape-parsing-3958httpsgithubcompowershellpowershellissues3958"></a>Implementowanie analizowania ucieczki Unicode [#3958](https://github.com/PowerShell/PowerShell/issues/3958)

`` `u#### `` lub `` `u{####} `` jest konwertowana na odpowiedni znak Unicode. Do wyjściowego literału `` `u ``, escape backtick: ``` ``u ```.

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940httpsgithubcompowershellpowershellissues3940"></a>Zmień `New-ModuleManifest` kodowanie `UTF8NoBOM` na platformach z systemem innym niż Windows [#3940](https://github.com/PowerShell/PowerShell/issues/3940)

Wcześniej `New-ModuleManifest` tworzy manifestów psd1 UTF-16 z BOM to problem dla narzędzi systemu Linux. Zmiany tej istotnej zmiany kodowanie `New-ModuleManifest` jako UTF (nie BOM) na platformach z systemem innym niż Windows.

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780httpsgithubcompowershellpowershellissues3780"></a>Zapobiegaj `Get-ChildItem` z recursing do łączy symbolicznych (#1875). [#3780](https://github.com/PowerShell/PowerShell/issues/3780)

Ta zmiana powoduje `Get-ChildItem` bardziej zgodne z systemem Unix `ls -r` i systemu Windows `dir /s` natywnych poleceń. Podobnie jak opisane powyżej poleceń polecenie cmdlet wyświetla katalogi podczas rekursji odnaleziono łącza symbolicznego, ale nie wracać do nich.

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706httpsgithubcompowershellpowershellissues3706"></a>Napraw `Get-Content -Delimiter` nie należeć ogranicznik wierszy zwracanych [#3706](https://github.com/PowerShell/PowerShell/issues/3706)

Wcześniej, dane wyjściowe podczas używania `Get-Content -Delimiter` jest niespójne i niewygodne, ponieważ wymagane dalsze przetwarzanie danych, aby usunąć ogranicznik. Ta zmiana spowoduje usunięcie ogranicznik wierszy zwracanych.

### <a name="implement-format-hex-in-c-3320httpsgithubcompowershellpowershellissues3320"></a>Implementowanie Hex formatu w C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320)

`-Raw` Parametr jest teraz "pusta" (nie). Idąc dalej, zostaną wyświetlone wszystkie dane wyjściowe z rzeczywistej reprezentacji liczb, które zawiera wszystkie bajtów dla tego typu (co `-Raw` parametru formalnego wykonywanych przed zmianą).

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319httpsgithubcompowershellpowershellissues3319"></a>PowerShell jako domyślną powłokę nie działa z polecenia skryptu [#3319](https://github.com/PowerShell/PowerShell/issues/3319)

W systemie Unix, jest Konwencja powłoki zaakceptować `-i` dla powłoki interakcyjne i wielu narzędzi spodziewać to zachowanie (`script` na przykład i ustawienie programu PowerShell jako domyślną powłokę) oraz wywołania powłoki z `-i` przełącznika. Ta zmiana jest krytyczne w tym `-i` wcześniej można było używać jako krótki ręcznie odpowiadające `-inputformat`, które teraz musi być `-in`.

### <a name="typo-fix-in-get-computerinfo-property-name-3167httpsgithubcompowershellpowershellissues3167"></a>Poprawka Literówka w nazwie właściwości Get-ComputerInfo [#3167](https://github.com/PowerShell/PowerShell/issues/3167)

`BiosSerialNumber` została błędnie wpisana jako `BiosSeralNumber` i został zmieniony na poprawną pisownię.

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024httpsgithubcompowershellpowershellissues3024"></a>Dodaj `Get-StringHash` i `Get-FileHash` poleceń cmdlet [#3024](https://github.com/PowerShell/PowerShell/issues/3024)

Ta zmiana jest, że niektóre algorytmy wyznaczania wartości skrótu nie są obsługiwane przez CoreFX, w związku z tym nie są one dostępne:

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672httpsgithubcompowershellpowershellissues2672"></a>Dodawanie walidacji na `Get-*` poleceń cmdlet, których przekazywanie $null zwraca wszystkie obiekty zamiast błędu [#2672](https://github.com/PowerShell/PowerShell/issues/2672)

Przekazywanie `$null` do żadnego z następujących teraz zwraca błąd:

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

Wcześniej `Import-Csv` polecenie cmdlet nie może służyć do bezpośrednio importowanie plików dziennika w rozszerzonym formacie W3C dziennika oraz dodatkowych akcji jest wymagana. Dzięki tej zmianie rozszerzonym formacie W3C dziennika jest obsługiwana.

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035httpsgithubcompowershellpowershellissues2035"></a>Problem powiązanie parametru z `ValueFromRemainingArguments` w funkcjach PS [#2035](https://github.com/PowerShell/PowerShell/issues/2035)

`ValueFromRemainingArguments` obecnie zwraca wartości jako tablicę zamiast jedną wartość, które jest tablicą.

### <a name="buildversion-is-removed-from-psversiontable-1415httpsgithubcompowershellpowershellissues1415"></a>`BuildVersion` zostanie usunięty z `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)

Usuń `BuildVersion` właściwość z `$PSVersionTable`. Tej właściwości został powiązany numer kompilacji systemu Windows. Zamiast tego zaleca się używanie `GitCommitId` można pobrać wersję kompilacji dokładne Core programu PowerShell.

### <a name="changes-to-web-cmdlets"></a>Zmiany do polecenia cmdlet sieci Web

Podstawowy interfejs API .NET poleceń cmdlet sieci Web został zmieniony na `System.Net.Http.HttpClient`. Ta zmiana oferuje wiele korzyści. Jednak ta zmiana wraz z braku współdziałania z programem Internet Explorer spowodowały kilka najważniejszych zmian w `Invoke-WebRequest` i `Invoke-RestMethod`.

- `Invoke-WebRequest` obsługuje teraz podstawowe HTML podczas analizowania tylko. `Invoke-WebRequest` zawsze zwraca `BasicHtmlWebResponseObject` obiektu. `ParsedHtml` i `Forms` właściwości zostały usunięte.
- `BasicHtmlWebResponseObject.Headers` wartości są teraz `String[]` zamiast `String`.
- `BasicHtmlWebResponseObject.BaseResponse` jest teraz `System.Net.Http.HttpResponseMessage` obiektu.
- `Response` Właściwość wyjątki polecenia Cmdlet sieci Web jest teraz `System.Net.Http.HttpResponseMessage` obiektu.
- Analizowanie Strict RFC nagłówka jest teraz domyślną `-Headers` i `-UserAgent` parametru. To jest obejście z `-SkipHeaderValidation`.
- `file://` i `ftp://` schematy identyfikatorów URI nie są już obsługiwane.
- `System.Net.ServicePointManager` ustawienia nie są uznawane.
- Nie aktualnie bez uwierzytelniania opartego na certyfikatach dostępnej na macOS.
- Użycie `-Credential` za pośrednictwem `http://` URI spowoduje błąd. Użyj `https://` identyfikatora URI lub podać `-AllowUnencryptedAuthentication` parametr, aby pominąć ten błąd.
