---
ms.date: 05/17/2018
keywords: Program PowerShell, core
title: Znane problemy dotyczące programu PowerShell w wersji 6.0
ms.openlocfilehash: ce40a1925e564fbd2c661e70ec36d3842d915dfe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085970"
---
# <a name="known-issues-for-powershell-60"></a>Znane problemy dotyczące programu PowerShell w wersji 6.0

## <a name="known-issues-for-powershell-on-non-windows-platforms"></a>Znane problemy dotyczące programu PowerShell na platformach innych niż Windows

Alfa wersje programu PowerShell w systemie Linux i macOS są prawie funkcjonalności, ale ma pewne ograniczenia znaczące i rozwiązaliśmy szereg problemów. Wydań beta programu PowerShell w systemie Linux i macOS są bardziej funkcjonalności i stabilne, niż w wersji alfa, ale nadal może zawiera zestaw funkcji, niektóre i może zawierać błędy. W niektórych przypadkach te problemy są po prostu błędy, które nie zostały jeszcze usunięte. W innych przypadkach (tak jak domyślne aliasy ls, cp, itp.), czekamy na opinie od społeczności dotyczące możliwości wprowadzania.

Uwaga: Z powodu podobieństwa wiele podstawowych podsystemów programu PowerShell w systemie Linux i macOS zwykle na tym samym poziomie dojrzałości zarówno w przypadku funkcji, jak i błędów. Z wyjątkiem wymienionych poniżej problemów w tej sekcji dotyczą obu systemów operacyjnych.

### <a name="case-sensitivity-in-powershell"></a>Uwzględnianie wielkości liter w programie PowerShell

W przeszłości program PowerShell został równomiernie bez uwzględniania wielkości liter, z pewnymi wyjątkami. W systemach operacyjnych podobnymi do systemu UNIX w systemie plików jest głównie wielkość liter i programu PowerShell jest zgodna ze standardem system plików; to jest dostępna za pośrednictwem na wiele sposobów, oczywiste i oczywiste.

#### <a name="directly"></a>bezpośrednio

- Podczas określania pliku w programie PowerShell, należy użyć odpowiedniej wielkości liter.

#### <a name="indirectly"></a>Pośrednio

- Jeśli skrypt próbuje załadować moduł, a nazwa modułu nie jest poprawna, a następnie ładowania modułu zakończy się niepowodzeniem. Może to spowodować problem z istniejących skryptów, jeśli nazwa, która odwołuje się do modułu nie pasuje do nazwy pliku.
- Uzupełnianie po naciśnięciu tabulatora będzie nie Ukończ automatycznie, jeśli wielkość liter nazwy pliku jest nieprawidłowy. Fragmentu, aby ukończyć musi być z uwzględnieniem wielkości liter prawidłowo. (Uzupełnianie jest rozróżniana wielkość liter, wpisz nazwę i typ elementu członkowskiego uzupełnienia).

### <a name="ps1-file-extensions"></a>. PS1 Rozszerzenia pliku

Skrypty programu PowerShell może kończyć się `.ps1` dla interpretera zrozumieć, jak można załadować i uruchomić je w bieżącym procesie. Uruchamianie skryptów w bieżącym procesie jest zwykle oczekiwane zachowanie programu PowerShell. `#!` Magiczna liczba mogą być dodawane do skryptu, który nie ma `.ps1` rozszerzenie, ale spowoduje, że skrypt do uruchomienia w nowym wystąpieniu programu PowerShell, uniemożliwiając skrypt pracy poprawnie podczas zamiany obiektów. (Uwaga: może to być pożądane zachowania, podczas wykonywania skryptu środowiska PowerShell z `bash` lub innego powłoki.)

### <a name="missing-command-aliases"></a>Brak aliasów poleceń

W systemie Linux/macOS, "aliasy wygody" dla podstawowych poleceń `ls`, `cp`, `mv`, `rm`, `cat`, `man`, `mount`, `ps` zostały usunięte. W Windows programu PowerShell zawiera zbiór aliasy mapowane na nazwy polecenia systemu Linux dla wygody użytkownika. Następujące aliasy zostały usunięte z domyślne programu PowerShell w dystrybucjach systemu Linux/macOS, dzięki czemu natywnego wykonywalnego do uruchomienia bez określania ścieżki.

Istnieją zalety i wady, aby to zrobić. Usuwanie aliasy udostępnia środowisko natywne polecenia użytkownikowi programu PowerShell, ale ogranicza funkcjonalność w powłoce, ponieważ natywnych poleceń zwracać ciągi zamiast obiektów.

> [!NOTE]
> Jest to obszar, w którym opinii szuka zespołu programu PowerShell.
> Co to jest preferowanym rozwiązaniem? Firma Microsoft pozostawić bez zmian lub Dodaj aliasy wygody, ponownie? Zobacz [wystawiać #929](https://github.com/PowerShell/PowerShell/issues/929).

### <a name="missing-wildcard-globbing-support"></a>Brak symbolu wieloznacznego (symboli wieloznacznych) pomocy technicznej

Obecnie program PowerShell tylko wykonuje rozwijanie symbolu wieloznacznego (symboli wieloznacznych), wbudowanych poleceń cmdlet na Windows i poleceń zewnętrznych lub plików binarnych, a także polecenia cmdlet w systemie Linux. Oznacza to, że polecenie, takie jak `ls
*.txt` zakończy się niepowodzeniem, ponieważ gwiazdka nie będą rozszerzane do dopasowania w nazwach plików. Można obejść to za pomocą ćwiczeń `ls (gci *.txt | % name)` lub po prostu, `gci *.txt` przy użyciu programu PowerShell wbudowanych równoważnik `ls`.

Zobacz [#954](https://github.com/PowerShell/PowerShell/issues/954) Aby przesłać nam swoją opinię na temat ulepszenia obsługi symboli wieloznacznych w systemie Linux/macOS.

### <a name="net-framework-vs-net-core-framework"></a>A .NET framework .NET Core Framework

Program PowerShell w systemach operacyjnych Linux/macOS korzysta z platformy .NET Core, która jest podzestawem pełnego .NET Framework na Microsoft Windows. Jest to istotne, ponieważ program PowerShell zapewnia bezpośredni dostęp do typów podstawowych framework, metod itd. W rezultacie skryptów uruchamianych na Windows może nie działać na platformach innych niż Windows z powodu różnic w struktury. Aby uzyskać więcej informacji na temat platformy .NET Core Framework Zobacz <https://dotnetfoundation.org/net-core>

Pojawienie [.NET Standard2.0](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/), .NET Core 2.0 będą następnie z powrotem w wielu tradycyjnych typów i metod obecne w pełny program .NET Framework. Oznacza to, że program PowerShell Core będzie można załadować wiele modułów programu Windows PowerShell tradycyjnych, bez żadnych modyfikacji. Możesz wykonać naszej platformy .NET Standard 2.0 powiązanych prac [tutaj](https://github.com/PowerShell/PowerShell/projects/4).

### <a name="redirection-issues"></a>Problemy z przekierowania

Przekierowywanie danych wejściowych nie jest obsługiwane w programie PowerShell na dowolnej platformie.
[Problem #1629](https://github.com/PowerShell/PowerShell/issues/1629)

Użyj `Get-Content` do zapisywania zawartości pliku z potokiem.

Przekierowane dane wyjściowe będą zawierać znacznika kolejności bajtów Unicode (BOM), gdy jest używane domyślne kodowanie UTF-8. Znak BOM będzie powodować problemy podczas pracy z narzędzia, które nie oczekuje lub podczas dołączania do pliku. Użyj `-Encoding Ascii` próbę zapisania tekstu ASCII, (który jest Unicode, nie będą mieć znak BOM).

> [!Note]
> zobacz [RFC0020](https://github.com/PowerShell/PowerShell-RFC/issues/71) Aby przesłać nam swoją opinię na temat zwiększania kodowania środowisko programu PowerShell Core na wszystkich platformach. Jesteśmy pracy do obsługi UTF-8 bez BOM i potencjalnie zmiana kodowania wartości domyślne dla różnych poleceń cmdlet między platformami.

### <a name="job-control"></a>Kontroli zadania

Brak obsługi kontroli zadania w programie PowerShell w systemie Linux/macOS.
`fg` i `bg` polecenia nie są dostępne.

W chwili obecnej, możesz użyć [zadań programu PowerShell](/powershell/module/microsoft.powershell.core/about/about_jobs) które działają na wszystkich platformach.

### <a name="remoting-support"></a>Obsługa komunikacji zdalnej

Obecnie program PowerShell Core obsługuje komunikacji zdalnej programu PowerShell (PSRP) za pośrednictwem usługi WS-Management za pomocą uwierzytelniania podstawowego w systemach macOS i Linux oraz przy użyciu uwierzytelniania NTLM w systemie Linux. (Uwierzytelnianie za pomocą protokołu Kerberos nie jest obsługiwane.)

Pracę dla niego komunikację zdalną z oparta na usłudze WSMan jest wykonywana [psl omi dostawcy](https://github.com/PowerShell/psl-omi-provider) repozytorium.

Program PowerShell Core obsługuje również komunikacji zdalnej programu PowerShell (PSRP) za pośrednictwem protokołu SSH na wszystkich platformach (Windows, macOS i Linux). Chociaż nie jest to obecnie obsługiwane w środowisku produkcyjnym, znajdziesz więcej informacji na temat konfigurowania [tutaj](../core-powershell/ssh-remoting-in-powershell-core.md).

### <a name="just-enough-administration-jea-support"></a>Obsługa Just dostatecznie Administration (JEA)

Możliwość tworzenia ograniczone administracji punktów końcowych usług zdalnych (JEA) nie jest obecnie dostępna w programie PowerShell w systemie Linux/macOS. Ta funkcja jest obecnie w zakresie 6.0 i coś, co firma Microsoft będzie wpis 6.0 wziąć pod uwagę wymaga, aby prace projektowe znaczące.

### <a name="sudo-exec-and-powershell"></a>`sudo`, `exec`, jak i programu PowerShell

Ponieważ program PowerShell działa większość używanych poleceń w pamięci (na przykład języka Python lub Ruby), nie można użyć "sudo" bezpośrednio za pomocą programu PowerShell elementy wbudowane. (Mogą oczywiście uruchamiać `pwsh` z "sudo".) Jeśli to konieczne do uruchamiania polecenia cmdlet programu PowerShell z wnętrza programu PowerShell przy użyciu programu sudo, na przykład `sudo Set-Date 8/18/2016`, a następnie należy wykonać `sudo pwsh Set-Date 8/18/2016`. Podobnie można wykonać exec programu PowerShell, które są wbudowane bezpośrednio. Zamiast tego trzeba wykonać `exec pwsh item_to_exec`.

Ten problem, obecnie jest śledzona jako część [#3232](https://github.com/PowerShell/PowerShell/issues/3232).

### <a name="missing-cmdlets"></a>Brak polecenia cmdlet

Dużej liczby poleceń (polecenia cmdlet) zwykle dostępne w programie PowerShell nie są dostępne w systemie Linux/macOS. W wielu przypadkach te polecenia nie ma sensu na tych platformach (np. funkcji specyficznych dla Windows, takich jak rejestr). Innych poleceń, takich jak polecenia sterowania usługi (Get/Start/Stop-Service) są obecne, ale nie działa. Przyszłe wersje będą rozwiązać te problemy, ustalania uszkodzone poleceń cmdlet i dodaje nowe wraz z upływem czasu.

### <a name="command-availability"></a>Dostępność poleceń

Poniższa tabela zawiera listę poleceń, które są znane, nie będą działać w programie PowerShell w systemie Linux/macOS.

|Polecenia|Stan operacyjny|Uwagi|
|--------|-----------------|-----|
|`Get-Service`, `New-Service`, `Restart-Service`, `Resume-Service`, `Set-Service`, `Start-Service`, `Stop-Service`, `Suspend-Service`|Nie jest dostępna.|Te polecenia nie zostanie rozpoznana. Ten problem powinien rozwiązany w przyszłej wersji.|
|`Get-Acl`, `Set-Acl`|Niedostępne.|Te polecenia nie zostanie rozpoznana. Ten problem powinien rozwiązany w przyszłej wersji.|
|`Get-AuthenticodeSignature`, `Set-AuthenticodeSignature`|Niedostępne.|Te polecenia nie zostanie rozpoznana. Ten problem powinien rozwiązany w przyszłej wersji.|
|`Wait-Process`|Dostępne, nie działa prawidłowo. |Na przykład `Start-Process gvim -PassThru | Wait-Process` nie działa; nie jest on oczekiwania na proces.|
|`Register-PSSessionConfiguration`, `Unregister-PSSessionConfiguration`, `Get-PSSessionConfiguration`|Dostępne, ale nie działa.|Zapisuje komunikat o błędzie wskazujący, że nie działają polecenia. Powinny one rozwiązany w przyszłej wersji.|
|`Get-Event`, `New-Event`, `Register-EngineEvent`, `Register-WmiEvent`, `Remove-Event`, `Unregister-Event`|Dostępne są dostępne, ale żadnych źródeł zdarzeń.|Polecenia programu PowerShell obsługi zdarzeń są obecne, ale większość źródeł zdarzeń użycia z poleceniami (na przykład System.Timers.Timer) nie są dostępne w systemie Linux, co polecenia bezużyteczne w wersji Alpha.|
|`Set-ExecutionPolicy`|Dostępne, ale nie działa.|Zwraca powiedzenie wiadomości nie jest obsługiwana na tej platformie. Zasady wykonywania jest skoncentrowane na użytkownika "pas bezpieczeństwa" ułatwiająca uniemożliwić użytkownikowi wprowadzanie błędami kosztowne. Nie jest granicy zabezpieczeń.|
|`New-PSSessionOption`, `New-PSTransportOption`|Dostępne, ale `New-PSSession` nie działa.|`New-PSSessionOption` i `New-PSTransportOption` obecnie nie są weryfikowane teraz pracę, która `New-PSSession` działa.|
