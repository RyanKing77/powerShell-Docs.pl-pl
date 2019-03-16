---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób DSC grupy
ms.openlocfilehash: 123e09b54a923af942a15f80fa7291c555b4235f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054972"
---
# <a name="dsc-group-resource"></a><span data-ttu-id="f4646-103">Zasób DSC grupy</span><span class="sxs-lookup"><span data-stu-id="f4646-103">DSC Group Resource</span></span>

> <span data-ttu-id="f4646-104">Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f4646-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="f4646-105">Zasób grupy w Windows PowerShell Desired State Configuration (DSC) udostępnia mechanizm do zarządzania grupami lokalnymi w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="f4646-105">The Group resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="f4646-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="f4646-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="f4646-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="f4646-107">Properties</span></span>

|  <span data-ttu-id="f4646-108">Właściwość</span><span class="sxs-lookup"><span data-stu-id="f4646-108">Property</span></span>  |  <span data-ttu-id="f4646-109">Opis</span><span class="sxs-lookup"><span data-stu-id="f4646-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="f4646-110">GroupName</span><span class="sxs-lookup"><span data-stu-id="f4646-110">GroupName</span></span>| <span data-ttu-id="f4646-111">Nazwa grupy, dla którego chcesz zapewnić określonego stanu.</span><span class="sxs-lookup"><span data-stu-id="f4646-111">The name of the group for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="f4646-112">Poświadczenie</span><span class="sxs-lookup"><span data-stu-id="f4646-112">Credential</span></span>| <span data-ttu-id="f4646-113">Poświadczenia wymagane do dostępu do zasobów zdalnych.</span><span class="sxs-lookup"><span data-stu-id="f4646-113">The credentials required to access remote resources.</span></span> <span data-ttu-id="f4646-114">**Uwaga**: To konto musi mieć odpowiednie uprawnienia usługi Active Directory, aby dodać wszystkie konta innego niż lokalne grupy; w przeciwnym razie wystąpi błąd, gdy konfiguracja jest wykonywana w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="f4646-114">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error occurs when the configuration is executed on the target node.</span></span>
| <span data-ttu-id="f4646-115">Opis</span><span class="sxs-lookup"><span data-stu-id="f4646-115">Description</span></span>| <span data-ttu-id="f4646-116">Opis grupy.</span><span class="sxs-lookup"><span data-stu-id="f4646-116">The description of the group.</span></span>|
| <span data-ttu-id="f4646-117">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="f4646-117">Ensure</span></span>| <span data-ttu-id="f4646-118">Wskazuje, czy grupa istnieje.</span><span class="sxs-lookup"><span data-stu-id="f4646-118">Indicates if the group exists.</span></span> <span data-ttu-id="f4646-119">Ustaw tę właściwość na "Brak", aby upewnić się, że grupa nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="f4646-119">Set this property to "Absent" to ensure that the group does not exist.</span></span> <span data-ttu-id="f4646-120">Ustawienie "Przedstawia" (wartość domyślna) gwarantuje, czy grupa istnieje.</span><span class="sxs-lookup"><span data-stu-id="f4646-120">Setting it to "Present" (the default value) ensures that the group exists.</span></span>|
| <span data-ttu-id="f4646-121">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="f4646-121">Members</span></span>| <span data-ttu-id="f4646-122">Użyj tej właściwości, aby zamienić bieżącego członkostwa w grupie z tymi elementami.</span><span class="sxs-lookup"><span data-stu-id="f4646-122">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="f4646-123">Wartość tej właściwości jest tablicą ciągów formularza *domeny*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="f4646-123">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="f4646-124">Jeśli ta właściwość jest ustawiona w konfiguracji, nie używaj albo **MembersToExclude** lub **MembersToInclude** właściwości.</span><span class="sxs-lookup"><span data-stu-id="f4646-124">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="f4646-125">Ten sposób spowoduje wygenerowanie błędu.</span><span class="sxs-lookup"><span data-stu-id="f4646-125">Doing so generates an error.</span></span>|
| <span data-ttu-id="f4646-126">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="f4646-126">MembersToExclude</span></span>| <span data-ttu-id="f4646-127">Ta właściwość służy do usuwania członków z istniejących członkostwa w grupie.</span><span class="sxs-lookup"><span data-stu-id="f4646-127">Use this property to remove members from the existing membership of the group.</span></span> <span data-ttu-id="f4646-128">Wartość tej właściwości jest tablicą ciągów formularza *domeny*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="f4646-128">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="f4646-129">Jeśli ustawisz tę właściwość w ramach konfiguracji należy używać **członków** właściwości.</span><span class="sxs-lookup"><span data-stu-id="f4646-129">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="f4646-130">Ten sposób spowoduje wygenerowanie błędu.</span><span class="sxs-lookup"><span data-stu-id="f4646-130">Doing so generates an error.</span></span>|
| <span data-ttu-id="f4646-131">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="f4646-131">MembersToInclude</span></span>| <span data-ttu-id="f4646-132">Aby dodać członków do istniejących członkostwa w grupie, należy używać tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="f4646-132">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="f4646-133">Wartość tej właściwości jest tablicą ciągów formularza *domeny*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="f4646-133">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="f4646-134">Jeśli ustawisz tę właściwość w ramach konfiguracji należy używać **członków** właściwości.</span><span class="sxs-lookup"><span data-stu-id="f4646-134">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="f4646-135">Ten sposób spowoduje wygenerowanie błędu.</span><span class="sxs-lookup"><span data-stu-id="f4646-135">Doing so will generate an error.</span></span>|
| <span data-ttu-id="f4646-136">dependsOn</span><span class="sxs-lookup"><span data-stu-id="f4646-136">DependsOn</span></span> | <span data-ttu-id="f4646-137">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="f4646-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f4646-138">Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest __ResourceName__ a jej typ jest __ResourceType__, składnia przy użyciu tej właściwości to "DependsOn ="[ ResourceName ResourceType]"".</span><span class="sxs-lookup"><span data-stu-id="f4646-138">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example-1"></a><span data-ttu-id="f4646-139">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="f4646-139">Example 1</span></span>

<span data-ttu-id="f4646-140">Poniższy przykład przedstawia sposób upewnij się, że grupa o nazwie "Grupatestowa" nieobecny.</span><span class="sxs-lookup"><span data-stu-id="f4646-140">The following example shows how to ensure that a group called "TestGroup" is absent.</span></span>

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2"></a><span data-ttu-id="f4646-141">Przykład 2</span><span class="sxs-lookup"><span data-stu-id="f4646-141">Example 2</span></span>

<span data-ttu-id="f4646-142">Poniższy przykład pokazuje, jak dodać użytkowników usługi Active Directory do lokalnej grupy administratorów, jako część kompilacji laboratorium wielu maszyn, których już używasz obiektu PSCredential dla konta administratora lokalnego.</span><span class="sxs-lookup"><span data-stu-id="f4646-142">The following example shows how to add an Active Directory User to the local administrators group as part of a Multi-Machine Lab build where you are already using a PSCredential for the Local Administrator account.</span></span>
<span data-ttu-id="f4646-143">Ponieważ jest on również używany dla konta administratora domeny (po promocji domeny), następnie należy przekonwertować tej PSCredential istniejących poświadczeń domeny przyjazna.</span><span class="sxs-lookup"><span data-stu-id="f4646-143">As this is also used for the Domain Admin Account (after Domain promotion), we then need to convert this existing PSCredential to a Domain Friendly credential.</span></span>
<span data-ttu-id="f4646-144">Następnie możemy dodać użytkownika domeny do lokalnej grupy administratorów na serwerze członkowskim.</span><span class="sxs-lookup"><span data-stu-id="f4646-144">Then we can add a Domain User to the Local Administrators Group on the Member server.</span></span>

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

## <a name="example-3"></a><span data-ttu-id="f4646-145">Przykład 3</span><span class="sxs-lookup"><span data-stu-id="f4646-145">Example 3</span></span>

<span data-ttu-id="f4646-146">Poniższy przykład pokazuje, jak upewnić się, to grupa lokalna TigerTeamAdmins, na serwerze TigerTeamSource.Contoso.Com nie zawiera konta domeny określonego Contoso\JerryG.</span><span class="sxs-lookup"><span data-stu-id="f4646-146">The following example shows how to ensure a local group, TigerTeamAdmins, on the server TigerTeamSource.Contoso.Com does not contain a particular domain account, Contoso\JerryG.</span></span>

```powershell
Configuration SecureTigerTeamSource {
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