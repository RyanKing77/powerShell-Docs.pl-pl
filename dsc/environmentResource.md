---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: DSC środowiska zasobów
ms.openlocfilehash: 4f024afe2d70c13e19406745ec7fd69821ab229b
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-environment-resource"></a>DSC środowiska zasobów

> Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0

__Środowiska__ zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm zarządzania zmiennych środowiskowych systemu.

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
| Nazwa| Wskazuje nazwę zmiennej środowiskowej, dla którego chcesz zapewnić z określonym stanem.|
| Upewnij się| Wskazuje, czy istnieje zmiennej. Ustawić tę właściwość na __obecny__ utworzyć zmienną środowiskową, jeśli nie istnieje lub upewnij się, że jego wartość odpowiada, jaka jest dostępna za pośrednictwem __wartość__ właściwości, jeśli zmienna już istnieje. Ustaw ją na __nieobecne__ można usunąć zmiennej, jeśli istnieje.|
| Ścieżka| Definiuje zmienną środowiskową, który jest konfigurowany. Ta właściwość jest ustawiana __$true__ Jeśli zmienna jest __ścieżki__ zmiennej; w przeciwnym razie ustaw ją na __$false__. Wartość domyślna to __$false__. Jeśli zmienna konfigurowany jest __ścieżki__ wartość zmiennej, realizowane za pośrednictwem __wartość__ właściwości, które zostaną dołączone do istniejącej wartości.|
| dependsOn | Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.|
| Wartość| Wartość do przypisania do zmiennej środowiskowej.|

## <a name="example"></a>Przykład

Poniższy przykład upewnia się, że __TestEnvironmentVariable__ jest obecny i ma wartość __WartośćTestowa__. Jeśli nie jest obecny, tworzy go.

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```