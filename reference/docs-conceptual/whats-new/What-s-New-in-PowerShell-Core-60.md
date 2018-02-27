# <a name="whats-new-in-powershell-core-60"></a>Co to jest nowa w programie PowerShell Core 6.0

[PowerShell Core 6.0] [ github] jest nowa wersja programu PowerShell, który to platform (Windows, system macOS i Linux), open source i opracowane w heterogenicznych środowiskach i chmura hybrydowa.

## <a name="moved-from-net-framework-to-net-core"></a>Przeniesione z .NET Framework do platformy .NET Core

Używa programu PowerShell Core [.NET Core 2.0][] jako jego obsługi.
.NET core 2.0 umożliwia Core programu PowerShell do pracy na wielu platformach (z systemem Windows, system macOS i Linux).
Podstawowe programu PowerShell udostępnia również zestaw interfejsu API oferowanych przez .NET Core 2.0 do użycia polecenia cmdlet programu PowerShell i skryptów.

Środowisko Windows PowerShell umożliwia środowiska uruchomieniowego .NET Framework hosta aparatu programu PowerShell.
Oznacza to, że programu Windows PowerShell udostępnia zestawu interfejsów API oferowane przez program .NET Framework.

Interfejsy API współużytkowane .NET Core i .NET Framework są definiowane jako część [.NET Standard][].

Aby uzyskać więcej informacji na to wpływ na zgodność skryptu modułu podstawowego środowiska PowerShell i programu Windows PowerShell, zobacz [Backwards zgodności przy użyciu programu Windows PowerShell](#backwards-compatibility-with-windows-powershell).

## <a name="support-for-macos-and-linux"></a>Obsługa macOS i Linux

PowerShell oficjalnie obsługuje teraz system macOS i Linux, w tym:

- Windows 7, 8.1 i 10
- Windows Server 2008 R2, 2012 R2, 2016
- [Windows Server częściowo roczna kanału][semi-annual]
- Ubuntu 14.04 i 16.04, 17.04
- Debian 8.7 + i 9
- CentOS 7
- Red Hat Enterprise Linux 7
- OpenSUSE 42.2
- Fedora 25, 26
- macOS 10.12+

Naszej społeczności przyczynił się również pakiety dla następujących platform, ale nie jest oficjalnie obsługiwana:

- Arch Linux
- Kali Linux
- AppImage (działa na wielu platformach systemu Linux)

Mamy także eksperymentalne wersjach (nieobsługiwany) dla następujących platform:

- Systemu Windows na ARM32/ARM64
- Raspbian (Stretch)

Liczba zmian wprowadzono w podstawowej programu PowerShell w wersji 6.0 Aby lepiej współpracuje w systemach z systemem innym niż Windows.
Niektóre z nich są istotne zmiany, które miały wpływ na system Windows.
Inne są tylko występuje lub jest stosowane w urządzeniach z systemem innym niż Windows PowerShell podstawowych.

- Dodano obsługę globbing polecenia natywnego na platformach systemu Unix.
- `more` Funkcji szanuje systemu Linux `$PAGER` i domyślnie ustawiany na `less`.
  Oznacza to, mogą teraz używać symboli wieloznacznych z natywnego plików binarnych/poleceń (na przykład `ls *.txt`). (#3463)
- Automatycznie wyjściowym kończyć się ukośnikiem, podczas pracy z argumentami polecenia macierzystego. (#4965)
- Ignoruj `-ExecutionPolicy` przełącznika podczas uruchamiania programu PowerShell na platformach z systemem innym niż Windows, ponieważ skrypt podpisywania nie jest obecnie obsługiwany. (#3481)
- Stałe ConsoleHost uwzględnić `NoEcho` na platformach systemu Unix. (#3801)
- Stałe `Get-Help` do obsługi dopasowanie wzorca bez uwzględniania wielkości liter na platformach systemu Unix. (#3852)
- `powershell` strony Man dodawane do pakietu

### <a name="logging"></a>Rejestrowanie

Na macOS, PowerShell korzysta z natywnego `os_log` interfejsów API do logowania do firmy Apple [unified systemu rejestrowania][os_log].
W systemie Linux, korzysta z programu PowerShell [Syslog][], rozwiązania uniwersalnych rejestrowania.

### <a name="filesystem"></a>System plików

Liczba zmian wprowadzono w macOS i Linux obsługują znaków filename tradycyjnie nie są obsługiwane w systemie Windows:

- Ścieżki do polecenia cmdlet są teraz pochodzącego od dowolnego ukośnika (zarówno / i \ pracy jako separator katalogu)
- Specyfikacja katalogu Base XDG jest teraz wzięty pod uwagę i używany domyślnie:
  - Ścieżka profilu systemu Linux/macOS znajduje się pod adresem `~/.config/powershell/profile.ps1`
  - Historia ścieżkę zapisu znajduje się pod adresem `~/.local/share/powershell/PSReadline/ConsoleHost_history.txt`
  - Ścieżka modułu użytkownika znajduje się w `~/.local/share/powershell/Modules`
- Obsługa nazwy plików i folderów zawierających znakiem dwukropka w systemach Unix. (#4959)
- Obsługa skryptów nazwy lub pełnych ścieżek, które mają przecinkami. (#4136) (Podziękowania dla @TimCurwick!)
- Wykryj, kiedy `-LiteralPath` służy do pomijania rozwijanie symbolu wieloznacznego dla poleceń cmdlet nawigacji. (#5038)
- Zaktualizowano `Get-ChildItem` do pracy typu więcej * nix `ls -R` i systemu Windows `DIR /S` natywnych poleceń.
  `Get-ChildItem` teraz zwraca linki symboliczne podczas cyklicznego wyszukiwania, a nie Szukaj katalogi który tych docelowym łącza. (#3780)

### <a name="case-sensitivity"></a>Uwzględniana wielkość liter

Linux i macOS zwykle jest rozróżniana wielkość liter, podczas gdy system Windows działa bez uwzględniania wielkości liter przy zachowaniu case.
Ogólnie rzecz biorąc programu PowerShell jest uwzględniana wielkość liter.

Na przykład zmienne środowiskowe są z uwzględnieniem wielkości liter na macOS i Linux, więc wielkość liter `PSModulePath` normalizowane zmiennej środowiskowej. (#3255) `Import-Module` nie uwzględnia wielkości liter podczas korzystania z ścieżka pliku można określić nazwy modułu. (#5097)

## <a name="support-for-side-by-side-installations"></a>Obsługa instalacji side-by-side

Podstawowe programu PowerShell jest zainstalowane, skonfigurowane i wykonać oddzielnie z poziomu środowiska Windows PowerShell.
Podstawowe programu PowerShell ma pakietu ZIP "portable".
Przy użyciu pakietu ZIP, można zainstalować dowolną liczbę wersji dowolne miejsce na dysku, włącznie z lokalnych do aplikacji, która przyjmuje programu PowerShell jako zależność.
Instalacja Side-by-side ułatwia przetestować nową wersję programu PowerShell i Migrowanie istniejących skryptów wraz z upływem czasu.
Side-by-side umożliwia również zapewnienia zgodności jako skrypty można przypiąć do określonej wersji, których wymagają.

> [!NOTE]
> Domyślnie Instalator MSI na podstawie w systemie Windows powoduje instalację aktualizacji w miejscu.
>

## <a name="renamed-powershellexe-to-pwshexe"></a>Zmieniona `powershell(.exe)` do `pwsh(.exe)`

Nazwa binarna podstawowych programu PowerShell została zmieniona z `powershell(.exe)` do `pwsh(.exe)`.
Ta zmiana umożliwia deterministyczne użytkownikom na uruchamianie programu PowerShell Core na maszynach do obsługi środowiska Windows PowerShell side-by-side i instalacji podstawowej programu PowerShell.
`pwsh` jest również znacznie krótsze i łatwiejsze do typu.

Dodatkowych zmian `pwsh(.exe)` z `powershell.exe`:

- Zmieniony pierwszy parametr pozycyjny z `-Command` do `-File`.
  Ta zmiana poprawki użycie `#!` (alias jako shebang) w skryptów programu PowerShell, które są wykonywane z powłoki-PowerShell na platformach z systemem innym niż Windows.
  Oznacza to również, że można uruchomić poleceń, takich jak `pwsh foo.ps1` lub `pwsh fooScript` bez określania `-File`.
  Jednak ta zmiana wymaga jawnego określenia `-c` lub `-Command` podczas próby uruchomienia poleceń, takich jak `pwsh.exe -Command Get-Command`. (#4019)
- Akceptuje podstawowe programu PowerShell `-i` (lub `-Interactive`) przełącznik, aby wskazać interakcyjne powłoki. (#3558) Dzięki temu programu PowerShell mają być używane jako domyślną powłokę na platformach systemu Unix.
- Usunąć parametry `-importsystemmodules` i `-psconsoleFile` z `pwsh.exe`. (#4995)
- Zmienione `pwsh -version` i wbudowany system pomocy dla `pwsh.exe` , aby były wyrównane z innych narzędzi natywnego. (#4958 & #4931) (Dziękujemy @iSazonov)
- Nieprawidłowy argument komunikaty o błędach `-File` i `-Command` i zgodne ze standardami Unix kody zakończenia (#4573)
- Dodaje `-WindowStyle` parametru w systemie Windows. (#4573) Podobnie instalacji pakietu aktualizacji na platformach systemu Windows są aktualizacje w miejscu.

## <a name="backwards-compatibility-with-windows-powershell"></a>Zapewnienia zgodności z programu Windows PowerShell

Celem Core programu PowerShell jest pozostaje jako zgodna, jak to możliwe przy użyciu programu Windows PowerShell.
Używa programu PowerShell Core [.NET Standard][] 2.0 w celu zapewnienia zgodności plików binarnych z istniejących zestawów platformy .NET.
Wiele modułów programu PowerShell są zależne od tych zestawów (często razy dll), więc .NET Standard pozwala na kontynuowanie pracy z platformą .NET Core.
Podstawowe programu PowerShell obejmuje również heurystyki do przeszukania folderów, dobrze znanego — na przykład gdy Global Assembly Cache zazwyczaj znajduje się na dysku — można znaleźć zależności biblioteki DLL programu .NET Framework.

Użytkownik może dowiedzieć się więcej o .NET Standard na [blogu .NET][], w tym [YouTube][] wideo, a przez to [— często zadawane pytania][] w witrynie GitHub.

Starań zostały wprowadzone, aby upewnić się, że moduły programu PowerShell języka i "wbudowane" (takie jak `Microsoft.PowerShell.Management`, `Microsoft.PowerShell.Utility`, itd.) działać w identyczny sposób jak w programie Windows PowerShell.
W wielu przypadkach za pomocą społeczności dodaliśmy nowe funkcje i poprawki do tych poleceń cmdlet.
W niektórych przypadkach, ze względu na brakującą zależność w niższych warstwach .NET funkcja została usunięta lub jest niedostępna.

Większość modułów, które są dostarczane jako część systemu Windows (na przykład `DnsClient`, `Hyper-V`, `NetTCPIP`, `Storage`, itd.) i innych produktów firmy Microsoft, w tym Azure i pakietu Office nie zostały jeszcze *jawnie* systemie. Jeszcze sieci podstawowej.
Zespół programu PowerShell współpracuje z tych grup produktów i zespołów, aby to zweryfikować i portu ich istniejących modułów programu PowerShell Core.
Przy użyciu platformy .NET Standard i [CDXML][]wiele z tych tradycyjnych modułów środowiska Windows PowerShell wydaje się do pracy w podstawowej programu PowerShell, ale nie zostały one oficjalnie zatwierdzone i oficjalnie nie są obsługiwane.

Instalując [ `WindowsPSModulePath` ] [ windowspsmodulepath] modułu, można używać programu Windows PowerShell modułów przez dodanie programu Windows PowerShell `PSModulePath` do podstawowego środowiska PowerShell `PSModulePath`.

Najpierw zainstaluj `WindowsPSModulePath` modułu z galerii programu PowerShell:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin 
Install-Module WindowsPSModulePath -Force
```

Po zainstalowaniu tego modułu, uruchom `Add-WindowsPSModulePath` polecenia cmdlet programu Windows PowerShell Dodaj `PSModulePath` na rdzeń środowiska PowerShell:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="docker-support"></a>Obsługa docker

Podstawowe programu PowerShell dodaje obsługę kontenery Docker dla wszystkich głównych platform obsługujemy (w tym wiele dystrybucjach systemu Linux, Windows Server Core i Nano Server).

Aby uzyskać pełną listę, zapoznaj się tagi na [ `microsoft/powershell` w Centrum Docker][docker-hub].
Aby uzyskać więcej informacji na Docker i podstawowe programu PowerShell, zobacz [Docker][] w witrynie GitHub.

## <a name="ssh-based-powershell-remoting"></a>Usługi zdalne SSH na podstawie środowiska PowerShell

Działa teraz protokołu komunikacji zdalnej programu PowerShell (PSRP) przy użyciu protokołu Secure Shell (SSH), oprócz tradycyjnego PSRP na podstawie usługi WinRM.

Oznacza to, że można użyć poleceń cmdlet, takich jak `Enter-PSSession` i `New-PSSession` i Uwierzytelnij się przy użyciu protokołu SSH.
Wystarczy, że jest rejestrowania programu PowerShell jako podsystemu z serwerem SSH na podstawie OpenSSH i służy istniejącą opartego na SSH uwierzytelniania mechanizmów (takie jak hasła lub kluczy prywatnych) w przypadku tradycyjnych `PSSession` semantyki.

Aby uzyskać więcej informacji na temat konfigurowania za pomocą opartego na SSH remoting, zobacz [komunikacji zdalnej programu PowerShell za pomocą protokołu SSH][ssh-remoting].

## <a name="default-encoding-is-utf-8-without-a-bom"></a>Domyślnym kodowaniem jest UTF-8 bez BOM

W przeszłości, poleceń cmdlet programu Windows PowerShell, takich jak `Get-Content`, `Set-Content` używać różnych kodowań, takie jak kodowanie ASCII i UTF-16.
Wariancje w wartością domyślną kodowania jest utworzenia problemów Mieszanie poleceń cmdlet bez określania opcji kodowania.

Platformy systemu Windows nie używać tradycyjnie UTF-8 bez znacznik kolejności bajtów (BOM) jako domyślne kodowanie plików tekstowych.
Przenoszenie od UTF-16, jak i do kodowania UTF-8 bez BOM są więcej aplikacji systemu Windows i narzędzia.
Podstawowe programu PowerShell zmienia domyślnym kodowaniem jest zgodny z ekosystemami szerszych.

To oznacza, że wszystkie polecenia cmdlet wbudowanych używające `-Encoding` Użyj parametru `UTF8NoBOM` wartości domyślne.
Zmiana ta dotyczy następujących poleceń cmdlet:

- Add-Content
- Export-Clixml
- Export-Csv
- Export-PSSession
- Format szesnastkowy
- Get-Content
- Import-Csv
- New-ModuleManifest
- Pliku wyjściowego
- Wybierz parametry
- Wyślij MailMessage
- Set-Content

Te polecenia cmdlet również zostały zaktualizowane, aby `-Encoding` powszechnie akceptuje parametr `System.Text.Encoding`.

Wartość domyślna `$OutputEncoding` również została zmieniona na UTF-8.

Najlepszym rozwiązaniem, należy jawnie ustawić kodowania w skrypty przy użyciu `-Encoding` parametr, aby utworzyć deterministyczne zachowanie różnych platform.

## <a name="support-backgrounding-of-pipelines-with-ampersand--3360"></a>Obsługuje backgrounding dla potoków z handlowego "i" (`&`) (#3360)

Umieszczanie `&` na końcu potoku powoduje, że potoku do uruchamiania jako zadanie programu PowerShell.
Gdy potoku jest backgrounded, jest zwracany obiektu zadania.
Po uruchomieniu potoku jako zadanie, wszystkie standardowe `*-Job` można użyć poleceń cmdlet do zarządzania zadaniem.
Zmienne (nie dotyczy określonego procesu zmienne) używane w potoku są automatycznie kopiowane do zadania tak `Copy-Item $foo $bar &` po prostu działa.
Zadanie jest również uruchamiane w bieżącym katalogu zamiast katalogu macierzystego użytkownika.
Aby uzyskać więcej informacji o zadaniach programu PowerShell, zobacz [about_Jobs](https://msdn.microsoft.com/powershell/reference/6/about/about_jobs).

## <a name="semantic-versioning"></a>Wersjonowania semantycznego

- Wprowadzone `SemanticVersion` zgodny z `SemVer 2.0`. (#5037) (Dziękujemy @iSazonov!)
- Zmienić domyślne `ModuleVersion` w `New-ModuleManifest` do `0.0.1` , aby były wyrównane z programu SemVer. (#4842) (Dziękujemy @LDSpits)
- Dodaje `semver` jako typ akceleratora dla `System.Management.Automation.SemanticVersion`. (#4142) (Podziękowania dla @oising!)
- Włączone porównanie `SemanticVersion` wystąpienia i `Version` wystąpienia, który jest tworzony tylko z `Major` i `Minor` wartości wersji.

## <a name="language-updates"></a>Języki aktualizacji

- Implementuje specjalne Unicode podczas analizowania, dzięki czemu użytkownicy mogą używać znaków Unicode jako argumenty, ciągi lub nazwy zmiennej. (#3958) (Podziękowania dla @rkeithhill!)
- Dodano nowe znak ucieczki dla ESC: `` `e``
- Dodano obsługę konwertowanie wyliczenia do ciągów (#4318) (Dziękujemy @KirkMunro)
- Rzutowanie stałym pojedynczy element tablicy do kolekcji uniwersalnej. (#3170)
- Przeciążenie zakresu znaków dodany do `..` operatora, więc `'a'..'z'` zwraca znaki "a" do "z". (#5026) (Dziękujemy @IISResetMe!)
- Stałe przypisanie zmiennej nie zastąpić zmienne tylko do odczytu
- Wypychanie elementów automatycznych zmiennych lokalnych "DottedScopes", gdy dotting skrypt poleceń cmdlet (#4709)
- Włącz użycie opcji "Singleline, Multiline" w operatorze podziału (#4721) (Dziękujemy @iSazonov)

## <a name="engine-updates"></a>Aktualizacje aparatu

- `$PSVersionTable` ma cztery nowe właściwości:
  - `PSEdition`: Ta wartość jest równa `Core` Core środowiska PowerShell i `Desktop` na programie Windows PowerShell
  - `GitCommitId`: To jest identyfikator zatwierdzania Git gałęzi Git lub tagu, w którym został utworzony programu PowerShell.
    W wydanej kompilacji, prawdopodobnie będzie taka sama jak `PSVersion`.
  - `OS`: To jest zwrócony przez ciąg wersji systemu operacyjnego `[System.Runtime.InteropServices.RuntimeInformation]::OSDescription`
  - `Platform`: Ten błąd jest zwracany przez `[System.Environment]::OSVersion.Platform` ma ustawioną wartość `Win32NT` w systemie Windows, `MacOSX` na macOS, i `Unix` w systemie Linux.
- Usunięte `BuildVersion` właściwość z `$PSVersionTable`.
  Ta właściwość została silnie powiązany numer kompilacji systemu Windows.
  Zamiast tego zaleca się używanie `GitCommitId` można pobrać wersję kompilacji dokładne Core programu PowerShell. (#3877) (Podziękowania dla @iSazonov!)
- Usuń `ClrVersion` właściwość z `$PSVersionTable`.
  Ta właściwość nie ma znaczenia dla platformy .NET Core i tylko został zachowany przy .NET Core do określonych celów starszej wersji, które są nie stosuje się do programu PowerShell.
- Dodaje trzy nowe automatycznych zmiennych, aby określić, czy środowisko PowerShell jest uruchomiony w danej wersji systemu operacyjnego: `$IsWindows`, `$IsMacOs`, i `$IsLinux`.
- Dodaj `GitCommitId` do transparent Core programu PowerShell.
  Teraz nie trzeba uruchomić `$PSVersionTable` zaraz po uruchomieniu programu PowerShell, aby pobrać wersję! (#3916) (Podziękowania dla @iSazonov!)
- Dodawanie pliku konfiguracji JSON o nazwie `powershell.config.json` w `$PSHome` do przechowywania niektórych ustawień wymagany czas uruchamiania (np. `ExecutionPolicy`).
- Nie należy blokować potoku podczas uruchamiania systemu Windows EXE
- Włączone wyliczenie COM kolekcji. (#4553)

## <a name="cmdlet-updates"></a>Polecenia cmdlet aktualizacji

### <a name="new-cmdlets"></a>Nowe polecenia cmdlet

- Dodaj `Get-Uptime` do `Microsoft.PowerShell.Utility`.
- Dodaj `Remove-Alias` polecenia. (#5143) (Dziękujemy @PowershellNinja!)
- Dodaj `Remove-Service` do modułu. (#4858) (Dziękujemy @joandrsn!)

### <a name="web-cmdlets"></a>Polecenia cmdlet sieci Web

- Dodaj obsługę uwierzytelniania certyfikatów dla polecenia cmdlet sieci web. (#4646) (Dziękujemy @markekraus)
- Dodaj obsługę nagłówki zawartości do polecenia cmdlet sieci web. (#4494 & #4640) (Dziękujemy @markekraus)
- Dodaj obsługę wielu nagłówka łącze do polecenia cmdlet sieci Web. (#5265) (Dziękujemy @markekraus!)
- Obsługuje podział na strony łącze nagłówka w poleceniach cmdlet sieci web (#3828)
  - Aby uzyskać `Invoke-WebRequest`, gdy odpowiedź zawiera nagłówek łącze utworzymy właściwości RelationLink jako słownik reprezentujący adresy URL i `rel` atrybutów i upewnij się, adresy URL są bezwzględne ułatwiają deweloperom stosowanie.
  - Dla `Invoke-RestMethod`, gdy odpowiedź zawiera nagłówek łącze uwidaczniamy `-FollowRelLink` przełącznik, aby automatycznie wykonać `next` `rel` łącza dopóki już nie istnieją, lub raz możemy trafień opcjonalny `-MaximumFollowRelLink` wartość parametru.
- Dodaj `-CustomMethod` parametru polecenia cmdlet sieci web umożliwiające niestandardową metodę zleceń. (#3142) (Podziękowania dla @Lee303!)
- Dodaj `SslProtocol` obsługuje do polecenia cmdlet sieci Web. (#5329) (Dziękujemy @markekraus!)
- Dodaj Multipart pomocy technicznej do polecenia cmdlet sieci web. (#4782) (Dziękujemy @markekraus)
- Dodaj `-NoProxy` do polecenia cmdlet sieci web tak, aby zignorować one systemowe ustawienia proxy. (#3447) (Podziękowania dla @TheFlyingCorpse!)
- Użytkownik agenta sieci Web z poleceń cmdlet raportuje obecnie Platforma systemu operacyjnego (#4937) (Dziękujemy @LDSpits)
- Dodaj `-SkipHeaderValidation` przełączyć się do polecenia cmdlet sieci web do obsługi dodawania nagłówków bez sprawdzania poprawności wartość nagłówka. (#4085)
- Włącz polecenia cmdlet sieci web nie zweryfikuje prawidłowo HTTPS certyfikat serwera, jeśli jest to wymagane.
- Dodaj do polecenia cmdlet programu web parametry uwierzytelniania. (#5052) (Dziękujemy @markekraus)
  - Dodaj `-Authentication` zapewnia trzy opcje: Basic, OAuth i elementu nośnego.
  - Dodaj `-Token` można pobrać elementu nośnego token OAuth i elementu nośnego opcje.
  - Dodaj `-AllowUnencryptedAuthentication` Aby pominąć uwierzytelnianie udostępnionego dla dowolnego schemat transportu innego niż HTTPS.
- Dodaj `-ResponseHeadersVariable` do `Invoke-RestMethod` umożliwia przechwytywanie nagłówków odpowiedzi. (#4888) (Dziękujemy @markekraus)
- Napraw polecenia cmdlet sieci web do uwzględnienia w wyjątek odpowiedzi HTTP, gdy kod stanu odpowiedzi nie jest Powodzenie. (#3201)
- Zmień polecenia cmdlet programu web `UserAgent` z `WindowsPowerShell` do `PowerShell`. (#4914) (Dziękujemy @markekraus)
- Dodaj jawne `ContentType` wykrywanie do `Invoke-RestMethod` (#4692)
- Usuń polecenia cmdlet programu web `-SkipHeaderValidation` do pracy z niestandardowym nagłówki agenta użytkownika. (#4479 & #4512) (Dziękujemy @markekraus)

### <a name="json-cmdlets"></a>Polecenia cmdlet JSON

- Dodaj `-AsHashtable` do `ConvertFrom-Json` do zwrócenia `Hashtable` zamiast tego. (#5043) (Dziękujemy @bergmeister!)
- Użyj prettier formatujący `ConvertTo-Json` danych wyjściowych. (#2787) (Podziękowania dla @kittholland!)
- Dodaj `Jobject` wsparcia serializacji `ConvertTo-Json`. (#5141)
- Usuń `ConvertFrom-Json` do deserializacji tablicy ciągów z potoku, które razem utworzyć pełną ciągu JSON.
  To rozwiązanie niektórych przypadkach, gdy newlines spowoduje przerwanie JSON analizy. (#3823)
- Usuń `AliasProperty "Count"` zdefiniowane dla `System.Array`.
  Spowoduje to usunięcie nadmiarowe `Count` właściwości dla niektórych `ConvertFrom-Json` danych wyjściowych. (#3231) (Podziękowania dla @PetSerAl!)

### <a name="csv-cmdlets"></a>Polecenia cmdlet CSV

- Dodaj `PSTypeName` obsługę `Import-Csv` i `ConvertFrom-Csv`. (#5389) (Dziękujemy @markekraus!)
- Wprowadź `Import-Csv` obsługuje `CR`, `LF`, i `CRLF` wiersza jako ograniczników. (#5363) (Dziękujemy @iSazonov!)
- Wprowadź `-NoTypeInformation` domyślnej na `Export-Csv` i `ConvertTo-Csv`. (#5164) (Dziękujemy @markekraus)

### <a name="service-cmdlets"></a>Polecenia cmdlet usługi

- Dodaj właściwości `UserName`, `Description`, `DelayedAutoStart`, `BinaryPathName`, i `StartupType` do `ServiceController` obiekty zwrócone przez `Get-Service`. (#4907) (Dziękujemy @joandrsn)
- Dodaj funkcje konfigurowania poświadczeń dla `Set-Service` polecenia. (#4844) (Dziękujemy @joandrsn)

### <a name="other-cmdlets"></a>Inne polecenia cmdlet

- Dodaj parametr `Get-ChildItem` o nazwie `-FollowSymlink` który przechodzi przez łączy symbolicznych na żądanie z sprawdza, czy łącze pętle. (#4020)
- Aktualizacja `Add-Type` do obsługi `CSharpVersion7`. (#3933) (Podziękowania dla @iSazonov)
- Usuń `Microsoft.PowerShell.LocalAccounts` modułu z powodu używania nieobsługiwany interfejsów API, aż do znalezienia lepszym rozwiązaniem. (#4302)
- Usuń `*-Counter` polecenia cmdlet w `Microsoft.PowerShell.Diagnostics` z powodu używania nieobsługiwany interfejsów API, aż do znalezienia lepszym rozwiązaniem. (#4303)
- Dodaj obsługę `Invoke-Item -Path <folder>`. (#4262)
- Dodaj `-Extension` i `-LeafBase` zmienia na `Split-Path` , dzięki czemu można podzielić ścieżek między rozszerzenie nazwy pliku i pozostałej części pliku. (#2721) (Podziękowania dla @powercode!)
- Dodaj parametry `-Top` i `-Bottom` do `Sort-Object` sortować górne i dolne N
- Udostępnianie procesu nadrzędnego procesu przez dodanie `CodeProperty "Parent"` do `System.Diagnostics.Process`. (#2850) (Podziękowania dla @powercode!)
- Użyj MB zamiast KB pamięci kolumn `Get-Process`
- Dodaj `-NoNewLine` przełączać `Out-String`. (#5056) (Dziękujemy @raghav710)
- `Move-Item` polecenie cmdlet będzie honorować `-Include`, `-Exclude`, i `-Filter` parametrów. (#3878)
- Zezwalaj na `*` do użycia w ścieżce rejestru dla `Remove-Item`. (#4866)
- Dodaj `-Title` do `Get-Credential` i ujednolicenie środowisko monitu o platformach.
- Dodaj `-TimeOut` parametr `Test-Connection`. (#2492)
- `Get-AuthenticodeSignature` polecenia cmdlet można teraz uzyskać sygnatury czasowej pliku podpisu. (#4061)
- Usuń nieobsługiwane `-ShowWindow` przejść z `Get-Help`. (#4903)
- Napraw `Get-Content -Delimiter` do zawiera ogranicznik w elementach tablicy zwracane (#3706) (Dziękujemy @mklement0)
- Dodaj `Meta`, `Charset`, i `Transitional` parametry `ConvertTo-HTML` (#4184) (Dziękujemy @ergo3114)
- Dodaj `WindowsUBR` i `WindowsVersion` właściwości `Get-ComputerInfo` wyników
- Dodaj `-Group` parametru `Get-Verb`
- Dodaj `ShouldProcess` obsługiwać `New-FileCatalog` i `Test-FileCatalog` (poprawki `-WhatIf` i `-Confirm`). (#3074) (Podziękowania dla @iSazonov!)
- Dodaj `-WhatIf` przełączyć się do `Start-Process` polecenia cmdlet (#4735) (Dziękujemy @sarithsutha)
- Dodaj `ValidateNotNullOrEmpty` zbyt wiele istniejących parametrów.

## <a name="tab-completion"></a>Uzupełnianie po naciśnięciu tabulatora

- Ulepszone wnioskowanie o typie w uzupełniania po naciśnięciu tabulatora na podstawie wartości zmiennych środowiska uruchomieniowego. (#2744) (Podziękowania dla @powercode!) Dzięki temu uzupełniania po naciśnięciu tabulatora w sytuacjach, takich jak:

  ```powershell
  $p = Get-Process
  $p | Foreach-Object Prio<tab>
  ```

- Dodaj kartę Hashtable uzupełnianie `-Property` z `Select-Object`. (#3625) (Podziękowania dla @powercode)
- Włącz Autouzupełnianie argument dla `-ExcludeProperty` i `-ExpandProperty` z `Select-Object`. (#3443) (Podziękowania dla @iSazonov!)
- Naprawa błędów w uzupełniania po naciśnięciu tabulatora, aby `native.exe --<tab>` wywołanie na ukończenie native. (#3633) (Podziękowania dla @powercode!)

## <a name="breaking-changes"></a>Fundamentalne zmiany

Dodaliśmy liczbę zmian, które psuły w podstawowej programu PowerShell w wersji 6.0.
Aby uzyskać więcej informacji na temat ich szczegóły, zobacz [fundamentalne zmiany w podstawowej programu PowerShell w wersji 6.0][breaking-changes].

## <a name="debugging"></a>Debugowanie

- Obsługa zdalnego debugowania step-in dla `Invoke-Command -ComputerName`. (#3015)
- Włącz integratora rejestrowanie debugowania w podstawowej programu PowerShell

## <a name="filesystem-updates"></a>Aktualizacje systemu plików

- Włącz użycie dostawcy Filesystem ze ścieżki UNC. ($4998)
- `Split-Path` teraz współpracuje z katalogów głównych UNC
- `cd` bez argumentów działa teraz jako `cd ~`
- Stałe środowiska PowerShell Core zezwalając na używanie ścieżek, które długie są więcej niż 260 znaków. (#3960)

## <a name="bug-fixes-and-performance-improvements"></a>Poprawki błędów i wydajności

Wprowadziliśmy *wiele* ulepszenia wydajności w programie PowerShell, w tym w chwili uruchomienia różnych wbudowanych i poleceń cmdlet interakcji z natywne pliki binarne.

Naprawiono również liczbę usterek w ramach podstawowych programu PowerShell.
Aby uzyskać pełną listę poprawek i zmian, zapoznaj się z naszym [wykaz zmian][] w witrynie GitHub.

## <a name="telemetry"></a>Telemetria

- PowerShell telemetrii Core 6.0 dodany host konsoli do raportu dwóch wartości (#3620):
  - Platforma systemu operacyjnego (`$PSVersionTable.OSDescription`)
  - dokładnej wersji środowiska PowerShell (`$PSVersionTable.GitCommitId`)

Jeśli chcesz zrezygnować z tego telemetrii, po prostu usuń `$PSHome\DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` lub Utwórz `POWERSHELL_TELEMETRY_OPTOUT` zmienną środowiskową o jedną z następujących wartości: `true`, `1` lub `yes`.
Usunięcie tego pliku lub tworzenia zmiennej pomija wszystkie dane telemetryczne nawet przed pierwszym uruchomieniu programu PowerShell.
Możemy również zaplanować na udostępnianie tych danych telemetrycznych i szczegółowych informacji, firma Microsoft zgromadzonych telemetrii w [pulpitu nawigacyjnego społeczności][community-dashboard].
Można znaleźć więcej informacji na temat sposobu wykorzystania przez nas w tym [wpis w blogu][telemetry-blog].

[github]: https://github.com/PowerShell/PowerShell
[.NET Core 2.0]: https://docs.microsoft.com/en-us/dotnet/core/
[.NET Standard]: https://docs.microsoft.com/en-us/dotnet/standard/net-standard
[os_log]: https://developer.apple.com/documentation/os/logging
[Syslog]: https://en.wikipedia.org/wiki/Syslog
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[breaking-changes]: https://github.com/PowerShell/PowerShell/tree/master/docs/BREAKINGCHANGES.md
[wykaz zmian]: https://github.com/PowerShell/PowerShell/tree/master/CHANGELOG.md
[community-dashboard]: https://aka.ms/PSGitHubBI
[telemetry-blog]: https://blogs.msdn.microsoft.com/powershell/2017/01/31/powershell-open-source-community-dashboard/
[.NET standard]: https://docs.microsoft.com/dotnet/standard/net-standard
[blogu .NET]: https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard
[YouTube]: https://www.youtube.com/watch?v=YI4MurjfMn8&list=PLRAdsfhKI4OWx321A_pr-7HhRNk7wOLLY
[— często zadawane pytania]: https://github.com/dotnet/standard/blob/master/docs/faq.md
[CDXML]: https://msdn.microsoft.com/en-us/library/jj542525(v=vs.85).aspx
[docker-hub]: https://hub.docker.com/r/microsoft/powershell/
[Docker]: https://github.com/PowerShell/PowerShell/tree/master/docker
[windowspsmodulepath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
