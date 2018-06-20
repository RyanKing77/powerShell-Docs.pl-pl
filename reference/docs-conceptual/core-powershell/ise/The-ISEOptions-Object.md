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
# <a name="the-iseoptions-object"></a><span data-ttu-id="348e9-103">Obiekt ISEOptions</span><span class="sxs-lookup"><span data-stu-id="348e9-103">The ISEOptions Object</span></span>

<span data-ttu-id="348e9-104">**ISEOptions** obiekt reprezentuje różne ustawienia dla programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="348e9-104">The **ISEOptions** object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="348e9-105">To wystąpienie **Microsoft.PowerShell.Host.ISE.ISEOptions** klasy.</span><span class="sxs-lookup"><span data-stu-id="348e9-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEOptions** class.</span></span>

<span data-ttu-id="348e9-106">**ISEOptions** obiektu udostępnia następujące metody i właściwości.</span><span class="sxs-lookup"><span data-stu-id="348e9-106">The **ISEOptions** object provides the following methods and properties.</span></span>

## <a name="methods"></a><span data-ttu-id="348e9-107">Metody</span><span class="sxs-lookup"><span data-stu-id="348e9-107">Methods</span></span>

### <a name="restoredefaultconsoletokencolors"></a><span data-ttu-id="348e9-108">RestoreDefaultConsoleTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="348e9-108">RestoreDefaultConsoleTokenColors\(\)</span></span>

<span data-ttu-id="348e9-109">Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="348e9-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="348e9-110">Przywraca domyślne wartości tokenu kolorów w okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="348e9-110">Restores the default values of the token colors in the Console pane.</span></span>

```powershell
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = 'red'
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a><span data-ttu-id="348e9-111">RestoreDefaults\(\)</span><span class="sxs-lookup"><span data-stu-id="348e9-111">RestoreDefaults\(\)</span></span>

<span data-ttu-id="348e9-112">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="348e9-112">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="348e9-113">Przywraca wartości domyślne wszystkich ustawień opcje w okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="348e9-113">Restores the default values of all options settings in the Console pane.</span></span> <span data-ttu-id="348e9-114">Resetuje ono również zachowanie różnych komunikaty ostrzegawcze, które zapewniają standardowe pole wyboru, aby zapobiec wiadomość ponownie wyświetlone.</span><span class="sxs-lookup"><span data-stu-id="348e9-114">It also resets the behavior of various warning messages that provide the standard check box to prevent the message from being shown again.</span></span>

```powershell
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = 'orange'
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a><span data-ttu-id="348e9-115">RestoreDefaultTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="348e9-115">RestoreDefaultTokenColors\(\)</span></span>

<span data-ttu-id="348e9-116">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="348e9-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="348e9-117">Przywraca domyślne wartości tokenu kolorów w okienku skryptów.</span><span class="sxs-lookup"><span data-stu-id="348e9-117">Restores the default values of the token colors in the Script pane.</span></span>

```powershell
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a><span data-ttu-id="348e9-118">RestoreDefaultXmlTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="348e9-118">RestoreDefaultXmlTokenColors\(\)</span></span>

<span data-ttu-id="348e9-119">Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="348e9-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="348e9-120">Przywraca ustawienia domyślne tokenu kolorów dla elementów XML, które są wyświetlane w środowisku Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="348e9-120">Restores the default values of the token colors for XML elements that are displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="348e9-121">Zobacz też [XmlTokenColors](#xmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="348e9-121">Also see [XmlTokenColors](#xmltokencolors).</span></span>

```powershell
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a><span data-ttu-id="348e9-122">Właściwości</span><span class="sxs-lookup"><span data-stu-id="348e9-122">Properties</span></span>

### <a name="autosaveminuteinterval"></a><span data-ttu-id="348e9-123">AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="348e9-123">AutoSaveMinuteInterval</span></span>

<span data-ttu-id="348e9-124">Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="348e9-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="348e9-125">Określa liczbę minut między operacjami automatycznego zapisywania plików przez program Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="348e9-125">Specifies the number of minutes between automatic save operations of your files by Windows PowerShell ISE.</span></span> <span data-ttu-id="348e9-126">Wartość domyślna to 2 minuty.</span><span class="sxs-lookup"><span data-stu-id="348e9-126">The default value is 2 minutes.</span></span> <span data-ttu-id="348e9-127">Wartość jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="348e9-127">The value is an integer.</span></span>

```powershell
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a><span data-ttu-id="348e9-128">CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="348e9-128">CommandPaneBackgroundColor</span></span>

<span data-ttu-id="348e9-129">Ta funkcja znajduje się w programie Windows PowerShell ISE 2.0, ale została usunięta lub zmieniona w nowszej wersji programu ISE.</span><span class="sxs-lookup"><span data-stu-id="348e9-129">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="348e9-130">W przypadku nowszych wersji, zobacz [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="348e9-130">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

<span data-ttu-id="348e9-131">Określa kolor tła okienka polecenia.</span><span class="sxs-lookup"><span data-stu-id="348e9-131">Specifies the background color for the Command pane.</span></span> <span data-ttu-id="348e9-132">To wystąpienie **System.Windows.Media.Color** klasy.</span><span class="sxs-lookup"><span data-stu-id="348e9-132">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = 'orange'
```

### <a name="commandpaneup"></a><span data-ttu-id="348e9-133">CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="348e9-133">CommandPaneUp</span></span>

<span data-ttu-id="348e9-134">Ta funkcja znajduje się w programie Windows PowerShell ISE 2.0, ale została usunięta lub zmieniona w nowszej wersji programu ISE.</span><span class="sxs-lookup"><span data-stu-id="348e9-134">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>

<span data-ttu-id="348e9-135">Określa, czy w okienku polecenia znajduje się powyżej w okienku danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="348e9-135">Specifies whether the Command pane is located above the Output pane.</span></span>

```powershell
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true
```

### <a name="consolepanebackgroundcolor"></a><span data-ttu-id="348e9-136">ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="348e9-136">ConsolePaneBackgroundColor</span></span>

<span data-ttu-id="348e9-137">Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="348e9-137">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="348e9-138">Określa kolor tła okienka konsoli.</span><span class="sxs-lookup"><span data-stu-id="348e9-138">Specifies the background color for the Console pane.</span></span> <span data-ttu-id="348e9-139">To wystąpienie **System.Windows.Media.Color** klasy.</span><span class="sxs-lookup"><span data-stu-id="348e9-139">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = 'red'
```

### <a name="consolepaneforegroundcolor"></a><span data-ttu-id="348e9-140">ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="348e9-140">ConsolePaneForegroundColor</span></span>

<span data-ttu-id="348e9-141">Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="348e9-141">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="348e9-142">Określa kolor tekstu w okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="348e9-142">Specifies the foreground color of the text in the Console pane.</span></span>

```powershell
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = 'yellow'
```

### <a name="consolepanetextbackgroundcolor"></a><span data-ttu-id="348e9-143">ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="348e9-143">ConsolePaneTextBackgroundColor</span></span>

<span data-ttu-id="348e9-144">Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="348e9-144">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="348e9-145">Określa kolor tła tekstu w okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="348e9-145">Specifies the background color of the text in the Console pane.</span></span>

```powershell
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = 'pink'
```

### <a name="consoletokencolors"></a><span data-ttu-id="348e9-146">ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="348e9-146">ConsoleTokenColors</span></span>

<span data-ttu-id="348e9-147">Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="348e9-147">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="348e9-148">Określa kolory tokenów IntelliSense w okienku konsoli programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="348e9-148">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Console pane.</span></span> <span data-ttu-id="348e9-149">Ta właściwość jest obiekt słownika zawierający pary nazwa/wartość typy tokenów i kolorów dla tego okienka konsoli.</span><span class="sxs-lookup"><span data-stu-id="348e9-149">This property is a dictionary object that contains name/value pairs of token types and colors for the Console pane.</span></span> <span data-ttu-id="348e9-150">Aby zmienić kolory tokenów IntelliSense w okienku skryptów, zobacz [TokenColors](#tokencolors).</span><span class="sxs-lookup"><span data-stu-id="348e9-150">To change the colors of the IntelliSense tokens in the Script pane, see [TokenColors](#tokencolors).</span></span> <span data-ttu-id="348e9-151">Aby przywrócić wartości domyślne kolory, zobacz [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span><span class="sxs-lookup"><span data-stu-id="348e9-151">To reset the colors to the default values, see [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span></span> <span data-ttu-id="348e9-152">Kolory tokenu można ustawić dla następujących: atrybut, polecenia, CommandArgument, CommandParameter, komentarza, GroupEnd, GroupStart, — słowo kluczowe, LineContinuation, LoopLabel, elementu członkowskiego, nowego wiersza, numer, operatora, pozycji, StatementSeparator, ciągu, typu, Nieznany, zmiennej.</span><span class="sxs-lookup"><span data-stu-id="348e9-152">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```powershell
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = 'green'
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = 'magenta'
```

### <a name="debugbackgroundcolor"></a><span data-ttu-id="348e9-153">DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="348e9-153">DebugBackgroundColor</span></span>

<span data-ttu-id="348e9-154">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="348e9-154">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="348e9-155">Określa kolor tła dla debugowania tekst wyświetlany w okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="348e9-155">Specifies the background color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="348e9-156">To wystąpienie **System.Windows.Media.Color** klasy.</span><span class="sxs-lookup"><span data-stu-id="348e9-156">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor = '#0000FF'
```

### <a name="debugforegroundcolor"></a><span data-ttu-id="348e9-157">DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="348e9-157">DebugForegroundColor</span></span>

<span data-ttu-id="348e9-158">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="348e9-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="348e9-159">Określa kolor pierwszego planu dla debugowania tekst wyświetlany w okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="348e9-159">Specifies the foreground color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="348e9-160">To wystąpienie **System.Windows.Media.Color** klasy.</span><span class="sxs-lookup"><span data-stu-id="348e9-160">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor = 'yellow'
```

### <a name="defaultoptions"></a><span data-ttu-id="348e9-161">DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="348e9-161">DefaultOptions</span></span>

<span data-ttu-id="348e9-162">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="348e9-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="348e9-163">Zbiór właściwości, które określają ma być używany podczas resetowania metody są używane wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="348e9-163">A collection of properties that specify the default values to be used when the Reset methods are used.</span></span>

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

### <a name="errorbackgroundcolor"></a><span data-ttu-id="348e9-164">ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="348e9-164">ErrorBackgroundColor</span></span>

<span data-ttu-id="348e9-165">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="348e9-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="348e9-166">Określa kolor tła dla błędu tekst wyświetlany w okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="348e9-166">Specifies the background color for error text that appears in the Console pane.</span></span> <span data-ttu-id="348e9-167">To wystąpienie **System.Windows.Media.Color** klasy.</span><span class="sxs-lookup"><span data-stu-id="348e9-167">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor = 'black'
```

### <a name="errorforegroundcolor"></a><span data-ttu-id="348e9-168">ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="348e9-168">ErrorForegroundColor</span></span>

<span data-ttu-id="348e9-169">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="348e9-169">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="348e9-170">Określa kolor pierwszego planu błąd tekst wyświetlany w okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="348e9-170">Specifies the foreground color for error text that appears in the Console pane.</span></span> <span data-ttu-id="348e9-171">To wystąpienie **System.Windows.Media.Color** klasy.</span><span class="sxs-lookup"><span data-stu-id="348e9-171">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor = 'green'
```

### <a name="fontname"></a><span data-ttu-id="348e9-172">FontName</span><span class="sxs-lookup"><span data-stu-id="348e9-172">FontName</span></span>

<span data-ttu-id="348e9-173">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="348e9-173">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="348e9-174">Określa nazwę czcionki aktualnie używane zarówno w okienku skryptów, jak i w okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="348e9-174">Specifies the font name currently in use in both the Script pane and the Console pane.</span></span>

```powershell
# Changes the font used in both panes.
$psISE.Options.FontName = 'Courier New'
```

### <a name="fontsize"></a><span data-ttu-id="348e9-175">FontSize</span><span class="sxs-lookup"><span data-stu-id="348e9-175">FontSize</span></span>

<span data-ttu-id="348e9-176">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="348e9-176">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="348e9-177">Określa rozmiar czcionki jako liczba całkowita.</span><span class="sxs-lookup"><span data-stu-id="348e9-177">Specifies the font size as an integer.</span></span> <span data-ttu-id="348e9-178">Jest on używany w okienku skryptów, w okienku polecenia i w okienku danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="348e9-178">It is used in the Script pane, the Command pane, and the Output pane.</span></span> <span data-ttu-id="348e9-179">Prawidłowy zakres wartości to 8 do 32.</span><span class="sxs-lookup"><span data-stu-id="348e9-179">The valid range of values is 8 through 32.</span></span>

```powershell
# Changes the font size in all panes.
$psISE.Options.FontSize = 20
```

### <a name="intellisensetimeoutinseconds"></a><span data-ttu-id="348e9-180">IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="348e9-180">IntellisenseTimeoutInSeconds</span></span>

<span data-ttu-id="348e9-181">Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="348e9-181">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="348e9-182">Określa liczbę sekund, używanych przez IntelliSense spróbować rozwiązać obecnie tekstu.</span><span class="sxs-lookup"><span data-stu-id="348e9-182">Specifies the number of seconds that IntelliSense uses to try to resolve the currently typed text.</span></span> <span data-ttu-id="348e9-183">Po następującej liczbie sekund IntelliSense upłynie limit czasu i umożliwia kontynuowanie, wpisując polecenie.</span><span class="sxs-lookup"><span data-stu-id="348e9-183">After this number of seconds, IntelliSense times out and enables you to continue typing.</span></span> <span data-ttu-id="348e9-184">Wartość domyślna to 3 sekundy.</span><span class="sxs-lookup"><span data-stu-id="348e9-184">The default value is 3 seconds.</span></span> <span data-ttu-id="348e9-185">Wartość jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="348e9-185">The value is an integer.</span></span>

```powershell
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a><span data-ttu-id="348e9-186">MruCount</span><span class="sxs-lookup"><span data-stu-id="348e9-186">MruCount</span></span>

<span data-ttu-id="348e9-187">Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="348e9-187">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="348e9-188">Określa liczbę ostatnio otwartych plików, które programu Windows PowerShell ISE śledzi i wyświetlane w dolnej części **Otwórz plik** menu.</span><span class="sxs-lookup"><span data-stu-id="348e9-188">Specifies the number of recently opened files that Windows PowerShell ISE tracks and displays at the bottom of the **File Open** menu.</span></span> <span data-ttu-id="348e9-189">Wartość domyślna to 10.</span><span class="sxs-lookup"><span data-stu-id="348e9-189">The default value is 10.</span></span> <span data-ttu-id="348e9-190">Wartość jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="348e9-190">The value is an integer.</span></span>

```powershell
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a><span data-ttu-id="348e9-191">OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="348e9-191">OutputPaneBackgroundColor</span></span>

<span data-ttu-id="348e9-192">Ta funkcja znajduje się w programie Windows PowerShell ISE 2.0, ale została usunięta lub zmieniona w nowszej wersji programu ISE.</span><span class="sxs-lookup"><span data-stu-id="348e9-192">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="348e9-193">W przypadku nowszych wersji, zobacz [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="348e9-193">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

<span data-ttu-id="348e9-194">Właściwość odczytu/zapisu, która pobiera lub ustawia kolor tła okienka wyjściowego samej siebie.</span><span class="sxs-lookup"><span data-stu-id="348e9-194">The read/write property that gets or sets the background color for the Output pane itself.</span></span> <span data-ttu-id="348e9-195">To wystąpienie **System.Windows.Media.Color** klasy.</span><span class="sxs-lookup"><span data-stu-id="348e9-195">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = 'gold'
```

### <a name="outputpanetextforegroundcolor"></a><span data-ttu-id="348e9-196">OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="348e9-196">OutputPaneTextForegroundColor</span></span>

<span data-ttu-id="348e9-197">Ta funkcja znajduje się w programie Windows PowerShell ISE 2.0, ale została usunięta lub zmieniona w nowszej wersji programu ISE.</span><span class="sxs-lookup"><span data-stu-id="348e9-197">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="348e9-198">W przypadku nowszych wersji, zobacz [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span><span class="sxs-lookup"><span data-stu-id="348e9-198">For later versions, see [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span></span>

<span data-ttu-id="348e9-199">Właściwości odczytu/zapisu, która zmienia kolor tekstu w okienku danych wyjściowych w programie Windows PowerShell ISE 2.0.</span><span class="sxs-lookup"><span data-stu-id="348e9-199">The read/write property that changes the foreground color of the text in the Output pane in Windows PowerShell ISE 2.0.</span></span>

```powershell
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = 'blue'
```

### <a name="outputpanetextbackgroundcolor"></a><span data-ttu-id="348e9-200">OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="348e9-200">OutputPaneTextBackgroundColor</span></span>

<span data-ttu-id="348e9-201">Ta funkcja znajduje się w programie Windows PowerShell ISE 2.0, ale została usunięta lub zmieniona w nowszej wersji programu ISE.</span><span class="sxs-lookup"><span data-stu-id="348e9-201">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="348e9-202">W przypadku nowszych wersji, zobacz [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="348e9-202">For later versions, see [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span></span>

<span data-ttu-id="348e9-203">Właściwości odczytu/zapisu, która zmienia kolor tła tekstu w okienku danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="348e9-203">The read/write property that changes the background color of the text in the Output pane.</span></span>

```powershell
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = 'pink'
```

### <a name="scriptpanebackgroundcolor"></a><span data-ttu-id="348e9-204">ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="348e9-204">ScriptPaneBackgroundColor</span></span>

<span data-ttu-id="348e9-205">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="348e9-205">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="348e9-206">Właściwości odczytu/zapisu, która pobiera lub ustawia kolor tła dla plików.</span><span class="sxs-lookup"><span data-stu-id="348e9-206">The read/write property that gets or sets the background color for files.</span></span> <span data-ttu-id="348e9-207">To wystąpienie **System.Windows.Media.Color** klasy.</span><span class="sxs-lookup"><span data-stu-id="348e9-207">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'
```

### <a name="scriptpaneforegroundcolor"></a><span data-ttu-id="348e9-208">ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="348e9-208">ScriptPaneForegroundColor</span></span>

<span data-ttu-id="348e9-209">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="348e9-209">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="348e9-210">Właściwości odczytu/zapisu, która pobiera lub ustawia kolor pierwszego planu dla plików z systemem innym niż skryptu w okienku skryptów.</span><span class="sxs-lookup"><span data-stu-id="348e9-210">The read/write property that gets or sets the foreground color for non-script files in the Script pane.</span></span>
<span data-ttu-id="348e9-211">Aby ustawić kolor pierwszego planu dla plików skryptów, użyj [TokenColors](#tokencolors).</span><span class="sxs-lookup"><span data-stu-id="348e9-211">To set the foreground color for script files, use the [TokenColors](#tokencolors).</span></span>

```powershell
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = 'green'
```

### <a name="selectedscriptpanestate"></a><span data-ttu-id="348e9-212">SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="348e9-212">SelectedScriptPaneState</span></span>

<span data-ttu-id="348e9-213">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="348e9-213">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="348e9-214">Właściwość odczytu/zapisu, która pobiera lub Ustawia położenie okienka Skrypt na ekranie.</span><span class="sxs-lookup"><span data-stu-id="348e9-214">The read/write property that gets or sets the position of the Script pane on the display.</span></span> <span data-ttu-id="348e9-215">Ten ciąg może być "Maximized", "Top" lub "Right".</span><span class="sxs-lookup"><span data-stu-id="348e9-215">The string can be either 'Maximized', 'Top', or 'Right'.</span></span>

```powershell
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = 'Top'
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = 'Right'
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = 'Maximized'
```

### <a name="showdefaultsnippets"></a><span data-ttu-id="348e9-216">ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="348e9-216">ShowDefaultSnippets</span></span>

<span data-ttu-id="348e9-217">Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="348e9-217">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="348e9-218">Określa, czy **CTRL + J** lista fragmentów zawiera zestaw starter, który znajduje się w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="348e9-218">Specifies whether the **CTRL+J** list of snippets includes the starter set that is included in Windows PowerShell.</span></span> <span data-ttu-id="348e9-219">Jeśli wartość **$false**, tylko wstawki zdefiniowane przez użytkownika są wyświetlane w **CTRL + J** listy.</span><span class="sxs-lookup"><span data-stu-id="348e9-219">When set to **$false**, only user-defined snippets appear in the **CTRL+J** list.</span></span> <span data-ttu-id="348e9-220">Wartość domyślna to **$true**.</span><span class="sxs-lookup"><span data-stu-id="348e9-220">The default value is **$true**.</span></span>

```powershell
# Hide the default snippets from the CTRL+J list.
$psISE.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a><span data-ttu-id="348e9-221">ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="348e9-221">ShowIntellisenseInConsolePane</span></span>

<span data-ttu-id="348e9-222">Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="348e9-222">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="348e9-223">Określa, czy IntelliSense oferuje składni, parametrów i sugestie wartość w okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="348e9-223">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Console pane.</span></span> <span data-ttu-id="348e9-224">Wartość domyślna to **$true**.</span><span class="sxs-lookup"><span data-stu-id="348e9-224">The default value is **$true**.</span></span>

```powershell
# Turn off IntelliSense in the console pane.
$psISE.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a><span data-ttu-id="348e9-225">ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="348e9-225">ShowIntellisenseInScriptPane</span></span>

<span data-ttu-id="348e9-226">Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="348e9-226">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="348e9-227">Określa, czy IntelliSense oferuje składni, parametrów i sugestie wartość w okienku skryptów.</span><span class="sxs-lookup"><span data-stu-id="348e9-227">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Script pane.</span></span> <span data-ttu-id="348e9-228">Wartość domyślna to **$true**.</span><span class="sxs-lookup"><span data-stu-id="348e9-228">The default value is **$true**.</span></span>

```powershell
# Turn off IntelliSense in the Script pane.
$psISE.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a><span data-ttu-id="348e9-229">ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="348e9-229">ShowLineNumbers</span></span>

<span data-ttu-id="348e9-230">Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="348e9-230">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="348e9-231">Określa, czy w okienku skryptu Wyświetla numery wierszy na lewym marginesie.</span><span class="sxs-lookup"><span data-stu-id="348e9-231">Specifies whether the Script pane displays line numbers in the left margin.</span></span> <span data-ttu-id="348e9-232">Wartość domyślna to **$true**.</span><span class="sxs-lookup"><span data-stu-id="348e9-232">The default value is **$true**.</span></span>

```powershell
# Turn off line numbers in the Script pane.
$psISE.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a><span data-ttu-id="348e9-233">ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="348e9-233">ShowOutlining</span></span>

<span data-ttu-id="348e9-234">Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="348e9-234">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="348e9-235">Określa, czy w okienku skryptu Wyświetla rozwijanej i zwijanej nawiasy obok fragmentów kodu na lewym marginesie.</span><span class="sxs-lookup"><span data-stu-id="348e9-235">Specifies whether the Script pane displays expandable and collapsible brackets next to sections of code in the left margin.</span></span> <span data-ttu-id="348e9-236">Gdy są one wyświetlane, możesz kliknąć minus \( - \) ikonami obok bloku tekstu, aby zwinąć lub kliknij przycisk plus \( + \) , aby rozwinąć blok tekstu.</span><span class="sxs-lookup"><span data-stu-id="348e9-236">When they are displayed, you can click the minus \(-\) icons next to a block of text to collapse it or click the plus \(+\) icon to expand a block of text.</span></span> <span data-ttu-id="348e9-237">Wartość domyślna to **$true**.</span><span class="sxs-lookup"><span data-stu-id="348e9-237">The default value is **$true**.</span></span>

```powershell
# Turn off outlining in the Script pane.
$psISE.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a><span data-ttu-id="348e9-238">ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="348e9-238">ShowToolBar</span></span>

<span data-ttu-id="348e9-239">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="348e9-239">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="348e9-240">Określa, czy pasek narzędzi ISE pojawia się w górnej części okna programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="348e9-240">Specifies whether the ISE toolbar appears at the top of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="348e9-241">Wartość domyślna to **$true**.</span><span class="sxs-lookup"><span data-stu-id="348e9-241">The default value is **$true**.</span></span>

```powershell
# Show the toolbar.
$psISE.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a><span data-ttu-id="348e9-242">ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="348e9-242">ShowWarningBeforeSavingOnRun</span></span>

<span data-ttu-id="348e9-243">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="348e9-243">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="348e9-244">Określa, czy jest wyświetlany komunikat ostrzegawczy, gdy przed uruchomieniem skryptu jest zapisywany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="348e9-244">Specifies whether a warning message appears when a script is saved automatically before it is run.</span></span> <span data-ttu-id="348e9-245">Wartość domyślna to **$true**.</span><span class="sxs-lookup"><span data-stu-id="348e9-245">The default value is **$true**.</span></span>

```powershell
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun = $true
```

### <a name="showwarningforduplicatefiles"></a><span data-ttu-id="348e9-246">ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="348e9-246">ShowWarningForDuplicateFiles</span></span>

<span data-ttu-id="348e9-247">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="348e9-247">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="348e9-248">Określa, czy jest wyświetlany komunikat ostrzegawczy, gdy ten sam plik jest otwarty na różnych kartach programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="348e9-248">Specifies whether a warning message appears when the same file is opened in different PowerShell tabs.</span></span> <span data-ttu-id="348e9-249">Jeśli ustawiono **$true**, aby otworzyć ten sam plik w wielu kartach wyświetla ten komunikat: "skopiuj ten plik jest otwarty w innej karty środowiska Windows PowerShell. Zmiany wprowadzone w tym pliku wpłynie na wszystkie otwarte kopie".</span><span class="sxs-lookup"><span data-stu-id="348e9-249">If set to **$true**, to open the same file in multiple tabs displays this message: "A copy of this file is open in another Windows PowerShell tab. Changes made to this file will affect all open copies."</span></span> <span data-ttu-id="348e9-250">Wartość domyślna to **$true**.</span><span class="sxs-lookup"><span data-stu-id="348e9-250">The default value is **$true**.</span></span>

```powershell
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true
```

### <a name="tokencolors"></a><span data-ttu-id="348e9-251">TokenColors</span><span class="sxs-lookup"><span data-stu-id="348e9-251">TokenColors</span></span>

<span data-ttu-id="348e9-252">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="348e9-252">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="348e9-253">Określa kolory tokenów IntelliSense w okienku skryptów programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="348e9-253">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Script pane.</span></span> <span data-ttu-id="348e9-254">Ta właściwość jest obiekt słownika zawierający pary nazwa/wartość typy tokenów i kolorów dla tego okienka skryptu.</span><span class="sxs-lookup"><span data-stu-id="348e9-254">This property is a dictionary object that contains name/value pairs of token types and colors for the Script pane.</span></span> <span data-ttu-id="348e9-255">Aby zmienić kolory tokenów IntelliSense w okienku konsoli, zobacz [ConsoleTokenColors](#consoletokencolors).</span><span class="sxs-lookup"><span data-stu-id="348e9-255">To change the colors of the IntelliSense tokens in the Console pane, see [ConsoleTokenColors](#consoletokencolors).</span></span> <span data-ttu-id="348e9-256">Aby przywrócić wartości domyślne kolory, zobacz [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span><span class="sxs-lookup"><span data-stu-id="348e9-256">To reset the colors to the default values, see [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span></span> <span data-ttu-id="348e9-257">Kolory tokenu można ustawić dla następujących: atrybut, polecenia, CommandArgument, CommandParameter, komentarza, GroupEnd, GroupStart, — słowo kluczowe, LineContinuation, LoopLabel, elementu członkowskiego, nowego wiersza, numer, operatora, pozycji, StatementSeparator, ciągu, typu, Nieznany, zmiennej.</span><span class="sxs-lookup"><span data-stu-id="348e9-257">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```powershell
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"
```

### <a name="useentertoselectinconsolepaneintellisense"></a><span data-ttu-id="348e9-258">UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="348e9-258">UseEnterToSelectInConsolePaneIntellisense</span></span>

<span data-ttu-id="348e9-259">Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="348e9-259">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="348e9-260">Określa, czy można używać klawisz Enter, aby wybrać IntelliSense Podana opcja w okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="348e9-260">Specifies whether you can use the Enter key to select an IntelliSense provided option in the Console pane.</span></span> <span data-ttu-id="348e9-261">Wartość domyślna to **$true**.</span><span class="sxs-lookup"><span data-stu-id="348e9-261">The default value is **$true**.</span></span>

```powershell
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $false
```

### <a name="useentertoselectinscriptpaneintellisense"></a><span data-ttu-id="348e9-262">UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="348e9-262">UseEnterToSelectInScriptPaneIntellisense</span></span>

<span data-ttu-id="348e9-263">Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="348e9-263">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="348e9-264">Określa, czy można używać klawisza Enter, aby wybrać opcję dostarczane do funkcji IntelliSense w okienku skryptów.</span><span class="sxs-lookup"><span data-stu-id="348e9-264">Specifies whether you can use the Enter key to select an IntelliSense-provided option in the Script pane.</span></span> <span data-ttu-id="348e9-265">Wartość domyślna to **$true**.</span><span class="sxs-lookup"><span data-stu-id="348e9-265">The default value is **$true**.</span></span>

```powershell
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $true
```

### <a name="uselocalhelp"></a><span data-ttu-id="348e9-266">UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="348e9-266">UseLocalHelp</span></span>

<span data-ttu-id="348e9-267">Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="348e9-267">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="348e9-268">Określa, czy Pomocy zainstalowanej lokalnie lub w trybie online TechNet Library pomocy jest wyświetlany, gdy kursor w słowach kluczowych naciśnij klawisz F1.</span><span class="sxs-lookup"><span data-stu-id="348e9-268">Specifies whether the locally installed Help or the online TechNet Library Help appears when you press F1 with the cursor positioned in a keyword.</span></span> <span data-ttu-id="348e9-269">Jeśli ustawiono **$true**, a następnie okno podręczne Wyświetla zawartość z pomocy instalowana lokalnie.</span><span class="sxs-lookup"><span data-stu-id="348e9-269">If set to **$true**, then a pop-up window shows content from the locally installed Help.</span></span> <span data-ttu-id="348e9-270">Pliki Pomocy można zainstalować, uruchamiając `Update-Help` polecenia.</span><span class="sxs-lookup"><span data-stu-id="348e9-270">You can install the Help files by running the `Update-Help` command.</span></span> <span data-ttu-id="348e9-271">Jeśli ustawiono **$false**, a następnie otwiera przeglądarkę na stronę w bibliotece TechNet.</span><span class="sxs-lookup"><span data-stu-id="348e9-271">If set to **$false**, then your browser opens to a page in the TechNet Library.</span></span>

```powershell
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp = $false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp = $true
```

### <a name="verbosebackgroundcolor"></a><span data-ttu-id="348e9-272">VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="348e9-272">VerboseBackgroundColor</span></span>

<span data-ttu-id="348e9-273">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="348e9-273">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="348e9-274">Określa kolor tła pełny tekst wyświetlany w okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="348e9-274">Specifies the background color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="348e9-275">Jest **System.Windows.Media.Color** obiektu.</span><span class="sxs-lookup"><span data-stu-id="348e9-275">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a><span data-ttu-id="348e9-276">VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="348e9-276">VerboseForegroundColor</span></span>

<span data-ttu-id="348e9-277">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="348e9-277">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="348e9-278">Określa kolor pierwszego planu pełny tekst wyświetlany w okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="348e9-278">Specifies the foreground color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="348e9-279">Jest **System.Windows.Media.Color** obiektu.</span><span class="sxs-lookup"><span data-stu-id="348e9-279">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor = 'yellow'
```

### <a name="warningbackgroundcolor"></a><span data-ttu-id="348e9-280">WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="348e9-280">WarningBackgroundColor</span></span>

<span data-ttu-id="348e9-281">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="348e9-281">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="348e9-282">Określa kolor tła ostrzeżenie tekst wyświetlany w okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="348e9-282">Specifies the background color for warning text that appears in the Console pane.</span></span> <span data-ttu-id="348e9-283">Jest **System.Windows.Media.Color** obiektu.</span><span class="sxs-lookup"><span data-stu-id="348e9-283">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor = '#0000FF'
```

### <a name="warningforegroundcolor"></a><span data-ttu-id="348e9-284">WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="348e9-284">WarningForegroundColor</span></span>

<span data-ttu-id="348e9-285">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="348e9-285">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="348e9-286">Określa kolor pierwszego planu ostrzeżenie tekst wyświetlany w okienku danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="348e9-286">Specifies the foreground color for warning text that appears in the Output pane.</span></span> <span data-ttu-id="348e9-287">Jest **System.Windows.Media.Color** obiektu.</span><span class="sxs-lookup"><span data-stu-id="348e9-287">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor = 'yellow'
```

### <a name="xmltokencolors"></a><span data-ttu-id="348e9-288">XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="348e9-288">XmlTokenColors</span></span>

<span data-ttu-id="348e9-289">Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="348e9-289">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="348e9-290">Określa obiekt słownika zawierający pary nazwa/wartość typy tokenów i kolory zawartość XML, która jest wyświetlana w środowisku Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="348e9-290">Specifies a dictionary object that contains name/value pairs of token types and colors for XML content that is displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="348e9-291">Kolory tokenu można ustawić dla następujących: atrybut, polecenia, CommandArgument, CommandParameter, komentarza, GroupEnd, GroupStart, — słowo kluczowe, LineContinuation, LoopLabel, elementu członkowskiego, nowego wiersza, numer, operatora, pozycji, StatementSeparator, ciągu, typu, Nieznany, zmiennej.</span><span class="sxs-lookup"><span data-stu-id="348e9-291">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span> <span data-ttu-id="348e9-292">Zobacz też [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="348e9-292">Also see [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span></span>

```powershell
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = 'green'
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = 'magenta'
```

### <a name="zoom"></a><span data-ttu-id="348e9-293">Powiększenie</span><span class="sxs-lookup"><span data-stu-id="348e9-293">Zoom</span></span>

<span data-ttu-id="348e9-294">Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="348e9-294">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="348e9-295">Określa rozmiar względny tekstu w okienku konsoli i skrypt.</span><span class="sxs-lookup"><span data-stu-id="348e9-295">Specifies the relative size of text in both the Console and Script panes.</span></span> <span data-ttu-id="348e9-296">Wartość domyślna to 100.</span><span class="sxs-lookup"><span data-stu-id="348e9-296">The default value is 100.</span></span> <span data-ttu-id="348e9-297">Mniejsze wartości powodują tekst w środowisku Windows PowerShell ISE i pojawienie się mniejszych większą liczbą spowodować tekst, który ma być wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="348e9-297">Smaller values cause the text in Windows PowerShell ISE to appear smaller while larger numbers cause text to appear larger.</span></span> <span data-ttu-id="348e9-298">Wartość jest liczbą całkowitą, która obejmuje 20 do 400.</span><span class="sxs-lookup"><span data-stu-id="348e9-298">The value is an integer that ranges from 20 to 400.</span></span>

```powershell
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a><span data-ttu-id="348e9-299">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="348e9-299">See Also</span></span>

- [<span data-ttu-id="348e9-300">Cel programu Windows PowerShell ISE skryptów modelu obiektów</span><span class="sxs-lookup"><span data-stu-id="348e9-300">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="348e9-301">Hierarchia modeli obiektów środowiska ISE</span><span class="sxs-lookup"><span data-stu-id="348e9-301">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)