---
title: Wprowadzenie do pomocy w sieci komentarz w skryptach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: d199c53a748ac57bb2a5f998b5056e39d3e80c0d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083233"
---
# <a name="placing-comment-based-help-in-scripts"></a><span data-ttu-id="d3709-102">Umieszczanie pomocy opartej na komentarzach w skryptach</span><span class="sxs-lookup"><span data-stu-id="d3709-102">Placing Comment-Based Help in Scripts</span></span>

<span data-ttu-id="d3709-103">W tym temacie opisano, gdzie umieścić oparta na komentarzach pomoc dotyczącą skryptu, aby `Get-Help` polecenia cmdlet kojarzy tematu pomocy oparta na komentarzach za pomocą skryptów i nie wszystkie funkcje, które mogą być w skrypcie.</span><span class="sxs-lookup"><span data-stu-id="d3709-103">This topic explains where to place comment-based help for a script so that the `Get-Help` cmdlet associates the comment-based help topic with scripts and not with any functions that might be in the script.</span></span>

## <a name="where-to-place-comment-based-help-for-a-script"></a><span data-ttu-id="d3709-104">Gdzie umieścić oparta na komentarzach pomoc dotyczącą skryptu</span><span class="sxs-lookup"><span data-stu-id="d3709-104">Where to Place Comment-Based Help for a Script</span></span>

- <span data-ttu-id="d3709-105">Na początku pliku skryptu.</span><span class="sxs-lookup"><span data-stu-id="d3709-105">At the beginning of the script file.</span></span> <span data-ttu-id="d3709-106">Pomoc skrypt może być poprzedzony w skrypcie tylko komentarze i puste wiersze.</span><span class="sxs-lookup"><span data-stu-id="d3709-106">Script Help can be preceded in the script only by comments and blank lines.</span></span>

- <span data-ttu-id="d3709-107">Na końcu pliku skryptu.</span><span class="sxs-lookup"><span data-stu-id="d3709-107">At the end of the script file.</span></span>

  <span data-ttu-id="d3709-108">Pierwszy element na treść skryptu (po pomoc) w przypadku deklaracji funkcji, musi istnieć co najmniej dwa puste wiersze między końcem skryptu pomocy i deklaracji funkcji.</span><span class="sxs-lookup"><span data-stu-id="d3709-108">If the first item in the script body (after the Help) is a function declaration, there must be at least two blank lines between the end of the script Help and the function declaration.</span></span> <span data-ttu-id="d3709-109">W przeciwnym razie pomocy jest interpretowany jako pomoc w przypadku funkcji nie pomoc dotyczącą skryptu.</span><span class="sxs-lookup"><span data-stu-id="d3709-109">Otherwise, the Help is interpreted as being Help for the function, not Help for the script.</span></span>

## <a name="examples-of-help-placement-in-a-script"></a><span data-ttu-id="d3709-110">Przykłady pomocy umieszczania w skrypcie</span><span class="sxs-lookup"><span data-stu-id="d3709-110">Examples of Help Placement in a Script</span></span>

 <span data-ttu-id="d3709-111">W poniższych przykładach pokazano każdej z opcji umieszczania oparta na komentarzach pomoc dotyczącą skryptu.</span><span class="sxs-lookup"><span data-stu-id="d3709-111">The following examples show each of the placement options for comment-based help for a script.</span></span>

### <a name="help-at-the-beginning-of-a-script"></a><span data-ttu-id="d3709-112">Pomoc na początku skryptu</span><span class="sxs-lookup"><span data-stu-id="d3709-112">Help at the Beginning of a Script</span></span>

 <span data-ttu-id="d3709-113">Poniższy przykład pokazuje, oparta na komentarzach na początku skryptu.</span><span class="sxs-lookup"><span data-stu-id="d3709-113">The following example shows comment-based at the beginning of a script.</span></span>

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a><span data-ttu-id="d3709-114">Pomoc na końcu skryptu</span><span class="sxs-lookup"><span data-stu-id="d3709-114">Help at the End of a Script</span></span>

 <span data-ttu-id="d3709-115">Poniższy przykład pokazuje, na podstawie komentarz na końcu skryptu.</span><span class="sxs-lookup"><span data-stu-id="d3709-115">The following example shows comment-based at the end of a script.</span></span>

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```