---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 27541d903748738675917941dc6b60bc9acdc3f4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684500"
---
# <a name="convert-string"></a>Convert-String
**Konwertuj ciąg** udostępnia funkcję "replace przez Magia". Podaj przed i po przykłady sposobu tekstu, aby zobaczyć, i **przekonwertować ciągu** automatycznego formatowania tekstu. Oto pokazowa - biorąc czyjeś imię i nazwisko i zastępując nazwisk, przecinek, pierwszy imienia swojego imienia, nazwiska i kropka. Wypróbuj aparat wyrażeń regularnych i zobacz, jak czas trwania.

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
