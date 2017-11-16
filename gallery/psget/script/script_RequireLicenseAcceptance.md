---
ms.date: 2017-06-09
schema: 2.0.0
keywords: "Środowiska PowerShell"
title: RequireLicenseAcceptanceScript
ms.openlocfilehash: 7092fb2e63b9e2b1eca59cd418317631bff8b172
ms.sourcegitcommit: cd66d4f49ea762a31887af2c72d087b219ddbe10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2017
---
# <a name="requiring-license-acceptance-for-scripts"></a><span data-ttu-id="35be8-103">Wymaganie akceptacji licencji dla skryptów</span><span class="sxs-lookup"><span data-stu-id="35be8-103">Requiring License Acceptance for Scripts</span></span>

<span data-ttu-id="35be8-104">Akceptacja licencji nie jest obsługiwana dla skryptów.</span><span class="sxs-lookup"><span data-stu-id="35be8-104">License Acceptance is not supported for scripts.</span></span> <span data-ttu-id="35be8-105">Jednak jest obsługiwany scenariusz, w którym skrypt jest zależna od moduł, który wymaga akceptacji licencji.</span><span class="sxs-lookup"><span data-stu-id="35be8-105">However, the scenario where a script depends on a module that requires license acceptance is supported.</span></span>

<span data-ttu-id="35be8-106">Skrypt commands(Install-Script/Save-Script/Update-Script) obsługuje nowy parametr - AcceptLicense, który zachowuje się tak, jakby użytkownik był wyświetlany licencji.</span><span class="sxs-lookup"><span data-stu-id="35be8-106">Script commands(Install-Script/Save-Script/Update-Script) support a new parameter -AcceptLicense that behaves as though user saw the license.</span></span> <span data-ttu-id="35be8-107">Jeśli nie określono - AcceptLicense; użytkownik będzie wyświetlany license.txt zależnych modułu i poproszony o zaakceptowanie licencji.</span><span class="sxs-lookup"><span data-stu-id="35be8-107">If -AcceptLicense is not specified; the user will be shown license.txt for dependent module and prompted to accept the license.</span></span>

## <a name="examples"></a><span data-ttu-id="35be8-108">PRZYKŁADY</span><span class="sxs-lookup"><span data-stu-id="35be8-108">EXAMPLES</span></span>

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="35be8-109">Przykład 1: Skrypt instalacji z zależnościami wymagająca akceptacji licencji</span><span class="sxs-lookup"><span data-stu-id="35be8-109">Example 1: Install Script with dependencies requiring license acceptance</span></span>
<span data-ttu-id="35be8-110">Skrypt "ScriptRequireLicenseAcceptance" zależy od modułu "ModuleRequireLicenseAcceptance".</span><span class="sxs-lookup"><span data-stu-id="35be8-110">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="35be8-111">Użytkownik jest monitowany o zaakceptować licencji.</span><span class="sxs-lookup"><span data-stu-id="35be8-111">User is prompted to Accept License.</span></span>
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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="35be8-112">Przykład 2: Skrypt instalacji z zależnościami wymaganie akceptacji licencji i - AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="35be8-112">Example 2: Install Script with dependencies requiring license acceptance and -AcceptLicense</span></span>
<span data-ttu-id="35be8-113">Skrypt "ScriptRequireLicenseAcceptance" zależy od modułu "ModuleRequireLicenseAcceptance".</span><span class="sxs-lookup"><span data-stu-id="35be8-113">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="35be8-114">Użytkownik nie jest monitowany o zaakceptować licencji - AcceptLicense jest określony.</span><span class="sxs-lookup"><span data-stu-id="35be8-114">User is not prompted to accept license as -AcceptLicense is specified.</span></span>
```PowerShell
PS C:\> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a><span data-ttu-id="35be8-115">więcej informacji</span><span class="sxs-lookup"><span data-stu-id="35be8-115">More details</span></span>
### <a name="require-license-acceptance-support-for-modulesmodulerequirelicenseacceptancemd"></a>[<span data-ttu-id="35be8-116">Wymagana obsługa akceptacji licencji dla modułów</span><span class="sxs-lookup"><span data-stu-id="35be8-116">Require License Acceptance support for Modules</span></span>](../module/RequireLicenseAcceptance.md)

### <a name="require-license-acceptance-support-on-powershellgallerypsgallerypsgalleryrequireslicenseacceptancemd"></a>[<span data-ttu-id="35be8-117">Wymagana obsługa akceptacji licencji na PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="35be8-117">Require License Acceptance support on PowerShellGallery</span></span>](../../psgallery/psgallery_requires_license_acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationpsgallerypsgallerydeploytoazureautomationrequirelicenseacceptancemd"></a>[<span data-ttu-id="35be8-118">Wymagaj akceptacji licencji na wdrażanie w automatyzacji Azure</span><span class="sxs-lookup"><span data-stu-id="35be8-118">Require License Acceptance on Deploy to Azure Automation</span></span>](../../psgallery/psgallery_deploy_to_azure_automation_requireLicenseAcceptance.md)
