---
ms.date: 05/17/2018
keywords: program PowerShell, rdzeń
title: Istotne zmiany w programie PowerShell 6,0
ms.openlocfilehash: 186e55c1ac46ce3fc172df18995f8c15d9eeb8eb
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2019
ms.locfileid: "67843938"
---
# <a name="breaking-changes-for-powershell-60"></a>Istotne zmiany w programie PowerShell 6,0

## <a name="features-no-longer-available-in-powershell-core"></a>Funkcje, które nie są już dostępne w programie PowerShell Core

### <a name="powershell-workflow"></a>Przepływ pracy programu PowerShell

[Przepływ pracy programu PowerShell][workflow] to funkcja środowiska Windows PowerShell, która kompiluje się na podstawie [Windows Workflow Foundation (WF)][workflow-foundation] , która umożliwia tworzenie niezawodnych elementów Runbook na potrzeby długotrwałych lub równoległych zadań.

Ze względu na brak wsparcia dla Windows Workflow Foundation w oprogramowaniu .NET Core nie będzie on obsługiwał przepływu pracy programu PowerShell w programie PowerShell Core.

W przyszłości chcemy włączyć natywną równoległość/współbieżność w języku programu PowerShell bez potrzeby przepływu pracy programu PowerShell.

[workflow]: https://docs.microsoft.com/powershell/scripting/core-powershell/workflows-guide
[workflow-foundation]: https://docs.microsoft.com/dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a>Przystawki niestandardowe

[Przystawki programu PowerShell][snapin] są poprzednikami modułów programu PowerShell, które nie mają powszechnego wdrożenia w społeczności programu PowerShell.

Ze względu na złożoność obsługi przystawek i ich braku użycia w społeczności, nie obsługujemy już niestandardowych przystawek w programie PowerShell Core.

Obecnie spowoduje to przerwanie `ActiveDirectory` modułów `DnsClient` i w systemach Windows i Windows Server.

[snapin]: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a>Polecenia cmdlet usługi WMI w wersji 1

Ze względu na złożoność obsługi dwóch zestawów modułów opartych na usłudze WMI, usunięto polecenia cmdlet usługi WMI w wersji 1 z programu PowerShell Core:

- `Get-WmiObject`
- `Invoke-WmiMethod`
- `Register-WmiEvent`
- `Set-WmiInstance`

Zamiast tego zaleca się użycie poleceń cmdlet modelu CIM (aliasu WMI v2), które zapewniają taką samą funkcjonalność, jak nowe funkcje i przeprojektowaną składnię:

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

### <a name="microsoftpowershelllocalaccounts"></a>Microsoft. PowerShell. LocalAccounts

Ze względu na użycie nieobsługiwanych `Microsoft.PowerShell.LocalAccounts` interfejsów API, został usunięty z programu PowerShell Core do momentu znalezienia lepszego rozwiązania.

### <a name="-computer-cmdlets"></a>`*-Computer`poleceń cmdlet

Ze względu na użycie nieobsługiwanych interfejsów API następujące polecenia cmdlet zostały usunięte z programu PowerShell Core do momentu znalezienia lepszego rozwiązania.

- Add-Computer
- Checkpoint-Computer
- Remove-Computer
- Przywracanie — komputer

### <a name="-counter-cmdlets"></a>`*-Counter`poleceń cmdlet

Ze względu na użycie nieobsługiwanych interfejsów `*-Counter` API program został usunięty z programu PowerShell Core do momentu znalezienia lepszego rozwiązania.

### <a name="-eventlog-cmdlets"></a>`*-EventLog`poleceń cmdlet

Ze względu na użycie nieobsługiwanych interfejsów `*-EventLog` API program został usunięty z programu PowerShell Core. do momentu znalezienia lepszego rozwiązania. `Get-WinEvent`i `Create-WinEvent` są dostępne do pobierania i tworzenia zdarzeń w systemie Windows.

## <a name="enginelanguage-changes"></a>Zmiany silnika/języka

### <a name="rename-powershellexe-to-pwshexe-5101httpsgithubcompowershellpowershellissues5101"></a>Zmień `powershell.exe` nazwę `pwsh.exe` na [#5101](https://github.com/PowerShell/PowerShell/issues/5101)

Aby zapewnić użytkownikom jednoznaczny sposób wywoływania programu PowerShell Core w systemie Windows (w przeciwieństwie do programu Windows PowerShell), plik binarny programu PowerShell został zmieniony `pwsh.exe` na system Windows i `pwsh` na platformach innych niż Windows.

Skrócona nazwa jest również spójna z nazewnictwem powłok na platformach innych niż Windows.

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193httpsgithubcompowershellpowershellissues5193"></a>Nie wstawiaj podziałów wierszy do danych wyjściowych (z wyjątkiem tabel) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)

Wcześniej dane wyjściowe były wyrównane do szerokości konsoli, a podziały wierszy zostały dodane na szerokości końcowej konsoli, co oznacza, że dane wyjściowe nie zostały sformatowane zgodnie z oczekiwaniami, jeśli rozmiar terminalu został zmieniony. Ta zmiana nie została zastosowana do tabel, ponieważ podziały wierszy są niezbędne, aby zachować wyrównanie kolumn.

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432httpsgithubcompowershellpowershellissues5432"></a>Pomiń sprawdzanie elementu o wartości null dla kolekcji z typem elementu typu wartości [#5432](https://github.com/PowerShell/PowerShell/issues/5432)

Dla parametru i `ValidateNotNull` i`ValidateNotNullOrEmpty` atrybutów Pomiń sprawdzanie elementu null, jeśli typ elementu kolekcji to typ wartości. `Mandatory`

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369httpsgithubcompowershellpowershellissues5369"></a>Zmień `$OutputEncoding` , aby `UTF-8 NoBOM` użyć kodowania zamiast [#5369](https://github.com/PowerShell/PowerShell/issues/5369) ASCII

Poprzednie kodowanie, ASCII (7-bitowy), spowoduje niepoprawne zmiany w danych wyjściowych w niektórych przypadkach. Ta zmiana ma na celu `UTF-8 NoBOM` ustawienie domyślne, które zachowuje dane wyjściowe Unicode z kodowaniem obsługiwanym przez większość narzędzi i systemów operacyjnych.

### <a name="remove-allscope-from-most-default-aliases-5268httpsgithubcompowershellpowershellissues5268"></a>Usuń `AllScope` z większości domyślnych aliasów [#5268](https://github.com/PowerShell/PowerShell/issues/5268)

Aby przyspieszyć tworzenie zakresu, `AllScope` został usunięty z większości domyślnych aliasów. `AllScope`pozostawiono dla kilku często używanych aliasów, w których wyszukiwanie było szybsze.

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113httpsgithubcompowershellpowershellissues5113"></a>`-Verbose`i `-Debug` nie zastępują `$ErrorActionPreference` już [#5113](https://github.com/PowerShell/PowerShell/issues/5113)

Wcześniej, jeśli `-Verbose` lub `-Debug` zostały określone, overrode zachowanie `$ErrorActionPreference`. Ta zmiana `-Verbose` `-Debug` nie wpływa już na zachowanie programu `$ErrorActionPreference`.

## <a name="cmdlet-changes"></a>Zmiany poleceń cmdlet

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320httpsgithubcompowershellpowershellissues5320"></a>Wywołanie metody Invoke-RestMethod nie zwraca użytecznych informacji, gdy nie są zwracane żadne dane. [#5320](https://github.com/PowerShell/PowerShell/issues/5320)

Gdy interfejs API zwraca tylko `null`, wywołanie metody Invoke-RestMethod było serializowane jako ciąg `"null"` zamiast `$null`. Ta zmiana naprawia logikę w `Invoke-RestMethod` programie, aby prawidłowo serializować prawidłowy literał JSON `null` o pojedynczej wartości jako `$null`.

### <a name="remove--protocol-from--computer-cmdlets-5277httpsgithubcompowershellpowershellissues5277"></a>Usuń `-Protocol` z`*-Computer` poleceń cmdlet [#5277](https://github.com/PowerShell/PowerShell/issues/5277)

Ze względu na problemy z usługami zdalnymi RPC w programie CoreFX (zwłaszcza na platformach innych niż Windows) i zapewnianie spójnego środowiska komunikacji `-Protocol` zdalnej w programie PowerShell, `\*-Computer` parametr został usunięty z poleceń cmdlet. Model DCOM nie jest już obsługiwany w przypadku komunikacji zdalnej. Następujące polecenia cmdlet obsługują tylko obsługę zdalną usługi WSMAN:

- Zmień nazwę komputera
- Polecenie Restart-Computer
- Zatrzymaj komputer

### <a name="remove--computername-from--service-cmdlets-5090httpsgithubcompowershellpowershellissues5094"></a>Usuń `-ComputerName` z`*-Service` poleceń cmdlet [#5090](https://github.com/PowerShell/PowerShell/issues/5094)

Aby zapewnić spójne użycie PSRP, `-ComputerName` parametr został usunięty z `*-Service` poleceń cmdlet.

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197httpsgithubcompowershellpowershellissues5197"></a>Popraw `Get-Item -LiteralPath a*b` , `a*b` Jeśli w rzeczywistości nie istnieje, aby zwracać błąd [#5197](https://github.com/PowerShell/PowerShell/issues/5197)

Wcześniej, `-LiteralPath` pod warunkiem, że symbol wieloznaczny `-Path` będzie traktowany tak samo jak i, jeśli symbol wieloznaczny nie znalazł żadnych plików, zostanie on dyskretnie zakończony. Poprawne zachowanie powinno być literałem, dlatego jeśli plik nie istnieje, powinien wystąpić `-LiteralPath` błąd. Zmiana ma na celu traktowanie symboli wieloznacznych używanych z `-Literal` jako literału.

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134httpsgithubcompowershellpowershellissues5134"></a>`Import-Csv`należy stosować `PSTypeNames` podczas importowania, gdy informacje o typie znajdują się w [#5134](https://github.com/PowerShell/PowerShell/issues/5134) CSV

Wcześniej obiekty eksportowane przy użyciu `Export-CSV` programu `TypeInformation` z zaimportowanym programem `ConvertFrom-Csv` nie zachowały informacji o typie. Ta zmiana powoduje dodanie informacji o typie `PSTypeNames` do elementu członkowskiego, jeśli jest on dostępny z pliku CSV.

### <a name="-notypeinformation-should-be-default-on-export-csv-5131httpsgithubcompowershellpowershellissues5131"></a>`-NoTypeInformation`powinien być wartością domyślną `Export-Csv` na [#5131](https://github.com/PowerShell/PowerShell/issues/5131)

Ta zmiana została wprowadzona w celu uwzględnienia opinii klientów na temat domyślnego `Export-CSV` zachowania programu w celu dołączenia informacji o typie.

Wcześniej polecenie cmdlet przeprowadził komentarz jako pierwszy wiersz zawierający nazwę typu obiektu. Zmiana polega na tym, że to ustawienie jest domyślnie pomijane, ponieważ nie jest zrozumiałe dla większości narzędzi. Użyj `-IncludeTypeInformation` , aby zachować poprzednie zachowanie.

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112httpsgithubcompowershellpowershellissues5112"></a>Polecenia cmdlet sieci Web powinny ostrzegać, gdy `-Credential` są wysyłane za pośrednictwem nieszyfrowanych połączeń [#5112](https://github.com/PowerShell/PowerShell/issues/5112)

W przypadku korzystania z protokołu HTTP zawartość zawierająca hasła jest wysyłana jako zwykły tekst. Ta zmiana nie jest domyślnie dozwolona i zwraca błąd, jeśli poświadczenia są przesyłane w niezabezpieczony sposób. Użytkownicy mogą ominąć ten stan przy użyciu `-AllowUnencryptedAuthentication` przełącznika.

## <a name="api-changes"></a>Zmiany interfejsu API

### <a name="remove-addtypecommandbase-class-5407httpsgithubcompowershellpowershellissues5407"></a>Usuń `AddTypeCommandBase` [#5407](https://github.com/PowerShell/PowerShell/issues/5407) klasy

Klasa została usunięta z `Add-Type` w celu zwiększenia wydajności. `AddTypeCommandBase` Ta klasa jest używana tylko przez polecenie cmdlet Add-Type i nie powinna mieć wpływu na użytkowników.

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080httpsgithubcompowershellpowershellissues5080"></a>Ujednolicenie poleceń cmdlet z `-Encoding` parametrem do typu `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)

`-Encoding` Wartość`Byte` została usunięta z poleceń cmdlet dostawcy systemu plików. Nowy parametr `-AsByteStream`,,, jest teraz używany do określania, że strumień bajtów jest wymagany jako dane wejściowe lub że dane wyjściowe to strumień bajtów.

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055httpsgithubcompowershellpowershellissues5055"></a>Dodaj lepszy komunikat o błędzie dla pustego `-UFormat` i pustego parametru [#5055](https://github.com/PowerShell/PowerShell/issues/5055)

Wcześniej podczas przekazywania pustego ciągu formatu do `-UFormat`, pojawi się komunikat o błędzie niepomocowy. Dodano więcej opisowego błędu.

### <a name="clean-up-console-code-4995httpsgithubcompowershellpowershellissues4995"></a>Wyczyść kod konsoli [#4995](https://github.com/PowerShell/PowerShell/issues/4995)

Następujące funkcje zostały usunięte, ponieważ nie są obsługiwane w programie PowerShell Core i nie ma żadnych planów do dodania obsługi, ponieważ istnieją one ze względu na starsze przyczyny dla `-psconsolefile` środowiska Windows PowerShell: `-importsystemmodules` przełącznik i kod, przełącznik i kod oraz zmiana czcionki kodu.

### <a name="removed-runspaceconfiguration-support-4942httpsgithubcompowershellpowershellissues4942"></a>`RunspaceConfiguration` Usunięto [#4942](https://github.com/PowerShell/PowerShell/issues/4942) pomocy technicznej

Wcześniej w przypadku tworzenia środowiska programu PowerShell programowo przy użyciu interfejsu API można użyć starszej [`RunspaceConfiguration`][runspaceconfig] wersji lub nowszej [`InitialSessionState`][iss]. Ta zmiana została usunięta `RunspaceConfiguration` i obsługuje `InitialSessionState`tylko program.

[runspaceconfig]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923httpsgithubcompowershellpowershellissues4923"></a>`CommandInvocationIntrinsics.InvokeScript`Powiąż argumenty `$input` z `$args` zamiast [#4923](https://github.com/PowerShell/PowerShell/issues/4923)

Niepoprawna pozycja parametru spowodowała, że argumenty przechodzą jako dane wejściowe zamiast argumentów AS.

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903httpsgithubcompowershellpowershellissues4903"></a>Usuń nieobsługiwany `-showwindow` przełącznik `Get-Help` z [#4903](https://github.com/PowerShell/PowerShell/issues/4903)

`-showwindow`opiera się na platformie WPF, która nie jest obsługiwana w CoreCLR.

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866httpsgithubcompowershellpowershellissues4866"></a>Zezwalaj * do użycia w ścieżce rejestru dla `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)

Wcześniej, `-LiteralPath` pod warunkiem, że symbol wieloznaczny `-Path` będzie traktowany tak samo jak i, jeśli symbol wieloznaczny nie znalazł żadnych plików, zostanie on dyskretnie zakończony. Poprawne zachowanie powinno być literałem, dlatego jeśli plik nie istnieje, powinien wystąpić `-LiteralPath` błąd. Zmiana ma na celu traktowanie symboli wieloznacznych używanych z `-Literal` jako literału.

### <a name="fix-set-service-failing-test-4802httpsgithubcompowershellpowershellissues4802"></a>Naprawianie `Set-Service` nieudanych prób [#4802](https://github.com/PowerShell/PowerShell/issues/4802) testowych

Wcześniej, jeśli `New-Service -StartupType foo` został użyty, `foo` został zignorowany, a usługa została utworzona przy użyciu pewnego domyślnego typu uruchomienia. Ta zmiana ma na celu jawne zgłoszenie błędu dla nieprawidłowego typu uruchomienia.

### <a name="rename-isosx-to-ismacos-4700httpsgithubcompowershellpowershellissues4700"></a>Zmień `$IsOSX` nazwę `$IsMacOS` na [#4700](https://github.com/PowerShell/PowerShell/issues/4700)

Nazewnictwo w programie PowerShell powinno być zgodne z naszym nazewnictwem i być zgodne z użyciem firmy Apple macOS zamiast OSX. Jednak w celu zapewnienia czytelności i spójnego korzystania z wielkości liter w języku Pascalów.

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573httpsgithubcompowershellpowershellissues4573"></a>Wykonaj spójny komunikat o błędzie podczas przekazywania nieprawidłowego skryptu do pliku, lepszy błąd podczas przekazywania niejednoznacznego argumentu [#4573](https://github.com/PowerShell/PowerShell/issues/4573)

Zmień kody `pwsh.exe` zakończenia, aby dostosować je do Konwencji systemu UNIX

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302httpsgithubcompowershellpowershellissues4302-4303httpsgithubcompowershellpowershellissues4303"></a>Usuwanie poleceń cmdlet `Diagnostics`izmodułów `LocalAccount` . [#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)

Ze względu na nieobsługiwane `LocalAccounts` interfejsy API moduł `Counter` i polecenia cmdlet w `Diagnostics` module zostały usunięte do momentu znalezienia lepszego rozwiązania.

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036httpsgithubcompowershellpowershellissues4036"></a>Wykonanie skryptu programu PowerShell z parametrem bool nie działa [#4036](https://github.com/PowerShell/PowerShell/issues/4036)

Wcześniej przy użyciu **programu PowerShell. exe** (teraz **pwsh. exe**) do wykonywania skryptu programu PowerShell `-File` przy użyciu podanego `$true` sposobu nie można przekazać / `$false` jako wartości parametrów. `$true` Dodanoobsługęjakoprzeanalizowanych`$false` wartości do parametrów. / Wartości switch są również obsługiwane, ponieważ aktualnie udokumentowana składnia nie działa.

### <a name="remove-clrversion-property-from-psversiontable-4027httpsgithubcompowershellpowershellissues4027"></a>Usuń `ClrVersion` właściwość z `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)

`ClrVersion` WłaściwośćniejestprzydatnawCoreCLR,użytkownicykońcowiniepowinniużywaćtejwartości`$PSVersionTable` w celu określenia zgodności.

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019httpsgithubcompowershellpowershellissues4019"></a>Zmień parametr pozycyjny `powershell.exe` dla z `-Command` na [#4019](https://github.com/PowerShell/PowerShell/issues/4019) `-File`

Włącz Shebang użycie programu PowerShell na platformach innych niż Windows. Oznacza to, że w systemach opartych na systemie UNIX można utworzyć plik wykonywalny skryptu, który będzie automatycznie wywoływał program `pwsh`PowerShell, a nie jawnie wywoływanie. Oznacza to również, że można teraz `powershell foo.ps1` lub `powershell fooScript` bez określenia `-File`. Jednak ta zmiana wymaga, aby jawnie określić `-c` lub `-Command` Kiedy próbujesz wykonać takie `powershell.exe Get-Command`czynności.

### <a name="implement-unicode-escape-parsing-3958httpsgithubcompowershellpowershellissues3958"></a>Implementuj [#3958](https://github.com/PowerShell/PowerShell/issues/3958) analizy ucieczki Unicode

`` `u####``lub `` `u{####}`` jest konwertowany na odpowiedni znak Unicode. Aby wyprowadzić `` `u``literał, wyjdź z znacznika ucieczki:. ``` ``u```

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940httpsgithubcompowershellpowershellissues3940"></a>Zmień `New-ModuleManifest` [](https://github.com/PowerShell/PowerShell/issues/3940) kodowanie na naplatformachinnychniż`UTF8NoBOM` Windows #3940

Wcześniej program `New-ModuleManifest` tworzy manifesty psd1 w formacie UTF-16 z BOM, tworząc problem dla narzędzi systemu Linux. Ta zmiana powodująca zmianę kodowania `New-ModuleManifest` na wartość UTF (bez BOM) na platformach innych niż Windows.

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780httpsgithubcompowershellpowershellissues3780"></a>Zapobiegaj `Get-ChildItem` powtarzaniu w linków symbolicznych (#1875). [#3780](https://github.com/PowerShell/PowerShell/issues/3780)

Ta zmiana `Get-ChildItem` powoduje dalsze wprowadzenie do systemu UNIX `ls -r` i poleceń natywnych `dir /s` systemu Windows. Podobnie jak wspomniane polecenia, polecenie cmdlet wyświetla symboliczne linki do katalogów znalezionych podczas rekursji, ale nie odnosi się do nich.

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706httpsgithubcompowershellpowershellissues3706"></a>Napraw `Get-Content -Delimiter` , aby nie uwzględnić ogranicznika w zwróconych wierszach [#3706](https://github.com/PowerShell/PowerShell/issues/3706)

Wcześniej dane wyjściowe podczas korzystania z `Get-Content -Delimiter` programu były niespójne i niewygodne, ponieważ wymagały dalszej obróbki danych w celu usunięcia ogranicznika. Ta zmiana powoduje usunięcie ogranicznika w zwracanych wierszach.

### <a name="implement-format-hex-in-c-3320httpsgithubcompowershellpowershellissues3320"></a>Implementuj format-hex w C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320)

`-Raw` Parametr jest teraz "No-op" (w tym przypadku nie robi nic). Przechodzenie do przodu wszystkie dane wyjściowe będą wyświetlane z rzeczywistą reprezentacją liczb, które obejmują wszystkie bajty dla tego typu (co `-Raw` jest formalnie wykonywane przed tą zmianą).

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319httpsgithubcompowershellpowershellissues3319"></a>Program PowerShell jako powłoka domyślna nie działa z poleceniem skryptu [#3319](https://github.com/PowerShell/PowerShell/issues/3319)

W systemie UNIX jest to Konwencja dla powłok, które mają być `-i` akceptowane dla powłoki interaktywnej, a wiele narzędzi oczekuje na`script` to zachowanie (na przykład, i podczas ustawiania programu PowerShell jako powłoki domyślnej) i `-i` wywołuje powłokę z przełącznikiem. Ta zmiana jest przerywana `-i` , ponieważ wcześniej może zostać użyta jako krótka do dopasowania `-inputformat`, która teraz musi `-in`być.

### <a name="typo-fix-in-get-computerinfo-property-name-3167httpsgithubcompowershellpowershellissues3167"></a>Poprawka literówki w nazwie właściwości get-ComputerInfo [#3167](https://github.com/PowerShell/PowerShell/issues/3167)

`BiosSerialNumber`był błędnie wpisany jako `BiosSeralNumber` i został zmieniony na poprawną pisownię.

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024httpsgithubcompowershellpowershellissues3024"></a>Polecenia `Get-StringHash` cmdlet `Get-FileHash` Add i [#3024](https://github.com/PowerShell/PowerShell/issues/3024)

Ta zmiana polega na tym, że niektóre algorytmy wyznaczania wartości skrótu nie są obsługiwane przez CoreFX, w związku z czym nie są już dostępne:

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672httpsgithubcompowershellpowershellissues2672"></a>Dodaj weryfikację `Get-*` w poleceniach cmdlet, gdzie przekazywanie $NULL zwraca wszystkie obiekty zamiast błędu [#2672](https://github.com/PowerShell/PowerShell/issues/2672)

Przekazanie `$null` do dowolnego z następujących elementów spowoduje zgłoszenie błędu:

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

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482httpsgithubcompowershellpowershellissues2482"></a>Dodano obsługę rozszerzonego formatu W3C plików dziennika `Import-Csv` w [#2482](https://github.com/PowerShell/PowerShell/issues/2482)

`Import-Csv` Wcześniej polecenie cmdlet nie może być używane do bezpośredniego importowania plików dziennika w rozszerzonym formacie dziennika W3C, a dodatkowa akcja powinna być wymagana. Ta zmiana powoduje, że rozszerzony format dziennika W3C jest obsługiwany.

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035httpsgithubcompowershellpowershellissues2035"></a>Problem z `ValueFromRemainingArguments` wiązaniem parametru w funkcjach PS [#2035](https://github.com/PowerShell/PowerShell/issues/2035)

`ValueFromRemainingArguments`teraz zwraca wartości jako tablicę zamiast pojedynczej wartości, która sama jest tablicą.

### <a name="buildversion-is-removed-from-psversiontable-1415httpsgithubcompowershellpowershellissues1415"></a>`BuildVersion`został usunięty z `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)

Usuń właściwość z `$PSVersionTable`. `BuildVersion` Ta właściwość została powiązana z wersją kompilacji systemu Windows. Zamiast tego zalecamy korzystanie `GitCommitId` z programu w celu pobrania dokładnej wersji kompilacji programu PowerShell Core.

### <a name="changes-to-web-cmdlets"></a>Zmiany w poleceniach cmdlet sieci Web

Podstawowy interfejs API platformy .NET dla poleceń cmdlet sieci Web został zmieniony na `System.Net.Http.HttpClient`. Ta zmiana zapewnia wiele korzyści. Jednak ta zmiana wraz z brakiem współdziałania z programem Internet Explorer spowodowała kilka istotnych zmian w ramach `Invoke-WebRequest` systemów `Invoke-RestMethod`i.

- `Invoke-WebRequest`obsługuje teraz wyłącznie podstawowe analizy kodu HTML. `Invoke-WebRequest`zawsze zwraca `BasicHtmlWebResponseObject` obiekt. Właściwości `ParsedHtml` i`Forms` zostały usunięte.
- `BasicHtmlWebResponseObject.Headers`wartości są teraz `String[]` `String`zamiast.
- `BasicHtmlWebResponseObject.BaseResponse`jest teraz `System.Net.Http.HttpResponseMessage` obiektem.
- Właściwość wyjątków poleceń cmdlet sieci Web jest `System.Net.Http.HttpResponseMessage` teraz obiektem. `Response`
- Ścisłe analizowanie nagłówka RFC jest teraz domyślnie dla `-Headers` parametru `-UserAgent` i. Można to pominąć za pomocą `-SkipHeaderValidation`.
- `file://`i `ftp://` schematy identyfikatorów URI nie są już obsługiwane.
- `System.Net.ServicePointManager`ustawienia nie są już honorowane.
- Na macOS nie ma obecnie dostępnego uwierzytelniania opartego na certyfikatach.
- `-Credential` Użycie zapośrednictwemidentyfikatoraURI`http://` spowoduje wystąpienie błędu. Użyj identyfikatora URI lub podaj parametr `-AllowUnencryptedAuthentication` , aby pominąć błąd. `https://`
- `-MaximumRedirection`teraz generuje błąd kończący, gdy próba przekierowania przekroczy podany limit zamiast zwracać wyniki ostatniego przekierowania.
