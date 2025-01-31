---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt PowerShellTabCollection
ms.openlocfilehash: 5a1318534ddce19c2f5faa0d2013e2b38d8b79e5
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030488"
---
# <a name="the-powershelltabcollection-object"></a>Obiekt PowerShellTabCollection

**PowerShellTab** obiekt kolekcji jest kolekcją **PowerShellTab** obiektów. Każdy **PowerShellTab** obiektu działa jako oddzielne środowiska. Jest wystąpieniem klasy Microsoft.PowerShell.Host.ISE.PowerShellTabs. Na przykład **$psISE.PowerShellTabs** obiektu.

## <a name="methods"></a>Metody

### <a name="add"></a>Dodaj\(\)

Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.

Dodaje nową kartę programu PowerShell do kolekcji. Zwraca nowo dodanych kartę.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a>Usuń\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.

Usuwa kartę, która jest określona przez **psTab** parametru.

**psTab** kartę programu PowerShell do usunięcia.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a>SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.

Wybiera kartę programu PowerShell, który jest określony przez **psTab** parametr, aby utworzyć obecnie aktywną kartę programu PowerShell.

**psTab** kartę programu PowerShell, aby wybrać.

```powershell
# Save the current tab in a variable and rename it
$oldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName = 'Old Tab'
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab = $oldTab
```

## <a name="see-also"></a>Zobacz też

- [Obiekt PowerShellTab](The-PowerShellTab-Object.md)
- [Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarchia modeli obiektów środowiska ISE](The-ISE-Object-Model-Hierarchy.md)
