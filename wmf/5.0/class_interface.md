---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 116f79a95126d0a1c579a95ec99eb5d8b75cc1e0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225491"
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="d20d8-102">Deklarowanie zaimplementowanego interfejsu</span><span class="sxs-lookup"><span data-stu-id="d20d8-102">Declare Implemented Interface</span></span>

<span data-ttu-id="d20d8-103">Zaimplementowane interfejsy mogą zadeklarować po typów podstawowych lub od razu po dwukropkiem (:), jeśli nie ma podstawowego typu określony.</span><span class="sxs-lookup"><span data-stu-id="d20d8-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="d20d8-104">Wszystkie nazwy typu oddzielić przecinkami.</span><span class="sxs-lookup"><span data-stu-id="d20d8-104">Separate all type names by using commas.</span></span> <span data-ttu-id="d20d8-105">Jest bardzo podobny do składni języka C#.</span><span class="sxs-lookup"><span data-stu-id="d20d8-105">It’s very similar to C# syntax.</span></span>

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
