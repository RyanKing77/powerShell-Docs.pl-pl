---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 424e0b7a4d62fc35e5040a7e425950e887021d7e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683779"
---
# <a name="call-base-class-constructor"></a>Wywoływanie konstruktora klasy bazowej

Aby wywołać konstruktora klasy bazowej z podklasy, należy użyć słowa kluczowego **podstawowy**:

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

Jeśli klasa bazowa ma Konstruktor domyślny (nie parametrów), można pominąć wywołanie jawny Konstruktor:

```powershell
class C : B
{
    C([int]$c) {}
}
```
