---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 1f165afbcd8fe8dc5f72cc7ea557d21ce2884e91
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="nonewline-parameter"></a><span data-ttu-id="3269e-102">Parametr NoNewLine</span><span class="sxs-lookup"><span data-stu-id="3269e-102">NoNewLine parameter</span></span>
<span data-ttu-id="3269e-103">**Out-file**, **Dodaj zawartość**, i **zestawu zawartości** teraz ma nowego **— NoNewline** przełącznika, która po prostu pomija znakiem nowego wiersza po danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="3269e-103">**Out-File**, **Add-Content**, and **Set-Content** now have a new **–NoNewline** switch which simply omits a new line after the output.</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt -NoNewline

PS C:\>; "a single " | Add-Content -Path Example.txt -NoNewline

PS C:\> "sentence." | Add-Content -Path Example.txt -NoNewline

PS C:\> Get-Content .\Example.txt

This is a single sentence.
```
<span data-ttu-id="3269e-104">Bez **— NoNewline** określony, każdy fragment będzie w osobnym wierszu:</span><span class="sxs-lookup"><span data-stu-id="3269e-104">Without **–NoNewline** specified, each fragment would be on a separate line:</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt

PS C:\> "a single " | Add-Content -Path Example.txt

PS C:\> "sentence." | Add-Content -Path Example.txt

PS C:\> Get-Content .\Example.txt

This is

a single

sentence.
```