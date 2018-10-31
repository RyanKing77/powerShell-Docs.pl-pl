---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
description: Udostępnia mechanizm do zarządzania grupami lokalnymi w docelowym węźle.
title: Zasób Groupset DSC
ms.openlocfilehash: 6fa8e9637da896848e859dc60a42add12e973b34
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2018
ms.locfileid: "50226121"
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="5a11d-104">Zasób Groupset DSC</span><span class="sxs-lookup"><span data-stu-id="5a11d-104">DSC GroupSet Resource</span></span>

> <span data-ttu-id="5a11d-105">Dotyczy: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5a11d-105">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="5a11d-106">**GroupSet** zasobów w Windows PowerShell Desired State Configuration (DSC) udostępnia mechanizm do zarządzania grupami lokalnymi w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="5a11d-106">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="5a11d-107">Ten zasób jest [złożonego zasobów](authoringResourceComposite.md) wywołująca [grupy zasobów](groupResource.md) dla każdej grupy określony w `GroupName` parametru.</span><span class="sxs-lookup"><span data-stu-id="5a11d-107">This resource is a [composite resource](authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="5a11d-108">Korzystając z tego zasobu, jeśli chcesz dodać i/lub usunięcia tej samej listy elementów członkowskich do więcej niż jednej grupy, usunąć więcej niż jednej grupy lub Dodaj więcej niż jednej grupy o tej samej listy elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="5a11d-108">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

## <a name="syntax"></a><span data-ttu-id="5a11d-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a11d-109">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="5a11d-110">Właściwości</span><span class="sxs-lookup"><span data-stu-id="5a11d-110">Properties</span></span>

|  <span data-ttu-id="5a11d-111">Właściwość</span><span class="sxs-lookup"><span data-stu-id="5a11d-111">Property</span></span>  |  <span data-ttu-id="5a11d-112">Opis</span><span class="sxs-lookup"><span data-stu-id="5a11d-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="5a11d-113">Nazwa grupy</span><span class="sxs-lookup"><span data-stu-id="5a11d-113">GroupName</span></span>| <span data-ttu-id="5a11d-114">Nazwy grup, dla których chcesz mieć pewność określonego stanu.</span><span class="sxs-lookup"><span data-stu-id="5a11d-114">The names of the groups for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="5a11d-115">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="5a11d-115">MembersToExclude</span></span>| <span data-ttu-id="5a11d-116">Ta właściwość służy do usuwania członków z istniejących członkostwa w grupach.</span><span class="sxs-lookup"><span data-stu-id="5a11d-116">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="5a11d-117">Wartość tej właściwości jest tablicą ciągów formularza *domeny*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="5a11d-117">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="5a11d-118">Jeśli ustawisz tę właściwość w ramach konfiguracji należy używać **członków** właściwości.</span><span class="sxs-lookup"><span data-stu-id="5a11d-118">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="5a11d-119">Ten sposób spowoduje wygenerowanie błędu.</span><span class="sxs-lookup"><span data-stu-id="5a11d-119">Doing so will generate an error.</span></span>|
| <span data-ttu-id="5a11d-120">Poświadczenie</span><span class="sxs-lookup"><span data-stu-id="5a11d-120">Credential</span></span>| <span data-ttu-id="5a11d-121">Poświadczenia wymagane do dostępu do zasobów zdalnych.</span><span class="sxs-lookup"><span data-stu-id="5a11d-121">The credentials required to access remote resources.</span></span> <span data-ttu-id="5a11d-122">**Uwaga**: to konto musi mieć odpowiednie uprawnienia usługi Active Directory można dodać wszystkie konta innego niż lokalne do grupy; w przeciwnym razie wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="5a11d-122">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span>
| <span data-ttu-id="5a11d-123">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="5a11d-123">Ensure</span></span>| <span data-ttu-id="5a11d-124">Wskazuje, czy istnieją grupy.</span><span class="sxs-lookup"><span data-stu-id="5a11d-124">Indicates whether the groups exist.</span></span> <span data-ttu-id="5a11d-125">Ustaw tę właściwość na "Brak", aby upewnić się, że nie istnieją grupy.</span><span class="sxs-lookup"><span data-stu-id="5a11d-125">Set this property to "Absent" to ensure that the groups do not exist.</span></span> <span data-ttu-id="5a11d-126">Ustawienie "Przedstawia" (wartość domyślna) gwarantuje, że istnieją grupy.</span><span class="sxs-lookup"><span data-stu-id="5a11d-126">Setting it to "Present" (the default value) ensures that the groups exist.</span></span>|
| <span data-ttu-id="5a11d-127">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="5a11d-127">Members</span></span>| <span data-ttu-id="5a11d-128">Użyj tej właściwości, aby zamienić bieżącego członkostwa w grupie z tymi elementami.</span><span class="sxs-lookup"><span data-stu-id="5a11d-128">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="5a11d-129">Wartość tej właściwości jest tablicą ciągów formularza *domeny*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="5a11d-129">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="5a11d-130">Jeśli ta właściwość jest ustawiona w konfiguracji, nie używaj albo **MembersToExclude** lub **MembersToInclude** właściwości.</span><span class="sxs-lookup"><span data-stu-id="5a11d-130">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="5a11d-131">Ten sposób spowoduje wygenerowanie błędu.</span><span class="sxs-lookup"><span data-stu-id="5a11d-131">Doing so will generate an error.</span></span>|
| <span data-ttu-id="5a11d-132">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="5a11d-132">MembersToInclude</span></span>| <span data-ttu-id="5a11d-133">Aby dodać członków do istniejących członkostwa w grupie, należy używać tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="5a11d-133">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="5a11d-134">Wartość tej właściwości jest tablicą ciągów formularza *domeny*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="5a11d-134">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="5a11d-135">Jeśli ustawisz tę właściwość w ramach konfiguracji należy używać **członków** właściwości.</span><span class="sxs-lookup"><span data-stu-id="5a11d-135">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="5a11d-136">Ten sposób spowoduje wygenerowanie błędu.</span><span class="sxs-lookup"><span data-stu-id="5a11d-136">Doing so will generate an error.</span></span>|
| <span data-ttu-id="5a11d-137">DependsOn</span><span class="sxs-lookup"><span data-stu-id="5a11d-137">DependsOn</span></span> | <span data-ttu-id="5a11d-138">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="5a11d-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="5a11d-139">Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest __ResourceName__ a jej typ jest __ResourceType__, składnia przy użyciu tej właściwości to "DependsOn ="[ ResourceName ResourceType]"".</span><span class="sxs-lookup"><span data-stu-id="5a11d-139">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example-1-ensuring-groups-are-present"></a><span data-ttu-id="5a11d-140">Przykład 1: Zapewnianie grupy są obecne</span><span class="sxs-lookup"><span data-stu-id="5a11d-140">Example 1: Ensuring Groups are present</span></span>

<span data-ttu-id="5a11d-141">Poniższy przykład pokazuje, jak upewnić się, że istnieją dwie grupy o nazwie "mojaGrupa" i "myOtherGroup".</span><span class="sxs-lookup"><span data-stu-id="5a11d-141">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span>

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

> [!NOTE] 
> <span data-ttu-id="5a11d-142">W tym przykładzie przy użyciu poświadczeń w postaci zwykłego tekstu dla uproszczenia.</span><span class="sxs-lookup"><span data-stu-id="5a11d-142">This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="5a11d-143">Aby uzyskać informacje o tym, jak można zaszyfrować poświadczenia w pliku MOF konfiguracji, zobacz [Zabezpieczanie pliku MOF](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="5a11d-143">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](secureMOF.md).</span></span>
