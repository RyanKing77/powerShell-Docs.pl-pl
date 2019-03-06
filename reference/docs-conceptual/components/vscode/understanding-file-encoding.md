---
title: Opis kodowania pliku w programie VSCode i PowerShell
description: Skonfiguruj kodowanie pliku VSCode i programu PowerShell
ms.date: 02/28/2019
ms.openlocfilehash: 9cf445ebd0c2bb2dbdf4438f02dafe3df3a5d1e2
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429809"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a>Opis kodowania pliku w programie VSCode i PowerShell

Używając programu VS Code do tworzenia i edytowania skryptów programu PowerShell, jest ważne, czy pliki są zapisywane w formacie kodowania znaków jest prawidłowa.

## <a name="what-is-file-encoding-and-why-is-it-important"></a>Co to jest kodowanie pliku i dlaczego jest ważna?

VSCode zarządza interfejs między ludzi, wprowadzanie ciągów znaków w buforze i bloków odczytu/zapisu bajtów w systemie plików. Gdy plik jest zapisywany VSCode, używa kodowania w tym celu tekstu.

Podobnie uruchomienie skryptu programu PowerShell ją przekonwertować bajtów w pliku znaków, aby odtworzyć go do programu PowerShell. Ponieważ VSCode zapisuje plik i programu PowerShell odczytuje plik, muszą używać tego samego systemu kodowania. Prowadzi to proces analizowania skrypt programu PowerShell: *bajtów* -> *znaków* -> *tokenów*  ->   *drzewo abstrakcyjnej składni* -> *wykonywania*.

Zarówno VSCode, jak i programu PowerShell są instalowane z rozsądne domyślną konfigurację kodowania. Jednak domyślne kodowanie używane przez program PowerShell został zmieniony wraz z wydaniem programu PowerShell Core (6.x). Aby upewnić się, nie problemów przy użyciu programu PowerShell lub rozszerzenia programu PowerShell w VSCode, należy skonfigurować ustawienia programu VSCode i programu PowerShell prawidłowo.

## <a name="common-causes-of-encoding-issues"></a>Typowe przyczyny problemów z kodowaniem

Kodowania problemy występują, gdy kodowanie VSCode lub pliku skryptu nie są zgodne oczekiwane kodowanie programu PowerShell. Nie ma możliwości dla programu PowerShell, aby automatycznie określić kodowanie pliku.

Wszystko jest bardziej prawdopodobne kodowanie problemy podczas korzystania z znaków nie [7-bitowego zestawu znaków ASCII](https://ascii.cl/). Przykład:

- Akcentowanie znaków łaciński (`É`, `ü`)
- Znaki inne niż łacińskie, takich jak cyrylica (`Д`, `Ц`)
- Chiński Hanowi (`脚`, `本`)

Typowe przyczyny problemów z kodowaniem są:

- Kodowanie VSCode i programu PowerShell nie została zmieniona z ustawień domyślnych. Programu PowerShell 5.1 i poniżej domyślne kodowanie różni się od VSCode firmy.
- Inny edytor otworzył i zastąpić plik przy użyciu nowego kodowania. To często zdarza się przy użyciu środowiska ISE.
- Plik jest sprawdzany do kontroli źródła przy użyciu kodowania, która różni się od jakich VSCode lub programu PowerShell oczekuje. Może to nastąpić, korzystając z współpracowników edytorów z różnymi konfiguracjami kodowania.

### <a name="how-to-tell-when-you-have-encoding-issues"></a>Jak sprawdzić, jeśli masz problemy z kodowaniem

Błędy kodowania często są one widoczne jako analizy błędów w skryptach. Jeśli okaże się sekwencje znaków dziwne w skrypcie, może to być problem. W przykładzie poniżej półpauzę (`–`) jest wyświetlana jako znaki `â€“`:

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

Ten problem występuje, ponieważ VSCode koduje znak `–` w formacie UTF-8, jako bajtów `0xE2 0x80 0x93`.
Kiedy bajty te są zdekodowany jako Windows-1252, są interpretowane jako znaki `â€“`.

Niektóre sekwencje znaków dziwne, które można napotkać obejmują:

- `â€“` Zamiast `–`
- `â€”` Zamiast `—`
- `Ã„2` Zamiast `Ä`
- `Â` zamiast ` ` (spacja nierozdzielająca)
- `Ã©` Zamiast `é`

Przydatne w tym [odwołania](https://www.i18nqa.com/debug/utf8-debug.html) zawiera listę typowych wzorców, które wskazują na problem kodowania UTF-8/Windows-1252.

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a>Jak działa rozszerzenie PowerShell VSCode współdziała z kodowania

Rozszerzenie PowerShell wchodzi w interakcję z skrypty na kilka sposobów:

1. Podczas edytowania skryptów w VSCode, zawartość są wysyłane przez VSCode do rozszerzenia. [Language Server Protocol][] określającemu, że ta zawartość jest przesyłany w formacie UTF-8. W związku z tym nie jest możliwe dla rozszerzenia Aby pobrać błędne szyfrowanie.
2. Gdy skryptów są wykonywane bezpośrednio w konsoli programu zintegrowanego, są odczytywane z pliku programu PowerShell, bezpośrednio. Jeśli kodowanie programu PowerShell różni się od firmy VSCode, coś tutaj można wprowadzić problem.
3. Gdy skrypt, który jest otwarty w VSCode odwołuje się do innego skryptu, który nie jest otwarty w VSCode, rozszerzenie przechodzi do ładowania zawartości tego skryptu z systemu plików. Rozszerzenie programu PowerShell, wartością domyślną jest kodowanie UTF-8, ale używa [znacznika kolejności bajtów][], lub znak BOM, wykrywania, aby wybrać poprawne kodowanie.

Ten problem występuje, gdy przy założeniu kodowanie formatów bez znaku BOM (takich jak [UTF-8][] z znak BOM nie i [Windows-1252][]).
Rozszerzenie PowerShell wartość domyślna to UTF-8. Rozszerzenie nie można zmienić ustawienia kodowania VSCode firmy.
Aby uzyskać więcej informacji, zobacz [wystawiać #824](https://github.com/Microsoft/vscode/issues/824).

## <a name="choosing-the-right-encoding"></a>Wybierając odpowiednie kodowania

Różne systemy i aplikacje mogą używać różnych kodowań:

- W programie .NET Standard w Internecie lub w środowisku systemu Linux, UTF-8 jest teraz kodowanie dominującego.
- Używana w wielu aplikacjach .NET Framework [UTF-16][]. Historyczne ze względu na jest to czasami nazywane "Unicode", która teraz termin odnosi się do szerokiego [standardowa](https://en.wikipedia.org/wiki/Unicode) zawierającej UTF-16 i UTF-8.
- W Windows wiele aplikacji natywnych, które powstały wcześniej niż Unicode nadal używać Windows-1252 domyślnie.

Kodowania Unicode mają również koncepcji kolejności bajtów (BOM) znaku. BOM występować na początku tekstu mówić dekoder, kodowania, która używa tekstu. Dla wielobajtowego kodowania, wskazuje także BOM [kolejność bajtów](https://en.wikipedia.org/wiki/Endianness) kodowania. BOM mają być bajtów, które rzadko występują w tekstu innego niż Unicode, dzięki czemu uzasadnione przypuszczenie, że tekst jest Unicode, jeśli występuje znak BOM.

BOM są opcjonalne i ich wdrażania nie jest tak popularne w środowisku systemu Linux, ponieważ niezawodną Konwencji UTF-8 są używane wszędzie. Większość aplikacji systemu Linux zakładają, że wprowadzanie tekstu jest zakodowany w formacie UTF-8. Gdy wiele aplikacji systemu Linux rozpozna i zapewnia prawidłowej obsługi znak BOM, liczbą nie, co prowadzi do artefaktów w tekście modyfikować za pomocą tych aplikacji.

**W związku z tym**:

- Pracujesz przede wszystkim z aplikacji Windows i programu Windows PowerShell, należy najpierw kodowania, takich jak UTF-8 z BOM lub UTF-16.
- Jeśli pracujesz na platformach preferowaną UTF-8 z BOM.
- Jeśli użytkownik pracuje się głównie w kontekstach skojarzone z systemem Linux, preferowaną UTF-8 bez BOM.
- Windows-1252 i latin-1 są zasadniczo starszych kodowania, które należy unikać, jeśli jest to możliwe.
  Jednak niektóre starsze aplikacje Windows może zależą od nich.
- Warto również zauważyć, że skrypt podpisywania [kodowanie zależne od](https://github.com/PowerShell/PowerShell/issues/3466), co oznacza zmianę kodowania na podpisanych skryptów będzie wymagać ponownego podpisywania.

## <a name="configuring-vscode"></a>Konfigurowanie programu VSCode

Dla programu VSCode domyślnym kodowaniem jest UTF-8 bez BOM.

Aby ustawić [Kodowanie dla programu VSCode][], przejdź do ustawień programu VSCode (<kbd>Ctrl<kbd>+</kbd>,</kbd>) i ustaw `"files.encoding"` ustawienia:

```json
"files.encoding": "utf8bom"
```

Niektóre możliwe wartości to:

- `utf8`: [UTF-8] bez BOM
- `utf8bom`: [UTF-8] z BOM
- `utf16le`: Little endian [UTF-16]
- `utf16be`: Big endian [UTF-16]
- `windows1252`: [Windows-1252]

Należy uzyskać listę rozwijaną dla tego w widoku graficznego interfejsu użytkownika lub wyświetlić uzupełnienia go w formacie JSON.

Na automatyczne wykrywanie kodowania, gdy jest to możliwe, można również dodać następujące czynności:

```json
"files.autoGuessEncoding": true
```

Jeśli nie chcesz, aby te ustawienia mają wpływ na wszystkie typy plików, programu VSCode umożliwia także konfiguracje między językami. Utwórz ustawienie specyficzne dla języka, umieszczając ustawienia `[<language-name>]` pola. Przykład:

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a>Konfigurowanie programu PowerShell

W programie PowerShell domyślne kodowanie różni się zależnie od wersji:

- W programie PowerShell 6 + kodowanie domyślne to UTF-8 bez BOM na wszystkich platformach.
- W programie Windows PowerShell, domyślnym kodowaniem jest zwykle Windows-1252, rozszerzenie [latin 1][], znanego również jako ISO 8859-1.

W programie PowerShell 5 + można znaleźć domyślnego kodowania w tym:

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

Następujące [skryptu](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) może służyć do określenia wnioskuje co kodowanie sesji programu PowerShell dla skryptu bez BOM.

```powershell
$badBytes = [byte[]]@(0xC3, 0x80)
$utf8Str = [System.Text.Encoding]::UTF8.GetString($badBytes)
$bytes = [System.Text.Encoding]::ASCII.GetBytes('Write-Output "') + [byte[]]@(0xC3, 0x80) + [byte[]]@(0x22)
$path = Join-Path ([System.IO.Path]::GetTempPath()) 'encodingtest.ps1'

try
{
    [System.IO.File]::WriteAllBytes($path, $bytes)

    switch (& $path)
    {
        $utf8Str
        {
            return 'UTF-8'
            break
        }

        default
        {
            return 'Windows-1252'
            break
        }
    }
}
finally
{
    Remove-Item $path
}
```

Istnieje możliwość konfigurowania programu PowerShell do korzystania z kodowaniem danego ogólnie za pomocą ustawień profilu. Zobacz następujące artykuły:

- [@mklement0]firmy [odpowiedziami dotyczącymi programu PowerShell kodowania na stronie StackOverflow](https://stackoverflow.com/a/40098904).
- [@rkeithhill]firmy [wpis w blogu o obsłudze wprowadzania bez BOM UTF-8 w programie PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).

Nie jest możliwe wymusić programu PowerShell do korzystania z określonego kodowania danych wejściowych. Program PowerShell 5.1 i poniżej domyślnie Windows-1252, kodowanie, gdy znak BOM nie istnieje. Ze względu na współdziałanie najlepiej jest zapisać skrypty w formacie Unicode, za pomocą znak BOM.

> [!IMPORTANT]
> Jakichkolwiek innych narzędzi, masz tego touch programu PowerShell, skryptów mogą mieć wpływ na wybór kodowania lub ponownie zakodować skrypty do innego kodowania.

### <a name="existing-scripts"></a>Istniejące skrypty

Skrypty już w systemie plików może być konieczne do zakodowania ponownie wybrany nowy kodowania. W dolnym pasku VSCode będzie wyświetlana etykieta UTF-8. Kliknij go, aby otworzyć pasek akcji, a następnie wybierz pozycję **Zapisz z kodowaniem**. Teraz możesz wybrać nowe kodowanie dla tego pliku. Zobacz [Kodowanie dla programu VSCode][] pełne instrukcje.

Jeśli potrzebujesz ponownie zakodować wiele plików, można użyć następującego skryptu:

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a>PowerShell Integrated Scripting środowiska (ISE)

Możesz również edytować skrypty przy użyciu programu PowerShell ISE, należy zsynchronizować swoje ustawienia kodowania.

Środowiska ISE należy uwzględnić znak BOM, ale jest również możliwe użycie odbicia do [Ustawianie kodowania](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).
Należy pamiętać o tym, czy nie byłoby to utrwalone między startupy.

### <a name="source-control-software"></a>Oprogramowanie do kontroli źródła

Niektóre narzędzia do kontroli źródła, takich jak git, ignorowanie kodowania; System git śledzi tylko bajtów.
Inne, takie jak TFS lub Mercurial, nie. Nawet z niektórych narzędzi opartych o git zależy od tego, dekodowanie tekstu.

Gdy jest to możliwe, upewnij się, że:

- Skonfiguruj kodowanie w kontroli źródła aby dopasować go do konfiguracji programu VSCode tekstu.
- Upewnij się, że wszystkie pliki są zaewidencjonowane do kontroli źródła przy użyciu odpowiednich kodowania.
- Uważaj, zmian kodowanie otrzymane za pomocą kontroli źródła. Klucza znak ten jest różnic wskazujący zmiany, ale gdy nic nie wydaje się, że zostały zmienione (ponieważ masz bajtów, ale znaki nie).

### <a name="collaborators-environments"></a>Współpracowników i środowiska

Na podstawie Konfigurowanie kontroli źródła, upewnij się, że współpracownicy w taki sposób, na wszystkie pliki, które możesz udostępniać nie ustawień, które zastępują kodowania przez ponowne kodowanie plików, programu PowerShell.

### <a name="other-programs"></a>Inne programy

Inny program, który odczytuje lub zapisuje skrypt programu PowerShell ponownie zakodować go.

Niektóre przykłady to:

- Korzystanie ze Schowka do kopiowania i wklejania skryptu. To jest typowe w przypadku takich scenariuszy:
  - Kopiowanie skrypt do maszyny Wirtualnej
  - Kopiowanie skryptu z wiadomości e-mail lub strony sieci Web
  - Kopiowanie skrypt do lub z dokumentu Microsoft Word lub PowerPoint
- Inne edytory tekstu, takie jak:
  - Notepad
  - vim
  - Inne Edytor skryptów programu PowerShell
- Edycji tekstu, narzędzia, takie jak:
  - `Get-Content`/`Set-Content`/`Out-File`
  - Operatorów przekierowania programu PowerShell, takie jak `>` i `>>`
  - `sed`/`awk`
- Plik transferu programów, takich jak:
  - Przeglądarka sieci web, podczas pobierania skryptów
  - Udział plików

Niektóre z tych narzędzi postępowania w bajtach, a nie na tekst, ale oferują inne konfiguracje kodowania. W przypadkach, gdzie należy skonfigurować, kodowania musisz wprowadzić takie same jak edytor kodowania, aby uniknąć problemów.

## <a name="other-resources-on-encoding-in-powershell"></a>Inne zasoby, kodując go w programie PowerShell

Istnieje kilka innych nieuprzywilejowany wpisy na kodowanie i konfigurowanie kodowania w programie PowerShell, które są warte odczytu:

- [@mklement0]firmy [podsumowania PowerShell kodowania na stronie StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)
- Wcześniejsze numery otwarta w programie PowerShell vscode kodowania problemy:
  - [#1308](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [#1628](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [#1680](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [#1744](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [#1751](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [Klasycznym *Joel oprogramowania* Opisz Unicode](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [Kodowanie w .NET Standard](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin 1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[znacznika kolejności bajtów]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[Language Server Protocol]: https://microsoft.github.io/language-server-protocol/
[Kodowanie dla programu VSCode]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
