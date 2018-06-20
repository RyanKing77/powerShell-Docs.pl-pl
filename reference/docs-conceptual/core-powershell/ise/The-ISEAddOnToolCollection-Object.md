---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISEAddOnToolCollection
ms.assetid: 634eab89-0845-4016-974b-361b09bb8f7b
ms.openlocfilehash: ff4f19d1a85a592f2f4f09c62caa0971751bdff7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953059"
---
# <a name="the-iseaddontoolcollection-object"></a>Obiekt ISEAddOnToolCollection

**ISEAddOnToolCollection** obiektu jest kolekcją **ISEAddOnTool** obiektów. Na przykład **$psISE.CurrentPowerShellTab.VerticalAddOnTools** obiektu.

## <a name="methods"></a>Metody

### <a name="add-name-controltype-isvisible-"></a>Dodaj\( nazwę, ControlType, \[IsVisible\] \)

Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

Dodaje nowe narzędzie dodatek do kolekcji. Zwraca narzędzie nowo dodanego dodatek. Przed uruchomieniem tego polecenia, należy zainstalować narzędzie dodatku na komputerze lokalnym i załadować zestawu.

**Nazwa** — ciąg Określa nazwę wyświetlaną narzędzia dodatek, który jest dodawany do programu Windows PowerShell ISE.

**ControlType** — typ Określa formant, który zostanie dodany.

**\[IsVisible\]**  -opcjonalna wartość logiczna Jeśli równa **$true**, narzędzie dodatek jest od razu widoczne w okienku skojarzone narzędzia.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a>Usuń\( elementu \)

Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

Usuwa dodatek określonego narzędzia z kolekcji.

**Element** -Microsoft.PowerShell.Host.ISE.ISEAddOnTool określa obiekt, który ma zostać usunięty z programu Windows PowerShell ISE.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a>SetSelectedPowerShellTab\( psTab \)

Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

Karta wybiera programu PowerShell, który **psTab** określa parametr.

**psTab** -PowerShell Microsoft.PowerShell.Host.ISE.PowerShellTab kartę, aby wybrać.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a>Usuń\( psTab \)

Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

Karta usuwa programu PowerShell, który **psTab** określa parametr.

**psTab** — karta Microsoft.PowerShell.Host.ISE.PowerShellTab programu PowerShell do usunięcia.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a>Zobacz też

- [Obiekt PowerShellTab](The-PowerShellTab-Object.md)
- [Cel programu Windows PowerShell ISE skryptów modelu obiektów](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarchia modeli obiektów środowiska ISE](The-ISE-Object-Model-Hierarchy.md)