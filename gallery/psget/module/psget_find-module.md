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
# <a name="find-module"></a>Znajdź moduł
Umożliwia znalezienie moduły z galerii online, spełniających określone kryteria.

## <a name="description"></a>Opis
Znajdź moduł odnajduje modułów z zarejestrowanych repozytoriów, które odpowiadają określonym kryteriom.
Dla każdego modułu znaleziono Znajdź moduł zwraca obiekt PSRepositoryItemInfo, który opcjonalnie można przetwarzana potokowo do instalacji modułu do instalowania modułów.

- Można znaleźć modułu filtr oparty na module zawartości z polecenia, - DscResource, - RoleCapability i - zawiera parametry.
- Znajdź moduł można filtrować z parametrami wersji: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.
  - Te parametry są wykluczają się wzajemnie, z wyjątkiem MinmimumVersion i MaximumVersion.
  - Te parametry wersji są dozwolone tylko w przypadku nazwę jednego modułu bez żadnych symboli wieloznacznych.
  - Jeśli nie określono parametru RequiredVersion, Znajdź moduł zwraca najnowszej wersji modułu, która jest równa lub większa niż określona wersja minimalna lub najnowszej wersji modułu, jeśli wersja minimalna nie jest określona. 
  - Jeśli określono parametr RequiredVersion, Znajdź moduł zwraca tylko wersji modułu, która dokładnie odpowiada określonej wersji.
- Znajdź moduł można filtrować według metadanych z parametrem - Tag
- Znajdź moduł można filtrować według języka wyszukiwania specyficznego dla repozytorium z parametrem - filtru.
- Znajdź moduł można filtrować według modułów z wszystkich lub kilku zarejestrowanych repozytoriów.

## <a name="cmdlet-syntax"></a>Składnia polecenia cmdlet
```powershell
Get-Command -Name Find-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Dokumentacja poleceń cmdlet pomocy online

[Znajdź moduł](http://go.microsoft.com/fwlink/?LinkID=398574)

## <a name="example-commands"></a>Przykładowe polecenia
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

