---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób środowiska DSC
ms.openlocfilehash: 2bc1600a9df32538d59efa712569b12fa9e3beee
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048409"
---
# <a name="dsc-environment-resource"></a>Zasób środowiska DSC

> Dotyczy: Program Windows PowerShell 4.0, Windows PowerShell 5.0

__Środowiska__ zasób w Windows PowerShell Desired State Configuration (DSC) zapewnia mechanizm zarządzania systemowe zmienne środowiskowe.

## <a name="syntax"></a>Składnia
``` mof
Environment [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Path = [bool] ]
    [ DependsOn = [string[]] ]
    [ Value = [string] ]
}
```

## <a name="properties"></a>Właściwości

|  Właściwość  |  Opis   |
|---|---|
| Nazwa| Wskazuje nazwę zmiennej środowiskowej, dla którego chcesz zapewnić określonego stanu.|
| Upewnij się| Wskazuje, czy zmienna istnieje. Ustaw tę właściwość na __obecne__ Utwórz zmienną środowiskową, jeśli nie istnieje lub upewnij się, że jego wartość odpowiada, co to jest oferowana w ramach __wartość__ właściwość, jeśli zmienna już istnieje. Ustaw ją na __nieobecne__ można usunąć zmiennej, jeśli taki istnieje.|
| Ścieżka| Definiuje zmienną środowiskową, która jest konfigurowana. Ustaw tę właściwość na __$true__ , gdy zmienna __ścieżki__ zmiennej; w przeciwnym razie ustaw ją na __$false__. Wartość domyślna to __$false__. Jeśli zmienna konfigurowany jest __ścieżki__ podana wartość zmiennej, za pośrednictwem __wartość__ właściwości, które zostaną dołączone do istniejącej wartości.|
| DependsOn | Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest __ResourceName__ a jej typ jest __ResourceType__, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.|
| Wartość| Wartość do przypisania do zmiennej środowiskowej.|

## <a name="example"></a>Przykład

Poniższy przykład zapewnia, że __TestEnvironmentVariable__ jest obecny i ma wartość __WartośćTestowa__. Jeśli nie jest obecny, tworzy go.

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```