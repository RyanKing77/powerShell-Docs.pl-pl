---
ms.date: 06/09/2017
schema: 2.0.0
keywords: Środowiska PowerShell
title: RequireLicenseAcceptance
ms.openlocfilehash: d78f8cb7f84869880e9a88a0f0407d18dc5c64cb
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="modules-requiring-license-acceptance"></a>Moduły wymagające akceptacji licencji

## <a name="synopsis"></a>SYNOPSIS
Działy prawne dla Niektórzy wydawcy modułu wymagają, że klienci muszą jawnie akceptuje przed zainstalowaniem ich modułu z galerii programu PowerShell. Jeśli użytkownik instaluje aktualizacji i zapisuje moduł za pomocą PowerShellGet, bezpośrednio lub jako zależność do innego elementu, a ten moduł wymaga od użytkownika zaakceptowania licencji, użytkownik musi wskazywać akceptacji licencji lub kończy się niepowodzeniem.

## <a name="publish-requirements-for-modules"></a>Publikowanie wymagania dotyczące modułów

Moduły, które chcesz wymagać od użytkowników zaakceptować licencji powinny spełniać następujące wymagania:

- Sekcja PSData manifestu modułu powinna zawierać RequireLicenseAcceptance = $True.
- Moduł zawiera pliku license.txt w katalogu głównym.
- Moduł manifestu powinien zawierać identyfikatora Uri licencji.
- Powinien zostać opublikowany modułu, z PowerShellGet formacie w wersji 2.0 lub wyższej.

## <a name="impact-on-installsaveupdate-module"></a>Wpływ na instalację/Save/aktualizacji — moduł

- Polecenia cmdlet Install/Save/aktualizacji będzie obsługiwać nowy parametr — AcceptLicense, które będą zachowywać się tak, jakby użytkownik był wyświetlany licencji.
- Jeśli nie określono AcceptLicense — RequiredLicenseAcceptance ma wartość PRAWDA, użytkownik będzie wyświetlany license.txt i zostanie wyświetlony monit o: &quot;czy akceptujesz postanowienia licencyjne (Yes/No/YesToAll/NoToAll)&quot;.
  - Jeśli licencja została zaakceptowana.
    - **Moduł zapisywania:** modułu zostaną skopiowane do użytkownika&#39;systemu s
    - **Moduł instalacji:** modułu zostaną skopiowane do użytkownika&#39;s systemu do prawidłowego folderu (oparte na zakresie)
    - **Moduł aktualizacji:** moduł zostanie zaktualizowany.
  - Jeśli licencja została odrzucona.
    - Operacja zostanie anulowana.
- Wszystkie polecenia cmdlet będzie sprawdzać dostępność metadanych (requireLicenseAcceptance i wersji formatu) z informacją, że wymagana jest akceptacja licencji
  - Jeśli format wersja klienta jest starsza niż 2.0, operacja będzie i monitowanie użytkownika o aktualizacji klienta.
  - Jeśli moduł został opublikowany w formacie wersji starszych niż 2.0, Flaga requireLicenseAcceptance zostanie zignorowany.


 ## <a name="module-dependencies"></a>Moduł zależności
- Podczas instalacji/Save/aktualizacji będzie wymagane działania, jeśli moduł zależne (czegoś innego zależy od modułu) wymaga akceptacji licencji, a następnie zachowanie akceptacji licencji (powyżej).
- Jeśli wersja modułu znajduje się już w katalogu lokalnego jako zainstalowane na komputerze, możemy ominięcie sprawdzanie licencji.
- Podczas operacji instalacji/Save/aktualizacji Jeśli modułu zależnego wymaga licencji i akceptacji licencji nie jest wykonywane, operacja będzie i postępuj zgodnie z normalnym procesy dla elementu nie powiodło się do zainstalowania/save/aktualizacji.

 ## <a name="impact-on--force"></a>Wpływ na - Force

Określanie – Force nie jest wystarczające, aby zaakceptować licencji. AcceptLicense — jest wymagany dla uprawnienia do zainstalowania. Jeśli – Force jest określony, RequiredLicenseAcceptance ma wartość PRAWDA i AcceptLicense — nie jest określony, operacja zakończy się niepowodzeniem.

## <a name="examples"></a>PRZYKŁADY

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a>Przykład 1: Aktualizacja modułu manifestu wymagać akceptacji licencji
```PowerShell
PS C:\> Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance

PrivateData = @{

    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```
To polecenie aktualizuje plik manifestu i ustawia flagę RequireLicenseAcceptance na wartość true.
### <a name="example-2-install-module-requiring-license-acceptance"></a>Przykład 2: Instalacja modułu wymaganie akceptacji licencji
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
To polecenie przedstawia licencji z pliku license.txt i monituje użytkownika o akceptuje.

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a>Przykład 3: Instalacja modułu wymaganie akceptacji licencji z - AcceptLicense
```PowerShell
PS C:\> Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```
Moduł jest zainstalowany bez żadnych wiersza, aby zaakceptować licencji.

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a>Przykład 4: Instalacja modułu wymaganie akceptacji licencji parametru - Force
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

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a>Przykład 5: Instalacja modułu z zależnościami wymagająca akceptacji licencji
Moduł "ModuleWithDependency" zależy od modułu "ModuleRequireLicenseAcceptance". Użytkownik jest monitowany o zaakceptować licencji.
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

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Przykład 6: Instalacja modułu z zależnościami wymaganie akceptacji licencji i - AcceptLicense
Moduł "ModuleWithDependency" zależy od modułu "ModuleRequireLicenseAcceptance". Użytkownik nie jest monitowany o zaakceptować licencji - AcceptLicense jest określony.
```PowerShell
PS C:\>  Install-Module -Name ModuleWithDependency -AcceptLicense
```
### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a>Przykład 7: Zainstaluj moduł wymagająca akceptacji licencji na kliencie starszych niż PSGetFormatVersion 2.0
```PowerShell
PS C:\windows\system32> Install-Module -Name ModuleRequireLicenseAcceptance

WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.

```
### <a name="example-8-save-module-requiring-license-acceptance"></a>Przykład 8: Zapisz modułu wymagająca akceptacji licencji
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
To polecenie przedstawia licencji z pliku license.txt i monituje użytkownika o akceptuje.

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a>Przykład 9: Zapisz wymagająca akceptacji licencji z AcceptLicense — moduł
```PowerShell
PS C:\> Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```
Moduł jest zapisany bez żadnych wiersza, aby zaakceptować licencji.

### <a name="example-10-update-module-requiring-license-acceptance"></a>Przykład 10: Akceptacji licencji wymaga aktualizacji modułu
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
To polecenie przedstawia licencji z pliku license.txt i monituje użytkownika o akceptuje.

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a>Przykład 11: Moduł aktualizacji wymaganie akceptacji licencji z - AcceptLicense
```PowerShell
PS C:\> Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```
Moduł jest aktualizowana bez żadnych wiersza, aby zaakceptować licencji.

## <a name="more-details"></a>więcej informacji
### <a name="require-license-acceptance-for-scriptsscriptscriptrequirelicenseacceptancemd"></a>[Wymaganie akceptacji licencji na potrzeby skryptów](../script/script_RequireLicenseAcceptance.md)

### <a name="require-license-acceptance-support-on-powershellgallerypsgallerypsgalleryrequireslicenseacceptancemd"></a>[Wymagana obsługa akceptacji licencji na PowerShellGallery](../../psgallery/psgallery_requires_license_acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationpsgallerypsgallerydeploytoazureautomationrequirelicenseacceptancemd"></a>[Wymaganie akceptacji licencji na potrzeby wdrażania w usłudze Azure Automation](../../psgallery/psgallery_deploy_to_azure_automation_requireLicenseAcceptance.md)