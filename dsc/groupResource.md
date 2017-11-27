---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Zasób grupy DSC"
ms.openlocfilehash: 6fb6c5f9593687d7204ff31fddd9bca978ed2707
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-group-resource"></a><span data-ttu-id="869ce-103">Zasób grupy DSC</span><span class="sxs-lookup"><span data-stu-id="869ce-103">DSC Group Resource</span></span>

> <span data-ttu-id="869ce-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="869ce-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="869ce-105">Grupy zasobów w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm zarządzania grup lokalnych w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="869ce-105">The Group resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="869ce-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="869ce-106">Syntax</span></span>
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

## <a name="properties"></a><span data-ttu-id="869ce-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="869ce-107">Properties</span></span>

|  <span data-ttu-id="869ce-108">Właściwość</span><span class="sxs-lookup"><span data-stu-id="869ce-108">Property</span></span>  |  <span data-ttu-id="869ce-109">Opis</span><span class="sxs-lookup"><span data-stu-id="869ce-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="869ce-110">Nazwa grupy</span><span class="sxs-lookup"><span data-stu-id="869ce-110">GroupName</span></span>| <span data-ttu-id="869ce-111">Nazwa grupy, dla którego chcesz zapewnić z określonym stanem.</span><span class="sxs-lookup"><span data-stu-id="869ce-111">The name of the group for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="869ce-112">Poświadczenie</span><span class="sxs-lookup"><span data-stu-id="869ce-112">Credential</span></span>| <span data-ttu-id="869ce-113">Poświadczenia wymagane do dostępu do zasobów zdalnego.</span><span class="sxs-lookup"><span data-stu-id="869ce-113">The credentials required to access remote resources.</span></span> <span data-ttu-id="869ce-114">**Uwaga**: to konto musi mieć odpowiednich uprawnień usługi Active Directory, aby dodać wszystkie konta innego niż lokalne do grupy; w przeciwnym razie wystąpi błąd, gdy konfiguracja jest wykonywana w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="869ce-114">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error occurs when the configuration is executed on the target node.</span></span>  
| <span data-ttu-id="869ce-115">Opis</span><span class="sxs-lookup"><span data-stu-id="869ce-115">Description</span></span>| <span data-ttu-id="869ce-116">Opis grupy.</span><span class="sxs-lookup"><span data-stu-id="869ce-116">The description of the group.</span></span>| 
| <span data-ttu-id="869ce-117">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="869ce-117">Ensure</span></span>| <span data-ttu-id="869ce-118">Wskazuje, czy dana grupa istnieje.</span><span class="sxs-lookup"><span data-stu-id="869ce-118">Indicates if the group exists.</span></span> <span data-ttu-id="869ce-119">Ustaw tę właściwość na "Brak", aby upewnić się, że grupa nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="869ce-119">Set this property to "Absent" to ensure that the group does not exist.</span></span> <span data-ttu-id="869ce-120">Ustawienie jej "Przedstawienie" (wartość domyślna) zapewnia, że grupa istnieje.</span><span class="sxs-lookup"><span data-stu-id="869ce-120">Setting it to "Present" (the default value) ensures that the group exists.</span></span>| 
| <span data-ttu-id="869ce-121">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="869ce-121">Members</span></span>| <span data-ttu-id="869ce-122">Ta właściwość służy do Zamień od bieżącego członkostwa grupy określone elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="869ce-122">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="869ce-123">Wartość tej właściwości jest tablicą ciągów w postaci *domeny*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="869ce-123">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="869ce-124">Jeśli ta właściwość jest ustawiona w konfiguracji, nie używaj albo **MembersToExclude** lub **MembersToInclude** właściwości.</span><span class="sxs-lookup"><span data-stu-id="869ce-124">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="869ce-125">Dzięki temu generuje błąd.</span><span class="sxs-lookup"><span data-stu-id="869ce-125">Doing so generates an error.</span></span>| 
| <span data-ttu-id="869ce-126">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="869ce-126">MembersToExclude</span></span>| <span data-ttu-id="869ce-127">Ta właściwość służy do usunięcia członków z istniejącego członkostwa grupy.</span><span class="sxs-lookup"><span data-stu-id="869ce-127">Use this property to remove members from the existing membership of the group.</span></span> <span data-ttu-id="869ce-128">Wartość tej właściwości jest tablicą ciągów w postaci *domeny*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="869ce-128">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="869ce-129">Jeśli ta właściwość jest ustawiona w konfiguracji, nie używaj **członków** właściwości.</span><span class="sxs-lookup"><span data-stu-id="869ce-129">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="869ce-130">Dzięki temu generuje błąd.</span><span class="sxs-lookup"><span data-stu-id="869ce-130">Doing so generates an error.</span></span>| 
| <span data-ttu-id="869ce-131">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="869ce-131">MembersToInclude</span></span>| <span data-ttu-id="869ce-132">Ta właściwość służy do dodawania członków do istniejącego członkostwa grupy.</span><span class="sxs-lookup"><span data-stu-id="869ce-132">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="869ce-133">Wartość tej właściwości jest tablicą ciągów w postaci *domeny*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="869ce-133">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="869ce-134">Jeśli ta właściwość jest ustawiona w konfiguracji, nie używaj **członków** właściwości.</span><span class="sxs-lookup"><span data-stu-id="869ce-134">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="869ce-135">W ten sposób spowoduje wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="869ce-135">Doing so will generate an error.</span></span>| 
| <span data-ttu-id="869ce-136">dependsOn</span><span class="sxs-lookup"><span data-stu-id="869ce-136">DependsOn</span></span> | <span data-ttu-id="869ce-137">Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="869ce-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="869ce-138">Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości to "DependsOn ="[ResourceName ResourceType]"".</span><span class="sxs-lookup"><span data-stu-id="869ce-138">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`\`.</span></span>| 

## <a name="example-1"></a><span data-ttu-id="869ce-139">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="869ce-139">Example 1</span></span>

<span data-ttu-id="869ce-140">Poniższy przykład przedstawia sposób upewnić się, że istnieje grupa o nazwie "TestGroup".</span><span class="sxs-lookup"><span data-stu-id="869ce-140">The following example shows how to ensure that a group called "TestGroup" is absent.</span></span> 

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```
## <a name="example-2"></a><span data-ttu-id="869ce-141">Przykład 2</span><span class="sxs-lookup"><span data-stu-id="869ce-141">Example 2</span></span>
<span data-ttu-id="869ce-142">Poniższy przykład przedstawia sposób dodawania użytkownika usługi Active Directory do lokalnej grupy administratorów jako część kompilacji laboratorium wielu maszyny, której korzystasz już z PSCredential dla konta administratora lokalnego.</span><span class="sxs-lookup"><span data-stu-id="869ce-142">The following example shows how to add an Active Directory User to the local administrators group as part of a Multi-Machine Lab build where you are already using a PSCredential for the Local Adminstrator account.</span></span> <span data-ttu-id="869ce-143">To jest również używana do konta administratora domeny (po podwyższenie poziomu domeny) musimy następnie przekonwertować tej PSCredential istniejącej domeny przyjazną poświadczenie, aby umożliwić nam można dodać użytkownika domeny do lokalnej grupy administratorów na serwerze członkowskim, na.</span><span class="sxs-lookup"><span data-stu-id="869ce-143">As this is also used for the Domain Admin Account (after Domain promotion) we then need to convert this existing PSCredential to a Domain Friendly credential to enable us to add a Domain User to the Local Administrators Group on the Member server.</span></span>

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

Group AddADUserToLocalAdminGroup
        {
            GroupName='Administrators'   
            Ensure= 'Present'             
            MembersToInclude= "$domain\$($Node.AdminAccount)"
            Credential = $dCredential    
            PsDscRunAsCredential = $DCredential
        }
```

## <a name="example-3"></a><span data-ttu-id="869ce-144">Przykład 3</span><span class="sxs-lookup"><span data-stu-id="869ce-144">Example 3</span></span>
<span data-ttu-id="869ce-145">Poniższy przykład przedstawia sposób zapewnienia grupą lokalną, TigerTeamAdmins, na serwerze TigerTeamSource.Contoso.Com nie zawiera konta domeny określonego Contoso\JerryG.</span><span class="sxs-lookup"><span data-stu-id="869ce-145">The following example shows how to ensure a local group, TigerTeamAdmins, on the server TigerTeamSource.Contoso.Com does not contain a particular domain account, Contoso\JerryG.</span></span>  

```powershell

Configuration SecureTigerTeamSrouce 
{
  Import-DscResource -ModuleName 'PSDesiredStateConfiguration'
  
  Node TigerTeamSource.Contoso.Com {
  Group TigerTeamAdmins
    {
       GroupName        = 'TigerTeamAdmins'   
       Ensure           = 'Absent'             
       MembersToInclude = "Contoso\JerryG"
    }
  }
}
```

