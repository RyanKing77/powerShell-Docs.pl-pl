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
# <a name="defining-default-member-sets-for-objects"></a><span data-ttu-id="dd5d7-102">Definiowanie domyślnych zestawów elementów członkowskich dla obiektów</span><span class="sxs-lookup"><span data-stu-id="dd5d7-102">Defining Default Member Sets for Objects</span></span>

<span data-ttu-id="dd5d7-103">Zestaw elementów członkowskich PSStandardMembers jest używana przez środowisko Windows PowerShell do definiowania zestawów właściwości domyślne dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="dd5d7-103">The PSStandardMembers member set is used by Windows PowerShell to define the default property sets for an object.</span></span> <span data-ttu-id="dd5d7-104">Domyślne zestawy właściwości może służyć za pomocą poleceń, takich jak formatowania polecenia cmdlet, aby wyświetlić tylko te właściwości, które są definiowane przez zestaw właściwości.</span><span class="sxs-lookup"><span data-stu-id="dd5d7-104">The default property sets can be used by commands such as the formatting cmdlets to display only those properties that are defined by the property set.</span></span> <span data-ttu-id="dd5d7-105">Domyślne zestawy właściwości obejmują DefaultDisplayProperty DefaultDisplayPropertySet i DefaultKeyPropertySet.</span><span class="sxs-lookup"><span data-stu-id="dd5d7-105">The default property sets include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="dd5d7-106">Program Windows PowerShell ignoruje wszystkie inne zestawy elementów członkowskich i inne zestawy właściwości, dodane do zestawu elementów członkowskich PSStandardMembers.</span><span class="sxs-lookup"><span data-stu-id="dd5d7-106">Windows PowerShell ignores all other member sets and any other property sets added to the PSStandardMembers member set.</span></span>

## <a name="member-set-for-systemdiagnosticsprocess"></a><span data-ttu-id="dd5d7-107">Zestaw elementów członkowskich dla System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="dd5d7-107">Member Set for System.Diagnostics.Process</span></span>

<span data-ttu-id="dd5d7-108">W poniższym przykładzie zestaw elementów członkowskich PSStandardMembers definiuje ustawienie właściwości DefaultDisplayPropertySet [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektów.</span><span class="sxs-lookup"><span data-stu-id="dd5d7-108">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="dd5d7-109">Ten zestaw właściwość jest używana przez [Format-Lista](/powershell/module/Microsoft.PowerShell.Utility/Format-List) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dd5d7-109">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>
<span data-ttu-id="dd5d7-110">W poniższym przykładzie zestaw elementów członkowskich PSStandardMembers definiuje ustawienie właściwości DefaultDisplayPropertySet [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektów.</span><span class="sxs-lookup"><span data-stu-id="dd5d7-110">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="dd5d7-111">Ten zestaw właściwość jest używana przez [Format-Lista](/powershell/module/Microsoft.PowerShell.Utility/Format-List) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dd5d7-111">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>

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

<span data-ttu-id="dd5d7-112">Następujące dane wyjściowe pokazują domyślne właściwości zwrócony przez [Format-Lista](/powershell/module/Microsoft.PowerShell.Utility/Format-List) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dd5d7-112">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="dd5d7-113">Tylko `Id`, `Handles`, `CPU`, i `Name` właściwości są zwracane dla każdego obiektu procesu.</span><span class="sxs-lookup"><span data-stu-id="dd5d7-113">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>
<span data-ttu-id="dd5d7-114">Następujące dane wyjściowe pokazują domyślne właściwości zwrócony przez [Format-Lista](/powershell/module/Microsoft.PowerShell.Utility/Format-List) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dd5d7-114">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="dd5d7-115">Tylko `Id`, `Handles`, `CPU`, i `Name` właściwości są zwracane dla każdego obiektu procesu.</span><span class="sxs-lookup"><span data-stu-id="dd5d7-115">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="dd5d7-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dd5d7-116">See Also</span></span>

[<span data-ttu-id="dd5d7-117">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dd5d7-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
