---
title: Co nowego w programie PowerShell Core 6.2
description: Nowe funkcje i zmiany w programie PowerShell Core 6.2
ms.date: 03/28/2019
ms.openlocfilehash: 6a0da8a410e602ae3963e0bc7bace745317d7d4b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058101"
---
# <a name="whats-new-in-powershell-core-62"></a>Co nowego w programie PowerShell Core 6.2

Wydanie programu PowerShell Core 6.2 koncentruje się na ulepszenia wydajności, poprawki i mniejszych ulepszeń języka i polecenia cmdlet, które poprawić jakość. Aby wyświetlić pełną listę ulepszeń, zapoznaj się z naszym szczegółowe [changelogs](https://github.com/PowerShell/PowerShell/releases) w witrynie GitHub.

## <a name="experimental-features"></a>Funkcje eksperymentalne

Wcześniej umożliwiliśmy obsługę [funkcje eksperymentalne][]. W wersji 6.2 mamy cztery funkcji eksperymentalnych, które możesz wypróbować. Prześlij opinię, dzięki czemu firma Microsoft może wprowadzić ulepszenia i zdecydować, czy funkcja jest warte podwyższania poziomu mainstream stanu.

Użyj `Get-ExperimentalFeature` w celu uzyskania listy dostępnych funkcji eksperymentalnych. Można włączyć lub wyłączyć te funkcje przy użyciu `Enable-ExperimentalFeature` i `Disable-ExperimentalFeature`.

### <a name="command-not-found-suggestions"></a>Nie znaleziono sugestie polecenia

Ta funkcja wykorzystuje funkcję dopasowywania rozmytego propozycje polecenia lub poleceń cmdlet, może być błędnie wpisane.

```powershell
Enable-ExperimentalFeature -Name PSCommandNotFoundSuggestion
```

#### <a name="example"></a>Przykład

W tym przykładzie nazwa błędnie polecenia cmdlet jest rozmyte dopasowane do kilka sugestii z największym prawdopodobieństwem najmniej prawdopodobne.

```powershell
Get-Commnd
```

```Output
Get-Commnd : The term 'Get-Commnd' is not recognized as the name of a cmdlet, function, script file, or operable program.
Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-Commnd
+ ~~~~~~~~~~
+ CategoryInfo          : ObjectNotFound: (Get-Commnd:String) [], CommandNotFoundException
+ FullyQualifiedErrorId : CommandNotFoundException


Suggestion [4,General]: The most similar commands are: Get-Command, Get-Content, Get-Job, Get-Module, Get-Event, Get-Host, Get-Member, Get-Item, Set-Content.
```

### <a name="implicit-remoting-batching"></a>Przetwarzanie wsadowe niejawne komunikacji zdalnej.

Korzystając z [niejawne remoting](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) w potoku programu PowerShell traktuje każde polecenie w potoku niezależnie. Obiekty są wielokrotnie serializowane i `de-serialized` między klientem a systemem zdalnym za pośrednictwem wykonywania potoku.

Dzięki tej funkcji PowerShell analizuje potoku tak, aby ustalić, czy polecenie jest bezpiecznie uruchomić i istnieje w systemie docelowym. W przypadku wartości true, programu PowerShell, cały potok jest wykonywany zdalnie i serializuje tylko i `de-serializes` wyniki z powrotem do klienta.

```powershell
Enable-ExperimentalFeature -Name PSImplicitRemotingBatching
```

Test na rzeczywistych `Get-Process | Sort-Object` za pośrednictwem localhost zmniejsza się z 10 – 15 sekund na 20 – 30 **milisekund**. Tę funkcję tylko musi być włączona na komputerze klienckim. Na serwerze są wymagane żadne zmiany.

### <a name="temp-drive"></a>Temp Drive

```powershell
Enable-ExperimentalFeature -Name PSTempDrive
```

Jeśli używasz programu PowerShell Core w różnych systemach operacyjnych, dowiesz się, że zmienna środowiskowa służące do znajdowania katalog tymczasowy jest różny na Windows, macOS i Linux! Dzięki tej funkcji możesz uzyskać [PSDrive][] o nazwie `Temp:` jest automatycznie mapowany do folderu tymczasowego systemu operacyjnego, którego używasz.

#### <a name="example"></a>Przykład

```powershell
PS> "Hello World!" > Temp:/hello.txt
PS> `Get-Content` Temp:/hello.txt
Hello World!
```

Należy pamiętać, poleceń tym natywnych plików (takich jak `ls` w systemie Linux) nie rozpoznają PSDrives i nie będziesz widzieć to `Temp:` dysku.

### <a name="abbreviation-expansion"></a>Rozszerzenie skrótu

Powinny mieć opisowy rzeczowniki poleceń cmdlet programu PowerShell. Skutkuje to długich nazwach, które są trudne do typu. Ta funkcja umożliwia po prostu wpisz wielkich liter, polecenia cmdlet i użyj uzupełniania po naciśnięciu tabulatora, aby znaleźć dopasowania.

```powershell
Enable-ExperimentalFeature -Name PSUseAbbreviationExpansion
```

#### <a name="example"></a>Przykład

```powershell
PS> i-arsavsf
```

Jeśli osiągnięty kartę i mieć programu Azure PowerShell [Az](https://www.powershellgallery.com/packages/Az) zainstalowany moduł zostanie automatycznego uzupełniania, aby:

```Output
PS> Import-AzRecoveryServicesAsrVaultSettingsFile
```

> [!NOTE]
> Ta funkcja jest przeznaczona do było używać hasła interaktywnie. Nie można wykonać formy skróconej poleceń cmdlet.
> Ta funkcja nie jest zamiennikiem aliasów.

## <a name="breaking-changes"></a>Zmiany powodujące niezgodność

- Napraw `-NoEnumerate` zachowanie `Write-Output` aby były zgodne z programu Windows PowerShell. (#9069)
- Wprowadzić `Join-String -InputObject 1,2,3` wyniku równa `1,2,3 | Join-String` wynik (#8611) (Dziękuję @sethvs!)
- Dodaj `-Stable` do `Sort-Object` i powiązanych testów (#7862) (Dziękuję @KirkMunro!)
- Poprawa `Start-Sleep` polecenia cmdlet, aby zaakceptować ułamków sekund (#8537) (Dziękuję @Prototyyppi!)
- Zmień obiektu hashtable do przy użyciu OrdinalIgnoreCase `case-insensitive` we wszystkich kulturach (#8566)
- Napraw **LiteralPath** w `Import-Csv` można powiązać `Get-ChildItem` danych wyjściowych (#8277) (Dziękuję @iSazonov!)
- Nie jest już pomija kolumny bez nazwy użycie podwójnego cudzysłowu ogranicznik `Import-Csv` (#7899) (Dziękuję @Topping!)
- `Get-ExperimentalFeature` nie ma już `-ListAvailable` przełącznika (#8318)
- Debugowanie zestawów teraz parametrów `$DebugPreference` do **Kontynuuj** zamiast **Inquire** (#8195) (Dziękuję @KirkMunro!)
- Honoruj `-OutputFormat` Jeśli określone w poleceniu-interactive, przekierowanego zakodowany używane z pwsh (#8115)
- Ładuj zestaw ze ścieżki podstawowej moduł przed podjęciem próby załadowania z pamięci podręcznej GAC (#8073)
- Usuń tylda z pakietów dla systemu Linux (wersja zapoznawcza) (#8244)
- Przenieś przetwarzania `-WorkingDirectory` przed rozpoczęciem przetwarzania profile (#8079)
- Nie należy dodawać `PATHEXT` zmiennej środowiskowej w systemach Unix (#7697) (Dziękuję @iSazonov!)

## <a name="known-issues"></a>Znane problemy

- Komunikacja zdalna na platformach Windows IOT ARM ma problem podczas ładowania modułów. Zobacz (#8053)

## <a name="general-updates-and-fixes"></a>Ogólne aktualizacje i poprawki

- Włączanie uzupełniania po naciśnięciu tabulatora bez uwzględniania wielkości liter, plików i folderów w systemie plików rozróżniana wielkość liter (#8128)
- Upublicznić PSVersionInfo.PSVersion i PSVersionInfo.PSEdition (#8054) (Dziękuję @KirkMunro!)
- Dodaj wnioskowanie o typie dla `$_`  /  `$PSItem` w `catch{ }` blokuje (#8020) (Dziękuję @vexx32!)
- Napraw wnioskowanie o typie wywołania metody statycznej (#8018) (Dziękuję @SeeminglyScience!)
- Tworzenie typów wywnioskowane `Select-Object`, `Group-Object`, **PSObject** i **Hashtable** (#7231) (Dziękuję @powercode!)
- Obsługuje wywołania metody z `ByRef-like` parametrów typu (#7721)
- Obsłużyć przypadek, gdzie Ścieżka modułu programu Windows PowerShell jest już PSModulePath środowiska (#7727)
- Włącz `SecureString` poleceń cmdlet dla innych niż Windows, przechowując zwykły tekst (#9199)
- Poprawić komunikat o błędzie na inne niż Windows, podczas importowania clixml z securestring (#7997)
- Dodanie parametru ReplyTo do `Send-MailMessage` (#8727) (Dziękuję @replicaJunction!)
- Dodaj komunikat przestarzałe `Send-MailMessage` (#9178)
- Napraw `Restart-Computer` pracować nad `localhost` , gdy usługi WinRM nie jest obecne (#9160)
- Wprowadź `Start-Job` zgłosić błąd powodujący zakończenie, gdy program PowerShell jest hostowana (#9128)
- Dodaj C# akceleratorów typu styl i sufiksy na potrzeby ushort, uint, ulong i krótki literały (#7813) (Dziękuję @vexx32!)
- Dodano nowe sufiksów literałów numerycznych — zobacz [about_Numeric_Literals][] (#7901) (Dziękuję @vexx32!)
- Poziom wpływu raportuje poprawnie, gdy SupportsShouldProcess nie jest ustawiona wartość "true" (#8209) (Dziękuję @vexx32!)
- Rozwiązywanie problemów Charset żądania w poleceniach cmdlet sieci Web (#8742) (Dziękuję @markekraus!)
- Napraw Expect `100-continue` problem za pomocą poleceń cmdlet sieci Web (#8679) (Dziękuję @markekraus!)
- Rozwiązać problem blokowania plików za pomocą poleceń cmdlet sieci web (#7676) (Dziękuję @Claustn!)
- Napraw strony kodowej problemu w `Invoke-RestMethod` (#8694) (Dziękuję @markekraus!)
- Refaktoryzuj `ConvertTo-Json` do udostępnienia JsonObject.ConvertToJson jako publiczny interfejs API (#8682)
- Dodawać można skonfigurować maksymalną głębokość w `ConvertFrom-Json` głębokość-(#8199) (Dziękuję @louistio!)
- Dodaj parametr EscapeHandling `ConvertTo-Json` polecenia cmdlet (#7775) (Dziękuję @iSazonov!)
- Dodaj `-CustomPipeName` do pwsh i `Enter-PSHostProcess` (#8889)
- Włącz tworzenie łącza symbolicznego względne w Windows za pomocą `New-Item` (#8783)
- Zezwalaj użytkownikom Windows w trybie dewelopera do tworzenia łączy symbolicznych bez podniesienia uprawnień (#8534)
- Włącz `Write-Information` do akceptowania `$null` (#8774)
- Napraw `Get-Help` zawartość pomocy dla zaawansowanych funkcji za pomocą MAML (#8353)
- Napraw `Get-Help` problem PSTypeName — parametr, gdy tylko jeden parametr jest zadeklarowany (#8754) (Dziękuję @pougetat!)
- Poprawka tokenu obliczeń dla `Get-Help` wykonywane na ScriptBlock, aby uzyskać pomoc w komentarz. (#8238) (Dziękuję @hubuk!)
- Zmiana `Get-Help` polecenia cmdlet — parametr parameter, więc przyjmuje parametry tablic (#8454) (Dziękuję @sethvs!)
- Rozwiąż, PAGER, jeśli jego ścieżka zawiera spacje (#8571) (Dziękuję @pougetat!)
- Dodaj monit z zastosowaniem `less` w funkcji "help", aby poinstruować użytkowników, jak zamknąć (#7998)
- Dodaj obsługę typów wyliczenia lub char wchodzą w `Format-Hex` polecenia cmdlet (#8191) (Dziękuję @iSazonov!)
- Usuń ShouldProcess z `Format-Hex` (#8178)
- Dodaj nowe parametry przesunięcia i licznika do `Format-Hex` i Refaktoryzuj polecenia cmdlet (#7877) (Dziękuję @iSazonov!)
- Zezwalaj na "name" jako klucza alias dla "label" w `ConvertTo-Html`, Zezwalaj na wpis "szerokość", aby być liczbą całkowitą (#8426) (Dziękuję @mklement0!)
- Blok skryptu Utwórz na podstawie obliczane właściwości ponownie działać `ConvertTo-Html` (#8427) (Dziękuję @mklement0!)
- Dodano polecenie cmdlet `Join-String` do utworzenia tekstu z potoku danych wejściowych (#7660) (Dziękuję @powercode!)
- Napraw `Join-String` polecenia cmdlet FormatString parametr logic (#8449) (Dziękuję @sethvs!)
- Zmiana `Clear-Host` stosowanie `$RAWUI` i gotowość do pracy z wywołaniem funkcji zdalnych (#8609)
- Zmiana `Clear-Host` wywołane po prostu `[console]::clear` i Usuń clear alias z systemu Unix (#8603)
- Napraw LiteralPath w `Import-Csv` można powiązać `Get-ChildItem` danych wyjściowych (#8277) (Dziękuję @iSazonov!)
- Funkcja pomocy nie należy na użytek pagera AliasHelpInfo (#8552)
- Dodaj `-UseMinimalHeader` do `Start-Transcript` zminimalizować nagłówka transkrypcji (#8402) (Dziękuję @lukexjeremy!)
- Dodaj `Enable-ExperimentalFeature` i `Disable-ExperimentalFeature` polecenia cmdlet (#8318)
- Udostępnianie wszystkie polecenia cmdlet z **PSDiagnostics** Jeśli logman.exe jest dostępny (#8366)
- Usuń **utrwalanie** parametr `New-PSDrive` na `non-Windows` platformy (#8291) (Dziękuję @lukexjeremy!)
- Dodano obsługę `cd +` (#7206) (Dziękuję @bergmeister!)
- Włącz `Set-Location -LiteralPath` do pracy z folderami o nazwie — a + (#8089)
- `Test-Path` Zwraca `$false` , gdy pustą lub `$null` ścieżka wartości (#8080) (Dziękuję @vexx32!)
- Zezwalaj na parametrów dynamicznych, które mają zostać zwrócone, nawet jeśli ścieżka nie jest zgodna z dowolnego dostawcy (#7957)
- Obsługa `Get-PSHostProcessInfo` i `Enter-PSHostProcess` na platformach Unix (#8232)
- Zmniejszenia alokacji w `Get-Content` polecenia cmdlet (#8103) (Dziękuję @iSazonov!)
- Włącz `Add-Content` udostępnianie dostęp do odczytu z innymi narzędziami podczas zapisywania zawartości (#8091)
- `Get/Add-Content` zgłasza błąd ulepszona, gdy kontener (#7823) (Dziękuję @kvprasoon!)
- Dodaj `-Name`, `-NoUserOverrides` i `-ListAvailable` parametry `Get-Culture` polecenia cmdlet (#7702) (Dziękuję @iSazonov!)
- Dodaj atrybut ujednoliconego na ukończenie dla **kodowanie** parametru. (#7732) (Dziękuję @ThreeFive-O!)
- Zezwalaj na liczbowe identyfikatory i nazwy stron kodowych zarejestrowanego w **kodowanie** parametrów (#7636) (Dziękuję @iSazonov!)
- Napraw `Rename-Item -Path` z symbolami wieloznacznymi char (#7398) (Dziękuję @kwkam!)
- Korzystając z `Start-Transcript` i plik istnieje, a pusty plik niż usunięcie (#8131) (Dziękuję @paalbra!)
- Wprowadź `Add-Type` otwierania plików źródłowych przy użyciu **FileAccess.Read** i **FileShare.Read** jawnie (#7915) (Dziękuję @IISResetMe!)
- Napraw `Enter-PSSession -ContainerId` dla najnowszych Windows (#7883)
- Upewnij się, **NestedModules** właściwość jest wypełniana przez `Test-ModuleManifest` (#7859)
- Dodaj `%F` wielkości liter do `Get-Date` - UFormat (#7630) (Dziękuję @britishben!)
- Napraw `Set-Service -Status Stopped` , aby zatrzymać usługi z zależnościami (#5525) (Dziękuję @zhenggu!)

<!-- Link references -->
[about_Numeric_Literals]: /powershell/module/Microsoft.PowerShell.Core/About/about_numeric_literals
[Funkcje eksperymentalne]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[PSDrive]: /powershell/module/microsoft.powershell.management/new-psdrive
