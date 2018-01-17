---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Zasób WaitForSome DSC"
ms.openlocfilehash: cbe16c543f0eeb62dbe1fb439af2f9147f1bc210
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
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
| ResourceName| Nazwa zasobu zależne.| 
| RetryIntervalSec| Liczba sekund przed ponowną próbą. Minimalną jest 1.| 
| RetryCount| Maksymalna liczba ponownych prób.| 
| ThrottleLimit| Liczba maszyn nawiązać jednocześnie. Domyślna to nowy cimsession domyślne.| 
| dependsOn | Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.|
| PsDscRunAsCredential | Zobacz [przy użyciu poświadczeń użytkownika przy użyciu usługi Konfiguracja DSC](https://docs.microsoft.com/en-us/powershell/dsc/runasuser) |


## <a name="example"></a>Przykład

Na przykład sposobu używania tego zasobu zobacz [określania zależności między węzłami](crossNodeDependencies.md)

