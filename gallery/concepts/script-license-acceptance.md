---
ms.date: 06/09/2017
schema: 2.0.0
keywords: Program PowerShell
title: Wymaganie akceptacji licencji dla skryptów
ms.openlocfilehash: e7101eb6a480dd87965b7b9be9d49583042b603f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684213"
---
# <a name="requiring-license-acceptance-for-scripts"></a><span data-ttu-id="4899b-103">Wymaganie akceptacji licencji dla skryptów</span><span class="sxs-lookup"><span data-stu-id="4899b-103">Requiring license acceptance for scripts</span></span>

<span data-ttu-id="4899b-104">Akceptacja licencji nie jest obsługiwana w przypadku skryptów.</span><span class="sxs-lookup"><span data-stu-id="4899b-104">License Acceptance is not supported for scripts.</span></span> <span data-ttu-id="4899b-105">Jednak jest obsługiwany scenariusz, w której skrypt jest zależna od moduł, który wymaga zaakceptowania licencji.</span><span class="sxs-lookup"><span data-stu-id="4899b-105">However, the scenario where a script depends on a module that requires license acceptance is supported.</span></span>

<span data-ttu-id="4899b-106">Skrypt commands(Install-Script/Save-Script/Update-Script) obsługuje nowy parametr - AcceptLicense, który zachowuje się tak, jakby użytkownik był wyświetlany licencji.</span><span class="sxs-lookup"><span data-stu-id="4899b-106">Script commands(Install-Script/Save-Script/Update-Script) support a new parameter -AcceptLicense that behaves as though user saw the license.</span></span> <span data-ttu-id="4899b-107">Jeśli nie określono - AcceptLicense; użytkownik będzie wyświetlane license.txt zależne modułu i zostanie wyświetlony monit, aby zaakceptować licencję.</span><span class="sxs-lookup"><span data-stu-id="4899b-107">If -AcceptLicense is not specified; the user will be shown license.txt for dependent module and prompted to accept the license.</span></span>

## <a name="examples"></a><span data-ttu-id="4899b-108">PRZYKŁADY</span><span class="sxs-lookup"><span data-stu-id="4899b-108">EXAMPLES</span></span>

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="4899b-109">Przykład 1: Skrypt instalacji z zależnościami wymagające akceptacji licencji</span><span class="sxs-lookup"><span data-stu-id="4899b-109">Example 1: Install Script with dependencies requiring license acceptance</span></span>

<span data-ttu-id="4899b-110">Skrypt "ScriptRequireLicenseAcceptance" zależy od modułu "ModuleRequireLicenseAcceptance".</span><span class="sxs-lookup"><span data-stu-id="4899b-110">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="4899b-111">Użytkownik jest monitowany, aby zaakceptować licencję.</span><span class="sxs-lookup"><span data-stu-id="4899b-111">User is prompted to Accept License.</span></span>

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="4899b-112">Przykład 2: Skrypt instalacji z zależnościami wymaganie akceptacji licencji i - AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="4899b-112">Example 2: Install Script with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="4899b-113">Skrypt "ScriptRequireLicenseAcceptance" zależy od modułu "ModuleRequireLicenseAcceptance".</span><span class="sxs-lookup"><span data-stu-id="4899b-113">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="4899b-114">Użytkownik nie jest monitowany o zaakceptowanie licencji, jak określono AcceptLicense —.</span><span class="sxs-lookup"><span data-stu-id="4899b-114">User is not prompted to accept license as -AcceptLicense is specified.</span></span>

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a><span data-ttu-id="4899b-115">Więcej szczegółów</span><span class="sxs-lookup"><span data-stu-id="4899b-115">More details</span></span>

- [<span data-ttu-id="4899b-116">Wymagana jest obsługa akceptacja licencji dla modułów</span><span class="sxs-lookup"><span data-stu-id="4899b-116">Require License Acceptance support for Modules</span></span>](module-license-acceptance.md)
- [<span data-ttu-id="4899b-117">Wymagana jest Obsługa akceptacji licencji na galerii PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="4899b-117">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-packages/packages-that-require-license-acceptance.md)
- [<span data-ttu-id="4899b-118">Wymaganie akceptacji licencji na potrzeby wdrażania w usłudze Azure Automation</span><span class="sxs-lookup"><span data-stu-id="4899b-118">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-packages/deploy-to-azure-automation.md)
