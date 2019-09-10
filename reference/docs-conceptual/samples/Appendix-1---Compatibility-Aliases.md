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
# <a name="appendix-1---compatibility-aliases"></a><span data-ttu-id="3a369-103">Dodatek 1 — aliasy zgodności</span><span class="sxs-lookup"><span data-stu-id="3a369-103">Appendix 1 - Compatibility Aliases</span></span>

<span data-ttu-id="3a369-104">Program PowerShell ma kilka aliasów umożliwiających użytkownikom **systemów UNIX** i **cmd. exe** używanie znanych poleceń.</span><span class="sxs-lookup"><span data-stu-id="3a369-104">PowerShell has several aliases that allow **UNIX** and **cmd.exe** users to use familiar commands.</span></span>
<span data-ttu-id="3a369-105">W poniższej tabeli przedstawiono polecenia i powiązane z nimi polecenie cmdlet programu PowerShell oraz Alias programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="3a369-105">The commands and their related PowerShell cmdlet and PowerShell alias are shown in the following table:</span></span>

|<span data-ttu-id="3a369-106">cmd. exe — polecenie</span><span class="sxs-lookup"><span data-stu-id="3a369-106">cmd.exe command</span></span>|<span data-ttu-id="3a369-107">Polecenie systemu UNIX</span><span class="sxs-lookup"><span data-stu-id="3a369-107">UNIX command</span></span>|<span data-ttu-id="3a369-108">Polecenie cmdlet programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="3a369-108">PowerShell cmdlet</span></span>|<span data-ttu-id="3a369-109">Alias programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="3a369-109">PowerShell alias</span></span>|
|---------------|----------------|--------------|------------|
|<span data-ttu-id="3a369-110">**ze**</span><span class="sxs-lookup"><span data-stu-id="3a369-110">**cls**</span></span>|<span data-ttu-id="3a369-111">**Wyczyść**</span><span class="sxs-lookup"><span data-stu-id="3a369-111">**clear**</span></span>|<span data-ttu-id="3a369-112">`Clear-Host`funkcyjn</span><span class="sxs-lookup"><span data-stu-id="3a369-112">`Clear-Host` (function)</span></span>|`cls`|
|<span data-ttu-id="3a369-113">**kopiowane**</span><span class="sxs-lookup"><span data-stu-id="3a369-113">**copy**</span></span>|<span data-ttu-id="3a369-114">**CP**</span><span class="sxs-lookup"><span data-stu-id="3a369-114">**cp**</span></span>|`Copy-Item`|`cpi`|
|<span data-ttu-id="3a369-115">**katalogów**</span><span class="sxs-lookup"><span data-stu-id="3a369-115">**dir**</span></span>|<span data-ttu-id="3a369-116">**ls**</span><span class="sxs-lookup"><span data-stu-id="3a369-116">**ls**</span></span>|`Get-ChildItem`|`gci`|
|<span data-ttu-id="3a369-117">**type**</span><span class="sxs-lookup"><span data-stu-id="3a369-117">**type**</span></span>|<span data-ttu-id="3a369-118">**Cat**</span><span class="sxs-lookup"><span data-stu-id="3a369-118">**cat**</span></span>|`Get-Content`|`gc`|
|<span data-ttu-id="3a369-119">**Przenieś**</span><span class="sxs-lookup"><span data-stu-id="3a369-119">**move**</span></span>|<span data-ttu-id="3a369-120">**MV**</span><span class="sxs-lookup"><span data-stu-id="3a369-120">**mv**</span></span>|`Move-Item`|`mi`|
|<span data-ttu-id="3a369-121">**md**</span><span class="sxs-lookup"><span data-stu-id="3a369-121">**md**</span></span>|<span data-ttu-id="3a369-122">**mkdir**</span><span class="sxs-lookup"><span data-stu-id="3a369-122">**mkdir**</span></span>|`New-Item`|`ni`|
|<span data-ttu-id="3a369-123">**pushd**</span><span class="sxs-lookup"><span data-stu-id="3a369-123">**pushd**</span></span>|<span data-ttu-id="3a369-124">**pushd**</span><span class="sxs-lookup"><span data-stu-id="3a369-124">**pushd**</span></span>|`Push-Location`|`pushd`|
|<span data-ttu-id="3a369-125">**popd**</span><span class="sxs-lookup"><span data-stu-id="3a369-125">**popd**</span></span>|<span data-ttu-id="3a369-126">**popd**</span><span class="sxs-lookup"><span data-stu-id="3a369-126">**popd**</span></span>|`Pop-Location`|`popd`|
|<span data-ttu-id="3a369-127">**del**, **Wymaż**, **Rd**, **rmdir**</span><span class="sxs-lookup"><span data-stu-id="3a369-127">**del**, **erase**, **rd**, **rmdir**</span></span>|<span data-ttu-id="3a369-128">**RM**</span><span class="sxs-lookup"><span data-stu-id="3a369-128">**rm**</span></span>|`Remove-Item`|`ri`|
|<span data-ttu-id="3a369-129">**inicjacj**</span><span class="sxs-lookup"><span data-stu-id="3a369-129">**ren**</span></span>|<span data-ttu-id="3a369-130">**MV**</span><span class="sxs-lookup"><span data-stu-id="3a369-130">**mv**</span></span>|`Rename-Item`|`rni`|
|<span data-ttu-id="3a369-131">**CD**, **chdir**</span><span class="sxs-lookup"><span data-stu-id="3a369-131">**cd**, **chdir**</span></span>|<span data-ttu-id="3a369-132">**cd**</span><span class="sxs-lookup"><span data-stu-id="3a369-132">**cd**</span></span>|`Set-Location`|`sl`|

<span data-ttu-id="3a369-133">Aby znaleźć aliasy programu PowerShell, użyj polecenia cmdlet [Get-alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) .</span><span class="sxs-lookup"><span data-stu-id="3a369-133">To find the PowerShell aliases, use the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet.</span></span> <span data-ttu-id="3a369-134">Aby wyświetlić Aliasy poleceń cmdlet, należy użyć parametru **definicji** i określić nazwę polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3a369-134">To display a cmdlet's aliases, use the **Definition** parameter and specify the cmdlet name.</span></span>
<span data-ttu-id="3a369-135">Aby znaleźć nazwę polecenia cmdlet aliasu, użyj parametru **name** i określ alias.</span><span class="sxs-lookup"><span data-stu-id="3a369-135">Or, to find an alias's cmdlet name, use the **Name** parameter and specify the alias.</span></span>

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
