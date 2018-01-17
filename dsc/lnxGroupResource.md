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
# <a name="dsc-for-linux-nxgroup-resource"></a><span data-ttu-id="0654f-103">DSC dla systemu Linux nxGroup zasobów</span><span class="sxs-lookup"><span data-stu-id="0654f-103">DSC for Linux nxGroup Resource</span></span>

<span data-ttu-id="0654f-104">**NxGroup** zasób w PowerShell żądanego stanu konfiguracji (DSC) zapewnia mechanizm zarządzania grup lokalnych w węźle systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="0654f-104">The **nxGroup** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="0654f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0654f-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="0654f-106">Właściwości</span><span class="sxs-lookup"><span data-stu-id="0654f-106">Properties</span></span>

|  <span data-ttu-id="0654f-107">Właściwość</span><span class="sxs-lookup"><span data-stu-id="0654f-107">Property</span></span> |  <span data-ttu-id="0654f-108">Opis</span><span class="sxs-lookup"><span data-stu-id="0654f-108">Description</span></span> | 
|---|---|
| <span data-ttu-id="0654f-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="0654f-109">GroupName</span></span>| <span data-ttu-id="0654f-110">Określa nazwę grupy, dla którego chcesz zapewnić z określonym stanem.</span><span class="sxs-lookup"><span data-stu-id="0654f-110">Specifies the name of the group for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="0654f-111">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="0654f-111">Ensure</span></span>| <span data-ttu-id="0654f-112">Określa, czy należy sprawdzić, czy dana grupa istnieje.</span><span class="sxs-lookup"><span data-stu-id="0654f-112">Determines whether to check if the group exists.</span></span> <span data-ttu-id="0654f-113">Ustaw tę właściwość na "Brak", aby upewnić się, że grupa istnieje.</span><span class="sxs-lookup"><span data-stu-id="0654f-113">Set this property to "Present" to ensure the group exists.</span></span> <span data-ttu-id="0654f-114">Ustaw ją na "Brak", aby upewnić się, że grupa nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="0654f-114">Set it to "Absent" to ensure the group does not exist.</span></span> <span data-ttu-id="0654f-115">Wartość domyślna to "Brak".</span><span class="sxs-lookup"><span data-stu-id="0654f-115">The default value is "Present".</span></span>| 
| <span data-ttu-id="0654f-116">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="0654f-116">Members</span></span>| <span data-ttu-id="0654f-117">Określa elementy członkowskie, które tworzą grupę.</span><span class="sxs-lookup"><span data-stu-id="0654f-117">Specifies the members that form the group.</span></span>| 
| <span data-ttu-id="0654f-118">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="0654f-118">MembersToInclude</span></span>| <span data-ttu-id="0654f-119">Określa, że użytkownicy, którzy chcą zapewnić są elementami członkowskimi grupy.</span><span class="sxs-lookup"><span data-stu-id="0654f-119">Specifies the users who you want to ensure are members of the group.</span></span>| 
| <span data-ttu-id="0654f-120">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="0654f-120">MembersToExclude</span></span>| <span data-ttu-id="0654f-121">Określa, że użytkownicy, którzy chcą zapewnić nie są członkami grupy.</span><span class="sxs-lookup"><span data-stu-id="0654f-121">Specifies the users who you want to ensure are not members of the group.</span></span>| 
| <span data-ttu-id="0654f-122">PreferredGroupID</span><span class="sxs-lookup"><span data-stu-id="0654f-122">PreferredGroupID</span></span>| <span data-ttu-id="0654f-123">Jeśli to możliwe Ustawia identyfikator grupy do podanej wartości.</span><span class="sxs-lookup"><span data-stu-id="0654f-123">Sets the group id to the provided value if possible.</span></span> <span data-ttu-id="0654f-124">Jeśli identyfikator grupy jest obecnie w użyciu, dalej identyfikator grupy dostępności jest używany.</span><span class="sxs-lookup"><span data-stu-id="0654f-124">If the group id is currently in use, the next available group id is used.</span></span>| 
| <span data-ttu-id="0654f-125">dependsOn</span><span class="sxs-lookup"><span data-stu-id="0654f-125">DependsOn</span></span> | <span data-ttu-id="0654f-126">Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="0654f-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0654f-127">Na przykład jeśli **identyfikator** zasobu jest pierwszy blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** i jej typ jest **ResourceType**, za pomocą tej składni Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="0654f-127">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="0654f-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="0654f-128">Example</span></span>

<span data-ttu-id="0654f-129">Poniższy przykład gwarantuje, że użytkownik "monuser" istnieje i jest członkiem grupy "DBusers".</span><span class="sxs-lookup"><span data-stu-id="0654f-129">The following example ensures that the user “monuser” exists and is a member of the group "DBusers".</span></span>

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

