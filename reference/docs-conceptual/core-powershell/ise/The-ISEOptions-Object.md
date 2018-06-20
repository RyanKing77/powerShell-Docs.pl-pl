---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISEOptions
ms.assetid: 75e2a76f-f3d1-490b-ad5d-e3829946aabb
ms.openlocfilehash: e756da21aaa5465f7fa6a90563b4180f0c89e87b
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953654"
---
# <a name="the-iseoptions-object"></a>Obiekt ISEOptions

**ISEOptions** obiekt reprezentuje różne ustawienia dla programu Windows PowerShell ISE. To wystąpienie **Microsoft.PowerShell.Host.ISE.ISEOptions** klasy.

**ISEOptions** obiektu udostępnia następujące metody i właściwości.

## <a name="methods"></a>Metody

### <a name="restoredefaultconsoletokencolors"></a>RestoreDefaultConsoleTokenColors\(\)

Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

Przywraca domyślne wartości tokenu kolorów w okienku konsoli.

```powershell
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = 'red'
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a>RestoreDefaults\(\)

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Przywraca wartości domyślne wszystkich ustawień opcje w okienku konsoli. Resetuje ono również zachowanie różnych komunikaty ostrzegawcze, które zapewniają standardowe pole wyboru, aby zapobiec wiadomość ponownie wyświetlone.

```powershell
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = 'orange'
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a>RestoreDefaultTokenColors\(\)

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Przywraca domyślne wartości tokenu kolorów w okienku skryptów.

```powershell
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a>RestoreDefaultXmlTokenColors\(\)

Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

Przywraca ustawienia domyślne tokenu kolorów dla elementów XML, które są wyświetlane w środowisku Windows PowerShell ISE. Zobacz też [XmlTokenColors](#xmltokencolors).

```powershell
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a>Właściwości

### <a name="autosaveminuteinterval"></a>AutoSaveMinuteInterval

Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

Określa liczbę minut między operacjami automatycznego zapisywania plików przez program Windows PowerShell ISE. Wartość domyślna to 2 minuty. Wartość jest liczbą całkowitą.

```powershell
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a>CommandPaneBackgroundColor

Ta funkcja znajduje się w programie Windows PowerShell ISE 2.0, ale została usunięta lub zmieniona w nowszej wersji programu ISE.  W przypadku nowszych wersji, zobacz [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).

Określa kolor tła okienka polecenia. To wystąpienie **System.Windows.Media.Color** klasy.

```powershell
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = 'orange'
```

### <a name="commandpaneup"></a>CommandPaneUp

Ta funkcja znajduje się w programie Windows PowerShell ISE 2.0, ale została usunięta lub zmieniona w nowszej wersji programu ISE.

Określa, czy w okienku polecenia znajduje się powyżej w okienku danych wyjściowych.

```powershell
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true
```

### <a name="consolepanebackgroundcolor"></a>ConsolePaneBackgroundColor

Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

Określa kolor tła okienka konsoli. To wystąpienie **System.Windows.Media.Color** klasy.

```powershell
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = 'red'
```

### <a name="consolepaneforegroundcolor"></a>ConsolePaneForegroundColor

Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

Określa kolor tekstu w okienku konsoli.

```powershell
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = 'yellow'
```

### <a name="consolepanetextbackgroundcolor"></a>ConsolePaneTextBackgroundColor

Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

Określa kolor tła tekstu w okienku konsoli.

```powershell
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = 'pink'
```

### <a name="consoletokencolors"></a>ConsoleTokenColors

Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

Określa kolory tokenów IntelliSense w okienku konsoli programu Windows PowerShell ISE. Ta właściwość jest obiekt słownika zawierający pary nazwa/wartość typy tokenów i kolorów dla tego okienka konsoli. Aby zmienić kolory tokenów IntelliSense w okienku skryptów, zobacz [TokenColors](#tokencolors). Aby przywrócić wartości domyślne kolory, zobacz [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors). Kolory tokenu można ustawić dla następujących: atrybut, polecenia, CommandArgument, CommandParameter, komentarza, GroupEnd, GroupStart, — słowo kluczowe, LineContinuation, LoopLabel, elementu członkowskiego, nowego wiersza, numer, operatora, pozycji, StatementSeparator, ciągu, typu, Nieznany, zmiennej.

```powershell
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = 'green'
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = 'magenta'
```

### <a name="debugbackgroundcolor"></a>DebugBackgroundColor

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Określa kolor tła dla debugowania tekst wyświetlany w okienku konsoli. To wystąpienie **System.Windows.Media.Color** klasy.

```powershell
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor = '#0000FF'
```

### <a name="debugforegroundcolor"></a>DebugForegroundColor

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Określa kolor pierwszego planu dla debugowania tekst wyświetlany w okienku konsoli. To wystąpienie **System.Windows.Media.Color** klasy.

```powershell
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor = 'yellow'
```

### <a name="defaultoptions"></a>DefaultOptions

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Zbiór właściwości, które określają ma być używany podczas resetowania metody są używane wartości domyślne.

```powershell
# Displays the name of the default options. This example is from ISE 4.0.
$psISE.Options.DefaultOptions

SelectedScriptPaneState                   : Top
ShowDefaultSnippets                       : True
ShowToolBar                               : True
ShowOutlining                             : True
ShowLineNumbers                           : True
TokenColors                               : {[Attribute, #FF00BFFF], [Command, #FF0000FF], [CommandArgument, #FF8A2BE2], [CommandParameter, #FF000080]...}
ConsoleTokenColors                        : {[Attribute, #FFB0C4DE], [Command, #FFE0FFFF], [CommandArgument, #FFEE82EE], [CommandParameter, #FFFFE4B5]...}
XmlTokenColors                            : {[Comment, #FF006400], [CommentDelimiter, #FF008000], [ElementName, #FF8B0000], [MarkupExtension, #FFFF8C00]...}
DefaultOptions                            : Microsoft.PowerShell.Host.ISE.ISEOptions
FontSize                                  : 9
Zoom                                      : 100
FontName                                  : Lucida Console
ErrorForegroundColor                      : #FFFF0000
ErrorBackgroundColor                      : #00FFFFFF
WarningForegroundColor                    : #FFFF8C00
WarningBackgroundColor                    : #00FFFFFF
VerboseForegroundColor                    : #FF00FFFF
VerboseBackgroundColor                    : #00FFFFFF
DebugForegroundColor                      : #FF00FFFF
DebugBackgroundColor                      : #00FFFFFF
ConsolePaneBackgroundColor                : #FF012456
ConsolePaneTextBackgroundColor            : #FF012456
ConsolePaneForegroundColor                : #FFF5F5F5
ScriptPaneBackgroundColor                 : #FFFFFFFF
ScriptPaneForegroundColor                 : #FF000000
ShowWarningForDuplicateFiles              : True
ShowWarningBeforeSavingOnRun              : True
UseLocalHelp                              : True
AutoSaveMinuteInterval                    : 2
MruCount                                  : 10
ShowIntellisenseInConsolePane             : True
ShowIntellisenseInScriptPane              : True
UseEnterToSelectInConsolePaneIntellisense : True
UseEnterToSelectInScriptPaneIntellisense  : True
IntellisenseTimeoutInSeconds              : 3
```

### <a name="errorbackgroundcolor"></a>ErrorBackgroundColor

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Określa kolor tła dla błędu tekst wyświetlany w okienku konsoli. To wystąpienie **System.Windows.Media.Color** klasy.

```powershell
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor = 'black'
```

### <a name="errorforegroundcolor"></a>ErrorForegroundColor

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Określa kolor pierwszego planu błąd tekst wyświetlany w okienku konsoli. To wystąpienie **System.Windows.Media.Color** klasy.

```powershell
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor = 'green'
```

### <a name="fontname"></a>FontName

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Określa nazwę czcionki aktualnie używane zarówno w okienku skryptów, jak i w okienku konsoli.

```powershell
# Changes the font used in both panes.
$psISE.Options.FontName = 'Courier New'
```

### <a name="fontsize"></a>FontSize

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Określa rozmiar czcionki jako liczba całkowita. Jest on używany w okienku skryptów, w okienku polecenia i w okienku danych wyjściowych. Prawidłowy zakres wartości to 8 do 32.

```powershell
# Changes the font size in all panes.
$psISE.Options.FontSize = 20
```

### <a name="intellisensetimeoutinseconds"></a>IntellisenseTimeoutInSeconds

Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

Określa liczbę sekund, używanych przez IntelliSense spróbować rozwiązać obecnie tekstu. Po następującej liczbie sekund IntelliSense upłynie limit czasu i umożliwia kontynuowanie, wpisując polecenie. Wartość domyślna to 3 sekundy. Wartość jest liczbą całkowitą.

```powershell
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a>MruCount

Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

Określa liczbę ostatnio otwartych plików, które programu Windows PowerShell ISE śledzi i wyświetlane w dolnej części **Otwórz plik** menu. Wartość domyślna to 10. Wartość jest liczbą całkowitą.

```powershell
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a>OutputPaneBackgroundColor

Ta funkcja znajduje się w programie Windows PowerShell ISE 2.0, ale została usunięta lub zmieniona w nowszej wersji programu ISE.  W przypadku nowszych wersji, zobacz [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).

Właściwość odczytu/zapisu, która pobiera lub ustawia kolor tła okienka wyjściowego samej siebie. To wystąpienie **System.Windows.Media.Color** klasy.

```powershell
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = 'gold'
```

### <a name="outputpanetextforegroundcolor"></a>OutputPaneTextForegroundColor

Ta funkcja znajduje się w programie Windows PowerShell ISE 2.0, ale została usunięta lub zmieniona w nowszej wersji programu ISE.  W przypadku nowszych wersji, zobacz [ConsolePaneForegroundColor](#consolepaneforegroundcolor).

Właściwości odczytu/zapisu, która zmienia kolor tekstu w okienku danych wyjściowych w programie Windows PowerShell ISE 2.0.

```powershell
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = 'blue'
```

### <a name="outputpanetextbackgroundcolor"></a>OutputPaneTextBackgroundColor

Ta funkcja znajduje się w programie Windows PowerShell ISE 2.0, ale została usunięta lub zmieniona w nowszej wersji programu ISE.  W przypadku nowszych wersji, zobacz [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).

Właściwości odczytu/zapisu, która zmienia kolor tła tekstu w okienku danych wyjściowych.

```powershell
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = 'pink'
```

### <a name="scriptpanebackgroundcolor"></a>ScriptPaneBackgroundColor

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Właściwości odczytu/zapisu, która pobiera lub ustawia kolor tła dla plików. To wystąpienie **System.Windows.Media.Color** klasy.

```powershell
# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'
```

### <a name="scriptpaneforegroundcolor"></a>ScriptPaneForegroundColor

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Właściwości odczytu/zapisu, która pobiera lub ustawia kolor pierwszego planu dla plików z systemem innym niż skryptu w okienku skryptów.
Aby ustawić kolor pierwszego planu dla plików skryptów, użyj [TokenColors](#tokencolors).

```powershell
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = 'green'
```

### <a name="selectedscriptpanestate"></a>SelectedScriptPaneState

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Właściwość odczytu/zapisu, która pobiera lub Ustawia położenie okienka Skrypt na ekranie. Ten ciąg może być "Maximized", "Top" lub "Right".

```powershell
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = 'Top'
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = 'Right'
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = 'Maximized'
```

### <a name="showdefaultsnippets"></a>ShowDefaultSnippets

Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

Określa, czy **CTRL + J** lista fragmentów zawiera zestaw starter, który znajduje się w programie Windows PowerShell. Jeśli wartość **$false**, tylko wstawki zdefiniowane przez użytkownika są wyświetlane w **CTRL + J** listy. Wartość domyślna to **$true**.

```powershell
# Hide the default snippets from the CTRL+J list.
$psISE.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a>ShowIntellisenseInConsolePane

Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

Określa, czy IntelliSense oferuje składni, parametrów i sugestie wartość w okienku konsoli. Wartość domyślna to **$true**.

```powershell
# Turn off IntelliSense in the console pane.
$psISE.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a>ShowIntellisenseInScriptPane

Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

Określa, czy IntelliSense oferuje składni, parametrów i sugestie wartość w okienku skryptów. Wartość domyślna to **$true**.

```powershell
# Turn off IntelliSense in the Script pane.
$psISE.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a>ShowLineNumbers

Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

Określa, czy w okienku skryptu Wyświetla numery wierszy na lewym marginesie. Wartość domyślna to **$true**.

```powershell
# Turn off line numbers in the Script pane.
$psISE.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a>ShowOutlining

Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

Określa, czy w okienku skryptu Wyświetla rozwijanej i zwijanej nawiasy obok fragmentów kodu na lewym marginesie. Gdy są one wyświetlane, możesz kliknąć minus \( - \) ikonami obok bloku tekstu, aby zwinąć lub kliknij przycisk plus \( + \) , aby rozwinąć blok tekstu. Wartość domyślna to **$true**.

```powershell
# Turn off outlining in the Script pane.
$psISE.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a>ShowToolBar

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Określa, czy pasek narzędzi ISE pojawia się w górnej części okna programu Windows PowerShell ISE. Wartość domyślna to **$true**.

```powershell
# Show the toolbar.
$psISE.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a>ShowWarningBeforeSavingOnRun

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Określa, czy jest wyświetlany komunikat ostrzegawczy, gdy przed uruchomieniem skryptu jest zapisywany automatycznie. Wartość domyślna to **$true**.

```powershell
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun = $true
```

### <a name="showwarningforduplicatefiles"></a>ShowWarningForDuplicateFiles

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Określa, czy jest wyświetlany komunikat ostrzegawczy, gdy ten sam plik jest otwarty na różnych kartach programu PowerShell. Jeśli ustawiono **$true**, aby otworzyć ten sam plik w wielu kartach wyświetla ten komunikat: "skopiuj ten plik jest otwarty w innej karty środowiska Windows PowerShell. Zmiany wprowadzone w tym pliku wpłynie na wszystkie otwarte kopie". Wartość domyślna to **$true**.

```powershell
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true
```

### <a name="tokencolors"></a>TokenColors

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Określa kolory tokenów IntelliSense w okienku skryptów programu Windows PowerShell ISE. Ta właściwość jest obiekt słownika zawierający pary nazwa/wartość typy tokenów i kolorów dla tego okienka skryptu. Aby zmienić kolory tokenów IntelliSense w okienku konsoli, zobacz [ConsoleTokenColors](#consoletokencolors). Aby przywrócić wartości domyślne kolory, zobacz [RestoreDefaultTokenColors](#restoredefaulttokencolors). Kolory tokenu można ustawić dla następujących: atrybut, polecenia, CommandArgument, CommandParameter, komentarza, GroupEnd, GroupStart, — słowo kluczowe, LineContinuation, LoopLabel, elementu członkowskiego, nowego wiersza, numer, operatora, pozycji, StatementSeparator, ciągu, typu, Nieznany, zmiennej.

```powershell
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"
```

### <a name="useentertoselectinconsolepaneintellisense"></a>UseEnterToSelectInConsolePaneIntellisense

Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

Określa, czy można używać klawisz Enter, aby wybrać IntelliSense Podana opcja w okienku konsoli. Wartość domyślna to **$true**.

```powershell
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $false
```

### <a name="useentertoselectinscriptpaneintellisense"></a>UseEnterToSelectInScriptPaneIntellisense

Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

Określa, czy można używać klawisza Enter, aby wybrać opcję dostarczane do funkcji IntelliSense w okienku skryptów. Wartość domyślna to **$true**.

```powershell
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $true
```

### <a name="uselocalhelp"></a>UseLocalHelp

Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

Określa, czy Pomocy zainstalowanej lokalnie lub w trybie online TechNet Library pomocy jest wyświetlany, gdy kursor w słowach kluczowych naciśnij klawisz F1. Jeśli ustawiono **$true**, a następnie okno podręczne Wyświetla zawartość z pomocy instalowana lokalnie. Pliki Pomocy można zainstalować, uruchamiając `Update-Help` polecenia. Jeśli ustawiono **$false**, a następnie otwiera przeglądarkę na stronę w bibliotece TechNet.

```powershell
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp = $false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp = $true
```

### <a name="verbosebackgroundcolor"></a>VerboseBackgroundColor

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Określa kolor tła pełny tekst wyświetlany w okienku konsoli. Jest **System.Windows.Media.Color** obiektu.

```powershell
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a>VerboseForegroundColor

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Określa kolor pierwszego planu pełny tekst wyświetlany w okienku konsoli. Jest **System.Windows.Media.Color** obiektu.

```powershell
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor = 'yellow'
```

### <a name="warningbackgroundcolor"></a>WarningBackgroundColor

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Określa kolor tła ostrzeżenie tekst wyświetlany w okienku konsoli. Jest **System.Windows.Media.Color** obiektu.

```powershell
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor = '#0000FF'
```

### <a name="warningforegroundcolor"></a>WarningForegroundColor

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Określa kolor pierwszego planu ostrzeżenie tekst wyświetlany w okienku danych wyjściowych. Jest **System.Windows.Media.Color** obiektu.

```powershell
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor = 'yellow'
```

### <a name="xmltokencolors"></a>XmlTokenColors

Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

Określa obiekt słownika zawierający pary nazwa/wartość typy tokenów i kolory zawartość XML, która jest wyświetlana w środowisku Windows PowerShell ISE. Kolory tokenu można ustawić dla następujących: atrybut, polecenia, CommandArgument, CommandParameter, komentarza, GroupEnd, GroupStart, — słowo kluczowe, LineContinuation, LoopLabel, elementu członkowskiego, nowego wiersza, numer, operatora, pozycji, StatementSeparator, ciągu, typu, Nieznany, zmiennej. Zobacz też [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).

```powershell
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = 'green'
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = 'magenta'
```

### <a name="zoom"></a>Powiększenie

Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

Określa rozmiar względny tekstu w okienku konsoli i skrypt. Wartość domyślna to 100. Mniejsze wartości powodują tekst w środowisku Windows PowerShell ISE i pojawienie się mniejszych większą liczbą spowodować tekst, który ma być wyświetlane. Wartość jest liczbą całkowitą, która obejmuje 20 do 400.

```powershell
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a>Zobacz też

- [Cel programu Windows PowerShell ISE skryptów modelu obiektów](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarchia modeli obiektów środowiska ISE](The-ISE-Object-Model-Hierarchy.md)