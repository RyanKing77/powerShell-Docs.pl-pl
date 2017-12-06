---
ms.date: 2017-10-17
contributor: keithb
ms.topic: reference
keywords: Galeria, programu powershell, polecenia cmdlet, psget
title: PrereleaseScript
ms.openlocfilehash: 2787e63944953d631b079f9e86a60ea5f3da768f
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2017
---
# <a name="prerelease-versions-of-scripts"></a>Wersje wstępne skryptów

Począwszy od wersji 1.6.0 PowerShellGet i galerii programu PowerShell zapewniają obsługę znakowania w wersjach nowszych niż 1.0.0 jako wstępnej wersji. Przed tej funkcji wersji wstępnej elementy były ograniczone do o wersji, począwszy od 0. Celem tych funkcji jest zapewniają lepsze wsparcie [v1.0.0 programu SemVer](http://semver.org/spec/v1.0.0.html) Konwencji versioning bez przerywania zapewnienia zgodności z programu PowerShell 3 i powyżej lub istniejącej wersji programu PowerShellGet. Ten temat koncentruje się na funkcji specyficznych dla skryptu. Są równoważne funkcje dla modułów [wstępnej wersji modułu](../module/PrereleaseModule.md) tematu. Korzystanie z tych funkcji, wydawców można zidentyfikować skrypt jako 2.5.0-alpha wersji, a później Zwolnij wersji gotowe do produkcji 2.5.0 zastępuje wersji wstępnej. 

Na wysokim poziomie funkcje wersji wstępnej skryptu obejmują:

* Dodanie sufiksu PrereleaseString ciąg wersji w manifeście skryptu. Gdy skryptów zostanie opublikowany w galerii programu PowerShell, te dane są wyodrębniane w manifeście i używany do identyfikowania wstępnej elementów.
* Uzyskiwanie elementów wstępnej wymaga Dodawanie flagi - AllowPrerelease do polecenia PowerShellGet Znajdź skryptów skrypt instalacji skryptu aktualizacji i Zapisz skrypt. Jeśli nie określono flagę, nie można wyświetlić elementy wersji wstępnej. 
* Wersje skryptu wyświetlane przez skrypt Znajdź, Get-InstalledScript i w galerii programu PowerShell zostanie wyświetlony z PrereleaseString, tak jak 2.5.0-alpha. 

Poniżej znajdują się szczegółowe informacje dotyczące funkcji. 


## <a name="identifying-a-script-version-as-a-prerelease"></a>Identyfikowanie jako wersja wstępna wersja skryptu 

Obsługa PowerShellGet wersje wstępne jest łatwiej niż moduły skryptów. Przechowywanie wersji skryptu jest obsługiwana przez PowerShellGet, tylko, dlatego nie ma żadnych problemów ze zgodnością spowodowane przez dodanie ciągu wersji wstępnej. Aby zidentyfikować skryptu w galerii programu PowerShell jako wstępnej wersji, należy dodać sufiks wersji wstępnej do ciąg wersji poprawnie sformatowana w metadanych skryptu. 

Przykład części manifestu skryptu z wersji wstępnej może wyglądać następująco:
```powershell
<#PSScriptInfo
            
.VERSION 3.2.1-alpha12
            
.GUID 

...

#>

```

Aby używać sufiksu wstępnej, ciąg wersji musi spełniać następujące wymagania: 

* Sufiks wstępnej może być określona tylko w przypadku wersji 3 segmentów dla Major.Minor.Build. Jest to zgodne z programu SemVer v1.0.0
* Wstępna sufiks jest ciągiem, który rozpoczyna się od łącznika i może zawierać alfanumeryczne ASCII [0-9A-Za - z —]
* Tylko ciągi wersji wstępnej programu SemVer v1.0.0 są obsługiwane w tej chwili tak wstępnej sufiks __nie mogą__ zawierać albo okres lub + [. +], które są dozwolone w programu SemVer 2.0 
* Przykłady obsługiwanych ciągów PrereleaseString:-alfa, - 1,-BETA, - update20171020

__Wpływ wersji wstępnej w folderach instalacji i kolejność sortowania__

Kolejność sortowania zmian za pomocą wersji wstępnej, co jest ważne podczas publikowania w galerii programu PowerShell, a podczas instalowania skryptów przy użyciu polecenia PowerShellGet. Jeśli dwa skrypty wersji z numerem wersji istnieje, kolejność sortowania jest oparta na części ciągu po łącznik. Tak 2.5.0-alpha wersji jest mniejsza niż 2.5.0-beta, czyli mniej niż 2.5.0-gamma. Jeśli dwa skrypty mają ten sam numer wersji i tylko jeden z nich ma PrereleaseString, skrypt __bez__ wstępnej sufiks zakłada, że wersja gotowe do produkcji i będą sortowane jako wersja większa niż wstępną Wersja. Na przykład podczas porównywania zwalnia 2.5.0 i 2.5.0-beta, 2.5.0 wersji będą uznawane za większa niż dwa. 

Podczas publikowania w galerii programu PowerShell, domyślnie wersji skryptu publikowaną muszą mieć wyższej wersji niż wersja wszystkie wcześniej publikowane w galerii programu PowerShell. Wydawcą może zaktualizować 2.5.0-alpha wersji 2.5.0-beta lub 2.5.0 (sufiksem nie wstępnej).

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a>Wyszukiwanie i pobieranie elementów wstępnej za pomocą polecenia PowerShellGet

Zajmujących się wstępnej elementów za pomocą skryptu-PowerShellGet Znajdź skryptów, skrypt instalacji aktualizacji, i Zapisz skrypt poleceń wymaga Dodawanie flagi - AllowPrerelease. Jeśli określono - AllowPrerelease, elementy wstępnej można włączyć, jeśli są obecne.
Jeśli nie określono flagę - AllowPrerelease, nie można wyświetlić elementy wersji wstępnej. 

Tylko wyjątki od tej reguły w poleceń skryptu PowerShellGet są Get InstalledScript i czasami z skrypt dezinstalacji skryptu. 

* Get-InstalledScript zawsze automatycznie wyświetli informacje o wersji wstępnej w ciągu wersji Jeśli jest obecny. 
* Odinstaluj skryptu domyślnie odinstaluje najnowszej wersji skryptu, jeśli __nie została zainstalowana wersja__ jest określona. To zachowanie nie została zmieniona. Jednak jeśli wstępna wersja jest określona za pomocą - RequiredVersion, - AllowPrerelease będzie wymagane. 

## <a name="examples"></a>Przykłady
```powershell
# Assume the PowerShell Gallery has TestPackage versions 1.8.0 and 1.9.0-alpha. If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> Find-Script TestPackage 

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Find-Script TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# To install a prerelease, you must specify -AllowPrerelease. Specifying a prerelease version string is not sufficient. 

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha
PackageManagement\Find-Package : No match was found for the specified search criteria and script name 'TestPackage'.
Try Get-PSRepository to see all available registered script repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exceptio
   n
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# Note that Get-InstalledScript shows the prerelease version. 
# If -RequiredVersion is not specified, all installed scripts will be displayed by Get-InstalledScript
```

Odinstaluj skryptu spowoduje usunięcie bieżącej wersji skryptu po - RequiredVersion nie jest dostarczony. Jeśli określono - RequiredVersion i jest wersja wstępna, - AllowPrerelease należy dodać do polecenia. 

``` powershell
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha
Uninstall-Script: The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Unnstall-Script TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Script], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninnstall-script


C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
# Since script versions are not installed side-by-side, the above could be simply "Uninstall-Script TestPackage"

C:\windows\system32> Get-Installedscript TestPackage
PackageManagement\Get-Package : No match was found for the specified search criteria and script names 'testpackage'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.5.0.0\PSModule.psm1:4088 char:9
+         PackageManagement\Get-Package @PSBoundParameters | Microsoft. ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...lets.GetPackage:GetPackage) [Get-Package], Exception
    + FullyQualifiedErrorId : NoMatchFound,Microsoft.PowerShell.PackageManagement.Cmdlets.GetPackage


```



## <a name="more-details"></a>więcej informacji
### <a name="prerelease-module-versionsmoduleprereleasemodulemd"></a>[Wersji wstępnej modułów](../module/PrereleaseModule.md)
### <a name="find-scriptpsgetfind-scriptmd"></a>[Znajdź skryptu](./psget_find-script.md)
### <a name="install-scriptpsgetinstall-scriptmd"></a>[Skrypt instalacji](./psget_install-script.md)
### <a name="save-scriptpsgetsave-scriptmd"></a>[Zapisz skrypt](./psget_save-script.md)
### <a name="update-scriptpsgetupdate-scriptmd"></a>[Skrypt aktualizacji](./psget_update-script.md)
### <a name="get-installedscriptpsgetget-installedscriptmd"></a>[Get-Installedscript](./psget_get-installedscript.md)
### <a name="uninstall-scriptpsgetuninstall-scriptmd"></a>[Odinstaluj skryptu](./psget_uninstall-script.md)
