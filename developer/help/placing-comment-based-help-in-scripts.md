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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850148"
---
# <a name="placing-comment-based-help-in-scripts"></a>Umieszczanie pomocy opartej na komentarzach w skryptach

W tym temacie opisano, gdzie umieścić oparta na komentarzach pomoc dotyczącą skryptu, aby `Get-Help` polecenia cmdlet kojarzy tematu pomocy oparta na komentarzach za pomocą skryptów i nie wszystkie funkcje, które mogą być w skrypcie.

## <a name="where-to-place-comment-based-help-for-a-script"></a>Gdzie umieścić oparta na komentarzach pomoc dotyczącą skryptu

- Na początku pliku skryptu. Pomoc skrypt może być poprzedzony w skrypcie tylko komentarze i puste wiersze.

- Na końcu pliku skryptu.

  Pierwszy element na treść skryptu (po pomoc) w przypadku deklaracji funkcji, musi istnieć co najmniej dwa puste wiersze między końcem skryptu pomocy i deklaracji funkcji. W przeciwnym razie pomocy jest interpretowany jako pomoc w przypadku funkcji nie pomoc dotyczącą skryptu.

## <a name="examples-of-help-placement-in-a-script"></a>Przykłady pomocy umieszczania w skrypcie

 W poniższych przykładach pokazano każdej z opcji umieszczania oparta na komentarzach pomoc dotyczącą skryptu.

### <a name="help-at-the-beginning-of-a-script"></a>Pomoc na początku skryptu

 Poniższy przykład pokazuje, oparta na komentarzach na początku skryptu.

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a>Pomoc na końcu skryptu

 Poniższy przykład pokazuje, na podstawie komentarz na końcu skryptu.

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```