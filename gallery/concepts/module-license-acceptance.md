---
ms.date: 06/09/2017
schema: 2.0.0
keywords: Program PowerShell
title: Moduły wymagające akceptacji licencji
ms.openlocfilehash: 93f92f6e83bcf18a40c3d89eb39a154e16ca5063
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893114"
---
# <a name="modules-requiring-license-acceptance"></a><span data-ttu-id="61084-103">Moduły wymagające akceptacji licencji</span><span class="sxs-lookup"><span data-stu-id="61084-103">Modules Requiring License Acceptance</span></span>

## <a name="synopsis"></a><span data-ttu-id="61084-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="61084-104">SYNOPSIS</span></span>

<span data-ttu-id="61084-105">Działy prawne dla Niektórzy wydawcy modułu wymagają, że klienci muszą jawnie akceptuje przed zainstalowaniem ich modułu z galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="61084-105">Legal departments for some module publishers require that customers must explicitly accept the license before installing their module from PowerShell Gallery.</span></span> <span data-ttu-id="61084-106">Jeśli użytkownik instaluje, aktualizacji lub zapisuje moduł za pomocą modułu PowerShellGet, bezpośrednio lub jako zależność dla innego elementu, a ten moduł wymaga od użytkownika zaakceptować licencję, użytkownik musi wskazywać akceptacji licencji lub kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="61084-106">If a user installs, updates, or saves a module using PowerShellGet, whether directly or as a dependency for another item, and that module requires the user to agree to a license, the user must indicate they accept the license or the operation fails.</span></span>

## <a name="publish-requirements-for-modules"></a><span data-ttu-id="61084-107">Publikowanie wymagania dotyczące modułów</span><span class="sxs-lookup"><span data-stu-id="61084-107">Publish Requirements for Modules</span></span>

<span data-ttu-id="61084-108">Moduły, które chcesz wymagać od użytkowników zaakceptować licencję powinny spełniać następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="61084-108">Modules that would like to require users to accept license should fulfill following requirements:</span></span>

- <span data-ttu-id="61084-109">PSData części manifestu modułu powinna zawierać RequireLicenseAcceptance = $True.</span><span class="sxs-lookup"><span data-stu-id="61084-109">PSData section of module manifest should include RequireLicenseAcceptance = $True.</span></span>
- <span data-ttu-id="61084-110">Moduł powinien zawierać pliku license.txt w katalogu głównym.</span><span class="sxs-lookup"><span data-stu-id="61084-110">Module should contain license.txt file in root directory.</span></span>
- <span data-ttu-id="61084-111">Manifest modułu powinna zawierać identyfikator Uri licencji.</span><span class="sxs-lookup"><span data-stu-id="61084-111">Module manifest should contain License Uri.</span></span>
- <span data-ttu-id="61084-112">Moduł powinny być publikowane z formatu PowerShellGet w wersji 2.0 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="61084-112">Module should be published with PowerShellGet Format Version 2.0 and above.</span></span>

## <a name="impact-on-installsaveupdate-module"></a><span data-ttu-id="61084-113">Wpływu na instalacji/Save/Update-Module</span><span class="sxs-lookup"><span data-stu-id="61084-113">Impact on Install/Save/Update-Module</span></span>

- <span data-ttu-id="61084-114">Polecenia cmdlet instalacji/Save/aktualizacji będzie obsługiwać nowy parametr — AcceptLicense, które będą zachowywać się, jak gdyby użytkownik był wyświetlany licencji.</span><span class="sxs-lookup"><span data-stu-id="61084-114">Install/Save/Update cmdlets will support a new parameter –AcceptLicense that will behave as though the user saw the license.</span></span>
- <span data-ttu-id="61084-115">Jeśli nie określono AcceptLicense — RequiredLicenseAcceptance ma wartość True, użytkownik będzie wyświetlany w pliku license.txt i zostanie wyświetlony monit o: &quot;czy akceptujesz postanowienia licencyjne (tak/nie/YesToAll/NoToAll)&quot;.</span><span class="sxs-lookup"><span data-stu-id="61084-115">If RequiredLicenseAcceptance is True and –AcceptLicense is not specified, the user will be shown the license.txt, and prompted with: &quot;Do you accept these license terms (Yes/No/YesToAll/NoToAll)&quot;.</span></span>
  - <span data-ttu-id="61084-116">Jeśli licencja zostanie zaakceptowana</span><span class="sxs-lookup"><span data-stu-id="61084-116">If the license is accepted</span></span>
    - <span data-ttu-id="61084-117">**Save-Module:** moduł zostanie skopiowany do użytkownika&#39;s system</span><span class="sxs-lookup"><span data-stu-id="61084-117">**Save-Module:** the module will be copied to the user&#39;s system</span></span>
    - <span data-ttu-id="61084-118">**Install-Module:** moduł zostanie skopiowany do użytkownika&#39;system s do odpowiedniego folderu (na podstawie zakresu)</span><span class="sxs-lookup"><span data-stu-id="61084-118">**Install-Module:** the module will be copied to the user&#39;s system to the proper folder (based on scope)</span></span>
    - <span data-ttu-id="61084-119">**Update-Module:** moduł zostanie zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="61084-119">**Update-Module:** the module will be updated.</span></span>
  - <span data-ttu-id="61084-120">Jeśli licencja została odrzucona.</span><span class="sxs-lookup"><span data-stu-id="61084-120">If the license is declined.</span></span>
    - <span data-ttu-id="61084-121">Operacja zostanie anulowana.</span><span class="sxs-lookup"><span data-stu-id="61084-121">Operation will be cancelled.</span></span>
    - <span data-ttu-id="61084-122">Wszystkie polecenia cmdlet będzie szukać metadanych (requireLicenseAcceptance i wersja formatu), stwierdzający, że wymagana jest akceptacja licencji</span><span class="sxs-lookup"><span data-stu-id="61084-122">All cmdlets will check for the metadata(requireLicenseAcceptance and Format Version) that says a license acceptance is required</span></span>
    - <span data-ttu-id="61084-123">Jeśli format wersja klienta jest starsza niż w wersji 2.0, operacja się nie powieść i poproś użytkownika, aby zaktualizować klienta.</span><span class="sxs-lookup"><span data-stu-id="61084-123">If format version of client is older than 2.0, operation will fail and ask the user to update the client.</span></span>
    - <span data-ttu-id="61084-124">Jeśli moduł został opublikowany za pomocą wersji formatu starsze niż w wersji 2.0, Flaga requireLicenseAcceptance zostanie zignorowana.</span><span class="sxs-lookup"><span data-stu-id="61084-124">If module was published with format version older than 2.0, requireLicenseAcceptance flag will be ignored.</span></span>

## <a name="module-dependencies"></a><span data-ttu-id="61084-125">Zależności modułów</span><span class="sxs-lookup"><span data-stu-id="61084-125">Module Dependencies</span></span>

- <span data-ttu-id="61084-126">Podczas instalacji/Save/aktualizacji operacji, jeśli moduł zależne (coś innego zależy od modułu) wymaga zaakceptowania licencji, a następnie zachowanie akceptacja licencji (powyżej) będą wymagane.</span><span class="sxs-lookup"><span data-stu-id="61084-126">During Install/Save/Update operation, if a dependent module(something else depends on the module) requires license acceptance, then the license acceptance behavior (above) will be required.</span></span>
- <span data-ttu-id="61084-127">Wersja modułu już znajduje się w katalogu lokalnym jako zainstalowane w systemie, czy możemy pominąć, sprawdzanie licencji.</span><span class="sxs-lookup"><span data-stu-id="61084-127">If the module version is already listed in the local catalog as being installed on the system, we would bypass the license checking.</span></span>
- <span data-ttu-id="61084-128">Podczas operacji instalacji/Save/aktualizacji Jeśli moduł zależne muszą mieć licencję i akceptacja licencji nie jest wykonywane, operacja będzie się nie powieść i postępuj zgodnie z normalnym procesów dla elementu instalacji/save/aktualizacji nie udało się.</span><span class="sxs-lookup"><span data-stu-id="61084-128">During Install/Save/Update operation, if a dependent module requires a license, and the license acceptance does not occur, the operation will fail and follow normal processes for the item failed to install/save/update.</span></span>

## <a name="impact-on--force"></a><span data-ttu-id="61084-129">Wpływ na - Force</span><span class="sxs-lookup"><span data-stu-id="61084-129">Impact on -Force</span></span>

<span data-ttu-id="61084-130">Określanie `–Force` nie jest wystarczające, aby zaakceptować licencję.</span><span class="sxs-lookup"><span data-stu-id="61084-130">Specifying `–Force` is NOT sufficient to accept a license.</span></span> <span data-ttu-id="61084-131">`–AcceptLicense` dla uprawnienia do instalacji jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="61084-131">`–AcceptLicense` is required for permission to install.</span></span> <span data-ttu-id="61084-132">Jeśli `–Force` określono RequiredLicenseAcceptance ma wartość PRAWDA, a `–AcceptLicense` nie zostanie określony, operacja zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="61084-132">If `–Force` is specified, RequiredLicenseAcceptance is True, and `–AcceptLicense` is NOT specified, the operation will fail.</span></span>

## <a name="examples"></a><span data-ttu-id="61084-133">PRZYKŁADY</span><span class="sxs-lookup"><span data-stu-id="61084-133">EXAMPLES</span></span>

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a><span data-ttu-id="61084-134">Przykład 1: Manifestu modułu aktualizacji za wymaganie akceptacji licencji</span><span class="sxs-lookup"><span data-stu-id="61084-134">Example 1: Update Module Manifest to require license acceptance</span></span>

```powershell
Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance -PrivateData @{
    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

<span data-ttu-id="61084-135">To polecenie aktualizuje plik manifestu i ustawia flagę RequireLicenseAcceptance na wartość true.</span><span class="sxs-lookup"><span data-stu-id="61084-135">This command updates the manifest file and sets the RequireLicenseAcceptance flag to true.</span></span>

### <a name="example-2-install-module-requiring-license-acceptance"></a><span data-ttu-id="61084-136">Przykład 2: Instalacja modułu wymaganie akceptacji licencji</span><span class="sxs-lookup"><span data-stu-id="61084-136">Example 2: Install Module requiring license acceptance</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```output
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

<span data-ttu-id="61084-137">To polecenie przedstawia licencji z pliku license.txt i wyświetla monit o zaakceptowanie licencji.</span><span class="sxs-lookup"><span data-stu-id="61084-137">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="61084-138">Przykład 3: Instalacja modułu wymaganie akceptacji licencji przy użyciu - AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="61084-138">Example 3: Install Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="61084-139">Moduł jest zainstalowany bez dowolnego wiersza, aby zaakceptować licencję.</span><span class="sxs-lookup"><span data-stu-id="61084-139">Module is installed without any prompt to accept license.</span></span>

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a><span data-ttu-id="61084-140">Przykład 4: Instalacja modułu wymaganie akceptacji licencji parametru - Force</span><span class="sxs-lookup"><span data-stu-id="61084-140">Example 4: Install Module requiring license acceptance with -Force</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -Force
```

```output
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="61084-141">Przykład 5: Instalacja modułu z zależnościami wymagające akceptacji licencji</span><span class="sxs-lookup"><span data-stu-id="61084-141">Example 5: Install Module with dependencies requiring license acceptance</span></span>

<span data-ttu-id="61084-142">Moduł "ModuleWithDependency" zależy od modułu "ModuleRequireLicenseAcceptance".</span><span class="sxs-lookup"><span data-stu-id="61084-142">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="61084-143">Użytkownik jest monitowany, aby zaakceptować licencję.</span><span class="sxs-lookup"><span data-stu-id="61084-143">User is prompted to Accept License.</span></span>

```powershell
Install-Module -Name ModuleWithDependency
```

```output
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

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="61084-144">Przykład 6: Instalacja modułu z zależnościami wymaganie akceptacji licencji i - AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="61084-144">Example 6: Install Module with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="61084-145">Moduł "ModuleWithDependency" zależy od modułu "ModuleRequireLicenseAcceptance".</span><span class="sxs-lookup"><span data-stu-id="61084-145">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="61084-146">Użytkownik nie jest monitowany o zaakceptowanie licencji, jak określono AcceptLicense —.</span><span class="sxs-lookup"><span data-stu-id="61084-146">User is not prompted to accept license as -AcceptLicense is specified.</span></span>

```powershell
Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a><span data-ttu-id="61084-147">Przykład 7: Zainstaluj moduł wymagające akceptacji licencji na komputerze klienckim, które są starsze niż PSGetFormatVersion w wersji 2.0</span><span class="sxs-lookup"><span data-stu-id="61084-147">Example 7: Install module requiring license acceptance on a client older than PSGetFormatVersion 2.0</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```output
WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.
```

### <a name="example-8-save-module-requiring-license-acceptance"></a><span data-ttu-id="61084-148">Przykład 8: Zapisywanie modułu wymagające akceptacji licencji</span><span class="sxs-lookup"><span data-stu-id="61084-148">Example 8: Save Module requiring license acceptance</span></span>

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved
```

```output
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

<span data-ttu-id="61084-149">To polecenie przedstawia licencji z pliku license.txt i wyświetla monit o zaakceptowanie licencji.</span><span class="sxs-lookup"><span data-stu-id="61084-149">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="61084-150">Przykład 9: Zapisz wymagające akceptacji licencji z AcceptLicense — moduł</span><span class="sxs-lookup"><span data-stu-id="61084-150">Example 9: Save Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

<span data-ttu-id="61084-151">Moduł są zapisywane bez dowolnego wiersza, aby zaakceptować licencję.</span><span class="sxs-lookup"><span data-stu-id="61084-151">Module is saved without any prompt to accept license.</span></span>

### <a name="example-10-update-module-requiring-license-acceptance"></a><span data-ttu-id="61084-152">Przykład 10: Aktualizacja modułu wymaganie akceptacji licencji</span><span class="sxs-lookup"><span data-stu-id="61084-152">Example 10: Update Module requiring license acceptance</span></span>

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance
```

```output
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

<span data-ttu-id="61084-153">To polecenie przedstawia licencji z pliku license.txt i wyświetla monit o zaakceptowanie licencji.</span><span class="sxs-lookup"><span data-stu-id="61084-153">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="61084-154">Przykład 11: Aktualizacja modułu wymaganie akceptacji licencji przy użyciu - AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="61084-154">Example 11: Update Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="61084-155">Moduł jest aktualizowany bez dowolnego wiersza, aby zaakceptować licencję.</span><span class="sxs-lookup"><span data-stu-id="61084-155">Module is updated without any prompt to accept license.</span></span>

## <a name="more-details"></a><span data-ttu-id="61084-156">Więcej szczegółów</span><span class="sxs-lookup"><span data-stu-id="61084-156">More details</span></span>

[<span data-ttu-id="61084-157">Wymaganie akceptacji licencji na potrzeby skryptów</span><span class="sxs-lookup"><span data-stu-id="61084-157">Require License Acceptance for Scripts</span></span>](./script-license-acceptance.md)

[<span data-ttu-id="61084-158">Wymagana jest Obsługa akceptacji licencji na galerii PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="61084-158">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-items/items-that-require-license-acceptance.md)

[<span data-ttu-id="61084-159">Wymaganie akceptacji licencji na potrzeby wdrażania w usłudze Azure Automation</span><span class="sxs-lookup"><span data-stu-id="61084-159">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-items/deploy-to-azure-automation.md)