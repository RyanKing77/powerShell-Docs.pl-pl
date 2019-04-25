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
# <a name="the-powershelltab-object"></a><span data-ttu-id="76ee9-103">Obiekt PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="76ee9-103">The PowerShellTab Object</span></span>

<span data-ttu-id="76ee9-104">**PowerShellTab** obiekt reprezentuje środowiska uruchomieniowego programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="76ee9-104">The **PowerShellTab** object represents a Windows PowerShell runtime environment.</span></span>

## <a name="methods"></a><span data-ttu-id="76ee9-105">Metody</span><span class="sxs-lookup"><span data-stu-id="76ee9-105">Methods</span></span>

### <a name="invoke-script-"></a><span data-ttu-id="76ee9-106">Wywoływanie\( skryptu \)</span><span class="sxs-lookup"><span data-stu-id="76ee9-106">Invoke\( Script \)</span></span>

<span data-ttu-id="76ee9-107">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="76ee9-107">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="76ee9-108">Uruchamia skrypt danej karcie programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="76ee9-108">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="76ee9-109">Ta metoda działa tylko na innych kartach programu PowerShell nie kartę programu PowerShell, w którym jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="76ee9-109">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="76ee9-110">Nie zwraca żadnych obiekt lub wartość.</span><span class="sxs-lookup"><span data-stu-id="76ee9-110">It does not return any object or value.</span></span> <span data-ttu-id="76ee9-111">Jeżeli kod modyfikuje dowolnej zmiennej, te zmiany zostaną zachowane na karcie, względem którego wywołano polecenie.</span><span class="sxs-lookup"><span data-stu-id="76ee9-111">If the code modifies any variable, then those changes persist on the tab against which the command was invoked.</span></span>

<span data-ttu-id="76ee9-112">**Skrypt** -System.Management.Automation.ScriptBlock lub ciągu bloku skryptu do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="76ee9-112">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

```powershell
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psISE.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a><span data-ttu-id="76ee9-113">InvokeSynchronous\( skryptu \[useNewScope\], millisecondsTimeout \)</span><span class="sxs-lookup"><span data-stu-id="76ee9-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span></span>

<span data-ttu-id="76ee9-114">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="76ee9-114">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="76ee9-115">Uruchamia skrypt danej karcie programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="76ee9-115">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="76ee9-116">Ta metoda działa tylko na innych kartach programu PowerShell nie kartę programu PowerShell, w którym jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="76ee9-116">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="76ee9-117">Blok skryptu zostanie uruchomione, a każdą wartość, która jest zwracana w skrypcie jest zwracana do środowisko uruchomieniowe, z którego wywołano polecenie.</span><span class="sxs-lookup"><span data-stu-id="76ee9-117">The script block is run and any value that is returned from the script is returned to the run environment from which you invoked the command.</span></span> <span data-ttu-id="76ee9-118">Jeśli wykonanie tego polecenia może być dłuższy niż **millesecondsTimeout** określa wartość, a następnie polecenie kończy się niepowodzeniem z powodu wyjątku: "Operacji został przekroczony."</span><span class="sxs-lookup"><span data-stu-id="76ee9-118">If the command takes longer to run than the **millesecondsTimeout** value specifies, then the command fails with an exception: "The operation has timed out."</span></span>

<span data-ttu-id="76ee9-119">**Skrypt** -System.Management.Automation.ScriptBlock lub ciągu bloku skryptu do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="76ee9-119">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

<span data-ttu-id="76ee9-120">**\[useNewScope\]**  -opcjonalna wartość logiczna, wartość domyślna to **$true** Jeśli równa **$true**, a następnie jest tworzony nowy zakres, w którym należy uruchomić polecenie.</span><span class="sxs-lookup"><span data-stu-id="76ee9-120">**\[useNewScope\]** -  Optional Boolean that defaults to **$true** If set to **$true**, then a new scope is created within which to run the command.</span></span> <span data-ttu-id="76ee9-121">Środowisko uruchomieniowe karty programu PowerShell, który jest określony za pomocą polecenia nie powoduje modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="76ee9-121">It does not modify the runtime environment of the PowerShell tab that is specified by the command.</span></span>

<span data-ttu-id="76ee9-122">**\[millisecondsTimeout\]**  -opcjonalną liczbą całkowitą, która domyślnie **500**.</span><span class="sxs-lookup"><span data-stu-id="76ee9-122">**\[millisecondsTimeout\]** -  Optional integer that defaults to **500**.</span></span>
<span data-ttu-id="76ee9-123">Jeśli polecenie zakończy się w określonym czasie, a następnie polecenie spowoduje wygenerowanie **TimeoutException** z komunikatem "Operacja przekroczyła limit."</span><span class="sxs-lookup"><span data-stu-id="76ee9-123">If the command does not finish within the specified time, then the command generates a **TimeoutException** with the message "The operation has timed out."</span></span>

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

## <a name="properties"></a><span data-ttu-id="76ee9-124">Właściwości</span><span class="sxs-lookup"><span data-stu-id="76ee9-124">Properties</span></span>

### <a name="addonsmenu"></a><span data-ttu-id="76ee9-125">AddOnsMenu</span><span class="sxs-lookup"><span data-stu-id="76ee9-125">AddOnsMenu</span></span>

<span data-ttu-id="76ee9-126">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="76ee9-126">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="76ee9-127">Właściwość tylko do odczytu, która menu dodatki dla karty programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="76ee9-127">The read-only property that gets the Add-ons menu for the PowerShell tab.</span></span>

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

### <a name="caninvoke"></a><span data-ttu-id="76ee9-128">CanInvoke</span><span class="sxs-lookup"><span data-stu-id="76ee9-128">CanInvoke</span></span>

<span data-ttu-id="76ee9-129">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="76ee9-129">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="76ee9-130">Właściwość logiczna przeznaczony tylko do odczytu, która zwraca **$true** wartość, gdy skrypt może być wywoływana ze [Invoke (skrypt)](#invoke-script-) metody.</span><span class="sxs-lookup"><span data-stu-id="76ee9-130">The read-only Boolean property that returns a **$true** value if a script can be invoked with the [Invoke( Script )](#invoke-script-) method.</span></span>

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

### <a name="consolepane"></a><span data-ttu-id="76ee9-131">Consolepane</span><span class="sxs-lookup"><span data-stu-id="76ee9-131">Consolepane</span></span>

<span data-ttu-id="76ee9-132">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="76ee9-132">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>  <span data-ttu-id="76ee9-133">W programie Windows PowerShell ISE 2.0 to nosiła nazwę **CommandPane**.</span><span class="sxs-lookup"><span data-stu-id="76ee9-133">In Windows PowerShell ISE 2.0 this was named **CommandPane**.</span></span>

<span data-ttu-id="76ee9-134">Właściwość tylko do odczytu, która w okienku konsoli [edytora](The-ISEEditor-Object.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="76ee9-134">The read-only property that gets the Console pane [editor](The-ISEEditor-Object.md) object.</span></span>

```powershell
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane
```

### <a name="displayname"></a><span data-ttu-id="76ee9-135">DisplayName</span><span class="sxs-lookup"><span data-stu-id="76ee9-135">DisplayName</span></span>

<span data-ttu-id="76ee9-136">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="76ee9-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="76ee9-137">Właściwości odczytu / zapisu, która pobiera lub ustawia tekst, który jest wyświetlany na karcie programu PowerShell. Domyślnie karty są nazywane "PowerShell #", gdzie # reprezentuje liczbę.</span><span class="sxs-lookup"><span data-stu-id="76ee9-137">The read-write property that gets or sets the text that is displayed on the PowerShell tab. By default, tabs are named "PowerShell #", where the # represents a number.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="expandedscript"></a><span data-ttu-id="76ee9-138">ExpandedScript</span><span class="sxs-lookup"><span data-stu-id="76ee9-138">ExpandedScript</span></span>

<span data-ttu-id="76ee9-139">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="76ee9-139">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="76ee9-140">Odczytu i zapisu właściwość typu Boolean, która określa, czy w okienku skryptu jest rozwinięta czy ukryty.</span><span class="sxs-lookup"><span data-stu-id="76ee9-140">The read-write Boolean property that determines whether the Script pane is expanded or hidden.</span></span>

```powershell
# Toggle the expanded script property to see its effect.
$psISE.CurrentPowerShellTab.ExpandedScript = !$psISE.CurrentPowerShellTab.ExpandedScript
```

### <a name="files"></a><span data-ttu-id="76ee9-141">Pliki</span><span class="sxs-lookup"><span data-stu-id="76ee9-141">Files</span></span>

<span data-ttu-id="76ee9-142">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="76ee9-142">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="76ee9-143">Właściwość tylko do odczytu, która pobiera [zbiór plików skryptów](The-ISEFileCollection-Object.md) , które są otwarte w kartę programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="76ee9-143">The read-only property that gets the [collection of script files](The-ISEFileCollection-Object.md) that are open in the PowerShell tab.</span></span>

```powershell
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb"
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a><span data-ttu-id="76ee9-144">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="76ee9-144">Output</span></span>

<span data-ttu-id="76ee9-145">Ta funkcja znajduje się w programie Windows PowerShell ISE 2.0, ale został usunięty lub zmieniono jego nazwę w nowszych wersjach środowiska ISE.</span><span class="sxs-lookup"><span data-stu-id="76ee9-145">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="76ee9-146">W nowszych wersjach programu Windows PowerShell ISE, można użyć **ConsolePane** obiektu do tych samych celów.</span><span class="sxs-lookup"><span data-stu-id="76ee9-146">In later versions of Windows PowerShell ISE, you can use the **ConsolePane** object for the same purposes.</span></span>

<span data-ttu-id="76ee9-147">Właściwość tylko do odczytu, która pobiera okienko danych wyjściowych bieżącego [edytora](The-ISEEditor-Object.md).</span><span class="sxs-lookup"><span data-stu-id="76ee9-147">The read-only property that gets the Output pane of the current [editor](The-ISEEditor-Object.md).</span></span>

```powershell
# Clears the text in the Output pane.
$psISE.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a><span data-ttu-id="76ee9-148">Monit</span><span class="sxs-lookup"><span data-stu-id="76ee9-148">Prompt</span></span>

<span data-ttu-id="76ee9-149">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="76ee9-149">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="76ee9-150">Właściwość tylko do odczytu, która umożliwia pobieranie bieżącego tekst monitu.</span><span class="sxs-lookup"><span data-stu-id="76ee9-150">The read-only property that gets the current prompt text.</span></span> <span data-ttu-id="76ee9-151">Uwaga: **monitu** funkcja może być zastąpiona przez użytkownika "™ profil.</span><span class="sxs-lookup"><span data-stu-id="76ee9-151">Note: the **Prompt** function can be overridden by the user'™s profile.</span></span> <span data-ttu-id="76ee9-152">Jeśli wynik jest inne niż prosty ciąg znaków, następnie właściwość ta zwraca nothing.</span><span class="sxs-lookup"><span data-stu-id="76ee9-152">If the result is other than a simple string, then this property returns nothing.</span></span>

```powershell
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a><span data-ttu-id="76ee9-153">ShowCommands</span><span class="sxs-lookup"><span data-stu-id="76ee9-153">ShowCommands</span></span>

<span data-ttu-id="76ee9-154">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="76ee9-154">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="76ee9-155">Właściwość odczytu / zapisu, która wskazuje, jeśli jest aktualnie wyświetlany w okienku poleceń.</span><span class="sxs-lookup"><span data-stu-id="76ee9-155">The read-write property that indicates if the Commands pane is currently displayed.</span></span>

```powershell
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $true
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands = $true}
```

### <a name="statustext"></a><span data-ttu-id="76ee9-156">StatusText</span><span class="sxs-lookup"><span data-stu-id="76ee9-156">StatusText</span></span>

<span data-ttu-id="76ee9-157">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="76ee9-157">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="76ee9-158">Właściwość tylko do odczytu, która pobiera **PowerShellTab** tekst statusu.</span><span class="sxs-lookup"><span data-stu-id="76ee9-158">The read-only property that gets the **PowerShellTab** status text.</span></span>

```powershell
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a><span data-ttu-id="76ee9-159">HorizontalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="76ee9-159">HorizontalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="76ee9-160">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="76ee9-160">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="76ee9-161">Właściwość tylko do odczytu, która wskazuje, czy poziomy okienko narzędzi dodatków jest obecnie otwarty.</span><span class="sxs-lookup"><span data-stu-id="76ee9-161">The read-only property that indicates whether the horizontal Add-Ons tool pane is currently open.</span></span>

```powershell
# Gets the current state of the horizontal Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a><span data-ttu-id="76ee9-162">VerticalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="76ee9-162">VerticalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="76ee9-163">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="76ee9-163">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="76ee9-164">Właściwość tylko do odczytu, która wskazuje, czy pionowy okienko narzędzi dodatków jest obecnie otwarty.</span><span class="sxs-lookup"><span data-stu-id="76ee9-164">The read-only property that indicates whether the vertical Add-Ons tool pane is currently open.</span></span>

```powershell
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands = $true
# Gets the current state of the vertical Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a><span data-ttu-id="76ee9-165">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="76ee9-165">See Also</span></span>

- [<span data-ttu-id="76ee9-166">Obiekt PowerShellTabCollection</span><span class="sxs-lookup"><span data-stu-id="76ee9-166">The PowerShellTabCollection Object</span></span>](The-PowerShellTabCollection-Object.md)
- [<span data-ttu-id="76ee9-167">Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="76ee9-167">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="76ee9-168">Hierarchia modeli obiektów środowiska ISE</span><span class="sxs-lookup"><span data-stu-id="76ee9-168">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)