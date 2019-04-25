---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 4b593e9a1eca43ee7ad85fc921ae3c1d62722db9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085866"
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="860d7-102">Deklarowanie zaimplementowanego interfejsu</span><span class="sxs-lookup"><span data-stu-id="860d7-102">Declare Implemented Interface</span></span>

<span data-ttu-id="860d7-103">Możesz zadeklarować implementowane interfejsy po typy podstawowe lub od razu po dwukropek (:), jeśli bez określonego typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="860d7-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="860d7-104">Oddziel nazwy wszystkich typów za pomocą przecinków.</span><span class="sxs-lookup"><span data-stu-id="860d7-104">Separate all type names by using commas.</span></span> <span data-ttu-id="860d7-105">Jest bardzo podobne do C# składni.</span><span class="sxs-lookup"><span data-stu-id="860d7-105">It’s very similar to C# syntax.</span></span>

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
