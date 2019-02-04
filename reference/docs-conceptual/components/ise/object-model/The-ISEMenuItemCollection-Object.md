---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISEMenuItemCollection
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 7e5030416df394aaa9e9d3f63978e204a7faabf1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688644"
---
# <a name="the-isemenuitemcollection-object"></a>Obiekt ISEMenuItemCollection

**ISEMenuItemCollection** obiektu jest kolekcją **ISEMenuItem** obiektów. Jest wystąpieniem klasy Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection. Na przykład **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** obiekt, który jest używany do dostosowywania **dodatek** menu w Windows PowerShell® zintegrowane Scripting Environment (ISE).

## <a name="method"></a>Metoda

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>Dodaj\(DisplayName, akcja System.Management.Automation.ScriptBlock System.Windows.Input.KeyGesture skrótu ciągu \)

Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.

Dodaje element menu do kolekcji.

**DisplayName** nazwę wyświetlaną w menu, które mają zostać dodane.

**Akcja** **System.Management.Automation.ScriptBlock** obiekt, który określa akcję, która jest skojarzona z tego elementu menu.

**Skrót** skrótu klawiaturowego dla akcji.

**Zwraca** obiekt ISEMenuItem, który właśnie został dodany.

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a>Usuń zaznaczenie\(\)

Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.

Usuwa wszystkie podmenu z elementu menu.

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a>Zobacz też

- [Obiekt ISEMenuItem](The-ISEMenuItem-Object.md)
- [Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarchia modeli obiektów środowiska ISE](The-ISE-Object-Model-Hierarchy.md)