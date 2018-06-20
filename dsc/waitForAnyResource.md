---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasób WaitForAny DSC
ms.openlocfilehash: c9700c908f8601db85f9c922445969a34b59d453
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186715"
---
# <a name="dsc-waitforany-resource"></a>Zasób WaitForAny DSC

> Dotyczy: Windows PowerShell 5.1 i nowszych

**WaitForSome** zasobów konfiguracji żądanego stanu (DSC) może być używana w bloku węzła w [konfiguracji DSC](configurations.md) Aby określić zależności w konfiguracji na innych węzłach.

Ten zasób zakończy się pomyślnie, jeśli Jeśli zasób określony przez **ResourceName** właściwość jest w żądanym stanie na wszystkie węzły docelowe zdefiniowane w **NodeName** właściwości.


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
| resourceName| Nazwa zasobu zależne. Jeśli ten zasób należy do innej konfiguracji, format nazwy jako "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "|
| nodeName| Węzły docelowe są zależne od zasobu.|
| RetryIntervalSec| Liczba sekund przed ponowną próbą. Minimalną jest 1.|
| retryCount| Maksymalna liczba ponownych prób.|
| ThrottleLimit| Liczba maszyn nawiązać jednocześnie. Domyślna to nowy cimsession domyślne.|
| dependsOn | Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.|


## <a name="example"></a>Przykład

Na przykład sposobu używania tego zasobu zobacz [określania zależności między węzłami](crossNodeDependencies.md)