---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 134c22efe4fb86045ffb326e109dfbcc741bcf2f
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="packagemanagement-cmdlets"></a>Polecenia cmdlet PackageManagement
Jest to podstawowy PackageManagement do obsługi oprogramowania odnajdywania, instalacji i magazynu (SDII). Wypróbowanie poleceń cmdlet do tych operacji:
-   Znajdź pakiet
-   Find-PackageProvider
-   Get-Package
-   Get-PackageProvider
-   Get-PackageSource
-   Import-PackageProvider
-   Pakiet instalacyjny
-   Install-PackageProvider
-   Register-PackageSource
-   Save-Package
-   Set-PackageSource
-   Uninstall-Package
-   Unregister-PackageSource

PackageManagement jest moduł programu PowerShell, można wykonać następujące czynności, aby zaktualizować PackageManagement się:
```powershell
PS C:\> Install-Module PackageManagement –Force
```
W takim przypadku będzie musiał ponownie wprowadzić sesji programu PowerShell, aby przełączyć się do nowej wersji PackageManagement.

## <a name="find-package-cmdlethttpstechnetmicrosoftcomlibrarydn890709aspx"></a>[Znajdź pakiet polecenia Cmdlet](https://technet.microsoft.com/library/dn890709.aspx)
To polecenie cmdlet pozwala odnajdywania pakietów oprogramowania w źródłach dostępne pakietu przy użyciu załadować dostawców pakietu.
```powershell
# Find all available Windows PowerShell module packages from galleries registered
# with PowerShellGet provider
Find-Package -Provider PowerShellGet -Source PSGallery

# Find a package from a provider that is not yet installed
# This will bootstrap NuGet provider and then search for jquery package using NuGet
# with <http://www.nuget.org/api/v2/> as source
Find-Package -Name jquery –Provider NuGet -Source http://www.nuget.org/api/v2/

# Find package with name and version
# Here we are assuming that the user already registered nuget.org using
# Register-PackageSource. You can specify either the provider or the source, or
# neither. For the latter, performance may be less optimal as it searches through all
# the providers and registered sources.
Find-Package -Name jquery –Provider NuGet –RequiredVersion 2.1.4 -Source nuget.org
```

## <a name="find-packageprovider-cmdlethttpstechnetmicrosoftcomlibrarymt676544aspx"></a>[Znajdź PackageProvider polecenia Cmdlet](https://technet.microsoft.com/library/mt676544.aspx)
Polecenia cmdlet Find PackageProvider znajduje zgodnych dostawców PackageManagement, które są dostępne w zarejestrowany PowerShellGet źródeł pakietów. Są dostępne do zainstalowania za pomocą polecenia cmdlet Install-PackageProvider dostawców pakietu. Domyślnie w tym moduły dostępne w galerii programu PowerShell z 'PackageManagement' i 'Provider' tagów. 

Znajdź PackageProvider znajduje się także zgodnych dostawców PackageManagement, które są dostępne w magazynie obiektów blob platformy azure PackageManagement, której używamy dostawcy boostrapper PackageManagement do znajdowania i instalowania ich.
```powershell
#Find all available package providers in PackageManagement azure blob store as well as in PowerShellGallery.com
Find-PackageProvider

#Find all versions of a provider
Find-PackageProvider -Name "Nuget" -AllVersions

#Find a provider from a specified source
Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

## <a name="get-package-cmdlethttpstechnetmicrosoftcomlibrarydn890704aspx"></a>[Get-Package Cmdlet](https://technet.microsoft.com/library/dn890704.aspx)
To polecenie cmdlet zwraca listę wszystkich pakietów oprogramowania, które zostały zainstalowane przy użyciu PackageManagement.
```powershell
# Get all the packages installed by Programs provider
Get-Package –Provider Programs

# Get all the packages installed by NuGet provider at c:\test using the dynamic
# parameter destination
Get-Package –Provider NuGet -Destination c:\test
```

## <a name="get-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890703aspx"></a>[Polecenie Cmdlet Get-PackageProvider](https://technet.microsoft.com/en-us/library/dn890703.aspx)
Pakiet dostawców, którzy są załadowane i gotowa do użycia na komputerze lokalnym można ewidencjonowaniu za pomocą polecenia cmdlet.
```powershell
# Get all currently loaded package providers
Get-PackageProvider

# The following cmdlet will show all the package providers available on the machine (including those that are not loaded):
Get-PackageProvider -ListAvailable
```

## <a name="get-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890705aspx"></a>[Get-PackageSource Cmdlet](https://technet.microsoft.com/en-us/library/dn890705.aspx)
To polecenie cmdlet pobiera listę źródła pakietów, które są zarejestrowane dla dostawcy pakietu.
```powershelll
# Get all package sources
Get-PackageSource

# Get all package sources for a specific provider
Get-PackageSource –ProviderName PowerShellGet
```

## <a name="import-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarymt676545aspx"></a>[Polecenia Cmdlet Import-PackageProvider](https://technet.microsoft.com/en-us/library/mt676545.aspx)
To polecenie cmdlet dodaje dostawców pakietu pakietu zarządzania do bieżącej sesji.
```powershell
# Import a package provider from the local machine
Import-PackageProvider –Name MyProvider

#The -Name parameter can be either the name of the provider or the full path to the provider. Currently, we support .dll, .exe and.psm1 for the full path case. If the name of the provider is used for the -Name parameter, then additional version parameters such as -RequiredVersion, -MinimumVersion and -MaximumVersion may be specified. Otherwise, the latest version of the provider will be imported.

#If a package provider is not yet loaded to your system, we can discover and install on-demand. You can use explicit discovery and install cmdlets to do so:
 Find-PackageProvider
 Install-PackageProvider –Name MyProvider

#After installed, follow the Import-PackageProvider to load it to your system.

# Import a specific version of a package provider. PackageManagement supports installations of multiple versions of a package provider using PackageProvider cmdlets (not by bootstrapper provider). You can install another version of a package provider given that you already have one up running by:
Find-PackageProvider –Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force
Get-PackageProvider –ListAvailable
Import-PackageProvider –Name "Nuget" -RequiredVersion "2.8.5.201" -Verbose
Import-PackageProvider –Name MyProvider –RequiredVersion xxxx -force
```

##<a name="-install-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890711aspx"></a>[ Polecenia Cmdlet Install-Package](https://technet.microsoft.com/en-us/library/dn890711.aspx)

To polecenie cmdlet umożliwia instalację pakietów oprogramowania w źródłach dostępne pakietu przy użyciu załadować dostawców pakietu.
```powershell
# Install a package by name.
# NuGet provider requires us to provide the dynamic parameter destination path
# when we use this provider to install. Not all providers will require you to supply
# dynamic parameters for PackageManagement cmdlets.
Install-Package -Name jquery -Source nuget.org -Destination c:\test

# Install a package by piping.
Find-Package -Name jquery –Provider NuGet | Install-Package -Destination c:\test
```

## <a name="install-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarymt676543aspx"></a>[Polecenia Cmdlet Install-PackageProvider](https://technet.microsoft.com/en-us/library/mt676543.aspx)
To polecenie cmdlet instaluje co najmniej jednego dostawcy pakietu zarządzania pakietami.
```powershell
# Install a package provider from the PowerShell Gallery
Install-PackageProvider –Name "Gistprovider" -Verbose

# Install a specified version of a package provider
Find-PackageProvider –Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force

# Find a provider and install it
Find-PackageProvider –Name "Gistprovider" | Install-PackageProvider -Verbose

# Install a provider to the current user’s module folder
Install-PackageProvider –Name Gistprovider –Verbose –Scope CurrentUser
```

## <a name="register-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890701aspx"></a>[Register-PackageSource Cmdlet](https://technet.microsoft.com/en-us/library/dn890701.aspx)
To polecenie cmdlet dodaje źródła pakietów dla dostawcy określonego pakietu.
Każdy dostawca PackageManagement może mieć jeden lub kilka źródeł oprogramowania lub repozytoriów. PackageManagement udostępnia polecenia cmdlet programu PowerShell Dodaj/Usuń/zapytania źródła. Na przykład można zarejestrować źródła pakietów dla dostawcy NuGet:
```powershell
Register-PackageSource -Name "NugetSource" -Location "http://www.nuget.org/api/v2" –ProviderName nuget
```

## <a name="save-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890708aspx"></a>[Polecenia Cmdlet zapisywania pakietu](https://technet.microsoft.com/en-us/library/dn890708.aspx)
To polecenie cmdlet zapisuje pakietów na komputerze lokalnym, bez konieczności instalowania ich.
```powershell
# Saves jquery package to c:\test using NuGetProvider
# Notes that the -Path parameter must point to an existing location
Save-Package -Name jquery –Provider NuGet -Path c:\test

# Save a package by piping.
Find-Package -Name jquery -Source http://www.nuget.org/api/v2/ | Save-Package -Path c:\test
Find-Package -source c:\test
```

## <a name="set-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890710aspx"></a>[Set-PackageSource Cmdlet](https://technet.microsoft.com/en-us/library/dn890710.aspx)
To polecenie cmdlet zmienia informacje o istniejącym źródle pakietu. 
```powershell
#Set-PackageSource changes the values for a source that has already been registered by running the Register-PackageSource cmdlet. By #running Set-PackageSource, you can change the source name and location.
Set-PackageSource  -Name nuget.org -Location  http://www.nuget.org/api/v2 -NewName nuget2 -NewLocation https://www.nuget.org/api/v2 
```

## <a name="uninstall-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890702aspx"></a>[Uninstall-Package Cmdlet](https://technet.microsoft.com/en-us/library/dn890702.aspx)
To polecenie cmdlet odinstalowuje pakietów zainstalowanych na komputerze lokalnym.
```powershell
# Uninstall jquery using nuget
Uninstall-Package -Name jquery –Provider NuGet -Destination c:\test

# Uninstall a package with by piping with Get-Package
Get-Package -Name jquery –Provider NuGet -Destination c:\test | Uninstall-Package
```

## <a name="unregister-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890707aspx"></a>[Unregister-PackageSource Cmdlet](https://technet.microsoft.com/en-us/library/dn890707.aspx)
```powershell
# Unregister a package source for the NuGet provider. You can use command Unregister-PackageSource, to disconnect with a repository, and Get-PackageSource, to discover what the repositories are associated with that provider.
Unregister-PackageSource  -Name "NugetSource"
```

