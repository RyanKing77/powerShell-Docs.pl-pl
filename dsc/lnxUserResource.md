---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "DSC dla systemu Linux nxUser zasobów"
ms.openlocfilehash: 93e2b12af076fce687e045e3043c94fa82d61861
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-for-linux-nxuser-resource"></a><span data-ttu-id="772d9-103">DSC dla systemu Linux nxUser zasobów</span><span class="sxs-lookup"><span data-stu-id="772d9-103">DSC for Linux nxUser Resource</span></span>

<span data-ttu-id="772d9-104">**NxUser** zasób w PowerShell żądanego stanu konfiguracji (DSC) zapewnia mechanizm do zarządzania użytkowników lokalnych w węźle systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="772d9-104">The **nxUser** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage local users on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="772d9-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="772d9-105">Syntax</span></span>

```
nxUser <string> #ResourceName
{
    UserName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="772d9-106">Właściwości</span><span class="sxs-lookup"><span data-stu-id="772d9-106">Properties</span></span>

|  <span data-ttu-id="772d9-107">Właściwość</span><span class="sxs-lookup"><span data-stu-id="772d9-107">Property</span></span> |  <span data-ttu-id="772d9-108">Wskazuje nazwę konta, dla którego chcesz zapewnić z określonym stanem.</span><span class="sxs-lookup"><span data-stu-id="772d9-108">Indicates the account name for which you want to ensure a specific state.</span></span> | 
|---|---|
| <span data-ttu-id="772d9-109">UserName</span><span class="sxs-lookup"><span data-stu-id="772d9-109">UserName</span></span>| <span data-ttu-id="772d9-110">Określa lokalizację, w której chcesz zapewnić stan pliku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="772d9-110">Specifies the location where you want to ensure the state for a file or directory.</span></span>| 
| <span data-ttu-id="772d9-111">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="772d9-111">Ensure</span></span>| <span data-ttu-id="772d9-112">Określa, czy konto istnieje.</span><span class="sxs-lookup"><span data-stu-id="772d9-112">Specifies whether the account exists.</span></span> <span data-ttu-id="772d9-113">Ustaw tę właściwość na "Brak", aby upewnić się, że konto istnieje i ustaw ją na "Brak", aby upewnić się, że konto nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="772d9-113">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>| 
| <span data-ttu-id="772d9-114">Imię i nazwisko</span><span class="sxs-lookup"><span data-stu-id="772d9-114">FullName</span></span>| <span data-ttu-id="772d9-115">Ciąg, który zawiera pełną nazwę dla konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="772d9-115">A string that contains the full name to use for the user account.</span></span>| 
| <span data-ttu-id="772d9-116">Opis</span><span class="sxs-lookup"><span data-stu-id="772d9-116">Description</span></span>| <span data-ttu-id="772d9-117">Opis konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="772d9-117">The description for the user account.</span></span>| 
| <span data-ttu-id="772d9-118">Hasło</span><span class="sxs-lookup"><span data-stu-id="772d9-118">Password</span></span>| <span data-ttu-id="772d9-119">Skrót hasła użytkownika w postaci odpowiednie dla tego komputera.</span><span class="sxs-lookup"><span data-stu-id="772d9-119">The hash of the users password in the appropriate form for the Linux computer.</span></span> <span data-ttu-id="772d9-120">Zazwyczaj jest to solone algorytmu SHA-256 lub wyznaczania wartości skrótu SHA-512.</span><span class="sxs-lookup"><span data-stu-id="772d9-120">Typically, this is a salted SHA-256, or SHA-512 hash.</span></span> <span data-ttu-id="772d9-121">Debian i Ubuntu Linux tę wartość można wygenerować za pomocą polecenia mkpasswd.</span><span class="sxs-lookup"><span data-stu-id="772d9-121">On Debian and Ubuntu Linux, this value can be generated with the mkpasswd command.</span></span> <span data-ttu-id="772d9-122">Dla innych dystrybucjach systemu Linux można wygenerować skrót metoda crypt biblioteki Crypt języka Python.</span><span class="sxs-lookup"><span data-stu-id="772d9-122">For other Linux distros, the crypt method of Python’s Crypt library can be used to generate the hash.</span></span>| 
| <span data-ttu-id="772d9-123">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="772d9-123">Disabled</span></span>| <span data-ttu-id="772d9-124">Wskazuje, czy konto jest włączone.</span><span class="sxs-lookup"><span data-stu-id="772d9-124">Indicates whether the account is enabled.</span></span> <span data-ttu-id="772d9-125">Ta właściwość jest ustawiana **$true** aby upewnić się, że to konto jest wyłączone i ustaw ją na **$false** aby upewnić się, że jest włączone.</span><span class="sxs-lookup"><span data-stu-id="772d9-125">Set this property to **$true** to ensure that this account is disabled, and set it to **$false** to ensure that it is enabled.</span></span>| 
| <span data-ttu-id="772d9-126">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="772d9-126">PasswordChangeRequired</span></span>| <span data-ttu-id="772d9-127">Wskazuje, czy użytkownik może zmienić hasło.</span><span class="sxs-lookup"><span data-stu-id="772d9-127">Indicates whether the user can change the password.</span></span> <span data-ttu-id="772d9-128">Ta właściwość jest ustawiana **$true** aby upewnić się, że użytkownik nie można zmienić hasło i ustaw ją na **$false** umożliwia użytkownikowi zmianę hasła.</span><span class="sxs-lookup"><span data-stu-id="772d9-128">Set this property to **$true** to ensure that the user cannot change the password, and set it to **$false** to allow the user to change the password.</span></span> <span data-ttu-id="772d9-129">Wartość domyślna to **$false**.</span><span class="sxs-lookup"><span data-stu-id="772d9-129">The default value is **$false**.</span></span> <span data-ttu-id="772d9-130">Ta właściwość jest oceniana tylko wtedy, jeśli konto użytkownika nie istniał wcześniej i jest tworzona.</span><span class="sxs-lookup"><span data-stu-id="772d9-130">This property is only evaluated if the user account did not exist previously and is being created.</span></span>| 
| <span data-ttu-id="772d9-131">Parametr Katalog_macierzysty</span><span class="sxs-lookup"><span data-stu-id="772d9-131">HomeDirectory</span></span>| <span data-ttu-id="772d9-132">Katalogu macierzystego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="772d9-132">The home directory for the user.</span></span>| 
| <span data-ttu-id="772d9-133">Identyfikator grupy</span><span class="sxs-lookup"><span data-stu-id="772d9-133">GroupID</span></span>| <span data-ttu-id="772d9-134">Identyfikator grupy podstawowej dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="772d9-134">The primary group ID for the user.</span></span>| 
| <span data-ttu-id="772d9-135">dependsOn</span><span class="sxs-lookup"><span data-stu-id="772d9-135">DependsOn</span></span> | <span data-ttu-id="772d9-136">Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="772d9-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="772d9-137">Na przykład jeśli identyfikator bloku skryptu konfiguracji zasobu, który chcesz uruchomić jest najpierw "ResourceName", jego typ to "Typu zasobu" Składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="772d9-137">For example, if the ID of the resource configuration script block that you want to run first is "ResourceName" and its type is "ResourceType", the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="772d9-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="772d9-138">Example</span></span>

<span data-ttu-id="772d9-139">Poniższy przykład gwarantuje, że użytkownik "monuser" istnieje i jest członkiem grupy "DBusers".</span><span class="sxs-lookup"><span data-stu-id="772d9-139">The following example ensures that the user "monuser" exists and is a member of the group "DBusers".</span></span>

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

