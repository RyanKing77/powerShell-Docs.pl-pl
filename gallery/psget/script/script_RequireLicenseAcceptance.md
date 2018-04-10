---
ms.date: 06/09/2017
schema: 2.0.0
keywords: Środowiska PowerShell
title: RequireLicenseAcceptanceScript
ms.openlocfilehash: 4a2dc39c2b6c380fb4ca94f9fd071ed9cdb35049
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="requiring-license-acceptance-for-scripts"></a><span data-ttu-id="457fe-103">Wymaganie akceptacji licencji dla skryptów</span><span class="sxs-lookup"><span data-stu-id="457fe-103">Requiring License Acceptance for Scripts</span></span>

<span data-ttu-id="457fe-104">Akceptacja licencji nie jest obsługiwana dla skryptów.</span><span class="sxs-lookup"><span data-stu-id="457fe-104">License Acceptance is not supported for scripts.</span></span> <span data-ttu-id="457fe-105">Jednak jest obsługiwany scenariusz, w którym skrypt jest zależna od moduł, który wymaga akceptacji licencji.</span><span class="sxs-lookup"><span data-stu-id="457fe-105">However, the scenario where a script depends on a module that requires license acceptance is supported.</span></span>

<span data-ttu-id="457fe-106">Skrypt commands(Install-Script/Save-Script/Update-Script) obsługuje nowy parametr - AcceptLicense, który zachowuje się tak, jakby użytkownik był wyświetlany licencji.</span><span class="sxs-lookup"><span data-stu-id="457fe-106">Script commands(Install-Script/Save-Script/Update-Script) support a new parameter -AcceptLicense that behaves as though user saw the license.</span></span> <span data-ttu-id="457fe-107">Jeśli nie określono - AcceptLicense; użytkownik będzie wyświetlany license.txt zależnych modułu i poproszony o zaakceptowanie licencji.</span><span class="sxs-lookup"><span data-stu-id="457fe-107">If -AcceptLicense is not specified; the user will be shown license.txt for dependent module and prompted to accept the license.</span></span>

## <a name="examples"></a><span data-ttu-id="457fe-108">PRZYKŁADY</span><span class="sxs-lookup"><span data-stu-id="457fe-108">EXAMPLES</span></span>

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="457fe-109">Przykład 1: Skrypt instalacji z zależnościami wymagająca akceptacji licencji</span><span class="sxs-lookup"><span data-stu-id="457fe-109">Example 1: Install Script with dependencies requiring license acceptance</span></span>
<span data-ttu-id="457fe-110">Skrypt "ScriptRequireLicenseAcceptance" zależy od modułu "ModuleRequireLicenseAcceptance".</span><span class="sxs-lookup"><span data-stu-id="457fe-110">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="457fe-111">Użytkownik jest monitowany o zaakceptować licencji.</span><span class="sxs-lookup"><span data-stu-id="457fe-111">User is prompted to Accept License.</span></span>
```PowerShell
PS C:\> Install-Script -Name ScriptRequireLicenseAcceptance

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="457fe-112">Przykład 2: Skrypt instalacji z zależnościami wymaganie akceptacji licencji i - AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="457fe-112">Example 2: Install Script with dependencies requiring license acceptance and -AcceptLicense</span></span>
<span data-ttu-id="457fe-113">Skrypt "ScriptRequireLicenseAcceptance" zależy od modułu "ModuleRequireLicenseAcceptance".</span><span class="sxs-lookup"><span data-stu-id="457fe-113">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="457fe-114">Użytkownik nie jest monitowany o zaakceptować licencji - AcceptLicense jest określony.</span><span class="sxs-lookup"><span data-stu-id="457fe-114">User is not prompted to accept license as -AcceptLicense is specified.</span></span>
```PowerShell
PS C:\> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a><span data-ttu-id="457fe-115">więcej informacji</span><span class="sxs-lookup"><span data-stu-id="457fe-115">More details</span></span>
### <a name="require-license-acceptance-support-for-modulesmodulerequirelicenseacceptancemd"></a>[<span data-ttu-id="457fe-116">Wymagana obsługa akceptacji licencji dla modułów</span><span class="sxs-lookup"><span data-stu-id="457fe-116">Require License Acceptance support for Modules</span></span>](../module/RequireLicenseAcceptance.md)

### <a name="require-license-acceptance-support-on-powershellgallerypsgallerypsgalleryrequireslicenseacceptancemd"></a>[<span data-ttu-id="457fe-117">Wymagana obsługa akceptacji licencji na PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="457fe-117">Require License Acceptance support on PowerShellGallery</span></span>](../../psgallery/psgallery_requires_license_acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationpsgallerypsgallerydeploytoazureautomationrequirelicenseacceptancemd"></a>[<span data-ttu-id="457fe-118">Wymaganie akceptacji licencji na potrzeby wdrażania w usłudze Azure Automation</span><span class="sxs-lookup"><span data-stu-id="457fe-118">Require License Acceptance on Deploy to Azure Automation</span></span>](../../psgallery/psgallery_deploy_to_azure_automation_requireLicenseAcceptance.md)