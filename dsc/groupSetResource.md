---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
description: Udostępnia mechanizm do zarządzania grupami lokalnymi w docelowym węźle.
title: Zasób GroupSet DSC
ms.openlocfilehash: 3d6fdcaef6053964d3fb3b709a5263d291a7c840
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="fddec-104">Zasób GroupSet DSC</span><span class="sxs-lookup"><span data-stu-id="fddec-104">DSC GroupSet Resource</span></span>

> <span data-ttu-id="fddec-105">Dotyczy: Windows środowiska Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="fddec-105">Applies To: Windows Windows PowerShell 5.0</span></span>

<span data-ttu-id="fddec-106">**GroupSet** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm zarządzania grup lokalnych w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="fddec-106">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="fddec-107">Ten zasób jest [złożonego zasobów](authoringResourceComposite.md) wywołującym [grupy zasobów](groupResource.md) dla każdej grupy określonej w `GroupName` parametru.</span><span class="sxs-lookup"><span data-stu-id="fddec-107">This resource is a [composite resource](authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="fddec-108">Jeśli chcesz dodać i/lub Usuń tę samą listę elementów członkowskich do więcej niż jednej grupy, Usuń więcej niż jedną grupę lub Dodaj więcej niż jednej grupy z tej samej listy elementów członkowskich, należy użyć tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="fddec-108">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

##<a name="syntax"></a><span data-ttu-id="fddec-109">Składnia ##</span><span class="sxs-lookup"><span data-stu-id="fddec-109">Syntax##</span></span>
```
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="fddec-110">Właściwości</span><span class="sxs-lookup"><span data-stu-id="fddec-110">Properties</span></span>

|  <span data-ttu-id="fddec-111">Właściwość</span><span class="sxs-lookup"><span data-stu-id="fddec-111">Property</span></span>  |  <span data-ttu-id="fddec-112">Opis</span><span class="sxs-lookup"><span data-stu-id="fddec-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="fddec-113">Nazwa grupy</span><span class="sxs-lookup"><span data-stu-id="fddec-113">GroupName</span></span>| <span data-ttu-id="fddec-114">Nazwy grup, dla których chcesz zapewnić z określonym stanem.</span><span class="sxs-lookup"><span data-stu-id="fddec-114">The names of the groups for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="fddec-115">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="fddec-115">MembersToExclude</span></span>| <span data-ttu-id="fddec-116">Ta właściwość umożliwia usunięcie członków z istniejącego członkostwa w grupach.</span><span class="sxs-lookup"><span data-stu-id="fddec-116">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="fddec-117">Wartość tej właściwości jest tablicą ciągów w postaci *domeny*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="fddec-117">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="fddec-118">Jeśli ta właściwość jest ustawiona w konfiguracji, nie używaj **członków** właściwości.</span><span class="sxs-lookup"><span data-stu-id="fddec-118">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="fddec-119">W ten sposób spowoduje wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="fddec-119">Doing so will generate an error.</span></span>|
| <span data-ttu-id="fddec-120">Poświadczenie</span><span class="sxs-lookup"><span data-stu-id="fddec-120">Credential</span></span>| <span data-ttu-id="fddec-121">Poświadczenia wymagane do dostępu do zasobów zdalnego.</span><span class="sxs-lookup"><span data-stu-id="fddec-121">The credentials required to access remote resources.</span></span> <span data-ttu-id="fddec-122">**Uwaga**: to konto musi mieć odpowiednich uprawnień usługi Active Directory, aby dodać wszystkie konta innego niż lokalne do grupy; w przeciwnym razie wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="fddec-122">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span>
| <span data-ttu-id="fddec-123">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="fddec-123">Ensure</span></span>| <span data-ttu-id="fddec-124">Wskazuje, czy istnieją grupy.</span><span class="sxs-lookup"><span data-stu-id="fddec-124">Indicates whether the groups exist.</span></span> <span data-ttu-id="fddec-125">Ustaw tę właściwość na "Brak", aby upewnić się, że grupy nie istnieją.</span><span class="sxs-lookup"><span data-stu-id="fddec-125">Set this property to "Absent" to ensure that the groups do not exist.</span></span> <span data-ttu-id="fddec-126">Ustawienie jej "Przedstawienie" (wartość domyślna) zapewnia, że istnieją grupy.</span><span class="sxs-lookup"><span data-stu-id="fddec-126">Setting it to "Present" (the default value) ensures that the groups exist.</span></span>|
| <span data-ttu-id="fddec-127">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="fddec-127">Members</span></span>| <span data-ttu-id="fddec-128">Ta właściwość służy do Zamień od bieżącego członkostwa grupy określone elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="fddec-128">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="fddec-129">Wartość tej właściwości jest tablicą ciągów w postaci *domeny*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="fddec-129">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="fddec-130">Jeśli ta właściwość jest ustawiona w konfiguracji, nie używaj albo **MembersToExclude** lub **MembersToInclude** właściwości.</span><span class="sxs-lookup"><span data-stu-id="fddec-130">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="fddec-131">W ten sposób spowoduje wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="fddec-131">Doing so will generate an error.</span></span>|
| <span data-ttu-id="fddec-132">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="fddec-132">MembersToInclude</span></span>| <span data-ttu-id="fddec-133">Ta właściwość służy do dodawania członków do istniejącego członkostwa grupy.</span><span class="sxs-lookup"><span data-stu-id="fddec-133">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="fddec-134">Wartość tej właściwości jest tablicą ciągów w postaci *domeny*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="fddec-134">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="fddec-135">Jeśli ta właściwość jest ustawiona w konfiguracji, nie używaj **członków** właściwości.</span><span class="sxs-lookup"><span data-stu-id="fddec-135">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="fddec-136">W ten sposób spowoduje wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="fddec-136">Doing so will generate an error.</span></span>|
| <span data-ttu-id="fddec-137">dependsOn</span><span class="sxs-lookup"><span data-stu-id="fddec-137">DependsOn</span></span> | <span data-ttu-id="fddec-138">Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="fddec-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="fddec-139">Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości to "DependsOn ="[ResourceName ResourceType]"".</span><span class="sxs-lookup"><span data-stu-id="fddec-139">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example-1"></a><span data-ttu-id="fddec-140">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="fddec-140">Example 1</span></span>

<span data-ttu-id="fddec-141">Poniższy przykład przedstawia sposób upewnić się, że istnieją dwie grupy o nazwie "mojaGrupa" i "myOtherGroup".</span><span class="sxs-lookup"><span data-stu-id="fddec-141">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span>

```powershell
configuration GroupSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        GroupSet GroupSetTest
        {
            GroupName        = @("myGroup", "myOtherGroup")
            Ensure           = "Present"
            MembersToInclude = @("contoso\alice", "contoso\bob")
            MembersToExclude = $("contoso\john")
            Credential       = Get-Credential
        }
    }
}
$cd = @{
    AllNodes = @(
        @{
            NodeName                    = 'localhost'
            PSDscAllowPlainTextPassword = $true
            PSDscAllowDomainUser        = $true
        }
    )
}


GroupSetTest -ConfigurationData $cd
```

><span data-ttu-id="fddec-142">**Uwaga:** w tym przykładzie używane poświadczenia w postaci zwykłego tekstu, dla uproszczenia.</span><span class="sxs-lookup"><span data-stu-id="fddec-142">**Note:** This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="fddec-143">Aby uzyskać informacje dotyczące do szyfrowania poświadczeń w pliku MOF konfiguracji, zobacz [Zabezpieczanie pliku MOF](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="fddec-143">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](secureMOF.md).</span></span>