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
# <a name="declare-implemented-interface"></a><span data-ttu-id="c0316-102">Deklarowanie zaimplementowany interfejs</span><span class="sxs-lookup"><span data-stu-id="c0316-102">Declare Implemented Interface</span></span>

<span data-ttu-id="c0316-103">Zaimplementowane interfejsy mogą zadeklarować po typów podstawowych lub od razu po dwukropkiem (:), jeśli nie ma podstawowego typu określony.</span><span class="sxs-lookup"><span data-stu-id="c0316-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="c0316-104">Wszystkie nazwy typu oddzielić przecinkami.</span><span class="sxs-lookup"><span data-stu-id="c0316-104">Separate all type names by using commas.</span></span> <span data-ttu-id="c0316-105">Jest bardzo podobny do składni języka C#.</span><span class="sxs-lookup"><span data-stu-id="c0316-105">It’s very similar to C# syntax.</span></span>

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

