---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISEEditor
ms.openlocfilehash: 2d4c3d941035384c591ca57e809c0e3a9b852f5c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="the-iseeditor-object"></a>Obiekt ISEEditor

**ISEEditor** obiekt jest wystąpieniem klasy Microsoft.PowerShell.Host.ISE.ISEEditor. W okienku konsoli jest **ISEEditor** obiektu. Każdy [ISEFile](The-ISEFile-Object.md) ma skojarzony obiekt **ISEEditor** obiektu. Poniższe sekcje zawierają listę metod i właściwości **ISEEditor** obiektu.

## <a name="methods"></a>Metody

### <a name="clear"></a>Wyczyść\(\)

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Usuwa tekst w edytorze.

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a>EnsureVisible\(int numer wiersza\)

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Przewija edytora, tak aby wiersz, który odpowiada określonym **numer wiersza** wartość parametru jest widoczna. Jeśli numer wiersza określony jest spoza zakresu 1, ostatni numer wiersza, który definiuje prawidłowe numery zgłasza wyjątek.

**numer wiersza** numer wiersza, który ma być widoczne.

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view.
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a>Fokus\(\)

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Ustawia fokus do edytora.

```powershell
# Sets focus to the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a>GetLineLength\(int numer wiersza \)

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Pobiera długość wiersza jako liczba całkowita dla wiersza, który jest określony przez numer wiersza.

**numer wiersza** numer wiersza, którego można pobrać długości.

**Zwraca** długość wiersza dla wiersza na określony numer wiersza.

```powershell
# Gets the length of the first line in the text of the Command pane.
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a>GoToMatch\(\)

Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

Przenosi karetkę do pasującego znaku, jeśli **CanGoToMatch** jest właściwością obiektu edytor **$true**, który występuje, gdy karetka znajduje się bezpośrednio przed nawiasem otwierającym, nawias kwadratowy lub klamrowy - \(,\[, {- lub bezpośrednio po zamykającym, nawias kwadratowy lub nawias klamrowy - \),\],}.  Daszek znajduje się przed znakiem otwierania lub po znaku zamknięcia. Jeśli **CanGoToMatch** właściwość jest **$false**, a następnie ta metoda nie działa.

```powershell
# Goes to the matching character if CanGoToMatch() is $true
$psISE.CurrentPowerShellTab.ConsolePane.GoToMatch()
```

### <a name="inserttext-text-"></a>InsertText\( tekstu \)

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Zamienia zaznaczenie tekstu lub wstawia tekst w bieżącym położeniu karetki.

**tekst** -String tekst do wstawienia.

Zobacz [przykładowe skrypty](#scripting-example) dalszej części tego tematu.

### <a name="select-startline-startcolumn-endline-endcolumn-"></a>Wybierz\( startLine, startColumn, endLine, wartość endColumn \)

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Wybiera tekst ze **startLine**, **startColumn**, **endLine**, i **wartość endColumn** parametrów.

**startLine** — liczba całkowita wiersza, w którym rozpoczyna się zaznaczenie.

**startColumn** — liczba całkowita kolumny wiersza start, gdy rozpoczyna się zaznaczenie.

**endLine** — liczba całkowita wiersza, w którym kończy się zaznaczenie.

**wartość endColumn** — liczba całkowita kolumny zakończyć wiersza, w którym kończy się zaznaczenie.

Zobacz [przykładowe skrypty](#scripting-example) dalszej części tego tematu.

### <a name="selectcaretline"></a>SelectCaretLine\(\)

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Zaznacza cały wiersz tekstu zawierającego karetki.

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a>SetCaretPosition\( numer wiersza, columnNumber \)

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Ustawia położenie karetki na numer wiersza i kolumny. Jeśli numer wiersza karetki lub numer kolumny karetki są poza ich odpowiednich prawidłowych zakresów, zgłasza wyjątek.

**numer wiersza** — całkowitą numer wiersza karetki.

**columnNumber** — całkowitą liczbę kolumn karetki.

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a>ToggleOutliningExpansion\(\)

Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

Powoduje, że wszystkie sekcje konspektu rozwinąć lub zwinąć.

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a>Właściwości

### <a name="cangotomatch"></a>CanGoToMatch

Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

Tylko do odczytu właściwości typu Boolean wskazująca, czy karetki obok nawias, nawias kwadratowy lub klamrowy - \( \), \[ \], {}. Jeśli karetka znajduje się bezpośrednio przed znakiem otwierania lub bezpośrednio po znaku zamknięcia pary, a następnie wartość tej właściwości jest **$true**. W przeciwnym razie jest **$false**.

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a>CaretColumn

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Właściwość tylko do odczytu, która pobiera numer kolumny, która odpowiada położeniu karetki.

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a>CaretLine

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Właściwość tylko do odczytu, która pobiera numer wiersza, który zawiera karetki.

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a>CaretLineText

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Właściwość tylko do odczytu, która pobiera cały wiersz tekstu, który zawiera karetki.

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a>LineCount

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Właściwość tylko do odczytu, która pobiera liczba wierszy w edytorze.

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a>SelectedText

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Właściwość tylko do odczytu, która pobiera zaznaczony tekst w edytorze.

Zobacz [przykładowe skrypty](#scripting-example) dalszej części tego tematu.

### <a name="text"></a>Tekst

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Właściwości odczytu/zapisu, która pobiera lub ustawia tekst w edytorze.

Zobacz [przykładowe skrypty](#scripting-example) dalszej części tego tematu.

## <a name="scripting-example"></a>Przykład skryptów

```powershell
# This illustrates how you can use the length of a line to
# select the entire line and shows how you can make it lowercase.
# You must run this in the Console pane. It will not run in the Script pane.
# Begin by getting a variable that points to the editor.
$myEditor = $psISE.CurrentFile.Editor
# Clear the text in the current file editor.
$myEditor.Clear()

# Make sure the file has five lines of text.
$myEditor.InsertText("LINE1 `n")
$myEditor.InsertText("LINE2 `n")
$myEditor.InsertText("LINE3 `n")
$myEditor.InsertText("LINE4 `n")
$myEditor.InsertText("LINE5 `n")

# Use the GetLineLength method to get the length of the third line.
$endColumn = $myEditor.GetLineLength(3)
# Select the text in the first three lines.
$myEditor.Select(1, 1, 3, $endColumn + 1)
$selection = $myEditor.SelectedText
# Clear all the text in the editor.
$myEditor.Clear()
# Add the selected text back, but in lower case.
$myEditor.InsertText($selection.ToLower())
```

## <a name="see-also"></a>Zobacz też

- [Obiekt ISEFile](The-ISEFile-Object.md)
- [Obiekt PowerShellTab](The-PowerShellTab-Object.md)
- [Cel programu Windows PowerShell ISE skryptów modelu obiektów](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarchia modeli obiektów środowiska ISE](The-ISE-Object-Model-Hierarchy.md)