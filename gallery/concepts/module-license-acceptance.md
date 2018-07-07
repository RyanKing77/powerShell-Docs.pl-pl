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
# <a name="modules-requiring-license-acceptance"></a>Moduły wymagające akceptacji licencji

## <a name="synopsis"></a>SYNOPSIS

Działy prawne dla Niektórzy wydawcy modułu wymagają, że klienci muszą jawnie akceptuje przed zainstalowaniem ich modułu z galerii programu PowerShell. Jeśli użytkownik instaluje, aktualizacji lub zapisuje moduł za pomocą modułu PowerShellGet, bezpośrednio lub jako zależność dla innego elementu, a ten moduł wymaga od użytkownika zaakceptować licencję, użytkownik musi wskazywać akceptacji licencji lub kończy się niepowodzeniem.

## <a name="publish-requirements-for-modules"></a>Publikowanie wymagania dotyczące modułów

Moduły, które chcesz wymagać od użytkowników zaakceptować licencję powinny spełniać następujące wymagania:

- PSData części manifestu modułu powinna zawierać RequireLicenseAcceptance = $True.
- Moduł powinien zawierać pliku license.txt w katalogu głównym.
- Manifest modułu powinna zawierać identyfikator Uri licencji.
- Moduł powinny być publikowane z formatu PowerShellGet w wersji 2.0 lub nowszym.

## <a name="impact-on-installsaveupdate-module"></a>Wpływu na instalacji/Save/Update-Module

- Polecenia cmdlet instalacji/Save/aktualizacji będzie obsługiwać nowy parametr — AcceptLicense, które będą zachowywać się, jak gdyby użytkownik był wyświetlany licencji.
- Jeśli nie określono AcceptLicense — RequiredLicenseAcceptance ma wartość True, użytkownik będzie wyświetlany w pliku license.txt i zostanie wyświetlony monit o: &quot;czy akceptujesz postanowienia licencyjne (tak/nie/YesToAll/NoToAll)&quot;.
  - Jeśli licencja zostanie zaakceptowana
    - **Save-Module:** moduł zostanie skopiowany do użytkownika&#39;s system
    - **Install-Module:** moduł zostanie skopiowany do użytkownika&#39;system s do odpowiedniego folderu (na podstawie zakresu)
    - **Update-Module:** moduł zostanie zaktualizowany.
  - Jeśli licencja została odrzucona.
    - Operacja zostanie anulowana.
    - Wszystkie polecenia cmdlet będzie szukać metadanych (requireLicenseAcceptance i wersja formatu), stwierdzający, że wymagana jest akceptacja licencji
    - Jeśli format wersja klienta jest starsza niż w wersji 2.0, operacja się nie powieść i poproś użytkownika, aby zaktualizować klienta.
    - Jeśli moduł został opublikowany za pomocą wersji formatu starsze niż w wersji 2.0, Flaga requireLicenseAcceptance zostanie zignorowana.

## <a name="module-dependencies"></a>Zależności modułów

- Podczas instalacji/Save/aktualizacji operacji, jeśli moduł zależne (coś innego zależy od modułu) wymaga zaakceptowania licencji, a następnie zachowanie akceptacja licencji (powyżej) będą wymagane.
- Wersja modułu już znajduje się w katalogu lokalnym jako zainstalowane w systemie, czy możemy pominąć, sprawdzanie licencji.
- Podczas operacji instalacji/Save/aktualizacji Jeśli moduł zależne muszą mieć licencję i akceptacja licencji nie jest wykonywane, operacja będzie się nie powieść i postępuj zgodnie z normalnym procesów dla elementu instalacji/save/aktualizacji nie udało się.

## <a name="impact-on--force"></a>Wpływ na - Force

Określanie `–Force` nie jest wystarczające, aby zaakceptować licencję. `–AcceptLicense` dla uprawnienia do instalacji jest wymagana. Jeśli `–Force` określono RequiredLicenseAcceptance ma wartość PRAWDA, a `–AcceptLicense` nie zostanie określony, operacja zakończy się niepowodzeniem.

## <a name="examples"></a>PRZYKŁADY

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a>Przykład 1: Manifestu modułu aktualizacji za wymaganie akceptacji licencji

```powershell
Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance -PrivateData @{
    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

To polecenie aktualizuje plik manifestu i ustawia flagę RequireLicenseAcceptance na wartość true.

### <a name="example-2-install-module-requiring-license-acceptance"></a>Przykład 2: Instalacja modułu wymaganie akceptacji licencji

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

To polecenie przedstawia licencji z pliku license.txt i wyświetla monit o zaakceptowanie licencji.

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a>Przykład 3: Instalacja modułu wymaganie akceptacji licencji przy użyciu - AcceptLicense

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

Moduł jest zainstalowany bez dowolnego wiersza, aby zaakceptować licencję.

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a>Przykład 4: Instalacja modułu wymaganie akceptacji licencji parametru - Force

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

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a>Przykład 5: Instalacja modułu z zależnościami wymagające akceptacji licencji

Moduł "ModuleWithDependency" zależy od modułu "ModuleRequireLicenseAcceptance". Użytkownik jest monitowany, aby zaakceptować licencję.

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

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Przykład 6: Instalacja modułu z zależnościami wymaganie akceptacji licencji i - AcceptLicense

Moduł "ModuleWithDependency" zależy od modułu "ModuleRequireLicenseAcceptance". Użytkownik nie jest monitowany o zaakceptowanie licencji, jak określono AcceptLicense —.

```powershell
Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a>Przykład 7: Zainstaluj moduł wymagające akceptacji licencji na komputerze klienckim, które są starsze niż PSGetFormatVersion w wersji 2.0

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```output
WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.
```

### <a name="example-8-save-module-requiring-license-acceptance"></a>Przykład 8: Zapisywanie modułu wymagające akceptacji licencji

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

To polecenie przedstawia licencji z pliku license.txt i wyświetla monit o zaakceptowanie licencji.

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a>Przykład 9: Zapisz wymagające akceptacji licencji z AcceptLicense — moduł

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

Moduł są zapisywane bez dowolnego wiersza, aby zaakceptować licencję.

### <a name="example-10-update-module-requiring-license-acceptance"></a>Przykład 10: Aktualizacja modułu wymaganie akceptacji licencji

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

To polecenie przedstawia licencji z pliku license.txt i wyświetla monit o zaakceptowanie licencji.

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a>Przykład 11: Aktualizacja modułu wymaganie akceptacji licencji przy użyciu - AcceptLicense

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

Moduł jest aktualizowany bez dowolnego wiersza, aby zaakceptować licencję.

## <a name="more-details"></a>Więcej szczegółów

[Wymaganie akceptacji licencji na potrzeby skryptów](./script-license-acceptance.md)

[Wymagana jest Obsługa akceptacji licencji na galerii PowerShellGallery](../how-to/working-with-items/items-that-require-license-acceptance.md)

[Wymaganie akceptacji licencji na potrzeby wdrażania w usłudze Azure Automation](../how-to/working-with-items/deploy-to-azure-automation.md)