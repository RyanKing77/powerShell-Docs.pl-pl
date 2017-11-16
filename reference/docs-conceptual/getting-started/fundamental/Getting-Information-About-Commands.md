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
# <a name="getting-information-about-commands"></a><span data-ttu-id="46250-103">Pobieranie informacji na temat poleceń</span><span class="sxs-lookup"><span data-stu-id="46250-103">Getting Information About Commands</span></span>
<span data-ttu-id="46250-104">Programu Windows PowerShell **Get-Command** polecenie cmdlet pobiera wszystkie polecenia, które są dostępne w bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="46250-104">The Windows PowerShell **Get-Command** cmdlet gets all commands that are available in your current session.</span></span> <span data-ttu-id="46250-105">Podczas wpisywania **Get-Command** w wierszu polecenia programu Windows PowerShell zostanie wyświetlone dane wyjściowe podobne do następującego:</span><span class="sxs-lookup"><span data-stu-id="46250-105">When you type **Get-Command** at a Windows PowerShell prompt, you will see output similar to the following:</span></span>

```
PS> Get-Command
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
Cmdlet          Add-Member                      Add-Member [-MemberType] <PS...
...
```

<span data-ttu-id="46250-106">Wygląda to output wiele takich jak dane wyjściowe pomocy Cmd.exe: tabelarycznym podsumowanie poleceń wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="46250-106">This output looks a lot like the Help output of Cmd.exe: a tabular summary of internal commands.</span></span> <span data-ttu-id="46250-107">W fragmencie z **Get-Command** polecenia wyjście przedstawionych powyżej, co zostało przedstawione ma CommandType Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="46250-107">In the excerpt of the **Get-Command** command output shown above, every command shown has a CommandType of Cmdlet.</span></span> <span data-ttu-id="46250-108">Polecenia cmdlet jest typem wewnętrzne polecenia programu Windows PowerShell — typ, który odpowiada około do **dir** i **cd** polecenia Cmd.exe oraz built-ins w powłoki systemu UNIX, takich jak BASH.</span><span class="sxs-lookup"><span data-stu-id="46250-108">A cmdlet is Windows PowerShell's intrinsic command type - a type that corresponds roughly to the **dir** and **cd** commands of Cmd.exe and to built-ins in UNIX shells such as BASH.</span></span>

<span data-ttu-id="46250-109">W danych wyjściowych **Get-Command** polecenia, wszystkie definicje kończyć wielokropek (...), aby wskazać, że programu PowerShell nie można wyświetlić całej zawartości w dostępnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="46250-109">In the output of the **Get-Command** command, all the definitions end with ellipses (...) to indicate that PowerShell cannot display all the content in the available space.</span></span> <span data-ttu-id="46250-110">Gdy środowiska Windows PowerShell umożliwia wyświetlenie danych wyjściowych, formatuje dane wyjściowe jako tekst, a następnie rozmieszcza aby prawidłowo mieści się w oknie danych.</span><span class="sxs-lookup"><span data-stu-id="46250-110">When Windows PowerShell displays output, it formats the output as text and then arranges it to make the data fit cleanly into the window.</span></span> <span data-ttu-id="46250-111">Zostanie omawianiu to później w sekcji na elementy formatujące.</span><span class="sxs-lookup"><span data-stu-id="46250-111">We will talk about this later in the section on formatters.</span></span>

<span data-ttu-id="46250-112">**Get-Command** polecenie cmdlet ma **składni** parametr, który pobiera składnia każde polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="46250-112">The **Get-Command** cmdlet has a **Syntax** parameter that gets the syntax of each cmdlet.</span></span> <span data-ttu-id="46250-113">Aby wyświetlić składnię polecenia cmdlet Get-Help, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="46250-113">To get the syntax of the Get-Help cmdlet, use the following command:</span></span>

<span data-ttu-id="46250-114">**Get-Help Get-Command-składni**</span><span class="sxs-lookup"><span data-stu-id="46250-114">**Get-Command Get-Help -Syntax**</span></span>

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

### <a name="displaying-available-command-types"></a><span data-ttu-id="46250-115">Wyświetlanie typów</span><span class="sxs-lookup"><span data-stu-id="46250-115">Displaying Available Command Types</span></span>
<span data-ttu-id="46250-116">**Get-Command** polecenia nie ma każdego polecenia, które jest dostępne w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="46250-116">The **Get-Command** command does not list every command that is available in Windows PowerShell.</span></span> <span data-ttu-id="46250-117">Zamiast tego **Get-Command** polecenie wyświetla tylko polecenia cmdlet w bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="46250-117">Instead, the **Get-Command** command lists only the cmdlets in the current session.</span></span> <span data-ttu-id="46250-118">Program Windows PowerShell faktycznie obsługuje kilka typów poleceń.</span><span class="sxs-lookup"><span data-stu-id="46250-118">Windows PowerShell actually supports several other types of commands.</span></span> <span data-ttu-id="46250-119">Aliasy, funkcji i skryptów są również poleceń programu Windows PowerShell, chociaż nie opisano szczegółowo w podręczniku użytkownika programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="46250-119">Aliases, functions, and scripts are also Windows PowerShell commands, although they are not discussed in detail in the Windows PowerShell User's Guide.</span></span> <span data-ttu-id="46250-120">Zewnętrzne pliki wykonywalne lub ma typ obsługi plików, również są sklasyfikowane jako polecenia.</span><span class="sxs-lookup"><span data-stu-id="46250-120">External files that are executable, or have a registered file type handler, are also classified as commands.</span></span>

<span data-ttu-id="46250-121">Aby uzyskać wszystkie polecenia w sesji, wpisz:</span><span class="sxs-lookup"><span data-stu-id="46250-121">To get all commands in the session, type:</span></span>

```
Get-Command *
```

<span data-ttu-id="46250-122">Ponieważ ta lista zawiera zewnętrzne pliki w ścieżce wyszukiwania, może on zawierać tysięcy elementów.</span><span class="sxs-lookup"><span data-stu-id="46250-122">Because this list includes external files in your search path, it may contain thousands of items.</span></span> <span data-ttu-id="46250-123">Warto więcej przyjrzeć się ograniczonego zestawu poleceń.</span><span class="sxs-lookup"><span data-stu-id="46250-123">It is more useful to look at a reduced set of commands.</span></span>

<span data-ttu-id="46250-124">Aby uzyskać natywnych poleceń innych typów, użyj **CommandType** parametr **Get-Command** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="46250-124">To get native commands of other types, use the **CommandType** parameter of the **Get-Command** cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="46250-125">Gwiazdka (\*) służy do dopasowanie w argumentach polecenia środowiska Windows PowerShell z symbolami wieloznacznymi.</span><span class="sxs-lookup"><span data-stu-id="46250-125">The asterisk (\*) is used for wildcard matching in Windows PowerShell command arguments.</span></span> <span data-ttu-id="46250-126">\* Oznacza "odpowiada jednej lub więcej znaków".</span><span class="sxs-lookup"><span data-stu-id="46250-126">The \* means "match one or more of any characters".</span></span> <span data-ttu-id="46250-127">Możesz wpisać **Get-Command\&#42;** znaleźć wszystkie polecenia, które zaczynają się od litery "".</span><span class="sxs-lookup"><span data-stu-id="46250-127">You can type **Get-Command a\&#42;** to find all commands that begin with the letter "a".</span></span> <span data-ttu-id="46250-128">W przeciwieństwie do dopasowania w Cmd.exe symboli wieloznacznych symbol wieloznaczny środowiska Windows PowerShell również zgodna okres.</span><span class="sxs-lookup"><span data-stu-id="46250-128">Unlike wildcard matching in Cmd.exe, Windows PowerShell's wildcard will also match a period.</span></span>

<span data-ttu-id="46250-129">Aby uzyskać aliasy poleceń, które są przypisane pseudonimy poleceń, wpisz:</span><span class="sxs-lookup"><span data-stu-id="46250-129">To get command aliases, which are the assigned nicknames of commands, type:</span></span>

```
Get-Command -CommandType Alias
```

<span data-ttu-id="46250-130">Aby uzyskać te funkcje w bieżącej sesji, wpisz:</span><span class="sxs-lookup"><span data-stu-id="46250-130">To get the functions in the current session, type:</span></span>

```
Get-Command -CommandType Function
```

<span data-ttu-id="46250-131">Aby wyświetlić skryptów w ścieżce wyszukiwania programu Windows PowerShell, wpisz:</span><span class="sxs-lookup"><span data-stu-id="46250-131">To display scripts in Windows PowerShell's search path, type:</span></span>

```
Get-Command -CommandType Script
```

