---
title: Co nowego w programie PowerShell Core 6.0
description: Nowe funkcje i zmiany w programie PowerShell Core 6.0
ms.date: 08/06/2018
ms.openlocfilehash: 83c104d838db9d86fe1d485e92245a9c8f2d2057
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62059019"
---
# <a name="whats-new-in-powershell-core-60"></a>Co nowego w programie PowerShell Core 6.0

[PowerShell Core 6.0] [ github] to nowa wersja programu PowerShell, który jest dla wielu platform (Windows, macOS i Linux), typu open source i dla środowisk heterogenicznych i chmura hybrydowa.

## <a name="moved-from-net-framework-to-net-core"></a>Przeniesione z .NET Framework i .NET Core

Używa programu PowerShell Core [.NET Core 2.0][] jako jego środowiska uruchomieniowego.
.NET core 2.0 umożliwia programu PowerShell Core pracować na wielu platformach (Windows, macOS i Linux).
Program PowerShell Core udostępnia również zestaw API oferowanych przez program .NET Core 2.0 do użycia w poleceń cmdlet programu PowerShell i skryptów.

Programu Windows PowerShell jest używane środowisko uruchomieniowe programu .NET Framework do hostowania aparatu programu PowerShell.
Oznacza to, że program Windows PowerShell udostępnia zestaw API oferowanych przez program .NET Framework.

Interfejsy API udostępniane między .NET Core i .NET Framework są zdefiniowane jako część [.NET Standard][].

Aby uzyskać więcej informacji na temat jak ma to wpływ na zgodność modułu skryptu programu PowerShell Core i programu Windows PowerShell, zobacz [Backwards zgodności przy użyciu programu Windows PowerShell](#backwards-compatibility-with-windows-powershell).

## <a name="support-for-macos-and-linux"></a>Obsługa systemu macOS i Linux

PowerShell oficjalnie obsługuje teraz systemach macOS i Linux, w tym:

- Windows 7, 8.1 i 10
- Windows Server 2008 R2, 2012 R2, 2016
- [Półroczny kanał dystrybucji systemu Windows Server][semi-annual]
- Ubuntu 14.04 i 16.04, 17.04
- Debian 8.7 + i 9
- CentOS 7
- Red Hat Enterprise Linux 7
- OpenSUSE 42.2
- Fedora 25, 26
- macOS 10.12+

Nasza społeczność współtworzonej również pakiety dla następujących platform, ale nie są oficjalnie obsługiwane:

- Arch Linux
- Kali Linux
- AppImage (działa na wielu platformach systemu Linux)

Mamy także eksperymentalnych wersji (nieobsługiwane) dla następujących platform:

- Windows na ARM32/ARM64
- Raspbian (Stretch)

Liczba zmian wprowadzono w programie PowerShell Core 6.0 aby stał się lepszą współpracę w systemach innych niż Windows.
Niektóre z nich są istotne zmiany, które również mają wpływ na Windows.
Inne są tylko obecne lub mające zastosowanie w instalacjach programu PowerShell Core innych niż Windows.

- Dodano obsługę polecenia natywnej obsługi symboli wieloznacznych na platformach Unix.
- `more` Funkcji szanuje Linux `$PAGER` i wartość domyślna to `less`.
  Oznacza to, można teraz używać symboli wieloznacznych przy użyciu natywnych plików binarnych/poleceń (na przykład `ls *.txt`). (#3463)
- Końcowy ukośnik odwrotny jest automatycznie poprzedzone znakiem zmiany znaczenia podczas pracy z argumentami polecenia natywnych. (#4965)
- Ignoruj `-ExecutionPolicy` Przełącz podczas uruchamiania programu PowerShell na platformach innych niż Windows, ponieważ podpisywanie skryptu nie jest obecnie obsługiwane. (#3481)
- Naprawiono ConsoleHost respektować `NoEcho` na platformach Unix. (#3801)
- Naprawiono `Get-Help` do obsługi na platformach Unix dopasowywania do wzorca bez uwzględniania wielkości liter. (#3852)
- `powershell` ataki typu man stronicowa dodawane do pakietu

### <a name="logging"></a>Rejestrowanie

W systemie macOS, programu PowerShell używa natywnych `os_log` interfejsów API do logowania do firmy Apple [ujednoliconego systemu rejestrowania][os_log].
W systemie Linux, korzysta z programu PowerShell [Syslog][], rozwiązanie wszechobecne rejestrowania.

### <a name="filesystem"></a>System plików

Wprowadzono szereg zmian w systemach macOS i Linux do obsługi znaków nazwy pliku nie tradycyjnie obsługiwana na Windows:

- Ścieżki do polecenia cmdlet są teraz niezależne od ukośnika (zarówno / i \ działają jako separator katalogu)
- Specyfikację katalogu Base XDG jest teraz przestrzegane i używany domyślnie:
  - Ścieżka profilu systemu Linux/macOS znajduje się w `~/.config/powershell/profile.ps1`
  - Historia ścieżka zapisu znajduje się w folderze `~/.local/share/powershell/PSReadline/ConsoleHost_history.txt`
  - Ścieżka modułu użytkownika znajduje się w `~/.local/share/powershell/Modules`
- Obsługa nazw plików i folderów zawierających znak dwukropek w systemach Unix. (#4959)
- Obsługa nazw skryptu lub pełnych ścieżek, które mają przecinkami. (#4136) (Dzięki [ @TimCurwick ](https://github.com/TimCurwick)!)
- Wykryć kiedy `-LiteralPath` służy do pomijania rozwijanie symbolu wieloznacznego dla poleceń cmdlet nawigacji. (#5038)
- Zaktualizowano `Get-ChildItem` pracę więcej podobne * nix `ls -R` i Windows `DIR /S` natywnych poleceń.
  `Get-ChildItem` teraz zwraca linki symboliczne podczas wyszukiwania cykliczne, a nie przeszukuje katalogi, te docelowy łącza. (#3780)

### <a name="case-sensitivity"></a>Rozróżnianie wielkości liter

Linux i macOS zwykle wielkości liter, podczas gdy Windows nie uwzględnia wielkości liter, zachowując przy tym przypadek.
Ogólnie rzecz biorąc programu PowerShell jest uwzględniana wielkość liter.

Na przykład, zmienne środowiskowe są uwzględniana wielkość liter w systemach macOS i Linux, więc wielkość liter `PSModulePath` normalizowane zmiennej środowiskowej. (#3255) `Import-Module` jest uwzględniana wielkość liter, gdy używane są ścieżki do pliku można określić nazwy modułu. (#5097)

## <a name="support-for-side-by-side-installations"></a>Obsługa instalacji side-by-side

Program PowerShell Core jest zainstalowane, skonfigurowane i wykonać oddzielnie, za pomocą programu Windows PowerShell.
Program PowerShell Core ma "przenośne" SPAKOWANY pakiet.
Przy użyciu pakietu ZIP, można zainstalować dowolną liczbę wersji dowolne miejsce na dysku, w tym lokalnych do aplikacji, która przyjmuje program PowerShell jako zależność.
Instalacja Side-by-side sprawia, że łatwiej testować nowe wersje programu PowerShell i Migrowanie istniejących skryptów wraz z upływem czasu.
Side-by-side umożliwia także wstecznej zgodności jak skrypty można przypiąć do określonych wersji, których potrzebują.

> [!NOTE]
> Domyślnie Instalatorze opartym na MSI na Windows wykonuje instalację aktualizacji w miejscu.
>

## <a name="renamed-powershellexe-to-pwshexe"></a>Zmieniono nazwę `powershell(.exe)` do `pwsh(.exe)`

Nazwa pliku binarnego dla programu PowerShell Core została zmieniona z `powershell(.exe)` do `pwsh(.exe)`.
Ta zmiana umożliwia deterministyczne użytkownikom na uruchamianie programu PowerShell Core na maszynach do obsługi instalacji programu PowerShell Core i side-by-side Windows PowerShell.
`pwsh` jest również znacznie krótsze i łatwiejsze do typu.

Dodatkowe zmiany do `pwsh(.exe)` z `powershell.exe`:

- Zmieniono pierwszy parametr pozycyjne z `-Command` do `-File`.
  Ta zmiana rozwiązuje użycie `#!` (zwane również jako shebang) w skryptach programu PowerShell, które są wykonywane z powłoki-PowerShell na platformach innych niż Windows.
  Oznacza to również, że można uruchamiać poleceń, takich jak `pwsh foo.ps1` lub `pwsh fooScript` bez określania `-File`.
  Jednak ta zmiana wymaga, że zostaną jawnie określone `-c` lub `-Command` podczas próby uruchomienia poleceń, takich jak `pwsh.exe -Command Get-Command`. (#4019)
- Program PowerShell Core akceptuje `-i` (lub `-Interactive`) przełącznik, aby wskazać interaktywnej powłoki. (#3558) Dzięki temu program PowerShell w celu można użyć jako domyślnej powłoki na platformach Unix.
- Usunąć parametry `-importsystemmodules` i `-psconsoleFile` z `pwsh.exe`. (#4995)
- Zmienione `pwsh -version` i wbudowaną Pomoc dotyczącą `pwsh.exe` dopasowanie z innymi narzędziami natywnych. (#4958 & #4931) (Dziękuję [ @iSazonov ](https://github.com/iSazonov))
- Komunikaty o błędach nieprawidłowy argument dla `-File` i `-Command` i zgodne z normami Unix kody zakończenia (#4573)
- Dodano `-WindowStyle` parametru na Windows. (#4573) Podobnie instalacji pakietu aktualizacji na platformach innych niż Windows są aktualizacje w miejscu.

## <a name="backwards-compatibility-with-windows-powershell"></a>Wstecznej zgodności przy użyciu programu Windows PowerShell

Celem programu PowerShell Core jest nadal jako zgodna, jak to możliwe przy użyciu programu Windows PowerShell.
Używa programu PowerShell Core [.NET Standard][] zapewniają zgodność binarną przy użyciu istniejących zestawów .NET w wersji 2.0.
Wiele modułów programu PowerShell są zależne od tych zestawów (często razy dll), dzięki czemu .NET Standard umożliwia kontynuowanie pracy z platformą .NET Core.
Program PowerShell Core obejmuje również heurystyki do przeszukania dobrze znanych folderów, — na przykład gdy Global Assembly Cache zazwyczaj znajduje się na dysku — można znaleźć zależności biblioteki DLL programu .NET Framework.

Temat można znaleźć więcej informacji na temat .NET Standard na [.NET Blog][], w tym [YouTube][] wideo i przy użyciu tego [FAQ][] w witrynie GitHub.

Zostały wprowadzone wszelkich starań, aby upewnić się, że język i "wbudowane" modułów programu PowerShell (takich jak `Microsoft.PowerShell.Management`, `Microsoft.PowerShell.Utility`, itp.) działać tak samo jak w programie Windows PowerShell.
W wielu przypadkach przy pomocy społeczności dodaliśmy nowe funkcje i poprawki do tych poleceń cmdlet.
W niektórych przypadkach z powodu brakującej zależności w niższych warstwach .NET funkcji została usunięta lub jest niedostępna.

Większość modułów, które są dostarczane jako część systemu Windows (na przykład `DnsClient`, `Hyper-V`, `NetTCPIP`, `Storage`, itp.) oraz innych produktów firmy Microsoft, w tym Azure i pakietu Office nie zostały jeszcze *jawnie* przenoszone do. Jeszcze .NET Core.
Zespół programu PowerShell pracuje się z tych grup produktów i zespołów, aby zweryfikować i portu swoich istniejących modułów programu PowerShell Core.
Za pomocą platformy .NET Standard i [CDXML][]wiele z tych tradycyjnych modułów programu Windows PowerShell wydaje się, że praca w programie PowerShell Core, ale nie zostały one oficjalnie zatwierdzone i nie jest oficjalnie obsługiwana.

Instalując [ `WindowsPSModulePath` ] [ windowspsmodulepath] modułu, można użyć modułów programu Windows PowerShell, dodając programu Windows PowerShell `PSModulePath` do podstawowego środowiska PowerShell `PSModulePath`.

Najpierw zainstaluj `WindowsPSModulePath` modułu z galerii programu PowerShell:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

Po zainstalowaniu tego modułu, należy uruchomić `Add-WindowsPSModulePath` polecenie cmdlet programu Windows PowerShell dodanie `PSModulePath` do programu PowerShell Core:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="docker-support"></a>Obsługę platformy docker

Program PowerShell Core dodaje obsługę kontenerów platformy Docker dla wszystkich głównych platform obsługujemy (w tym wiele dystrybucje systemu Linux, Windows Server Core i Nano Server).

Aby uzyskać pełną listę, zapoznaj się z tagów na [ `microsoft/powershell` w usłudze Docker Hub][docker-hub].
Aby uzyskać więcej informacji na temat platformy Docker i PowerShell Core, zobacz [Docker][] w witrynie GitHub.

## <a name="ssh-based-powershell-remoting"></a>Komunikacji zdalnej programu PowerShell — opartego na SSH

Protokół komunikacji zdalnej programu PowerShell (PSRP) współpracuje teraz z protokołem Secure Shell (SSH), oprócz tradycyjnego PSRP na podstawie usługi WinRM.

Oznacza to, że można użyć polecenia cmdlet, takich jak `Enter-PSSession` i `New-PSSession` i Uwierzytelnij się przy użyciu protokołu SSH.
Trzeba wystarczy zarejestrować program PowerShell jako podsystemu serwer opartych na OpenSSH SSH i możesz użyć istniejącej opartego na SSH uwierzytelniania mechanizmów (takie jak hasła lub kluczy prywatnych) przy użyciu tradycyjnych `PSSession` semantyki.

Aby uzyskać więcej informacji na temat konfigurowania i używania remoting opartego na SSH, zobacz [komunikacji zdalnej programu PowerShell za pomocą protokołu SSH][ssh-remoting].

## <a name="default-encoding-is-utf-8-without-a-bom-except-for-new-modulemanifest"></a>Domyślnym kodowaniem jest UTF-8 bez BOM, z wyjątkiem nowego ModuleManifest

W przeszłości, poleceń cmdlet programu Windows PowerShell, takie jak `Get-Content`, `Set-Content` używać różnych kodowań, takie jak ASCII i UTF-16.
Wariancja w wartością domyślną kodowania jest utworzenia problemów Mieszanie poleceń cmdlet bez określania opcji kodowania.

Platformy Windows inne niż tradycyjnie Użyj UTF-8 bez znacznika kolejności bajtów (BOM) jako domyślnego kodowania szukać plików tekstowych.
Więcej aplikacji Windows i narzędzia są przenoszenie od UTF-16 i kierunku kodowania UTF-8 bez BOM.
Program PowerShell Core zmienia domyślnego kodowania, aby były zgodne z szerszego ekosystemów.

Oznacza to, że wszystkie wbudowane polecenia cmdlet używające `-Encoding` używanie parametrów `UTF8NoBOM` wartości domyślne.
Ta zmiana dotyczy następujących poleceń cmdlet:

- Dodaj zawartość
- Export-Clixml
- Export-Csv
- Export-PSSession
- Format-Hex
- Get-Content
- Import-Csv
- Out-file
- Wybierz parametry
- Send-MailMessage
- Zawartość zestawu

Te polecenia cmdlet również zostały zaktualizowane, aby `-Encoding` powszechnie akceptuje parametr `System.Text.Encoding`.

Wartość domyślna `$OutputEncoding` również został zmieniony na UTF-8.

Najlepszym rozwiązaniem, należy jawnie ustawić kodowania za pomocą skryptów `-Encoding` parametru, aby wygenerować deterministyczne zachowanie różnych platformach.

`New-ModuleManifest` polecenie cmdlet nie ma **kodowanie** parametru. Kodowanie pliku manifestu (psd1) modułu utworzonych za pomocą `New-ModuleManifest` polecenia cmdlet zależy od środowiska: Jeśli program PowerShell Core działającej w systemie Linux następnie kodowanie UTF-8 (nie BOM); jest w przeciwnym razie kodowanie UTF-16 (z BOM). (#3940)

## <a name="support-backgrounding-of-pipelines-with-ampersand--3360"></a>Obsługuje uruchamianie procesów w tle potoków przy użyciu handlowe "i" (`&`) (#3360)

Umieszczenie `&` na końcu potoku powoduje, że potok do uruchamiania jako zadania programu PowerShell.
Gdy jest backgrounded potoku, jest zwracany obiekt zadania.
Gdy potok jest uruchomiona jako zadanie, wszystkich standardowych `*-Job` można użyć poleceń cmdlet do zarządzania zadaniem.
Zmienne (bez uwzględnienia zmiennymi specyficznymi dla procesu) używane w potoku są automatycznie kopiowane do zadania tak `Copy-Item $foo $bar &` po prostu działa.
Zadanie jest również uruchamiane w bieżącym katalogu zamiast katalogu macierzystego użytkownika.
Aby uzyskać więcej informacji na temat zadań programu PowerShell, zobacz [about_Jobs](https://msdn.microsoft.com/powershell/reference/6/about/about_jobs).

## <a name="semantic-versioning"></a>Przechowywanie wersji semantyczne

- Wprowadzone `SemanticVersion` zgodny z `SemVer 2.0`. (#5037) (Dziękuję [ @iSazonov ](https://github.com/iSazonov)!)
- Zmienić domyślne `ModuleVersion` w `New-ModuleManifest` do `0.0.1` wyrównać SemVer. (#4842) (Dziękuję [ @LDSpits ](https://github.com/LDSpits))
- Dodano `semver` jako typ akceleratora, w celu `System.Management.Automation.SemanticVersion`. (#4142) (Dzięki [ @oising ](https://github.com/oising)!)
- Włączone porównanie `SemanticVersion` wystąpienia i `Version` wystąpienia, który jest tworzony tylko w przypadku `Major` i `Minor` wartości wersji.

## <a name="language-updates"></a>Języki aktualizacji

- Implementowanie ucieczki Unicode, analizy, dzięki czemu użytkownicy mogą używać znaków Unicode jako argumenty, ciągi lub nazwy zmiennych. (#3958) (Dzięki [ @rkeithhill ](https://github.com/rkeithhill)!)
- Dodano nowe znak ucieczki dla ESC: `` `e``
- Dodano obsługę konwersji typów wyliczeniowych do ciągów (#4318) (Dziękuję [ @KirkMunro ](https://github.com/KirkMunro))
- Naprawiono rzutowanie pojedynczy element tablicy do ogólnych kolekcji. (#3170)
- Zakres znaków dodano przeładowania `..` operatora, więc `'a'..'z'` zwraca znaki "a" do "z". (#5026) (Dziękuję [ @IISResetMe ](https://github.com/IISResetMe)!)
- Naprawiono przypisanie zmiennej nie zastąpić zmienne tylko do odczytu
- Wypychanie do "DottedScopes" zmiennych lokalnych, zmiennych automatycznych, gdy dotting poleceń cmdlet skryptów (#4709)
- Włącz opcję "Singleline, wielowierszowy" w operatorze podziału (#4721) (Dziękuję [ @iSazonov ](https://github.com/iSazonov))

## <a name="engine-updates"></a>Aktualizacje aparatu

- `$PSVersionTable` ma cztery nowe właściwości:
  - `PSEdition`: Jest ono ustawione na `Core` w programie PowerShell Core i `Desktop` na programie Windows PowerShell
  - `GitCommitId`: Jest to identyfikator zatwierdzenia Git Git gałęzi lub tagu której została skompilowana programu PowerShell.
    Wydana w kompilacji, prawdopodobnie będzie taka sama jak `PSVersion`.
  - `OS`: Jest to zwrócony przez ciąg wersji systemu operacyjnego `[System.Runtime.InteropServices.RuntimeInformation]::OSDescription`
  - `Platform`: Ta wartość jest zwracana przez `[System.Environment]::OSVersion.Platform` jest równa `Win32NT` na Windows, `Unix` w systemie macOS i `Unix` w systemie Linux.
- Usunięte `BuildVersion` właściwość `$PSVersionTable`.
  Ta właściwość silnie powiązanej z wersji kompilacji Windows.
  Zamiast tego zaleca się używanie `GitCommitId` można pobrać kompilacji dokładną wersję programu PowerShell Core. (#3877) (Dzięki [ @iSazonov ](https://github.com/iSazonov)!)
- Usuń `ClrVersion` właściwość `$PSVersionTable`.
  Ta właściwość nie ma znaczenia dla platformy .NET Core i tylko została zachowana w programie .NET Core do określonych celów starszej wersji, które są nie stosuje się do programu PowerShell.
- Dodane trzy nowe automatycznych zmiennych, aby ustalić, czy program PowerShell jest uruchomiony w danej wersji systemu operacyjnego: `$IsWindows`, `$IsMacOs`, i `$IsLinux`.
- Dodaj `GitCommitId` do programu PowerShell Core baner.
  Teraz nie musisz przeprowadzić `$PSVersionTable` zaraz po uruchomieniu programu PowerShell, aby pobrać wersję! (#3916) (Dzięki [ @iSazonov ](https://github.com/iSazonov)!)
- Dodawanie pliku konfiguracji JSON o nazwie `powershell.config.json` w `$PSHome` do przechowywania niektórych ustawień wymagany czas uruchamiania (np. `ExecutionPolicy`).
- Nie blokuj potoku podczas uruchamiania Windows EXE
- Włączono wyliczenie COM kolekcji. (#4553)

## <a name="cmdlet-updates"></a>Polecenia cmdlet aktualizacji

### <a name="new-cmdlets"></a>Nowe polecenia cmdlet

- Add `Get-Uptime` to `Microsoft.PowerShell.Utility`.
- Dodaj `Remove-Alias` polecenia. (#5143) (Dziękuję [ @PowershellNinja ](https://github.com/PowershellNinja)!)
- Dodaj `Remove-Service` do modułu. (#4858) (Dziękuję [ @joandrsn ](https://github.com/joandrsn)!)

### <a name="web-cmdlets"></a>Polecenia cmdlet sieci Web

- Dodano obsługę uwierzytelniania certyfikatów dla poleceń cmdlet sieci web. (#4646) (Dziękuję [ @markekraus ](https://github.com/markekraus))
- Obsługę nagłówki zawartości w poleceniach cmdlet usługi sieci web. (#4494 & #4640) (Dziękuję [ @markekraus ](https://github.com/markekraus))
- Dodaj obsługę wielu nagłówka łącze poleceniach cmdlet usługi sieci Web. (#5265) (Dziękuję [ @markekraus ](https://github.com/markekraus)!)
- Obsługa dzielenia na strony łącze nagłówka w poleceniach cmdlet sieci web (#3828)
  - Aby uzyskać `Invoke-WebRequest`, gdy odpowiedź zawiera nagłówek łącza, możemy utworzyć właściwość RelationLink jako słownik reprezentujący adresy URL i `rel` atrybutów, a następnie upewnij się, adresy URL są bezwzględne ułatwiają deweloperom stosowanie.
  - Dla `Invoke-RestMethod`, gdy odpowiedź zawiera nagłówek łącze uwidaczniamy `-FollowRelLink` przełącznik, aby automatycznie wykonać `next` `rel` łączy, dopóki nie jest już istnieje, lub raz możemy trafień opcjonalnego `-MaximumFollowRelLink` wartość parametru.
- Dodaj `-CustomMethod` parametru w poleceniach cmdlet usługi sieci web umożliwiające niestandardową metodę zleceń. (#3142) (Dzięki [ @Lee303 ](https://github.com/Lee303)!)
- Dodaj `SslProtocol` obsługi w poleceniach cmdlet usługi sieci Web. (#5329) (Dziękuję [ @markekraus ](https://github.com/markekraus)!)
- Dodaj Multipart pomocy technicznej w poleceniach cmdlet usługi sieci web. (#4782) (Dziękuję [ @markekraus ](https://github.com/markekraus))
- Dodaj `-NoProxy` poleceniach cmdlet usługi sieci web tak, aby zignorować są systemowe ustawienia proxy. (#3447) (Dzięki [ @TheFlyingCorpse ](https://github.com/TheFlyingCorpse)!)
- Użytkownik agenta sieci Web z poleceń cmdlet zgłasza teraz Platforma systemu operacyjnego (#4937) (Dziękuję [ @LDSpits ](https://github.com/LDSpits))
- Dodaj `-SkipHeaderValidation` przełączyć się do polecenia cmdlet w sieci web do obsługi dodawania nagłówków bez sprawdzania poprawności wartość nagłówka. (#4085)
- Włącz polecenia cmdlet w sieci web nie zweryfikuje certyfikat HTTPS serwera, jeśli jest to wymagane.
- Dodaj parametry uwierzytelniania w poleceniach cmdlet usługi sieci web. (#5052) (Dziękuję [ @markekraus ](https://github.com/markekraus))
  - Dodaj `-Authentication` , zawiera trzy opcje: Podstawowe, OAuth i elementu nośnego.
  - Dodaj `-Token` można uzyskać elementu nośnego tokenu OAuth i elementu nośnego opcje.
  - Dodaj `-AllowUnencryptedAuthentication` na pominięcie uwierzytelniania, który jest udostępniany dla dowolnego schematu transportu innych niż HTTPS.
- Dodaj `-ResponseHeadersVariable` do `Invoke-RestMethod` Aby włączyć funkcję przechwytywania nagłówków odpowiedzi. (#4888) (Dziękuję [ @markekraus ](https://github.com/markekraus))
- Naprawiono polecenia cmdlet w sieci web do uwzględnienia w wyjątku odpowiedzi HTTP, gdy kod stanu odpowiedzi to nie sukces. (#3201)
- Zmień polecenia cmdlet programu web `UserAgent` z `WindowsPowerShell` do `PowerShell`. (#4914) (Dziękuję [ @markekraus ](https://github.com/markekraus))
- Dodawanie jawnych `ContentType` wykrywania `Invoke-RestMethod` (#4692)
- Napraw polecenia cmdlet programu web `-SkipHeaderValidation` do pracy z niestandardowych nagłówków agenta użytkownika. (#4479 & #4512) (Dziękuję [ @markekraus ](https://github.com/markekraus))

### <a name="json-cmdlets"></a>Polecenia cmdlet JSON

- Dodaj `-AsHashtable` do `ConvertFrom-Json` do zwrócenia `Hashtable` zamiast tego. (#5043) (Dziękuję [ @bergmeister ](https://github.com/bergmeister)!)
- Użyj prettier element formatujący `ConvertTo-Json` danych wyjściowych. (#2787) (Dzięki @kittholland!)
- Dodaj `Jobject` obsługę serializacji `ConvertTo-Json`. (#5141)
- Napraw `ConvertFrom-Json` do deserializacji, tablica ciągów z potoku, które ze sobą konstruowania całego ciągu JSON.
  To naprawia czasami, w którym oddzielane zaburzyłaby analizy JSON. (#3823)
- Usuń `AliasProperty "Count"` zdefiniowane dla `System.Array`.
  Spowoduje to usunięcie obce `Count` niektórych właściwości `ConvertFrom-Json` danych wyjściowych. (#3231) (Dzięki [ @PetSerAl ](https://github.com/PetSerAl)!)

### <a name="csv-cmdlets"></a>Polecenia cmdlet CSV

- Dodaj `PSTypeName` Obsługa `Import-Csv` i `ConvertFrom-Csv`. (#5389) (Dziękuję [ @markekraus ](https://github.com/markekraus)!)
- Wprowadź `Import-Csv` obsługuje `CR`, `LF`, i `CRLF` wiersz jako ograniczniki. (#5363) (Dziękuję [ @iSazonov ](https://github.com/iSazonov)!)
- Wprowadź `-NoTypeInformation` domyślny w `Export-Csv` i `ConvertTo-Csv`. (#5164) (Dziękuję [ @markekraus ](https://github.com/markekraus))

### <a name="service-cmdlets"></a>Polecenia cmdlet usługi

- Dodaj właściwości `UserName`, `Description`, `DelayedAutoStart`, `BinaryPathName`, i `StartupType` do `ServiceController` obiektów zwróconych przez `Get-Service`. (#4907) (Dziękuję [ @joandrsn ](https://github.com/joandrsn))
- Dodawanie funkcji, aby ustawić poświadczenia na `Set-Service` polecenia. (#4844) (Dziękuję [ @joandrsn ](https://github.com/joandrsn))

### <a name="other-cmdlets"></a>Inne polecenia cmdlet

- Dodaj parametr `Get-ChildItem` o nazwie `-FollowSymlink` łączy symbolicznych ten, który przechodzi na żądanie przy użyciu sprawdza, czy łącze pętli. (#4020)
- Aktualizacja `Add-Type` do obsługi `CSharpVersion7`. (#3933) (Dzięki [ @iSazonov ](https://github.com/iSazonov))
- Usuń `Microsoft.PowerShell.LocalAccounts` modułu z powodu używania nieobsługiwany interfejsów API, aż do znalezienia lepszym rozwiązaniem. (#4302)
- Usuń `*-Counter` polecenia cmdlet w `Microsoft.PowerShell.Diagnostics` ze względu na użycie nieobsługiwanego interfejsów API, aż do znalezienia lepszym rozwiązaniem. (#4303)
- Dodano obsługę `Invoke-Item -Path <folder>`. (#4262)
- Dodaj `-Extension` i `-LeafBase` przełącza się `Split-Path` tak, aby podzielić ścieżek między rozszerzenie nazwy pliku i pozostałej części nazwy pliku. (#2721) (Dzięki [ @powercode ](https://github.com/powercode)!)
- Dodaj parametry `-Top` i `-Bottom` do `Sort-Object` sortować górne/dolne N
- Udostępnianie proces nadrzędny procesu, dodając `CodeProperty "Parent"` do `System.Diagnostics.Process`. (#2850) (Dzięki [ @powercode ](https://github.com/powercode)!)
- Na użytek MB zamiast KB pamięci kolumn `Get-Process`
- Dodaj `-NoNewLine` przełączać `Out-String`. (#5056) (Dziękuję [ @raghav710 ](https://github.com/raghav710))
- `Move-Item` polecenia cmdlet honoruje `-Include`, `-Exclude`, i `-Filter` parametrów. (#3878)
- Zezwalaj na `*` do użycia w ścieżce rejestru dla `Remove-Item`. (#4866)
- Dodaj `-Title` do `Get-Credential` i ujednolicenie środowiska monitu między platformami.
- Dodaj `-TimeOut` parametr `Test-Connection`. (#2492)
- `Get-AuthenticodeSignature` polecenia cmdlet można teraz uzyskać sygnatura czasowa pliku podpisu. (#4061)
- Usuń nieobsługiwane `-ShowWindow` przełączyć się z `Get-Help`. (#4903)
- Napraw `Get-Content -Delimiter` do elementów tablicy nie zawierać ogranicznik zwracane (#3706) (Dziękuję [ @mklement0 ](https://github.com/mklement0))
- Dodaj `Meta`, `Charset`, i `Transitional` parametry `ConvertTo-HTML` (#4184) (Dziękuję [ @ergo3114 ](https://github.com/ergo3114))
- Dodaj `WindowsUBR` i `WindowsVersion` właściwości `Get-ComputerInfo` wynik
- Dodaj `-Group` parametr `Get-Verb`
- Dodaj `ShouldProcess` Obsługa `New-FileCatalog` i `Test-FileCatalog` (poprawki `-WhatIf` i `-Confirm`). (#3074) (Dzięki [ @iSazonov ](https://github.com/iSazonov)!)
- Dodaj `-WhatIf` przełączyć się do `Start-Process` polecenia cmdlet (#4735) (Dziękuję [ @sarithsutha ](https://github.com/sarithsutha))
- Dodaj `ValidateNotNullOrEmpty` zbyt wiele parametrów istniejącego.

## <a name="tab-completion"></a>Uzupełnianie po naciśnięciu tabulatora

- Ulepszone wnioskowanie o typie w uzupełniania po naciśnięciu tabulatora na podstawie wartości zmiennej środowiska uruchomieniowego. (#2744) (Dzięki [ @powercode ](https://github.com/powercode)!) Dzięki temu uzupełniania po naciśnięciu tabulatora w sytuacjach, takich jak:

  ```powershell
  $p = Get-Process
  $p | Foreach-Object Prio<tab>
  ```

- Dodaj uzupełniania po naciśnięciu tabulatora w tablicy skrótów do `-Property` z `Select-Object`. (#3625) (Dzięki [ @powercode ](https://github.com/powercode))
- Włącz argument automatycznego uzupełniania dla `-ExcludeProperty` i `-ExpandProperty` z `Select-Object`. (#3443) (Dzięki [ @iSazonov ](https://github.com/iSazonov)!)
- Naprawienie usterki w uzupełniania po naciśnięciu tabulatora, aby `native.exe --<tab>` wywołania do natywnego modułu wypełniania. (#3633) (Dzięki [ @powercode ](https://github.com/powercode)!)

## <a name="breaking-changes"></a>Zmiany powodujące niezgodność

Wprowadziliśmy szereg przełomowe zmiany w programie PowerShell Core 6.0.
Aby dowiedzieć się więcej o nich szczegółowo, zobacz [fundamentalne zmiany w programie PowerShell Core 6.0][breaking-changes].

## <a name="debugging"></a>Debugowanie

- Obsługa step-in debugowania zdalnego dla `Invoke-Command -ComputerName`. (#3015)
- Włączanie rejestrowania w programie PowerShell Core debugowania integratorów modeli

## <a name="filesystem-updates"></a>Aktualizacje systemu plików

- Włącz użycie dostawcy Filesystem ze ścieżki UNC. ($4998)
- `Split-Path` teraz współpracuje z katalogów głównych UNC
- `cd` bez argumentów teraz zachowuje się jak `cd ~`
- Naprawiono programu PowerShell Core, zezwalając na używanie ścieżek, które są długo więcej niż 260 znaków. (#3960)

## <a name="bug-fixes-and-performance-improvements"></a>Poprawki błędów i ulepszenia wydajności

Wprowadziliśmy *wiele* ulepszenia wydajności w programie PowerShell, w tym czas uruchamiania, różnych wbudowanych poleceń cmdlet i interakcji z natywnych plików binarnych.

Poprawiliśmy również liczbę błędów w programie PowerShell Core.
Aby uzyskać pełną listę poprawek i zmian, zapoznaj się z naszym [dziennika zmian][] w witrynie GitHub.

## <a name="telemetry"></a>Telemetria

- PowerShell Core 6.0, dodać telemetrię, aby host konsoli do raportu dwóch wartości (#3620):
  - Platforma systemu operacyjnego (`$PSVersionTable.OSDescription`)
  - Dokładna wersja programu PowerShell (`$PSVersionTable.GitCommitId`)

Jeśli chcesz zrezygnować z tych danych telemetrycznych po prostu Utwórz `POWERSHELL_TELEMETRY_OPTOUT` zmienną środowiskową przy użyciu jednego z następujących wartości: `true`, `1` lub `yes`.
Tworzenie zmiennej pomija wszystkie dane telemetryczne, nawet przed pierwszym uruchomieniu programu PowerShell.
Planujemy także udostępnianie tych danych telemetrycznych i szczegółowe dane możemy zgromadzonych danych telemetrycznych w [pulpit nawigacyjny społeczności][community-dashboard].
Możesz dowiedzieć się więcej na temat sposobu ich wykorzystania przez nas w tym [wpis w blogu][telemetry-blog].

[github]: https://github.com/PowerShell/PowerShell
[.NET Core 2.0]: https://docs.microsoft.com/dotnet/core/
[.NET Standard]: https://docs.microsoft.com/dotnet/standard/net-standard
[os_log]: https://developer.apple.com/documentation/os/logging
[Syslog]: https://en.wikipedia.org/wiki/Syslog
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[breaking-changes]: breaking-changes-ps6.md
[dziennika zmian]: https://github.com/PowerShell/PowerShell/tree/master/CHANGELOG.md
[community-dashboard]: https://aka.ms/PSGitHubBI
[telemetry-blog]: https://blogs.msdn.microsoft.com/powershell/2017/01/31/powershell-open-source-community-dashboard/
[.NET Standard]: https://docs.microsoft.com/dotnet/standard/net-standard
[.NET Blog]: https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard
[YouTube]: https://www.youtube.com/watch?v=YI4MurjfMn8&list=PLRAdsfhKI4OWx321A_pr-7HhRNk7wOLLY
[FAQ]: https://github.com/dotnet/standard/blob/master/docs/faq.md
[CDXML]: https://msdn.microsoft.com/library/jj542525(v=vs.85).aspx
[docker-hub]: https://hub.docker.com/r/microsoft/powershell/
[docker]: https://github.com/PowerShell/PowerShell/tree/master/docker
[windowspsmodulepath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
