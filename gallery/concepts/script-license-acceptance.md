---
ms.date: 06/09/2017
schema: 2.0.0
keywords: Program PowerShell
title: Wymaganie akceptacji licencji dla skryptów
ms.openlocfilehash: e7101eb6a480dd87965b7b9be9d49583042b603f
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002586"
---
# <a name="requiring-license-acceptance-for-scripts"></a>Wymaganie akceptacji licencji dla skryptów

Akceptacja licencji nie jest obsługiwana w przypadku skryptów. Jednak jest obsługiwany scenariusz, w której skrypt jest zależna od moduł, który wymaga zaakceptowania licencji.

Skrypt commands(Install-Script/Save-Script/Update-Script) obsługuje nowy parametr - AcceptLicense, który zachowuje się tak, jakby użytkownik był wyświetlany licencji. Jeśli nie określono - AcceptLicense; użytkownik będzie wyświetlane license.txt zależne modułu i zostanie wyświetlony monit, aby zaakceptować licencję.

## <a name="examples"></a>PRZYKŁADY

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a>Przykład 1: Skrypt instalacji z zależnościami wymagające akceptacji licencji

Skrypt "ScriptRequireLicenseAcceptance" zależy od modułu "ModuleRequireLicenseAcceptance". Użytkownik jest monitowany, aby zaakceptować licencję.

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Przykład 2: Skrypt instalacji z zależnościami wymaganie akceptacji licencji i - AcceptLicense

Skrypt "ScriptRequireLicenseAcceptance" zależy od modułu "ModuleRequireLicenseAcceptance". Użytkownik nie jest monitowany o zaakceptowanie licencji, jak określono AcceptLicense —.

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a>Więcej szczegółów

- [Wymagana jest obsługa akceptacja licencji dla modułów](module-license-acceptance.md)
- [Wymagana jest Obsługa akceptacji licencji na galerii PowerShellGallery](../how-to/working-with-packages/packages-that-require-license-acceptance.md)
- [Wymaganie akceptacji licencji na potrzeby wdrażania w usłudze Azure Automation](../how-to/working-with-packages/deploy-to-azure-automation.md)
