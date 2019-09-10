---
ms.date: 09/09/2019
keywords: PowerShell, polecenie cmdlet
title: Dodatek 1 Aliasy zgodności
ms.openlocfilehash: 2351fdf23711fe1417f7e3fc3cca5b642d5a59fc
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848165"
---
# <a name="appendix-1---compatibility-aliases"></a>Dodatek 1 — aliasy zgodności

Program PowerShell ma kilka aliasów umożliwiających użytkownikom **systemów UNIX** i **cmd. exe** używanie znanych poleceń.
W poniższej tabeli przedstawiono polecenia i powiązane z nimi polecenie cmdlet programu PowerShell oraz Alias programu PowerShell:

|cmd. exe — polecenie|Polecenie systemu UNIX|Polecenie cmdlet programu PowerShell|Alias programu PowerShell|
|---------------|----------------|--------------|------------|
|**ze**|**Wyczyść**|`Clear-Host`funkcyjn|`cls`|
|**kopiowane**|**CP**|`Copy-Item`|`cpi`|
|**katalogów**|**ls**|`Get-ChildItem`|`gci`|
|**type**|**Cat**|`Get-Content`|`gc`|
|**Przenieś**|**MV**|`Move-Item`|`mi`|
|**md**|**mkdir**|`New-Item`|`ni`|
|**pushd**|**pushd**|`Push-Location`|`pushd`|
|**popd**|**popd**|`Pop-Location`|`popd`|
|**del**, **Wymaż**, **Rd**, **rmdir**|**RM**|`Remove-Item`|`ri`|
|**inicjacj**|**MV**|`Rename-Item`|`rni`|
|**CD**, **chdir**|**cd**|`Set-Location`|`sl`|

Aby znaleźć aliasy programu PowerShell, użyj polecenia cmdlet [Get-alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) . Aby wyświetlić Aliasy poleceń cmdlet, należy użyć parametru **definicji** i określić nazwę polecenia cmdlet.
Aby znaleźć nazwę polecenia cmdlet aliasu, użyj parametru **name** i określ alias.

```powershell
Get-Alias -Definition Get-ChildItem
```

```Output
CommandType     Name
-----------     ----
Alias           dir -> Get-ChildItem
Alias           gci -> Get-ChildItem
Alias           ls -> Get-ChildItem
```

```powershell
Get-Alias -Name gci
```

```Output
CommandType     Name
-----------     ----
Alias           gci -> Get-ChildItem
```
