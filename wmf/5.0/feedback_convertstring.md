---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 7730912707bb14e90a9926b387fb3a859d7ca26d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="convert-string"></a><span data-ttu-id="59179-102">Convert-String</span><span class="sxs-lookup"><span data-stu-id="59179-102">Convert-String</span></span>
<span data-ttu-id="59179-103">**Konwertuj ciąg** udostępnia funkcje "należy zastąpić magic".</span><span class="sxs-lookup"><span data-stu-id="59179-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="59179-104">Podaj przed i po nich przykłady sposobu tekstu, aby zobaczyć, i **przekonwertować ciągu** automatycznego formatowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="59179-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="59179-105">Oto pokaz - biorąc osoby na imię i nazwisko i zastąpienie go z nazwisk, przecinek, pierwszy początkowej nazwisk i kropką.</span><span class="sxs-lookup"><span data-stu-id="59179-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="59179-106">Spróbuj go za pomocą regex i zobacz, jak długo trwa użytkownik.</span><span class="sxs-lookup"><span data-stu-id="59179-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
