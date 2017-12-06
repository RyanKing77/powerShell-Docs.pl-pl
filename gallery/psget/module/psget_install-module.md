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
# <a name="install-module"></a><span data-ttu-id="c188e-103">Zainstaluj moduł</span><span class="sxs-lookup"><span data-stu-id="c188e-103">Install-Module</span></span>

<span data-ttu-id="c188e-104">Instaluje moduły programu PowerShell z repozytoriami online na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="c188e-104">Installs the PowerShell modules from online repositories to the local computer.</span></span>

## <a name="description"></a><span data-ttu-id="c188e-105">Opis</span><span class="sxs-lookup"><span data-stu-id="c188e-105">Description</span></span>

<span data-ttu-id="c188e-106">Polecenia cmdlet Install-modułu pobiera jednego lub większej liczby modułów z galerii online, weryfikuje i instaluje je na komputerze lokalnym do zakresu określonej instalacji.</span><span class="sxs-lookup"><span data-stu-id="c188e-106">Install-Module cmdlet downloads one or more modules from an online gallery, validates and installs them on the local computer to the specified installation scope.</span></span>

<span data-ttu-id="c188e-107">Polecenia cmdlet Install-Module pobiera jednego lub większej liczby modułów spełniające określone kryteria z galerii online, sprawdza, czy wyniki wyszukiwania są prawidłowe moduły i kopiowania modułu folderów do lokalizacji instalacji.</span><span class="sxs-lookup"><span data-stu-id="c188e-107">The Install-Module cmdlet gets one or more modules that meet specified criteria from an online gallery, verifies that search results are valid modules, and copies module folders to the installation location.</span></span>

<span data-ttu-id="c188e-108">Jeśli żaden zakres nie jest zdefiniowana lub gdy wartość parametru zakresu jest AllUsers, moduł jest zainstalowany na %systemdrive%:\Program Files\WindowsPowerShell\Modules.</span><span class="sxs-lookup"><span data-stu-id="c188e-108">When no scope is defined, or when the value of the Scope parameter is AllUsers, the module is installed to %systemdrive%:\Program Files\WindowsPowerShell\Modules.</span></span> <span data-ttu-id="c188e-109">Wartość zakresu po CurrentUser modułu zainstalowano $home\Documents\WindowsPowerShell\Modules.</span><span class="sxs-lookup"><span data-stu-id="c188e-109">When the value of Scope is CurrentUser, the module is installed to $home\Documents\WindowsPowerShell\Modules.</span></span>

<span data-ttu-id="c188e-110">Można filtrować wyniki oparte na minimalną i dokładnej wersji określone moduły.</span><span class="sxs-lookup"><span data-stu-id="c188e-110">You can filter your results based on minimum and exact versions of specified modules.</span></span>

- <span data-ttu-id="c188e-111">Obsługa wersji Side-by-side, w programie Windows PowerShell 5.0 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="c188e-111">Side-by-side version support on Windows PowerShell 5.0 or newer</span></span>
- <span data-ttu-id="c188e-112">Obsługa instalacji modułu zależności</span><span class="sxs-lookup"><span data-stu-id="c188e-112">Module dependency installation support</span></span>
- <span data-ttu-id="c188e-113">**Zaufany monit:**akceptacji użytkownika jest wymagane w celu zainstalowania modułów z niezaufanych repozytorium.</span><span class="sxs-lookup"><span data-stu-id="c188e-113">**Untrusted prompt:**User acceptance is required for installing the modules from an untrusted repository.</span></span>
- <span data-ttu-id="c188e-114">-Force instaluje ponownie zainstalowany moduł</span><span class="sxs-lookup"><span data-stu-id="c188e-114">-Force reinstalls the installed module</span></span>
- <span data-ttu-id="c188e-115">RequiredVersion powoduje zainstalowanie wersji określonej w SxS z istniejącymi wersjami na programu PowerShell w wersji 5.0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="c188e-115">RequiredVersion installs the specified version in SxS with existing versions on PowerShell version 5.0 or newer.</span></span>

### <a name="scope"></a><span data-ttu-id="c188e-116">Zakres</span><span class="sxs-lookup"><span data-stu-id="c188e-116">Scope</span></span>
<span data-ttu-id="c188e-117">Określa zakres instalacji modułu.</span><span class="sxs-lookup"><span data-stu-id="c188e-117">Specifies the installation scope of the module.</span></span> <span data-ttu-id="c188e-118">Dopuszczalne wartości tego parametru to: AllUsers i CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="c188e-118">The acceptable values for this parameter are: AllUsers and CurrentUser.</span></span>

<span data-ttu-id="c188e-119">Domyślny zakres instalacji jest AllUsers.</span><span class="sxs-lookup"><span data-stu-id="c188e-119">The default installation scope is AllUsers.</span></span>

<span data-ttu-id="c188e-120">Zakresu AllUsers umożliwia moduły można zainstalować w lokalizacji, która jest dostępna dla wszystkich użytkowników komputera, czyli "$env: SystemDrive\Program Files\WindowsPowerShell\Modules".</span><span class="sxs-lookup"><span data-stu-id="c188e-120">The AllUsers scope lets modules be installed in a location that is accessible to all users of the computer, that is, "$env:SystemDrive\Program Files\WindowsPowerShell\Modules".</span></span>

<span data-ttu-id="c188e-121">Zakres CurrentUser umożliwia moduły można zainstalować tylko na "$home\Documents\WindowsPowerShell\Modules", tak, aby moduł jest dostępna tylko dla bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c188e-121">The CurrentUser scope lets modules be installed only to "$home\Documents\WindowsPowerShell\Modules", so that the module is available only to the current user.</span></span>

## <a name="notes"></a><span data-ttu-id="c188e-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c188e-122">Notes</span></span>

<span data-ttu-id="c188e-123">To polecenie cmdlet jest uruchamiane w środowisku Windows PowerShell 3.0 ani nowszych wersji środowiska Windows PowerShell w systemie Windows 7 lub Windows 2008 R2 i nowszych wersjach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="c188e-123">This cmdlet runs on Windows PowerShell 3.0 or later releases of Windows PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

<span data-ttu-id="c188e-124">Jeśli zainstalowany moduł nie można zaimportować (Jeśli nie ma .psm1, psd1 lub .dll o takiej samej nazwie w folderze), instalacja zakończy się niepowodzeniem, jeżeli nie zostanie dodany do polecenia parametru Force.</span><span class="sxs-lookup"><span data-stu-id="c188e-124">If an installed module cannot be imported (that is, if it does not have a .psm1, .psd1, or .dll of the same name within the folder), installation fails unless you add the Force parameter to your command.</span></span>

<span data-ttu-id="c188e-125">Jeśli wartość określona dla parametru Name odpowiada wersji modułu, na komputerze, a parametr MinimumVersion lub RequiredVersion nie zostały dodane, moduł instalacji dyskretnej nadal bez instalowania tego modułu.</span><span class="sxs-lookup"><span data-stu-id="c188e-125">If a version of the module on the computer matches the value specified for the Name parameter, and you have not added the MinimumVersion or RequiredVersion parameter, Install-Module silently continues without installing that module.</span></span> <span data-ttu-id="c188e-126">Jeśli zostały podane parametry MinimumVersion lub RequiredVersion, a istniejący moduł pasuje do wartości tego parametru, następnie wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="c188e-126">If the MinimumVersion or RequiredVersion parameters are specified, and the existing module does not match the values in that parameter, then an error occurs.</span></span> <span data-ttu-id="c188e-127">Aby dokładniej: Jeśli wersja aktualnie zainstalowanego modułu jest niższa niż wartość parametru MinimumVersion lub nie jest równa wartości parametru RequiredVersion, wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="c188e-127">To be more specific: if the version of the currently-installed module is either lower than the value of the MinimumVersion parameter, or not equal to the value of the RequiredVersion parameter, an error occurs.</span></span> <span data-ttu-id="c188e-128">Jeśli wersja zainstalowanego modułu jest większa niż wartość parametru MinimumVersion lub równa wartości parametru RequiredVersion, moduł instalacji dyskretnej nadal bez instalowania tego modułu.</span><span class="sxs-lookup"><span data-stu-id="c188e-128">If the version of the installed module is greater than the value of the MinimumVersion parameter, or equal to the value of the RequiredVersion parameter, Install-Module silently continues without installing that module.</span></span>

<span data-ttu-id="c188e-129">Zainstaluj moduł zwraca błąd, jeśli moduł nie istnieje w galerii online, który odpowiada nazwie określonej.</span><span class="sxs-lookup"><span data-stu-id="c188e-129">Install-Module returns an error if no module exists in the online gallery that matches the specified name.</span></span>

<span data-ttu-id="c188e-130">Aby zainstalować wiele modułów, określ tablicę nazw modułu, oddzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="c188e-130">To install multiple modules, specify an array of the module names, separated by commas.</span></span> <span data-ttu-id="c188e-131">Nie można dodać MinimumVersion lub RequiredVersion, jeśli można określić wiele nazw modułu.</span><span class="sxs-lookup"><span data-stu-id="c188e-131">You cannot add MinimumVersion or RequiredVersion if you specify multiple module names.</span></span>

<span data-ttu-id="c188e-132">Domyślnie moduły są instalowane w folderze Program Files, aby uniknąć pomyłek, podczas instalowania zasobów systemu Windows PowerShell Desired stan konfiguracji (DSC). Możesz przekazać wielu obiektów PSGetItemInfo do modułu instalacji; jest to innym sposobem określania wielu modułów instalacji za pomocą jednego polecenia.</span><span class="sxs-lookup"><span data-stu-id="c188e-132">By default, modules are installed to the Program Files folder, to prevent confusion when you are installing Windows PowerShell Desired State Configuration (DSC) resources.You can pipe multiple PSGetItemInfo objects to Install-Module; this is another way of specifying multiple modules to install in a single command.</span></span>

<span data-ttu-id="c188e-133">Aby zapobiec uruchomionych modułów, które zawierają złośliwego kodu, zainstalowane moduły nie są automatycznie importowane przez instalację.</span><span class="sxs-lookup"><span data-stu-id="c188e-133">To help prevent running modules that contain malicious code, installed modules are not automatically imported by installation.</span></span> <span data-ttu-id="c188e-134">Bezpieczeństwa najlepiej, ocenę modułu kodu przed uruchomieniem polecenia cmdlet ani funkcji w module po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="c188e-134">As a security best practice, evaluate module code before running any cmdlets or functions in a module for the first time.</span></span>


## <a name="cmdlet-syntax"></a><span data-ttu-id="c188e-135">Składnia polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="c188e-135">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Install-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="c188e-136">Dokumentacja poleceń cmdlet pomocy online</span><span class="sxs-lookup"><span data-stu-id="c188e-136">Cmdlet online help reference</span></span>

[<span data-ttu-id="c188e-137">Zainstaluj moduł</span><span class="sxs-lookup"><span data-stu-id="c188e-137">Install-Module</span></span>](http://go.microsoft.com/fwlink/?LinkID=398573)

## <a name="example-commands"></a><span data-ttu-id="c188e-138">Przykładowe polecenia</span><span class="sxs-lookup"><span data-stu-id="c188e-138">Example commands</span></span>

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

## <a name="install-module-cmdlet-in-pipeline-operations"></a><span data-ttu-id="c188e-139">Polecenia cmdlet Install-modułu w ramach operacji potoku</span><span class="sxs-lookup"><span data-stu-id="c188e-139">Install-Module cmdlet in pipeline operations</span></span>

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

## <a name="side-by-side-version-support-on-powershell-50-or-newer"></a><span data-ttu-id="c188e-140">Obsługa wersji Side-by-Side programu PowerShell w wersji 5.0 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="c188e-140">Side-by-Side Version Support on PowerShell 5.0 or newer</span></span>

<span data-ttu-id="c188e-141">PowerShellGet obsługuje obsługę wersji side-by-side (SxS) modułu w Module instalacji aktualizacji modułu i poleceń cmdlet Publish-Module uruchamiających w programie Windows PowerShell 5.0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="c188e-141">PowerShellGet supports the side-by-side (SxS) module version support in Install-Module, Update-Module, and Publish-Module cmdlets that run in Windows PowerShell 5.0 or newer.</span></span>

### <a name="install-module-examples"></a><span data-ttu-id="c188e-142">Zainstaluj moduł przykłady</span><span class="sxs-lookup"><span data-stu-id="c188e-142">Install-Module examples</span></span>

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

## <a name="install-module-with-its-dependencies"></a><span data-ttu-id="c188e-143">Zainstaluj moduł z jego zależności</span><span class="sxs-lookup"><span data-stu-id="c188e-143">Install module with its dependencies</span></span>

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

## <a name="error-scenarios"></a><span data-ttu-id="c188e-144">Błąd scenariuszy</span><span class="sxs-lookup"><span data-stu-id="c188e-144">Error scenarios</span></span>

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

