---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób DSC użytkownika
ms.openlocfilehash: 04543351df19160a2da05ccea96e5d392d8c55bf
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048569"
---
# <a name="dsc-user-resource"></a><span data-ttu-id="7a8d5-103">Zasób DSC użytkownika</span><span class="sxs-lookup"><span data-stu-id="7a8d5-103">DSC User Resource</span></span>

<span data-ttu-id="7a8d5-104">Dotyczy: Program Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7a8d5-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="7a8d5-105">**Użytkownika** zasób w Windows PowerShell Desired State Configuration (DSC) zapewnia mechanizm zarządzania kont użytkowników lokalnych w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="7a8d5-105">The **User** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local user accounts on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="7a8d5-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="7a8d5-106">Syntax</span></span>

```
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="7a8d5-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="7a8d5-107">Properties</span></span>

|  <span data-ttu-id="7a8d5-108">Właściwość</span><span class="sxs-lookup"><span data-stu-id="7a8d5-108">Property</span></span>  |  <span data-ttu-id="7a8d5-109">Opis</span><span class="sxs-lookup"><span data-stu-id="7a8d5-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="7a8d5-110">UserName</span><span class="sxs-lookup"><span data-stu-id="7a8d5-110">UserName</span></span>| <span data-ttu-id="7a8d5-111">Wskazuje nazwę konta, dla którego chcesz zapewnić określonego stanu.</span><span class="sxs-lookup"><span data-stu-id="7a8d5-111">Indicates the account name for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="7a8d5-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7a8d5-112">Description</span></span>| <span data-ttu-id="7a8d5-113">Określa opis, który ma być używana dla konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7a8d5-113">Indicates the description you want to use for the user account.</span></span>|
| <span data-ttu-id="7a8d5-114">Wyłącz</span><span class="sxs-lookup"><span data-stu-id="7a8d5-114">Disabled</span></span>| <span data-ttu-id="7a8d5-115">Wskazuje, czy konto jest włączone.</span><span class="sxs-lookup"><span data-stu-id="7a8d5-115">Indicates if the account is enabled.</span></span> <span data-ttu-id="7a8d5-116">Ustaw tę właściwość na `$true` aby upewnić się, że to konto jest wyłączone i ustaw ją na `$false` aby upewnić się, że jest włączone.</span><span class="sxs-lookup"><span data-stu-id="7a8d5-116">Set this property to `$true` to ensure that this account is disabled, and set it to `$false` to ensure that it is enabled.</span></span>|
| <span data-ttu-id="7a8d5-117">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="7a8d5-117">Ensure</span></span>| <span data-ttu-id="7a8d5-118">Wskazuje, czy konto istnieje.</span><span class="sxs-lookup"><span data-stu-id="7a8d5-118">Indicates if the account exists.</span></span> <span data-ttu-id="7a8d5-119">Ustaw tę właściwość na "Obecny", aby upewnić się, że konto istnieje i ustaw go na "Brak", aby upewnić się, że konto nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="7a8d5-119">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>|
| <span data-ttu-id="7a8d5-120">Imię i nazwisko</span><span class="sxs-lookup"><span data-stu-id="7a8d5-120">FullName</span></span>| <span data-ttu-id="7a8d5-121">Określa ciąg pełną nazwą, który ma być używana dla konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7a8d5-121">Represents a string with the full name you want to use for the user account.</span></span>|
| <span data-ttu-id="7a8d5-122">Hasło</span><span class="sxs-lookup"><span data-stu-id="7a8d5-122">Password</span></span>| <span data-ttu-id="7a8d5-123">Wskazuje hasło, którego chcesz użyć dla tego konta.</span><span class="sxs-lookup"><span data-stu-id="7a8d5-123">Indicates the password you want to use for this account.</span></span> |
| <span data-ttu-id="7a8d5-124">PasswordChangeNotAllowed</span><span class="sxs-lookup"><span data-stu-id="7a8d5-124">PasswordChangeNotAllowed</span></span>| <span data-ttu-id="7a8d5-125">Wskazuje, jeśli użytkownik może zmienić hasła.</span><span class="sxs-lookup"><span data-stu-id="7a8d5-125">Indicates if the user can change the password.</span></span> <span data-ttu-id="7a8d5-126">Ustaw tę właściwość na `$true` aby upewnić się, że użytkownik nie może zmienić hasło i ustaw ją na `$false` umożliwia użytkownikowi zmianę hasła.</span><span class="sxs-lookup"><span data-stu-id="7a8d5-126">Set this property to `$true` to ensure that the user cannot change the password, and set it to `$false` to allow the user to change the password.</span></span> <span data-ttu-id="7a8d5-127">Wartość domyślna to `$false`.</span><span class="sxs-lookup"><span data-stu-id="7a8d5-127">The default value is `$false`.</span></span>|
| <span data-ttu-id="7a8d5-128">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="7a8d5-128">PasswordChangeRequired</span></span>| <span data-ttu-id="7a8d5-129">Wskazuje, jeśli użytkownik musi zmienić hasło podczas następnego logowania.</span><span class="sxs-lookup"><span data-stu-id="7a8d5-129">Indicates if the user must change the password at the next sign in.</span></span> <span data-ttu-id="7a8d5-130">Ustaw tę właściwość na `$true` Jeśli użytkownik musi zmienić hasło.</span><span class="sxs-lookup"><span data-stu-id="7a8d5-130">Set this property to `$true` if the user must change the password.</span></span> <span data-ttu-id="7a8d5-131">Wartość domyślna to `$true`.</span><span class="sxs-lookup"><span data-stu-id="7a8d5-131">The default value is `$true`.</span></span>|
| <span data-ttu-id="7a8d5-132">PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="7a8d5-132">PasswordNeverExpires</span></span>| <span data-ttu-id="7a8d5-133">Wskazuje, jeśli hasło wygaśnie.</span><span class="sxs-lookup"><span data-stu-id="7a8d5-133">Indicates if the password will expire.</span></span> <span data-ttu-id="7a8d5-134">Aby upewnić się, że hasło dla tego konta nigdy nie wygasa, ustaw tę właściwość na `$true`i ustaw ją na `$false` Jeśli hasło wygaśnie.</span><span class="sxs-lookup"><span data-stu-id="7a8d5-134">To ensure that the password for this account will never expire, set this property to `$true`, and set it to `$false` if the password will expire.</span></span> <span data-ttu-id="7a8d5-135">Wartość domyślna to `$false`.</span><span class="sxs-lookup"><span data-stu-id="7a8d5-135">The default value is `$false`.</span></span>|
| <span data-ttu-id="7a8d5-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7a8d5-136">DependsOn</span></span> | <span data-ttu-id="7a8d5-137">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="7a8d5-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7a8d5-138">Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest **ResourceName** a jej typ jest **ResourceType**, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="7a8d5-138">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="7a8d5-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="7a8d5-139">Example</span></span>

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```