---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: e01f6ceea361f5a9b3de645346d0652986b6267d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057234"
---
# <a name="nonewline-parameter"></a><span data-ttu-id="0bd79-102">Parametr NoNewLine</span><span class="sxs-lookup"><span data-stu-id="0bd79-102">NoNewLine parameter</span></span>
<span data-ttu-id="0bd79-103">**Out-file**, **Dodaj zawartość**, i **zestaw zawartości** powstał nowy **— NoNewline** przełącznika, który po prostu pomija znakiem nowego wiersza po danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="0bd79-103">**Out-File**, **Add-Content**, and **Set-Content** now have a new **–NoNewline** switch which simply omits a new line after the output.</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt -NoNewline

PS C:\>; "a single " | Add-Content -Path Example.txt -NoNewline

PS C:\> "sentence." | Add-Content -Path Example.txt -NoNewline

PS C:\> Get-Content .\Example.txt

This is a single sentence.
```
<span data-ttu-id="0bd79-104">Bez **— NoNewline** określony, poszczególne fragmenty powinna znajdować się w osobnym wierszu:</span><span class="sxs-lookup"><span data-stu-id="0bd79-104">Without **–NoNewline** specified, each fragment would be on a separate line:</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt

PS C:\> "a single " | Add-Content -Path Example.txt

PS C:\> "sentence." | Add-Content -Path Example.txt

PS C:\> Get-Content .\Example.txt

This is

a single

sentence.
```
