---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISEEditor
ms.openlocfilehash: 2d4c3d941035384c591ca57e809c0e3a9b852f5c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686152"
---
# <a name="the-iseeditor-object"></a><span data-ttu-id="723f2-103">Obiekt ISEEditor</span><span class="sxs-lookup"><span data-stu-id="723f2-103">The ISEEditor Object</span></span>

<span data-ttu-id="723f2-104">**ISEEditor** obiekt jest wystąpieniem klasy Microsoft.PowerShell.Host.ISE.ISEEditor.</span><span class="sxs-lookup"><span data-stu-id="723f2-104">An **ISEEditor** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEEditor class.</span></span> <span data-ttu-id="723f2-105">W okienku konsoli jest **ISEEditor** obiektu.</span><span class="sxs-lookup"><span data-stu-id="723f2-105">The Console pane is an **ISEEditor** object.</span></span> <span data-ttu-id="723f2-106">Każdy [ISEFile](The-ISEFile-Object.md) obiekt ma skojarzoną **ISEEditor** obiektu.</span><span class="sxs-lookup"><span data-stu-id="723f2-106">Each [ISEFile](The-ISEFile-Object.md) object has an associated **ISEEditor** object.</span></span> <span data-ttu-id="723f2-107">W poniższych sekcjach wymieniono metody i właściwości **ISEEditor** obiektu.</span><span class="sxs-lookup"><span data-stu-id="723f2-107">The following sections list the methods and properties of an **ISEEditor** object.</span></span>

## <a name="methods"></a><span data-ttu-id="723f2-108">Metody</span><span class="sxs-lookup"><span data-stu-id="723f2-108">Methods</span></span>

### <a name="clear"></a><span data-ttu-id="723f2-109">Usuń zaznaczenie\(\)</span><span class="sxs-lookup"><span data-stu-id="723f2-109">Clear\(\)</span></span>

<span data-ttu-id="723f2-110">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="723f2-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="723f2-111">Usuwa tekst w edytorze.</span><span class="sxs-lookup"><span data-stu-id="723f2-111">Clears the text in the editor.</span></span>

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a><span data-ttu-id="723f2-112">EnsureVisible\(int lineNumber\)</span><span class="sxs-lookup"><span data-stu-id="723f2-112">EnsureVisible\(int lineNumber\)</span></span>

<span data-ttu-id="723f2-113">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="723f2-113">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="723f2-114">Przewija edytora, dzięki czemu wiersz, który odpowiada określony **lineNumber** wartość parametru jest widoczna.</span><span class="sxs-lookup"><span data-stu-id="723f2-114">Scrolls the editor so that the line that corresponds to the specified **lineNumber** parameter value is visible.</span></span> <span data-ttu-id="723f2-115">Zgłasza wyjątek, jeśli określony numer wiersza jest spoza zakresu 1, ostatni numer wiersza, który definiuje prawidłowe numery.</span><span class="sxs-lookup"><span data-stu-id="723f2-115">It throws an exception if the specified line number is outside the range of 1,last line number, which defines the valid line numbers.</span></span>

<span data-ttu-id="723f2-116">**numer wiersza** numer wiersza, który ma być widoczne.</span><span class="sxs-lookup"><span data-stu-id="723f2-116">**lineNumber** The number of the line that is to be made visible.</span></span>

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view.
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a><span data-ttu-id="723f2-117">Focus\(\)</span><span class="sxs-lookup"><span data-stu-id="723f2-117">Focus\(\)</span></span>

<span data-ttu-id="723f2-118">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="723f2-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="723f2-119">Ustawia fokus do edytora.</span><span class="sxs-lookup"><span data-stu-id="723f2-119">Sets the focus to the editor.</span></span>

```powershell
# Sets focus to the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a><span data-ttu-id="723f2-120">GetLineLength\(int lineNumber \)</span><span class="sxs-lookup"><span data-stu-id="723f2-120">GetLineLength\(int lineNumber \)</span></span>

<span data-ttu-id="723f2-121">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="723f2-121">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="723f2-122">Pobiera długość wiersza jako liczby całkowitej dla wiersza, który jest określony przez numer wiersza.</span><span class="sxs-lookup"><span data-stu-id="723f2-122">Gets the line length as an integer for the line that is specified by the line number.</span></span>

<span data-ttu-id="723f2-123">**numer wiersza** numer wiersza, z którego mają zostać pobrane długości.</span><span class="sxs-lookup"><span data-stu-id="723f2-123">**lineNumber** The number of the line of which to get the length.</span></span>

<span data-ttu-id="723f2-124">**Zwraca** długość wiersza dla wiersza na określony numer wiersza.</span><span class="sxs-lookup"><span data-stu-id="723f2-124">**Returns** The line length for the line at the specified line number.</span></span>

```powershell
# Gets the length of the first line in the text of the Command pane.
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a><span data-ttu-id="723f2-125">GoToMatch\(\)</span><span class="sxs-lookup"><span data-stu-id="723f2-125">GoToMatch\(\)</span></span>

<span data-ttu-id="723f2-126">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="723f2-126">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="723f2-127">Przenosi karetkę do pasującego znaku, jeśli **CanGoToMatch** jest właściwością obiektu edytora **$true**, który występuje, gdy karetka znajduje się bezpośrednio przed otwierającym nawiasem, nawias kwadratowy lub nawiasu klamrowego — \(,\[, {— lub natychmiast po nawiasie zamykającym, nawias kwadratowy lub nawiasu klamrowego — \),\],}.</span><span class="sxs-lookup"><span data-stu-id="723f2-127">Moves the caret to the matching character if the **CanGoToMatch** property of the editor object is **$true**, which occurs when the caret is immediately before an opening parenthesis, bracket, or brace - \(,\[,{ - or immediately after a closing parenthesis, bracket, or brace - \),\],}.</span></span>  <span data-ttu-id="723f2-128">Daszek jest umieszczany przed otwierającym znakiem lub po znaku zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="723f2-128">The caret is placed before an opening character or after a closing character.</span></span> <span data-ttu-id="723f2-129">Jeśli **CanGoToMatch** właściwość **$false**, wówczas ta metoda nie działa.</span><span class="sxs-lookup"><span data-stu-id="723f2-129">If the **CanGoToMatch** property is **$false**, then this method does nothing.</span></span>

```powershell
# Goes to the matching character if CanGoToMatch() is $true
$psISE.CurrentPowerShellTab.ConsolePane.GoToMatch()
```

### <a name="inserttext-text-"></a><span data-ttu-id="723f2-130">InsertText\( tekstu \)</span><span class="sxs-lookup"><span data-stu-id="723f2-130">InsertText\( text \)</span></span>

<span data-ttu-id="723f2-131">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="723f2-131">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="723f2-132">Zamienia tekst zaznaczenia lub wstawia tekst w bieżącym położeniu karetki.</span><span class="sxs-lookup"><span data-stu-id="723f2-132">Replaces the selection with text or inserts text at the current caret position.</span></span>

<span data-ttu-id="723f2-133">**tekst** — ciąg tekst do wstawienia.</span><span class="sxs-lookup"><span data-stu-id="723f2-133">**text** - String The text to insert.</span></span>

<span data-ttu-id="723f2-134">Zobacz [skryptów przykład](#scripting-example) w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="723f2-134">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="select-startline-startcolumn-endline-endcolumn-"></a><span data-ttu-id="723f2-135">Select\( startLine, startColumn, endLine, endColumn \)</span><span class="sxs-lookup"><span data-stu-id="723f2-135">Select\( startLine, startColumn, endLine, endColumn \)</span></span>

<span data-ttu-id="723f2-136">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="723f2-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="723f2-137">Zaznacza tekst z **startLine**, **startColumn**, **endLine**, i **endColumn** parametrów.</span><span class="sxs-lookup"><span data-stu-id="723f2-137">Selects the text from the **startLine**, **startColumn**, **endLine**, and **endColumn** parameters.</span></span>

<span data-ttu-id="723f2-138">**startLine** -liczba całkowita wiersza, gdzie rozpoczyna się zaznaczenie.</span><span class="sxs-lookup"><span data-stu-id="723f2-138">**startLine** - Integer The line where the selection starts.</span></span>

<span data-ttu-id="723f2-139">**startColumn** -liczba całkowita kolumna w wierszu rozpoczęcia, gdzie rozpoczyna się zaznaczenie.</span><span class="sxs-lookup"><span data-stu-id="723f2-139">**startColumn** - Integer The column within the start line where the selection starts.</span></span>

<span data-ttu-id="723f2-140">**endLine** -liczba całkowita wiersza, w którym kończy się zaznaczenie.</span><span class="sxs-lookup"><span data-stu-id="723f2-140">**endLine** - Integer The line where the selection ends.</span></span>

<span data-ttu-id="723f2-141">**endColumn** -liczba całkowita kolumny wiersz końcowy, w którym kończy się zaznaczenie.</span><span class="sxs-lookup"><span data-stu-id="723f2-141">**endColumn** - Integer The column within the end line where the selection ends.</span></span>

<span data-ttu-id="723f2-142">Zobacz [skryptów przykład](#scripting-example) w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="723f2-142">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="selectcaretline"></a><span data-ttu-id="723f2-143">SelectCaretLine\(\)</span><span class="sxs-lookup"><span data-stu-id="723f2-143">SelectCaretLine\(\)</span></span>

<span data-ttu-id="723f2-144">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="723f2-144">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="723f2-145">Zaznacza cały wiersz tekstu zawierającego karetki.</span><span class="sxs-lookup"><span data-stu-id="723f2-145">Selects the entire line of text that currently contains the caret.</span></span>

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a><span data-ttu-id="723f2-146">SetCaretPosition\( lineNumber, columnNumber \)</span><span class="sxs-lookup"><span data-stu-id="723f2-146">SetCaretPosition\( lineNumber, columnNumber \)</span></span>

<span data-ttu-id="723f2-147">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="723f2-147">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="723f2-148">Ustawia położenia karetki na numer wiersza i numer kolumny.</span><span class="sxs-lookup"><span data-stu-id="723f2-148">Sets the caret position at the line number and the column number.</span></span> <span data-ttu-id="723f2-149">Zgłasza wyjątek, jeśli numer wiersza karetki lub numer kolumny karetki znajdą się poza ich odpowiednich prawidłowych zakresów.</span><span class="sxs-lookup"><span data-stu-id="723f2-149">It throws an exception if either the caret line number  or the caret column number  are out of their respective valid ranges.</span></span>

<span data-ttu-id="723f2-150">**numer wiersza** -liczba całkowita numer wiersza karetki.</span><span class="sxs-lookup"><span data-stu-id="723f2-150">**lineNumber** - Integer The caret line number.</span></span>

<span data-ttu-id="723f2-151">**columnNumber** -całkowitą numer kolumny karetki.</span><span class="sxs-lookup"><span data-stu-id="723f2-151">**columnNumber** - Integer The caret column number.</span></span>

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a><span data-ttu-id="723f2-152">ToggleOutliningExpansion\(\)</span><span class="sxs-lookup"><span data-stu-id="723f2-152">ToggleOutliningExpansion\(\)</span></span>

<span data-ttu-id="723f2-153">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="723f2-153">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="723f2-154">Powoduje, że wszystkie sekcje konspektu rozwinąć lub zwinąć.</span><span class="sxs-lookup"><span data-stu-id="723f2-154">Causes all the outline sections to expand or collapse.</span></span>

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a><span data-ttu-id="723f2-155">Właściwości</span><span class="sxs-lookup"><span data-stu-id="723f2-155">Properties</span></span>

### <a name="cangotomatch"></a><span data-ttu-id="723f2-156">CanGoToMatch</span><span class="sxs-lookup"><span data-stu-id="723f2-156">CanGoToMatch</span></span>

<span data-ttu-id="723f2-157">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="723f2-157">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="723f2-158">Właściwość logiczna przeznaczony tylko do odczytu do wskazania, czy karetka znajduje się obok nawiasu, nawias kwadratowy lub nawiasu klamrowego — \( \), \[ \], {}.</span><span class="sxs-lookup"><span data-stu-id="723f2-158">The read-only Boolean property to indicate whether the caret is next to a parenthesis, bracket, or brace - \(\), \[\], {}.</span></span> <span data-ttu-id="723f2-159">Jeśli karetka znajduje się bezpośrednio przed otwierającym znakiem lub bezpośrednio po znaku zamknięcia parę, a następnie wartość tej właściwości jest **$true**.</span><span class="sxs-lookup"><span data-stu-id="723f2-159">If the caret is immediately before the opening character or immediately after the closing character of a pair, then this property value is **$true**.</span></span> <span data-ttu-id="723f2-160">W przeciwnym razie jest **$false**.</span><span class="sxs-lookup"><span data-stu-id="723f2-160">Otherwise, it is **$false**.</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a><span data-ttu-id="723f2-161">CaretColumn</span><span class="sxs-lookup"><span data-stu-id="723f2-161">CaretColumn</span></span>

<span data-ttu-id="723f2-162">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="723f2-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="723f2-163">Właściwość tylko do odczytu, która pobiera numer kolumny, która odpowiada to położeniu karetki.</span><span class="sxs-lookup"><span data-stu-id="723f2-163">The read-only property that gets the column number that corresponds to the position of the caret.</span></span>

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a><span data-ttu-id="723f2-164">CaretLine</span><span class="sxs-lookup"><span data-stu-id="723f2-164">CaretLine</span></span>

<span data-ttu-id="723f2-165">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="723f2-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="723f2-166">Właściwość tylko do odczytu, która pobiera numer wiersza, który zawiera karetki.</span><span class="sxs-lookup"><span data-stu-id="723f2-166">The read-only property that gets the number of the line that contains the caret.</span></span>

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a><span data-ttu-id="723f2-167">CaretLineText</span><span class="sxs-lookup"><span data-stu-id="723f2-167">CaretLineText</span></span>

<span data-ttu-id="723f2-168">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="723f2-168">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="723f2-169">Właściwość tylko do odczytu, która pobiera pełny wiersz tekstu, który zawiera karetki.</span><span class="sxs-lookup"><span data-stu-id="723f2-169">The read-only property that gets the complete line of text that contains the caret.</span></span>

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a><span data-ttu-id="723f2-170">LineCount</span><span class="sxs-lookup"><span data-stu-id="723f2-170">LineCount</span></span>

<span data-ttu-id="723f2-171">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="723f2-171">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="723f2-172">Właściwość tylko do odczytu, która liczba wierszy w edytorze.</span><span class="sxs-lookup"><span data-stu-id="723f2-172">The read-only property that gets the line count from the editor.</span></span>

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a><span data-ttu-id="723f2-173">SelectedText</span><span class="sxs-lookup"><span data-stu-id="723f2-173">SelectedText</span></span>

<span data-ttu-id="723f2-174">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="723f2-174">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="723f2-175">Właściwość tylko do odczytu, która pobiera zaznaczony tekst w edytorze.</span><span class="sxs-lookup"><span data-stu-id="723f2-175">The read-only property that gets the selected text from the editor.</span></span>

<span data-ttu-id="723f2-176">Zobacz [skryptów przykład](#scripting-example) w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="723f2-176">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="text"></a><span data-ttu-id="723f2-177">Tekst</span><span class="sxs-lookup"><span data-stu-id="723f2-177">Text</span></span>

<span data-ttu-id="723f2-178">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="723f2-178">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="723f2-179">Właściwości odczytu/zapisu, który pobiera lub ustawia tekst w edytorze.</span><span class="sxs-lookup"><span data-stu-id="723f2-179">The read/write property that gets or sets the text in the editor.</span></span>

<span data-ttu-id="723f2-180">Zobacz [skryptów przykład](#scripting-example) w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="723f2-180">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

## <a name="scripting-example"></a><span data-ttu-id="723f2-181">Przykład skryptu</span><span class="sxs-lookup"><span data-stu-id="723f2-181">Scripting Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="723f2-182">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="723f2-182">See Also</span></span>

- [<span data-ttu-id="723f2-183">Obiekt ISEFile</span><span class="sxs-lookup"><span data-stu-id="723f2-183">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="723f2-184">Obiekt PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="723f2-184">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="723f2-185">Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="723f2-185">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="723f2-186">Hierarchia modeli obiektów środowiska ISE</span><span class="sxs-lookup"><span data-stu-id="723f2-186">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)