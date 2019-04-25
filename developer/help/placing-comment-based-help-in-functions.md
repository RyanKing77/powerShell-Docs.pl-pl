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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083199"
---
# <a name="placing-comment-based-help-in-functions"></a>Umieszczanie pomocy opartej na komentarzach w funkcjach

W tym temacie opisano, gdzie umieścić oparta na komentarzach pomocy dla funkcji, aby `Get-Help` polecenia cmdlet kojarzy tematu pomocy oparta na komentarzach z odpowiedniej funkcji.

## <a name="where-to-place-comment-based-help-for-a-function"></a>Gdzie umieścić oparta na komentarzach pomocy dla funkcji

- Na początku treści funkcji.

- Na końcu treści funkcji.

- Przed `Function` — słowo kluczowe. Gdy funkcja jest w skrypcie lub moduł skryptu, nie może istnieć więcej niż jeden pusty wiersz między ostatni wiersz Pomoc oparta na komentarzach i `Function` — słowo kluczowe. W przeciwnym razie `Get-Help` kojarzy pomocy za pomocą skryptu, a nie funkcji.

## <a name="examples-of-help-placement-in-a-function"></a>Przykłady pomocy umieszczania w funkcji

 W poniższych przykładach pokazano każdą z opcji umieszczania trzy oparta na komentarzach pomocy dla funkcji.

### <a name="help-at-the-beginning-of-a-function-body"></a>Pomoc na początku treści funkcji

 Poniższy przykład pokazuje, oparta na komentarzach na początku treści funkcji.

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

### <a name="help-at-the-end-of-a-function-body"></a>Pomoc na końcu treści funkcji

 Poniższy przykład pokazuje, na podstawie komentarz na końcu treści funkcji.

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

### <a name="help-before-the-function-keyword"></a>Pomoc przed słowa kluczowego Function

 Następujące przykłady przedstawiają oparte na komentarz w wierszu przed słowa kluczowego function.

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```