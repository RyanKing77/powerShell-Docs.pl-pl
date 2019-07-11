---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób WaitForAny DSC
ms.openlocfilehash: d15acb3fb34d571eca56ed496eaa9a04b2551ff0
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726859"
---
# <a name="dsc-waitforany-resource"></a>Zasób WaitForAny DSC

> Dotyczy: Program Windows PowerShell w wersji 5.1 i nowszych

**WaitForAny** zasobów Desired State Configuration (DSC) mogą być używane w bloku węzła w [konfiguracji DSC](../../../configurations/configurations.md) do określania zależności w konfiguracji na innych węzłach.

Ten zasób zakończy się pomyślnie, jeśli zasób określony przez **ResourceName** właściwość jest w żądanym stanie na wszystkie węzły docelowe, zdefiniowane w **NodeName** właściwości.

> [!NOTE]
> **WaitForAny** zasobów używa Windows Remote Management, aby sprawdzić stan innych węzłów.
> Aby uzyskać więcej informacji na temat wymagania dotyczące portów i zabezpieczeń dla usługi WinRM, zobacz [zagadnienia dotyczące zabezpieczeń komunikacji zdalnej programu PowerShell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).

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
| RetryCount| Maksymalna liczba ponownych prób.|
| ThrottleLimit| Liczba maszyn do łączenia z jednocześnie. Domyślną jest domyślna nowy cimsession.|
| dependsOn | Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest __ResourceName__ a jej typ jest __ResourceType__, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Przykład

Na przykład dotyczące używania tego zasobu zobacz [określanie zależności między węzłami](../../../configurations/crossNodeDependencies.md)
