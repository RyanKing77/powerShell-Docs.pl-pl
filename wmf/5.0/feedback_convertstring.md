---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
ms.openlocfilehash: 6caff8c06174a1dcb990ed8e5062ccca5848dbb8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="convert-string"></a><span data-ttu-id="835f9-102">Konwertowanie ciągów</span><span class="sxs-lookup"><span data-stu-id="835f9-102">Convert-String</span></span>
<span data-ttu-id="835f9-103">**Konwertuj ciąg** udostępnia funkcje "należy zastąpić magic".</span><span class="sxs-lookup"><span data-stu-id="835f9-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="835f9-104">Podaj przed i po nich przykłady sposobu tekstu, aby zobaczyć, i **przekonwertować ciągu** automatycznego formatowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="835f9-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="835f9-105">Oto pokaz - biorąc osoby na imię i nazwisko i zastąpienie go z nazwisk, przecinek, pierwszy początkowej nazwisk i kropką.</span><span class="sxs-lookup"><span data-stu-id="835f9-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="835f9-106">Spróbuj go za pomocą regex i zobacz, jak długo trwa użytkownik.</span><span class="sxs-lookup"><span data-stu-id="835f9-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```

