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
# <a name="whats-new-in-powershell-core-62"></a><span data-ttu-id="01460-103">Co nowego w programie PowerShell Core 6.2</span><span class="sxs-lookup"><span data-stu-id="01460-103">What's New in PowerShell Core 6.2</span></span>

<span data-ttu-id="01460-104">Wydanie programu PowerShell Core 6.2 koncentruje się na ulepszenia wydajności, poprawki i mniejszych ulepszeń języka i polecenia cmdlet, które poprawić jakość.</span><span class="sxs-lookup"><span data-stu-id="01460-104">The PowerShell Core 6.2 release focused on performance improvements, bug fixes, and smaller cmdlet and language enhancements that improve the quality.</span></span> <span data-ttu-id="01460-105">Aby wyświetlić pełną listę ulepszeń, zapoznaj się z naszym szczegółowe [changelogs](https://github.com/PowerShell/PowerShell/releases) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="01460-105">To see a full list of improvements, check out our detailed [changelogs](https://github.com/PowerShell/PowerShell/releases) on GitHub.</span></span>

## <a name="experimental-features"></a><span data-ttu-id="01460-106">Funkcje eksperymentalne</span><span class="sxs-lookup"><span data-stu-id="01460-106">Experimental Features</span></span>

<span data-ttu-id="01460-107">Wcześniej umożliwiliśmy obsługę [funkcje eksperymentalne][].</span><span class="sxs-lookup"><span data-stu-id="01460-107">Previously, we enabled support for [Experimental Features][].</span></span> <span data-ttu-id="01460-108">W wersji 6.2 mamy cztery funkcji eksperymentalnych, które możesz wypróbować. Prześlij opinię, dzięki czemu firma Microsoft może wprowadzić ulepszenia i zdecydować, czy funkcja jest warte podwyższania poziomu mainstream stanu.</span><span class="sxs-lookup"><span data-stu-id="01460-108">In the 6.2 release, we have four experimental features to try out. Please provide feedback so we can make improvements and to decide whether the feature is worth promoting to mainstream status.</span></span>

<span data-ttu-id="01460-109">Użyj `Get-ExperimentalFeature` w celu uzyskania listy dostępnych funkcji eksperymentalnych.</span><span class="sxs-lookup"><span data-stu-id="01460-109">Use `Get-ExperimentalFeature` to get a list of available experimental features.</span></span> <span data-ttu-id="01460-110">Można włączyć lub wyłączyć te funkcje przy użyciu `Enable-ExperimentalFeature` i `Disable-ExperimentalFeature`.</span><span class="sxs-lookup"><span data-stu-id="01460-110">You can enable or disable these features with `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature`.</span></span>

### <a name="command-not-found-suggestions"></a><span data-ttu-id="01460-111">Nie znaleziono sugestie polecenia</span><span class="sxs-lookup"><span data-stu-id="01460-111">Command Not Found Suggestions</span></span>

<span data-ttu-id="01460-112">Ta funkcja wykorzystuje funkcję dopasowywania rozmytego propozycje polecenia lub poleceń cmdlet, może być błędnie wpisane.</span><span class="sxs-lookup"><span data-stu-id="01460-112">This feature uses fuzzy matching to find suggestions for commands or cmdlets you may have mistyped.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSCommandNotFoundSuggestion
```

#### <a name="example"></a><span data-ttu-id="01460-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="01460-113">Example</span></span>

<span data-ttu-id="01460-114">W tym przykładzie nazwa błędnie polecenia cmdlet jest rozmyte dopasowane do kilka sugestii z największym prawdopodobieństwem najmniej prawdopodobne.</span><span class="sxs-lookup"><span data-stu-id="01460-114">In this example, the misspelled cmdlet name is fuzzy matched to several suggestions from most likely to least likely.</span></span>

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

### <a name="implicit-remoting-batching"></a><span data-ttu-id="01460-115">Przetwarzanie wsadowe niejawne komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="01460-115">Implicit Remoting Batching</span></span>

<span data-ttu-id="01460-116">Korzystając z [niejawne remoting](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) w potoku programu PowerShell traktuje każde polecenie w potoku niezależnie.</span><span class="sxs-lookup"><span data-stu-id="01460-116">When using [implicit remoting](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) in a pipeline, PowerShell treats each command in the pipeline independently.</span></span> <span data-ttu-id="01460-117">Obiekty są wielokrotnie serializowane i `de-serialized` między klientem a systemem zdalnym za pośrednictwem wykonywania potoku.</span><span class="sxs-lookup"><span data-stu-id="01460-117">Objects are repeatedly serialized and `de-serialized` between the client and remote system over the execution of the pipeline.</span></span>

<span data-ttu-id="01460-118">Dzięki tej funkcji PowerShell analizuje potoku tak, aby ustalić, czy polecenie jest bezpiecznie uruchomić i istnieje w systemie docelowym.</span><span class="sxs-lookup"><span data-stu-id="01460-118">With this feature, PowerShell analyzes the pipeline to determine if the command is safe to run and it exists on the target system.</span></span> <span data-ttu-id="01460-119">W przypadku wartości true, programu PowerShell, cały potok jest wykonywany zdalnie i serializuje tylko i `de-serializes` wyniki z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="01460-119">When true, PowerShell executes the entire pipeline remotely and only serializes and `de-serializes` the results back to the client.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSImplicitRemotingBatching
```

<span data-ttu-id="01460-120">Test na rzeczywistych `Get-Process | Sort-Object` za pośrednictwem localhost zmniejsza się z 10 – 15 sekund na 20 – 30 **milisekund**.</span><span class="sxs-lookup"><span data-stu-id="01460-120">A real-world test of `Get-Process | Sort-Object` over localhost decreases from 10-15 seconds to 20-30 **milliseconds**.</span></span> <span data-ttu-id="01460-121">Tę funkcję tylko musi być włączona na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="01460-121">The feature only needs to be enabled on the client.</span></span> <span data-ttu-id="01460-122">Na serwerze są wymagane żadne zmiany.</span><span class="sxs-lookup"><span data-stu-id="01460-122">No changes are required on the server.</span></span>

### <a name="temp-drive"></a><span data-ttu-id="01460-123">Temp Drive</span><span class="sxs-lookup"><span data-stu-id="01460-123">Temp Drive</span></span>

```powershell
Enable-ExperimentalFeature -Name PSTempDrive
```

<span data-ttu-id="01460-124">Jeśli używasz programu PowerShell Core w różnych systemach operacyjnych, dowiesz się, że zmienna środowiskowa służące do znajdowania katalog tymczasowy jest różny na Windows, macOS i Linux!</span><span class="sxs-lookup"><span data-stu-id="01460-124">If you're using PowerShell Core on different operating systems, you'll discover that the environment variable for finding the temporary directory is different on Windows, macOS, and Linux!</span></span> <span data-ttu-id="01460-125">Dzięki tej funkcji możesz uzyskać [PSDrive][] o nazwie `Temp:` jest automatycznie mapowany do folderu tymczasowego systemu operacyjnego, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="01460-125">With this feature, you get a [PSDrive][] called `Temp:` that is automatically mapped to the temporary folder for the operating system you are using.</span></span>

#### <a name="example"></a><span data-ttu-id="01460-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="01460-126">Example</span></span>

```powershell
PS> "Hello World!" > Temp:/hello.txt
PS> `Get-Content` Temp:/hello.txt
Hello World!
```

<span data-ttu-id="01460-127">Należy pamiętać, poleceń tym natywnych plików (takich jak `ls` w systemie Linux) nie rozpoznają PSDrives i nie będziesz widzieć to `Temp:` dysku.</span><span class="sxs-lookup"><span data-stu-id="01460-127">Be aware that native file commands (like `ls` on Linux) are not aware of PSDrives and won't see this `Temp:` drive.</span></span>

### <a name="abbreviation-expansion"></a><span data-ttu-id="01460-128">Rozszerzenie skrótu</span><span class="sxs-lookup"><span data-stu-id="01460-128">Abbreviation Expansion</span></span>

<span data-ttu-id="01460-129">Powinny mieć opisowy rzeczowniki poleceń cmdlet programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="01460-129">PowerShell cmdlets are expected to have descriptive nouns.</span></span> <span data-ttu-id="01460-130">Skutkuje to długich nazwach, które są trudne do typu.</span><span class="sxs-lookup"><span data-stu-id="01460-130">This results in long names that are more difficult to type.</span></span> <span data-ttu-id="01460-131">Ta funkcja umożliwia po prostu wpisz wielkich liter, polecenia cmdlet i użyj uzupełniania po naciśnięciu tabulatora, aby znaleźć dopasowania.</span><span class="sxs-lookup"><span data-stu-id="01460-131">This feature allows you to just type the uppercase characters of the cmdlet and use tab-completion to find a match.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSUseAbbreviationExpansion
```

#### <a name="example"></a><span data-ttu-id="01460-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="01460-132">Example</span></span>

```powershell
PS> i-arsavsf
```

<span data-ttu-id="01460-133">Jeśli osiągnięty kartę i mieć programu Azure PowerShell [Az](https://www.powershellgallery.com/packages/Az) zainstalowany moduł zostanie automatycznego uzupełniania, aby:</span><span class="sxs-lookup"><span data-stu-id="01460-133">If you hit tab, and have the Azure PowerShell [Az](https://www.powershellgallery.com/packages/Az) module installed, it will autocomplete to:</span></span>

```Output
PS> Import-AzRecoveryServicesAsrVaultSettingsFile
```

> [!NOTE]
> <span data-ttu-id="01460-134">Ta funkcja jest przeznaczona do było używać hasła interaktywnie.</span><span class="sxs-lookup"><span data-stu-id="01460-134">This feature is intended to be used interactively.</span></span> <span data-ttu-id="01460-135">Nie można wykonać formy skróconej poleceń cmdlet.</span><span class="sxs-lookup"><span data-stu-id="01460-135">Abbreviated forms of cmdlets can't be executed.</span></span>
> <span data-ttu-id="01460-136">Ta funkcja nie jest zamiennikiem aliasów.</span><span class="sxs-lookup"><span data-stu-id="01460-136">This feature is not a replacement for aliases.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="01460-137">Zmiany powodujące niezgodność</span><span class="sxs-lookup"><span data-stu-id="01460-137">Breaking Changes</span></span>

- <span data-ttu-id="01460-138">Napraw `-NoEnumerate` zachowanie `Write-Output` aby były zgodne z programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="01460-138">Fix `-NoEnumerate` behavior in `Write-Output` to be consistent with Windows PowerShell.</span></span> <span data-ttu-id="01460-139">(#9069)</span><span class="sxs-lookup"><span data-stu-id="01460-139">(#9069)</span></span>
- <span data-ttu-id="01460-140">Wprowadzić `Join-String -InputObject 1,2,3` wyniku równa `1,2,3 | Join-String` wynik (#8611) (Dziękuję @sethvs!)</span><span class="sxs-lookup"><span data-stu-id="01460-140">Make `Join-String -InputObject 1,2,3` result equal to `1,2,3 | Join-String` result (#8611) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="01460-141">Dodaj `-Stable` do `Sort-Object` i powiązanych testów (#7862) (Dziękuję @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="01460-141">Add `-Stable` to `Sort-Object` and related tests (#7862) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="01460-142">Poprawa `Start-Sleep` polecenia cmdlet, aby zaakceptować ułamków sekund (#8537) (Dziękuję @Prototyyppi!)</span><span class="sxs-lookup"><span data-stu-id="01460-142">Improve `Start-Sleep` cmdlet to accept fractional seconds (#8537) (Thanks @Prototyyppi!)</span></span>
- <span data-ttu-id="01460-143">Zmień obiektu hashtable do przy użyciu OrdinalIgnoreCase `case-insensitive` we wszystkich kulturach (#8566)</span><span class="sxs-lookup"><span data-stu-id="01460-143">Change hashtable to use OrdinalIgnoreCase to be `case-insensitive` in all Cultures (#8566)</span></span>
- <span data-ttu-id="01460-144">Napraw **LiteralPath** w `Import-Csv` można powiązać `Get-ChildItem` danych wyjściowych (#8277) (Dziękuję @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="01460-144">Fix **LiteralPath** in `Import-Csv` to bind to `Get-ChildItem` output (#8277) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="01460-145">Nie jest już pomija kolumny bez nazwy użycie podwójnego cudzysłowu ogranicznik `Import-Csv` (#7899) (Dziękuję @Topping!)</span><span class="sxs-lookup"><span data-stu-id="01460-145">No longer skips a column without name if double quote delimiter is used in `Import-Csv` (#7899) (Thanks @Topping!)</span></span>
- <span data-ttu-id="01460-146">`Get-ExperimentalFeature` nie ma już `-ListAvailable` przełącznika (#8318)</span><span class="sxs-lookup"><span data-stu-id="01460-146">`Get-ExperimentalFeature` no longer has `-ListAvailable` switch (#8318)</span></span>
- <span data-ttu-id="01460-147">Debugowanie zestawów teraz parametrów `$DebugPreference` do **Kontynuuj** zamiast **Inquire** (#8195) (Dziękuję @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="01460-147">Debug parameter now sets `$DebugPreference` to **Continue** instead of **Inquire** (#8195) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="01460-148">Honoruj `-OutputFormat` Jeśli określone w poleceniu-interactive, przekierowanego zakodowany używane z pwsh (#8115)</span><span class="sxs-lookup"><span data-stu-id="01460-148">Honor `-OutputFormat` if specified in non-interactive, redirected, encoded command used with pwsh (#8115)</span></span>
- <span data-ttu-id="01460-149">Ładuj zestaw ze ścieżki podstawowej moduł przed podjęciem próby załadowania z pamięci podręcznej GAC (#8073)</span><span class="sxs-lookup"><span data-stu-id="01460-149">Load assembly from module base path before trying to load from the GAC (#8073)</span></span>
- <span data-ttu-id="01460-150">Usuń tylda z pakietów dla systemu Linux (wersja zapoznawcza) (#8244)</span><span class="sxs-lookup"><span data-stu-id="01460-150">Remove tilde from Linux preview packages (#8244)</span></span>
- <span data-ttu-id="01460-151">Przenieś przetwarzania `-WorkingDirectory` przed rozpoczęciem przetwarzania profile (#8079)</span><span class="sxs-lookup"><span data-stu-id="01460-151">Move processing of `-WorkingDirectory` before processing of profiles (#8079)</span></span>
- <span data-ttu-id="01460-152">Nie należy dodawać `PATHEXT` zmiennej środowiskowej w systemach Unix (#7697) (Dziękuję @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="01460-152">Do not add `PATHEXT` environment variable on Unix (#7697) (Thanks @iSazonov!)</span></span>

## <a name="known-issues"></a><span data-ttu-id="01460-153">Znane problemy</span><span class="sxs-lookup"><span data-stu-id="01460-153">Known Issues</span></span>

- <span data-ttu-id="01460-154">Komunikacja zdalna na platformach Windows IOT ARM ma problem podczas ładowania modułów.</span><span class="sxs-lookup"><span data-stu-id="01460-154">Remoting on Windows IOT ARM platforms has an issue loading modules.</span></span> <span data-ttu-id="01460-155">Zobacz (#8053)</span><span class="sxs-lookup"><span data-stu-id="01460-155">See (#8053)</span></span>

## <a name="general-updates-and-fixes"></a><span data-ttu-id="01460-156">Ogólne aktualizacje i poprawki</span><span class="sxs-lookup"><span data-stu-id="01460-156">General Updates and Fixes</span></span>

- <span data-ttu-id="01460-157">Włączanie uzupełniania po naciśnięciu tabulatora bez uwzględniania wielkości liter, plików i folderów w systemie plików rozróżniana wielkość liter (#8128)</span><span class="sxs-lookup"><span data-stu-id="01460-157">Enable case-insensitive tab completion for files and folders on case-sensitive filesystem (#8128)</span></span>
- <span data-ttu-id="01460-158">Upublicznić PSVersionInfo.PSVersion i PSVersionInfo.PSEdition (#8054) (Dziękuję @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="01460-158">Make PSVersionInfo.PSVersion and PSVersionInfo.PSEdition public (#8054) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="01460-159">Dodaj wnioskowanie o typie dla `$_`  /  `$PSItem` w `catch{ }` blokuje (#8020) (Dziękuję @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="01460-159">Add Type Inference for `$_` / `$PSItem` in `catch{ }` blocks (#8020) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="01460-160">Napraw wnioskowanie o typie wywołania metody statycznej (#8018) (Dziękuję @SeeminglyScience!)</span><span class="sxs-lookup"><span data-stu-id="01460-160">Fix static method invocation type inference (#8018) (Thanks @SeeminglyScience!)</span></span>
- <span data-ttu-id="01460-161">Tworzenie typów wywnioskowane `Select-Object`, `Group-Object`, **PSObject** i **Hashtable** (#7231) (Dziękuję @powercode!)</span><span class="sxs-lookup"><span data-stu-id="01460-161">Create inferred types for `Select-Object`, `Group-Object`, **PSObject** and **Hashtable** (#7231) (Thanks @powercode!)</span></span>
- <span data-ttu-id="01460-162">Obsługuje wywołania metody z `ByRef-like` parametrów typu (#7721)</span><span class="sxs-lookup"><span data-stu-id="01460-162">Support calling method with `ByRef-like` type parameters (#7721)</span></span>
- <span data-ttu-id="01460-163">Obsłużyć przypadek, gdzie Ścieżka modułu programu Windows PowerShell jest już PSModulePath środowiska (#7727)</span><span class="sxs-lookup"><span data-stu-id="01460-163">Handle the case where the Windows PowerShell module path is already in the environment's PSModulePath (#7727)</span></span>
- <span data-ttu-id="01460-164">Włącz `SecureString` poleceń cmdlet dla innych niż Windows, przechowując zwykły tekst (#9199)</span><span class="sxs-lookup"><span data-stu-id="01460-164">Enable `SecureString` cmdlets for non-Windows by storing the plain text (#9199)</span></span>
- <span data-ttu-id="01460-165">Poprawić komunikat o błędzie na inne niż Windows, podczas importowania clixml z securestring (#7997)</span><span class="sxs-lookup"><span data-stu-id="01460-165">Improve error message on non-Windows when importing clixml with securestring (#7997)</span></span>
- <span data-ttu-id="01460-166">Dodanie parametru ReplyTo do `Send-MailMessage` (#8727) (Dziękuję @replicaJunction!)</span><span class="sxs-lookup"><span data-stu-id="01460-166">Adding parameter ReplyTo to `Send-MailMessage` (#8727) (Thanks @replicaJunction!)</span></span>
- <span data-ttu-id="01460-167">Dodaj komunikat przestarzałe `Send-MailMessage` (#9178)</span><span class="sxs-lookup"><span data-stu-id="01460-167">Add Obsolete message to `Send-MailMessage` (#9178)</span></span>
- <span data-ttu-id="01460-168">Napraw `Restart-Computer` pracować nad `localhost` , gdy usługi WinRM nie jest obecne (#9160)</span><span class="sxs-lookup"><span data-stu-id="01460-168">Fix `Restart-Computer` to work on `localhost` when WinRM is not present (#9160)</span></span>
- <span data-ttu-id="01460-169">Wprowadź `Start-Job` zgłosić błąd powodujący zakończenie, gdy program PowerShell jest hostowana (#9128)</span><span class="sxs-lookup"><span data-stu-id="01460-169">Make `Start-Job` throw terminating error when PowerShell is being hosted (#9128)</span></span>
- <span data-ttu-id="01460-170">Dodaj C# akceleratorów typu styl i sufiksy na potrzeby ushort, uint, ulong i krótki literały (#7813) (Dziękuję @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="01460-170">Add C# style type accelerators and suffixes for ushort, uint, ulong, and short literals (#7813) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="01460-171">Dodano nowe sufiksów literałów numerycznych — zobacz [about_Numeric_Literals][] (#7901) (Dziękuję @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="01460-171">Added new suffixes for numeric literals - see [about_Numeric_Literals][] (#7901) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="01460-172">Poziom wpływu raportuje poprawnie, gdy SupportsShouldProcess nie jest ustawiona wartość "true" (#8209) (Dziękuję @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="01460-172">Correctly Report impact level when SupportsShouldProcess is not set to 'true' (#8209) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="01460-173">Rozwiązywanie problemów Charset żądania w poleceniach cmdlet sieci Web (#8742) (Dziękuję @markekraus!)</span><span class="sxs-lookup"><span data-stu-id="01460-173">Fix Request Charset Issues in Web Cmdlets (#8742) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="01460-174">Napraw Expect `100-continue` problem za pomocą poleceń cmdlet sieci Web (#8679) (Dziękuję @markekraus!)</span><span class="sxs-lookup"><span data-stu-id="01460-174">Fix Expect `100-continue` issue with Web Cmdlets (#8679) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="01460-175">Rozwiązać problem blokowania plików za pomocą poleceń cmdlet sieci web (#7676) (Dziękuję @Claustn!)</span><span class="sxs-lookup"><span data-stu-id="01460-175">Fix file blocking issue with web cmdlets (#7676) (Thanks @Claustn!)</span></span>
- <span data-ttu-id="01460-176">Napraw strony kodowej problemu w `Invoke-RestMethod` (#8694) (Dziękuję @markekraus!)</span><span class="sxs-lookup"><span data-stu-id="01460-176">Fix code page parsing issue in `Invoke-RestMethod` (#8694) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="01460-177">Refaktoryzuj `ConvertTo-Json` do udostępnienia JsonObject.ConvertToJson jako publiczny interfejs API (#8682)</span><span class="sxs-lookup"><span data-stu-id="01460-177">Refactor `ConvertTo-Json` to expose JsonObject.ConvertToJson as a public API (#8682)</span></span>
- <span data-ttu-id="01460-178">Dodawać można skonfigurować maksymalną głębokość w `ConvertFrom-Json` głębokość-(#8199) (Dziękuję @louistio!)</span><span class="sxs-lookup"><span data-stu-id="01460-178">Add configurable maximum depth in `ConvertFrom-Json` with -Depth (#8199) (Thanks @louistio!)</span></span>
- <span data-ttu-id="01460-179">Dodaj parametr EscapeHandling `ConvertTo-Json` polecenia cmdlet (#7775) (Dziękuję @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="01460-179">Add EscapeHandling parameter in `ConvertTo-Json` cmdlet (#7775) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="01460-180">Dodaj `-CustomPipeName` do pwsh i `Enter-PSHostProcess` (#8889)</span><span class="sxs-lookup"><span data-stu-id="01460-180">Add `-CustomPipeName` to pwsh and `Enter-PSHostProcess` (#8889)</span></span>
- <span data-ttu-id="01460-181">Włącz tworzenie łącza symbolicznego względne w Windows za pomocą `New-Item` (#8783)</span><span class="sxs-lookup"><span data-stu-id="01460-181">Enable creating relative symbolic links on Windows with `New-Item` (#8783)</span></span>
- <span data-ttu-id="01460-182">Zezwalaj użytkownikom Windows w trybie dewelopera do tworzenia łączy symbolicznych bez podniesienia uprawnień (#8534)</span><span class="sxs-lookup"><span data-stu-id="01460-182">Allow Windows users in developer mode to create symlinks without elevation (#8534)</span></span>
- <span data-ttu-id="01460-183">Włącz `Write-Information` do akceptowania `$null` (#8774)</span><span class="sxs-lookup"><span data-stu-id="01460-183">Enable `Write-Information` to accept `$null` (#8774)</span></span>
- <span data-ttu-id="01460-184">Napraw `Get-Help` zawartość pomocy dla zaawansowanych funkcji za pomocą MAML (#8353)</span><span class="sxs-lookup"><span data-stu-id="01460-184">Fix `Get-Help` for advanced functions with MAML help content (#8353)</span></span>
- <span data-ttu-id="01460-185">Napraw `Get-Help` problem PSTypeName — parametr, gdy tylko jeden parametr jest zadeklarowany (#8754) (Dziękuję @pougetat!)</span><span class="sxs-lookup"><span data-stu-id="01460-185">Fix `Get-Help` PSTypeName issue with -Parameter when only one parameter is declared (#8754) (Thanks @pougetat!)</span></span>
- <span data-ttu-id="01460-186">Poprawka tokenu obliczeń dla `Get-Help` wykonywane na ScriptBlock, aby uzyskać pomoc w komentarz.</span><span class="sxs-lookup"><span data-stu-id="01460-186">Token calculation fix for `Get-Help` executed on ScriptBlock for comment help.</span></span> <span data-ttu-id="01460-187">(#8238) (Dziękuję @hubuk!)</span><span class="sxs-lookup"><span data-stu-id="01460-187">(#8238) (Thanks @hubuk!)</span></span>
- <span data-ttu-id="01460-188">Zmiana `Get-Help` polecenia cmdlet — parametr parameter, więc przyjmuje parametry tablic (#8454) (Dziękuję @sethvs!)</span><span class="sxs-lookup"><span data-stu-id="01460-188">Change `Get-Help` cmdlet -Parameter parameter so it accepts string arrays (#8454) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="01460-189">Rozwiąż, PAGER, jeśli jego ścieżka zawiera spacje (#8571) (Dziękuję @pougetat!)</span><span class="sxs-lookup"><span data-stu-id="01460-189">Resolve PAGER if its path contains spaces (#8571) (Thanks @pougetat!)</span></span>
- <span data-ttu-id="01460-190">Dodaj monit z zastosowaniem `less` w funkcji "help", aby poinstruować użytkowników, jak zamknąć (#7998)</span><span class="sxs-lookup"><span data-stu-id="01460-190">Add prompt to the use of `less` in the function 'help' to instruct user how to quit (#7998)</span></span>
- <span data-ttu-id="01460-191">Dodaj obsługę typów wyliczenia lub char wchodzą w `Format-Hex` polecenia cmdlet (#8191) (Dziękuję @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="01460-191">Add support enum and char types in `Format-Hex` cmdlet (#8191) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="01460-192">Usuń ShouldProcess z `Format-Hex` (#8178)</span><span class="sxs-lookup"><span data-stu-id="01460-192">Remove ShouldProcess from `Format-Hex` (#8178)</span></span>
- <span data-ttu-id="01460-193">Dodaj nowe parametry przesunięcia i licznika do `Format-Hex` i Refaktoryzuj polecenia cmdlet (#7877) (Dziękuję @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="01460-193">Add new Offset and Count parameters to `Format-Hex` and refactor the cmdlet (#7877) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="01460-194">Zezwalaj na "name" jako klucza alias dla "label" w `ConvertTo-Html`, Zezwalaj na wpis "szerokość", aby być liczbą całkowitą (#8426) (Dziękuję @mklement0!)</span><span class="sxs-lookup"><span data-stu-id="01460-194">Allow 'name' as an alias key for 'label' in `ConvertTo-Html`, allow the 'width' entry to be an integer (#8426) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="01460-195">Blok skryptu Utwórz na podstawie obliczane właściwości ponownie działać `ConvertTo-Html` (#8427) (Dziękuję @mklement0!)</span><span class="sxs-lookup"><span data-stu-id="01460-195">Make scriptblock based calculated properties work again in `ConvertTo-Html` (#8427) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="01460-196">Dodano polecenie cmdlet `Join-String` do utworzenia tekstu z potoku danych wejściowych (#7660) (Dziękuję @powercode!)</span><span class="sxs-lookup"><span data-stu-id="01460-196">Add cmdlet `Join-String` for creating text from pipeline input (#7660) (Thanks @powercode!)</span></span>
- <span data-ttu-id="01460-197">Napraw `Join-String` polecenia cmdlet FormatString parametr logic (#8449) (Dziękuję @sethvs!)</span><span class="sxs-lookup"><span data-stu-id="01460-197">Fix `Join-String` cmdlet FormatString parameter logic (#8449) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="01460-198">Zmiana `Clear-Host` stosowanie `$RAWUI` i gotowość do pracy z wywołaniem funkcji zdalnych (#8609)</span><span class="sxs-lookup"><span data-stu-id="01460-198">Change `Clear-Host` back to using `$RAWUI` and clear to work over remoting (#8609)</span></span>
- <span data-ttu-id="01460-199">Zmiana `Clear-Host` wywołane po prostu `[console]::clear` i Usuń clear alias z systemu Unix (#8603)</span><span class="sxs-lookup"><span data-stu-id="01460-199">Change `Clear-Host` to simply called `[console]::clear` and remove clear alias from Unix (#8603)</span></span>
- <span data-ttu-id="01460-200">Napraw LiteralPath w `Import-Csv` można powiązać `Get-ChildItem` danych wyjściowych (#8277) (Dziękuję @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="01460-200">Fix LiteralPath in `Import-Csv` to bind to `Get-ChildItem` output (#8277) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="01460-201">Funkcja pomocy nie należy na użytek pagera AliasHelpInfo (#8552)</span><span class="sxs-lookup"><span data-stu-id="01460-201">help function shouldn't use pager for AliasHelpInfo (#8552)</span></span>
- <span data-ttu-id="01460-202">Dodaj `-UseMinimalHeader` do `Start-Transcript` zminimalizować nagłówka transkrypcji (#8402) (Dziękuję @lukexjeremy!)</span><span class="sxs-lookup"><span data-stu-id="01460-202">Add `-UseMinimalHeader` to `Start-Transcript` to minimize transcript header (#8402) (Thanks @lukexjeremy!)</span></span>
- <span data-ttu-id="01460-203">Dodaj `Enable-ExperimentalFeature` i `Disable-ExperimentalFeature` polecenia cmdlet (#8318)</span><span class="sxs-lookup"><span data-stu-id="01460-203">Add `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature` cmdlets (#8318)</span></span>
- <span data-ttu-id="01460-204">Udostępnianie wszystkie polecenia cmdlet z **PSDiagnostics** Jeśli logman.exe jest dostępny (#8366)</span><span class="sxs-lookup"><span data-stu-id="01460-204">Expose all cmdlets from **PSDiagnostics** if logman.exe is available (#8366)</span></span>
- <span data-ttu-id="01460-205">Usuń **utrwalanie** parametr `New-PSDrive` na `non-Windows` platformy (#8291) (Dziękuję @lukexjeremy!)</span><span class="sxs-lookup"><span data-stu-id="01460-205">Remove **Persist** parameter from `New-PSDrive` on `non-Windows` platform (#8291) (Thanks @lukexjeremy!)</span></span>
- <span data-ttu-id="01460-206">Dodano obsługę `cd +` (#7206) (Dziękuję @bergmeister!)</span><span class="sxs-lookup"><span data-stu-id="01460-206">Add support for `cd +` (#7206) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="01460-207">Włącz `Set-Location -LiteralPath` do pracy z folderami o nazwie — a + (#8089)</span><span class="sxs-lookup"><span data-stu-id="01460-207">Enable `Set-Location -LiteralPath` to work with folders named - and + (#8089)</span></span>
- <span data-ttu-id="01460-208">`Test-Path` Zwraca `$false` , gdy pustą lub `$null` ścieżka wartości (#8080) (Dziękuję @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="01460-208">`Test-Path` returns `$false` when given an empty or `$null` path value (#8080) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="01460-209">Zezwalaj na parametrów dynamicznych, które mają zostać zwrócone, nawet jeśli ścieżka nie jest zgodna z dowolnego dostawcy (#7957)</span><span class="sxs-lookup"><span data-stu-id="01460-209">Allow dynamic parameter to be returned even if path does not match any provider (#7957)</span></span>
- <span data-ttu-id="01460-210">Obsługa `Get-PSHostProcessInfo` i `Enter-PSHostProcess` na platformach Unix (#8232)</span><span class="sxs-lookup"><span data-stu-id="01460-210">Support `Get-PSHostProcessInfo` and `Enter-PSHostProcess` on Unix platforms (#8232)</span></span>
- <span data-ttu-id="01460-211">Zmniejszenia alokacji w `Get-Content` polecenia cmdlet (#8103) (Dziękuję @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="01460-211">Reduce allocations in `Get-Content` cmdlet (#8103) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="01460-212">Włącz `Add-Content` udostępnianie dostęp do odczytu z innymi narzędziami podczas zapisywania zawartości (#8091)</span><span class="sxs-lookup"><span data-stu-id="01460-212">Enable `Add-Content` to share read access with other tools while writing content (#8091)</span></span>
- <span data-ttu-id="01460-213">`Get/Add-Content` zgłasza błąd ulepszona, gdy kontener (#7823) (Dziękuję @kvprasoon!)</span><span class="sxs-lookup"><span data-stu-id="01460-213">`Get/Add-Content` throws improved error when targeting a container (#7823) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="01460-214">Dodaj `-Name`, `-NoUserOverrides` i `-ListAvailable` parametry `Get-Culture` polecenia cmdlet (#7702) (Dziękuję @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="01460-214">Add `-Name`, `-NoUserOverrides` and `-ListAvailable` parameters to `Get-Culture` cmdlet (#7702) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="01460-215">Dodaj atrybut ujednoliconego na ukończenie dla **kodowanie** parametru.</span><span class="sxs-lookup"><span data-stu-id="01460-215">Add unified attribute for completion for **Encoding** parameter.</span></span> <span data-ttu-id="01460-216">(#7732) (Dziękuję @ThreeFive-O!)</span><span class="sxs-lookup"><span data-stu-id="01460-216">(#7732) (Thanks @ThreeFive-O!)</span></span>
- <span data-ttu-id="01460-217">Zezwalaj na liczbowe identyfikatory i nazwy stron kodowych zarejestrowanego w **kodowanie** parametrów (#7636) (Dziękuję @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="01460-217">Allow numeric Ids and name of registered code pages in **Encoding** parameters (#7636) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="01460-218">Napraw `Rename-Item -Path` z symbolami wieloznacznymi char (#7398) (Dziękuję @kwkam!)</span><span class="sxs-lookup"><span data-stu-id="01460-218">Fix `Rename-Item -Path` with wildcard char (#7398) (Thanks @kwkam!)</span></span>
- <span data-ttu-id="01460-219">Korzystając z `Start-Transcript` i plik istnieje, a pusty plik niż usunięcie (#8131) (Dziękuję @paalbra!)</span><span class="sxs-lookup"><span data-stu-id="01460-219">When using `Start-Transcript` and file exists, empty file rather than deleting (#8131) (Thanks @paalbra!)</span></span>
- <span data-ttu-id="01460-220">Wprowadź `Add-Type` otwierania plików źródłowych przy użyciu **FileAccess.Read** i **FileShare.Read** jawnie (#7915) (Dziękuję @IISResetMe!)</span><span class="sxs-lookup"><span data-stu-id="01460-220">Make `Add-Type` open source files with **FileAccess.Read** and **FileShare.Read** explicitly (#7915) (Thanks @IISResetMe!)</span></span>
- <span data-ttu-id="01460-221">Napraw `Enter-PSSession -ContainerId` dla najnowszych Windows (#7883)</span><span class="sxs-lookup"><span data-stu-id="01460-221">Fix `Enter-PSSession -ContainerId` for the latest Windows (#7883)</span></span>
- <span data-ttu-id="01460-222">Upewnij się, **NestedModules** właściwość jest wypełniana przez `Test-ModuleManifest` (#7859)</span><span class="sxs-lookup"><span data-stu-id="01460-222">Ensure **NestedModules** property gets populated by `Test-ModuleManifest` (#7859)</span></span>
- <span data-ttu-id="01460-223">Dodaj `%F` wielkości liter do `Get-Date` - UFormat (#7630) (Dziękuję @britishben!)</span><span class="sxs-lookup"><span data-stu-id="01460-223">Add `%F` case to `Get-Date` -UFormat (#7630) (Thanks @britishben!)</span></span>
- <span data-ttu-id="01460-224">Napraw `Set-Service -Status Stopped` , aby zatrzymać usługi z zależnościami (#5525) (Dziękuję @zhenggu!)</span><span class="sxs-lookup"><span data-stu-id="01460-224">Fix `Set-Service -Status Stopped` to stop services with dependencies (#5525) (Thanks @zhenggu!)</span></span>

<!-- Link references -->
[about_Numeric_Literals]: /powershell/module/Microsoft.PowerShell.Core/About/about_numeric_literals
[Funkcje eksperymentalne]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[Experimental Features]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[PSDrive]: /powershell/module/microsoft.powershell.management/new-psdrive
