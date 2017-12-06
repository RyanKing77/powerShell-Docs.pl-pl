---
ms.date: 2017-09-26
contributor: keithb
ms.topic: reference
keywords: Galeria, programu powershell, polecenia cmdlet, psget
title: PrereleaseModule
ms.openlocfilehash: d2c629d0e0ec0d4a4adafe5994a37d3985d13a06
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2017
---
# <a name="prerelease-module-versions"></a>Wersji wstępnej modułów
Począwszy od wersji 1.6.0 PowerShellGet i galerii programu PowerShell zapewniają obsługę znakowania w wersjach nowszych niż 1.0.0 jako wstępnej wersji. Przed tej funkcji wersji wstępnej elementy były ograniczone do o wersji, począwszy od 0. Celem tych funkcji jest zapewniają lepsze wsparcie [v1.0.0 programu SemVer](http://semver.org/spec/v1.0.0.html) Konwencji versioning bez przerywania zapewnienia zgodności z programu PowerShell 3 i powyżej lub istniejącej wersji programu PowerShellGet. Ten temat koncentruje się na funkcji specyficznych dla modułu. Są równoważne funkcje skryptów [wstępnej wersji skryptów](../script/PrereleaseScript.md) tematu. Korzystanie z tych funkcji, wydawców można zidentyfikować modułu lub skrypt jako 2.5.0-alpha wersji, a później Zwolnij wersji gotowe do produkcji 2.5.0 zastępuje wersji wstępnej. 

Na wysokim poziomie funkcje wersji wstępnej modułu obejmują:

* Dodawanie ciąg wersji wstępnej do sekcji PSData manifestu modułu identyfikuje modułu jako wersji wstępnej. Gdy moduł zostanie opublikowany w galerii programu PowerShell, te dane są wyodrębniane w manifeście i używany do identyfikowania wstępnej elementów.
* Uzyskiwanie elementów wstępnej wymaga Dodawanie flagi - AllowPrerelease do polecenia PowerShellGet Znajdź-Module Install-Module moduł aktualizacji i Zapisz modułu. Jeśli nie określono flagę, nie można wyświetlić elementy wersji wstępnej.  
* Wersje modułu wyświetlane przez moduł znajdowania, Get-InstalledModule i w galerii programu PowerShell będą wyświetlane jako pojedynczy ciąg z wersji wstępnej ciąg dołączany, tak jak 2.5.0-alpha. 

Poniżej znajdują się szczegółowe informacje dotyczące funkcji. 

Te zmiany nie wpływają na obsługę wersji modułu skompilowanego w programie PowerShell i są zgodne z programem PowerShell 3.0, 4.0 i 5. 

## <a name="identifying-a-module-version-as-a-prerelease"></a>Identyfikowanie wersji modułu jako wstępnej wersji 

Obsługa PowerShellGet wersje wstępne wymaga użycia dwóch pól w manifeście modułu:

* ModuleVersion zawarte w manifeście modułu musi być w wersji 3 części, jeśli wstępna wersja jest używana, a musi być zgodne z istniejącej wersji programu PowerShell. Format wersji będą A.B.C, gdzie A, B i C to wszystkie liczby całkowite. 
* Ciąg wersji wstępnej jest określona w manifeście modułu, w sekcji PSData PrivateData. Szczegółowe wymagania na ciąg wersji wstępnej są poniżej. 

Przykład części manifestu modułu, który definiuje moduł jako wstępnej wersji będzie wyglądać następująco:
```powershell
@{
    ModuleVersion = '2.5.0'
    #---
    PrivateData = @{
        PSData = @{
            Prerelease = 'alpha'
        }
    }
}
```

Szczegółowe wymagania dotyczące ciąg wersji wstępnej są: 

* Ciąg wersji wstępnej może być określona tylko, gdy ModuleVersion jest 3 segmentów dla Major.Minor.Build. Jest to zgodne z programu SemVer v1.0.0.
* Łącznik jest separator numer kompilacji i ciąg wersji wstępnej. Łącznik mogą zostać zawarte w wersji wstępnej ciągu jako pierwszy znak, tylko.
* Ciąg wersji wstępnej może zawierać tylko alfanumeryczne ASCII [0-9A-Za - z —]. Jest najlepszym rozwiązaniem jest rozpocząć wstępną ciąg znaków alfanumerycznych, ponieważ będzie on łatwiej zidentyfikować, że to jest wersja wstępna podczas skanowania listy elementów. 
* Tylko programu SemVer v1.0.0 wstępnej ciągi są obsługiwane w tej chwili. Ciąg wersji wstępnej __nie mogą__ zawierać albo okres lub + [. +], które są dozwolone w programu SemVer 2.0. 
* Przykłady obsługiwanych wersji wstępnej ciągu:-alfa, - 1,-BETA, - update20171020

__Wpływ wersji wstępnej w folderach instalacji i kolejność sortowania__

Kolejność sortowania zmian za pomocą wersji wstępnej, co jest ważne podczas publikowania w galerii programu PowerShell, a podczas instalowania modułów za pomocą polecenia PowerShellGet. Jeśli określono ciąg wersji wstępnej dwa moduły, kolejność sortowania jest oparta na fragment ciągu, po łącznik. Tak 2.5.0-alpha wersji jest mniejsza niż 2.5.0-beta, czyli mniej niż 2.5.0-gamma. Jeśli dwa moduły mają tego samego ModuleVersion i tylko jeden z nich zawiera ciąg wersji wstępnej, modułu bez wstępnej ciąg zakłada, że wersja gotowe do produkcji i będą sortowane jako wersja większe niż (w tym wstępną wersję wstępną ciąg). Na przykład podczas porównywania zwalnia 2.5.0 i 2.5.0-beta, 2.5.0 wersji będą uznawane za większa niż dwa. 

Podczas publikowania w galerii programu PowerShell, domyślnie wersję modułu publikowaną muszą mieć wyższej wersji niż wersja wszystkie wcześniej publikowane w galerii programu PowerShell. 

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a>Wyszukiwanie i pobieranie elementów wstępnej za pomocą polecenia PowerShellGet

Zajmujących się wstępnej elementów za pomocą aktualizacji znajdź PowerShellGet-Module, Install-Module-modułu, i Zapisz modułu polecenia wymaga Dodawanie flagi - AllowPrerelease. Jeśli określono - AllowPrerelease, elementy wstępnej można włączyć, jeśli są obecne.
Jeśli nie określono flagę - AllowPrerelease, nie można wyświetlić elementy wersji wstępnej. 

Tylko wyjątki od tej reguły w poleceniach modułu PowerShellGet są Get InstalledModule i czasami modułem Odinstaluj. 

* Get-InstalledModule zawsze automatycznie wyświetli informacje o wersji wstępnej w ciągu wersji dla modułów. 
* Odinstaluj moduł domyślnie odinstaluje najnowszej wersji modułu, jeśli __nie została zainstalowana wersja__ jest określona. To zachowanie nie została zmieniona. Jednak jeśli wstępna wersja jest określona za pomocą - RequiredVersion, - AllowPrerelease będzie wymagane. 

## <a name="examples"></a>Przykłady
```powershell
# Assume the PowerShell Gallery has TestPackage module versions 1.8.0 and 1.9.0-alpha. If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> find-module TestPackage 

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

# To install a prerelease, always specify -AllowPrerelease. Specifying a prerelease version string is not sufficient. 

C:\windows\system32> Install-module TestPackage -RequiredVersion 1.9.0-alpha
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exceptio
   n
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

```

Instalacja Side-by-side wersji modułu, które różnią się tylko ze względu na określony wstępną nie jest obsługiwana. Podczas instalowania modułu przy użyciu PowerShellGet, różne wersje tego samego modułu są zainstalowane obok siebie, tworząc nazwę folderu przy użyciu ModuleVersion. ModuleVersion, bez wstępnej ciąg jest używany dla nazwy folderu. Jeśli użytkownik zainstaluje MyModule 2.5.0-alpha wersji, zostanie zainstalowana w folderze MyModule\2.5.0. Jeśli użytkownik zainstaluje następnie 2.5.0-beta, wersja 2.5.0-beta będzie __uwierzytelniając zapisu__ zawartość folderu MyModule\2.5.0. Jedną z zalet tego podejścia jest, że nie istnieje potrzeba aby odinstalować wstępną wersję po zainstalowaniu wersji gotowe do produkcji. W poniższym przykładzie pokazano, czego można oczekiwać:


``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-beta     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-beta      TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

```

Odinstalowanie modułu spowoduje usunięcie najnowszej wersji modułu, gdy - RequiredVersion nie jest dostarczony. Jeśli określono - RequiredVersion i jest wersja wstępna, - AllowPrerelease należy dodać do polecenia. 

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
2.0.0-alpha1    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta
Uninstall-Module : The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Unnstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninnstall-Module



C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
2.0.0-alpha1    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...


```



## <a name="more-details"></a>więcej informacji
### <a name="prerelease-script-versionsscriptprereleasescriptmd"></a>[Wersji wstępnej skryptu](../script/PrereleaseScript.md)
### <a name="find-modulepsgetfind-modulemd"></a>[Znajdź moduł](./psget_find-module.md)
### <a name="install-modulepsgetinstall-modulemd"></a>[Zainstaluj moduł](./psget_install-module.md)
### <a name="save-modulepsgetsave-modulemd"></a>[Moduł zapisywania](./psget_save-module.md)
### <a name="update-modulepsgetupdate-modulemd"></a>[Moduł aktualizacji](./psget_update-module.md)
### <a name="get-installedmodulepsgetget-installedmodulemd"></a>[Get-InstalledModule](./psget_get-installedmodule.md)
### <a name="uninstall-modulepsgetuninstall-modulemd"></a>[Odinstaluj moduł](./psget_uninstall-module.md)
