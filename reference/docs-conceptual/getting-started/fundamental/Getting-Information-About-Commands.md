---
ms.date: 08/27/2018
keywords: polecenia cmdlet programu PowerShell
title: Uzyskiwanie informacji dotyczących poleceń
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: 7af83e3a0e776d96e580b442430357b4ea063a72
ms.sourcegitcommit: c170a1608d20d3c925d79c35fa208f650d014146
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2018
ms.locfileid: "43353174"
---
# <a name="getting-information-about-commands"></a><span data-ttu-id="06741-103">Uzyskiwanie informacji dotyczących poleceń</span><span class="sxs-lookup"><span data-stu-id="06741-103">Getting information about commands</span></span>

<span data-ttu-id="06741-104">PowerShell `Get-Command` Wyświetla polecenia, które są dostępne w bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="06741-104">The PowerShell `Get-Command` displays commands that are available in your current session.</span></span>
<span data-ttu-id="06741-105">Po uruchomieniu `Get-Command` polecenia cmdlet, zauważysz coś, co jest podobne do następujących danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="06741-105">When you run the `Get-Command` cmdlet, you see something similar to the following output:</span></span>

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

<span data-ttu-id="06741-106">To danych wyjściowych wygląda bardzo podobnie jak dane wyjściowe pomocy **cmd.exe**: tabelarycznych podsumowanie poleceń wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="06741-106">This output looks a lot like the Help output of **cmd.exe**: a tabular summary of internal commands.</span></span> <span data-ttu-id="06741-107">W wycinku z `Get-Command` polecenia powyżej każdego polecenia wyświetlane w danych wyjściowych ma CommandType Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="06741-107">In the excerpt of the `Get-Command` command output shown above, every command shown has a CommandType of Cmdlet.</span></span> <span data-ttu-id="06741-108">Polecenie cmdlet jest typ wewnętrzne polecenia programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="06741-108">A cmdlet is PowerShell's intrinsic command type.</span></span> <span data-ttu-id="06741-109">Ten typ odpowiada mniej więcej poleceń, takich jak `dir` i `cd` w **cmd.exe** lub wbudowanego polecenia systemu Unix powłoki bash.</span><span class="sxs-lookup"><span data-stu-id="06741-109">This type corresponds roughly to commands like `dir` and `cd` in **cmd.exe** or the built-in commands of Unix shells like bash.</span></span>

<span data-ttu-id="06741-110">`Get-Command` Polecenie cmdlet ma **składni** parametr, który zwraca składni każdego polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="06741-110">The `Get-Command` cmdlet has a **Syntax** parameter that returns syntax of each cmdlet.</span></span> <span data-ttu-id="06741-111">Poniższy przykład pokazuje, jak uzyskać składnię `Get-Help` polecenia cmdlet:</span><span class="sxs-lookup"><span data-stu-id="06741-111">The following example shows how to get the syntax of the `Get-Help` cmdlet:</span></span>

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

## <a name="displaying-available-command-by-type"></a><span data-ttu-id="06741-112">Wyświetlanie dostępnych poleceń według typu</span><span class="sxs-lookup"><span data-stu-id="06741-112">Displaying available command by type</span></span>

<span data-ttu-id="06741-113">`Get-Command` Polecenie wyświetla listę tylko polecenia cmdlet w bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="06741-113">The `Get-Command` command lists only the cmdlets in the current session.</span></span> <span data-ttu-id="06741-114">Program PowerShell faktycznie obsługuje kilka typów poleceń:</span><span class="sxs-lookup"><span data-stu-id="06741-114">PowerShell actually supports several other types of commands:</span></span>

- <span data-ttu-id="06741-115">Aliasy</span><span class="sxs-lookup"><span data-stu-id="06741-115">Aliases</span></span>
- <span data-ttu-id="06741-116">Funkcje</span><span class="sxs-lookup"><span data-stu-id="06741-116">Functions</span></span>
- <span data-ttu-id="06741-117">Skrypty</span><span class="sxs-lookup"><span data-stu-id="06741-117">Scripts</span></span>

<span data-ttu-id="06741-118">Zewnętrzne pliki wykonywalne lub pliki, których program obsługi typów plików, również są klasyfikowane jako polecenia.</span><span class="sxs-lookup"><span data-stu-id="06741-118">External executable files, or files that have a registered file type handler, are also classified as commands.</span></span>

<span data-ttu-id="06741-119">Aby uzyskać wszystkie polecenia w sesji, wpisz:</span><span class="sxs-lookup"><span data-stu-id="06741-119">To get all commands in the session, type:</span></span>

```powershell
Get-Command *
```

<span data-ttu-id="06741-120">Ta lista zawiera poleceń zewnętrznych w ścieżce wyszukiwania, dzięki czemu może zawierać tysięcy elementów.</span><span class="sxs-lookup"><span data-stu-id="06741-120">This list includes external commands in your search path so it can contain thousands of items.</span></span>
<span data-ttu-id="06741-121">Jest bardziej użyteczny przyjrzeć się ograniczonego zestawu poleceń.</span><span class="sxs-lookup"><span data-stu-id="06741-121">It is more useful to look at a reduced set of commands.</span></span>

> [!NOTE]
> <span data-ttu-id="06741-122">Gwiazdka (\*) służy do dopasowanie w argumentach polecenia programu PowerShell z symbolami wieloznacznymi.</span><span class="sxs-lookup"><span data-stu-id="06741-122">The asterisk (\*) is used for wildcard matching in PowerShell command arguments.</span></span> <span data-ttu-id="06741-123">\* Oznacza, że "odpowiada jednej lub więcej znaków".</span><span class="sxs-lookup"><span data-stu-id="06741-123">The \* means "match one or more of any characters".</span></span> <span data-ttu-id="06741-124">Możesz wpisać `Get-Command a*` można znaleźć wszystkie polecenia, które zaczynają się od litery "".</span><span class="sxs-lookup"><span data-stu-id="06741-124">You can type `Get-Command a*` to find all commands that begin with the letter "a".</span></span> <span data-ttu-id="06741-125">W odróżnieniu od dopasowanie z symbolami wieloznacznymi w **cmd.exe**, programu PowerShell symbol wieloznaczny będzie również dopasowanie kropki.</span><span class="sxs-lookup"><span data-stu-id="06741-125">Unlike wildcard matching in **cmd.exe**, PowerShell's wildcard will also match a period.</span></span>

<span data-ttu-id="06741-126">Użyj **CommandType** parametru `Get-Command` można pobrać natywnych poleceń innych typów.</span><span class="sxs-lookup"><span data-stu-id="06741-126">Use the **CommandType** parameter of `Get-Command` to get native commands of other types.</span></span>
<span data-ttu-id="06741-127">.</span><span class="sxs-lookup"><span data-stu-id="06741-127">cmdlet.</span></span>

<span data-ttu-id="06741-128">Aby uzyskać aliasów poleceń, które są przypisane pseudonimy poleceń, wpisz:</span><span class="sxs-lookup"><span data-stu-id="06741-128">To get command aliases, which are the assigned nicknames of commands, type:</span></span>

```powershell
Get-Command -CommandType Alias
```

<span data-ttu-id="06741-129">Aby uzyskać funkcje w bieżącej sesji, wpisz:</span><span class="sxs-lookup"><span data-stu-id="06741-129">To get the functions in the current session, type:</span></span>

```powershell
Get-Command -CommandType Function
```

<span data-ttu-id="06741-130">Aby wyświetlić skrypty w ścieżce wyszukiwania programu PowerShell, wpisz:</span><span class="sxs-lookup"><span data-stu-id="06741-130">To display scripts in PowerShell's search path, type:</span></span>

```powershell
Get-Command -CommandType Script
```