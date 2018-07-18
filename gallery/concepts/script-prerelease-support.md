---
ms.date: 10/17/2017
contributor: keithb
keywords: Galeria, programu powershell, polecenie cmdlet, psget
title: Wersje wstępne skryptów
ms.openlocfilehash: 7d4cec9d2b4ee5ad0b19ad5d9c68bb68747abd57
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093852"
---
# <a name="prerelease-versions-of-scripts"></a>Wersje wstępne skryptów

Począwszy od wersji 1.6.0 modułu PowerShellGet oraz spełnione galerii programu PowerShell zapewniają obsługę tagowania w wersjach nowszych niż 1.0.0 jako wersji wstępnej. Przed tej funkcji wersji wstępnej elementy były korzystać z wersji począwszy od 0. Celem tych funkcji jest zapewniają lepsze wsparcie [1.0.0 SemVer](http://semver.org/spec/v1.0.0.html) Konwencji wersji bez przerywania wstecznej zgodności przy użyciu programu PowerShell 3 i powyżej lub istniejącej wersji programu PowerShellGet. Ten temat koncentruje się na funkcji specyficznych dla skryptu. Równoważne funkcje dla modułów znajdują się w [wersje modułu wersję wstępną](module-prerelease-support.md) tematu. Korzystając z tych funkcji, wydawców można skrypt jako 2.5.0-alpha wersji i później wydanej wersji gotowe do produkcji 2.5.0, która zastępuje wersję wstępną.

Na wysokim poziomie funkcje wersji wstępnej skryptu obejmują:

- Dodanie do ciąg wersji w manifeście skrypt sufiksu PrereleaseString. Po opublikowaniu skrypty w galerii programu PowerShell te dane są wyodrębniane z manifestu i używany do identyfikowania elementów wersji wstępnej.
- Pobieranie elementów wstępnych wymaga dodanie flagi - AllowPrerelease poleceń modułu PowerShellGet Find-Script skrypt instalacji skryptu aktualizacji i Zapisz skrypt. Jeśli nie określono flagę, wstępna elementy nie będą wyświetlane.
- Wersje skryptu wyświetlane przez Find-Script, Get-InstalledScript i w galerii programu PowerShell będą wyświetlane z PrereleaseString, tak jak 2.5.0-alpha.

Poniżej znajdują się szczegółowe informacje dla funkcji.

## <a name="identifying-a-script-version-as-a-prerelease"></a>Identyfikowanie wersji skryptu jako wersji wstępnej

Obsługa modułu PowerShellGet wersje wstępne jest łatwiejsze w przypadku skryptów niż moduły. Przechowywanie wersji skrypt jest obsługiwany tylko modułu PowerShellGet, więc nie ma żadnych problemów ze zgodnością spowodowane przez dodanie ciągu wersji wstępnej. Aby określić skrypt w galerii programu PowerShell, zgodnie z wersji wstępnej, należy dodać sufiks wersji wstępnej do wersji poprawnie sformatowany ciąg znaków w metadanych skryptów.

Przykład części manifestu skryptu za pomocą wersji wstępnej powinien wyglądać następująco:

```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>
```

Aby użyć sufiks wersji wstępnej, ciąg wersji musi spełniać następujące wymagania:

- Sufiks wersji wstępnej może być określona tylko, gdy wersja jest 3 segmenty dla główna.pomocnicza.kompilacja.
  Jest to zgodne z 1.0.0 SemVer
- Wstępna sufiks jest to ciąg, który rozpoczyna się łącznikiem i może zawierać znaki alfanumeryczne ASCII [0-9A-Za - z-]
- Tylko ciągi wstępna wersja 1.0.0 SemVer są obsługiwane w tej chwili więc sufiks wersji wstępnej __nie__ zawierać albo okres lub + [. +], mogą SemVer w wersji 2.0
- Przykłady obsługiwanych ciągów PrereleaseString:-alfa, - 1,-BETA, - update20171020

__Wpływ wersji wstępnej w folderach instalacji i kolejność sortowania__

Kolejność sortowania zmienia się podczas korzystania z wersji wstępnej, co jest ważne w przypadku publikowania w galerii programu PowerShell, a podczas instalowania skryptów przy użyciu poleceń modułu PowerShellGet. Jeśli dwa skrypty w wersji z numerem wersji istnieją, kolejność sortowania jest oparty na fragment ciągu, postępując łącznika. Dlatego 2.5.0-alpha wersji jest mniejszy niż 2.5.0-beta, która jest mniejsza niż 2.5.0-gamma. Jeśli dwa skrypty mają ten sam numer wersji, i tylko jeden PrereleaseString, skrypt __bez__ sufiks wersji wstępnej zakłada, że wersja gotowe do produkcji i będą sortowane jako nowszej wersji niż wersja wstępna Wersja. Na przykład podczas porównywania zwalnia 2.5.0 i 2.5.0-beta, 2.5.0 wersji będą uznawane za większa niż dwa.

Publikowanie w galerii programu PowerShell, domyślnie wersja skryptu publikacji musi mieć nieco większa niż wersja wszystkie wcześniej publikowane w galerii programu PowerShell. Wydawca może aktualizować 2.5.0-alpha wersji 2.5.0-beta lub z 2.5.0 (sufiksem nie wstępnej).

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a>Wyszukiwanie i pobieranie elementów wersji wstępnej, za pomocą poleceń modułu PowerShellGet

Korzystające z elementów wersji wstępnej, za pomocą skryptu-PowerShellGet Find-Script, skrypt instalacji aktualizacji, a polecenia Save-Script wymaga dodanie flagi - AllowPrerelease. Jeśli - AllowPrerelease jest określony, wstępnej elementy zostaną dołączone, jeśli są obecne. Flaga - AllowPrerelease nie zostanie określona, wstępna elementy nie będą wyświetlane.

Jedynym wyjątkiem od tej w poleceniach skryptu PowerShellGet są Get InstalledScript i czasami z skrypt dezinstalacji.

- Get-InstalledScript zawsze automatycznie wyświetli informacje wstępne w ciągu wersji Jeśli jest obecny.
- Odinstaluj skryptu domyślnie odinstaluje najnowszej wersji skryptu, jeśli __nie została zainstalowana wersja__ jest określony. To zachowanie nie zmienił się. Jednak jeśli jest to wersja wstępna produktu jest określony, przy użyciu - RequiredVersion, - AllowPrerelease jest wymagana.

## <a name="examples"></a>Przykłady

```powershell
# Assume the PowerShell Gallery has TestPackage versions 1.8.0 and 1.9.0-alpha.
# If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
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

Odinstaluj skrypt spowoduje usunięcie bieżącej wersji skryptu, gdy - RequiredVersion nie zostanie dostarczona.
Jeśli - RequiredVersion zostanie określona, jest w wersji wstępnej, - AllowPrerelease należy dodać do polecenia.

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

## <a name="more-details"></a>Więcej szczegółów

- [Wersje wstępne modułu](module-prerelease-support.md)
- [Znajdź script](/powershell/module/powershellget/find-script)
- [Skrypt instalacji](/powershell/module/powershellget/install-script)
- [Save-script](/powershell/module/powershellget/save-script)
- [Skrypt aktualizacji](/powershell/module/powershellget/update-script)
- [Get-Installedscript](/powershell/module/powershellget/get-installedscript)
- [Odinstaluj skryptu](/powershell/module/powershellget/uninstall-script)