---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
ms.openlocfilehash: 968e78beb8df77588a08a9ce8732e4abcadde4d0
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2017
---
# <a name="declare-implemented-interface"></a>Deklarowanie zaimplementowany interfejs

Zaimplementowane interfejsy mogą zadeklarować po typów podstawowych lub od razu po dwukropkiem (:), jeśli nie ma podstawowego typu określony. Wszystkie nazwy typu oddzielić przecinkami. Jest bardzo podobny do składni języka C#.

```powershell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

