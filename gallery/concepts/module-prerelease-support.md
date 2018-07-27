---
ms.date: 09/26/2017
contributor: keithb
keywords: Galeria, programu powershell, polecenie cmdlet, psget
title: Wersje wstępne modułu
ms.openlocfilehash: 9c3ddb623fbcb7f4b3453dd70cdc56a8dc2e9f6a
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268623"
---
# <a name="prerelease-module-versions"></a><span data-ttu-id="e3fe6-103">Wersje wstępne modułu</span><span class="sxs-lookup"><span data-stu-id="e3fe6-103">Prerelease Module Versions</span></span>

<span data-ttu-id="e3fe6-104">Począwszy od wersji 1.6.0 modułu PowerShellGet oraz spełnione galerii programu PowerShell zapewniają obsługę tagowania w wersjach nowszych niż 1.0.0 jako wersji wstępnej.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="e3fe6-105">Przed tej funkcji wersji wstępnej elementy były korzystać z wersji począwszy od 0.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-105">Prior to this feature, prerelease items were limited to having a version beginning with 0.</span></span> <span data-ttu-id="e3fe6-106">Celem tych funkcji jest zapewniają lepsze wsparcie [1.0.0 SemVer](http://semver.org/spec/v1.0.0.html) Konwencji wersji bez przerywania wstecznej zgodności przy użyciu programu PowerShell 3 i powyżej lub istniejącej wersji programu PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="e3fe6-107">Ten temat koncentruje się na funkcji specyficznych dla modułu.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-107">This topic focuses on the module-specific features.</span></span> <span data-ttu-id="e3fe6-108">Równoważne funkcje dla skryptów znajdują się w [wersję wstępną wersji skryptów](script-prerelease-support.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-108">The equivalent features for scripts are in the [Prerelease Versions of Scripts](script-prerelease-support.md) topic.</span></span> <span data-ttu-id="e3fe6-109">Korzystania z tych funkcji, wydawców można zidentyfikować modułu lub skryptu jako 2.5.0-alpha wersji i później wydanej wersji gotowe do produkcji 2.5.0, która zastępuje wersję wstępną.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-109">Using these features, publishers can identify a module or script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="e3fe6-110">Na wysokim poziomie funkcje wersji wstępnej modułu obejmują:</span><span class="sxs-lookup"><span data-stu-id="e3fe6-110">At a high level, the prerelease module features include:</span></span>

- <span data-ttu-id="e3fe6-111">Dodawanie ciąg wersji wstępnej do sekcji PSData manifestu modułu identyfikuje moduł jako wersji wstępnej.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-111">Adding a Prerelease string to the PSData section of the module manifest identifies the module as a prerelease version.</span></span> <span data-ttu-id="e3fe6-112">Gdy moduł zostanie opublikowany w galerii programu PowerShell, te dane są wyodrębniane z manifestu i używany do identyfikowania elementów wersji wstępnej.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-112">When the module is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease items.</span></span>
- <span data-ttu-id="e3fe6-113">Pobieranie elementów wstępnych wymaga dodania `-AllowPrerelease` Flaga poleceń modułu PowerShellGet `Find-Module`, `Install-Module`, `Update-Module`, i `Save-Module`.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-113">Acquiring prerelease items requires adding `-AllowPrerelease` flag to the PowerShellGet commands `Find-Module`, `Install-Module`, `Update-Module`, and `Save-Module`.</span></span> <span data-ttu-id="e3fe6-114">Jeśli nie określono flagę, wstępna elementy nie będą wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-114">If the flag is not specified, prerelease items will not be shown.</span></span>
- <span data-ttu-id="e3fe6-115">Wersje modułu wyświetlane przez `Find-Module`, `Get-InstalledModule`, a w galerii programu PowerShell będą wyświetlane jako pojedynczy ciąg parametrami wstępnej dołączane, tak jak 2.5.0-alpha.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-115">Module versions displayed by `Find-Module`, `Get-InstalledModule`, and in the PowerShell Gallery will be displayed as a single string with the Prerelease string appended, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="e3fe6-116">Poniżej znajdują się szczegółowe informacje dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-116">Details for the features are included below.</span></span>

<span data-ttu-id="e3fe6-117">Te zmiany nie wpływają na obsługę wersji modułu, która jest wbudowana w programie PowerShell i są zgodne z programem PowerShell 3.0 i 4.0, 5.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-117">These changes do not affect the module version support that is built into PowerShell, and are compatible with PowerShell 3.0, 4.0, and 5.</span></span>

## <a name="identifying-a-module-version-as-a-prerelease"></a><span data-ttu-id="e3fe6-118">Identyfikuje wersję modułu jako wersji wstępnej</span><span class="sxs-lookup"><span data-stu-id="e3fe6-118">Identifying a module version as a prerelease</span></span>

<span data-ttu-id="e3fe6-119">Moduł PowerShellGet obsługę wersji wstępnej wymaga użycia dwóch pól w manifeście modułu:</span><span class="sxs-lookup"><span data-stu-id="e3fe6-119">PowerShellGet support for prerelease versions requires the use of two fields within the Module Manifest:</span></span>

- <span data-ttu-id="e3fe6-120">ModuleVersion zawarte w manifeście modułu musi być w wersji 3 części, jeśli to wersja wstępna produktu jest używana i musi być zgodne z istniejącej wersji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-120">The ModuleVersion included in the module manifest must be a 3-part version if a prerelease version is used, and must comply with existing PowerShell versioning.</span></span> <span data-ttu-id="e3fe6-121">Format wersji byłoby A.B.C, gdzie A, B i C, to wszystkie liczby całkowite.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-121">The version format would be A.B.C, where A, B, and C are all integers.</span></span>
- <span data-ttu-id="e3fe6-122">Wstępna ciągu jest określona w manifeście modułu, w sekcji PSData PrivateData.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-122">The Prerelease string is specified in the module manifest, in the PSData section of PrivateData.</span></span>

<span data-ttu-id="e3fe6-123">Szczegółowe wymagania wstępne ciągu są wyświetlane poniżej.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-123">Detailed requirements on the Prerelease string are below.</span></span>

<span data-ttu-id="e3fe6-124">Przykład części manifestu modułu, który definiuje moduł jako wersji wstępnej powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="e3fe6-124">An example section of a module manifest that defines a module as a prerelease would look like the following:</span></span>

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

<span data-ttu-id="e3fe6-125">Szczegółowe wymagania wstępne ciągu są następujące:</span><span class="sxs-lookup"><span data-stu-id="e3fe6-125">The detailed requirements for Prerelease string are:</span></span>

- <span data-ttu-id="e3fe6-126">Ciąg wersji wstępnej może być określona tylko po ModuleVersion 3 segmenty dla główna.pomocnicza.kompilacja.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-126">Prerelease string may only be specified when the ModuleVersion is 3 segments for Major.Minor.Build.</span></span> <span data-ttu-id="e3fe6-127">Jest to zgodne z SemVer 1.0.0.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-127">This aligns with SemVer v1.0.0.</span></span>
- <span data-ttu-id="e3fe6-128">Łącznik jest separator numer kompilacji i wersji wstępnej ciągu.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-128">A hyphen is the delimiter between the Build number and the Prerelease string.</span></span> <span data-ttu-id="e3fe6-129">Łącznik mogą zostać zawarte w wersji wstępnej ciągu jako pierwszego znaku, tylko.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-129">A hyphen may be included in the Prerelease string as the first character, only.</span></span>
- <span data-ttu-id="e3fe6-130">Wstępna ciągu może zawierać tylko znaki alfanumeryczne ASCII [0-9A-Za - z-].</span><span class="sxs-lookup"><span data-stu-id="e3fe6-130">The Prerelease string may contain only ASCII alphanumerics [0-9A-Za-z-].</span></span> <span data-ttu-id="e3fe6-131">Jest najlepszym rozwiązaniem, aby rozpocząć wstępną ciągu za pomocą znaków alfanumerycznych, ponieważ będzie on łatwiej można zidentyfikować, że jest to wersja wstępna produktu podczas skanowania listy elementów.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-131">It is a best practice to begin the Prerelease string with an alpha character, as it will be easier to identify that this is a prerelease version when scanning a list of items.</span></span>
- <span data-ttu-id="e3fe6-132">Tylko SemVer 1.0.0 wstępnej ciągi są obsługiwane w tej chwili.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-132">Only SemVer v1.0.0 prerelease strings are supported at this time.</span></span> <span data-ttu-id="e3fe6-133">Ciąg wersji wstępnej **nie** zawierać albo okres lub + [. +], mogą SemVer w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-133">Prerelease string **must not** contain either period or + [.+], which are allowed in SemVer 2.0.</span></span>
- <span data-ttu-id="e3fe6-134">Przykłady obsługiwany ciąg wersji wstępnej:-alfa, - 1,-BETA, - update20171020</span><span class="sxs-lookup"><span data-stu-id="e3fe6-134">Examples of supported Prerelease string are: -alpha, -alpha1, -BETA, -update20171020</span></span>

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a><span data-ttu-id="e3fe6-135">Wpływ wersji wstępnej w folderach instalacji i kolejność sortowania</span><span class="sxs-lookup"><span data-stu-id="e3fe6-135">Prerelease versioning impact on sort order and installation folders</span></span>

<span data-ttu-id="e3fe6-136">Kolejność sortowania zmienia się podczas korzystania z wersji wstępnej, co jest ważne w przypadku publikowania w galerii programu PowerShell, a podczas instalowania modułów przy użyciu poleceń modułu PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-136">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing modules using PowerShellGet commands.</span></span> <span data-ttu-id="e3fe6-137">Jeśli ciąg wersji wstępnej jest określona dla dwóch modułów, kolejność sortowania jest oparty na fragment ciągu, postępując łącznika.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-137">If the Prerelease string is specified for two modules, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="e3fe6-138">Dlatego 2.5.0-alpha wersji jest mniejszy niż 2.5.0-beta, która jest mniejsza niż 2.5.0-gamma.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-138">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="e3fe6-139">Jeśli dwa moduły mają ten sam ModuleVersion i tylko jeden ma ciąg wersji wstępnej, modułu bez wstępnej ciągu zakłada, że wersja gotowe do produkcji i będą sortowane jako nowszej wersji niż wersja wstępna, (co obejmuje wersja wstępna ciąg).</span><span class="sxs-lookup"><span data-stu-id="e3fe6-139">If two modules have the same ModuleVersion, and only one has a Prerelease string, the module without the Prerelease string is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version (which includes the Prerelease string).</span></span> <span data-ttu-id="e3fe6-140">Na przykład podczas porównywania zwalnia 2.5.0 i 2.5.0-beta, 2.5.0 wersji będą uznawane za większa niż dwa.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-140">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="e3fe6-141">Publikowanie w galerii programu PowerShell, domyślnie wersję modułu publikacji musi mieć nieco większa niż wersja wszystkie wcześniej publikowane w galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-141">When publishing to the PowerShell Gallery, by default the version of the module being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span>

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a><span data-ttu-id="e3fe6-142">Wyszukiwanie i pobieranie elementów wersji wstępnej, za pomocą poleceń modułu PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="e3fe6-142">Finding and acquiring prerelease items using PowerShellGet commands</span></span>

<span data-ttu-id="e3fe6-143">Korzystające z elementów wersji wstępnej, za pomocą aktualizacji modułu PowerShellGet Find-Module Install-Module-Module, i polecenia Save-Module wymaga dodanie flagi - AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-143">Dealing with prerelease items using PowerShellGet Find-Module, Install-Module, Update-Module, and Save-Module commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="e3fe6-144">Jeśli - AllowPrerelease jest określony, wstępnej elementy zostaną dołączone, jeśli są obecne.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-144">If -AllowPrerelease is specified, prerelease items will be included if they are present.</span></span> <span data-ttu-id="e3fe6-145">Flaga - AllowPrerelease nie zostanie określona, wstępna elementy nie będą wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-145">If -AllowPrerelease flag is not specified, prerelease items will not be shown.</span></span>

<span data-ttu-id="e3fe6-146">Jedynym wyjątkiem od tej poleceń modułu PowerShellGet są Get InstalledModule i czasami z modułem dezinstalacji.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-146">The only exceptions to this in the PowerShellGet module commands are Get-InstalledModule, and some cases with Uninstall-Module.</span></span>

- <span data-ttu-id="e3fe6-147">Get-InstalledModule zawsze automatycznie wyświetli informacje wstępne w ciągu wersji dla modułów.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-147">Get-InstalledModule always will automatically show the prerelease information in the version string for modules.</span></span>
- <span data-ttu-id="e3fe6-148">Odinstalowanie modułu domyślnie odinstaluje najbardziej aktualną wersję modułu, jeśli __nie została zainstalowana wersja__ jest określony.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-148">Uninstall-Module will by default uninstall the most recent version of a module, if __no version__ is specified.</span></span> <span data-ttu-id="e3fe6-149">To zachowanie nie zmienił się.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-149">That behavior has not changed.</span></span> <span data-ttu-id="e3fe6-150">Jednak jeśli jest to wersja wstępna produktu jest określony, przy użyciu - RequiredVersion, - AllowPrerelease jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-150">However, if a prerelease version is specified using -RequiredVersion, -AllowPrerelease will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="e3fe6-151">Przykłady</span><span class="sxs-lookup"><span data-stu-id="e3fe6-151">Examples</span></span>

<span data-ttu-id="e3fe6-152">Załóżmy, że galerii programu PowerShell ma wersje modułu TestPackage 1.8.0 i 1.9.0-alpha.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-152">Assume the PowerShell Gallery has TestPackage module versions 1.8.0 and 1.9.0-alpha.</span></span> <span data-ttu-id="e3fe6-153">Jeśli `-AllowPrerelease` jest nie określono wersji 1.8.0 zostaną zwrócone.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-153">If `-AllowPrerelease` is not specified, only version 1.8.0 will be returned.</span></span>

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

<span data-ttu-id="e3fe6-154">Aby zainstalować wersji wstępnej, należy zawsze określić - AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-154">To install a prerelease, always specify -AllowPrerelease.</span></span> <span data-ttu-id="e3fe6-155">Określanie wersji wstępnej ciąg nie jest wystarczające.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-155">Specifying a prerelease version string is not sufficient.</span></span>

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

<span data-ttu-id="e3fe6-156">Poprzednie polecenie nie powiodło się, ponieważ nie określono - AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-156">The previous command failed because -AllowPrerelease was not specified.</span></span> <span data-ttu-id="e3fe6-157">Dodawanie `-AllowPrerelease` spowoduje Powodzenie.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-157">Adding `-AllowPrerelease` will result in success.</span></span>

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
Get-InstalledModule TestPackage
```

```output
Version         Name          Repository  Description
-------         ----          ----------  -----------
1.9.0-alpha     TestPackage   PSGallery   Package used to validate changes to the PowerShe...
```

<span data-ttu-id="e3fe6-158">Instalacja obok siebie wersji modułu, które różnią się tylko ze względu na wersję wstępną określony nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-158">Side-by-side installation of versions of a module that differ only due to the prerelease specified is not supported.</span></span> <span data-ttu-id="e3fe6-159">Podczas instalowania modułu przy użyciu funkcji PowerShellGet, różne wersje tego samego modułu są zainstalowane side-by-side, tworząc nazwę folderu, za pomocą ModuleVersion.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-159">When installing a module using PowerShellGet, different versions of the same module are installed side-by-side by creating a folder name using the ModuleVersion.</span></span> <span data-ttu-id="e3fe6-160">ModuleVersion, bez wstępnej ciąg jest używany dla nazwy folderu.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-160">The ModuleVersion, without the prerelease string, is used for the folder name.</span></span> <span data-ttu-id="e3fe6-161">Jeśli użytkownik zainstaluje 2.5.0-alpha wersji MyModule, zostanie zainstalowana do `MyModule\2.5.0` folderu.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-161">If a user installs MyModule version 2.5.0-alpha, it will be installed to the `MyModule\2.5.0` folder.</span></span> <span data-ttu-id="e3fe6-162">Jeśli użytkownik instaluje następnie 2.5.0-beta, wersja 2.5.0-beta będzie **zastąpić** zawartość folderu `MyModule\2.5.0`.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-162">If the user then installs 2.5.0-beta, the 2.5.0-beta version will **overwrite** the contents of the folder `MyModule\2.5.0`.</span></span> <span data-ttu-id="e3fe6-163">Jedną z zalet tego podejścia jest nie musisz odinstalować wstępną wersję po zainstalowaniu wersji gotowe do produkcji.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-163">One advantage to this approach is that there is no need to un-install the prerelease version after installing the production-ready version.</span></span> <span data-ttu-id="e3fe6-164">W poniższym przykładzie pokazano, czego można oczekiwać:</span><span class="sxs-lookup"><span data-stu-id="e3fe6-164">The example below shows what to expect:</span></span>

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

<span data-ttu-id="e3fe6-165">Odinstalowanie modułu spowoduje usunięcie najnowszą wersję modułu, jeśli nie podano - RequiredVersion.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-165">Uninstall-Module will remove the latest version of a module when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="e3fe6-166">Jeśli - RequiredVersion zostanie określona, jest w wersji wstępnej, - AllowPrerelease należy dodać do polecenia.</span><span class="sxs-lookup"><span data-stu-id="e3fe6-166">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

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
+ Unnstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninnstall-Module

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

## <a name="more-details"></a><span data-ttu-id="e3fe6-167">Więcej szczegółów</span><span class="sxs-lookup"><span data-stu-id="e3fe6-167">More details</span></span>

- [<span data-ttu-id="e3fe6-168">Wersje wstępne skryptu</span><span class="sxs-lookup"><span data-stu-id="e3fe6-168">Prerelease Script Versions</span></span>](script-prerelease-support.md)
- [<span data-ttu-id="e3fe6-169">Find-Module</span><span class="sxs-lookup"><span data-stu-id="e3fe6-169">Find-Module</span></span>](/powershell/module/powershellget/find-module)
- [<span data-ttu-id="e3fe6-170">Install-Module</span><span class="sxs-lookup"><span data-stu-id="e3fe6-170">Install-Module</span></span>](/powershell/module/powershellget/install-module)
- [<span data-ttu-id="e3fe6-171">Save-Module</span><span class="sxs-lookup"><span data-stu-id="e3fe6-171">Save-Module</span></span>](/powershell/module/powershellget/save-module)
- [<span data-ttu-id="e3fe6-172">Update-Module</span><span class="sxs-lookup"><span data-stu-id="e3fe6-172">Update-Module</span></span>](/powershell/module/powershellget/Update-Module)
- [<span data-ttu-id="e3fe6-173">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="e3fe6-173">Get-InstalledModule</span></span>](/powershell/module/powershellget/get-installedmodule)
- [<span data-ttu-id="e3fe6-174">Odinstalowanie modułu</span><span class="sxs-lookup"><span data-stu-id="e3fe6-174">UnInstall-Module</span></span>](/powershell/module/powershellget/uninstall-module)