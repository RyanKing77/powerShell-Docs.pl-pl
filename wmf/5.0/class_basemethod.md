---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 0e79127faf3f9bf6fe7d525db5bb946daf3b93e1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058628"
---
# <a name="call-base-class-method"></a><span data-ttu-id="e8627-102">Wywoływanie metody klasy bazowej</span><span class="sxs-lookup"><span data-stu-id="e8627-102">Call Base Class Method</span></span>

<span data-ttu-id="e8627-103">Można zastąpić istniejących metod w podklasach.</span><span class="sxs-lookup"><span data-stu-id="e8627-103">You can override existing methods in subclasses.</span></span> <span data-ttu-id="e8627-104">Aby to zrobić, należy zadeklarować metody przy użyciu tej samej nazwie i sygnaturze:</span><span class="sxs-lookup"><span data-stu-id="e8627-104">To do this, declare methods by using the same name and signature:</span></span>

```powershell
class baseClass
{
    [int]foo() {return 100500}
}

class childClass1 : baseClass
{
    [int]foo() {return 200600}
}

[childClass1]::new().foo() # return 200600
```

<span data-ttu-id="e8627-105">Aby wywołać metody klasy bazowej z implementacji zastąpione, rzutowanie do klasy bazowej ($[baseClass] to) na wywołania:</span><span class="sxs-lookup"><span data-stu-id="e8627-105">To call base class methods from overridden implementations, cast to the base class ([baseClass]$this) on invocation:</span></span>

```powershell
class childClass2 : baseClass
{
    [int]foo()
    {
        return 3 * ([baseClass]$this).foo()
    }
}

[childClass2]::new().foo() # return 301500
```

<span data-ttu-id="e8627-106">Wszystkie metody programu PowerShell są wirtualne.</span><span class="sxs-lookup"><span data-stu-id="e8627-106">All PowerShell methods are virtual.</span></span> <span data-ttu-id="e8627-107">Można ukryć .NET metod niewirtualnych w podklasę przy użyciu tej samej składni, podobnie jak w przypadku zastąpienia: tylko do deklarowania metod o tej samej nazwie i sygnaturze.</span><span class="sxs-lookup"><span data-stu-id="e8627-107">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override: just declare methods with same name and signature.</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{
    # Add is final in system.collections.generic.list
    [void] Add([int]$arg)
    {
        ([system.collections.generic.list[int]]$this).Add($arg * 2)
    }
}

$list = [MyIntList]::new()
$list.Add(100)
$list[0] # return 200
```
