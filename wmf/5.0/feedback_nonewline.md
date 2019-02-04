---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: e01f6ceea361f5a9b3de645346d0652986b6267d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685914"
---
# <a name="nonewline-parameter"></a>Parametr NoNewLine
**Out-file**, **Dodaj zawartość**, i **zestaw zawartości** powstał nowy **— NoNewline** przełącznika, który po prostu pomija znakiem nowego wiersza po danych wyjściowych.
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt -NoNewline

PS C:\>; "a single " | Add-Content -Path Example.txt -NoNewline

PS C:\> "sentence." | Add-Content -Path Example.txt -NoNewline

PS C:\> Get-Content .\Example.txt

This is a single sentence.
```
Bez **— NoNewline** określony, poszczególne fragmenty powinna znajdować się w osobnym wierszu:
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt

PS C:\> "a single " | Add-Content -Path Example.txt

PS C:\> "sentence." | Add-Content -Path Example.txt

PS C:\> Get-Content .\Example.txt

This is

a single

sentence.
```
