---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: Obiekt PowerShellTab
ms.assetid: a9b58556-951b-4f48-b3ae-b351b7564360
ms.openlocfilehash: 15d9a7474e4c2cf2a9ff8edb88802106489cdba1
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2017
---
# <a name="the-powershelltab-object"></a>Obiekt PowerShellTab
  **PowerShellTab** obiekt reprezentuje środowiska uruchomieniowego programu Windows PowerShell.

## <a name="methods"></a>Metody

### <a name="invoke-script-"></a>Wywołanie\( skryptu\)
  Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy. 

 Uruchamia skrypt danej karcie środowiska PowerShell.

> [!NOTE]
> Ta metoda działa tylko na inne karty z programu PowerShell, nie na karcie środowiska PowerShell, z którego zostało uruchomione. Nie zwraca żadnych obiektu lub wartości. Jeśli kod modyfikuje dowolnej zmiennej, a następnie zachować te zmiany na karcie, względem którego wywołano polecenia.

 **Skrypt** -System.Management.Automation.ScriptBlock lub ciągu bloku skryptu do uruchomienia.

```
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psise.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a>InvokeSynchronous\( skryptu, \[useNewScope\], millisecondsTimeout\)
  Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach. 

 Uruchamia skrypt danej karcie środowiska PowerShell.

> [!NOTE]
> Ta metoda działa tylko na inne karty z programu PowerShell, nie na karcie środowiska PowerShell, z którego zostało uruchomione. Blok skryptu zostanie uruchomione, a każdą wartość, która jest zwracana w skrypcie jest zwracana do uruchamiania środowiska, z którego wywołany polecenia. Jeśli polecenie trwa dłużej, niż **millesecondsTimeout** określa wartość, a następnie polecenie kończy się niepowodzeniem z powodu wyjątku: "operacji został przekroczony."

 **Skrypt** -System.Management.Automation.ScriptBlock lub ciągu bloku skryptu do uruchomienia.

 **\[useNewScope\]**  -opcjonalna wartość logiczna który domyślnie **$true** Jeśli ustawioną **$true**, następnie nowego zakresu jest tworzony w ramach którego uruchomienia polecenia. Nie modyfikuje środowisko uruchomieniowe karta programu PowerShell, określonym przez polecenie.

 **\[millisecondsTimeout\]**  — opcjonalnie liczba całkowita, która domyślnie **500**.
Jeśli polecenie nie zakończy się w określonym czasie, a następnie generuje polecenie **TimeoutException** z komunikatem "operacji został przekroczony."

```
# create a new PowerShell tab and then switch back to the first
$PSise.PowerShellTabs.Add()
$psISE.PowerShellTabs.SetSelectedPowerShellTab($psISE.PowerShellTabs[0]) 

# Invoke a simple command on the other tab, in its own scope
$psISE.PowerShellTabs[1].InvokeSynchronous('$x=1',$false)
# You can switch to the other tab and type 'œ$x' to see that the value is saved there.

# This example sets a value in the other tab (in a different scope) 
# and returns it through the pipeline to this tab to store in $a
$a=$psISE.PowerShellTabs[1].InvokeSynchronous('$z=3;$z') 
$a

# This example runs a command that takes longer than the allowed timeout value
# and measures how long it runs so that you can see the impact
measure-command {$psISE.PowerShellTabs[1].InvokeSynchronous("sleep 10",$false,5000)}

```

## <a name="properties"></a>Właściwości

### <a name="addonsmenu"></a>AddOnsMenu
  Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy. 

 Właściwość tylko do odczytu, która pobiera menu dodatków na karcie środowiska PowerShell.

```
# Clear the Add-ons menu if one exists.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
# Create an AddOns menu with an accessor.
# Note the use of "_"  as opposed to the "&" for mapping to the fast key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P") 
# Add a nested menu. 
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("Parent",$null,$null) 
$parentAdded.SubMenus.Add("_Dir",{dir},"Alt+D")
# Show the Add-ons menu on the current PowerShell tab.
$psISE.CurrentPowerShellTab.AddOnsMenu
```

### <a name="caninvoke"></a>Właściwość CanInvoke
  Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy. 

 Właściwości typu Boolean tylko do odczytu, która zwraca **$true** wartość, gdy skrypt może być wywoływana ze [Invoke (skrypt)](#invoke-script-) metody.

```
# CanInvoke will be false if the PowerShell
# tab is running a script that takes a while, and you
# check its properties from another PowerShell tab. It is
# always false if checked on the current PowerShell tab. 
# Manually create a second PowerShell tab before running this script.
# Return to the first tab and type
$secondTab = $psise.PowerShellTabs[1] 
$secondTab.CanInvoke 
$secondTab.Invoke({sleep 20})
$secondTab.CanInvoke

```

### <a name="consolepane"></a>Consolepane
  Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.  W programie Windows PowerShell ISE 2.0 to miał nazwę **CommandPane**.

 Właściwość tylko do odczytu, która w okienku konsoli [edytor](../ise/The-ISEEditor-Object.md) obiektu.

```
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane

```

### <a name="displayname"></a>DisplayName
  Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy. 

 Pobiera lub ustawia tekst, który jest wyświetlany na karcie środowiska PowerShell właściwość do odczytu i zapisu. Domyślnie program o nazwie karty "PowerShell #", gdzie # reprezentuje liczbę.

```
$newTab = $psise.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="Brand New Tab"
```

### <a name="expandedscript"></a>ExpandedScript
  Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy. 

 Odczyt i zapis właściwości typu Boolean, która określa, czy w okienku skryptu jest rozwinięty, czy ukryty.

```
# Toggle the expanded script property to see its effect.
$PSise.CurrentPowerShellTab.ExpandedScript=!$PSise.CurrentPowerShellTab.ExpandedScript

```

### <a name="files"></a>Pliki
  Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy. 

 Właściwość tylko do odczytu, która pobiera [kolekcji plików skryptów](../ise/The-ISEFileCollection-Object.md) otwartych na karcie środowiska PowerShell.

```
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb" 
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a>Dane wyjściowe
  Ta funkcja znajduje się w programie Windows PowerShell ISE 2.0, ale została usunięta lub zmieniona w nowszej wersji programu ISE.  W nowszych wersjach programu Windows PowerShell ISE, można użyć **ConsolePane** obiektu dla tych samych celów.

 Właściwość tylko do odczytu, która w okienku danych wyjściowych bieżącego [edytor](../ise/The-ISEEditor-Object.md).

```
# Clears the text in the Output pane.
$psise.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a>Monit
  Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy. 

 Właściwość tylko do odczytu, która pobiera bieżący tekst monitu. Uwaga: **monitu** funkcja może zostać przesłonięta przez użytkownika "™ s profilu. Jeśli wynik wynosi innego niż prosty ciąg, następnie ta właściwość nic nie zwraca.

```
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a>ShowCommands
  Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach. 

 Właściwość odczytu i zapisu, która wskazuje, czy okienko poleceń jest aktualnie wyświetlany.

```
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $True
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands=$True}
```

### <a name="statustext"></a>StatusText
  Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy. 

 Właściwość tylko do odczytu, która pobiera **PowerShellTab** tekstu stanu.

```
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a>HorizontalAddOnToolsPaneOpened
  Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach. 

 Właściwości tylko do odczytu, która wskazuje, czy poziomy okienko narzędzi dodatków jest obecnie otwarty.

```
# Gets the current state of the horizontal Add-ons tool pane. 
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a>VerticalAddOnToolsPaneOpened
  Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach. 

 Właściwości tylko do odczytu, która wskazuje, czy pionowy okienko narzędzi dodatków jest obecnie otwarty.

```
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands=$True
# Gets the current state of the vertical Add-ons tool pane. 
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a>Zobacz też
- [Obiekt PowerShellTabCollection](The-PowerShellTabCollection-Object.md) 
- [Windows PowerShell ISE skryptów modelu obiektów](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Dotyczące modelu obiektów programu Windows PowerShell ISE](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [Hierarchia modelu obiektów ISE](../ise/The-ISE-Object-Model-Hierarchy.md)

  
