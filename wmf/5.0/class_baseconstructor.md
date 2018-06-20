---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9486fdbaeca66c83551564c76ce47482f77c36b9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225610"
---
# <a name="call-base-class-constructor"></a>Wywoływanie konstruktora klasy bazowej

Aby wywołać konstruktora klasy podstawowej z podklasy, użyj słowa kluczowego **podstawowej**:

```powershell
class A
{
    [int]$a

    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

[B]::new().a # return 103
```

Jeśli klasa podstawowa ma konstruktora domyślnego (nie parametrów), można pominąć wywołanie jawny Konstruktor:

```powershell
class C : B
{
    C([int]$c) {}
}
```
