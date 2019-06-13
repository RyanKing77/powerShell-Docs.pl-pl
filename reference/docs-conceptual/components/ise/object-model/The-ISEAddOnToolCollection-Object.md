---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISEAddOnToolCollection
ms.openlocfilehash: 28ab9747e573b7a76ee655289b341870b1728bc2
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030625"
---
# <a name="the-iseaddontoolcollection-object"></a>Obiekt ISEAddOnToolCollection

**ISEAddOnToolCollection** obiektu jest kolekcją **ISEAddOnTool** obiektów. Na przykład **$psISE.CurrentPowerShellTab.VerticalAddOnTools** obiektu.

## <a name="methods"></a>Metody

### <a name="add-name-controltype-isvisible-"></a>Dodaj\( nazwę, ControlType, \[IsVisible\] \)

Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.

Dodaje nowe narzędzie dodatek do kolekcji. Zwraca narzędzie nowo dodanych dodatku. Przed uruchomieniem tego polecenia, należy zainstalować narzędzie dodatku na komputerze lokalnym i załadować zestawu.

**Nazwa** — ciąg Określa nazwę wyświetlaną narzędzia dodatek, który zostanie dodany do programu Windows PowerShell ISE.

**ControlType** — typ Określa formant, który zostanie dodany.

**\[IsVisible\]**  -opcjonalna wartość logiczna Jeśli równa **$true**, narzędzie dodatek jest natychmiast widoczne w okienku narzędzi skojarzone.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a>Usuń\( elementu \)

Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.

Usuwa narzędzie określonego dodatku z kolekcji.

**Element** -Microsoft.PowerShell.Host.ISE.ISEAddOnTool określa obiekt, który ma zostać usunięty z programu Windows PowerShell ISE.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a>SetSelectedPowerShellTab\( psTab \)

Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.

Karty programu PowerShell wybiera **psTab** określa parametr.

**psTab** -kartę Microsoft.PowerShell.Host.ISE.PowerShellTab programu PowerShell, aby wybrać.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a>Remove\( psTab \)

Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.

Usuwa programu PowerShell karty **psTab** określa parametr.

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
- [Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarchia modeli obiektów środowiska ISE](The-ISE-Object-Model-Hierarchy.md)
