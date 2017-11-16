---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
ms.openlocfilehash: 91b60a22580dcb8eae245f45e202710812522a64
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="powershellget-cmdlets-for-module-management"></a>Polecenia cmdlet PowerShellGet dla modułu zarządzania

- [Znajdź DscResource](https://technet.microsoft.com/en-us/library/mt654006.aspx)
- [Znajdź moduł](https://technet.microsoft.com/en-us/library/dn807167.aspx)
- [Znajdź skryptu](https://technet.microsoft.com/en-us/library/mt654001.aspx)
- [Get-InstalledModule](https://technet.microsoft.com/en-us/library/mt653990.aspx)
- [Get-InstalledScript](https://technet.microsoft.com/en-us/library/mt653994.aspx)
- [Get-PSRepository](https://technet.microsoft.com/en-us/library/dn807170.aspx)
- [Zainstaluj moduł](https://technet.microsoft.com/en-us/library/dn807162.aspx)
- [Skrypt instalacji](https://technet.microsoft.com/en-us/library/mt653998.aspx)
- [Nowe ScriptFileInfo](https://technet.microsoft.com/en-us/library/mt653995.aspx)
- [Publikowanie modułu](https://technet.microsoft.com/en-us/library/dn807163.aspx)
- [Publikowanie skryptu](https://technet.microsoft.com/en-us/library/mt654003.aspx)
- [Rejestr PSRepository](https://technet.microsoft.com/en-us/library/dn807168.aspx)
- [Moduł zapisywania](https://technet.microsoft.com/en-us/library/mt653992.aspx)
- [Zapisz skrypt](https://technet.microsoft.com/en-us/library/mt654004.aspx)
- [Zestaw PSRepository](https://technet.microsoft.com/en-us/library/dn807165.aspx)
- [ScriptFileInfo testu](https://technet.microsoft.com/en-us/library/mt654005.aspx)
- [Odinstaluj moduł](https://technet.microsoft.com/en-us/library/mt653996.aspx)
- [Odinstaluj skryptu](https://technet.microsoft.com/en-us/library/mt653989.aspx)
- [Moduł aktualizacji](https://technet.microsoft.com/en-us/library/dn807166.aspx)
- [ModuleManifest aktualizacji](https://technet.microsoft.com/en-us/library/mt654002.aspx)
- [Skrypt aktualizacji](https://technet.microsoft.com/en-us/library/mt653997.aspx)
- [ScriptFileInfo aktualizacji](https://technet.microsoft.com/en-us/library/mt653991.aspx)
- [Wyrejestruj PSRepository](https://technet.microsoft.com/en-us/library/dn807161.aspx)

## <a name="module-dependency-installation-support-get-installedmodule-and-uninstall-module-cmdlets"></a>Obsługa instalacji modułu zależności, Get-InstalledModule i polecenia cmdlet Uninstall-modułu
- W dodanym module populacji zależności w poleceniu cmdlet Publish-Module. Listy RequiredModules i NestedModules PSModuleInfo są używane w celu przygotowania na liście zależności modułu do opublikowania.
- Obsługa instalacji dodano zależności w polecenia cmdlet Install-Module i aktualizacji modułu. Moduł zależności są zainstalowane i zaktualizować domyślnie.
- Dodać parametr - IncludeDependencies do obejmują zależności modułu w wynikach polecenia cmdlet modułu Znajdź.
- Dodano obsługę - MaximumVersion w Module Znajdź moduł instalacji i polecenia cmdlet modułu aktualizacji.
- Dodano nowe Get InstalledModule i odinstalowywania modułu polecenia cmdlet.

## <a name="powershellget-cmdlets-demo-with-module-dependencies-support"></a>Obsługuje PowerShellGet pokaz poleceń cmdlet z modułu zależności:

### <a name="ensure-that-module-dependencies-are-available-on-the-repository"></a>Upewnij się, że moduł zależności są dostępne w repozytorium:
```powershell
Find-Module -Repository LocalRepo -Name RequiredModule1,RequiredModule2,RequiredModule3,NestedRequiredModule1,NestedRequiredModule2,NestedRequiredModule3 | Sort-Object -Property Name

Version    Name                     Repository    Description                  
-------    ----                     ----------    -----------                  
2.5        NestedRequiredModule1    LocalRepo     NestedRequiredModule1 module 
2.5        NestedRequiredModule2    LocalRepo     NestedRequiredModule2 module 
2.0        NestedRequiredModule3    LocalRepo     NestedRequiredModule3 module 
2.5        RequiredModule1          LocalRepo     RequiredModule1 module  
2.5        RequiredModule2          LocalRepo     RequiredModule2 module  
2.0        RequiredModule3          LocalRepo     RequiredModule3 module
```

### <a name="create-a-module-with-dependencies-that-are-specified-in-the-requiredmodules-and-nestedmodules-properties-of-its-module-manifest"></a>Utwórz moduł z zależnościami, które są określone we właściwościach RequiredModules i NestedModules w manifeście modułu.
```powershell
$RequiredModules = @('RequiredModule1',
                     @{ModuleName = 'RequiredModule2'; ModuleVersion = '1.5'; },
                     @{ModuleName = 'RequiredModule3'; RequiredVersion = '2.0'; })

$NestedRequiredModules = @('TestDepWithNestedRequiredModules1.psm1', 'NestedRequiredModule1',
                            @{ModuleName = 'NestedRequiredModule2'; ModuleVersion = '1.5'; },
                            @{ModuleName = 'NestedRequiredModule3'; RequiredVersion = '2.0'; })

New-ModuleManifest -Path 'C:\Program Files\WindowsPowerShell\Modules\TestDepWithNestedRequiredModules1\TestDepWithNestedRequiredModules1.psd1' `
-NestedModules $NestedRequiredModules -RequiredModules $RequiredModules -ModuleVersion "1.0" -Description "TestDepWithNestedRequiredModules1 module"
```

###  <a name="publish-two-versions-10-and-20-of-the-testdepwithnestedrequiredmodules1-module-with-dependencies-to-the-repository"></a>Publikowanie dwie wersje (**"1.0"** i **"2.0"**) modułu TestDepWithNestedRequiredModules1 zależności do repozytorium.
```powershell
Publish-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -NuGetApiKey "MyNuGet-ApiKey-For-LocalRepo"
```

###  <a name="find-the-testdepwithnestedrequiredmodules1-module-with-its-dependencies-by-specifying--includedependencies"></a>Znajdź moduł TestDepWithNestedRequiredModules1 z zależnościami, określając - IncludeDependencies.
```powershell
Find-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo –IncludeDependencies -MaximumVersion "1.0"

Version    Name                                Repository  Description 
-------    ----                                ----------  -----------  
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module  
2.5        RequiredModule1                     LocalRepo   RequiredModule1 module      
2.5        RequiredModule2                     LocalRepo   RequiredModule2 module      
2.0        RequiredModule3                     LocalRepo   RequiredModule3 module      
2.5        NestedRequiredModule1               LocalRepo   NestedRequiredModule1 module
2.5        NestedRequiredModule2               LocalRepo   NestedRequiredModule2 module
2.0        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
``` 

### <a name="use-find-module-metadata-to-find-the-module-dependencies"></a>Znajdź zależności modułu przy użyciu modułu Znajdź metadanych.
```powershell
$psgetModuleInfo = Find-Module -Repository MSPSGallery -Name ModuleWithDependencies2
$psgetModuleInfo.Dependencies.ModuleName

RequiredModule1
RequiredModule2
RequiredModule3
NestedRequiredModule1
NestedRequiredModule2
NestedRequiredModule3

$psgetModuleInfo.Dependencies

Name Value
---- -----
ModuleName RequiredModule1
CanonicalId PowerShellGet:RequiredModule1/#http://psget/psGallery/api/v2/

ModuleName RequiredModule2
ModuleVersion 2.0
CanonicalId PowerShellGet:RequiredModule2/2.0#http://psget/psGallery/api/v2/

ModuleName RequiredModule3
RequiredVersion 2.5
CanonicalId PowerShellGet:RequiredModule3/2.5#http://psget/psGallery/api/v2/

ModuleName NestedRequiredModule1
CanonicalId PowerShellGet:NestedRequiredModule1/#http://psget/psGallery/api/v2/

ModuleName NestedRequiredModule2
ModuleVersion 2.0
CanonicalId PowerShellGet:NestedRequiredModule2/2.0#http://psget/psGallery/api/v2/

ModuleName NestedRequiredModule3
RequiredVersion 2.5
CanonicalId PowerShellGet:NestedRequiredModule3/2.5#http://psget/psGallery/api/v2/
```

###  <a name="install-the-testdepwithnestedrequiredmodules1-module-with-dependencies"></a>Zainstaluj moduł TestDepWithNestedRequiredModules1 z zależności.
```powershell
Install-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -RequiredVersion "1.0"
Get-InstalledModule

Version    Name                    Repository   Description                 
-------    ----                    ----------   -----------                 
1.0        NestedRequiredModule1   LocalRepo    NestedRequiredModule1 module
2.5        NestedRequiredModule2   LocalRepo    NestedRequiredModule2 module
2.0        NestedRequiredModule3   LocalRepo    NestedRequiredModule3 module
1.0        RequiredModule1         LocalRepo    RequiredModule1 module      
2.5        RequiredModule2                    LocalRepo    RequiredModule2 module 
2.0        RequiredModule3                    LocalRepo    RequiredModule3 module 
1.0        TestDepWithNestedRequiredModules1  LocalRepo    TestDepWithNestedRequiredModules1 module
```

###  <a name="update-the-testdepwithnestedrequiredmodules1-module-with-dependencies"></a>Zaktualizuj moduł TestDepWithNestedRequiredModules1 z zależności.
```powershell
Find-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -AllVersions

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module

Update-Module -Name TestDepWithNestedRequiredModules1 -RequiredVersion 2.0
Get-InstalledModule

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        NestedRequiredModule1               LocalRepo   NestedRequiredModule1 module
2.5        NestedRequiredModule2               LocalRepo   NestedRequiredModule2 module
2.0        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
2.5        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
1.0        RequiredModule1                     LocalRepo   RequiredModule1 module
2.5        RequiredModule2                     LocalRepo   RequiredModule2 module
2.0        RequiredModule3                     LocalRepo   RequiredModule3 module
2.5        RequiredModule3                     LocalRepo   RequiredModule3 module
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
```

###  <a name="run-the-uninstall-module-cmdlet-to-uninstall-a-module-that-you-installed-by-using-powershellget"></a>Uruchom polecenie cmdlet Uninstall-Module, aby odinstalować moduł, który został zainstalowany przy użyciu PowerShellGet.
Jeśli inny moduł zależy od moduł, który chcesz usunąć, PowerShellGet zgłasza błąd.
```powershell
Get-InstalledModule -Name RequiredModule1 | Uninstall-Module

PackageManagement\Uninstall-Package : The module 'RequiredModule1' of version '2.5' in module base folder 'C:\Program Files\WindowsPowerShell\Modules\RequiredModule1\2.5' cannot be uninstalled, because one or more other modules 'ModuleWithDependencies2' are dependent on this module. Uninstall the modules that depend on this module before uninstalling module 'RequiredModule1'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\PSGet.psm1:1303 char:25
+ ... $null = PackageManagement\\Uninstall-Package @PSBoundParameters
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo : InvalidOperation: (Microsoft.Power...ninstallPackage:UninstallPackage) [Uninstall-Package], Exception
+ FullyQualifiedErrorId : UnableToUninstallAsOtherModulesNeedThisModule,Uninstall-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.UninstallPackage
```

## <a name="save-module-cmdlet"></a>Polecenia cmdlet modułu zapisywania
```powershell
Save-Module -Repository MSPSGallery -Name ModuleWithDependencies2 -Path C:\MySavedModuleLocation
dir C:\MySavedModuleLocation

Directory: C:\MySavedModuleLocation

Mode LastWriteTime Length Name
---- ------------- ------ ----
d----- 4/21/2015 5:40 PM ModuleWithDependencies2
d----- 4/21/2015 5:40 PM NestedRequiredModule1
d----- 4/21/2015 5:40 PM NestedRequiredModule2
d----- 4/21/2015 5:40 PM NestedRequiredModule3
d----- 4/21/2015 5:40 PM RequiredModule1
d----- 4/21/2015 5:40 PM RequiredModule2
d----- 4/21/2015 5:40 PM RequiredModule3
```

## <a name="update-modulemanifest-cmdlet"></a>Polecenie cmdlet Update-ModuleManifest
To nowe polecenie cmdlet służy do aktualizacji pliku z wartościami właściwości wejściowej manifestu. Trwa wszystkich parametrów, które jest ModuleManifest testu.

Zauważymy, że wiele autorów modułu czy chcesz określić "\*" w wartości wyeksportowanej, takie jak FunctionsToExport, CmdletsToExport, itp. Podczas publikowania modułu w galerii programu PowerShell, nieokreślone funkcji i poleceń nie zostaną wypełnione prawidłowo na galerii. W związku z tym sugerujemy aktualizowanie autorów modułu ich manifestów odpowiednie wartości.

Jeśli masz modułów, które zostały wyeksportowane właściwości ModuleManifest aktualizacji spowoduje wypełnienie wybranego pliku manifestu z informacjami z eksportowane funkcje, polecenia cmdlet, zmienne itp:
```powershell
Get-Content -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
@{
# Script module or binary module file associated with this manifest.
# RootModule = ''
# Version number of this module.
ModuleVersion = '2.5'
# ID used to uniquely identify this module
GUID = '610e5c5b-dc42-4eaa-8511-ebfb44066d5e'

#(Other properties removed here for Simplicity…)

# Functions to export from this module
FunctionsToExport = '*'
# Cmdlets to export from this module
CmdletsToExport = '*'
# Variables to export from this module
VariablesToExport = '*'
# Aliases to export from this module
AliasesToExport = '*'
}
```

Po ModuleManifest aktualizacji:
```powershell
Update-ModuleManifest -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
Get-Content -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
#
# Module manifest for module 'NewManifest'
#
# Generated by: author name
#
# Generated on: 11/13/2015
#
@{
# Script module or binary module file associated with this manifest.
# RootModule = ''
# Version number of this module.
ModuleVersion = '2.5'
# ID used to uniquely identify this module
GUID = '610e5c5b-dc42-4eaa-8511-ebfb44066d5e'
# Functions to export from this module
FunctionsToExport = 'Get-FooFn Get-FooWF'
# Cmdlets to export from this module
CmdletsToExport = 'Test-PSGetTestCmdlet'
}
```

Dla każdego modułu są również pola metadanych skojarzonych z nim. Aby prawidłowo wyświetlić metadanych w galerii PowrShell, ModuleManifest aktualizacji służy do wypełniania tych pól w obszarze PrivateData.
```powershell
Update-ModuleManifest -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1" -Tags "Tag1" -LicenseUri "http://license.com" -ProjectUri "http://project.com" -IconUri "http://icon.com" -ReleaseNotes "Test module"
```
Hashtable PrivateData z szablonu pliku manifestu ma następujące właściwości:
```powershell
# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{
    PSData = @{
        # Tags applied to this module. These help with module discovery in online galleries.
        # Tags = @()

        # A URL to the license for this module.
        # LicenseUri = ''
    
        # A URL to the main website for this project.
        # ProjectUri = ''
        
        # A URL to an icon representing this module.
        # IconUri = ''
        
        # ReleaseNotes of this module
        # ReleaseNotes = ''
        
        # External dependent modules of this module
        # ExternalModuleDependencies = ''
    } # End of PSData hashtable
} # End of PrivateData hashtable
```
***Uwaga:*** DscResourcesToExport jest obsługiwana tylko w najnowszej programu PowerShell w wersji 5.0. Firma Microsoft nie można zaktualizować pola, jeśli są uruchomione na poprzedniej wersji programu PowerShell.

