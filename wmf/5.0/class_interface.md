---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 2c007321789ae22b4a2e048d2d64162b065f9a75
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="75f0b-102">Deklarowanie zaimplementowanego interfejsu</span><span class="sxs-lookup"><span data-stu-id="75f0b-102">Declare Implemented Interface</span></span>

<span data-ttu-id="75f0b-103">Zaimplementowane interfejsy mogą zadeklarować po typów podstawowych lub od razu po dwukropkiem (:), jeśli nie ma podstawowego typu określony.</span><span class="sxs-lookup"><span data-stu-id="75f0b-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="75f0b-104">Wszystkie nazwy typu oddzielić przecinkami.</span><span class="sxs-lookup"><span data-stu-id="75f0b-104">Separate all type names by using commas.</span></span> <span data-ttu-id="75f0b-105">Jest bardzo podobny do składni języka C#.</span><span class="sxs-lookup"><span data-stu-id="75f0b-105">It’s very similar to C# syntax.</span></span>

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