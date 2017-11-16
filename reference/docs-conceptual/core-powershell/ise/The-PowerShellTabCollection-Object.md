---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: Obiekt PowerShellTabCollection
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: dcdc16ae126453b6ade64917ac4950cc05e5f8ad
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2017
---
# <a name="the-powershelltabcollection-object"></a>Obiekt PowerShellTabCollection
  **PowerShellTab** obiektu kolekcji jest kolekcją **PowerShellTab** obiektów. Każdy **PowerShellTab** obiektu działa jako oddzielne środowiska. To wystąpienie klasy Microsoft.PowerShell.Host.ISE.PowerShellTabs. Na przykład **$psISE.PowerShellTabs** obiektu.

## <a name="methods"></a>Metody

### <a name="add"></a>Dodaj\(\)
  Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy. 

 Dodaje nową kartę programu PowerShell do kolekcji. Zwraca nowo dodanego kartę.

```
$NewTab=$psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab"
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a>Usuń\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)
  Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy. 

 Usuwa określoną przez kartę **psTab** parametru.

 **psTab** kartę programu PowerShell do usunięcia.

```

$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a>SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)
  Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy. 

 Wybiera karcie programu PowerShell, która jest określona przez **psTab** parametr, aby stał się aktywne kartę programu PowerShell.

 **psTab** kartę programu PowerShell, aby wybrać.

```
# Save the current tab in a variable and rename it
$OldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName="Old Tab"
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab" 
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab=$oldtab
```

## <a name="see-also"></a>Zobacz też
- [Obiekt PowerShellTab](The-PowerShellTab-Object.md) 
- [Windows PowerShell ISE skryptów modelu obiektów](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Dotyczące modelu obiektów programu Windows PowerShell ISE](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [Hierarchia modelu obiektów ISE](../ise/The-ISE-Object-Model-Hierarchy.md)

  
