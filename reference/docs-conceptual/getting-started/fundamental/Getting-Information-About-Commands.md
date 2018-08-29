---
ms.date: 08/27/2018
keywords: polecenia cmdlet programu PowerShell
title: Uzyskiwanie informacji dotyczących poleceń
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: f4238927f10b4204cd3e23f0b0453011f54cb04a
ms.sourcegitcommit: 59727f71dc204785a1bcdedc02716d8340a77aeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2018
ms.locfileid: "43134014"
---
# <a name="getting-information-about-commands"></a>Uzyskiwanie informacji dotyczących poleceń

PowerShell `Get-Command` Wyświetla polecenia, które są dostępne w bieżącej sesji.
Po uruchomieniu `Get-Command` polecenia cmdlet, zauważysz coś, co jest podobne do następujących danych wyjściowych:

```output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Cmdlet          Add-Computer            3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-Content             3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-History             3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-JobTrigger          1.1.0.0    PSScheduledJob
Cmdlet          Add-LocalGroupMember    1.0.0.0    Microsoft.PowerShell.LocalAccounts
Cmdlet          Add-Member              3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Add-PSSnapin            3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-Type                3.1.0.0    Microsoft.PowerShell.Utility
...
```

To danych wyjściowych wygląda bardzo podobnie jak dane wyjściowe Cmd.exe Help: tabelarycznych podsumowanie poleceń wewnętrznego. W wycinku z `Get-Command` polecenia powyżej każdego polecenia wyświetlane w danych wyjściowych ma CommandType Cmdlet. Polecenie cmdlet jest typ wewnętrzne polecenia programu PowerShell. Ten typ odpowiada mniej więcej poleceń, takich jak `dir` i `cd` Cmd.exe lub wbudowanego polecenia systemu Unix powłoki, takie jak bash.

`Get-Command` Polecenie cmdlet ma **składni** parametr, który zwraca składni każdego polecenia cmdlet. Poniższy przykład pokazuje, jak uzyskać składnię `Get-Help` polecenia cmdlet:

```powershell
Get-Command Get-Help -Syntax
```

```output
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

## <a name="displaying-available-command-by-type"></a>Wyświetlanie dostępnych poleceń według typu

`Get-Command` Polecenie wyświetla listę tylko polecenia cmdlet w bieżącej sesji. Program PowerShell faktycznie obsługuje kilka typów poleceń:

- Aliasy
- Funkcje
- Skrypty

Zewnętrzne pliki wykonywalne lub pliki, których program obsługi typów plików, również są klasyfikowane jako polecenia.

Aby uzyskać wszystkie polecenia w sesji, wpisz:

```powershell
Get-Command *
```

Ta lista zawiera poleceń zewnętrznych w ścieżce wyszukiwania, dzięki czemu może zawierać tysięcy elementów.
Jest bardziej użyteczny przyjrzeć się ograniczonego zestawu poleceń.

> [!NOTE]
> Gwiazdka (\*) służy do dopasowanie w argumentach polecenia programu PowerShell z symbolami wieloznacznymi. \* Oznacza, że "odpowiada jednej lub więcej znaków". Możesz wpisać `Get-Command a*` można znaleźć wszystkie polecenia, które zaczynają się od litery "". W odróżnieniu od dopasowanie w Cmd.exe z symbolami wieloznacznymi programu PowerShell symboli wieloznacznych również dopasowanie kropki.

Użyj **CommandType** parametru `Get-Command` można pobrać natywnych poleceń innych typów.
.

Aby uzyskać aliasów poleceń, które są przypisane pseudonimy poleceń, wpisz:

```powershell
Get-Command -CommandType Alias
```

Aby uzyskać funkcje w bieżącej sesji, wpisz:

```powershell
Get-Command -CommandType Function
```

Aby wyświetlić skrypty w ścieżce wyszukiwania programu PowerShell, wpisz:

```powershell
Get-Command -CommandType Script
```