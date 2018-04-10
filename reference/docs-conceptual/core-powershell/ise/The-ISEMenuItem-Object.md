---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISEMenuItem
ms.assetid: a16660bd-0aee-46fd-ac17-3f022165d089
ms.openlocfilehash: 556f88117c07100b1734c8ffd8956dce6efe6fb1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="the-isemenuitem-object"></a>Obiekt ISEMenuItem

**ISEMenuItem** obiekt jest wystąpieniem klasy Microsoft.PowerShell.Host.ISE.ISEMenuItem. Wszystkie obiekty menu na **dodatki** menu są wystąpieniami klasy **Microsoft.PowerShell.Host.ISE.ISEMenuItem** klasy.

## <a name="properties"></a>Właściwości

### <a name="displayname"></a>DisplayName

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Właściwość tylko do odczytu, który pobiera nazwę wyświetlaną elementu menu.

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a>Akcja

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Właściwość tylko do odczytu, która pobiera blok skryptu. Po kliknięciu elementu menu, wywołuje akcję.

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a>Skrót

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Właściwość tylko do odczytu, która pobiera systemu Windows wprowadź skrót klawiaturowy do elementu menu.

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a>Podmenu

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Właściwość tylko do odczytu, która pobiera [listy podmenu](The-ISEMenuItemCollection-Object.md) elementu menu.

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a>Przykład skryptów

Aby lepiej zrozumieć użycie menu dodatków i jego właściwości skryptowe, zapoznaj się z artykułem poniższy przykład skryptów.

```powershell
# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of “_”  as opposed to the “&” for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu - a parent and a child submenu item.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
```

## <a name="see-also"></a>Zobacz też

- [Obiekt ISEMenuItemCollection](The-ISEMenuItemCollection-Object.md)
- [Cel programu Windows PowerShell ISE skryptów modelu obiektów](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarchia modeli obiektów środowiska ISE](The-ISE-Object-Model-Hierarchy.md)