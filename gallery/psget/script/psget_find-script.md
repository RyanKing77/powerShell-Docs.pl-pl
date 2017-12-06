---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galeria, programu powershell, polecenia cmdlet, psget
title: "Znajdź skryptu"
ms.openlocfilehash: df62a9934d8013d37bd0083c03f90fa7fa05ac0c
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2017
---
# <a name="find-script"></a>Znajdź skryptu

Umożliwia znalezienie PowerShell pliki skryptów z galerii online spełniających określone kryteria.

## <a name="description"></a>Opis

Znajdź skryptu odnajduje plików skryptów z zarejestrowanych repozytoriów, które odpowiadają określonym kryteriom.
Dla każdego skryptu znaleziono Znajdź skrypt zwraca obiektu PSRepositoryItemInfo, który opcjonalnie można przetwarzana potokowo do skryptu instalacji instalowania skryptów.
Polecenie cmdlet Znajdź skrypt umożliwia odnajdowanie plików skryptów z innych kryteriów wyszukiwania z repozytoriami określonych lub wszystkich zarejestrowanych i takie jak nazwa tagu, filtrowanie, nazwa polecenia, zakres wersji, dokładnej wersji, wszystkie wersje, łącznie z jego zależności.

- Można znaleźć skryptu filtr oparty na skrypcie zawartości przy użyciu polecenia i - zawiera parametry.
- Znajdź skryptu można filtrować z parametrami wersji: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.
  - Te parametry są wykluczają się wzajemnie, z wyjątkiem MinmimumVersion i MaximumVersion.
  - Te parametry wersji są dozwolone tylko w przypadku nazwę jednego skryptu bez żadnych symboli wieloznacznych.
  - Jeśli nie określono parametru RequiredVersion, Znajdź skrypt zwraca najnowszą wersję skrypt, który jest równa lub większa niż określona wersja minimalna lub najnowszą wersję skryptu, jeśli wersja minimalna nie jest określona. 
  - Jeśli określono parametr RequiredVersion, Znajdź skrypt zwraca tylko wersji skryptu, która dokładnie odpowiada określonej wersji.
- Znajdź skryptu można filtrować według metadanych skryptów z parametrem - Tag.
- Znajdź skryptu można filtrować według języka wyszukiwania specyficznego dla repozytorium z parametrem - filtru.
- Znajdź skryptu można filtrować według skryptów z wszystkich lub kilku zarejestrowanych repozytoriów.

**Uwaga:** PSRepository zarejestrowanej powinien mieć prawidłową ScriptSourceLocation. Można ustawić wartości ScriptSourceLocation, można użyć PSRepository zestawu.

## <a name="cmdlet-syntax"></a>Składnia polecenia cmdlet

```powershell
Get-Command -Name Find-Script -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Dokumentacja poleceń cmdlet pomocy online

[Znajdź skryptu](http://go.microsoft.com/fwlink/?LinkId=619785)

## <a name="example-commands"></a>Przykładowe polecenia

```powershell
# Find a script from the registered repository with ScriptSourceLocation
Find-Script Connect-AzureVM

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0        Connect-AzureVM                     PSGallery            This runbook sets up a connection to an Azure vi...

# Find multiple scripts
Find-Script -Name Connect-AzureVM, Show-Tree, Connect-O365

# Find scripts with wildcards in -Name
Find-Script -Name *Azure*

# Find all versions of a script
Find-Script -Name Connect-O365 -AllVersions

# Find a script with -MinimumVersion. 
# With MinimumVersion we can find a script whose version is greate than or equal to the specified MinimumVersion value.
Find-Script Connect-O365 -MinimumVersion 1.4

# Find a script with MaximumVersion
Find-Script -Name Connect-O365 -MaximumVersion 1.6.2

# Find a script with both MinimumVersion and MaximumVersion range.
Find-Script -Name Connect-O365 -MinimumVersion 1.1 -MaximumVersion 1.6.2

# Find a script with exact version
Find-Script -Name Connect-O365 -RequiredVersion 1.5.7

# Find a script with a specific pre-release version
Find-Script -Name Connect-O365 -RequiredVersion 1.3.2-alpha -AllowPrerelease

# Find a script from the specified repository
Find-Script -Name Fabrikam-ServerScript -Repository MyLocalRepo

# Find available scripts from all registered repositories
Find-Script

# Find available scripts from few registered repositories
Find-Script -Repository PSGallery, PrivatePSGallery

# Find a script along with its dependent modules and scripts
Find-Script -Name Connect-AzureVM -IncludeDependencies

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0        Connect-AzureVM                     PSGallery            This runbook sets up a connection to an Azure vi...
1.4.0      Azure                               PSGallery            Microsoft Azure PowerShell - Service Management
1.1.2      Azure.Storage                       PSGallery            Microsoft Azure PowerShell - Storage service cmd...
1.0.8      AzureRM.profile                     PSGallery            Microsoft Azure PowerShell - Profile credential ...

# Find all scripts with workflows
Find-Script -Includes Workflow

# Find all scripts with functions
Find-Script -Includes Function

# Find scripts with specific commands
Find-Script -Command Log-Message
Find-Script -Command Log-Message, Show-Tree -Includes Function
Find-Script -Command Connect-AzureVM -Includes Workflow

# Find scripts with -Filter based search. -Filter searches in description and names
Find-Script -Filter Windows
Find-Script -Filter Azure

# Find all scripts with tags O365 or Nano
Find-Script -Tag O365, Nano

# Properties of Find-Script returned object
Find-Script Show-Tree | Format-List * -Force
Name                       : Show-Tree
Version                    : 1.0.0
Type                       : Script
Description                : Script to show the layout of PowerShell namespaces (Trees) using ASCII
Author                     : Jeffrey Snover
CompanyName                : jsnover
Copyright                  : (C) Microsoft Corporation. All rights reserved.
PublishedDate              : 2/15/2016 10:15:35 PM
InstalledDate              :
UpdatedDate                :
LicenseUri                 :
ProjectUri                 :
IconUri                    :
Tags                       : {Nano, PSScript}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               :
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {versionDownloadCount, ItemType, copyright, PackageManagementProvider...}


# Includes property on PSRepositoryItemInfo object
$t = Find-Script -Includes Workflow -Repository INT -Name Fabrikam-ClientScript
$t.Includes

Name                           Value
----                           -----
Function                       {Test-FunctionFromScript_Fabrikam-ClientScript}
RoleCapability                 {}
Command                        {Test-FunctionFromScript_Fabrikam-ClientScript, Test-WorkflowFromScript_Fabrikam-Clie...
DscResource                    {}
Workflow                       {Test-WorkflowFromScript_Fabrikam-ClientScript}
Cmdlet                         {}


```

