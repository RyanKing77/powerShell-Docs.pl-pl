---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galeria, programu powershell, polecenia cmdlet, psget
title: "Znajdź moduł"
ms.openlocfilehash: 65c466909c007ed08c3fa978f78483983b00ba73
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2017
---
# <a name="find-module"></a><span data-ttu-id="0e964-103">Znajdź moduł</span><span class="sxs-lookup"><span data-stu-id="0e964-103">Find-Module</span></span>
<span data-ttu-id="0e964-104">Umożliwia znalezienie moduły z galerii online, spełniających określone kryteria.</span><span class="sxs-lookup"><span data-stu-id="0e964-104">Finds modules from an online gallery that match specified criteria.</span></span>

## <a name="description"></a><span data-ttu-id="0e964-105">Opis</span><span class="sxs-lookup"><span data-stu-id="0e964-105">Description</span></span>
<span data-ttu-id="0e964-106">Znajdź moduł odnajduje modułów z zarejestrowanych repozytoriów, które odpowiadają określonym kryteriom.</span><span class="sxs-lookup"><span data-stu-id="0e964-106">Find-Module discovers the modules from registered repositories that matches the specified criteria.</span></span>
<span data-ttu-id="0e964-107">Dla każdego modułu znaleziono Znajdź moduł zwraca obiekt PSRepositoryItemInfo, który opcjonalnie można przetwarzana potokowo do instalacji modułu do instalowania modułów.</span><span class="sxs-lookup"><span data-stu-id="0e964-107">For each module found, Find-Module returns a PSRepositoryItemInfo object which can optionally be piped to Install-Module for installing the modules.</span></span>

- <span data-ttu-id="0e964-108">Można znaleźć modułu filtr oparty na module zawartości z polecenia, - DscResource, - RoleCapability i - zawiera parametry.</span><span class="sxs-lookup"><span data-stu-id="0e964-108">Find-Module can filter based on module contents with the -Command, -DscResource, -RoleCapability and -Includes parameters.</span></span>
- <span data-ttu-id="0e964-109">Znajdź moduł można filtrować z parametrami wersji: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.</span><span class="sxs-lookup"><span data-stu-id="0e964-109">Find-Module can filter with version parameters: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="0e964-110">Te parametry są wykluczają się wzajemnie, z wyjątkiem MinmimumVersion i MaximumVersion.</span><span class="sxs-lookup"><span data-stu-id="0e964-110">These parameters are mutually exclusive, except MinmimumVersion and MaximumVersion.</span></span>
  - <span data-ttu-id="0e964-111">Te parametry wersji są dozwolone tylko w przypadku nazwę jednego modułu bez żadnych symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="0e964-111">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="0e964-112">Jeśli nie określono parametru RequiredVersion, Znajdź moduł zwraca najnowszej wersji modułu, która jest równa lub większa niż określona wersja minimalna lub najnowszej wersji modułu, jeśli wersja minimalna nie jest określona.</span><span class="sxs-lookup"><span data-stu-id="0e964-112">If the RequiredVersion parameter is not specified, Find-Module returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span> 
  - <span data-ttu-id="0e964-113">Jeśli określono parametr RequiredVersion, Znajdź moduł zwraca tylko wersji modułu, która dokładnie odpowiada określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="0e964-113">If the RequiredVersion parameter is specified, Find-Module only returns the version of module that exactly matches the specified version.</span></span>
- <span data-ttu-id="0e964-114">Znajdź moduł można filtrować według metadanych z parametrem - Tag</span><span class="sxs-lookup"><span data-stu-id="0e964-114">Find-Module can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="0e964-115">Znajdź moduł można filtrować według języka wyszukiwania specyficznego dla repozytorium z parametrem - filtru.</span><span class="sxs-lookup"><span data-stu-id="0e964-115">Find-Module can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="0e964-116">Znajdź moduł można filtrować według modułów z wszystkich lub kilku zarejestrowanych repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="0e964-116">Find-Module can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="0e964-117">Składnia polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="0e964-117">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="0e964-118">Dokumentacja poleceń cmdlet pomocy online</span><span class="sxs-lookup"><span data-stu-id="0e964-118">Cmdlet online help reference</span></span>

[<span data-ttu-id="0e964-119">Znajdź moduł</span><span class="sxs-lookup"><span data-stu-id="0e964-119">Find-Module</span></span>](http://go.microsoft.com/fwlink/?LinkID=398574)

## <a name="example-commands"></a><span data-ttu-id="0e964-120">Przykładowe polecenia</span><span class="sxs-lookup"><span data-stu-id="0e964-120">Example commands</span></span>
```powershell
# Find a specific module
Find-Module Azure

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.3.2      Azure                               PSGallery            Microsoft Azure PowerShell - Service Management

# Find multiple modules
Find-Module Azure,AzureRM

# Find modules with wildcards in -Name
Find-Module -Name AzureRM*

# Find all versions of a module
Find-Module -Name PSReadline -AllVersions

# Find a module with -MinimumVersion. 
# With MinimumVersion we can find a module whose version is greate than or equal to the specified MinimumVersion value.
Find-Module -Name PSReadline -MinimumVersion 1.0.0.12

# Find a module with MaximumVersion
Find-Module -Name PSReadline -MaximumVersion 1.0.0.13

# Find a module with both MinimumVersion and MaximumVersion range.
Find-Module -Name PSReadline -MinimumVersion 1.0.0.12 -MaximumVersion 1.0.0.13

# Find a module with exact version
Find-Module -Name AzureRM -RequiredVersion 1.3.2

# Find a module with a specific prerelease version
Find-Module -Name AzureRM -RequiredVersion 1.3.2-alpha -AllowPrerelease

# Find a module from the specified repository
Find-Module -Name Contoso -Repository MyLocalRepo

# Find available modules from all registered repositories
Find-Module

# Find available modules from few registered repositories
Find-Module -Repository PSGallery,PrivatePSGallery

# Find a module along with its dependencies
Find-Module -Name AzureRM -IncludeDependencies

# Find all modules with Dsc resources
Find-Module -Includes DscResource

# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

# Find all modules with cmdlets
Find-Module -Includes Cmdlet

# Find all modules with functions
Find-Module -Includes Function

# Find all modules with Role Capabilities
Find-Module -Includes RoleCapability

# Find all modules with the specified Role Capability name
Find-Module -RoleCapability RoleCap1
Find-Module -RoleCapability RoleCap2 -Includes RoleCapability

# Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer -Includes Cmdlet
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer -Includes Function

# Find modules with -Filter based search. -Filter searches in description and names
Find-Module -Filter Cookbook
Find-Module -Filter RBAC
Find-Module -Filter 'App Domain' -Includes 'DscResource'

# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

# Properties of Find-Module returned object
Find-Module AzureRM.Profile | Format-List * -Force

Name                       : AzureRM.profile
Version                    : 1.0.8
Type                       : Module
Description                : Microsoft Azure PowerShell - Profile credential management cmdlets for Azure Resource
                             Manager
Author                     : Microsoft Corporation
CompanyName                : {elogeel, azure-sdk}
Copyright                  : Microsoft Corporation. All rights reserved.
PublishedDate              : 5/4/2016 9:40:33 PM
InstalledDate              :
UpdatedDate                :
LicenseUri                 : https://raw.githubusercontent.com/Azure/azure-powershell/dev/LICENSE.txt
ProjectUri                 : https://github.com/Azure/azure-powershell
IconUri                    :
Tags                       : {PSModule}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               : https://github.com/Azure/azure-powershell/blob/dev/ChangeLog.md
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {downloadCount, description, copyright, FileList...}

```

