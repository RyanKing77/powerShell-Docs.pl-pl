---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galeria, programu powershell, polecenia cmdlet, psget
title: "Zainstaluj moduł"
ms.openlocfilehash: c066f4b34a03206cc0f31e9d40144fd719d9e305
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2017
---
# <a name="install-module"></a>Zainstaluj moduł

Instaluje moduły programu PowerShell z repozytoriami online na komputerze lokalnym.

## <a name="description"></a>Opis

Polecenia cmdlet Install-modułu pobiera jednego lub większej liczby modułów z galerii online, weryfikuje i instaluje je na komputerze lokalnym do zakresu określonej instalacji.

Polecenia cmdlet Install-Module pobiera jednego lub większej liczby modułów spełniające określone kryteria z galerii online, sprawdza, czy wyniki wyszukiwania są prawidłowe moduły i kopiowania modułu folderów do lokalizacji instalacji.

Jeśli żaden zakres nie jest zdefiniowana lub gdy wartość parametru zakresu jest AllUsers, moduł jest zainstalowany na %systemdrive%:\Program Files\WindowsPowerShell\Modules. Wartość zakresu po CurrentUser modułu zainstalowano $home\Documents\WindowsPowerShell\Modules.

Można filtrować wyniki oparte na minimalną i dokładnej wersji określone moduły.

- Obsługa wersji Side-by-side, w programie Windows PowerShell 5.0 lub nowszej
- Obsługa instalacji modułu zależności
- **Zaufany monit:**akceptacji użytkownika jest wymagane w celu zainstalowania modułów z niezaufanych repozytorium.
- -Force instaluje ponownie zainstalowany moduł
- RequiredVersion powoduje zainstalowanie wersji określonej w SxS z istniejącymi wersjami na programu PowerShell w wersji 5.0 lub nowszej.

### <a name="scope"></a>Zakres
Określa zakres instalacji modułu. Dopuszczalne wartości tego parametru to: AllUsers i CurrentUser.

Domyślny zakres instalacji jest AllUsers.

Zakresu AllUsers umożliwia moduły można zainstalować w lokalizacji, która jest dostępna dla wszystkich użytkowników komputera, czyli "$env: SystemDrive\Program Files\WindowsPowerShell\Modules".

Zakres CurrentUser umożliwia moduły można zainstalować tylko na "$home\Documents\WindowsPowerShell\Modules", tak, aby moduł jest dostępna tylko dla bieżącego użytkownika.

## <a name="notes"></a>Uwagi

To polecenie cmdlet jest uruchamiane w środowisku Windows PowerShell 3.0 ani nowszych wersji środowiska Windows PowerShell w systemie Windows 7 lub Windows 2008 R2 i nowszych wersjach systemu Windows.

Jeśli zainstalowany moduł nie można zaimportować (Jeśli nie ma .psm1, psd1 lub .dll o takiej samej nazwie w folderze), instalacja zakończy się niepowodzeniem, jeżeli nie zostanie dodany do polecenia parametru Force.

Jeśli wartość określona dla parametru Name odpowiada wersji modułu, na komputerze, a parametr MinimumVersion lub RequiredVersion nie zostały dodane, moduł instalacji dyskretnej nadal bez instalowania tego modułu. Jeśli zostały podane parametry MinimumVersion lub RequiredVersion, a istniejący moduł pasuje do wartości tego parametru, następnie wystąpi błąd. Aby dokładniej: Jeśli wersja aktualnie zainstalowanego modułu jest niższa niż wartość parametru MinimumVersion lub nie jest równa wartości parametru RequiredVersion, wystąpi błąd. Jeśli wersja zainstalowanego modułu jest większa niż wartość parametru MinimumVersion lub równa wartości parametru RequiredVersion, moduł instalacji dyskretnej nadal bez instalowania tego modułu.

Zainstaluj moduł zwraca błąd, jeśli moduł nie istnieje w galerii online, który odpowiada nazwie określonej.

Aby zainstalować wiele modułów, określ tablicę nazw modułu, oddzielonych przecinkami. Nie można dodać MinimumVersion lub RequiredVersion, jeśli można określić wiele nazw modułu.

Domyślnie moduły są instalowane w folderze Program Files, aby uniknąć pomyłek, podczas instalowania zasobów systemu Windows PowerShell Desired stan konfiguracji (DSC). Możesz przekazać wielu obiektów PSGetItemInfo do modułu instalacji; jest to innym sposobem określania wielu modułów instalacji za pomocą jednego polecenia.

Aby zapobiec uruchomionych modułów, które zawierają złośliwego kodu, zainstalowane moduły nie są automatycznie importowane przez instalację. Bezpieczeństwa najlepiej, ocenę modułu kodu przed uruchomieniem polecenia cmdlet ani funkcji w module po raz pierwszy.


## <a name="cmdlet-syntax"></a>Składnia polecenia cmdlet
```powershell
Get-Command -Name Install-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Dokumentacja poleceń cmdlet pomocy online

[Zainstaluj moduł](http://go.microsoft.com/fwlink/?LinkID=398573)

## <a name="example-commands"></a>Przykładowe polecenia

```powershell

# Install a module by name
Install-Module -Name MyDscModule

# Install multiple modules
Install-Module ContosoClient,ContosoServer

# Install a module using its minimum version
Install-Module -Name ContosoServer -MinimumVersion 1.0

# Install a specific version of a module
Install-Module -Name ContosoServer -RequiredVersion 1.1.3

# Install a specific prerelease version of a module
Install-Module -Name ContosoServer -RequiredVersion 1.1.3-alpha -AllowPrerelease

# Install the latest version of a module by name, including prelrelease versions if one exists
Install-Module -Name ContosoServer -AllowPrerelease

# Install the latest version of a module to $home\Documents\WindowsPowerShell\Modules.
Install-Module -Name ContosoServer -Scope CurrentUser

# if a module is already available under $env:PSModulePath, below command fails with 'ModuleAlreadyInstalled,Install-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage'
Install-Module ContosoServer -RequiredVersion 1.5

# if a module is already available under $env:PSModulePath, below command fails with 'ModuleAlreadyInstalled,Install-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage'
Install-Module ContosoServer -MinimumVersion 2.5

# Install multiple modules from multiple registered repositories
Install-Module ContosoClient,ContosoServer -Repository PSGallery, PrivatePSGallery

# Install a module with -WhatIf
Install-Module ContosoClient -WhatIf

# Install a module with -Confirm. A prompt will be displayed to confirm the installation.
Install-Module ContosoClient -WhatIf

# -Force option reinstalls the installed module
Install-Module ContosoClient -Force

# Install a module with dependencies
Install-Module -Name 
```

## <a name="install-module-cmdlet-in-pipeline-operations"></a>Polecenia cmdlet Install-modułu w ramach operacji potoku

```powershell

# Find a module and install it
Find-Module -Name "MyDSC*" | Install-Module

# Find a module and install it to the CurrentUser scope
Find-Module -Name "MyDSC*" | Install-Module -Scope CurrentUser

# Find commands by name and install them
# The first command finds the specified commands in the INT repository, and then uses the pipeline operator to pass them to Install-Module to install them.
# The second command uses Get-InstalledModule to verify the modules from the prior command are installed.
Find-Command -Repository "INT" -Name Get-ContosoClient,Get-ContosoServer | Install-Module
Get-InstalledModule

# This command finds the resource named MyResource and passes it to the Install-Module cmdlet by using the pipeline operator. The Install-Module cmdlet installs the module for the resource. 
# If you pipe multiple resources to the Install-Module cmdlet from the same module, Install-Module attempts to install the module only once. 
Find-DscResource -Name "MyResource" | Install-Module
Get-InstalledModule

# Find multiple role capabilities and install them
Find-RoleCapability -Name MyJeaRole, Maintenance | Install-Module
Get-InstalledModule

```

## <a name="side-by-side-version-support-on-powershell-50-or-newer"></a>Obsługa wersji Side-by-Side programu PowerShell w wersji 5.0 lub nowszej

PowerShellGet obsługuje obsługę wersji side-by-side (SxS) modułu w Module instalacji aktualizacji modułu i poleceń cmdlet Publish-Module uruchamiających w programie Windows PowerShell 5.0 lub nowszej.

### <a name="install-module-examples"></a>Zainstaluj moduł przykłady

```powershell
# Install a version of the module
Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.0 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name : PSScriptAnalyzer
Version : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

# Install another version of the module in Side-by-Side with already installed version.
Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.1 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name       : PSScriptAnalyzer 
Version    : 1.1.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.1
Name       : PSScriptAnalyzer
Version    : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

# Get all versions of an installed module
Get-InstalledModule -Name PSScriptAnalyzer -AllVersions
Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.1.0      PSScriptAnalyzer                    PSGallery            PSScriptAnalyzer provides script analysis... 
1.1.1      PSScriptAnalyzer                    PSGallery            PSScriptAnalyzer provides script analysis...


```

## <a name="install-module-with-its-dependencies"></a>Zainstaluj moduł z jego zależności

```powershell

# Find a module
Find-Module -Name TypePx -Repository PSGallery

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...

# Find a module and its dependencies
Find-Module -Name TypePx -Repository PSGallery -IncludeDependencies

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...
1.0.5.18   SnippetPx                           PSGallery            The SnippetPx module enhances the snippet experience i...

# Discover the dependencies list without adding -IncludeDependencies
$result = Find-Module -Name TypePx -Repository PSGallery
$result.Dependencies

Name                           Value
----                           -----
Name                           SnippetPx
CanonicalId                    powershellget:SnippetPx/#https://www.powershellgallery.com/api/v2/


# Now install the module along with its dependencies
Install-Module -Name TypePx -Repository PSGallery -Verbose

VERBOSE: Repository details, Name = 'PSGallery', Location = 'https://www.powershellgallery.com/api/v2/'; IsTrusted =
'False'; IsRegistered = 'True'.
VERBOSE: Using the provider 'PowerShellGet' for searching packages.
VERBOSE: Using the specified source names : 'PSGallery'.
VERBOSE: Getting the provider object for the PackageManagement Provider 'NuGet'.
VERBOSE: The specified Location is 'https://www.powershellgallery.com/api/v2/' and PackageManagementProvider is
'NuGet'.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='TypePx'' for ''.
VERBOSE: Total package yield:'1' for the specified package 'TypePx'.
VERBOSE: Performing the operation "Install-Module" on target "Version '2.0.1.20' of module 'TypePx'".

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): Y
VERBOSE: The installation scope is specified to be 'AllUsers'.
VERBOSE: The specified module will be installed in 'C:\Program Files\WindowsPowerShell\Modules'.
VERBOSE: The specified Location is 'NuGet' and PackageManagementProvider is 'NuGet'.
VERBOSE: Downloading module 'TypePx' with version '2.0.1.20' from the repository
'https://www.powershellgallery.com/api/v2/'.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='TypePx'' for ''.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='SnippetPx'' for ''.
VERBOSE: InstallPackage' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: DownloadPackage' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896\SnippetPx\SnippetPx.nupkg',
uri='https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'
VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'.
VERBOSE: Completed downloading 'SnippetPx'.
VERBOSE: Hash for package 'SnippetPx' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: InstallPackage' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: DownloadPackage' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896\TypePx\TypePx.nupkg',
uri='https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'
VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'.
VERBOSE: Completed downloading 'TypePx'.
VERBOSE: Hash for package 'TypePx' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: Installing the dependency module 'SnippetPx' with version '1.0.5.18' for the module 'TypePx'.
VERBOSE: Module 'SnippetPx' was installed successfully to path 'C:\Program
Files\WindowsPowerShell\Modules\SnippetPx\1.0.5.18'.
VERBOSE: Module 'TypePx' was installed successfully to path 'C:\Program
Files\WindowsPowerShell\Modules\TypePx\2.0.1.20'.


# Get the installed modules
Get-InstalledModule

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0.5.18   SnippetPx                           PSGallery            The SnippetPx module enhances the snippet experience i...
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...

```

## <a name="error-scenarios"></a>Błąd scenariuszy

```powershell

# Below command fails with 'NameShouldNotContainWildcardCharacters,Install-Module'
Install-Module ContosoServe*

# Below command fails with 'VersionRangeAndRequiredVersionCannotBeSpecifiedTogether,Install-Module'
Install-Module ContosoServer -MinimumVersion 1.0 -RequiredVersion 5.0

# Below command fails with 'VersionParametersAreAllowedOnlyWithSingleName,Install-Module'
Install-Module ContosoClient,ContosoServer -RequiredVersion 2.0

# Below command fails with 'VersionParametersAreAllowedOnlyWithSingleName,Install-Module'
Install-Module ContosoClient,ContosoServer -MinimumVersion 2.0

```

