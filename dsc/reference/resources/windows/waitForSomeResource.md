---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób WaitForSome DSC
ms.openlocfilehash: 906375a8fcf9b87d4b7487e63e6fae3f05b86d0d
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048381"
---
# <a name="dsc-waitforsome-resource"></a>Zasób WaitForSome DSC

> Dotyczy: Program Windows PowerShell 5.0 lub nowszy

**WaitForAny** zasobów Desired State Configuration (DSC) mogą być używane w bloku węzła w [konfiguracji DSC](../../../configurations/configurations.md) do określania zależności w konfiguracji na innych węzłach.

Ten zasób zakończy się pomyślnie, jeśli zasób określony przez **ResourceName** właściwość jest w żądanym stanie na minimalna liczba węzłów (określony przez **NodeCount**) zdefiniowane przez **NodeName**  właściwości.


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
| NodeCount| Minimalna liczba węzłów, które muszą być w żądanym stanie dla tego zasobu została wykonana pomyślnie.|
| NodeName| Węzły docelowe zasobu, aby była zależna od.|
| ResourceName| Nazwa zasobu, aby była zależna od. Jeśli ten zasób należy do innej konfiguracji, format nazwy jako "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "|
| RetryIntervalSec| Liczba sekund przed ponowną próbą. Minimalny to 1.|
| retryCount| Maksymalna liczba ponownych prób.|
| ThrottleLimit| Liczba maszyn do łączenia z jednocześnie. Domyślną jest domyślna nowy cimsession.|
| DependsOn | Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest __ResourceName__ a jej typ jest __ResourceType__, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.|
| PsDscRunAsCredential | Zobacz [DSC przy użyciu poświadczeń użytkownika](https://docs.microsoft.com/powershell/dsc/runasuser) |

## <a name="example"></a>Przykład

Na przykład dotyczące używania tego zasobu zobacz [określanie zależności między węzłami](../../../configurations/crossNodeDependencies.md)
