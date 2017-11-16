---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galeria, programu powershell, polecenia cmdlet, psget
title: Get-InstalledScript
ms.openlocfilehash: f35e57cdadd1448bd9032ab007d692003c4cf4a2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="get-installedscript"></a>Get-InstalledScript

Pobiera skrypty są zainstalowane na komputerze.

## <a name="description"></a>Opis

Polecenie cmdlet Get-InstalledScript pobiera zainstalowane skryptów programu PowerShell na komputerze.

Dla każdego zainstalowanego skryptu Get InstalledScript zwraca obiekt PSRepositoryItemInfo, który opcjonalnie można przetwarzana potokowo do skrypt dezinstalacji skryptu odinstalowywania zainstalowanych skryptów.

- Get-InstalledScript można filtrować skrypty zainstalowanych na podstawie nazwy, wersji parametrów.
- Get-InstalledScript można filtrować z parametrami wersji: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.
  - Te parametry są wykluczają się wzajemnie, z wyjątkiem MinmimumVersion i MaximumVersion.
  - Te parametry wersji są dozwolone tylko w przypadku nazwę jednego skryptu bez żadnych symboli wieloznacznych.
  - Jeśli nie określono parametru RequiredVersion, Get InstalledScript zwraca najnowszej wersji zainstalowanej skrypt, który jest równa lub większa niż określona wersja minimalna lub najnowszą wersję skryptu, jeśli wersja minimalna nie jest określona. 
  - Jeśli określono parametr RequiredVersion, Get InstalledScript zwraca tylko wersję zainstalowanego skryptu, która dokładnie odpowiada określonej wersji.

## <a name="cmdlet-syntax"></a>Składnia polecenia cmdlet

```powershell
Get-Command -Name Get-InstalledScript -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Dokumentacja poleceń cmdlet pomocy online

[Get-InstalledScript](http://go.microsoft.com/fwlink/?LinkId=619790)

## <a name="example-commands"></a>Przykładowe polecenia

```powershell

# Get all scripts installed using PowerShellGet cmdlets
Get-InstalledScript

# Get a specific installed script
Get-InstalledScript Show-Tree

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0.0      Show-Tree                           PSGallery            Script to show the layout of PowerShell namespaces (Tr...

# Get installed script with wildcards
Get-InstalledScript -Name *Azure*

# Get all versions of an installed script
Get-InstalledScript -Name Connect-O365 -AllVersions

# Get installed script with MinimumVersion
Get-InstalledScript -Name Connect-O365 -MinimumVersion 1.1

# Get installed script with MaximumVersion
Get-InstalledScript -Name Connect-O365 -MaximumVersion 1.6.3

# Get installed script with version range
Get-InstalledScript -Name Connect-O365 -MinimumVersion 1.1 -MaximumVersion 1.6.3

# Get installed script with RequiredVersion
Get-InstalledScript -Name Connect-O365 -RequiredVersion 1.4

# Properties of Get-InstalledScript returned object
Get-InstalledScript Show-Tree | Format-List * -Force

Name                       : Show-Tree
Version                    : 1.0.0
Type                       : Script
Description                : Script to show the layout of PowerShell namespaces (Trees) using ASCII
Author                     : Jeffrey Snover
CompanyName                : jsnover
Copyright                  : (C) Microsoft Corporation. All rights reserved.
PublishedDate              : 2/15/2016 10:15:35 PM
InstalledDate              : 5/4/2016 11:44:13 PM
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
AdditionalMetadata         : {description, installeddate, tags, PackageManagementProvider...}
InstalledLocation          : C:\Program Files\WindowsPowerShell\Scripts


```

