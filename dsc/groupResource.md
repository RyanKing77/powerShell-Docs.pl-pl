---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasób grupy DSC
ms.openlocfilehash: 68e0840eaeb116b92260ca697acd5796460a2909
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222075"
---
# <a name="dsc-group-resource"></a><span data-ttu-id="95b2e-103">Zasób grupy DSC</span><span class="sxs-lookup"><span data-stu-id="95b2e-103">DSC Group Resource</span></span>

> <span data-ttu-id="95b2e-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="95b2e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="95b2e-105">Grupy zasobów w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm zarządzania grup lokalnych w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="95b2e-105">The Group resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="95b2e-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="95b2e-106">Syntax</span></span>

```
Group [string] #ResourceName
{
    GroupName          = [string]
    [ Credential       = [PSCredential] ]
    [ Description      = [string[]] ]
    [ Ensure           = [string] { Absent | Present }  ]
    [ Members          = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn        = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="95b2e-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="95b2e-107">Properties</span></span>

|  <span data-ttu-id="95b2e-108">Właściwość</span><span class="sxs-lookup"><span data-stu-id="95b2e-108">Property</span></span>  |  <span data-ttu-id="95b2e-109">Opis</span><span class="sxs-lookup"><span data-stu-id="95b2e-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="95b2e-110">Nazwa grupy</span><span class="sxs-lookup"><span data-stu-id="95b2e-110">GroupName</span></span>| <span data-ttu-id="95b2e-111">Nazwa grupy, dla którego chcesz zapewnić z określonym stanem.</span><span class="sxs-lookup"><span data-stu-id="95b2e-111">The name of the group for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="95b2e-112">Poświadczenie</span><span class="sxs-lookup"><span data-stu-id="95b2e-112">Credential</span></span>| <span data-ttu-id="95b2e-113">Poświadczenia wymagane do dostępu do zasobów zdalnego.</span><span class="sxs-lookup"><span data-stu-id="95b2e-113">The credentials required to access remote resources.</span></span> <span data-ttu-id="95b2e-114">**Uwaga**: to konto musi mieć odpowiednich uprawnień usługi Active Directory, aby dodać wszystkie konta innego niż lokalne do grupy; w przeciwnym razie wystąpi błąd, gdy konfiguracja jest wykonywana w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="95b2e-114">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error occurs when the configuration is executed on the target node.</span></span>
| <span data-ttu-id="95b2e-115">Opis</span><span class="sxs-lookup"><span data-stu-id="95b2e-115">Description</span></span>| <span data-ttu-id="95b2e-116">Opis grupy.</span><span class="sxs-lookup"><span data-stu-id="95b2e-116">The description of the group.</span></span>|
| <span data-ttu-id="95b2e-117">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="95b2e-117">Ensure</span></span>| <span data-ttu-id="95b2e-118">Wskazuje, czy dana grupa istnieje.</span><span class="sxs-lookup"><span data-stu-id="95b2e-118">Indicates if the group exists.</span></span> <span data-ttu-id="95b2e-119">Ustaw tę właściwość na "Brak", aby upewnić się, że grupa nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="95b2e-119">Set this property to "Absent" to ensure that the group does not exist.</span></span> <span data-ttu-id="95b2e-120">Ustawienie jej "Przedstawienie" (wartość domyślna) zapewnia, że grupa istnieje.</span><span class="sxs-lookup"><span data-stu-id="95b2e-120">Setting it to "Present" (the default value) ensures that the group exists.</span></span>|
| <span data-ttu-id="95b2e-121">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="95b2e-121">Members</span></span>| <span data-ttu-id="95b2e-122">Ta właściwość służy do Zamień od bieżącego członkostwa grupy określone elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="95b2e-122">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="95b2e-123">Wartość tej właściwości jest tablicą ciągów w postaci *domeny*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="95b2e-123">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="95b2e-124">Jeśli ta właściwość jest ustawiona w konfiguracji, nie używaj albo **MembersToExclude** lub **MembersToInclude** właściwości.</span><span class="sxs-lookup"><span data-stu-id="95b2e-124">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="95b2e-125">Dzięki temu generuje błąd.</span><span class="sxs-lookup"><span data-stu-id="95b2e-125">Doing so generates an error.</span></span>|
| <span data-ttu-id="95b2e-126">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="95b2e-126">MembersToExclude</span></span>| <span data-ttu-id="95b2e-127">Ta właściwość służy do usunięcia członków z istniejącego członkostwa grupy.</span><span class="sxs-lookup"><span data-stu-id="95b2e-127">Use this property to remove members from the existing membership of the group.</span></span> <span data-ttu-id="95b2e-128">Wartość tej właściwości jest tablicą ciągów w postaci *domeny*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="95b2e-128">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="95b2e-129">Jeśli ta właściwość jest ustawiona w konfiguracji, nie używaj **członków** właściwości.</span><span class="sxs-lookup"><span data-stu-id="95b2e-129">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="95b2e-130">Dzięki temu generuje błąd.</span><span class="sxs-lookup"><span data-stu-id="95b2e-130">Doing so generates an error.</span></span>|
| <span data-ttu-id="95b2e-131">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="95b2e-131">MembersToInclude</span></span>| <span data-ttu-id="95b2e-132">Ta właściwość służy do dodawania członków do istniejącego członkostwa grupy.</span><span class="sxs-lookup"><span data-stu-id="95b2e-132">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="95b2e-133">Wartość tej właściwości jest tablicą ciągów w postaci *domeny*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="95b2e-133">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="95b2e-134">Jeśli ta właściwość jest ustawiona w konfiguracji, nie używaj **członków** właściwości.</span><span class="sxs-lookup"><span data-stu-id="95b2e-134">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="95b2e-135">W ten sposób spowoduje wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="95b2e-135">Doing so will generate an error.</span></span>|
| <span data-ttu-id="95b2e-136">dependsOn</span><span class="sxs-lookup"><span data-stu-id="95b2e-136">DependsOn</span></span> | <span data-ttu-id="95b2e-137">Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="95b2e-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="95b2e-138">Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości to "DependsOn ="[ResourceName ResourceType]"".</span><span class="sxs-lookup"><span data-stu-id="95b2e-138">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example-1"></a><span data-ttu-id="95b2e-139">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="95b2e-139">Example 1</span></span>

<span data-ttu-id="95b2e-140">Poniższy przykład przedstawia sposób upewnić się, że istnieje grupa o nazwie "TestGroup".</span><span class="sxs-lookup"><span data-stu-id="95b2e-140">The following example shows how to ensure that a group called "TestGroup" is absent.</span></span>

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2"></a><span data-ttu-id="95b2e-141">Przykład 2</span><span class="sxs-lookup"><span data-stu-id="95b2e-141">Example 2</span></span>

<span data-ttu-id="95b2e-142">Poniższy przykład przedstawia sposób dodawania użytkownika usługi Active Directory do lokalnej grupy administratorów jako część kompilacji laboratorium wielu maszyny, której korzystasz już z PSCredential dla konta administratora lokalnego.</span><span class="sxs-lookup"><span data-stu-id="95b2e-142">The following example shows how to add an Active Directory User to the local administrators group as part of a Multi-Machine Lab build where you are already using a PSCredential for the Local Adminstrator account.</span></span>
<span data-ttu-id="95b2e-143">Jest to również używana do konta administratora domeny (po podwyższenie poziomu domeny), następnie należy przekonwertować tej PSCredential istniejących poświadczeń domeny przyjazną.</span><span class="sxs-lookup"><span data-stu-id="95b2e-143">As this is also used for the Domain Admin Account (after Domain promotion), we then need to convert this existing PSCredential to a Domain Friendly credential.</span></span>
<span data-ttu-id="95b2e-144">Następnie możemy dodać użytkownika domeny do lokalnej grupy administratorów na serwerze członkowskim.</span><span class="sxs-lookup"><span data-stu-id="95b2e-144">Then we can add a Domain User to the Local Administrators Group on the Member server.</span></span>

```powershell
@{
    AllNodes = @(
        @{
            NodeName = '*';
            DomainName = 'SubTest.contoso.com';
         }
        @{
            NodeName = 'Box2';
            AdminAccount = 'Admin-Dave_Alexanderson'
        }
    )
}

$domain = $node.DomainName.split('.')[0]
$DCredential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList ("$domain\$($credential.Username)", $Credential.Password)

Group AddADUserToLocalAdminGroup {
    GroupName='Administrators'
    Ensure= 'Present'
    MembersToInclude= "$domain\$($Node.AdminAccount)"
    Credential = $dCredential
    PsDscRunAsCredential = $DCredential
}
```

## <a name="example-3"></a><span data-ttu-id="95b2e-145">Przykład 3</span><span class="sxs-lookup"><span data-stu-id="95b2e-145">Example 3</span></span>

<span data-ttu-id="95b2e-146">Poniższy przykład przedstawia sposób zapewnienia grupą lokalną, TigerTeamAdmins, na serwerze TigerTeamSource.Contoso.Com nie zawiera konta domeny określonego Contoso\JerryG.</span><span class="sxs-lookup"><span data-stu-id="95b2e-146">The following example shows how to ensure a local group, TigerTeamAdmins, on the server TigerTeamSource.Contoso.Com does not contain a particular domain account, Contoso\JerryG.</span></span>

```powershell
Configuration SecureTigerTeamSrouce {
  Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

  Node TigerTeamSource.Contoso.Com {
    Group TigerTeamAdmins {
       GroupName        = 'TigerTeamAdmins'
       Ensure           = 'Present'
       MembersToExclude = "Contoso\JerryG"
    }
  }
}
```