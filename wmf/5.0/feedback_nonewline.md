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
# <a name="nonewline-parameter"></a><span data-ttu-id="b9ac4-102">Parametr NoNewLine</span><span class="sxs-lookup"><span data-stu-id="b9ac4-102">NoNewLine parameter</span></span>
<span data-ttu-id="b9ac4-103">**Out-file**, **Dodaj zawartość**, i **zestaw zawartości** powstał nowy **— NoNewline** przełącznika, który po prostu pomija znakiem nowego wiersza po danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="b9ac4-103">**Out-File**, **Add-Content**, and **Set-Content** now have a new **–NoNewline** switch which simply omits a new line after the output.</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt -NoNewline

PS C:\>; "a single " | Add-Content -Path Example.txt -NoNewline

PS C:\> "sentence." | Add-Content -Path Example.txt -NoNewline

PS C:\> Get-Content .\Example.txt

This is a single sentence.
```
<span data-ttu-id="b9ac4-104">Bez **— NoNewline** określony, poszczególne fragmenty powinna znajdować się w osobnym wierszu:</span><span class="sxs-lookup"><span data-stu-id="b9ac4-104">Without **–NoNewline** specified, each fragment would be on a separate line:</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt

PS C:\> "a single " | Add-Content -Path Example.txt

PS C:\> "sentence." | Add-Content -Path Example.txt

PS C:\> Get-Content .\Example.txt

This is

a single

sentence.
```
