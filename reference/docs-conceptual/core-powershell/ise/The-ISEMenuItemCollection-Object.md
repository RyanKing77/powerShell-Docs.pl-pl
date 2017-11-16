---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISEMenuItemCollection
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 7ce9132021d4d5e755503e0adb355beb388a625a
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2017
---
# <a name="the-isemenuitemcollection-object"></a>Obiekt ISEMenuItemCollection
  **ISEMenuItemCollection** obiektu jest kolekcją **ISEMenuItem** obiektów. To wystąpienie klasy Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection. Na przykład **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** obiekt, który służy do dostosowywania **dodatek** menu w Windows PowerShell® Integrated Scripting Environment (ISE).

## <a name="method"></a>Metoda

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>Dodaj\(DisplayName, akcja System.Management.Automation.ScriptBlock System.Windows.Input.KeyGesture skrótu ciągu\)
  Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy. 

 Dodaje element menu do kolekcji.

 **Nazwa wyświetlana** nazwę wyświetlaną menu ma zostać dodana.

 **Akcja** **System.Management.Automation.ScriptBlock** obiekt, który określa akcję, która jest skojarzona z tym elementem menu.

 **Skrót** skrót klawiaturowy dla akcji.

 **Zwraca** ISEMenuItem obiektu, który został dodany.

```
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
```

### <a name="clear"></a>Wyczyść\(\)
  Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy. 

 Usuwa wszystkie podmenu z elementu menu.

```
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

```

## <a name="see-also"></a>Zobacz też
- [Obiekt ISEMenuItem](The-ISEMenuItem-Object.md) 
- [Windows PowerShell ISE skryptów modelu obiektów](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Dotyczące modelu obiektów programu Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [Hierarchia modelu obiektów ISE](The-ISE-Object-Model-Hierarchy.md)

  
