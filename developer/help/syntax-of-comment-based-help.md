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
# <a name="syntax-of-comment-based-help"></a>Składnia pomocy opartej na komentarzach

W tej sekcji opisano składnię Pomoc oparta na komentarz.

## <a name="syntax-diagram"></a>Diagram składni

 Składnia pomocy w sieci komentarza jest następujący:

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a>Opis składni

 Pomoc oparta na komentarzach są zapisywane jako serię komentarzy. Możesz wpisać symbol komentarza (#), przed każdym wierszem komentarze lub można użyć "\<#" i "#>" symbole, aby utworzyć blok komentarza. Wszystkie wiersze w blok komentarza są interpretowane jako komentarze.

 Każda sekcja oparta na komentarzach pomocy jest definiowany przez słowo kluczowe, a każde słowo kluczowe jest poprzedzony przez pojedynczego znaku kropki (.). Słowa kluczowe może występować w dowolnej kolejności. Nazwy — słowo kluczowe nie jest rozróżniana wielkość liter.

 Blok komentarza musi zawierać co najmniej jedno słowo kluczowe pomocy. Niektóre słów kluczowych, takich jak na przykład może znajdować się wiele razy w tym samym bloku komentarza. Zawartość pomocy na każde słowo kluczowe zaczyna się od wiersza po słowie kluczowym i może obejmować wiele wierszy.

 Wszystkie wiersze w temacie pomocy oparta na komentarzach muszą być ciągłe. Jeśli tematu pomocy oparta na komentarzach komentarz, który nie jest częścią tematu pomocy, musi istnieć co najmniej jeden pusty wiersz między ostatni wiersz komentarza-Help a początkiem Pomoc oparta na komentarz.

 Na przykład zawiera następujące oparta na komentarzach tematu Pomocy. Opis słowa kluczowego i jego wartość, która znajduje się opis funkcji lub skrypcie.

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```