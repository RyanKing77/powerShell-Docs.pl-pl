---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt PowerShellTabCollection
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: d9088b26de35360b8258d3f15924b3010a986d15
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953076"
---
# <a name="the-powershelltabcollection-object"></a>Obiekt PowerShellTabCollection

**PowerShellTab** obiektu kolekcji jest kolekcją **PowerShellTab** obiektów. Każdy **PowerShellTab** obiektu działa jako oddzielne środowiska. To wystąpienie klasy Microsoft.PowerShell.Host.ISE.PowerShellTabs. Na przykład **$psISE.PowerShellTabs** obiektu.

## <a name="methods"></a>Metody

### <a name="add"></a>Dodaj\(\)

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Dodaje nową kartę programu PowerShell do kolekcji. Zwraca nowo dodanego kartę.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a>Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Usuwa określoną przez kartę **psTab** parametru.

**psTab** kartę programu PowerShell do usunięcia.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a>SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Wybiera karcie programu PowerShell, która jest określona przez **psTab** parametr, aby stał się aktywne kartę programu PowerShell.

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
- [Cel programu Windows PowerShell ISE skryptów modelu obiektów](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarchia modeli obiektów środowiska ISE](The-ISE-Object-Model-Hierarchy.md)