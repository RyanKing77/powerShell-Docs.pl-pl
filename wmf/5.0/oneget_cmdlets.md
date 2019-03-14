---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 042e9a30068d32dc5860255bdec960371121d866
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795100"
---
# <a name="packagemanagement-cmdlets"></a>Polecenia cmdlet funkcji PackageManagement

Jest to podstawowy PackageManagement do obsługi oprogramowania, odnajdywania, instalowania i inwentaryzacji. Wypróbuj poleceń cmdlet dla tych operacji:

- `Find-Package`
- `Find-PackageProvider`
- `Get-Package`
- `Get-PackageProvider`
- `Get-PackageSource`
- `Import-PackageProvider`
- `Install-Package`
- `Install-PackageProvider`
- `Register-PackageSource`
- `Save-Package`
- `Set-PackageSource`
- `Uninstall-Package`
- `Unregister-PackageSource`

Podobnie jak PackageManagement modułu programu PowerShell, można wykonać następujące polecenie, aby zaktualizować PackageManagement sam:

```powershell
Install-Module PackageManagement –Force
```

W takim przypadku konieczne będzie ponowne wprowadzenie sesji programu PowerShell, aby przełączyć się do nowej wersji PackageManagement.

## <a name="find-package-cmdletpowershellmodulepackagemanagementfind-package"></a>[Znajdź pakiet polecenia Cmdlet](/powershell/module/PackageManagement/Find-Package)

To polecenie cmdlet umożliwia odnajdywanie pakietów oprogramowania w źródłach pakiet przy użyciu załadować dostawców pakietu.

```powershell
# Find all available Windows PowerShell module packages from galleries registered
# with PowerShellGet provider
Find-Package -ProviderName PowerShellGet -Source as source
Find-Package -Name jquery –Provider NuGet -Source http://www.nuget.org/api/v2/

# Find package with name and version
# Here we are assuming that the user already registered nuget.org using
# Register-PackageSource. You can specify either the provider or the source, or
# neither. For the latter, performance may be less optimal as it searches through all
# the providers and registered sources.
Find-Package -Name jquery –Provider NuGet –RequiredVersion 2.1.4 -Source nuget.org
```

## <a name="find-packageprovider-cmdletpowershellmodulepackagemanagementfind-packageprovider"></a>[Find-PackageProvider Cmdlet](/powershell/module/PackageManagement/Find-PackageProvider)

`Find-PackageProvider` Polecenie cmdlet umożliwia znalezienie dopasowania PackageManagement dostawców, które są dostępne w źródeł pakietów zarejestrowane przy użyciu funkcji PowerShellGet. Są one dostępne do zainstalowania przy użyciu dostawcy pakietu `Install-PackageProvider` polecenia cmdlet. Domyślnie w tym moduły dostępne w galerii programu PowerShell przy użyciu tagów "Provider" i "PackageManagement".

`Find-PackageProvider` Wyszukuje również zgodnych dostawców PackageManagement, które są dostępne w magazynie obiektów blob platformy azure PackageManagement, której używamy dostawcy boostrapper PackageManagement do znajdowania i instalowania ich.

```powershell
#Find all available package providers in PackageManagement azure blob store as well as in PowerShellGallery.com
Find-PackageProvider

#Find all versions of a provider
Find-PackageProvider -Name "Nuget" -AllVersions

#Find a provider from a specified source
Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

## <a name="get-package-cmdletpowershellmodulepackagemanagementget-package"></a>[Polecenie Cmdlet Get-Package](/powershell/module/PackageManagement/Get-Package)

To polecenie cmdlet zwraca listę wszystkich pakietów oprogramowania, które zostały zainstalowane za pomocą modułu PackageManagement.

```powershell
# Get all the packages installed by Programs provider
Get-Package –Provider Programs

# Get all the packages installed by NuGet provider at c:\test using the dynamic
# parameter destination
Get-Package –Provider NuGet -Destination c:\test
```

## <a name="get-packageprovider-cmdletpowershellmodulepackagemanagementget-packageprovider"></a>[Get-PackageProvider Cmdlet](/powershell/module/PackageManagement/Get-PackageProvider)

Dostawcy pakietu, które są ładowane i gotowe do użycia na komputerze lokalnym można spisywany używając polecenia cmdlet.

```powershell
# Get all currently loaded package providers
Get-PackageProvider

# The following cmdlet will show all the package providers available on the machine (including those that are not loaded):
Get-PackageProvider -ListAvailable
```

## <a name="get-packagesource-cmdletpowershellmodulepackagemanagementget-packagesource"></a>[Get-PackageSource Cmdlet](/powershell/module/PackageManagement/Get-PackageSource)

To polecenie cmdlet pobiera listę źródeł pakietów, które są zarejestrowane dla dostawcy pakietu.

```powershell
# Get all package sources
Get-PackageSource

# Get all package sources for a specific provider
Get-PackageSource –ProviderName PowerShellGet
```

## <a name="import-packageprovider-cmdletpowershellmodulepackagemanagementimport-packageprovider"></a>[Import-PackageProvider Cmdlet](/powershell/module/PackageManagement/Import-PackageProvider)

To polecenie cmdlet umożliwia dodawanie dostawców pakietu zarządzania pakietami do bieżącej sesji.

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

## <a name="install-package-cmdletpowershellmodulepackagemanagementinstall-package"></a>[Polecenia Cmdlet Install-Package](/powershell/module/PackageManagement/Install-Package)

To polecenie cmdlet umożliwia instalację pakietów oprogramowania w źródłach pakiet przy użyciu załadować dostawców pakietu.

```powershell
# Install a package by name.
# NuGet provider requires us to provide the dynamic parameter destination path
# when we use this provider to install. Not all providers will require you to supply
# dynamic parameters for PackageManagement cmdlets.
Install-Package -Name jquery -Source nuget.org -Destination c:\test

# Install a package by piping.
Find-Package -Name jquery –Provider NuGet | Install-Package -Destination c:\test
```

## <a name="install-packageprovider-cmdletpowershellmodulepackagemanagementinstall-packageprovider"></a>[Install-PackageProvider Cmdlet](/powershell/module/PackageManagement/Install-PackageProvider)

To polecenie cmdlet instaluje przynajmniej jednego dostawcy pakietu zarządzania pakietami.

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

## <a name="register-packagesource-cmdletpowershellmodulepackagemanagementregister-packagesource"></a>[Register-PackageSource Cmdlet](/powershell/module/PackageManagement/Register-PackageSource)

To polecenie cmdlet dodaje źródło pakietu dla dostawcy określonego pakietu.
Każdy dostawca PackageManagement może mieć jednego lub kilku źródeł oprogramowania lub repozytoriów. PackageManagement udostępnia polecenia cmdlet programu PowerShell do dodawania/usuwania/query źródła. Na przykład można zarejestrować źródło pakietu dla dostawcy NuGet:

```powershell
Register-PackageSource -Name "NugetSource" -Location "http://www.nuget.org/api/v2" –ProviderName nuget
```

## <a name="save-package-cmdletpowershellmodulepackagemanagementsave-package"></a>[Polecenie Cmdlet Save-Package](/powershell/module/PackageManagement/Save-Package)

To polecenie cmdlet zapisuje pakietów na komputerze lokalnym bez instalowania ich.

```powershell
# Saves jquery package to c:\test using NuGetProvider
# Notes that the -Path parameter must point to an existing location
Save-Package -Name jquery –Provider NuGet -Path c:\test

# Save a package by piping.
Find-Package -Name jquery -Source http://www.nuget.org/api/v2/ | Save-Package -Path c:\test
Find-Package -Source c:\test
```

## <a name="set-packagesource-cmdletpowershellmodulepackagemanagementset-packagesource"></a>[Set-PackageSource Cmdlet](/powershell/module/PackageManagement/Set-PackageSource)

To polecenie cmdlet zmienia informacje o istniejącym źródle pakietu.

```powershell
#Set-PackageSource changes the values for a source that has already been registered by running the Register-PackageSource cmdlet. By #running Set-PackageSource, you can change the source name and location.
Set-PackageSource  -Name nuget.org -Location  http://www.nuget.org/api/v2 -NewName nuget2 -NewLocation https://www.nuget.org/api/v2
```

## <a name="uninstall-package-cmdletpowershellmodulepackagemanagementuninstall-package"></a>[Polecenia Cmdlet Odinstaluj pakiet](/powershell/module/PackageManagement/Uninstall-Package)

To polecenie cmdlet powoduje odinstalowanie pakietów zainstalowanych na komputerze lokalnym.

```powershell
# Uninstall jquery using nuget
Uninstall-Package -Name jquery –Provider NuGet -Destination c:\test

# Uninstall a package with by piping with Get-Package
Get-Package -Name jquery –Provider NuGet -Destination c:\test | Uninstall-Package
```

## <a name="unregister-packagesource-cmdletpowershellmodulepackagemanagementunregister-packagesource"></a>[Unregister-PackageSource Cmdlet](/powershell/module/PackageManagement/Unregister-PackageSource)

```powershell
# Unregister a package source for the NuGet provider. You can use command Unregister-PackageSource, to disconnect with a repository, and Get-PackageSource, to discover what the repositories are associated with that provider.
Unregister-PackageSource  -Name "NugetSource"
```