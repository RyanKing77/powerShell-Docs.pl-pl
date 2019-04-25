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
# <a name="call-base-class-method"></a>Wywoływanie metody klasy bazowej

Można zastąpić istniejących metod w podklasach. Aby to zrobić, należy zadeklarować metody przy użyciu tej samej nazwie i sygnaturze:

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

Aby wywołać metody klasy bazowej z implementacji zastąpione, rzutowanie do klasy bazowej ($[baseClass] to) na wywołania:

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

Wszystkie metody programu PowerShell są wirtualne. Można ukryć .NET metod niewirtualnych w podklasę przy użyciu tej samej składni, podobnie jak w przypadku zastąpienia: tylko do deklarowania metod o tej samej nazwie i sygnaturze.

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
