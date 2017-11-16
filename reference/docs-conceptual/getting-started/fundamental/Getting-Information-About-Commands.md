---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: "Pobieranie informacji na temat poleceń"
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: 98e449110860ea81939d6ec0b7b1a8534a2da2aa
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2017
---
# <a name="getting-information-about-commands"></a>Pobieranie informacji na temat poleceń
Programu Windows PowerShell **Get-Command** polecenie cmdlet pobiera wszystkie polecenia, które są dostępne w bieżącej sesji. Podczas wpisywania **Get-Command** w wierszu polecenia programu Windows PowerShell zostanie wyświetlone dane wyjściowe podobne do następującego:

```
PS> Get-Command
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
Cmdlet          Add-Member                      Add-Member [-MemberType] <PS...
...
```

Wygląda to output wiele takich jak dane wyjściowe pomocy Cmd.exe: tabelarycznym podsumowanie poleceń wewnętrznego. W fragmencie z **Get-Command** polecenia wyjście przedstawionych powyżej, co zostało przedstawione ma CommandType Cmdlet. Polecenia cmdlet jest typem wewnętrzne polecenia programu Windows PowerShell — typ, który odpowiada około do **dir** i **cd** polecenia Cmd.exe oraz built-ins w powłoki systemu UNIX, takich jak BASH.

W danych wyjściowych **Get-Command** polecenia, wszystkie definicje kończyć wielokropek (...), aby wskazać, że programu PowerShell nie można wyświetlić całej zawartości w dostępnego miejsca. Gdy środowiska Windows PowerShell umożliwia wyświetlenie danych wyjściowych, formatuje dane wyjściowe jako tekst, a następnie rozmieszcza aby prawidłowo mieści się w oknie danych. Zostanie omawianiu to później w sekcji na elementy formatujące.

**Get-Command** polecenie cmdlet ma **składni** parametr, który pobiera składnia każde polecenie cmdlet. Aby wyświetlić składnię polecenia cmdlet Get-Help, użyj następującego polecenia:

**Get-Help Get-Command-składni**

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

### <a name="displaying-available-command-types"></a>Wyświetlanie typów
**Get-Command** polecenia nie ma każdego polecenia, które jest dostępne w programie Windows PowerShell. Zamiast tego **Get-Command** polecenie wyświetla tylko polecenia cmdlet w bieżącej sesji. Program Windows PowerShell faktycznie obsługuje kilka typów poleceń. Aliasy, funkcji i skryptów są również poleceń programu Windows PowerShell, chociaż nie opisano szczegółowo w podręczniku użytkownika programu Windows PowerShell. Zewnętrzne pliki wykonywalne lub ma typ obsługi plików, również są sklasyfikowane jako polecenia.

Aby uzyskać wszystkie polecenia w sesji, wpisz:

```
Get-Command *
```

Ponieważ ta lista zawiera zewnętrzne pliki w ścieżce wyszukiwania, może on zawierać tysięcy elementów. Warto więcej przyjrzeć się ograniczonego zestawu poleceń.

Aby uzyskać natywnych poleceń innych typów, użyj **CommandType** parametr **Get-Command** polecenia cmdlet.

> [!NOTE]
> Gwiazdka (\*) służy do dopasowanie w argumentach polecenia środowiska Windows PowerShell z symbolami wieloznacznymi. \* Oznacza "odpowiada jednej lub więcej znaków". Możesz wpisać **Get-Command\&#42;** znaleźć wszystkie polecenia, które zaczynają się od litery "". W przeciwieństwie do dopasowania w Cmd.exe symboli wieloznacznych symbol wieloznaczny środowiska Windows PowerShell również zgodna okres.

Aby uzyskać aliasy poleceń, które są przypisane pseudonimy poleceń, wpisz:

```
Get-Command -CommandType Alias
```

Aby uzyskać te funkcje w bieżącej sesji, wpisz:

```
Get-Command -CommandType Function
```

Aby wyświetlić skryptów w ścieżce wyszukiwania programu Windows PowerShell, wpisz:

```
Get-Command -CommandType Script
```

