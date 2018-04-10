---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISEMenuItemCollection
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 7e5030416df394aaa9e9d3f63978e204a7faabf1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="the-isemenuitemcollection-object"></a>Obiekt ISEMenuItemCollection

**ISEMenuItemCollection** obiektu jest kolekcją **ISEMenuItem** obiektów. To wystąpienie klasy Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection. Na przykład **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** obiekt, który służy do dostosowywania **dodatek** menu w Windows PowerShell® Integrated Scripting Environment (ISE).

## <a name="method"></a>Metoda

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Dodaje element menu do kolekcji.

**Nazwa wyświetlana** nazwę wyświetlaną menu ma zostać dodana.

**Akcja** **System.Management.Automation.ScriptBlock** obiekt, który określa akcję, która jest skojarzona z tym elementem menu.

**Skrót** skrót klawiaturowy dla akcji.

**Zwraca** ISEMenuItem obiektu, który został dodany.

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a>Wyczyść\(\)

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Usuwa wszystkie podmenu z elementu menu.

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a>Zobacz też

- [Obiekt ISEMenuItem](The-ISEMenuItem-Object.md)
- [Cel programu Windows PowerShell ISE skryptów modelu obiektów](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarchia modeli obiektów środowiska ISE](The-ISE-Object-Model-Hierarchy.md)