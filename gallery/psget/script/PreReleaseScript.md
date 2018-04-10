---
ms.date: 10/17/2017
contributor: keithb
ms.topic: reference
keywords: Galeria, programu powershell, polecenia cmdlet, psget
title: PrereleaseScript
ms.openlocfilehash: 575babd6bc373e99a4e924fafef6e9edeec972d4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="prerelease-versions-of-scripts"></a><span data-ttu-id="8adf9-103">Wersje wstępne skryptów</span><span class="sxs-lookup"><span data-stu-id="8adf9-103">Prerelease Versions of Scripts</span></span>

<span data-ttu-id="8adf9-104">Począwszy od wersji 1.6.0 PowerShellGet i galerii programu PowerShell zapewniają obsługę znakowania w wersjach nowszych niż 1.0.0 jako wstępnej wersji.</span><span class="sxs-lookup"><span data-stu-id="8adf9-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="8adf9-105">Przed tej funkcji wersji wstępnej elementy były ograniczone do o wersji, począwszy od 0.</span><span class="sxs-lookup"><span data-stu-id="8adf9-105">Prior to this feature, prerelease items were limited to having a version beginning with 0.</span></span> <span data-ttu-id="8adf9-106">Celem tych funkcji jest zapewniają lepsze wsparcie [v1.0.0 programu SemVer](http://semver.org/spec/v1.0.0.html) Konwencji versioning bez przerywania zapewnienia zgodności z programu PowerShell 3 i powyżej lub istniejącej wersji programu PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="8adf9-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span>
<span data-ttu-id="8adf9-107">Ten temat koncentruje się na funkcji specyficznych dla skryptu.</span><span class="sxs-lookup"><span data-stu-id="8adf9-107">This topic focuses on the script-specific features.</span></span> <span data-ttu-id="8adf9-108">Są równoważne funkcje dla modułów [wstępnej wersji modułu](../module/PrereleaseModule.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="8adf9-108">The equivalent features for modules are in the [Prerelease Module Versions](../module/PrereleaseModule.md) topic.</span></span> <span data-ttu-id="8adf9-109">Korzystanie z tych funkcji, wydawców można zidentyfikować skrypt jako 2.5.0-alpha wersji, a później Zwolnij wersji gotowe do produkcji 2.5.0 zastępuje wersji wstępnej.</span><span class="sxs-lookup"><span data-stu-id="8adf9-109">Using these features, publishers can identify a script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="8adf9-110">Na wysokim poziomie funkcje wersji wstępnej skryptu obejmują:</span><span class="sxs-lookup"><span data-stu-id="8adf9-110">At a high level, the prerelease script features include:</span></span>

* <span data-ttu-id="8adf9-111">Dodanie sufiksu PrereleaseString ciąg wersji w manifeście skryptu.</span><span class="sxs-lookup"><span data-stu-id="8adf9-111">Adding a PrereleaseString suffix to the version string in the script manifest.</span></span>
<span data-ttu-id="8adf9-112">Gdy skryptów zostanie opublikowany w galerii programu PowerShell, te dane są wyodrębniane w manifeście i używany do identyfikowania wstępnej elementów.</span><span class="sxs-lookup"><span data-stu-id="8adf9-112">When the scripts is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease items.</span></span>
* <span data-ttu-id="8adf9-113">Uzyskiwanie elementów wstępnej wymaga Dodawanie flagi - AllowPrerelease do polecenia PowerShellGet Znajdź skryptów skrypt instalacji skryptu aktualizacji i Zapisz skrypt.</span><span class="sxs-lookup"><span data-stu-id="8adf9-113">Acquiring prerelease items requires adding -AllowPrerelease flag to the PowerShellGet commands Find-Script, Install-Script, Update-Script, and Save-Script.</span></span>
<span data-ttu-id="8adf9-114">Jeśli nie określono flagę, nie można wyświetlić elementy wersji wstępnej.</span><span class="sxs-lookup"><span data-stu-id="8adf9-114">If the flag is not specified, prerelease items will not be shown.</span></span>
* <span data-ttu-id="8adf9-115">Wersje skryptu wyświetlane przez skrypt Znajdź, Get-InstalledScript i w galerii programu PowerShell zostanie wyświetlony z PrereleaseString, tak jak 2.5.0-alpha.</span><span class="sxs-lookup"><span data-stu-id="8adf9-115">Script versions displayed by Find-Script, Get-InstalledScript, and in the PowerShell Gallery will be displayed with the PrereleaseString, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="8adf9-116">Poniżej znajdują się szczegółowe informacje dotyczące funkcji.</span><span class="sxs-lookup"><span data-stu-id="8adf9-116">Details for the features are included below.</span></span>


## <a name="identifying-a-script-version-as-a-prerelease"></a><span data-ttu-id="8adf9-117">Identyfikowanie jako wersja wstępna wersja skryptu</span><span class="sxs-lookup"><span data-stu-id="8adf9-117">Identifying a script version as a prerelease</span></span>

<span data-ttu-id="8adf9-118">Obsługa PowerShellGet wersje wstępne jest łatwiej niż moduły skryptów.</span><span class="sxs-lookup"><span data-stu-id="8adf9-118">PowerShellGet support for prerelease versions is easier for scripts than modules.</span></span>
<span data-ttu-id="8adf9-119">Przechowywanie wersji skryptu jest obsługiwana przez PowerShellGet, tylko, dlatego nie ma żadnych problemów ze zgodnością spowodowane przez dodanie ciągu wersji wstępnej.</span><span class="sxs-lookup"><span data-stu-id="8adf9-119">Script versioning is only supported by PowerShellGet, so there are no compatibility issues caused by adding the prerelease string.</span></span>
<span data-ttu-id="8adf9-120">Aby zidentyfikować skryptu w galerii programu PowerShell jako wstępnej wersji, należy dodać sufiks wersji wstępnej do ciąg wersji poprawnie sformatowana w metadanych skryptu.</span><span class="sxs-lookup"><span data-stu-id="8adf9-120">To identify a script in the PowerShell Gallery as a prerelease, add a prerelease suffix to a properly-formatted version string in the script metadata.</span></span>

<span data-ttu-id="8adf9-121">Przykład części manifestu skryptu z wersji wstępnej może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="8adf9-121">An example section of a script manifest with a prerelease version would look like the following:</span></span>
```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>

```

<span data-ttu-id="8adf9-122">Aby używać sufiksu wstępnej, ciąg wersji musi spełniać następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="8adf9-122">To use a prerelease suffix, the version string must meet the following requirements:</span></span>

* <span data-ttu-id="8adf9-123">Sufiks wstępnej może być określona tylko w przypadku wersji 3 segmentów dla Major.Minor.Build.</span><span class="sxs-lookup"><span data-stu-id="8adf9-123">A prerelease suffix may only be specified when the Version is 3 segments for Major.Minor.Build.</span></span> <span data-ttu-id="8adf9-124">Jest to zgodne z programu SemVer v1.0.0</span><span class="sxs-lookup"><span data-stu-id="8adf9-124">This aligns with SemVer v1.0.0</span></span>
* <span data-ttu-id="8adf9-125">Wstępna sufiks jest ciągiem, który rozpoczyna się od łącznika i może zawierać alfanumeryczne ASCII [0-9A-Za - z —]</span><span class="sxs-lookup"><span data-stu-id="8adf9-125">The prerelease suffix is a string which begins with a hyphen, and may contain ASCII alphanumerics [0-9A-Za-z-]</span></span>
* <span data-ttu-id="8adf9-126">Tylko ciągi wersji wstępnej programu SemVer v1.0.0 są obsługiwane w tej chwili tak wstępnej sufiks __nie mogą__ zawierać albo okres lub + [. +], które są dozwolone w programu SemVer 2.0</span><span class="sxs-lookup"><span data-stu-id="8adf9-126">Only SemVer v1.0.0 prerelease strings are supported at this time, so the prerelease suffix __must not__ contain either period or + [.+], which are allowed in SemVer 2.0</span></span>
* <span data-ttu-id="8adf9-127">Przykłady obsługiwanych ciągów PrereleaseString:-alfa, - 1,-BETA, - update20171020</span><span class="sxs-lookup"><span data-stu-id="8adf9-127">Examples of supported PrereleaseString strings are: -alpha, -alpha1, -BETA, -update20171020</span></span>

<span data-ttu-id="8adf9-128">__Wpływ wersji wstępnej w folderach instalacji i kolejność sortowania__</span><span class="sxs-lookup"><span data-stu-id="8adf9-128">__Prerelease versioning impact on sort order and installation folders__</span></span>

<span data-ttu-id="8adf9-129">Kolejność sortowania zmian za pomocą wersji wstępnej, co jest ważne podczas publikowania w galerii programu PowerShell, a podczas instalowania skryptów przy użyciu polecenia PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="8adf9-129">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing scripts using PowerShellGet commands.</span></span>
<span data-ttu-id="8adf9-130">Jeśli dwa skrypty wersji z numerem wersji istnieje, kolejność sortowania jest oparta na części ciągu po łącznik.</span><span class="sxs-lookup"><span data-stu-id="8adf9-130">If two scripts versions with the version number exist, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="8adf9-131">Tak 2.5.0-alpha wersji jest mniejsza niż 2.5.0-beta, czyli mniej niż 2.5.0-gamma.</span><span class="sxs-lookup"><span data-stu-id="8adf9-131">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span>
<span data-ttu-id="8adf9-132">Jeśli dwa skrypty mają ten sam numer wersji i tylko jeden z nich ma PrereleaseString, skrypt __bez__ wstępnej sufiks zakłada, że wersja gotowe do produkcji i będą sortowane jako wersja większa niż wstępną Wersja.</span><span class="sxs-lookup"><span data-stu-id="8adf9-132">If two scripts have the same version number, and only one has a PrereleaseString, the script __without__ the prerelease suffix is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version.</span></span>
<span data-ttu-id="8adf9-133">Na przykład podczas porównywania zwalnia 2.5.0 i 2.5.0-beta, 2.5.0 wersji będą uznawane za większa niż dwa.</span><span class="sxs-lookup"><span data-stu-id="8adf9-133">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="8adf9-134">Podczas publikowania w galerii programu PowerShell, domyślnie wersji skryptu publikowaną muszą mieć wyższej wersji niż wersja wszystkie wcześniej publikowane w galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8adf9-134">When publishing to the PowerShell Gallery, by default the version of the script being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span>
<span data-ttu-id="8adf9-135">Wydawcą może zaktualizować 2.5.0-alpha wersji 2.5.0-beta lub 2.5.0 (sufiksem nie wstępnej).</span><span class="sxs-lookup"><span data-stu-id="8adf9-135">A publisher may update version 2.5.0-alpha with 2.5.0-beta, or with 2.5.0 (with no prerelease suffix).</span></span>

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a><span data-ttu-id="8adf9-136">Wyszukiwanie i pobieranie elementów wstępnej za pomocą polecenia PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="8adf9-136">Finding and acquiring prerelease items using PowerShellGet commands</span></span>

<span data-ttu-id="8adf9-137">Zajmujących się wstępnej elementów za pomocą skryptu-PowerShellGet Znajdź skryptów, skrypt instalacji aktualizacji, i Zapisz skrypt poleceń wymaga Dodawanie flagi - AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="8adf9-137">Dealing with prerelease items using PowerShellGet Find-Script, Install-Script, Update-Script, and Save-Script commands requires adding the -AllowPrerelease flag.</span></span>
<span data-ttu-id="8adf9-138">Jeśli określono - AllowPrerelease, elementy wstępnej można włączyć, jeśli są obecne.</span><span class="sxs-lookup"><span data-stu-id="8adf9-138">If -AllowPrerelease is specified, prerelease items will be included if they are present.</span></span>
<span data-ttu-id="8adf9-139">Jeśli nie określono flagę - AllowPrerelease, nie można wyświetlić elementy wersji wstępnej.</span><span class="sxs-lookup"><span data-stu-id="8adf9-139">If -AllowPrerelease flag is not specified, prerelease items will not be shown.</span></span>

<span data-ttu-id="8adf9-140">Tylko wyjątki od tej reguły w poleceń skryptu PowerShellGet są Get InstalledScript i czasami z skrypt dezinstalacji skryptu.</span><span class="sxs-lookup"><span data-stu-id="8adf9-140">The only exceptions to this in the PowerShellGet script commands are Get-InstalledScript, and some cases with Uninstall-Script.</span></span>

* <span data-ttu-id="8adf9-141">Get-InstalledScript zawsze automatycznie wyświetli informacje o wersji wstępnej w ciągu wersji Jeśli jest obecny.</span><span class="sxs-lookup"><span data-stu-id="8adf9-141">Get-InstalledScript always will automatically show the prerelease information in the version string if it is present.</span></span>
* <span data-ttu-id="8adf9-142">Odinstaluj skryptu domyślnie odinstaluje najnowszej wersji skryptu, jeśli __nie została zainstalowana wersja__ jest określona.</span><span class="sxs-lookup"><span data-stu-id="8adf9-142">Uninstall-Script will by default uninstall the most recent version of a script, if __no version__ is specified.</span></span> <span data-ttu-id="8adf9-143">To zachowanie nie została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="8adf9-143">That behavior has not changed.</span></span> <span data-ttu-id="8adf9-144">Jednak jeśli wstępna wersja jest określona za pomocą - RequiredVersion, - AllowPrerelease będzie wymagane.</span><span class="sxs-lookup"><span data-stu-id="8adf9-144">However, if a prerelease version is specified using -RequiredVersion, -AllowPrerelease will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="8adf9-145">Przykłady</span><span class="sxs-lookup"><span data-stu-id="8adf9-145">Examples</span></span>
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

<span data-ttu-id="8adf9-146">Odinstaluj skryptu spowoduje usunięcie bieżącej wersji skryptu po - RequiredVersion nie jest dostarczony.</span><span class="sxs-lookup"><span data-stu-id="8adf9-146">Uninstall-Script will remove the current version of a script when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="8adf9-147">Jeśli określono - RequiredVersion i jest wersja wstępna, - AllowPrerelease należy dodać do polecenia.</span><span class="sxs-lookup"><span data-stu-id="8adf9-147">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

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



## <a name="more-details"></a><span data-ttu-id="8adf9-148">więcej informacji</span><span class="sxs-lookup"><span data-stu-id="8adf9-148">More details</span></span>
### <a name="prerelease-module-versionsmoduleprereleasemodulemd"></a>[<span data-ttu-id="8adf9-149">Wersji wstępnej modułów</span><span class="sxs-lookup"><span data-stu-id="8adf9-149">Prerelease Module Versions</span></span>](../module/PrereleaseModule.md)
### <a name="find-scriptpsgetfind-scriptmd"></a>[<span data-ttu-id="8adf9-150">Znajdź skryptu</span><span class="sxs-lookup"><span data-stu-id="8adf9-150">Find-script</span></span>](./psget_find-script.md)
### <a name="install-scriptpsgetinstall-scriptmd"></a>[<span data-ttu-id="8adf9-151">Skrypt instalacji</span><span class="sxs-lookup"><span data-stu-id="8adf9-151">Install-script</span></span>](./psget_install-script.md)
### <a name="save-scriptpsgetsave-scriptmd"></a>[<span data-ttu-id="8adf9-152">Save-script</span><span class="sxs-lookup"><span data-stu-id="8adf9-152">Save-script</span></span>](./psget_save-script.md)
### <a name="update-scriptpsgetupdate-scriptmd"></a>[<span data-ttu-id="8adf9-153">Update-script</span><span class="sxs-lookup"><span data-stu-id="8adf9-153">Update-script</span></span>](./psget_update-script.md)
### <a name="get-installedscriptpsgetget-installedscriptmd"></a>[<span data-ttu-id="8adf9-154">Get-Installedscript</span><span class="sxs-lookup"><span data-stu-id="8adf9-154">Get-Installedscript</span></span>](./psget_get-installedscript.md)
### <a name="uninstall-scriptpsgetuninstall-scriptmd"></a>[<span data-ttu-id="8adf9-155">UnInstall-script</span><span class="sxs-lookup"><span data-stu-id="8adf9-155">UnInstall-script</span></span>](./psget_uninstall-script.md)