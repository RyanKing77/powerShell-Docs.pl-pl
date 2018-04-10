---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 3269c8cc871f22488b64fb072dac72698983f360
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
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