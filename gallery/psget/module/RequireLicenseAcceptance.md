---
ms.date: 2017-06-09
schema: 2.0.0
keywords: "Środowiska PowerShell"
title: RequireLicenseAcceptance
ms.openlocfilehash: 260ccc1ee52d09a640e88203c5644f20f9723d6f
ms.sourcegitcommit: cd66d4f49ea762a31887af2c72d087b219ddbe10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2017
---
# <a name="modules-requiring-license-acceptance"></a><span data-ttu-id="292a3-103">Moduły wymagająca akceptacji licencji</span><span class="sxs-lookup"><span data-stu-id="292a3-103">Modules Requiring License Acceptance</span></span>

## <a name="synopsis"></a><span data-ttu-id="292a3-104">STRESZCZENIE</span><span class="sxs-lookup"><span data-stu-id="292a3-104">SYNOPSIS</span></span>
<span data-ttu-id="292a3-105">Działy prawne dla Niektórzy wydawcy modułu wymagają, że klienci muszą jawnie akceptuje przed zainstalowaniem ich modułu z galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="292a3-105">Legal departments for some module publishers require that customers must explicitly accept the license before installing their module from PowerShell Gallery.</span></span> <span data-ttu-id="292a3-106">Jeśli użytkownik instaluje aktualizacji i zapisuje moduł za pomocą PowerShellGet, bezpośrednio lub jako zależność do innego elementu, a ten moduł wymaga od użytkownika zaakceptowania licencji, użytkownik musi wskazywać akceptacji licencji lub kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="292a3-106">If a user installs, updates, or saves a module using PowerShellGet, whether directly or as a dependency for another item, and that module requires the user to agree to a license, the user must indicate they accept the license or the operation fails.</span></span>

## <a name="publish-requirements-for-modules"></a><span data-ttu-id="292a3-107">Publikowanie wymagania dotyczące modułów</span><span class="sxs-lookup"><span data-stu-id="292a3-107">Publish Requirements for Modules</span></span>

<span data-ttu-id="292a3-108">Moduły, które chcesz wymagać od użytkowników zaakceptować licencji powinny spełniać następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="292a3-108">Modules that would like to require users to accept license should fulfill following requirements:</span></span>
    
- <span data-ttu-id="292a3-109">Sekcja PSData manifestu modułu powinna zawierać RequireLicenseAcceptance = $True.</span><span class="sxs-lookup"><span data-stu-id="292a3-109">PSData section of module manifest should include RequireLicenseAcceptance = $True.</span></span>
- <span data-ttu-id="292a3-110">Moduł zawiera pliku license.txt w katalogu głównym.</span><span class="sxs-lookup"><span data-stu-id="292a3-110">Module should contain license.txt file in root directory.</span></span>
- <span data-ttu-id="292a3-111">Moduł manifestu powinien zawierać identyfikatora Uri licencji.</span><span class="sxs-lookup"><span data-stu-id="292a3-111">Module manifest should contain License Uri.</span></span>
- <span data-ttu-id="292a3-112">Powinien zostać opublikowany modułu, z PowerShellGet formacie w wersji 2.0 lub wyższej.</span><span class="sxs-lookup"><span data-stu-id="292a3-112">Module should be published with PowerShellGet Format Version 2.0 and above.</span></span>

## <a name="impact-on-installsaveupdate-module"></a><span data-ttu-id="292a3-113">Wpływ na instalację/Save/aktualizacji — moduł</span><span class="sxs-lookup"><span data-stu-id="292a3-113">Impact on Install/Save/Update-Module</span></span>

- <span data-ttu-id="292a3-114">Polecenia cmdlet Install/Save/aktualizacji będzie obsługiwać nowy parametr — AcceptLicense, które będą zachowywać się tak, jakby użytkownik był wyświetlany licencji.</span><span class="sxs-lookup"><span data-stu-id="292a3-114">Install/Save/Update cmdlets will support a new parameter –AcceptLicense that will behave as though the user saw the license.</span></span>
- <span data-ttu-id="292a3-115">Jeśli nie określono AcceptLicense — RequiredLicenseAcceptance ma wartość PRAWDA, użytkownik będzie wyświetlany license.txt i zostanie wyświetlony monit o: &quot;czy akceptujesz postanowienia licencyjne (Yes/No/YesToAll/NoToAll)&quot;.</span><span class="sxs-lookup"><span data-stu-id="292a3-115">If RequiredLicenseAcceptance is True and –AcceptLicense is not specified, the user will be shown the license.txt, and prompted with: &quot;Do you accept these license terms (Yes/No/YesToAll/NoToAll)&quot;.</span></span>
  - <span data-ttu-id="292a3-116">Jeśli licencja została zaakceptowana.</span><span class="sxs-lookup"><span data-stu-id="292a3-116">If the license is accepted</span></span>
    - <span data-ttu-id="292a3-117">**Moduł zapisywania:** modułu zostaną skopiowane do użytkownika &#39; s systemu</span><span class="sxs-lookup"><span data-stu-id="292a3-117">**Save-Module:** the module will be copied to the user&#39;s system</span></span>
    - <span data-ttu-id="292a3-118">**Moduł instalacji:** modułu zostaną skopiowane do użytkownika &#39; s systemu do prawidłowego folderu (oparte na zakresie)</span><span class="sxs-lookup"><span data-stu-id="292a3-118">**Install-Module:** the module will be copied to the user&#39;s system to the proper folder (based on scope)</span></span>
    - <span data-ttu-id="292a3-119">**Moduł aktualizacji:** moduł zostanie zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="292a3-119">**Update-Module:** the module will be updated.</span></span>
  - <span data-ttu-id="292a3-120">Jeśli licencja została odrzucona.</span><span class="sxs-lookup"><span data-stu-id="292a3-120">If the license is declined.</span></span> 
    - <span data-ttu-id="292a3-121">Operacja zostanie anulowana.</span><span class="sxs-lookup"><span data-stu-id="292a3-121">Operation will be cancelled.</span></span>
- <span data-ttu-id="292a3-122">Wszystkie polecenia cmdlet będzie sprawdzać dostępność metadanych (requireLicenseAcceptance i wersji formatu) z informacją, że wymagana jest akceptacja licencji</span><span class="sxs-lookup"><span data-stu-id="292a3-122">All cmdlets will check for the metadata(requireLicenseAcceptance and Format Version) that says a license acceptance is required</span></span>
  - <span data-ttu-id="292a3-123">Jeśli format wersja klienta jest starsza niż 2.0, operacja będzie i monitowanie użytkownika o aktualizacji klienta.</span><span class="sxs-lookup"><span data-stu-id="292a3-123">If format version of client is older than 2.0, operation will fail and ask the user to update the client.</span></span>
  - <span data-ttu-id="292a3-124">Jeśli moduł został opublikowany w formacie wersji starszych niż 2.0, Flaga requireLicenseAcceptance zostanie zignorowany.</span><span class="sxs-lookup"><span data-stu-id="292a3-124">If module was published with format version older than 2.0, requireLicenseAcceptance flag will be ignored.</span></span>

    
 ## <a name="module-dependencies"></a><span data-ttu-id="292a3-125">Moduł zależności</span><span class="sxs-lookup"><span data-stu-id="292a3-125">Module Dependencies</span></span>
- <span data-ttu-id="292a3-126">Podczas instalacji/Save/aktualizacji będzie wymagane działania, jeśli moduł zależne (czegoś innego zależy od modułu) wymaga akceptacji licencji, a następnie zachowanie akceptacji licencji (powyżej).</span><span class="sxs-lookup"><span data-stu-id="292a3-126">During Install/Save/Update operation, if a dependent module(something else depends on the module) requires license acceptance, then the license acceptance behavior (above) will be required.</span></span>
- <span data-ttu-id="292a3-127">Jeśli wersja modułu znajduje się już w katalogu lokalnego jako zainstalowane na komputerze, możemy ominięcie sprawdzanie licencji.</span><span class="sxs-lookup"><span data-stu-id="292a3-127">If the module version is already listed in the local catalog as being installed on the system, we would bypass the license checking.</span></span>
- <span data-ttu-id="292a3-128">Podczas operacji instalacji/Save/aktualizacji Jeśli modułu zależnego wymaga licencji i akceptacji licencji nie jest wykonywane, operacja będzie i postępuj zgodnie z normalnym procesy dla elementu nie powiodło się do zainstalowania/save/aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="292a3-128">During Install/Save/Update operation, if a dependent module requires a license, and the license acceptance does not occur, the operation will fail and follow normal processes for the item failed to install/save/update.</span></span>

 ## <a name="impact-on--force"></a><span data-ttu-id="292a3-129">Wpływ na - Force</span><span class="sxs-lookup"><span data-stu-id="292a3-129">Impact on -Force</span></span>

<span data-ttu-id="292a3-130">Określanie – Force nie jest wystarczające, aby zaakceptować licencji.</span><span class="sxs-lookup"><span data-stu-id="292a3-130">Specifying –Force is NOT sufficient to accept a license.</span></span> <span data-ttu-id="292a3-131">AcceptLicense — jest wymagany dla uprawnienia do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="292a3-131">–AcceptLicense is required for permission to install.</span></span> <span data-ttu-id="292a3-132">Jeśli – Force jest określony, RequiredLicenseAcceptance ma wartość PRAWDA i AcceptLicense — nie jest określony, operacja zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="292a3-132">If –Force is specified, RequiredLicenseAcceptance is True, and –AcceptLicense is NOT specified, the operation will fail.</span></span>

## <a name="examples"></a><span data-ttu-id="292a3-133">PRZYKŁADY</span><span class="sxs-lookup"><span data-stu-id="292a3-133">EXAMPLES</span></span>

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a><span data-ttu-id="292a3-134">Przykład 1: Aktualizacja modułu manifestu wymagać akceptacji licencji</span><span class="sxs-lookup"><span data-stu-id="292a3-134">Example 1: Update Module Manifest to require license acceptance</span></span>
```PowerShell
PS C:\> Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance

PrivateData = @{

    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable
    
 } # End of PrivateData hashtable
```
<span data-ttu-id="292a3-135">To polecenie aktualizuje plik manifestu i ustawia flagę RequireLicenseAcceptance na wartość true.</span><span class="sxs-lookup"><span data-stu-id="292a3-135">This command updates the manifest file and sets the RequireLicenseAcceptance flag to true.</span></span>
### <a name="example-2-install-module-requiring-license-acceptance"></a><span data-ttu-id="292a3-136">Przykład 2: Instalacja modułu wymaganie akceptacji licencji</span><span class="sxs-lookup"><span data-stu-id="292a3-136">Example 2: Install Module requiring license acceptance</span></span>
```PowerShell
PS C:\> Install-Module -Name ModuleRequireLicenseAcceptance

License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): 

```
<span data-ttu-id="292a3-137">To polecenie przedstawia licencji z pliku license.txt i monituje użytkownika o akceptuje.</span><span class="sxs-lookup"><span data-stu-id="292a3-137">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="292a3-138">Przykład 3: Instalacja modułu wymaganie akceptacji licencji z - AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="292a3-138">Example 3: Install Module requiring license acceptance with -AcceptLicense</span></span>
```PowerShell
PS C:\> Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```
<span data-ttu-id="292a3-139">Moduł jest zainstalowany bez żadnych wiersza, aby zaakceptować licencji.</span><span class="sxs-lookup"><span data-stu-id="292a3-139">Module is installed without any prompt to accept license.</span></span>

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a><span data-ttu-id="292a3-140">Przykład 4: Instalacja modułu wymaganie akceptacji licencji parametru - Force</span><span class="sxs-lookup"><span data-stu-id="292a3-140">Example 4: Install Module requiring license acceptance with -Force</span></span>
```PowerShell
PS C:\> Install-Module -Name ModuleRequireLicenseAcceptance -Force
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="292a3-141">Przykład 5: Instalacja modułu z zależnościami wymagająca akceptacji licencji</span><span class="sxs-lookup"><span data-stu-id="292a3-141">Example 5: Install Module with dependencies requiring license acceptance</span></span>
<span data-ttu-id="292a3-142">Moduł "ModuleWithDependency" zależy od modułu "ModuleRequireLicenseAcceptance".</span><span class="sxs-lookup"><span data-stu-id="292a3-142">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="292a3-143">Użytkownik jest monitowany o zaakceptować licencji.</span><span class="sxs-lookup"><span data-stu-id="292a3-143">User is prompted to Accept License.</span></span>
```PowerShell
PS C:\> Install-Module -Name ModuleWithDependency

License Acceptance
MIT License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): 
```

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="292a3-144">Przykład 6: Instalacja modułu z zależnościami wymaganie akceptacji licencji i - AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="292a3-144">Example 6: Install Module with dependencies requiring license acceptance and -AcceptLicense</span></span>
<span data-ttu-id="292a3-145">Moduł "ModuleWithDependency" zależy od modułu "ModuleRequireLicenseAcceptance".</span><span class="sxs-lookup"><span data-stu-id="292a3-145">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="292a3-146">Użytkownik nie jest monitowany o zaakceptować licencji - AcceptLicense jest określony.</span><span class="sxs-lookup"><span data-stu-id="292a3-146">User is not prompted to accept license as -AcceptLicense is specified.</span></span>
```PowerShell
PS C:\>  Install-Module -Name ModuleWithDependency -AcceptLicense
```
### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a><span data-ttu-id="292a3-147">Przykład 7: Zainstaluj moduł wymagająca akceptacji licencji na kliencie starszych niż PSGetFormatVersion 2.0</span><span class="sxs-lookup"><span data-stu-id="292a3-147">Example 7: Install module requiring license acceptance on a client older than PSGetFormatVersion 2.0</span></span>
```PowerShell
PS C:\windows\system32> Install-Module -Name ModuleRequireLicenseAcceptance

WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.

```
### <a name="example-8-save-module-requiring-license-acceptance"></a><span data-ttu-id="292a3-148">Przykład 8: Zapisz modułu wymagająca akceptacji licencji</span><span class="sxs-lookup"><span data-stu-id="292a3-148">Example 8: Save Module requiring license acceptance</span></span>
```PowerShell
PS C:\> Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved

License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): 
```
<span data-ttu-id="292a3-149">To polecenie przedstawia licencji z pliku license.txt i monituje użytkownika o akceptuje.</span><span class="sxs-lookup"><span data-stu-id="292a3-149">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="292a3-150">Przykład 9: Zapisz wymagająca akceptacji licencji z AcceptLicense — moduł</span><span class="sxs-lookup"><span data-stu-id="292a3-150">Example 9: Save Module requiring license acceptance with -AcceptLicense</span></span>
```PowerShell
PS C:\> Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```
<span data-ttu-id="292a3-151">Moduł jest zapisany bez żadnych wiersza, aby zaakceptować licencji.</span><span class="sxs-lookup"><span data-stu-id="292a3-151">Module is saved without any prompt to accept license.</span></span>

### <a name="example-10-update-module-requiring-license-acceptance"></a><span data-ttu-id="292a3-152">Przykład 10: Akceptacji licencji wymaga aktualizacji modułu</span><span class="sxs-lookup"><span data-stu-id="292a3-152">Example 10: Update Module requiring license acceptance</span></span>
```PowerShell
PS C:\> Update-Module -Name ModuleRequireLicenseAcceptance

License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): 
```
<span data-ttu-id="292a3-153">To polecenie przedstawia licencji z pliku license.txt i monituje użytkownika o akceptuje.</span><span class="sxs-lookup"><span data-stu-id="292a3-153">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="292a3-154">Przykład 11: Moduł aktualizacji wymaganie akceptacji licencji z - AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="292a3-154">Example 11: Update Module requiring license acceptance with -AcceptLicense</span></span>
```PowerShell
PS C:\> Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```
<span data-ttu-id="292a3-155">Moduł jest aktualizowana bez żadnych wiersza, aby zaakceptować licencji.</span><span class="sxs-lookup"><span data-stu-id="292a3-155">Module is updated without any prompt to accept license.</span></span>

## <a name="more-details"></a><span data-ttu-id="292a3-156">więcej informacji</span><span class="sxs-lookup"><span data-stu-id="292a3-156">More details</span></span>
### <a name="require-license-acceptance-for-scriptsscriptscriptrequirelicenseacceptancemd"></a>[<span data-ttu-id="292a3-157">Wymagaj akceptacji licencji dla skryptów</span><span class="sxs-lookup"><span data-stu-id="292a3-157">Require License Acceptance for Scripts</span></span>](../script/script_RequireLicenseAcceptance.md)

### <a name="require-license-acceptance-support-on-powershellgallerypsgallerypsgalleryrequireslicenseacceptancemd"></a>[<span data-ttu-id="292a3-158">Wymagana obsługa akceptacji licencji na PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="292a3-158">Require License Acceptance support on PowerShellGallery</span></span>](../../psgallery/psgallery_requires_license_acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationpsgallerypsgallerydeploytoazureautomationrequirelicenseacceptancemd"></a>[<span data-ttu-id="292a3-159">Wymagaj akceptacji licencji na wdrażanie w automatyzacji Azure</span><span class="sxs-lookup"><span data-stu-id="292a3-159">Require License Acceptance on Deploy to Azure Automation</span></span>](../../psgallery/psgallery_deploy_to_azure_automation_requireLicenseAcceptance.md)
