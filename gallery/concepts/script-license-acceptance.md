---
ms.date: 06/09/2017
schema: 2.0.0
keywords: Środowiska PowerShell
title: Wymaganie akceptacji licencji dla skryptów
ms.openlocfilehash: 6374c8c8536dd0c8f27580a5b8895b8db18424f9
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
ms.locfileid: "34048883"
---
# <a name="requiring-license-acceptance-for-scripts"></a>Wymaganie akceptacji licencji dla skryptów

Akceptacja licencji nie jest obsługiwana dla skryptów. Jednak jest obsługiwany scenariusz, w którym skrypt jest zależna od moduł, który wymaga akceptacji licencji.

Skrypt commands(Install-Script/Save-Script/Update-Script) obsługuje nowy parametr - AcceptLicense, który zachowuje się tak, jakby użytkownik był wyświetlany licencji. Jeśli nie określono - AcceptLicense; użytkownik będzie wyświetlany license.txt zależnych modułu i poproszony o zaakceptowanie licencji.

## <a name="examples"></a>PRZYKŁADY

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a>Przykład 1: Skrypt instalacji z zależnościami wymagająca akceptacji licencji

Skrypt "ScriptRequireLicenseAcceptance" zależy od modułu "ModuleRequireLicenseAcceptance". Użytkownik jest monitowany o zaakceptować licencji.

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

Skrypt "ScriptRequireLicenseAcceptance" zależy od modułu "ModuleRequireLicenseAcceptance". Użytkownik nie jest monitowany o zaakceptować licencji - AcceptLicense jest określony.

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a>więcej informacji

- [Wymagana obsługa akceptacji licencji dla modułów](module-license-acceptance.md)
- [Wymagana obsługa akceptacji licencji na PowerShellGallery](../how-to/working-with-items/items-that-require-license-acceptance.md)
- [Wymaganie akceptacji licencji na potrzeby wdrażania w usłudze Azure Automation](../how-to/working-with-items/deploy-to-azure-automation.md)