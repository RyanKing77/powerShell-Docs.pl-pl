---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 302a347b0f4c9c322f7701e8d6a721f9ffba9b59
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="convert-string"></a>Convert-String
**Konwertuj ciąg** udostępnia funkcje "należy zastąpić magic". Podaj przed i po nich przykłady sposobu tekstu, aby zobaczyć, i **przekonwertować ciągu** automatycznego formatowania tekstu. Oto pokaz - biorąc osoby na imię i nazwisko i zastąpienie go z nazwisk, przecinek, pierwszy początkowej nazwisk i kropką. Spróbuj go za pomocą regex i zobacz, jak długo trwa użytkownik.

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```