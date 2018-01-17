---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "DSC dla systemu Linux nxGroup zasobów"
ms.openlocfilehash: bc01f6ae5ed61aff63958fe55f30d82f9b81b2b9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-for-linux-nxgroup-resource"></a>DSC dla systemu Linux nxGroup zasobów

**NxGroup** zasób w PowerShell żądanego stanu konfiguracji (DSC) zapewnia mechanizm zarządzania grup lokalnych w węźle systemu Linux.

## <a name="syntax"></a>Składnia

```powershell
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Members = <string[]> ]
    [ MebersToInclude = <string[]>]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}

```

## <a name="properties"></a>Właściwości

|  Właściwość |  Opis | 
|---|---|
| GroupName| Określa nazwę grupy, dla którego chcesz zapewnić z określonym stanem.| 
| Upewnij się| Określa, czy należy sprawdzić, czy dana grupa istnieje. Ustaw tę właściwość na "Brak", aby upewnić się, że grupa istnieje. Ustaw ją na "Brak", aby upewnić się, że grupa nie istnieje. Wartość domyślna to "Brak".| 
| Elementy członkowskie| Określa elementy członkowskie, które tworzą grupę.| 
| MembersToInclude| Określa, że użytkownicy, którzy chcą zapewnić są elementami członkowskimi grupy.| 
| MembersToExclude| Określa, że użytkownicy, którzy chcą zapewnić nie są członkami grupy.| 
| PreferredGroupID| Jeśli to możliwe Ustawia identyfikator grupy do podanej wartości. Jeśli identyfikator grupy jest obecnie w użyciu, dalej identyfikator grupy dostępności jest używany.| 
| dependsOn | Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli **identyfikator** zasobu jest pierwszy blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** i jej typ jest **ResourceType**, za pomocą tej składni Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.| 

## <a name="example"></a>Przykład

Poniższy przykład gwarantuje, że użytkownik "monuser" istnieje i jest członkiem grupy "DBusers".

```
Import-DSCResource -Module nx 

Node $node {

nxUser UserExample{
   UserName = "monuser"
   Description = "Monitoring user"
   Password  =    '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
   Ensure = "Present"
   HomeDirectory = "/home/monuser"
}
 
nxGroup GroupExample{
   GroupName = "DBusers"
   Ensure = "Present"
   MembersToInclude = "monuser"
   DependsOn = "[nxUser]UserExample"            
}
}
```

