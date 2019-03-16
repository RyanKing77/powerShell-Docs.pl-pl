---
ms.date: 09/26/2017
contributor: keithb
keywords: Galeria, programu powershell, polecenie cmdlet, psget
title: Wersje wstępne modułu
ms.openlocfilehash: eced067dd21082de0db653daf3b838217154f1dd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056249"
---
# <a name="prerelease-module-versions"></a>Wersje wstępne modułu

Począwszy od wersji 1.6.0 modułu PowerShellGet oraz spełnione galerii programu PowerShell zapewniają obsługę tagowania w wersjach nowszych niż 1.0.0 jako wersji wstępnej. Przed tą funkcją pakiety w wersjach wstępnych były korzystać z wersji począwszy od 0. Celem tych funkcji jest zapewniają lepsze wsparcie [1.0.0 SemVer](http://semver.org/spec/v1.0.0.html) Konwencji wersji bez przerywania wstecznej zgodności przy użyciu programu PowerShell 3 i powyżej lub istniejącej wersji programu PowerShellGet. Ten temat koncentruje się na funkcji specyficznych dla modułu. Równoważne funkcje dla skryptów znajdują się w [wersję wstępną wersji skryptów](script-prerelease-support.md) tematu. Korzystania z tych funkcji, wydawców można zidentyfikować modułu lub skryptu jako 2.5.0-alpha wersji i później wydanej wersji gotowe do produkcji 2.5.0, która zastępuje wersję wstępną.

Na wysokim poziomie funkcje wersji wstępnej modułu obejmują:

- Dodawanie ciąg wersji wstępnej do sekcji PSData manifestu modułu identyfikuje moduł jako wersji wstępnej. Gdy moduł zostanie opublikowany w galerii programu PowerShell, te dane są wyodrębniane z manifestu i używany do identyfikowania pakiety w wersjach wstępnych.
- Pobieranie pakietów wydań wstępnych wymaga dodania `-AllowPrerelease` Flaga poleceń modułu PowerShellGet `Find-Module`, `Install-Module`, `Update-Module`, i `Save-Module`. Jeśli nie określono flagę, pakiety w wersjach wstępnych nie będą wyświetlane.
- Wersje modułu wyświetlane przez `Find-Module`, `Get-InstalledModule`, a w galerii programu PowerShell będą wyświetlane jako pojedynczy ciąg parametrami wstępnej dołączane, tak jak 2.5.0-alpha.

Poniżej znajdują się szczegółowe informacje dla funkcji.

Te zmiany nie wpływają na obsługę wersji modułu, która jest wbudowana w programie PowerShell i są zgodne z programem PowerShell 3.0 i 4.0, 5.

## <a name="identifying-a-module-version-as-a-prerelease"></a>Identyfikuje wersję modułu jako wersji wstępnej

Moduł PowerShellGet obsługę wersji wstępnej wymaga użycia dwóch pól w manifeście modułu:

- ModuleVersion zawarte w manifeście modułu musi być w wersji 3 części, jeśli to wersja wstępna produktu jest używana i musi być zgodne z istniejącej wersji programu PowerShell. Format wersji byłoby A.B.C, gdzie A, B i C, to wszystkie liczby całkowite.
- Wstępna ciągu jest określona w manifeście modułu, w sekcji PSData PrivateData.

Szczegółowe wymagania wstępne ciągu są wyświetlane poniżej.

Przykład części manifestu modułu, który definiuje moduł jako wersji wstępnej powinien wyglądać następująco:

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

Szczegółowe wymagania wstępne ciągu są następujące:

- Ciąg wersji wstępnej może być określona tylko po ModuleVersion 3 segmenty dla główna.pomocnicza.kompilacja. Jest to zgodne z SemVer 1.0.0.
- Łącznik jest separator numer kompilacji i wersji wstępnej ciągu. Łącznik mogą zostać zawarte w wersji wstępnej ciągu jako pierwszego znaku, tylko.
- Wstępna ciągu może zawierać tylko znaki alfanumeryczne ASCII [0-9A-Za - z-]. Jest najlepszym rozwiązaniem, aby rozpocząć wstępną ciągu za pomocą znaków alfanumerycznych, ponieważ będzie on łatwiej można zidentyfikować, że jest to wersja wstępna produktu podczas skanowania do listy pakietów.
- Tylko SemVer 1.0.0 wstępnej ciągi są obsługiwane w tej chwili. Ciąg wersji wstępnej **nie** zawierać albo okres lub + [. +], mogą SemVer w wersji 2.0.
- Przykłady obsługiwany ciąg wersji wstępnej:-alfa, - 1,-BETA, - update20171020

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a>Wpływ wersji wstępnej w folderach instalacji i kolejność sortowania

Kolejność sortowania zmienia się podczas korzystania z wersji wstępnej, co jest ważne w przypadku publikowania w galerii programu PowerShell, a podczas instalowania modułów przy użyciu poleceń modułu PowerShellGet. Jeśli ciąg wersji wstępnej jest określona dla dwóch modułów, kolejność sortowania jest oparty na fragment ciągu, postępując łącznika. Dlatego 2.5.0-alpha wersji jest mniejszy niż 2.5.0-beta, która jest mniejsza niż 2.5.0-gamma. Jeśli dwa moduły mają ten sam ModuleVersion i tylko jeden ma ciąg wersji wstępnej, modułu bez wstępnej ciągu zakłada, że wersja gotowe do produkcji i będą sortowane jako nowszej wersji niż wersja wstępna, (co obejmuje wersja wstępna ciąg). Na przykład podczas porównywania zwalnia 2.5.0 i 2.5.0-beta, 2.5.0 wersji będą uznawane za większa niż dwa.

Publikowanie w galerii programu PowerShell, domyślnie wersję modułu publikacji musi mieć nieco większa niż wersja wszystkie wcześniej publikowane w galerii programu PowerShell.

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a>Znajdowanie i Uzyskiwanie pakietów wydań wstępnych przy użyciu poleceń modułu PowerShellGet

Obsługa pakietów wydań wstępnych, za pomocą aktualizacji modułu PowerShellGet Find-Module Install-Module-Module, i polecenia Save-Module wymaga dodanie flagi - AllowPrerelease. Jeśli określono - AllowPrerelease, pakiety w wersjach wstępnych zostaną dołączone, jeśli są obecne. Jeśli nie określono flagę - AllowPrerelease, pakiety w wersjach wstępnych nie będą wyświetlane.

Jedynym wyjątkiem od tej poleceń modułu PowerShellGet są Get InstalledModule i czasami z modułem dezinstalacji.

- Get-InstalledModule zawsze automatycznie wyświetli informacje wstępne w ciągu wersji dla modułów.
- Odinstalowanie modułu domyślnie odinstaluje najbardziej aktualną wersję modułu, jeśli __nie została zainstalowana wersja__ jest określony. To zachowanie nie zmienił się. Jednak jeśli jest to wersja wstępna produktu jest określony, przy użyciu - RequiredVersion, - AllowPrerelease jest wymagana.

## <a name="examples"></a>Przykłady

Załóżmy, że galerii programu PowerShell ma wersje modułu TestPackage 1.8.0 i 1.9.0-alpha. Jeśli `-AllowPrerelease` jest nie określono wersji 1.8.0 zostaną zwrócone.

```powershell
find-module TestPackage
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.8.0          TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

```powershell
find-module TestPackage -AllowPrerelease
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.9.0-alpha    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

Aby zainstalować wersji wstępnej, należy zawsze określić - AllowPrerelease. Określanie wersji wstępnej ciąg nie jest wystarczające.

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha
```

```output
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exception
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage
```

Poprzednie polecenie nie powiodło się, ponieważ nie określono - AllowPrerelease. Dodawanie `-AllowPrerelease` spowoduje Powodzenie.

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
Get-InstalledModule TestPackage
```

```output
Version         Name          Repository  Description
-------         ----          ----------  -----------
1.9.0-alpha     TestPackage   PSGallery   Package used to validate changes to the PowerShe...
```

Instalacja obok siebie wersji modułu, które różnią się tylko ze względu na wersję wstępną określony nie jest obsługiwana. Podczas instalowania modułu przy użyciu funkcji PowerShellGet, różne wersje tego samego modułu są zainstalowane side-by-side, tworząc nazwę folderu, za pomocą ModuleVersion. ModuleVersion, bez wstępnej ciąg jest używany dla nazwy folderu. Jeśli użytkownik zainstaluje 2.5.0-alpha wersji MyModule, zostanie zainstalowana do `MyModule\2.5.0` folderu. Jeśli użytkownik instaluje następnie 2.5.0-beta, wersja 2.5.0-beta będzie **zastąpić** zawartość folderu `MyModule\2.5.0`. Jedną z zalet tego podejścia jest nie musisz odinstalować wstępną wersję po zainstalowaniu wersji gotowe do produkcji. W poniższym przykładzie pokazano, czego można oczekiwać:

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-alpha     TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name            Repository  Description
-------        ----            ----------  -----------
1.9.0-beta     TestPackage     PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

```

Odinstalowanie modułu spowoduje usunięcie najnowszą wersję modułu, jeśli nie podano - RequiredVersion.
Jeśli - RequiredVersion zostanie określona, jest w wersji wstępnej, - AllowPrerelease należy dodać do polecenia.

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
2.0.0-alpha1    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta

Uninstall-Module : The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninstall-Module

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
2.0.0-alpha1    TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...
```

## <a name="more-details"></a>Więcej szczegółów

- [Wersje wstępne skryptu](script-prerelease-support.md)
- [Find-Module](/powershell/module/powershellget/find-module)
- [Install-Module](/powershell/module/powershellget/install-module)
- [Save-Module](/powershell/module/powershellget/save-module)
- [Update-Module](/powershell/module/powershellget/Update-Module)
- [Get-InstalledModule](/powershell/module/powershellget/get-installedmodule)
- [UnInstall-Module](/powershell/module/powershellget/uninstall-module)
