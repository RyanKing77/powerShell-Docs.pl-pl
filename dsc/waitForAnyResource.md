---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób WaitForAny DSC
ms.openlocfilehash: 39100f0fc52092c54bbecab55e3ef3dfabb4c70e
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2018
ms.locfileid: "50226053"
---
# <a name="dsc-waitforany-resource"></a>Zasób WaitForAny DSC

> Mają zastosowanie do: Program Windows PowerShell 5.1 i nowszych

**WaitForSome** zasobów Desired State Configuration (DSC) mogą być używane w bloku węzła w [konfiguracji DSC](configurations.md) do określania zależności w konfiguracji na innych węzłach.

Ten zasób zakończy się pomyślnie, jeśli zasób określony przez **ResourceName** właściwość jest w żądanym stanie na wszystkie węzły docelowe, zdefiniowane w **NodeName** właściwości.


## <a name="syntax"></a>Składnia

```
WaitForAny [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ]
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Właściwości

|  Właściwość  |  Opis   |
|---|---|
| ResourceName| Nazwa zasobu, aby była zależna od. Jeśli ten zasób należy do innej konfiguracji, format nazwy jako "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "|
| NodeName| Węzły docelowe zasobu, aby była zależna od.|
| RetryIntervalSec| Liczba sekund przed ponowną próbą. Minimalny to 1.|
| retryCount| Maksymalna liczba ponownych prób.|
| ThrottleLimit| Liczba maszyn do łączenia z jednocześnie. Domyślną jest domyślna nowy cimsession.|
| DependsOn | Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest __ResourceName__ a jej typ jest __ResourceType__, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.|


## <a name="example"></a>Przykład

Na przykład dotyczące używania tego zasobu zobacz [określanie zależności między węzłami](crossNodeDependencies.md)