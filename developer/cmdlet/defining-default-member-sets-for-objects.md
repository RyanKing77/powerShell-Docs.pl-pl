---
title: Definiowanie ustawia domyślny element członkowski obiektów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 77f94326-8ffe-4d40-bd2a-b79fb0b4a4e5
caps.latest.revision: 8
ms.openlocfilehash: e8185eb7221a3be0445eddc537dbca89478c74f2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849469"
---
# <a name="defining-default-member-sets-for-objects"></a>Definiowanie domyślnych zestawów elementów członkowskich dla obiektów

Zestaw elementów członkowskich PSStandardMembers jest używana przez środowisko Windows PowerShell do definiowania zestawów właściwości domyślne dla obiektu. Domyślne zestawy właściwości może służyć za pomocą poleceń, takich jak formatowania polecenia cmdlet, aby wyświetlić tylko te właściwości, które są definiowane przez zestaw właściwości. Domyślne zestawy właściwości obejmują DefaultDisplayProperty DefaultDisplayPropertySet i DefaultKeyPropertySet. Program Windows PowerShell ignoruje wszystkie inne zestawy elementów członkowskich i inne zestawy właściwości, dodane do zestawu elementów członkowskich PSStandardMembers.

## <a name="member-set-for-systemdiagnosticsprocess"></a>Zestaw elementów członkowskich dla System.Diagnostics.Process

W poniższym przykładzie zestaw elementów członkowskich PSStandardMembers definiuje ustawienie właściwości DefaultDisplayPropertySet [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektów. Ten zestaw właściwość jest używana przez [Format-Lista](/powershell/module/Microsoft.PowerShell.Utility/Format-List) polecenia cmdlet.
W poniższym przykładzie zestaw elementów członkowskich PSStandardMembers definiuje ustawienie właściwości DefaultDisplayPropertySet [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektów. Ten zestaw właściwość jest używana przez [Format-Lista](/powershell/module/Microsoft.PowerShell.Utility/Format-List) polecenia cmdlet.

```xml
<Type>
  <Name>System.Diagnostics.Process</Name>
  <Members>
    <MemberSet>
     <Name>PSStandardMembers</Name>
     <Members>
       <PropertySet>
         <Name>DefaultDisplayPropertySet</Name>
         <ReferencedProperties>
           <Name>Id</Name>
           <Name>Handles</Name>
           <Name>CPU</Name>
           <Name>Name</Name>
         </ReferencedProperties>
      </PropertySet>
    </Members>
  </MemberSet>
```

Następujące dane wyjściowe pokazują domyślne właściwości zwrócony przez [Format-Lista](/powershell/module/Microsoft.PowerShell.Utility/Format-List) polecenia cmdlet. Tylko `Id`, `Handles`, `CPU`, i `Name` właściwości są zwracane dla każdego obiektu procesu.
Następujące dane wyjściowe pokazują domyślne właściwości zwrócony przez [Format-Lista](/powershell/module/Microsoft.PowerShell.Utility/Format-List) polecenia cmdlet. Tylko `Id`, `Handles`, `CPU`, i `Name` właściwości są zwracane dla każdego obiektu procesu.

```powershell
Get-Process | format-list
```

```output
Id      : 2036
Handles : 27
CPU     :
Name    : AEADISRV

Id      : 272
Handles : 38
CPU     :
Name    : agrsmsvc
...
```

## <a name="see-also"></a>Zobacz też

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
