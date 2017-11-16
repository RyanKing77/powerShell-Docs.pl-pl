---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
ms.openlocfilehash: 7817769c3fc060a51c833b7469f7b556b9b40e87
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2017
---
# <a name="call-base-class-method"></a><span data-ttu-id="4409f-102">Wywołanie metody klasy podstawowej</span><span class="sxs-lookup"><span data-stu-id="4409f-102">Call Base Class Method</span></span>

<span data-ttu-id="4409f-103">Można zastąpić istniejących metod w podklasach.</span><span class="sxs-lookup"><span data-stu-id="4409f-103">You can override existing methods in subclasses.</span></span> <span data-ttu-id="4409f-104">Aby to zrobić, należy zadeklarować metody przy użyciu tej samej nazwie i podpisie:</span><span class="sxs-lookup"><span data-stu-id="4409f-104">To do this, declare methods by using the same name and signature:</span></span>

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

<span data-ttu-id="4409f-105">Aby wywołać metod klasy podstawowej z implementacji przesłoniętych, rzutowanie na klasę podstawową ($[baseclass —] to) na wywołania:</span><span class="sxs-lookup"><span data-stu-id="4409f-105">To call base class methods from overridden implementations, cast to the base class ([baseClass]$this) on invocation:</span></span>

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

<span data-ttu-id="4409f-106">Wirtualne są wszystkie metody programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4409f-106">All PowerShell methods are virtual.</span></span> <span data-ttu-id="4409f-107">-Virtual metod .NET w podklasy można ukryć, przy użyciu takiej samej składni jak w przypadku zastąpienia: tylko deklarować metod o tej samej nazwie i podpisie.</span><span class="sxs-lookup"><span data-stu-id="4409f-107">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override: just declare methods with same name and signature.</span></span>

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

