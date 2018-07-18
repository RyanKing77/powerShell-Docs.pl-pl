---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: DSC dla systemu Linux zasób nxGroup
ms.openlocfilehash: c61b6ab4a8c56d085b5297dcfc7582187d54f946
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093606"
---
# <a name="dsc-for-linux-nxgroup-resource"></a>DSC dla systemu Linux zasób nxGroup

**NxGroup** zasobów w programie PowerShell Desired State Configuration (DSC) udostępnia mechanizm do zarządzania grupami lokalnymi w węźle systemu Linux.

## <a name="syntax"></a>Składnia

```
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present } ]
    [ Members = <string[]> ]
    [ MembersToInclude = <string[]> ]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a>Właściwości

|  Właściwość |  Opis |
|---|---|
| Nazwa grupy| Określa nazwę grupy, dla którego chcesz zapewnić określonego stanu.|
| Upewnij się| Określa, czy należy sprawdzić, czy grupa istnieje. Ustaw tę właściwość "Present", aby upewnić się, że grupa istnieje. Ustaw ją na "Brak", aby upewnić się, że grupa nie istnieje. Wartość domyślna to "Istnieje".|
| Elementy członkowskie| Określa elementy członkowskie, które tworzą grupy.|
| MembersToInclude| Określa, że użytkownicy, którzy chcesz, aby upewnić się, są członkami grupy.|
| MembersToExclude| Określa, że użytkownicy, którzy chcesz, aby upewnić się, nie są członkami grupy.|
| PreferredGroupID| Ustawia identyfikator grupy podana jest wartość, jeśli jest to możliwe. Jeśli identyfikator grupy jest obecnie w użyciu, dalej identyfikator grupy dostępności jest używany.|
| DependsOn | Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli **identyfikator** zasobu jest najpierw blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** a jej typ jest **ResourceType**, składnia za pomocą tego Właściwość jest `DependsOn = '[ResourceType]ResourceName'`.|

## <a name="example"></a>Przykład

Poniższy przykład zapewnia, że użytkownik monuser istnieje i jest członkiem grupy "DBusers".

```powershell
Import-DSCResource -Module nx

Node $node {
    nxUser UserExample {
       UserName = 'monuser'
       Description = 'Monitoring user'
       Password = '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
       Ensure = 'Present'
       HomeDirectory = '/home/monuser'
    }

    nxGroup GroupExample {
       GroupName = 'DBusers'
       Ensure = 'Present'
       MembersToInclude = 'monuser'
       DependsOn = '[nxUser]UserExample'
    }
}
```