---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt PowerShellTab
ms.assetid: a9b58556-951b-4f48-b3ae-b351b7564360
ms.openlocfilehash: 577e2aaaddf3071801816d9ae91dbf0006dd5072
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057676"
---
# <a name="the-powershelltab-object"></a>Obiekt PowerShellTab

**PowerShellTab** obiekt reprezentuje środowiska uruchomieniowego programu Windows PowerShell.

## <a name="methods"></a>Metody

### <a name="invoke-script-"></a>Wywoływanie\( skryptu \)

Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.

Uruchamia skrypt danej karcie programu PowerShell.

> [!NOTE]
> Ta metoda działa tylko na innych kartach programu PowerShell nie kartę programu PowerShell, w którym jest wykonywane. Nie zwraca żadnych obiekt lub wartość. Jeżeli kod modyfikuje dowolnej zmiennej, te zmiany zostaną zachowane na karcie, względem którego wywołano polecenie.

**Skrypt** -System.Management.Automation.ScriptBlock lub ciągu bloku skryptu do uruchomienia.

```powershell
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psISE.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a>InvokeSynchronous\( skryptu \[useNewScope\], millisecondsTimeout \)

Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.

Uruchamia skrypt danej karcie programu PowerShell.

> [!NOTE]
> Ta metoda działa tylko na innych kartach programu PowerShell nie kartę programu PowerShell, w którym jest wykonywane. Blok skryptu zostanie uruchomione, a każdą wartość, która jest zwracana w skrypcie jest zwracana do środowisko uruchomieniowe, z którego wywołano polecenie. Jeśli wykonanie tego polecenia może być dłuższy niż **millesecondsTimeout** określa wartość, a następnie polecenie kończy się niepowodzeniem z powodu wyjątku: "Operacji został przekroczony."

**Skrypt** -System.Management.Automation.ScriptBlock lub ciągu bloku skryptu do uruchomienia.

**\[useNewScope\]**  -opcjonalna wartość logiczna, wartość domyślna to **$true** Jeśli równa **$true**, a następnie jest tworzony nowy zakres, w którym należy uruchomić polecenie. Środowisko uruchomieniowe karty programu PowerShell, który jest określony za pomocą polecenia nie powoduje modyfikacji.

**\[millisecondsTimeout\]**  -opcjonalną liczbą całkowitą, która domyślnie **500**.
Jeśli polecenie zakończy się w określonym czasie, a następnie polecenie spowoduje wygenerowanie **TimeoutException** z komunikatem "Operacja przekroczyła limit."

```powershell
# Create a new PowerShell tab and then switch back to the first
$psISE.PowerShellTabs.Add()
$psISE.PowerShellTabs.SetSelectedPowerShellTab($psISE.PowerShellTabs[0])

# Invoke a simple command on the other tab, in its own scope
$psISE.PowerShellTabs[1].InvokeSynchronous('$x=1', $false)
# You can switch to the other tab and type '$x' to see that the value is saved there.

# This example sets a value in the other tab (in a different scope)
# and returns it through the pipeline to this tab to store in $a
$a = $psISE.PowerShellTabs[1].InvokeSynchronous('$z=3;$z')
$a

# This example runs a command that takes longer than the allowed timeout value
# and measures how long it runs so that you can see the impact
Measure-Command {$psISE.PowerShellTabs[1].InvokeSynchronous('sleep 10', $false, 5000)}
```

## <a name="properties"></a>Właściwości

### <a name="addonsmenu"></a>AddOnsMenu

Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.

Właściwość tylko do odczytu, która menu dodatki dla karty programu PowerShell.

```powershell
# Clear the Add-ons menu if one exists.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
# Create an AddOns menu with an accessor.
# Note the use of "_"  as opposed to the "&" for mapping to the fast key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
# Show the Add-ons menu on the current PowerShell tab.
$psISE.CurrentPowerShellTab.AddOnsMenu
```

### <a name="caninvoke"></a>CanInvoke

Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.

Właściwość logiczna przeznaczony tylko do odczytu, która zwraca **$true** wartość, gdy skrypt może być wywoływana ze [Invoke (skrypt)](#invoke-script-) metody.

```powershell
# CanInvoke will be false if the PowerShell
# tab is running a script that takes a while, and you
# check its properties from another PowerShell tab. It is
# always false if checked on the current PowerShell tab.
# Manually create a second PowerShell tab before running this script.
# Return to the first tab and type
$secondTab = $psISE.PowerShellTabs[1]
$secondTab.CanInvoke
$secondTab.Invoke({sleep 20})
$secondTab.CanInvoke
```

### <a name="consolepane"></a>Consolepane

Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.  W programie Windows PowerShell ISE 2.0 to nosiła nazwę **CommandPane**.

Właściwość tylko do odczytu, która w okienku konsoli [edytora](The-ISEEditor-Object.md) obiektu.

```powershell
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane
```

### <a name="displayname"></a>DisplayName

Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.

Właściwości odczytu / zapisu, która pobiera lub ustawia tekst, który jest wyświetlany na karcie programu PowerShell. Domyślnie karty są nazywane "PowerShell #", gdzie # reprezentuje liczbę.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="expandedscript"></a>ExpandedScript

Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.

Odczytu i zapisu właściwość typu Boolean, która określa, czy w okienku skryptu jest rozwinięta czy ukryty.

```powershell
# Toggle the expanded script property to see its effect.
$psISE.CurrentPowerShellTab.ExpandedScript = !$psISE.CurrentPowerShellTab.ExpandedScript
```

### <a name="files"></a>Pliki

Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.

Właściwość tylko do odczytu, która pobiera [zbiór plików skryptów](The-ISEFileCollection-Object.md) , które są otwarte w kartę programu PowerShell.

```powershell
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb"
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a>Dane wyjściowe

Ta funkcja znajduje się w programie Windows PowerShell ISE 2.0, ale został usunięty lub zmieniono jego nazwę w nowszych wersjach środowiska ISE.  W nowszych wersjach programu Windows PowerShell ISE, można użyć **ConsolePane** obiektu do tych samych celów.

Właściwość tylko do odczytu, która pobiera okienko danych wyjściowych bieżącego [edytora](The-ISEEditor-Object.md).

```powershell
# Clears the text in the Output pane.
$psISE.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a>Monit

Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.

Właściwość tylko do odczytu, która umożliwia pobieranie bieżącego tekst monitu. Uwaga: **monitu** funkcja może być zastąpiona przez użytkownika "™ profil. Jeśli wynik jest inne niż prosty ciąg znaków, następnie właściwość ta zwraca nothing.

```powershell
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a>ShowCommands

Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.

Właściwość odczytu / zapisu, która wskazuje, jeśli jest aktualnie wyświetlany w okienku poleceń.

```powershell
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $true
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands = $true}
```

### <a name="statustext"></a>StatusText

Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.

Właściwość tylko do odczytu, która pobiera **PowerShellTab** tekst statusu.

```powershell
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a>HorizontalAddOnToolsPaneOpened

Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.

Właściwość tylko do odczytu, która wskazuje, czy poziomy okienko narzędzi dodatków jest obecnie otwarty.

```powershell
# Gets the current state of the horizontal Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a>VerticalAddOnToolsPaneOpened

Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.

Właściwość tylko do odczytu, która wskazuje, czy pionowy okienko narzędzi dodatków jest obecnie otwarty.

```powershell
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands = $true
# Gets the current state of the vertical Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a>Zobacz też

- [Obiekt PowerShellTabCollection](The-PowerShellTabCollection-Object.md)
- [Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarchia modeli obiektów środowiska ISE](The-ISE-Object-Model-Hierarchy.md)