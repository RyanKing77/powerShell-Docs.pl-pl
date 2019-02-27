---
title: Wprowadzenie do pomocy w sieci komentarz w funkcjach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848174"
---
# <a name="placing-comment-based-help-in-functions"></a><span data-ttu-id="ba74e-102">Umieszczanie pomocy opartej na komentarzach w funkcjach</span><span class="sxs-lookup"><span data-stu-id="ba74e-102">Placing Comment-Based Help in Functions</span></span>

<span data-ttu-id="ba74e-103">W tym temacie opisano, gdzie umieścić oparta na komentarzach pomocy dla funkcji, aby `Get-Help` polecenia cmdlet kojarzy tematu pomocy oparta na komentarzach z odpowiedniej funkcji.</span><span class="sxs-lookup"><span data-stu-id="ba74e-103">This topic explains where to place comment-based help for a function so that the `Get-Help` cmdlet associates the comment-based help topic with the correct function.</span></span>

## <a name="where-to-place-comment-based-help-for-a-function"></a><span data-ttu-id="ba74e-104">Gdzie umieścić oparta na komentarzach pomocy dla funkcji</span><span class="sxs-lookup"><span data-stu-id="ba74e-104">Where to Place Comment-Based Help for a Function</span></span>

- <span data-ttu-id="ba74e-105">Na początku treści funkcji.</span><span class="sxs-lookup"><span data-stu-id="ba74e-105">At the beginning of the function body.</span></span>

- <span data-ttu-id="ba74e-106">Na końcu treści funkcji.</span><span class="sxs-lookup"><span data-stu-id="ba74e-106">At the end of the function body.</span></span>

- <span data-ttu-id="ba74e-107">Przed `Function` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="ba74e-107">Before the `Function` keyword.</span></span> <span data-ttu-id="ba74e-108">Gdy funkcja jest w skrypcie lub moduł skryptu, nie może istnieć więcej niż jeden pusty wiersz między ostatni wiersz Pomoc oparta na komentarzach i `Function` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="ba74e-108">When the function is in a script or script module, there cannot be more than one blank line between the last line of the comment-based help and the `Function` keyword.</span></span> <span data-ttu-id="ba74e-109">W przeciwnym razie `Get-Help` kojarzy pomocy za pomocą skryptu, a nie funkcji.</span><span class="sxs-lookup"><span data-stu-id="ba74e-109">Otherwise, `Get-Help` associates the help with the script, not with the function.</span></span>

## <a name="examples-of-help-placement-in-a-function"></a><span data-ttu-id="ba74e-110">Przykłady pomocy umieszczania w funkcji</span><span class="sxs-lookup"><span data-stu-id="ba74e-110">Examples of Help Placement in a Function</span></span>

 <span data-ttu-id="ba74e-111">W poniższych przykładach pokazano każdą z opcji umieszczania trzy oparta na komentarzach pomocy dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="ba74e-111">The following examples show each of the three placement options for comment-based help for a function.</span></span>

### <a name="help-at-the-beginning-of-a-function-body"></a><span data-ttu-id="ba74e-112">Pomoc na początku treści funkcji</span><span class="sxs-lookup"><span data-stu-id="ba74e-112">Help at the Beginning of a Function Body</span></span>

 <span data-ttu-id="ba74e-113">Poniższy przykład pokazuje, oparta na komentarzach na początku treści funkcji.</span><span class="sxs-lookup"><span data-stu-id="ba74e-113">The following example shows comment-based at the beginning of a function body.</span></span>

```powershell

function MyProcess
{
    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>

    Get-Process powershell
}

```

### <a name="help-at-the-end-of-a-function-body"></a><span data-ttu-id="ba74e-114">Pomoc na końcu treści funkcji</span><span class="sxs-lookup"><span data-stu-id="ba74e-114">Help at the End of a Function Body</span></span>

 <span data-ttu-id="ba74e-115">Poniższy przykład pokazuje, na podstawie komentarz na końcu treści funkcji.</span><span class="sxs-lookup"><span data-stu-id="ba74e-115">The following example shows comment-based at the end of a function body.</span></span>

```powershell

function MyFunction
{
    Get-Process powershell

    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>
}

```

### <a name="help-before-the-function-keyword"></a><span data-ttu-id="ba74e-116">Pomoc przed słowa kluczowego Function</span><span class="sxs-lookup"><span data-stu-id="ba74e-116">Help Before the Function Keyword</span></span>

 <span data-ttu-id="ba74e-117">Następujące przykłady przedstawiają oparte na komentarz w wierszu przed słowa kluczowego function.</span><span class="sxs-lookup"><span data-stu-id="ba74e-117">The following examples shows comment-based on the line before the function keyword.</span></span>

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```