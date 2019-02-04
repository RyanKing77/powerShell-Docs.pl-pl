---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: DSC for Linux nxGroup Resource
ms.openlocfilehash: c61b6ab4a8c56d085b5297dcfc7582187d54f946
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688343"
---
# <a name="dsc-for-linux-nxgroup-resource"></a><span data-ttu-id="a89c9-103">DSC for Linux nxGroup Resource</span><span class="sxs-lookup"><span data-stu-id="a89c9-103">DSC for Linux nxGroup Resource</span></span>

<span data-ttu-id="a89c9-104">**NxGroup** zasobów w programie PowerShell Desired State Configuration (DSC) udostępnia mechanizm do zarządzania grupami lokalnymi w węźle systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="a89c9-104">The **nxGroup** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="a89c9-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a89c9-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="a89c9-106">Właściwości</span><span class="sxs-lookup"><span data-stu-id="a89c9-106">Properties</span></span>

|  <span data-ttu-id="a89c9-107">Właściwość</span><span class="sxs-lookup"><span data-stu-id="a89c9-107">Property</span></span> |  <span data-ttu-id="a89c9-108">Opis</span><span class="sxs-lookup"><span data-stu-id="a89c9-108">Description</span></span> |
|---|---|
| <span data-ttu-id="a89c9-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="a89c9-109">GroupName</span></span>| <span data-ttu-id="a89c9-110">Określa nazwę grupy, dla którego chcesz zapewnić określonego stanu.</span><span class="sxs-lookup"><span data-stu-id="a89c9-110">Specifies the name of the group for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="a89c9-111">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="a89c9-111">Ensure</span></span>| <span data-ttu-id="a89c9-112">Określa, czy należy sprawdzić, czy grupa istnieje.</span><span class="sxs-lookup"><span data-stu-id="a89c9-112">Determines whether to check if the group exists.</span></span> <span data-ttu-id="a89c9-113">Ustaw tę właściwość "Present", aby upewnić się, że grupa istnieje.</span><span class="sxs-lookup"><span data-stu-id="a89c9-113">Set this property to "Present" to ensure the group exists.</span></span> <span data-ttu-id="a89c9-114">Ustaw ją na "Brak", aby upewnić się, że grupa nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="a89c9-114">Set it to "Absent" to ensure the group does not exist.</span></span> <span data-ttu-id="a89c9-115">Wartość domyślna to "Istnieje".</span><span class="sxs-lookup"><span data-stu-id="a89c9-115">The default value is "Present".</span></span>|
| <span data-ttu-id="a89c9-116">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a89c9-116">Members</span></span>| <span data-ttu-id="a89c9-117">Określa elementy członkowskie, które tworzą grupy.</span><span class="sxs-lookup"><span data-stu-id="a89c9-117">Specifies the members that form the group.</span></span>|
| <span data-ttu-id="a89c9-118">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="a89c9-118">MembersToInclude</span></span>| <span data-ttu-id="a89c9-119">Określa, że użytkownicy, którzy chcesz, aby upewnić się, są członkami grupy.</span><span class="sxs-lookup"><span data-stu-id="a89c9-119">Specifies the users who you want to ensure are members of the group.</span></span>|
| <span data-ttu-id="a89c9-120">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="a89c9-120">MembersToExclude</span></span>| <span data-ttu-id="a89c9-121">Określa, że użytkownicy, którzy chcesz, aby upewnić się, nie są członkami grupy.</span><span class="sxs-lookup"><span data-stu-id="a89c9-121">Specifies the users who you want to ensure are not members of the group.</span></span>|
| <span data-ttu-id="a89c9-122">PreferredGroupID</span><span class="sxs-lookup"><span data-stu-id="a89c9-122">PreferredGroupID</span></span>| <span data-ttu-id="a89c9-123">Ustawia identyfikator grupy podana jest wartość, jeśli jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="a89c9-123">Sets the group id to the provided value if possible.</span></span> <span data-ttu-id="a89c9-124">Jeśli identyfikator grupy jest obecnie w użyciu, dalej identyfikator grupy dostępności jest używany.</span><span class="sxs-lookup"><span data-stu-id="a89c9-124">If the group id is currently in use, the next available group id is used.</span></span>|
| <span data-ttu-id="a89c9-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="a89c9-125">DependsOn</span></span> | <span data-ttu-id="a89c9-126">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="a89c9-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a89c9-127">Na przykład jeśli **identyfikator** zasobu jest najpierw blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** a jej typ jest **ResourceType**, składnia za pomocą tego Właściwość jest `DependsOn = '[ResourceType]ResourceName'`.</span><span class="sxs-lookup"><span data-stu-id="a89c9-127">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = '[ResourceType]ResourceName'`.</span></span>|

## <a name="example"></a><span data-ttu-id="a89c9-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="a89c9-128">Example</span></span>

<span data-ttu-id="a89c9-129">Poniższy przykład zapewnia, że użytkownik monuser istnieje i jest członkiem grupy "DBusers".</span><span class="sxs-lookup"><span data-stu-id="a89c9-129">The following example ensures that the user 'monuser' exists and is a member of the group 'DBusers'.</span></span>

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