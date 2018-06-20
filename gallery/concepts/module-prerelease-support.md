---
ms.date: 09/26/2017
contributor: keithb
keywords: Galeria, programu powershell, polecenia cmdlet, psget
title: Wersji wstępnej modułów
ms.openlocfilehash: 2a4fcd40353450e5ba03910984c5a05772a93d0d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189843"
---
# <a name="prerelease-module-versions"></a><span data-ttu-id="65a15-103">Wersji wstępnej modułów</span><span class="sxs-lookup"><span data-stu-id="65a15-103">Prerelease Module Versions</span></span>

<span data-ttu-id="65a15-104">Począwszy od wersji 1.6.0 PowerShellGet i galerii programu PowerShell zapewniają obsługę znakowania w wersjach nowszych niż 1.0.0 jako wstępnej wersji.</span><span class="sxs-lookup"><span data-stu-id="65a15-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="65a15-105">Przed tej funkcji wersji wstępnej elementy były ograniczone do o wersji, począwszy od 0.</span><span class="sxs-lookup"><span data-stu-id="65a15-105">Prior to this feature, prerelease items were limited to having a version beginning with 0.</span></span> <span data-ttu-id="65a15-106">Celem tych funkcji jest zapewniają lepsze wsparcie [v1.0.0 programu SemVer](http://semver.org/spec/v1.0.0.html) Konwencji versioning bez przerywania zapewnienia zgodności z programu PowerShell 3 i powyżej lub istniejącej wersji programu PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="65a15-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="65a15-107">Ten temat koncentruje się na funkcji specyficznych dla modułu.</span><span class="sxs-lookup"><span data-stu-id="65a15-107">This topic focuses on the module-specific features.</span></span> <span data-ttu-id="65a15-108">Są równoważne funkcje skryptów [wstępnej wersji skryptów](script-prerelease-support.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="65a15-108">The equivalent features for scripts are in the [Prerelease Versions of Scripts](script-prerelease-support.md) topic.</span></span> <span data-ttu-id="65a15-109">Korzystanie z tych funkcji, wydawców można zidentyfikować modułu lub skrypt jako 2.5.0-alpha wersji, a później Zwolnij wersji gotowe do produkcji 2.5.0 zastępuje wersji wstępnej.</span><span class="sxs-lookup"><span data-stu-id="65a15-109">Using these features, publishers can identify a module or script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="65a15-110">Na wysokim poziomie funkcje wersji wstępnej modułu obejmują:</span><span class="sxs-lookup"><span data-stu-id="65a15-110">At a high level, the prerelease module features include:</span></span>

- <span data-ttu-id="65a15-111">Dodawanie ciąg wersji wstępnej do sekcji PSData manifestu modułu identyfikuje modułu jako wersji wstępnej.</span><span class="sxs-lookup"><span data-stu-id="65a15-111">Adding a Prerelease string to the PSData section of the module manifest identifies the module as a prerelease version.</span></span> <span data-ttu-id="65a15-112">Gdy moduł zostanie opublikowany w galerii programu PowerShell, te dane są wyodrębniane w manifeście i używany do identyfikowania wstępnej elementów.</span><span class="sxs-lookup"><span data-stu-id="65a15-112">When the module is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease items.</span></span>
- <span data-ttu-id="65a15-113">Uzyskiwanie elementów wstępnej wymaga Dodawanie flagi - AllowPrerelease do polecenia PowerShellGet Znajdź-Module Install-Module moduł aktualizacji i Zapisz modułu.</span><span class="sxs-lookup"><span data-stu-id="65a15-113">Acquiring prerelease items requires adding -AllowPrerelease flag to the PowerShellGet commands Find-Module, Install-Module, Update-Module, and Save-Module.</span></span> <span data-ttu-id="65a15-114">Jeśli nie określono flagę, nie można wyświetlić elementy wersji wstępnej.</span><span class="sxs-lookup"><span data-stu-id="65a15-114">If the flag is not specified, prerelease items will not be shown.</span></span>
- <span data-ttu-id="65a15-115">Wersje modułu wyświetlane przez moduł znajdowania, Get-InstalledModule i w galerii programu PowerShell będą wyświetlane jako pojedynczy ciąg z wersji wstępnej ciąg dołączany, tak jak 2.5.0-alpha.</span><span class="sxs-lookup"><span data-stu-id="65a15-115">Module versions displayed by Find-Module, Get-InstalledModule, and in the PowerShell Gallery will be displayed as a single string with the Prerelease string appended, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="65a15-116">Poniżej znajdują się szczegółowe informacje dotyczące funkcji.</span><span class="sxs-lookup"><span data-stu-id="65a15-116">Details for the features are included below.</span></span>

<span data-ttu-id="65a15-117">Te zmiany nie wpływają na obsługę wersji modułu skompilowanego w programie PowerShell i są zgodne z programem PowerShell 3.0, 4.0 i 5.</span><span class="sxs-lookup"><span data-stu-id="65a15-117">These changes do not affect the module version support that is built into PowerShell, and are compatible with PowerShell 3.0, 4.0, and 5.</span></span>

## <a name="identifying-a-module-version-as-a-prerelease"></a><span data-ttu-id="65a15-118">Identyfikowanie wersji modułu jako wstępnej wersji</span><span class="sxs-lookup"><span data-stu-id="65a15-118">Identifying a module version as a prerelease</span></span>

<span data-ttu-id="65a15-119">Obsługa PowerShellGet wersje wstępne wymaga użycia dwóch pól w manifeście modułu:</span><span class="sxs-lookup"><span data-stu-id="65a15-119">PowerShellGet support for prerelease versions requires the use of two fields within the Module Manifest:</span></span>

- <span data-ttu-id="65a15-120">ModuleVersion zawarte w manifeście modułu musi być w wersji 3 części, jeśli wstępna wersja jest używana, a musi być zgodne z istniejącej wersji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="65a15-120">The ModuleVersion included in the module manifest must be a 3-part version if a prerelease version is used, and must comply with existing PowerShell versioning.</span></span> <span data-ttu-id="65a15-121">Format wersji będą A.B.C, gdzie A, B i C to wszystkie liczby całkowite.</span><span class="sxs-lookup"><span data-stu-id="65a15-121">The version format would be A.B.C, where A, B, and C are all integers.</span></span>
- <span data-ttu-id="65a15-122">Ciąg wersji wstępnej jest określona w manifeście modułu, w sekcji PSData PrivateData.</span><span class="sxs-lookup"><span data-stu-id="65a15-122">The Prerelease string is specified in the module manifest, in the PSData section of PrivateData.</span></span>

<span data-ttu-id="65a15-123">Szczegółowe wymagania na ciąg wersji wstępnej są poniżej.</span><span class="sxs-lookup"><span data-stu-id="65a15-123">Detailed requirements on the Prerelease string are below.</span></span>

<span data-ttu-id="65a15-124">Przykład części manifestu modułu, który definiuje moduł jako wstępnej wersji będzie wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="65a15-124">An example section of a module manifest that defines a module as a prerelease would look like the following:</span></span>

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

<span data-ttu-id="65a15-125">Szczegółowe wymagania dotyczące ciąg wersji wstępnej są:</span><span class="sxs-lookup"><span data-stu-id="65a15-125">The detailed requirements for Prerelease string are:</span></span>

- <span data-ttu-id="65a15-126">Ciąg wersji wstępnej może być określona tylko, gdy ModuleVersion jest 3 segmentów dla Major.Minor.Build.</span><span class="sxs-lookup"><span data-stu-id="65a15-126">Prerelease string may only be specified when the ModuleVersion is 3 segments for Major.Minor.Build.</span></span> <span data-ttu-id="65a15-127">Jest to zgodne z programu SemVer v1.0.0.</span><span class="sxs-lookup"><span data-stu-id="65a15-127">This aligns with SemVer v1.0.0.</span></span>
- <span data-ttu-id="65a15-128">Łącznik jest separator numer kompilacji i ciąg wersji wstępnej.</span><span class="sxs-lookup"><span data-stu-id="65a15-128">A hyphen is the delimiter between the Build number and the Prerelease string.</span></span> <span data-ttu-id="65a15-129">Łącznik mogą zostać zawarte w wersji wstępnej ciągu jako pierwszy znak, tylko.</span><span class="sxs-lookup"><span data-stu-id="65a15-129">A hyphen may be included in the Prerelease string as the first character, only.</span></span>
- <span data-ttu-id="65a15-130">Ciąg wersji wstępnej może zawierać tylko alfanumeryczne ASCII [0-9A-Za - z —].</span><span class="sxs-lookup"><span data-stu-id="65a15-130">The Prerelease string may contain only ASCII alphanumerics [0-9A-Za-z-].</span></span> <span data-ttu-id="65a15-131">Jest najlepszym rozwiązaniem jest rozpocząć wstępną ciąg znaków alfanumerycznych, ponieważ będzie on łatwiej zidentyfikować, że to jest wersja wstępna podczas skanowania listy elementów.</span><span class="sxs-lookup"><span data-stu-id="65a15-131">It is a best practice to begin the Prerelease string with an alpha character, as it will be easier to identify that this is a prerelease version when scanning a list of items.</span></span>
- <span data-ttu-id="65a15-132">Tylko programu SemVer v1.0.0 wstępnej ciągi są obsługiwane w tej chwili.</span><span class="sxs-lookup"><span data-stu-id="65a15-132">Only SemVer v1.0.0 prerelease strings are supported at this time.</span></span> <span data-ttu-id="65a15-133">Ciąg wersji wstępnej __nie mogą__ zawierać albo okres lub + [. +], które są dozwolone w programu SemVer 2.0.</span><span class="sxs-lookup"><span data-stu-id="65a15-133">Prerelease string __must not__ contain either period or + [.+], which are allowed in SemVer 2.0.</span></span>
- <span data-ttu-id="65a15-134">Przykłady obsługiwanych wersji wstępnej ciągu:-alfa, - 1,-BETA, - update20171020</span><span class="sxs-lookup"><span data-stu-id="65a15-134">Examples of supported Prerelease string are: -alpha, -alpha1, -BETA, -update20171020</span></span>

<span data-ttu-id="65a15-135">__Wpływ wersji wstępnej w folderach instalacji i kolejność sortowania__</span><span class="sxs-lookup"><span data-stu-id="65a15-135">__Prerelease versioning impact on sort order and installation folders__</span></span>

<span data-ttu-id="65a15-136">Kolejność sortowania zmian za pomocą wersji wstępnej, co jest ważne podczas publikowania w galerii programu PowerShell, a podczas instalowania modułów za pomocą polecenia PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="65a15-136">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing modules using PowerShellGet commands.</span></span> <span data-ttu-id="65a15-137">Jeśli określono ciąg wersji wstępnej dwa moduły, kolejność sortowania jest oparta na fragment ciągu, po łącznik.</span><span class="sxs-lookup"><span data-stu-id="65a15-137">If the Prerelease string is specified for two modules, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="65a15-138">Tak 2.5.0-alpha wersji jest mniejsza niż 2.5.0-beta, czyli mniej niż 2.5.0-gamma.</span><span class="sxs-lookup"><span data-stu-id="65a15-138">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="65a15-139">Jeśli dwa moduły mają tego samego ModuleVersion i tylko jeden z nich zawiera ciąg wersji wstępnej, modułu bez wstępnej ciąg zakłada, że wersja gotowe do produkcji i będą sortowane jako wersja większe niż (w tym wstępną wersję wstępną ciąg).</span><span class="sxs-lookup"><span data-stu-id="65a15-139">If two modules have the same ModuleVersion, and only one has a Prerelease string, the module without the Prerelease string is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version (which includes the Prerelease string).</span></span> <span data-ttu-id="65a15-140">Na przykład podczas porównywania zwalnia 2.5.0 i 2.5.0-beta, 2.5.0 wersji będą uznawane za większa niż dwa.</span><span class="sxs-lookup"><span data-stu-id="65a15-140">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="65a15-141">Podczas publikowania w galerii programu PowerShell, domyślnie wersję modułu publikowaną muszą mieć wyższej wersji niż wersja wszystkie wcześniej publikowane w galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="65a15-141">When publishing to the PowerShell Gallery, by default the version of the module being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span>

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a><span data-ttu-id="65a15-142">Wyszukiwanie i pobieranie elementów wstępnej za pomocą polecenia PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="65a15-142">Finding and acquiring prerelease items using PowerShellGet commands</span></span>

<span data-ttu-id="65a15-143">Zajmujących się wstępnej elementów za pomocą aktualizacji znajdź PowerShellGet-Module, Install-Module-modułu, i Zapisz modułu polecenia wymaga Dodawanie flagi - AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="65a15-143">Dealing with prerelease items using PowerShellGet Find-Module, Install-Module, Update-Module, and Save-Module commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="65a15-144">Jeśli określono - AllowPrerelease, elementy wstępnej można włączyć, jeśli są obecne.</span><span class="sxs-lookup"><span data-stu-id="65a15-144">If -AllowPrerelease is specified, prerelease items will be included if they are present.</span></span> <span data-ttu-id="65a15-145">Jeśli nie określono flagę - AllowPrerelease, nie można wyświetlić elementy wersji wstępnej.</span><span class="sxs-lookup"><span data-stu-id="65a15-145">If -AllowPrerelease flag is not specified, prerelease items will not be shown.</span></span>

<span data-ttu-id="65a15-146">Tylko wyjątki od tej reguły w poleceniach modułu PowerShellGet są Get InstalledModule i czasami modułem Odinstaluj.</span><span class="sxs-lookup"><span data-stu-id="65a15-146">The only exceptions to this in the PowerShellGet module commands are Get-InstalledModule, and some cases with Uninstall-Module.</span></span>

- <span data-ttu-id="65a15-147">Get-InstalledModule zawsze automatycznie wyświetli informacje o wersji wstępnej w ciągu wersji dla modułów.</span><span class="sxs-lookup"><span data-stu-id="65a15-147">Get-InstalledModule always will automatically show the prerelease information in the version string for modules.</span></span>
- <span data-ttu-id="65a15-148">Odinstaluj moduł domyślnie odinstaluje najnowszej wersji modułu, jeśli __nie została zainstalowana wersja__ jest określona.</span><span class="sxs-lookup"><span data-stu-id="65a15-148">Uninstall-Module will by default uninstall the most recent version of a module, if __no version__ is specified.</span></span> <span data-ttu-id="65a15-149">To zachowanie nie została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="65a15-149">That behavior has not changed.</span></span> <span data-ttu-id="65a15-150">Jednak jeśli wstępna wersja jest określona za pomocą - RequiredVersion, - AllowPrerelease będzie wymagane.</span><span class="sxs-lookup"><span data-stu-id="65a15-150">However, if a prerelease version is specified using -RequiredVersion, -AllowPrerelease will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="65a15-151">Przykłady</span><span class="sxs-lookup"><span data-stu-id="65a15-151">Examples</span></span>

```powershell
# Assume the PowerShell Gallery has TestPackage module versions 1.8.0 and 1.9.0-alpha.
# If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
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

<span data-ttu-id="65a15-152">Instalacja Side-by-side wersji modułu, które różnią się tylko ze względu na określony wstępną nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="65a15-152">Side-by-side installation of versions of a module that differ only due to the prerelease specified is not supported.</span></span> <span data-ttu-id="65a15-153">Podczas instalowania modułu przy użyciu PowerShellGet, różne wersje tego samego modułu są zainstalowane obok siebie, tworząc nazwę folderu przy użyciu ModuleVersion.</span><span class="sxs-lookup"><span data-stu-id="65a15-153">When installing a module using PowerShellGet, different versions of the same module are installed side-by-side by creating a folder name using the ModuleVersion.</span></span> <span data-ttu-id="65a15-154">ModuleVersion, bez wstępnej ciąg jest używany dla nazwy folderu.</span><span class="sxs-lookup"><span data-stu-id="65a15-154">The ModuleVersion, without the prerelease string, is used for the folder name.</span></span> <span data-ttu-id="65a15-155">Jeśli użytkownik zainstaluje MyModule 2.5.0-alpha wersji, zostanie zainstalowana w folderze MyModule\2.5.0.</span><span class="sxs-lookup"><span data-stu-id="65a15-155">If a user installs MyModule version 2.5.0-alpha, it will be installed to the MyModule\2.5.0 folder.</span></span> <span data-ttu-id="65a15-156">Jeśli użytkownik zainstaluje następnie 2.5.0-beta, wersja 2.5.0-beta będzie __uwierzytelniając zapisu__ zawartość folderu MyModule\2.5.0.</span><span class="sxs-lookup"><span data-stu-id="65a15-156">If the user then installs 2.5.0-beta, the 2.5.0-beta version will __over-write__ the contents of the folder MyModule\2.5.0.</span></span> <span data-ttu-id="65a15-157">Jedną z zalet tego podejścia jest, że nie istnieje potrzeba aby odinstalować wstępną wersję po zainstalowaniu wersji gotowe do produkcji.</span><span class="sxs-lookup"><span data-stu-id="65a15-157">One advantage to this approach is that there is no need to un-install the prerelease version after installing the production-ready version.</span></span> <span data-ttu-id="65a15-158">W poniższym przykładzie pokazano, czego można oczekiwać:</span><span class="sxs-lookup"><span data-stu-id="65a15-158">The example below shows what to expect:</span></span>

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

<span data-ttu-id="65a15-159">Odinstalowanie modułu spowoduje usunięcie najnowszej wersji modułu, gdy - RequiredVersion nie jest dostarczony.</span><span class="sxs-lookup"><span data-stu-id="65a15-159">Uninstall-Module will remove the latest version of a module when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="65a15-160">Jeśli określono - RequiredVersion i jest wersja wstępna, - AllowPrerelease należy dodać do polecenia.</span><span class="sxs-lookup"><span data-stu-id="65a15-160">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

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

## <a name="more-details"></a><span data-ttu-id="65a15-161">więcej informacji</span><span class="sxs-lookup"><span data-stu-id="65a15-161">More details</span></span>

- [<span data-ttu-id="65a15-162">Wersji wstępnej skryptu</span><span class="sxs-lookup"><span data-stu-id="65a15-162">Prerelease Script Versions</span></span>](script-prerelease-support.md)
- [<span data-ttu-id="65a15-163">Znajdź moduł</span><span class="sxs-lookup"><span data-stu-id="65a15-163">Find-Module</span></span>](/powershell/module/powershellget/find-module)
- [<span data-ttu-id="65a15-164">Install-Module</span><span class="sxs-lookup"><span data-stu-id="65a15-164">Install-Module</span></span>](/powershell/module/powershellget/install-module)
- [<span data-ttu-id="65a15-165">Save-Module</span><span class="sxs-lookup"><span data-stu-id="65a15-165">Save-Module</span></span>](/powershell/module/powershellget/save-module)
- [<span data-ttu-id="65a15-166">Update-Module</span><span class="sxs-lookup"><span data-stu-id="65a15-166">Update-Module</span></span>](/powershell/module/powershellget/Update-Module)
- [<span data-ttu-id="65a15-167">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="65a15-167">Get-InstalledModule</span></span>](/powershell/module/powershellget/get-installedmodule)
- [<span data-ttu-id="65a15-168">Odinstaluj moduł</span><span class="sxs-lookup"><span data-stu-id="65a15-168">UnInstall-Module</span></span>](/powershell/gallery/psget/module/psget_uninstall-module)