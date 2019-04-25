---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 27541d903748738675917941dc6b60bc9acdc3f4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057795"
---
# <a name="convert-string"></a><span data-ttu-id="4d0f6-102">Convert-String</span><span class="sxs-lookup"><span data-stu-id="4d0f6-102">Convert-String</span></span>
<span data-ttu-id="4d0f6-103">**Konwertuj ciąg** udostępnia funkcję "replace przez Magia".</span><span class="sxs-lookup"><span data-stu-id="4d0f6-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="4d0f6-104">Podaj przed i po przykłady sposobu tekstu, aby zobaczyć, i **przekonwertować ciągu** automatycznego formatowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="4d0f6-105">Oto pokazowa - biorąc czyjeś imię i nazwisko i zastępując nazwisk, przecinek, pierwszy imienia swojego imienia, nazwiska i kropka.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="4d0f6-106">Wypróbuj aparat wyrażeń regularnych i zobacz, jak czas trwania.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
