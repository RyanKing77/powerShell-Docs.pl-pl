---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasób WaitForAll DSC
ms.openlocfilehash: 7cb2fc134f4391de0e5df2cd719902097bf2ebf5
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-waitforall-resource"></a>Zasób WaitForAll DSC

> Dotyczy: Windows PowerShell 5.0 i nowszych

**WaitForAll** zasobów konfiguracji żądanego stanu (DSC) może być używana w bloku węzła w [konfiguracji DSC](configurations.md) Aby określić zależności w konfiguracji na innych węzłach.

Ten zasób zakończy się powodzeniem, czy jeśli zasób określony przez **ResourceName** właściwość jest w żądanym stanie na wszystkich węzłach docelowych określonych w **NodeName** właściwości.


## <a name="syntax"></a>Składnia

```
WaitForAll [string] #ResourceName
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
| ResourceName| Nazwa zasobu zależne. Jeśli ten zasób należy do innej konfiguracji, format nazwy jako "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "|
| nodeName| Węzły docelowe są zależne od zasobu.|
| RetryIntervalSec| Liczba sekund przed ponowną próbą. Minimalną jest 1.|
| RetryCount| Maksymalna liczba ponownych prób.|
| ThrottleLimit| Liczba maszyn nawiązać jednocześnie. Domyślna to nowy cimsession domyślne.|
| dependsOn | Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.|


## <a name="example"></a>Przykład

Na przykład sposobu używania tego zasobu zobacz [określania zależności między węzłami](crossNodeDependencies.md)