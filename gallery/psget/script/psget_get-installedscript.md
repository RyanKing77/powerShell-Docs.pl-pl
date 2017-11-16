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
# <a name="get-installedscript"></a><span data-ttu-id="b825b-103">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="b825b-103">Get-InstalledScript</span></span>

<span data-ttu-id="b825b-104">Pobiera skrypty są zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="b825b-104">Gets installed scripts on a computer.</span></span>

## <a name="description"></a><span data-ttu-id="b825b-105">Opis</span><span class="sxs-lookup"><span data-stu-id="b825b-105">Description</span></span>

<span data-ttu-id="b825b-106">Polecenie cmdlet Get-InstalledScript pobiera zainstalowane skryptów programu PowerShell na komputerze.</span><span class="sxs-lookup"><span data-stu-id="b825b-106">The Get-InstalledScript cmdlet gets installed PowerShell scripts on a computer.</span></span>

<span data-ttu-id="b825b-107">Dla każdego zainstalowanego skryptu Get InstalledScript zwraca obiekt PSRepositoryItemInfo, który opcjonalnie można przetwarzana potokowo do skrypt dezinstalacji skryptu odinstalowywania zainstalowanych skryptów.</span><span class="sxs-lookup"><span data-stu-id="b825b-107">For each installed script, Get-InstalledScript returns a PSRepositoryItemInfo object which can optionally be piped to Uninstall-Script for uninstalling the installed scripts.</span></span>

- <span data-ttu-id="b825b-108">Get-InstalledScript można filtrować skrypty zainstalowanych na podstawie nazwy, wersji parametrów.</span><span class="sxs-lookup"><span data-stu-id="b825b-108">Get-InstalledScript can filter installed scripts based on name, version parameters.</span></span>
- <span data-ttu-id="b825b-109">Get-InstalledScript można filtrować z parametrami wersji: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.</span><span class="sxs-lookup"><span data-stu-id="b825b-109">Get-InstalledScript can filter with version parameters: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="b825b-110">Te parametry są wykluczają się wzajemnie, z wyjątkiem MinmimumVersion i MaximumVersion.</span><span class="sxs-lookup"><span data-stu-id="b825b-110">These parameters are mutually exclusive, except MinmimumVersion and MaximumVersion.</span></span>
  - <span data-ttu-id="b825b-111">Te parametry wersji są dozwolone tylko w przypadku nazwę jednego skryptu bez żadnych symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="b825b-111">These version parameters are allowed only with the single script name without any wildcards.</span></span>
  - <span data-ttu-id="b825b-112">Jeśli nie określono parametru RequiredVersion, Get InstalledScript zwraca najnowszej wersji zainstalowanej skrypt, który jest równa lub większa niż określona wersja minimalna lub najnowszą wersję skryptu, jeśli wersja minimalna nie jest określona.</span><span class="sxs-lookup"><span data-stu-id="b825b-112">If the RequiredVersion parameter is not specified, Get-InstalledScript returns the latest version of the installed script that is equal to or greater than the minimum version specified or the latest version of the script if no minimum version is specified.</span></span> 
  - <span data-ttu-id="b825b-113">Jeśli określono parametr RequiredVersion, Get InstalledScript zwraca tylko wersję zainstalowanego skryptu, która dokładnie odpowiada określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="b825b-113">If the RequiredVersion parameter is specified, Get-InstalledScript only returns the version of installed script that exactly matches the specified version.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="b825b-114">Składnia polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="b825b-114">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Get-InstalledScript -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="b825b-115">Dokumentacja poleceń cmdlet pomocy online</span><span class="sxs-lookup"><span data-stu-id="b825b-115">Cmdlet online help reference</span></span>

[<span data-ttu-id="b825b-116">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="b825b-116">Get-InstalledScript</span></span>](http://go.microsoft.com/fwlink/?LinkId=619790)

## <a name="example-commands"></a><span data-ttu-id="b825b-117">Przykładowe polecenia</span><span class="sxs-lookup"><span data-stu-id="b825b-117">Example commands</span></span>

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

