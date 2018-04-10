---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galeria, programu powershell, polecenia cmdlet, psget
title: Znajdź RoleCapability
ms.openlocfilehash: 89aacd604d54f6a5e9752790be65cc3bcc77c8e1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="find-rolecapability"></a><span data-ttu-id="09d5f-103">Znajdź RoleCapability</span><span class="sxs-lookup"><span data-stu-id="09d5f-103">Find-RoleCapability</span></span>

<span data-ttu-id="09d5f-104">Znajduje rolę funkcji w modułach.</span><span class="sxs-lookup"><span data-stu-id="09d5f-104">Finds role capabilities in modules.</span></span>

## <a name="description"></a><span data-ttu-id="09d5f-105">Opis</span><span class="sxs-lookup"><span data-stu-id="09d5f-105">Description</span></span>
<span data-ttu-id="09d5f-106">Polecenia cmdlet Find RoleCapability znajduje możliwości roli programu PowerShell w modułach.</span><span class="sxs-lookup"><span data-stu-id="09d5f-106">The Find-RoleCapability cmdlet finds PowerShell role capabilities in modules.</span></span> <span data-ttu-id="09d5f-107">Znajdź RoleCapability wyszukuje modułów w zarejestrowany repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="09d5f-107">Find-RoleCapability searches modules in registered repositories.</span></span>
<span data-ttu-id="09d5f-108">Dla każdej funkcji roli wyszukującą to polecenie cmdlet zwraca obiekt PSGetRoleCapabilityInfo.</span><span class="sxs-lookup"><span data-stu-id="09d5f-108">For each role capability that this cmdlet finds, it returns a PSGetRoleCapabilityInfo object.</span></span> <span data-ttu-id="09d5f-109">Obiekt PSGetRoleCapabilityInfo można przekazać do polecenia cmdlet Install-Module zainstalować moduł, który zawiera możliwości roli.</span><span class="sxs-lookup"><span data-stu-id="09d5f-109">You can pass a PSGetRoleCapabilityInfo object to the Install-Module cmdlet to install the module that contains the role capability.</span></span>
<span data-ttu-id="09d5f-110">Możliwości roli programu PowerShell definiują, które polecenia, aplikacji i tak dalej są dostępne dla użytkownika w punkcie końcowym tylko tyle administracyjnej (JEA).</span><span class="sxs-lookup"><span data-stu-id="09d5f-110">PowerShell role capabilities define which commands, applications, and so on are available to a user at a Just Enough Administration (JEA) endpoint.</span></span> <span data-ttu-id="09d5f-111">Możliwości roli są definiowane przez pliki z rozszerzeniem .psrc.</span><span class="sxs-lookup"><span data-stu-id="09d5f-111">Role capabilities are defined by files with a .psrc extension.</span></span>

- <span data-ttu-id="09d5f-112">Znajdź RoleCapability można filtrować z parametrami wersji: MinimumVersion, RequiredVersion, AllVersions.</span><span class="sxs-lookup"><span data-stu-id="09d5f-112">Find-RoleCapability can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="09d5f-113">Parametry te wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="09d5f-113">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="09d5f-114">Te parametry wersji są dozwolone tylko w przypadku nazwę jednego modułu bez żadnych symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="09d5f-114">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="09d5f-115">Jeśli nie określono parametru RequiredVersion, Znajdź RoleCapability zwraca najnowszej wersji modułu, która jest równa lub większa niż określona wersja minimalna lub najnowszej wersji modułu, jeśli wersja minimalna nie jest określona.</span><span class="sxs-lookup"><span data-stu-id="09d5f-115">If the RequiredVersion parameter is not specified, Find-RoleCapability returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="09d5f-116">Jeśli określono parametr RequiredVersion, Znajdź RoleCapability zwraca tylko wersję modułu, która dokładnie odpowiada określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="09d5f-116">If the RequiredVersion parameter is specified, Find-RoleCapability only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="09d5f-117">Znajdź RoleCapability można filtrować według metadanych z parametrem - Tag</span><span class="sxs-lookup"><span data-stu-id="09d5f-117">Find-RoleCapability can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="09d5f-118">Znajdź RoleCapability można filtrować według języka wyszukiwania specyficznego dla repozytorium z parametrem - filtru.</span><span class="sxs-lookup"><span data-stu-id="09d5f-118">Find-RoleCapability can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="09d5f-119">Znajdź RoleCapability można filtrować według modułów z wszystkich lub kilku zarejestrowanych repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="09d5f-119">Find-RoleCapability can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="09d5f-120">Składnia polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="09d5f-120">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-RoleCapability -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="09d5f-121">Dokumentacja poleceń cmdlet pomocy online</span><span class="sxs-lookup"><span data-stu-id="09d5f-121">Cmdlet online help reference</span></span>

[<span data-ttu-id="09d5f-122">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="09d5f-122">Find-RoleCapability</span></span>](http://go.microsoft.com/fwlink/?LinkId=718029)

## <a name="example-commands"></a><span data-ttu-id="09d5f-123">Przykładowe polecenia</span><span class="sxs-lookup"><span data-stu-id="09d5f-123">Example commands</span></span>
```powershell

# Find a specific role capability
Find-RoleCapability -Name Maintenance

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Maintenance                         1.5.0      RoleCapModule                       PrivatePSGallery

# Find multiple role capabilities
Find-RoleCapability -Name MyJeaRole, Maintenance

# Find all available role capabilities from all registered repositories
Find-RoleCapability

# Find available role capabilities from few registered repositories
Find-RoleCapability -Repository PSGallery,PrivatePSGallery

# Find all role capabilities in a specified repository
Find-RoleCapability -Repository PSGallery

# Find a role capability defined in a specific module
Find-RoleCapability -Name Maintenance -ModuleName RoleCapModule

# Find role capabilities from all versions of a module
Find-RoleCapability -ModuleName RoleCapModule -AllVersions

# Find role capabilities with module name and MinimumVersion.
Find-RoleCapability -ModuleName RoleCapModule -MinimumVersion 1.1

# Find role capabilities with module name and exact version
Find-RoleCapability -ModuleName RoleCapModule -RequiredVersion 1.4.0

# Find role capabilities defined modules with -Filter based search. -Filter searches in description and module names
Find-RoleCapability -Filter Cookbook
Find-RoleCapability -Filter RBAC

# Find all role capabilities with tags Azure or DSC in module metadata
Find-RoleCapability -Tag Azure, DSC

```