---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Zasób użytkownika DSC"
ms.openlocfilehash: a4e4e8af4fcfe5c997c460613174d8583261dedf
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
#<a name="dsc-user-resource"></a><span data-ttu-id="4e3c7-103">Zasób użytkownika DSC #</span><span class="sxs-lookup"><span data-stu-id="4e3c7-103">DSC User Resource#</span></span>

 
><span data-ttu-id="4e3c7-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4e3c7-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="4e3c7-105">__Użytkownika__ zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm zarządzania kont użytkowników lokalnych w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="4e3c7-105">The __User__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local user accounts on the target node.</span></span>


##<a name="syntax"></a><span data-ttu-id="4e3c7-106">Składnia ##</span><span class="sxs-lookup"><span data-stu-id="4e3c7-106">Syntax##</span></span>

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

## <a name="properties"></a><span data-ttu-id="4e3c7-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="4e3c7-107">Properties</span></span>
|  <span data-ttu-id="4e3c7-108">Właściwość</span><span class="sxs-lookup"><span data-stu-id="4e3c7-108">Property</span></span>  |  <span data-ttu-id="4e3c7-109">Opis</span><span class="sxs-lookup"><span data-stu-id="4e3c7-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="4e3c7-110">UserName</span><span class="sxs-lookup"><span data-stu-id="4e3c7-110">UserName</span></span>| <span data-ttu-id="4e3c7-111">Wskazuje nazwę konta, dla którego chcesz zapewnić z określonym stanem.</span><span class="sxs-lookup"><span data-stu-id="4e3c7-111">Indicates the account name for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="4e3c7-112">Opis</span><span class="sxs-lookup"><span data-stu-id="4e3c7-112">Description</span></span>| <span data-ttu-id="4e3c7-113">Określa opis, który ma być używany dla konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4e3c7-113">Indicates the description you want to use for the user account.</span></span>| 
| <span data-ttu-id="4e3c7-114">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="4e3c7-114">Disabled</span></span>| <span data-ttu-id="4e3c7-115">Wskazuje, czy konto jest włączone.</span><span class="sxs-lookup"><span data-stu-id="4e3c7-115">Indicates if the account is enabled.</span></span> <span data-ttu-id="4e3c7-116">Ta właściwość jest ustawiana __$true__ aby upewnić się, że to konto jest wyłączone i ustaw ją na __$false__ aby upewnić się, że jest włączone.</span><span class="sxs-lookup"><span data-stu-id="4e3c7-116">Set this property to __$true__ to ensure that this account is disabled, and set it to __$false__ to ensure that it is enabled.</span></span>| 
| <span data-ttu-id="4e3c7-117">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="4e3c7-117">Ensure</span></span>| <span data-ttu-id="4e3c7-118">Wskazuje, czy konto istnieje.</span><span class="sxs-lookup"><span data-stu-id="4e3c7-118">Indicates if the account exists.</span></span> <span data-ttu-id="4e3c7-119">Ustaw tę właściwość na "Brak", aby upewnić się, że konto istnieje i ustaw ją na "Brak", aby upewnić się, że konto nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="4e3c7-119">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>| 
| <span data-ttu-id="4e3c7-120">Imię i nazwisko</span><span class="sxs-lookup"><span data-stu-id="4e3c7-120">FullName</span></span>| <span data-ttu-id="4e3c7-121">Określa ciąg z pełną nazwę, który ma być używany dla konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4e3c7-121">Represents a string with the full name you want to use for the user account.</span></span>| 
| <span data-ttu-id="4e3c7-122">Hasło</span><span class="sxs-lookup"><span data-stu-id="4e3c7-122">Password</span></span>| <span data-ttu-id="4e3c7-123">Wskazuje hasło, którego chcesz użyć dla tego konta.</span><span class="sxs-lookup"><span data-stu-id="4e3c7-123">Indicates the password you want to use for this account.</span></span> | 
| <span data-ttu-id="4e3c7-124">PasswordChangeNotAllowed</span><span class="sxs-lookup"><span data-stu-id="4e3c7-124">PasswordChangeNotAllowed</span></span>| <span data-ttu-id="4e3c7-125">Wskazuje, czy użytkownik może zmienić hasło.</span><span class="sxs-lookup"><span data-stu-id="4e3c7-125">Indicates if the user can change the password.</span></span> <span data-ttu-id="4e3c7-126">Ta właściwość jest ustawiana __$true__ aby upewnić się, że użytkownik nie można zmienić hasło i ustaw ją na __$false__ umożliwia użytkownikowi zmianę hasła.</span><span class="sxs-lookup"><span data-stu-id="4e3c7-126">Set this property to __$true__ to ensure that the user cannot change the password, and set it to __$false__ to allow the user to change the password.</span></span> <span data-ttu-id="4e3c7-127">Wartość domyślna to __$false__.</span><span class="sxs-lookup"><span data-stu-id="4e3c7-127">The default value is __$false__.</span></span>| 
| <span data-ttu-id="4e3c7-128">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="4e3c7-128">PasswordChangeRequired</span></span>| <span data-ttu-id="4e3c7-129">Wskazuje, czy użytkownik musi zmienić hasło przy następnym logowaniu.</span><span class="sxs-lookup"><span data-stu-id="4e3c7-129">Indicates if the user must change the password at the next sign in.</span></span> <span data-ttu-id="4e3c7-130">Ta właściwość jest ustawiana __$true__ Jeśli użytkownik musi zmienić hasło.</span><span class="sxs-lookup"><span data-stu-id="4e3c7-130">Set this property to __$true__ if the user must change the password.</span></span> <span data-ttu-id="4e3c7-131">Wartość domyślna to __$true__.</span><span class="sxs-lookup"><span data-stu-id="4e3c7-131">The default value is __$true__.</span></span>| 
| <span data-ttu-id="4e3c7-132">PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="4e3c7-132">PasswordNeverExpires</span></span>| <span data-ttu-id="4e3c7-133">Wskazuje, czy hasło wygaśnie.</span><span class="sxs-lookup"><span data-stu-id="4e3c7-133">Indicates if the password will expire.</span></span> <span data-ttu-id="4e3c7-134">Aby upewnić się, że hasło dla tego konta nigdy nie wygasa, ustawić tę właściwość na __$true__i ustaw ją na __$false__ Jeśli hasło wygaśnie.</span><span class="sxs-lookup"><span data-stu-id="4e3c7-134">To ensure that the password for this account will never expire, set this property to __$true__, and set it to __$false__ if the password will expire.</span></span> <span data-ttu-id="4e3c7-135">Wartość domyślna to __$false__.</span><span class="sxs-lookup"><span data-stu-id="4e3c7-135">The default value is __$false__.</span></span>| 
| <span data-ttu-id="4e3c7-136">dependsOn</span><span class="sxs-lookup"><span data-stu-id="4e3c7-136">DependsOn</span></span> | <span data-ttu-id="4e3c7-137">Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="4e3c7-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="4e3c7-138">Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="4e3c7-138">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="4e3c7-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="4e3c7-139">Example</span></span>

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```

