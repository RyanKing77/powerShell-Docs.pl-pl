---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 4b593e9a1eca43ee7ad85fc921ae3c1d62722db9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687860"
---
# <a name="declare-implemented-interface"></a>Deklarowanie zaimplementowanego interfejsu

Możesz zadeklarować implementowane interfejsy po typy podstawowe lub od razu po dwukropek (:), jeśli bez określonego typu podstawowego. Oddziel nazwy wszystkich typów za pomocą przecinków. Jest bardzo podobne do C# składni.

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
