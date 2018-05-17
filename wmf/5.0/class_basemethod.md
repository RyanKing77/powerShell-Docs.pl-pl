---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: d7aec1a2ba8964e877ddd7406609fe135b1eb462
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="call-base-class-method"></a>Wywoływanie metody klasy bazowej

Można zastąpić istniejących metod w podklasach. Aby to zrobić, należy zadeklarować metody przy użyciu tej samej nazwie i podpisie:

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

Aby wywołać metod klasy podstawowej z implementacji przesłoniętych, rzutowanie na klasę podstawową ($[baseclass —] to) na wywołania:

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

Wirtualne są wszystkie metody programu PowerShell. -Virtual metod .NET w podklasy można ukryć, przy użyciu takiej samej składni jak w przypadku zastąpienia: tylko deklarować metod o tej samej nazwie i podpisie.

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
