---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISEEditor
ms.openlocfilehash: c593eeebf0b9a94769841efd2aa78f84a3829ca5
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2017
---
# <a name="the-iseeditor-object"></a><span data-ttu-id="ce1e7-103">Obiekt ISEEditor</span><span class="sxs-lookup"><span data-stu-id="ce1e7-103">The ISEEditor Object</span></span>
  <span data-ttu-id="ce1e7-104">**ISEEditor** obiekt jest wystąpieniem klasy Microsoft.PowerShell.Host.ISE.ISEEditor.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-104">An **ISEEditor** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEEditor class.</span></span> <span data-ttu-id="ce1e7-105">W okienku konsoli jest **ISEEditor** obiektu.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-105">The Console pane is an **ISEEditor** object.</span></span> <span data-ttu-id="ce1e7-106">Każdy [ISEFile](The-ISEFile-Object.md) ma skojarzony obiekt **ISEEditor** obiektu.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-106">Each [ISEFile](The-ISEFile-Object.md) object has an associated **ISEEditor** object.</span></span> <span data-ttu-id="ce1e7-107">Poniższe sekcje zawierają listę metod i właściwości **ISEEditor** obiektu.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-107">The following sections list the methods and properties of an **ISEEditor** object.</span></span>

## <a name="methods"></a><span data-ttu-id="ce1e7-108">Metody</span><span class="sxs-lookup"><span data-stu-id="ce1e7-108">Methods</span></span>

### <a name="clear"></a><span data-ttu-id="ce1e7-109">Wyczyść\(\)</span><span class="sxs-lookup"><span data-stu-id="ce1e7-109">Clear\(\)</span></span>
  <span data-ttu-id="ce1e7-110">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ce1e7-111">Usuwa tekst w edytorze.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-111">Clears the text in the editor.</span></span>

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a><span data-ttu-id="ce1e7-112">EnsureVisible\(int numer wiersza\)</span><span class="sxs-lookup"><span data-stu-id="ce1e7-112">EnsureVisible\(int lineNumber\)</span></span>
  <span data-ttu-id="ce1e7-113">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-113">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ce1e7-114">Przewija edytora, tak aby wiersz, który odpowiada określonym **numer wiersza** wartość parametru jest widoczna.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-114">Scrolls the editor so that the line that corresponds to the specified **lineNumber** parameter value is visible.</span></span> <span data-ttu-id="ce1e7-115">Jeśli numer wiersza określony jest spoza zakresu 1, ostatni numer wiersza, który definiuje prawidłowe numery zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-115">It throws an exception if the specified line number is outside the range of 1,last line number, which defines the valid line numbers.</span></span>

 <span data-ttu-id="ce1e7-116">**numer wiersza** numer wiersza, który ma być widoczne.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-116">**lineNumber** The number of the line that is to be made visible.</span></span>

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view. 
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a><span data-ttu-id="ce1e7-117">Fokus\(\)</span><span class="sxs-lookup"><span data-stu-id="ce1e7-117">Focus\(\)</span></span>
  <span data-ttu-id="ce1e7-118">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ce1e7-119">Ustawia fokus do edytora.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-119">Sets the focus to the editor.</span></span>

```powershell
# Sets focus to the Console pane. 
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a><span data-ttu-id="ce1e7-120">GetLineLength\(int numer wiersza\)</span><span class="sxs-lookup"><span data-stu-id="ce1e7-120">GetLineLength\(int lineNumber \)</span></span>
  <span data-ttu-id="ce1e7-121">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-121">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ce1e7-122">Pobiera długość wiersza jako liczba całkowita dla wiersza, który jest określony przez numer wiersza.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-122">Gets the line length as an integer for the line that is specified by the line number.</span></span>

 <span data-ttu-id="ce1e7-123">**numer wiersza** numer wiersza, którego można pobrać długości.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-123">**lineNumber** The number of the line of which to get the length.</span></span>

 <span data-ttu-id="ce1e7-124">**Zwraca** długość wiersza dla wiersza na określony numer wiersza.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-124">**Returns** The line length for the line at the specified line number.</span></span>

```powershell
# Gets the length of the first line in the text of the Command pane. 
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a><span data-ttu-id="ce1e7-125">GoToMatch\(\)</span><span class="sxs-lookup"><span data-stu-id="ce1e7-125">GoToMatch\(\)</span></span>
  <span data-ttu-id="ce1e7-126">Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-126">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="ce1e7-127">Przenosi karetkę do pasującego znaku, jeśli **CanGoToMatch** jest właściwością obiektu edytor **$true**, który występuje, gdy karetka znajduje się bezpośrednio przed nawiasem otwierającym, nawias kwadratowy lub klamrowy - \(,\[, {- lub bezpośrednio po zamykającym, nawias kwadratowy lub nawias klamrowy - \),\],}.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-127">Moves the caret to the matching character if the **CanGoToMatch** property of the editor object is **$true**, which occurs when the caret is immediately before an opening parenthesis, bracket, or brace - \(,\[,{ - or immediately after a closing parenthesis, bracket, or brace - \),\],}.</span></span>  <span data-ttu-id="ce1e7-128">Daszek znajduje się przed znakiem otwierania lub po znaku zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-128">The caret is placed before an opening character or after a closing character.</span></span> <span data-ttu-id="ce1e7-129">Jeśli **CanGoToMatch** właściwość jest **$false**, a następnie ta metoda nie działa.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-129">If the **CanGoToMatch** property is **$false**, then this method does nothing.</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace.
```

### <a name="inserttext-text-"></a><span data-ttu-id="ce1e7-130">InsertText\( tekstu\)</span><span class="sxs-lookup"><span data-stu-id="ce1e7-130">InsertText\( text \)</span></span>
  <span data-ttu-id="ce1e7-131">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-131">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ce1e7-132">Zamienia zaznaczenie tekstu lub wstawia tekst w bieżącym położeniu karetki.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-132">Replaces the selection with text or inserts text at the current caret position.</span></span>

 <span data-ttu-id="ce1e7-133">**tekst** -String tekst do wstawienia.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-133">**text** - String The text to insert.</span></span>

 <span data-ttu-id="ce1e7-134">Zobacz [przykładowe skrypty](#scripting-example) dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-134">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="select-startline-startcolumn-endline-endcolumn-"></a><span data-ttu-id="ce1e7-135">Wybierz\( startLine, startColumn, endLine, wartość endColumn\)</span><span class="sxs-lookup"><span data-stu-id="ce1e7-135">Select\( startLine, startColumn, endLine, endColumn \)</span></span>
  <span data-ttu-id="ce1e7-136">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ce1e7-137">Wybiera tekst ze **startLine**, **startColumn**, **endLine**, i **wartość endColumn** parametrów.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-137">Selects the text from the **startLine**, **startColumn**, **endLine**, and **endColumn** parameters.</span></span>

 <span data-ttu-id="ce1e7-138">**startLine** — liczba całkowita wiersza, w którym rozpoczyna się zaznaczenie.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-138">**startLine** - Integer The line where the selection starts.</span></span>

 <span data-ttu-id="ce1e7-139">**startColumn** — liczba całkowita kolumny wiersza start, gdy rozpoczyna się zaznaczenie.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-139">**startColumn** - Integer The column within the start line where the selection starts.</span></span>

 <span data-ttu-id="ce1e7-140">**endLine** — liczba całkowita wiersza, w którym kończy się zaznaczenie.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-140">**endLine** - Integer The line where the selection ends.</span></span>

 <span data-ttu-id="ce1e7-141">**wartość endColumn** — liczba całkowita kolumny zakończyć wiersza, w którym kończy się zaznaczenie.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-141">**endColumn** - Integer The column within the end line where the selection ends.</span></span>

 <span data-ttu-id="ce1e7-142">Zobacz [przykładowe skrypty](#scripting-example) dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-142">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="selectcaretline"></a><span data-ttu-id="ce1e7-143">SelectCaretLine\(\)</span><span class="sxs-lookup"><span data-stu-id="ce1e7-143">SelectCaretLine\(\)</span></span>
  <span data-ttu-id="ce1e7-144">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-144">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ce1e7-145">Zaznacza cały wiersz tekstu zawierającego karetki.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-145">Selects the entire line of text that currently contains the caret.</span></span>

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1) 
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a><span data-ttu-id="ce1e7-146">SetCaretPosition\( numer wiersza, columnNumber\)</span><span class="sxs-lookup"><span data-stu-id="ce1e7-146">SetCaretPosition\( lineNumber, columnNumber \)</span></span>
  <span data-ttu-id="ce1e7-147">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-147">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ce1e7-148">Ustawia położenie karetki na numer wiersza i kolumny.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-148">Sets the caret position at the line number and the column number.</span></span> <span data-ttu-id="ce1e7-149">Jeśli numer wiersza karetki lub numer kolumny karetki są poza ich odpowiednich prawidłowych zakresów, zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-149">It throws an exception if either the caret line number  or the caret column number  are out of their respective valid ranges.</span></span>

 <span data-ttu-id="ce1e7-150">**numer wiersza** — całkowitą numer wiersza karetki.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-150">**lineNumber** - Integer The caret line number.</span></span>

 <span data-ttu-id="ce1e7-151">**columnNumber** — całkowitą liczbę kolumn karetki.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-151">**columnNumber** - Integer The caret column number.</span></span>

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a><span data-ttu-id="ce1e7-152">ToggleOutliningExpansion\(\)</span><span class="sxs-lookup"><span data-stu-id="ce1e7-152">ToggleOutliningExpansion\(\)</span></span>
  <span data-ttu-id="ce1e7-153">Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-153">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="ce1e7-154">Powoduje, że wszystkie sekcje konspektu rozwinąć lub zwinąć.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-154">Causes all the outline sections to expand or collapse.</span></span>

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a><span data-ttu-id="ce1e7-155">Właściwości</span><span class="sxs-lookup"><span data-stu-id="ce1e7-155">Properties</span></span>

### <a name="cangotomatch"></a><span data-ttu-id="ce1e7-156">CanGoToMatch</span><span class="sxs-lookup"><span data-stu-id="ce1e7-156">CanGoToMatch</span></span>
  <span data-ttu-id="ce1e7-157">Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-157">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="ce1e7-158">Tylko do odczytu właściwości typu Boolean wskazująca, czy karetki obok nawias, nawias kwadratowy lub klamrowy - \( \), \[ \], {}.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-158">The read-only Boolean property to indicate whether the caret is next to a parenthesis, bracket, or brace - \(\), \[\], {}.</span></span> <span data-ttu-id="ce1e7-159">Jeśli karetka znajduje się bezpośrednio przed znakiem otwierania lub bezpośrednio po znaku zamknięcia pary, a następnie wartość tej właściwości jest **$true**.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-159">If the caret is immediately before the opening character or immediately after the closing character of a pair, then this property value is **$true**.</span></span> <span data-ttu-id="ce1e7-160">W przeciwnym razie jest **$false**.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-160">Otherwise, it is **$false**.</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a><span data-ttu-id="ce1e7-161">CaretColumn</span><span class="sxs-lookup"><span data-stu-id="ce1e7-161">CaretColumn</span></span>
  <span data-ttu-id="ce1e7-162">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ce1e7-163">Właściwość tylko do odczytu, która pobiera numer kolumny, która odpowiada położeniu karetki.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-163">The read-only property that gets the column number that corresponds to the position of the caret.</span></span>

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a><span data-ttu-id="ce1e7-164">CaretLine</span><span class="sxs-lookup"><span data-stu-id="ce1e7-164">CaretLine</span></span>
  <span data-ttu-id="ce1e7-165">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ce1e7-166">Właściwość tylko do odczytu, która pobiera numer wiersza, który zawiera karetki.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-166">The read-only property that gets the number of the line that contains the caret.</span></span>

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a><span data-ttu-id="ce1e7-167">CaretLineText</span><span class="sxs-lookup"><span data-stu-id="ce1e7-167">CaretLineText</span></span>
  <span data-ttu-id="ce1e7-168">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-168">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ce1e7-169">Właściwość tylko do odczytu, która pobiera cały wiersz tekstu, który zawiera karetki.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-169">The read-only property that gets the complete line of text that contains the caret.</span></span>

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a><span data-ttu-id="ce1e7-170">LineCount</span><span class="sxs-lookup"><span data-stu-id="ce1e7-170">LineCount</span></span>
  <span data-ttu-id="ce1e7-171">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-171">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ce1e7-172">Właściwość tylko do odczytu, która pobiera liczba wierszy w edytorze.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-172">The read-only property that gets the line count from the editor.</span></span>

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a><span data-ttu-id="ce1e7-173">SelectedText</span><span class="sxs-lookup"><span data-stu-id="ce1e7-173">SelectedText</span></span>
  <span data-ttu-id="ce1e7-174">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-174">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ce1e7-175">Właściwość tylko do odczytu, która pobiera zaznaczony tekst w edytorze.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-175">The read-only property that gets the selected text from the editor.</span></span>

 <span data-ttu-id="ce1e7-176">Zobacz [przykładowe skrypty](#scripting-example) dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-176">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="text"></a><span data-ttu-id="ce1e7-177">Tekst</span><span class="sxs-lookup"><span data-stu-id="ce1e7-177">Text</span></span>
  <span data-ttu-id="ce1e7-178">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-178">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ce1e7-179">Właściwości odczytu/zapisu, która pobiera lub ustawia tekst w edytorze.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-179">The read/write property that gets or sets the text in the editor.</span></span>

 <span data-ttu-id="ce1e7-180">Zobacz [przykładowe skrypty](#scripting-example) dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ce1e7-180">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

## <a name="scripting-example"></a><span data-ttu-id="ce1e7-181">Przykład skryptów</span><span class="sxs-lookup"><span data-stu-id="ce1e7-181">Scripting Example</span></span>

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
$endColumn= $myEditor.GetLineLength(3)
# Select the text in the first three lines.
$myEditor.Select(1,1,3,$endColumn + 1)
$selection = $myEditor.SelectedText
# Clear all the text in the editor.
$myEditor.Clear()
# Add the selected text back, but in lower case.
$myEditor.InsertText($selection.ToLower())
```

## <a name="see-also"></a><span data-ttu-id="ce1e7-182">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce1e7-182">See Also</span></span>
- [<span data-ttu-id="ce1e7-183">Obiekt ISEFile</span><span class="sxs-lookup"><span data-stu-id="ce1e7-183">The ISEFile Object</span></span>](The-ISEFile-Object.md) 
- [<span data-ttu-id="ce1e7-184">Obiekt PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="ce1e7-184">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md) 
- [<span data-ttu-id="ce1e7-185">Windows PowerShell ISE skryptów modelu obiektów</span><span class="sxs-lookup"><span data-stu-id="ce1e7-185">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="ce1e7-186">Dotyczące modelu obiektów programu Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="ce1e7-186">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="ce1e7-187">Hierarchia modelu obiektów ISE</span><span class="sxs-lookup"><span data-stu-id="ce1e7-187">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
