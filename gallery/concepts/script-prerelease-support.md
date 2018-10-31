---
ms.date: 10/17/2017
contributor: keithb
keywords: Galeria, programu powershell, polecenie cmdlet, psget
title: Wersje wstępne skryptów
ms.openlocfilehash: 4e7eab682008ed57163c51fe3a61a744b347bef2
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002739"
---
# <a name="prerelease-versions-of-scripts"></a><span data-ttu-id="04584-103">Wersje wstępne skryptów</span><span class="sxs-lookup"><span data-stu-id="04584-103">Prerelease versions of scripts</span></span>

<span data-ttu-id="04584-104">Począwszy od wersji 1.6.0 modułu PowerShellGet oraz spełnione galerii programu PowerShell zapewniają obsługę tagowania w wersjach nowszych niż 1.0.0 jako wersji wstępnej.</span><span class="sxs-lookup"><span data-stu-id="04584-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="04584-105">Przed tą funkcją pakiety w wersjach wstępnych były korzystać z wersji począwszy od 0.</span><span class="sxs-lookup"><span data-stu-id="04584-105">Prior to this feature, prerelease packages were limited to having a version beginning with 0.</span></span> <span data-ttu-id="04584-106">Celem tych funkcji jest zapewniają lepsze wsparcie [1.0.0 SemVer](http://semver.org/spec/v1.0.0.html) Konwencji wersji bez przerywania wstecznej zgodności przy użyciu programu PowerShell 3 i powyżej lub istniejącej wersji programu PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="04584-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="04584-107">Ten temat koncentruje się na funkcji specyficznych dla skryptu.</span><span class="sxs-lookup"><span data-stu-id="04584-107">This topic focuses on the script-specific features.</span></span> <span data-ttu-id="04584-108">Równoważne funkcje dla modułów znajdują się w [wersje modułu wersję wstępną](module-prerelease-support.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="04584-108">The equivalent features for modules are in the [Prerelease Module Versions](module-prerelease-support.md) topic.</span></span> <span data-ttu-id="04584-109">Korzystając z tych funkcji, wydawców można skrypt jako 2.5.0-alpha wersji i później wydanej wersji gotowe do produkcji 2.5.0, która zastępuje wersję wstępną.</span><span class="sxs-lookup"><span data-stu-id="04584-109">Using these features, publishers can identify a script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="04584-110">Na wysokim poziomie funkcje wersji wstępnej skryptu obejmują:</span><span class="sxs-lookup"><span data-stu-id="04584-110">At a high level, the prerelease script features include:</span></span>

- <span data-ttu-id="04584-111">Dodanie do ciąg wersji w manifeście skrypt sufiksu PrereleaseString.</span><span class="sxs-lookup"><span data-stu-id="04584-111">Adding a PrereleaseString suffix to the version string in the script manifest.</span></span> <span data-ttu-id="04584-112">Po opublikowaniu skrypty w galerii programu PowerShell te dane są wyodrębniane z manifestu i używany do identyfikowania pakiety w wersjach wstępnych.</span><span class="sxs-lookup"><span data-stu-id="04584-112">When the scripts is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease packages.</span></span>
- <span data-ttu-id="04584-113">Pobieranie pakietów wydań wstępnych wymaga dodanie flagi - AllowPrerelease poleceń modułu PowerShellGet Find-Script skrypt instalacji skryptu aktualizacji i Zapisz skrypt.</span><span class="sxs-lookup"><span data-stu-id="04584-113">Acquiring prerelease packages requires adding -AllowPrerelease flag to the PowerShellGet commands Find-Script, Install-Script, Update-Script, and Save-Script.</span></span> <span data-ttu-id="04584-114">Jeśli nie określono flagę, pakiety w wersjach wstępnych nie będą wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="04584-114">If the flag is not specified, prerelease packages will not be shown.</span></span>
- <span data-ttu-id="04584-115">Wersje skryptu wyświetlane przez Find-Script, Get-InstalledScript i w galerii programu PowerShell będą wyświetlane z PrereleaseString, tak jak 2.5.0-alpha.</span><span class="sxs-lookup"><span data-stu-id="04584-115">Script versions displayed by Find-Script, Get-InstalledScript, and in the PowerShell Gallery will be displayed with the PrereleaseString, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="04584-116">Poniżej znajdują się szczegółowe informacje dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="04584-116">Details for the features are included below.</span></span>

## <a name="identifying-a-script-version-as-a-prerelease"></a><span data-ttu-id="04584-117">Identyfikowanie wersji skryptu jako wersji wstępnej</span><span class="sxs-lookup"><span data-stu-id="04584-117">Identifying a script version as a prerelease</span></span>

<span data-ttu-id="04584-118">Obsługa modułu PowerShellGet wersje wstępne jest łatwiejsze w przypadku skryptów niż moduły.</span><span class="sxs-lookup"><span data-stu-id="04584-118">PowerShellGet support for prerelease versions is easier for scripts than modules.</span></span> <span data-ttu-id="04584-119">Przechowywanie wersji skrypt jest obsługiwany tylko modułu PowerShellGet, więc nie ma żadnych problemów ze zgodnością spowodowane przez dodanie ciągu wersji wstępnej.</span><span class="sxs-lookup"><span data-stu-id="04584-119">Script versioning is only supported by PowerShellGet, so there are no compatibility issues caused by adding the prerelease string.</span></span> <span data-ttu-id="04584-120">Aby określić skrypt w galerii programu PowerShell, zgodnie z wersji wstępnej, należy dodać sufiks wersji wstępnej do wersji poprawnie sformatowany ciąg znaków w metadanych skryptów.</span><span class="sxs-lookup"><span data-stu-id="04584-120">To identify a script in the PowerShell Gallery as a prerelease, add a prerelease suffix to a properly-formatted version string in the script metadata.</span></span>

<span data-ttu-id="04584-121">Przykład części manifestu skryptu za pomocą wersji wstępnej powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="04584-121">An example section of a script manifest with a prerelease version would look like the following:</span></span>

```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>
```

<span data-ttu-id="04584-122">Aby użyć sufiks wersji wstępnej, ciąg wersji musi spełniać następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="04584-122">To use a prerelease suffix, the version string must meet the following requirements:</span></span>

- <span data-ttu-id="04584-123">Sufiks wersji wstępnej może być określona tylko, gdy wersja jest 3 segmenty dla główna.pomocnicza.kompilacja.</span><span class="sxs-lookup"><span data-stu-id="04584-123">A prerelease suffix may only be specified when the Version is 3 segments for Major.Minor.Build.</span></span>
  <span data-ttu-id="04584-124">Jest to zgodne z 1.0.0 SemVer</span><span class="sxs-lookup"><span data-stu-id="04584-124">This aligns with SemVer v1.0.0</span></span>
- <span data-ttu-id="04584-125">Wstępna sufiks jest to ciąg, który rozpoczyna się łącznikiem i może zawierać znaki alfanumeryczne ASCII [0-9A-Za - z-]</span><span class="sxs-lookup"><span data-stu-id="04584-125">The prerelease suffix is a string which begins with a hyphen, and may contain ASCII alphanumerics [0-9A-Za-z-]</span></span>
- <span data-ttu-id="04584-126">Tylko ciągi wstępna wersja 1.0.0 SemVer są obsługiwane w tej chwili więc sufiks wersji wstępnej **nie** zawierać albo okres lub + [. +], mogą SemVer w wersji 2.0</span><span class="sxs-lookup"><span data-stu-id="04584-126">Only SemVer v1.0.0 prerelease strings are supported at this time, so the prerelease suffix **must not** contain either period or + [.+], which are allowed in SemVer 2.0</span></span>
- <span data-ttu-id="04584-127">Przykłady obsługiwanych ciągów PrereleaseString:-alfa, - 1,-BETA, - update20171020</span><span class="sxs-lookup"><span data-stu-id="04584-127">Examples of supported PrereleaseString strings are: -alpha, -alpha1, -BETA, -update20171020</span></span>

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a><span data-ttu-id="04584-128">Wpływ wersji wstępnej w folderach instalacji i kolejność sortowania</span><span class="sxs-lookup"><span data-stu-id="04584-128">Prerelease versioning impact on sort order and installation folders</span></span>

<span data-ttu-id="04584-129">Kolejność sortowania zmienia się podczas korzystania z wersji wstępnej, co jest ważne w przypadku publikowania w galerii programu PowerShell, a podczas instalowania skryptów przy użyciu poleceń modułu PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="04584-129">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing scripts using PowerShellGet commands.</span></span> <span data-ttu-id="04584-130">Jeśli dwa skrypty w wersji z numerem wersji istnieją, kolejność sortowania jest oparty na fragment ciągu, postępując łącznika.</span><span class="sxs-lookup"><span data-stu-id="04584-130">If two scripts versions with the version number exist, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="04584-131">Dlatego 2.5.0-alpha wersji jest mniejszy niż 2.5.0-beta, która jest mniejsza niż 2.5.0-gamma.</span><span class="sxs-lookup"><span data-stu-id="04584-131">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="04584-132">Jeśli dwa skrypty mają ten sam numer wersji, i tylko jeden PrereleaseString, skrypt **bez** sufiks wersji wstępnej zakłada, że wersja gotowe do produkcji i będą sortowane jako nowszej wersji niż wersja wstępna Wersja.</span><span class="sxs-lookup"><span data-stu-id="04584-132">If two scripts have the same version number, and only one has a PrereleaseString, the script **without** the prerelease suffix is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version.</span></span> <span data-ttu-id="04584-133">Na przykład podczas porównywania zwalnia 2.5.0 i 2.5.0-beta, 2.5.0 wersji będą uznawane za większa niż dwa.</span><span class="sxs-lookup"><span data-stu-id="04584-133">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="04584-134">Publikowanie w galerii programu PowerShell, domyślnie wersja skryptu publikacji musi mieć nieco większa niż wersja wszystkie wcześniej publikowane w galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="04584-134">When publishing to the PowerShell Gallery, by default the version of the script being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span> <span data-ttu-id="04584-135">Wydawca może aktualizować 2.5.0-alpha wersji 2.5.0-beta lub z 2.5.0 (sufiksem nie wstępnej).</span><span class="sxs-lookup"><span data-stu-id="04584-135">A publisher may update version 2.5.0-alpha with 2.5.0-beta, or with 2.5.0 (with no prerelease suffix).</span></span>

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a><span data-ttu-id="04584-136">Znajdowanie i Uzyskiwanie pakietów wydań wstępnych przy użyciu poleceń modułu PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="04584-136">Finding and acquiring prerelease packages using PowerShellGet commands</span></span>

<span data-ttu-id="04584-137">Obsługa pakietów wydań wstępnych przy użyciu skryptu-PowerShellGet Find-Script, skrypt instalacji aktualizacji, a polecenia Save-Script wymaga dodanie flagi - AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="04584-137">Dealing with prerelease packages using PowerShellGet Find-Script, Install-Script, Update-Script, and Save-Script commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="04584-138">Jeśli określono - AllowPrerelease, pakiety w wersjach wstępnych zostaną dołączone, jeśli są obecne.</span><span class="sxs-lookup"><span data-stu-id="04584-138">If -AllowPrerelease is specified, prerelease packages will be included if they are present.</span></span> <span data-ttu-id="04584-139">Jeśli nie określono flagę - AllowPrerelease, pakiety w wersjach wstępnych nie będą wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="04584-139">If -AllowPrerelease flag is not specified, prerelease packages will not be shown.</span></span>

<span data-ttu-id="04584-140">Jedynym wyjątkiem od tej w poleceniach skryptu PowerShellGet są Get InstalledScript i czasami z skrypt dezinstalacji.</span><span class="sxs-lookup"><span data-stu-id="04584-140">The only exceptions to this in the PowerShellGet script commands are Get-InstalledScript, and some cases with Uninstall-Script.</span></span>

- <span data-ttu-id="04584-141">Get-InstalledScript zawsze automatycznie wyświetli informacje wstępne w ciągu wersji Jeśli jest obecny.</span><span class="sxs-lookup"><span data-stu-id="04584-141">Get-InstalledScript always will automatically show the prerelease information in the version string if it is present.</span></span>
- <span data-ttu-id="04584-142">Odinstaluj skryptu domyślnie odinstaluje najnowszej wersji skryptu, jeśli **nie została zainstalowana wersja** jest określony.</span><span class="sxs-lookup"><span data-stu-id="04584-142">Uninstall-Script will by default uninstall the most recent version of a script, if **no version** is specified.</span></span> <span data-ttu-id="04584-143">To zachowanie nie zmienił się.</span><span class="sxs-lookup"><span data-stu-id="04584-143">That behavior has not changed.</span></span> <span data-ttu-id="04584-144">Jednakże jeśli jest to wersja wstępna produktu jest określony, przy użyciu `-RequiredVersion`, `-AllowPrerelease` będą wymagane.</span><span class="sxs-lookup"><span data-stu-id="04584-144">However, if a prerelease version is specified using `-RequiredVersion`, `-AllowPrerelease` will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="04584-145">Przykłady</span><span class="sxs-lookup"><span data-stu-id="04584-145">Examples</span></span>

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
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage)[Find-Package], Exception
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

<span data-ttu-id="04584-146">Odinstaluj skrypt spowoduje usunięcie bieżącej wersji skryptu, gdy - RequiredVersion nie zostanie dostarczona.</span><span class="sxs-lookup"><span data-stu-id="04584-146">Uninstall-Script will remove the current version of a script when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="04584-147">Jeśli - RequiredVersion zostanie określona, jest w wersji wstępnej, - AllowPrerelease należy dodać do polecenia.</span><span class="sxs-lookup"><span data-stu-id="04584-147">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

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

## <a name="more-details"></a><span data-ttu-id="04584-148">Więcej szczegółów</span><span class="sxs-lookup"><span data-stu-id="04584-148">More details</span></span>

- [<span data-ttu-id="04584-149">Wersje wstępne modułu</span><span class="sxs-lookup"><span data-stu-id="04584-149">Prerelease Module Versions</span></span>](module-prerelease-support.md)
- [<span data-ttu-id="04584-150">Znajdź script</span><span class="sxs-lookup"><span data-stu-id="04584-150">Find-script</span></span>](/powershell/module/powershellget/find-script)
- [<span data-ttu-id="04584-151">Skrypt instalacji</span><span class="sxs-lookup"><span data-stu-id="04584-151">Install-script</span></span>](/powershell/module/powershellget/install-script)
- [<span data-ttu-id="04584-152">Save-script</span><span class="sxs-lookup"><span data-stu-id="04584-152">Save-script</span></span>](/powershell/module/powershellget/save-script)
- [<span data-ttu-id="04584-153">Skrypt aktualizacji</span><span class="sxs-lookup"><span data-stu-id="04584-153">Update-script</span></span>](/powershell/module/powershellget/update-script)
- [<span data-ttu-id="04584-154">Get-Installedscript</span><span class="sxs-lookup"><span data-stu-id="04584-154">Get-Installedscript</span></span>](/powershell/module/powershellget/get-installedscript)
- [<span data-ttu-id="04584-155">Odinstaluj skryptu</span><span class="sxs-lookup"><span data-stu-id="04584-155">UnInstall-script</span></span>](/powershell/module/powershellget/uninstall-script)
