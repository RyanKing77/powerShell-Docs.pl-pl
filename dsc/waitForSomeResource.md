---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasób WaitForSome DSC
ms.openlocfilehash: 08a5b96bee0b1b4475470e0d857dca79dee2b02e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190234"
---
# <a name="dsc-waitforsome-resource"></a>Zasób WaitForSome DSC

> Dotyczy: Windows PowerShell 5.0 i nowszych

**WaitForAny** zasobów konfiguracji żądanego stanu (DSC) może być używana w bloku węzła w [konfiguracji DSC](configurations.md) Aby określić zależności w konfiguracji na innych węzłach.

Ten zasób zakończy się pomyślnie, jeśli zasób określony przez **ResourceName** właściwość jest w żądanym stanie na minimalna liczba węzłów (określonego przez **NodeCount**) zdefiniowanych przez **NodeName**  właściwości.


## <a name="syntax"></a>Składnia

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

## <a name="properties"></a>Właściwości

|  Właściwość  |  Opis   |
|---|---|
| NodeCount| Minimalna liczba węzłów, które muszą być w żądanym stanie dla tego zasobu powiodło się.|
| nodeName| Węzły docelowe są zależne od zasobu.|
| resourceName| Nazwa zasobu zależne. Jeśli ten zasób należy do innej konfiguracji, format nazwy jako "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "|
| RetryIntervalSec| Liczba sekund przed ponowną próbą. Minimalną jest 1.|
| retryCount| Maksymalna liczba ponownych prób.|
| ThrottleLimit| Liczba maszyn nawiązać jednocześnie. Domyślna to nowy cimsession domyślne.|
| dependsOn | Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.|
| PsDscRunAsCredential | Zobacz [przy użyciu poświadczeń użytkownika przy użyciu usługi Konfiguracja DSC](https://docs.microsoft.com/powershell/dsc/runasuser) |


## <a name="example"></a>Przykład

Na przykład sposobu używania tego zasobu zobacz [określania zależności między węzłami](crossNodeDependencies.md)