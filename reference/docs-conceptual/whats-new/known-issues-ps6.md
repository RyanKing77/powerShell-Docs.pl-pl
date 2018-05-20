---
ms.date: 05/17/2018
keywords: środowiska PowerShell, podstawowe
title: Znane problemy dotyczące programu PowerShell w wersji 6.0
ms.openlocfilehash: 6ad1bcaf1de06f204b57eb8ce23b3053ba4a5b38
ms.sourcegitcommit: 2d9cf1ccb9a653db7726a408ebcb65530dcb1522
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2018
---
# <a name="known-issues-for-powershell-60"></a>Znane problemy dotyczące programu PowerShell w wersji 6.0

## <a name="known-issues-for-powershell-on-non-windows-platforms"></a>Znane problemy dotyczące programu PowerShell na platformach systemu Windows

Alfa wersje programu PowerShell w systemie Linux i macOS przede wszystkim funkcjonalności, którzy mają pewnych ograniczeń znaczących i problemów z użytecznością. Wydanie beta programu PowerShell w systemie Linux i macOS więcej funkcjonalności i stabilnego niż alfa wersje, ale nadal może brakuje niektórych zestaw funkcji i mogą zawierać błędy. W niektórych przypadkach te problemy są po prostu usterki, które nie zostały jeszcze rozwiązane. W innych przypadkach (tak jak domyślne aliasy ls cp, itp.), czekamy na opinie od społeczności dotyczące opcji wykonujemy.

Uwaga: Z powodu podobieństwa wiele podstawowych podsystemów, programu PowerShell w systemie Linux i macOS zwykle na tym samym poziomie dojrzałości w funkcji i błędów. Z wyjątkiem przypadków wymienionych poniżej, problemy w tej sekcji dotyczą obu systemów operacyjnych.

### <a name="case-sensitivity-in-powershell"></a>Opcja uwzględniania wielkości liter w programie PowerShell

W przeszłości PowerShell została jednolicie bez uwzględniania wielkości liter, z pewnymi wyjątkami. W systemach operacyjnych UNIX przypominającej systemu plików jest głównie z uwzględnieniem wielkości liter i programu PowerShell jest zgodna ze standardem systemu plików; jest to za pośrednictwem na wiele sposobów, oczywiste i oczywiste.

#### <a name="directly"></a>bezpośrednio

- Podczas określania pliku w programie PowerShell, należy użyć poprawną wielkość.

#### <a name="indirectly"></a>Pośrednio

- Jeśli skrypt próbuje załadować modułu, a nazwa modułu jest nie z uwzględnieniem wielkości liter, załadowanie modułu zakończy się niepowodzeniem. Może to spowodować problem z istniejących skryptów, jeśli nazwa za pomocą którego istnieje odwołanie do modułu nie pasuje do nazwy pliku.
- Uzupełnianie po naciśnięciu tabulatora zostanie nie Ukończ automatycznie, jeśli przypadek nazwa pliku jest nieprawidłowy. Fragment do wykonania musi być z uwzględnieniem wielkości liter poprawnie. (Bez uwzględniania wielkości liter dla wpisz nazwę i typ elementu członkowskiego zakończeń jest ukończenia).

### <a name="ps1-file-extensions"></a>. PS1 Rozszerzenia plików

Skrypty programu PowerShell musi kończyć się `.ps1` dla interpretera zrozumienie, jak załadować i uruchamiać je w bieżącym procesie. Uruchamianie skryptów w bieżącym procesie jest zwykle oczekiwane zachowanie środowiska PowerShell. `#!` Magiczna liczba mogą być dodawane do skryptu, który nie ma `.ps1` rozszerzenie, ale spowoduje, że skrypt do uruchomienia w nowym wystąpieniu programu PowerShell uniemożliwia skrypt pracy poprawnie podczas zamiany obiektów. (Uwaga: może to być pożądane zachowanie podczas wykonywania skryptu programu PowerShell z `bash` lub innego powłoki.)

### <a name="missing-command-aliases"></a>Brak aliasy poleceń

W systemie Linux/macOS, "aliasów wygody" dla podstawowych poleceń `ls`, `cp`, `mv`, `rm`, `cat`, `man`, `mount`, `ps` zostały usunięte. W systemie Windows PowerShell udostępnia zestaw aliasy mapowane na nazwy polecenia systemu Linux dla wygody użytkownika. Następujące aliasy zostały usunięte z domyślnej programu PowerShell na dystrybucje systemu Linux/macOS, dzięki czemu natywnego pliku wykonywalnego do uruchomienia bez określania ścieżki.

Brak zalet i wad do tej czynności. Usuwanie aliasów przedstawia w środowisku macierzystym polecenia użytkownikowi programu PowerShell, ale zmniejsza funkcjonalność w powłoce, ponieważ natywnych poleceń zwraca ciągi zamiast obiektów.

> [!NOTE]
> Jest to obszar, w którym opinii szuka zespołowi środowiska PowerShell.
> Co to jest preferowany rozwiązania? Firma Microsoft pozostawienie bez zmian lub Dodaj aliasy wygody ponownie? Zobacz [wystawiać #929](https://github.com/PowerShell/PowerShell/issues/929).

### <a name="missing-wildcard-globbing-support"></a>Brak symbolu wieloznacznego (globbing) pomocy technicznej

Obecnie PowerShell tylko ma rozwijanie symbolu wieloznacznego (globbing), wbudowanego polecenia cmdlet w systemie Windows oraz poleceń zewnętrznych lub pliki binarne, jak również polecenia cmdlet w systemie Linux. Oznacza to, że polecenia, takich jak `ls
*.txt` zakończy się niepowodzeniem, ponieważ gwiazdki nie będą rozszerzane można dopasować nazw plików. Można obejść to za pomocą ćwiczeń `ls (gci *.txt | % name)` lub po prostu, `gci *.txt` przy użyciu programu PowerShell wbudowanych odpowiednikiem `ls`.

Zobacz [#954](https://github.com/PowerShell/PowerShell/issues/954) na przekazanie nam opinii na temat sposobów usprawnienia środowisko globbing w systemie Linux/macOS.

### <a name="net-framework-vs-net-core-framework"></a>.NET framework w wersji programu vs .NET Core Framework

PowerShell w systemie Linux/macOS korzysta z platformy .NET Core, który jest podzbiorem pełnej .NET Framework Microsoft Windows. Jest to istotne, ponieważ PowerShell zapewnia bezpośredni dostęp do typów podstawowych framework, metody itp. W związku z tym skryptów uruchamianych w systemie Windows może nie działać na różnych platformach z systemem innym niż Windows z powodu różnic w struktury. Aby uzyskać więcej informacji na temat platformy .NET Core Framework Zobacz <https://dotnetfoundation.org/net-core>

Pojawienie [.NET 2.0 standardowe](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/), .NET Core 2.0 będzie przywrócić wiele tradycyjnych typów i metod znajdujących się w pełnej .NET Framework. Oznacza to, podstawowe programu PowerShell będzie można załadować wiele modułów środowiska Windows PowerShell tradycyjnych bez żadnych modyfikacji. Możesz wykonać .NET Standard 2.0 pokrewne pracę [tutaj](https://github.com/PowerShell/PowerShell/projects/4).

### <a name="redirection-issues"></a>Problemy z przekierowania

Przekierowywanie wejściowy nie jest obsługiwane w programie PowerShell na dowolnej platformie.
[Problem #1629](https://github.com/PowerShell/PowerShell/issues/1629)

Użyj `Get-Content` do zapisywania zawartości pliku z potokiem.

Przekierowane dane wyjściowe będzie zawierać znacznika kolejności bajtów Unicode (BOM), gdy używane jest kodowanie UTF-8 domyślne. BOM powoduje problemów podczas pracy z narzędzia, które nie oczekują lub dołączanie do pliku. Użyj `-Encoding Ascii` zapisać tekst w formacie ASCII (który nie jest Unicode, nie będą miały BOM). (Uwaga: zobacz [RFC0020](https://github.com/PowerShell/PowerShell-RFC/issues/71) Aby wysłać nam swoją opinię na temat zwiększania kodowania środowiska PowerShell podstawowych na wszystkich platformach. Jesteśmy pracy do obsługi UTF-8 bez BOM i może zmienić kodowania wartości domyślne dla poszczególnych poleceń cmdlet na platformach.)

### <a name="job-control"></a>Zadanie kontroli

Brak obsługi sterowania zadania w programie PowerShell w systemie Linux/macOS.
`fg` i `bg` polecenia nie są dostępne.

W chwili obecnej, można użyć [zadania programu PowerShell](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_jobs) które działają na wszystkich platformach.

### <a name="remoting-support"></a>Obsługa komunikacji zdalnej

Obecnie PowerShell Core obsługuje komunikację zdalną środowiska PowerShell (PSRP) przez WSMan z uwierzytelnianiem podstawowym w macOS i Linux oraz z uwierzytelniania NTLM w systemie Linux. (Uwierzytelnianie za pomocą protokołu Kerberos nie jest obsługiwana.)

Pracy nad oparta na usłudze WSMan zdalnych jest wykonywana [psl omi dostawcy](https://github.com/PowerShell/psl-omi-provider) repozytorium.

PowerShell Core obsługuje również komunikację zdalną środowiska PowerShell (PSRP) za pomocą protokołu SSH na wszystkich platformach (z systemem Windows, system macOS i Linux). Podczas to nie jest obecnie obsługiwane w środowisku produkcyjnym, możesz dowiedzieć się więcej o konfigurowania [tutaj](../core-powershell/ssh-remoting-in-powershell-core.md).

### <a name="just-enough-administration-jea-support"></a>Obsługa Just dostatecznie administracyjnej (JEA)

Możliwość tworzenia ograniczonego administrowanie punktów końcowych usług zdalnych (JEA) nie jest obecnie dostępne w programie PowerShell w systemie Linux/macOS. Ta funkcja aktualnie nie jest w zakresie 6.0 i coś firma Microsoft będzie post 6.0 wziąć pod uwagę wymaga znaczących projektowe.

### <a name="sudo-exec-and-powershell"></a>`sudo`, `exec`, jak i programu PowerShell

Ponieważ Środowisko PowerShell jest uruchamiana większość używanych poleceń w pamięci (na przykład Python lub Ruby), nie można użyć sudo bezpośrednio z built-ins środowiska PowerShell. (Mogą oczywiście uruchamiać `powershell` z sudo.) Jeśli jest konieczne uruchomienie polecenia cmdlet programu PowerShell z wewnątrz programu PowerShell z sudo, na przykład `sudo Set-Date 8/18/2016`, a następnie należy `sudo powershell Set-Date 8/18/2016`. Podobnie nie możesz exec programu PowerShell wbudowanych bezpośrednio. Zamiast tego należy wykonać `exec powershell item_to_exec`.

Ten problem jest obecnie śledzony jako część #3232.

### <a name="missing-cmdlets"></a>Brak polecenia cmdlet

Dużej liczby poleceń (polecenia cmdlet) zwykle dostępne w programie PowerShell nie są dostępne w systemie Linux/macOS. W wielu przypadkach tych poleceń nie ma sensu na tych platformach (np. funkcje właściwe dla systemu Windows, takie jak rejestru). Inne polecenia, takich jak polecenia sterowania usługi (Get/Start/Stop-Service) są dostępne, ale nie działa. Przyszłych wydaniach będzie rozwiązać te problemy, ustalania przerwane poleceń cmdlet i dodaje nowe wraz z upływem czasu.

### <a name="command-availability"></a>Polecenie dostępności

Poniższa tabela zawiera listę poleceń, które są znane nie będą działać w programie PowerShell w systemie Linux/macOS.

<table>
<th>Polecenia</th><th>Stan operacyjny</th><th>Uwagi</th>
<tr>
<td>Get-Service, nowej usługi, Restart-Service, Resume-Service, usługi zestawu, Start-Service, Stop-Service, wstrzymanie usługi
<td>Niedostępne.
<td>Polecenia te nie zostaną rozpoznane. Powinien być rozwiązany w przyszłej wersji.
</tr>
<tr>
<td>Listy Acl GET, Set-list kontroli dostępu
<td>Niedostępne.
<td>Polecenia te nie zostaną rozpoznane. Powinien być rozwiązany w przyszłej wersji.
</tr>
<tr>
<td>Get-AuthenticodeSignature, Set-AuthenticodeSignature
<td>Niedostępne.
<td>Polecenia te nie zostaną rozpoznane. Powinien być rozwiązany w przyszłej wersji.
</tr>
<tr>
<td>Proces oczekiwania
<td>Dostępne, nie działa prawidłowo. <td>Na przykład `Start-Process gvim -PassThru | Wait-Process` nie działa; nie jest on poczekaj, aż proces.
</tr>
<tr>
<td>Register-PSSessionConfiguration, Unregister-PSSessionConfiguration, Get-PSSessionConfiguration
<td>Dostępne, ale nie działa.
<td>Zapisuje komunikat o błędzie wskazujący, że nie działają polecenia. Te powinny zostać ustalone w przyszłej wersji.
</tr>
<tr>
<td>Get zdarzeń, nowe zdarzenie, EngineEvent rejestru, Register-WmiEvent, zdarzenie usuwania wyrejestrować — zdarzenie
<td>Dostępne są dostępne, ale nie źródła zdarzeń.
<td>Polecenia programu PowerShell zdarzeń są obecne, ale większość źródła zdarzeń używanych z poleceniami (na przykład System.Timers.Timer) nie są dostępne w systemie Linux wprowadzania polecenia bezużyteczne w wersji alfa.
</tr>
<tr>
<td>Set-ExecutionPolicy
<td>Dostępne, ale nie działa.
<td>Zwraca komunikat nie jest obsługiwana na tej platformie. Zasady wykonywania jest zorientowanych na użytkownika "bezpieczeństwa taśmy" która pomaga zapobiegać wprowadzania kosztowne błędów przez użytkownika. Nie jest granicy zabezpieczeń.
</tr>
<tr>
<td>Nowe PSSessionOption nowe PSTransportOption
<td>Dostępne, ale New-PSSession nie działa.
<td>New-PSSessionOption i nowy PSTransportOption nie są obecnie weryfikowane pracę teraz, New-PSSession działa.
</tr>
</table>
