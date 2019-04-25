---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: DSC dla systemu Linux zasób nxUser
ms.openlocfilehash: 1b02be1559957585a2a1733630cb93440e8182f9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077657"
---
# <a name="dsc-for-linux-nxuser-resource"></a><span data-ttu-id="df1c8-103">DSC dla systemu Linux zasób nxUser</span><span class="sxs-lookup"><span data-stu-id="df1c8-103">DSC for Linux nxUser Resource</span></span>

<span data-ttu-id="df1c8-104">**NxUser** zasób w programie PowerShell Desired State Configuration (DSC) zapewnia mechanizm zarządzania użytkowników lokalnych skonfigurowanych na węzeł systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="df1c8-104">The **nxUser** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local users on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="df1c8-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="df1c8-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="df1c8-106">Właściwości</span><span class="sxs-lookup"><span data-stu-id="df1c8-106">Properties</span></span>

|  <span data-ttu-id="df1c8-107">Właściwość</span><span class="sxs-lookup"><span data-stu-id="df1c8-107">Property</span></span> |  <span data-ttu-id="df1c8-108">Wskazuje nazwę konta, dla którego chcesz zapewnić określonego stanu.</span><span class="sxs-lookup"><span data-stu-id="df1c8-108">Indicates the account name for which you want to ensure a specific state.</span></span> |
|---|---|
| <span data-ttu-id="df1c8-109">UserName</span><span class="sxs-lookup"><span data-stu-id="df1c8-109">UserName</span></span>| <span data-ttu-id="df1c8-110">Określa lokalizację, w którym chcesz upewnić się, stan dla pliku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="df1c8-110">Specifies the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="df1c8-111">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="df1c8-111">Ensure</span></span>| <span data-ttu-id="df1c8-112">Określa, czy konto istnieje.</span><span class="sxs-lookup"><span data-stu-id="df1c8-112">Specifies whether the account exists.</span></span> <span data-ttu-id="df1c8-113">Ustaw tę właściwość na "Obecny", aby upewnić się, że konto istnieje i ustaw go na "Brak", aby upewnić się, że konto nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="df1c8-113">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>|
| <span data-ttu-id="df1c8-114">Imię i nazwisko</span><span class="sxs-lookup"><span data-stu-id="df1c8-114">FullName</span></span>| <span data-ttu-id="df1c8-115">Ciąg, który zawiera pełną nazwę konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="df1c8-115">A string that contains the full name to use for the user account.</span></span>|
| <span data-ttu-id="df1c8-116">Opis</span><span class="sxs-lookup"><span data-stu-id="df1c8-116">Description</span></span>| <span data-ttu-id="df1c8-117">Opis konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="df1c8-117">The description for the user account.</span></span>|
| <span data-ttu-id="df1c8-118">Hasło</span><span class="sxs-lookup"><span data-stu-id="df1c8-118">Password</span></span>| <span data-ttu-id="df1c8-119">Skrót hasła użytkownika w odpowiednim formularzu komputera z systemem Linux.</span><span class="sxs-lookup"><span data-stu-id="df1c8-119">The hash of the users password in the appropriate form for the Linux computer.</span></span> <span data-ttu-id="df1c8-120">Zazwyczaj jest to solone algorytmu SHA-256 lub wyznaczania wartości skrótu SHA-512.</span><span class="sxs-lookup"><span data-stu-id="df1c8-120">Typically, this is a salted SHA-256, or SHA-512 hash.</span></span> <span data-ttu-id="df1c8-121">W systemie Debian i Ubuntu Linux ta wartość może zostać wygenerowany za pomocą polecenia mkpasswd.</span><span class="sxs-lookup"><span data-stu-id="df1c8-121">On Debian and Ubuntu Linux, this value can be generated with the mkpasswd command.</span></span> <span data-ttu-id="df1c8-122">Inne dystrybucje systemu Linux metoda crypt biblioteki kryptograficznego języka Python może służyć do generowania skrótów.</span><span class="sxs-lookup"><span data-stu-id="df1c8-122">For other Linux distros, the crypt method of Python’s Crypt library can be used to generate the hash.</span></span>|
| <span data-ttu-id="df1c8-123">Wyłącz</span><span class="sxs-lookup"><span data-stu-id="df1c8-123">Disabled</span></span>| <span data-ttu-id="df1c8-124">Wskazuje, czy konto jest włączone.</span><span class="sxs-lookup"><span data-stu-id="df1c8-124">Indicates whether the account is enabled.</span></span> <span data-ttu-id="df1c8-125">Ustaw tę właściwość na **$true** aby upewnić się, że to konto jest wyłączone i ustaw ją na **$false** aby upewnić się, że jest włączone.</span><span class="sxs-lookup"><span data-stu-id="df1c8-125">Set this property to **$true** to ensure that this account is disabled, and set it to **$false** to ensure that it is enabled.</span></span>|
| <span data-ttu-id="df1c8-126">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="df1c8-126">PasswordChangeRequired</span></span>| <span data-ttu-id="df1c8-127">Wskazuje, czy użytkownik może zmienić hasła.</span><span class="sxs-lookup"><span data-stu-id="df1c8-127">Indicates whether the user can change the password.</span></span> <span data-ttu-id="df1c8-128">Ustaw tę właściwość na **$true** aby upewnić się, że użytkownik nie może zmienić hasło i ustaw ją na **$false** umożliwia użytkownikowi zmianę hasła.</span><span class="sxs-lookup"><span data-stu-id="df1c8-128">Set this property to **$true** to ensure that the user cannot change the password, and set it to **$false** to allow the user to change the password.</span></span> <span data-ttu-id="df1c8-129">Wartość domyślna to **$false**.</span><span class="sxs-lookup"><span data-stu-id="df1c8-129">The default value is **$false**.</span></span> <span data-ttu-id="df1c8-130">Ta właściwość jest oceniane tylko, jeśli konto użytkownika nie istniał wcześniej i jest tworzona.</span><span class="sxs-lookup"><span data-stu-id="df1c8-130">This property is only evaluated if the user account did not exist previously and is being created.</span></span>|
| <span data-ttu-id="df1c8-131">HomeDirectory</span><span class="sxs-lookup"><span data-stu-id="df1c8-131">HomeDirectory</span></span>| <span data-ttu-id="df1c8-132">Katalog macierzysty dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="df1c8-132">The home directory for the user.</span></span>|
| <span data-ttu-id="df1c8-133">Identyfikator grupy</span><span class="sxs-lookup"><span data-stu-id="df1c8-133">GroupID</span></span>| <span data-ttu-id="df1c8-134">Identyfikator grupy głównej dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="df1c8-134">The primary group ID for the user.</span></span>|
| <span data-ttu-id="df1c8-135">dependsOn</span><span class="sxs-lookup"><span data-stu-id="df1c8-135">DependsOn</span></span> | <span data-ttu-id="df1c8-136">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="df1c8-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="df1c8-137">Na przykład, jeśli identyfikator bloku skryptu konfiguracji zasobu, który chcesz uruchomić najpierw jest "ResourceName" i jego typem jest "ResourceType", składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="df1c8-137">For example, if the ID of the resource configuration script block that you want to run first is "ResourceName" and its type is "ResourceType", the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="df1c8-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="df1c8-138">Example</span></span>

<span data-ttu-id="df1c8-139">Poniższy przykład zapewnia, że użytkownik "monuser" istnieje i jest członkiem grupy "DBusers".</span><span class="sxs-lookup"><span data-stu-id="df1c8-139">The following example ensures that the user "monuser" exists and is a member of the group "DBusers".</span></span>

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