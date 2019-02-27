---
title: Składnia Pomoc oparta na komentarzach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846494"
---
# <a name="syntax-of-comment-based-help"></a><span data-ttu-id="2cd10-102">Składnia pomocy opartej na komentarzach</span><span class="sxs-lookup"><span data-stu-id="2cd10-102">Syntax of Comment-Based Help</span></span>

<span data-ttu-id="2cd10-103">W tej sekcji opisano składnię Pomoc oparta na komentarz.</span><span class="sxs-lookup"><span data-stu-id="2cd10-103">This section describes the syntax of comment-based help.</span></span>

## <a name="syntax-diagram"></a><span data-ttu-id="2cd10-104">Diagram składni</span><span class="sxs-lookup"><span data-stu-id="2cd10-104">Syntax Diagram</span></span>

 <span data-ttu-id="2cd10-105">Składnia pomocy w sieci komentarza jest następujący:</span><span class="sxs-lookup"><span data-stu-id="2cd10-105">The syntax for comment-based Help is as follows:</span></span>

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a><span data-ttu-id="2cd10-106">Opis składni</span><span class="sxs-lookup"><span data-stu-id="2cd10-106">Syntax Description</span></span>

 <span data-ttu-id="2cd10-107">Pomoc oparta na komentarzach są zapisywane jako serię komentarzy.</span><span class="sxs-lookup"><span data-stu-id="2cd10-107">Comment-based Help is written as a series of comments.</span></span> <span data-ttu-id="2cd10-108">Możesz wpisać symbol komentarza (#), przed każdym wierszem komentarze lub można użyć "\<#" i "#>" symbole, aby utworzyć blok komentarza.</span><span class="sxs-lookup"><span data-stu-id="2cd10-108">You can type a comment symbol (#) before each line of comments, or you can use the "\<#" and "#>" symbols to create a comment block.</span></span> <span data-ttu-id="2cd10-109">Wszystkie wiersze w blok komentarza są interpretowane jako komentarze.</span><span class="sxs-lookup"><span data-stu-id="2cd10-109">All the lines within the comment block are interpreted as comments.</span></span>

 <span data-ttu-id="2cd10-110">Każda sekcja oparta na komentarzach pomocy jest definiowany przez słowo kluczowe, a każde słowo kluczowe jest poprzedzony przez pojedynczego znaku kropki (.).</span><span class="sxs-lookup"><span data-stu-id="2cd10-110">Each section of comment-based Help is defined by a keyword and each keyword is preceded by a dot (.).</span></span> <span data-ttu-id="2cd10-111">Słowa kluczowe może występować w dowolnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="2cd10-111">The keywords can appear in any order.</span></span> <span data-ttu-id="2cd10-112">Nazwy — słowo kluczowe nie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="2cd10-112">The keyword names are not case-sensitive.</span></span>

 <span data-ttu-id="2cd10-113">Blok komentarza musi zawierać co najmniej jedno słowo kluczowe pomocy.</span><span class="sxs-lookup"><span data-stu-id="2cd10-113">A comment block must contain at least one help keyword.</span></span> <span data-ttu-id="2cd10-114">Niektóre słów kluczowych, takich jak na przykład może znajdować się wiele razy w tym samym bloku komentarza.</span><span class="sxs-lookup"><span data-stu-id="2cd10-114">Some of the keywords, such as EXAMPLE, can appear many times in the same comment block.</span></span> <span data-ttu-id="2cd10-115">Zawartość pomocy na każde słowo kluczowe zaczyna się od wiersza po słowie kluczowym i może obejmować wiele wierszy.</span><span class="sxs-lookup"><span data-stu-id="2cd10-115">The Help content for each keyword begins on the line after the keyword and can span multiple lines.</span></span>

 <span data-ttu-id="2cd10-116">Wszystkie wiersze w temacie pomocy oparta na komentarzach muszą być ciągłe.</span><span class="sxs-lookup"><span data-stu-id="2cd10-116">All of the lines in a comment-based Help topic must be contiguous.</span></span> <span data-ttu-id="2cd10-117">Jeśli tematu pomocy oparta na komentarzach komentarz, który nie jest częścią tematu pomocy, musi istnieć co najmniej jeden pusty wiersz między ostatni wiersz komentarza-Help a początkiem Pomoc oparta na komentarz.</span><span class="sxs-lookup"><span data-stu-id="2cd10-117">If a comment-based Help topic follows a comment that is not part of the Help topic, there must be at least one blank line between the last non-Help comment line and the beginning of the comment-based Help.</span></span>

 <span data-ttu-id="2cd10-118">Na przykład zawiera następujące oparta na komentarzach tematu Pomocy. Opis słowa kluczowego i jego wartość, która znajduje się opis funkcji lub skrypcie.</span><span class="sxs-lookup"><span data-stu-id="2cd10-118">For example, the following comment-based help topic contains the .Description keyword and its value, which is a description of a function or script.</span></span>

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```