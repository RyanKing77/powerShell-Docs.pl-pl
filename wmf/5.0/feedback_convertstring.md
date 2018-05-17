---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 7730912707bb14e90a9926b387fb3a859d7ca26d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="convert-string"></a>Convert-String
**Konwertuj ciąg** udostępnia funkcje "należy zastąpić magic". Podaj przed i po nich przykłady sposobu tekstu, aby zobaczyć, i **przekonwertować ciągu** automatycznego formatowania tekstu. Oto pokaz - biorąc osoby na imię i nazwisko i zastąpienie go z nazwisk, przecinek, pierwszy początkowej nazwisk i kropką. Spróbuj go za pomocą regex i zobacz, jak długo trwa użytkownik.

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
