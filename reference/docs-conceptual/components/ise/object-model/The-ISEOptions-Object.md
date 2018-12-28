---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISEOptions
ms.assetid: 75e2a76f-f3d1-490b-ad5d-e3829946aabb
ms.openlocfilehash: e756da21aaa5465f7fa6a90563b4180f0c89e87b
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405420"
---
# <a name="the-iseoptions-object"></a><span data-ttu-id="66e15-103">Obiekt ISEOptions</span><span class="sxs-lookup"><span data-stu-id="66e15-103">The ISEOptions Object</span></span>

<span data-ttu-id="66e15-104">**ISEOptions** obiekt reprezentuje różne ustawienia dla środowiska Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="66e15-104">The **ISEOptions** object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="66e15-105">To wystąpienie **Microsoft.PowerShell.Host.ISE.ISEOptions** klasy.</span><span class="sxs-lookup"><span data-stu-id="66e15-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEOptions** class.</span></span>

<span data-ttu-id="66e15-106">**ISEOptions** obiektu udostępnia następujące metody i właściwości.</span><span class="sxs-lookup"><span data-stu-id="66e15-106">The **ISEOptions** object provides the following methods and properties.</span></span>

## <a name="methods"></a><span data-ttu-id="66e15-107">Metody</span><span class="sxs-lookup"><span data-stu-id="66e15-107">Methods</span></span>

### <a name="restoredefaultconsoletokencolors"></a><span data-ttu-id="66e15-108">RestoreDefaultConsoleTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="66e15-108">RestoreDefaultConsoleTokenColors\(\)</span></span>

<span data-ttu-id="66e15-109">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="66e15-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="66e15-110">Przywraca domyślne wartości tokenu kolory w okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="66e15-110">Restores the default values of the token colors in the Console pane.</span></span>

```powershell
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = 'red'
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a><span data-ttu-id="66e15-111">RestoreDefaults\(\)</span><span class="sxs-lookup"><span data-stu-id="66e15-111">RestoreDefaults\(\)</span></span>

<span data-ttu-id="66e15-112">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="66e15-112">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="66e15-113">Przywraca domyślne wartości wszystkich ustawień opcji w okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="66e15-113">Restores the default values of all options settings in the Console pane.</span></span> <span data-ttu-id="66e15-114">Resetuje zachowanie różne komunikaty ostrzegawcze, które zapewniają standardowe pole wyboru, aby uniemożliwić wiadomość ponownie wyświetlone.</span><span class="sxs-lookup"><span data-stu-id="66e15-114">It also resets the behavior of various warning messages that provide the standard check box to prevent the message from being shown again.</span></span>

```powershell
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = 'orange'
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a><span data-ttu-id="66e15-115">RestoreDefaultTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="66e15-115">RestoreDefaultTokenColors\(\)</span></span>

<span data-ttu-id="66e15-116">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="66e15-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="66e15-117">Przywraca domyślne wartości tokenu kolory w okienku skryptów.</span><span class="sxs-lookup"><span data-stu-id="66e15-117">Restores the default values of the token colors in the Script pane.</span></span>

```powershell
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a><span data-ttu-id="66e15-118">RestoreDefaultXmlTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="66e15-118">RestoreDefaultXmlTokenColors\(\)</span></span>

<span data-ttu-id="66e15-119">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="66e15-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="66e15-120">Przywraca domyślne wartości tokenu kolorów dla elementów XML, które są wyświetlane w środowisku Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="66e15-120">Restores the default values of the token colors for XML elements that are displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="66e15-121">Zobacz też [XmlTokenColors](#xmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="66e15-121">Also see [XmlTokenColors](#xmltokencolors).</span></span>

```powershell
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a><span data-ttu-id="66e15-122">Właściwości</span><span class="sxs-lookup"><span data-stu-id="66e15-122">Properties</span></span>

### <a name="autosaveminuteinterval"></a><span data-ttu-id="66e15-123">AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="66e15-123">AutoSaveMinuteInterval</span></span>

<span data-ttu-id="66e15-124">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="66e15-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="66e15-125">Określa liczbę minut między operacjami automatycznego zapisywania plików przez program Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="66e15-125">Specifies the number of minutes between automatic save operations of your files by Windows PowerShell ISE.</span></span> <span data-ttu-id="66e15-126">Wartość domyślna to 2 minuty.</span><span class="sxs-lookup"><span data-stu-id="66e15-126">The default value is 2 minutes.</span></span> <span data-ttu-id="66e15-127">Wartość jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="66e15-127">The value is an integer.</span></span>

```powershell
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a><span data-ttu-id="66e15-128">CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="66e15-128">CommandPaneBackgroundColor</span></span>

<span data-ttu-id="66e15-129">Ta funkcja znajduje się w programie Windows PowerShell ISE 2.0, ale został usunięty lub zmieniono jego nazwę w nowszych wersjach środowiska ISE.</span><span class="sxs-lookup"><span data-stu-id="66e15-129">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="66e15-130">W przypadku nowszych wersji, zobacz [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="66e15-130">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

<span data-ttu-id="66e15-131">Określa kolor tła dla okienka polecenia.</span><span class="sxs-lookup"><span data-stu-id="66e15-131">Specifies the background color for the Command pane.</span></span> <span data-ttu-id="66e15-132">To wystąpienie **System.Windows.Media.Color** klasy.</span><span class="sxs-lookup"><span data-stu-id="66e15-132">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = 'orange'
```

### <a name="commandpaneup"></a><span data-ttu-id="66e15-133">CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="66e15-133">CommandPaneUp</span></span>

<span data-ttu-id="66e15-134">Ta funkcja znajduje się w programie Windows PowerShell ISE 2.0, ale został usunięty lub zmieniono jego nazwę w nowszych wersjach środowiska ISE.</span><span class="sxs-lookup"><span data-stu-id="66e15-134">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>

<span data-ttu-id="66e15-135">Określa, czy w okienku poleceń znajduje się powyżej w okienku danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="66e15-135">Specifies whether the Command pane is located above the Output pane.</span></span>

```powershell
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true
```

### <a name="consolepanebackgroundcolor"></a><span data-ttu-id="66e15-136">ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="66e15-136">ConsolePaneBackgroundColor</span></span>

<span data-ttu-id="66e15-137">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="66e15-137">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="66e15-138">Określa kolor tła dla okienka konsoli.</span><span class="sxs-lookup"><span data-stu-id="66e15-138">Specifies the background color for the Console pane.</span></span> <span data-ttu-id="66e15-139">To wystąpienie **System.Windows.Media.Color** klasy.</span><span class="sxs-lookup"><span data-stu-id="66e15-139">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = 'red'
```

### <a name="consolepaneforegroundcolor"></a><span data-ttu-id="66e15-140">ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="66e15-140">ConsolePaneForegroundColor</span></span>

<span data-ttu-id="66e15-141">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="66e15-141">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="66e15-142">Określa kolor tekstu w okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="66e15-142">Specifies the foreground color of the text in the Console pane.</span></span>

```powershell
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = 'yellow'
```

### <a name="consolepanetextbackgroundcolor"></a><span data-ttu-id="66e15-143">ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="66e15-143">ConsolePaneTextBackgroundColor</span></span>

<span data-ttu-id="66e15-144">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="66e15-144">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="66e15-145">Określa kolor tła tekstu w okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="66e15-145">Specifies the background color of the text in the Console pane.</span></span>

```powershell
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = 'pink'
```

### <a name="consoletokencolors"></a><span data-ttu-id="66e15-146">ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="66e15-146">ConsoleTokenColors</span></span>

<span data-ttu-id="66e15-147">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="66e15-147">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="66e15-148">Określa kolory tokenów IntelliSense w okienku konsoli programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="66e15-148">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Console pane.</span></span> <span data-ttu-id="66e15-149">Ta właściwość jest obiekt słownika zawierający pary nazwa/wartość typy tokenów i kolorów dla tego okienka konsoli.</span><span class="sxs-lookup"><span data-stu-id="66e15-149">This property is a dictionary object that contains name/value pairs of token types and colors for the Console pane.</span></span> <span data-ttu-id="66e15-150">Aby zmienić kolory tokenów IntelliSense w okienku skryptu, zobacz [TokenColors](#tokencolors).</span><span class="sxs-lookup"><span data-stu-id="66e15-150">To change the colors of the IntelliSense tokens in the Script pane, see [TokenColors](#tokencolors).</span></span> <span data-ttu-id="66e15-151">Aby przywrócić kolory domyślne wartości, zobacz [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span><span class="sxs-lookup"><span data-stu-id="66e15-151">To reset the colors to the default values, see [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span></span> <span data-ttu-id="66e15-152">Kolory tokenów można ustawić dla następujących elementów: Atrybut, polecenia, Właściwość CommandArgument, CommandParameter, komentarz, GroupEnd, GroupStart, — słowo kluczowe, LineContinuation, LoopLabel, elementu członkowskiego, nowego wiersza, numer, operatora, pozycja, StatementSeparator, ciąg, typu, nieznany, zmiennej.</span><span class="sxs-lookup"><span data-stu-id="66e15-152">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```powershell
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = 'green'
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = 'magenta'
```

### <a name="debugbackgroundcolor"></a><span data-ttu-id="66e15-153">DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="66e15-153">DebugBackgroundColor</span></span>

<span data-ttu-id="66e15-154">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="66e15-154">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="66e15-155">Określa kolor tła tekstu debugowania, który pojawia się w okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="66e15-155">Specifies the background color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="66e15-156">To wystąpienie **System.Windows.Media.Color** klasy.</span><span class="sxs-lookup"><span data-stu-id="66e15-156">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor = '#0000FF'
```

### <a name="debugforegroundcolor"></a><span data-ttu-id="66e15-157">DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="66e15-157">DebugForegroundColor</span></span>

<span data-ttu-id="66e15-158">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="66e15-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="66e15-159">Określa kolor pierwszego planu dla tekstu debugowania, który jest wyświetlany w okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="66e15-159">Specifies the foreground color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="66e15-160">To wystąpienie **System.Windows.Media.Color** klasy.</span><span class="sxs-lookup"><span data-stu-id="66e15-160">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor = 'yellow'
```

### <a name="defaultoptions"></a><span data-ttu-id="66e15-161">DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="66e15-161">DefaultOptions</span></span>

<span data-ttu-id="66e15-162">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="66e15-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="66e15-163">Zbiór właściwości, które określają wartości domyślne, które będą używane podczas resetowania metody są używane.</span><span class="sxs-lookup"><span data-stu-id="66e15-163">A collection of properties that specify the default values to be used when the Reset methods are used.</span></span>

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

### <a name="errorbackgroundcolor"></a><span data-ttu-id="66e15-164">ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="66e15-164">ErrorBackgroundColor</span></span>

<span data-ttu-id="66e15-165">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="66e15-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="66e15-166">Określa kolor tła tekst błędu, który pojawia się w okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="66e15-166">Specifies the background color for error text that appears in the Console pane.</span></span> <span data-ttu-id="66e15-167">To wystąpienie **System.Windows.Media.Color** klasy.</span><span class="sxs-lookup"><span data-stu-id="66e15-167">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor = 'black'
```

### <a name="errorforegroundcolor"></a><span data-ttu-id="66e15-168">ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="66e15-168">ErrorForegroundColor</span></span>

<span data-ttu-id="66e15-169">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="66e15-169">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="66e15-170">Określa kolor pierwszego planu tekst błędu, który pojawia się w okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="66e15-170">Specifies the foreground color for error text that appears in the Console pane.</span></span> <span data-ttu-id="66e15-171">To wystąpienie **System.Windows.Media.Color** klasy.</span><span class="sxs-lookup"><span data-stu-id="66e15-171">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor = 'green'
```

### <a name="fontname"></a><span data-ttu-id="66e15-172">FontName</span><span class="sxs-lookup"><span data-stu-id="66e15-172">FontName</span></span>

<span data-ttu-id="66e15-173">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="66e15-173">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="66e15-174">Określa nazwę czcionki aktualnie używanym w okienku skryptów i okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="66e15-174">Specifies the font name currently in use in both the Script pane and the Console pane.</span></span>

```powershell
# Changes the font used in both panes.
$psISE.Options.FontName = 'Courier New'
```

### <a name="fontsize"></a><span data-ttu-id="66e15-175">FontSize</span><span class="sxs-lookup"><span data-stu-id="66e15-175">FontSize</span></span>

<span data-ttu-id="66e15-176">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="66e15-176">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="66e15-177">Określa rozmiar czcionki jako liczba całkowita.</span><span class="sxs-lookup"><span data-stu-id="66e15-177">Specifies the font size as an integer.</span></span> <span data-ttu-id="66e15-178">Jest on używany w okienku skryptów, w okienku poleceń i okienko danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="66e15-178">It is used in the Script pane, the Command pane, and the Output pane.</span></span> <span data-ttu-id="66e15-179">Prawidłowy zakres wartości wynosi 8 do 32.</span><span class="sxs-lookup"><span data-stu-id="66e15-179">The valid range of values is 8 through 32.</span></span>

```powershell
# Changes the font size in all panes.
$psISE.Options.FontSize = 20
```

### <a name="intellisensetimeoutinseconds"></a><span data-ttu-id="66e15-180">IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="66e15-180">IntellisenseTimeoutInSeconds</span></span>

<span data-ttu-id="66e15-181">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="66e15-181">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="66e15-182">Określa liczbę sekund, które korzysta z technologii IntelliSense spróbować rozwiązać obecnie tekstu.</span><span class="sxs-lookup"><span data-stu-id="66e15-182">Specifies the number of seconds that IntelliSense uses to try to resolve the currently typed text.</span></span> <span data-ttu-id="66e15-183">Po następującej liczbie sekund IntelliSense upłynie limit czasu i umożliwia kontynuowanie wpisywania.</span><span class="sxs-lookup"><span data-stu-id="66e15-183">After this number of seconds, IntelliSense times out and enables you to continue typing.</span></span> <span data-ttu-id="66e15-184">Wartość domyślna to 3 sekundy.</span><span class="sxs-lookup"><span data-stu-id="66e15-184">The default value is 3 seconds.</span></span> <span data-ttu-id="66e15-185">Wartość jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="66e15-185">The value is an integer.</span></span>

```powershell
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a><span data-ttu-id="66e15-186">MruCount</span><span class="sxs-lookup"><span data-stu-id="66e15-186">MruCount</span></span>

<span data-ttu-id="66e15-187">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="66e15-187">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="66e15-188">Określa liczbę ostatnio otwartych plików, które program Windows PowerShell ISE śledzi i wyświetlane w dolnej części **Otwórz plik** menu.</span><span class="sxs-lookup"><span data-stu-id="66e15-188">Specifies the number of recently opened files that Windows PowerShell ISE tracks and displays at the bottom of the **File Open** menu.</span></span> <span data-ttu-id="66e15-189">Wartość domyślna to 10.</span><span class="sxs-lookup"><span data-stu-id="66e15-189">The default value is 10.</span></span> <span data-ttu-id="66e15-190">Wartość jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="66e15-190">The value is an integer.</span></span>

```powershell
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a><span data-ttu-id="66e15-191">OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="66e15-191">OutputPaneBackgroundColor</span></span>

<span data-ttu-id="66e15-192">Ta funkcja znajduje się w programie Windows PowerShell ISE 2.0, ale został usunięty lub zmieniono jego nazwę w nowszych wersjach środowiska ISE.</span><span class="sxs-lookup"><span data-stu-id="66e15-192">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="66e15-193">W przypadku nowszych wersji, zobacz [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="66e15-193">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

<span data-ttu-id="66e15-194">Pobiera lub ustawia kolor tła dla okienka danych wyjściowych, sama właściwość do odczytu/zapisu.</span><span class="sxs-lookup"><span data-stu-id="66e15-194">The read/write property that gets or sets the background color for the Output pane itself.</span></span> <span data-ttu-id="66e15-195">To wystąpienie **System.Windows.Media.Color** klasy.</span><span class="sxs-lookup"><span data-stu-id="66e15-195">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = 'gold'
```

### <a name="outputpanetextforegroundcolor"></a><span data-ttu-id="66e15-196">OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="66e15-196">OutputPaneTextForegroundColor</span></span>

<span data-ttu-id="66e15-197">Ta funkcja znajduje się w programie Windows PowerShell ISE 2.0, ale został usunięty lub zmieniono jego nazwę w nowszych wersjach środowiska ISE.</span><span class="sxs-lookup"><span data-stu-id="66e15-197">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="66e15-198">W przypadku nowszych wersji, zobacz [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span><span class="sxs-lookup"><span data-stu-id="66e15-198">For later versions, see [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span></span>

<span data-ttu-id="66e15-199">Właściwości odczytu/zapisu, który zmienia kolor pierwszego planu tekstu w okienku danych wyjściowych w programie Windows PowerShell ISE 2.0.</span><span class="sxs-lookup"><span data-stu-id="66e15-199">The read/write property that changes the foreground color of the text in the Output pane in Windows PowerShell ISE 2.0.</span></span>

```powershell
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = 'blue'
```

### <a name="outputpanetextbackgroundcolor"></a><span data-ttu-id="66e15-200">OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="66e15-200">OutputPaneTextBackgroundColor</span></span>

<span data-ttu-id="66e15-201">Ta funkcja znajduje się w programie Windows PowerShell ISE 2.0, ale został usunięty lub zmieniono jego nazwę w nowszych wersjach środowiska ISE.</span><span class="sxs-lookup"><span data-stu-id="66e15-201">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="66e15-202">W przypadku nowszych wersji, zobacz [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="66e15-202">For later versions, see [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span></span>

<span data-ttu-id="66e15-203">Właściwości odczytu/zapisu, który zmienia kolor tła tekstu w okienku danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="66e15-203">The read/write property that changes the background color of the text in the Output pane.</span></span>

```powershell
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = 'pink'
```

### <a name="scriptpanebackgroundcolor"></a><span data-ttu-id="66e15-204">ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="66e15-204">ScriptPaneBackgroundColor</span></span>

<span data-ttu-id="66e15-205">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="66e15-205">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="66e15-206">Właściwości odczytu/zapisu, który pobiera lub ustawia kolor tła dla plików.</span><span class="sxs-lookup"><span data-stu-id="66e15-206">The read/write property that gets or sets the background color for files.</span></span> <span data-ttu-id="66e15-207">To wystąpienie **System.Windows.Media.Color** klasy.</span><span class="sxs-lookup"><span data-stu-id="66e15-207">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'
```

### <a name="scriptpaneforegroundcolor"></a><span data-ttu-id="66e15-208">ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="66e15-208">ScriptPaneForegroundColor</span></span>

<span data-ttu-id="66e15-209">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="66e15-209">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="66e15-210">Właściwości odczytu/zapisu, która pobiera lub ustawia kolor pierwszego planu dla plików bez skryptu w okienku skryptów.</span><span class="sxs-lookup"><span data-stu-id="66e15-210">The read/write property that gets or sets the foreground color for non-script files in the Script pane.</span></span>
<span data-ttu-id="66e15-211">Aby ustawić kolor pierwszego planu dla plików skryptów, użyj [TokenColors](#tokencolors).</span><span class="sxs-lookup"><span data-stu-id="66e15-211">To set the foreground color for script files, use the [TokenColors](#tokencolors).</span></span>

```powershell
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = 'green'
```

### <a name="selectedscriptpanestate"></a><span data-ttu-id="66e15-212">SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="66e15-212">SelectedScriptPaneState</span></span>

<span data-ttu-id="66e15-213">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="66e15-213">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="66e15-214">Właściwości odczytu/zapisu, który pobiera lub Ustawia położenie okienka Skrypt na ekranie.</span><span class="sxs-lookup"><span data-stu-id="66e15-214">The read/write property that gets or sets the position of the Script pane on the display.</span></span> <span data-ttu-id="66e15-215">Ciąg może być "Maximized", "Top" lub "Right".</span><span class="sxs-lookup"><span data-stu-id="66e15-215">The string can be either 'Maximized', 'Top', or 'Right'.</span></span>

```powershell
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = 'Top'
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = 'Right'
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = 'Maximized'
```

### <a name="showdefaultsnippets"></a><span data-ttu-id="66e15-216">ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="66e15-216">ShowDefaultSnippets</span></span>

<span data-ttu-id="66e15-217">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="66e15-217">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="66e15-218">Określa, czy **CTRL + J** lista fragmenty obejmuje początkowy zestaw, który znajduje się w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="66e15-218">Specifies whether the **CTRL+J** list of snippets includes the starter set that is included in Windows PowerShell.</span></span> <span data-ttu-id="66e15-219">Po ustawieniu **$false**, tylko fragmenty zdefiniowanych przez użytkownika są wyświetlane w **CTRL + J** listy.</span><span class="sxs-lookup"><span data-stu-id="66e15-219">When set to **$false**, only user-defined snippets appear in the **CTRL+J** list.</span></span> <span data-ttu-id="66e15-220">Wartość domyślna to **$true**.</span><span class="sxs-lookup"><span data-stu-id="66e15-220">The default value is **$true**.</span></span>

```powershell
# Hide the default snippets from the CTRL+J list.
$psISE.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a><span data-ttu-id="66e15-221">ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="66e15-221">ShowIntellisenseInConsolePane</span></span>

<span data-ttu-id="66e15-222">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="66e15-222">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="66e15-223">Określa, czy funkcja IntelliSense oferuje składni, parametrów i wartości sugestie w okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="66e15-223">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Console pane.</span></span> <span data-ttu-id="66e15-224">Wartość domyślna to **$true**.</span><span class="sxs-lookup"><span data-stu-id="66e15-224">The default value is **$true**.</span></span>

```powershell
# Turn off IntelliSense in the console pane.
$psISE.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a><span data-ttu-id="66e15-225">ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="66e15-225">ShowIntellisenseInScriptPane</span></span>

<span data-ttu-id="66e15-226">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="66e15-226">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="66e15-227">Określa, czy funkcja IntelliSense oferuje składni, parametrów i sugestii wartości w okienku skryptów.</span><span class="sxs-lookup"><span data-stu-id="66e15-227">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Script pane.</span></span> <span data-ttu-id="66e15-228">Wartość domyślna to **$true**.</span><span class="sxs-lookup"><span data-stu-id="66e15-228">The default value is **$true**.</span></span>

```powershell
# Turn off IntelliSense in the Script pane.
$psISE.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a><span data-ttu-id="66e15-229">ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="66e15-229">ShowLineNumbers</span></span>

<span data-ttu-id="66e15-230">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="66e15-230">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="66e15-231">Określa, czy w okienku skryptu wyświetlają się numery wierszy na lewym marginesie.</span><span class="sxs-lookup"><span data-stu-id="66e15-231">Specifies whether the Script pane displays line numbers in the left margin.</span></span> <span data-ttu-id="66e15-232">Wartość domyślna to **$true**.</span><span class="sxs-lookup"><span data-stu-id="66e15-232">The default value is **$true**.</span></span>

```powershell
# Turn off line numbers in the Script pane.
$psISE.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a><span data-ttu-id="66e15-233">ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="66e15-233">ShowOutlining</span></span>

<span data-ttu-id="66e15-234">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="66e15-234">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="66e15-235">Określa, czy w okienku skryptu Wyświetla rozwijanej i zwijanej nawiasach obok sekcji kodu, na lewym marginesie.</span><span class="sxs-lookup"><span data-stu-id="66e15-235">Specifies whether the Script pane displays expandable and collapsible brackets next to sections of code in the left margin.</span></span> <span data-ttu-id="66e15-236">Gdy są one wyświetlane, można kliknąć znak minus \( - \) ikony obok blok tekstu, aby go zwinąć lub kliknij przycisk plus \( + \) ikonę, aby rozwinąć blok tekstu.</span><span class="sxs-lookup"><span data-stu-id="66e15-236">When they are displayed, you can click the minus \(-\) icons next to a block of text to collapse it or click the plus \(+\) icon to expand a block of text.</span></span> <span data-ttu-id="66e15-237">Wartość domyślna to **$true**.</span><span class="sxs-lookup"><span data-stu-id="66e15-237">The default value is **$true**.</span></span>

```powershell
# Turn off outlining in the Script pane.
$psISE.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a><span data-ttu-id="66e15-238">ShowToolbar —</span><span class="sxs-lookup"><span data-stu-id="66e15-238">ShowToolBar</span></span>

<span data-ttu-id="66e15-239">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="66e15-239">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="66e15-240">Określa, czy pasek narzędzi środowiska ISE pojawia się w górnej części okna programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="66e15-240">Specifies whether the ISE toolbar appears at the top of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="66e15-241">Wartość domyślna to **$true**.</span><span class="sxs-lookup"><span data-stu-id="66e15-241">The default value is **$true**.</span></span>

```powershell
# Show the toolbar.
$psISE.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a><span data-ttu-id="66e15-242">ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="66e15-242">ShowWarningBeforeSavingOnRun</span></span>

<span data-ttu-id="66e15-243">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="66e15-243">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="66e15-244">Określa, czy jest wyświetlany komunikat ostrzegawczy, gdy przed uruchomieniem skryptu są zapisywane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="66e15-244">Specifies whether a warning message appears when a script is saved automatically before it is run.</span></span> <span data-ttu-id="66e15-245">Wartość domyślna to **$true**.</span><span class="sxs-lookup"><span data-stu-id="66e15-245">The default value is **$true**.</span></span>

```powershell
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun = $true
```

### <a name="showwarningforduplicatefiles"></a><span data-ttu-id="66e15-246">ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="66e15-246">ShowWarningForDuplicateFiles</span></span>

<span data-ttu-id="66e15-247">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="66e15-247">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="66e15-248">Określa, czy jest wyświetlany komunikat ostrzegawczy, gdy ten sam plik jest otwarty na różnych kartach programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="66e15-248">Specifies whether a warning message appears when the same file is opened in different PowerShell tabs.</span></span> <span data-ttu-id="66e15-249">Jeśli ustawiono **$true**, aby otworzyć ten sam plik w wielu kartach wyświetla ten komunikat: "Skopiuj ten plik jest otwarty w innej karcie środowiska Windows PowerShell. Zmiany wprowadzone do tego pliku wpłynie na wszystkie otwarte kopie".</span><span class="sxs-lookup"><span data-stu-id="66e15-249">If set to **$true**, to open the same file in multiple tabs displays this message: "A copy of this file is open in another Windows PowerShell tab. Changes made to this file will affect all open copies."</span></span> <span data-ttu-id="66e15-250">Wartość domyślna to **$true**.</span><span class="sxs-lookup"><span data-stu-id="66e15-250">The default value is **$true**.</span></span>

```powershell
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true
```

### <a name="tokencolors"></a><span data-ttu-id="66e15-251">TokenColors</span><span class="sxs-lookup"><span data-stu-id="66e15-251">TokenColors</span></span>

<span data-ttu-id="66e15-252">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="66e15-252">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="66e15-253">Określa kolory tokenów IntelliSense w okienku skryptu programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="66e15-253">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Script pane.</span></span> <span data-ttu-id="66e15-254">Ta właściwość jest obiekt słownika zawierający pary nazwa/wartość typy tokenów i kolory w okienku skryptów.</span><span class="sxs-lookup"><span data-stu-id="66e15-254">This property is a dictionary object that contains name/value pairs of token types and colors for the Script pane.</span></span> <span data-ttu-id="66e15-255">Aby zmienić kolory tokenów IntelliSense w okienku konsoli, zobacz [ConsoleTokenColors](#consoletokencolors).</span><span class="sxs-lookup"><span data-stu-id="66e15-255">To change the colors of the IntelliSense tokens in the Console pane, see [ConsoleTokenColors](#consoletokencolors).</span></span> <span data-ttu-id="66e15-256">Aby przywrócić kolory domyślne wartości, zobacz [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span><span class="sxs-lookup"><span data-stu-id="66e15-256">To reset the colors to the default values, see [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span></span> <span data-ttu-id="66e15-257">Kolory tokenów można ustawić dla następujących elementów: Atrybut, polecenia, Właściwość CommandArgument, CommandParameter, komentarz, GroupEnd, GroupStart, — słowo kluczowe, LineContinuation, LoopLabel, elementu członkowskiego, nowego wiersza, numer, operatora, pozycja, StatementSeparator, ciąg, typu, nieznany, zmiennej.</span><span class="sxs-lookup"><span data-stu-id="66e15-257">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```powershell
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"
```

### <a name="useentertoselectinconsolepaneintellisense"></a><span data-ttu-id="66e15-258">UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="66e15-258">UseEnterToSelectInConsolePaneIntellisense</span></span>

<span data-ttu-id="66e15-259">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="66e15-259">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="66e15-260">Określa, czy można użyć klawisz Enter, aby wybrać funkcję IntelliSense, podana opcja w okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="66e15-260">Specifies whether you can use the Enter key to select an IntelliSense provided option in the Console pane.</span></span> <span data-ttu-id="66e15-261">Wartość domyślna to **$true**.</span><span class="sxs-lookup"><span data-stu-id="66e15-261">The default value is **$true**.</span></span>

```powershell
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $false
```

### <a name="useentertoselectinscriptpaneintellisense"></a><span data-ttu-id="66e15-262">UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="66e15-262">UseEnterToSelectInScriptPaneIntellisense</span></span>

<span data-ttu-id="66e15-263">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="66e15-263">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="66e15-264">Określa, czy można użyć klawisza Enter, aby wybrać określoną opcję dostarczone przez funkcję IntelliSense w okienku skryptów.</span><span class="sxs-lookup"><span data-stu-id="66e15-264">Specifies whether you can use the Enter key to select an IntelliSense-provided option in the Script pane.</span></span> <span data-ttu-id="66e15-265">Wartość domyślna to **$true**.</span><span class="sxs-lookup"><span data-stu-id="66e15-265">The default value is **$true**.</span></span>

```powershell
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $true
```

### <a name="uselocalhelp"></a><span data-ttu-id="66e15-266">UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="66e15-266">UseLocalHelp</span></span>

<span data-ttu-id="66e15-267">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="66e15-267">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="66e15-268">Określa, czy zainstalowane lokalnie pomocy lub TechNet Library pomocy online pojawia się po naciśnięciu klawisza F1, umieść kursor w słowem kluczowym.</span><span class="sxs-lookup"><span data-stu-id="66e15-268">Specifies whether the locally installed Help or the online TechNet Library Help appears when you press F1 with the cursor positioned in a keyword.</span></span> <span data-ttu-id="66e15-269">Jeśli ustawiono **$true**, wówczas okno podręczne zawiera zawartości z zainstalowanymi lokalnie pomocy.</span><span class="sxs-lookup"><span data-stu-id="66e15-269">If set to **$true**, then a pop-up window shows content from the locally installed Help.</span></span> <span data-ttu-id="66e15-270">Pliki Pomocy można zainstalować, uruchamiając `Update-Help` polecenia.</span><span class="sxs-lookup"><span data-stu-id="66e15-270">You can install the Help files by running the `Update-Help` command.</span></span> <span data-ttu-id="66e15-271">Jeśli wartość **$false**, a następnie w przeglądarce zostanie otwarta na stronę w bibliotece TechNet.</span><span class="sxs-lookup"><span data-stu-id="66e15-271">If set to **$false**, then your browser opens to a page in the TechNet Library.</span></span>

```powershell
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp = $false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp = $true
```

### <a name="verbosebackgroundcolor"></a><span data-ttu-id="66e15-272">VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="66e15-272">VerboseBackgroundColor</span></span>

<span data-ttu-id="66e15-273">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="66e15-273">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="66e15-274">Określa kolor tła dla pełnego tekstu, który jest wyświetlany w okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="66e15-274">Specifies the background color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="66e15-275">Jest **System.Windows.Media.Color** obiektu.</span><span class="sxs-lookup"><span data-stu-id="66e15-275">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a><span data-ttu-id="66e15-276">VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="66e15-276">VerboseForegroundColor</span></span>

<span data-ttu-id="66e15-277">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="66e15-277">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="66e15-278">Określa kolor pierwszego planu dla pełnego tekstu, który jest wyświetlany w okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="66e15-278">Specifies the foreground color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="66e15-279">Jest **System.Windows.Media.Color** obiektu.</span><span class="sxs-lookup"><span data-stu-id="66e15-279">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor = 'yellow'
```

### <a name="warningbackgroundcolor"></a><span data-ttu-id="66e15-280">WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="66e15-280">WarningBackgroundColor</span></span>

<span data-ttu-id="66e15-281">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="66e15-281">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="66e15-282">Określa kolor tła tekstu ostrzeżenia, który pojawia się w okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="66e15-282">Specifies the background color for warning text that appears in the Console pane.</span></span> <span data-ttu-id="66e15-283">Jest **System.Windows.Media.Color** obiektu.</span><span class="sxs-lookup"><span data-stu-id="66e15-283">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor = '#0000FF'
```

### <a name="warningforegroundcolor"></a><span data-ttu-id="66e15-284">WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="66e15-284">WarningForegroundColor</span></span>

<span data-ttu-id="66e15-285">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="66e15-285">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="66e15-286">Określa kolor pierwszego planu tekst ostrzeżenia, który pojawia się w okienku danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="66e15-286">Specifies the foreground color for warning text that appears in the Output pane.</span></span> <span data-ttu-id="66e15-287">Jest **System.Windows.Media.Color** obiektu.</span><span class="sxs-lookup"><span data-stu-id="66e15-287">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor = 'yellow'
```

### <a name="xmltokencolors"></a><span data-ttu-id="66e15-288">XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="66e15-288">XmlTokenColors</span></span>

<span data-ttu-id="66e15-289">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="66e15-289">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="66e15-290">Określa obiekt słownika zawierający pary nazwa/wartość typy tokenów i kolorów dla zawartości XML, który jest wyświetlany w środowisku Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="66e15-290">Specifies a dictionary object that contains name/value pairs of token types and colors for XML content that is displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="66e15-291">Kolory tokenów można ustawić dla następujących elementów: Atrybut, polecenia, Właściwość CommandArgument, CommandParameter, komentarz, GroupEnd, GroupStart, — słowo kluczowe, LineContinuation, LoopLabel, elementu członkowskiego, nowego wiersza, numer, operatora, pozycja, StatementSeparator, ciąg, typu, nieznany, zmiennej.</span><span class="sxs-lookup"><span data-stu-id="66e15-291">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span> <span data-ttu-id="66e15-292">Zobacz też [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="66e15-292">Also see [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span></span>

```powershell
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = 'green'
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = 'magenta'
```

### <a name="zoom"></a><span data-ttu-id="66e15-293">Powiększenie</span><span class="sxs-lookup"><span data-stu-id="66e15-293">Zoom</span></span>

<span data-ttu-id="66e15-294">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="66e15-294">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="66e15-295">Określa względny rozmiar tekstu w okienku konsoli i skryptów.</span><span class="sxs-lookup"><span data-stu-id="66e15-295">Specifies the relative size of text in both the Console and Script panes.</span></span> <span data-ttu-id="66e15-296">Wartość domyślna to 100.</span><span class="sxs-lookup"><span data-stu-id="66e15-296">The default value is 100.</span></span> <span data-ttu-id="66e15-297">Mniejsze wartości powodują tekst w środowisku Windows PowerShell ISE pojawienie mniejszej liczby większe powodują tekst wyświetlany większe.</span><span class="sxs-lookup"><span data-stu-id="66e15-297">Smaller values cause the text in Windows PowerShell ISE to appear smaller while larger numbers cause text to appear larger.</span></span> <span data-ttu-id="66e15-298">Wartość jest liczbą całkowitą z zakresu od 20 do 400.</span><span class="sxs-lookup"><span data-stu-id="66e15-298">The value is an integer that ranges from 20 to 400.</span></span>

```powershell
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a><span data-ttu-id="66e15-299">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="66e15-299">See Also</span></span>

- [<span data-ttu-id="66e15-300">Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="66e15-300">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="66e15-301">Hierarchia modeli obiektów środowiska ISE</span><span class="sxs-lookup"><span data-stu-id="66e15-301">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)