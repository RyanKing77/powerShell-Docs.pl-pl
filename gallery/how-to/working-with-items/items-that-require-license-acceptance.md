---
ms.date: 06/12/2017
contributor: Farehar
ms.topic: conceptual
keywords: galerii programu powershell, psgallery
title: Wymagaj akceptacji licencji
ms.openlocfilehash: 76f16e848e1cd660e062bf8569fb914b32f14934
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="require-license-acceptance"></a><span data-ttu-id="f284f-103">Wymagaj akceptacji licencji</span><span class="sxs-lookup"><span data-stu-id="f284f-103">Require license acceptance</span></span>

<span data-ttu-id="f284f-104">Tekst akceptacji licencji są wyświetlane na stronie Szczegóły elementu dla modułów, które wymagają akceptacji licencji wymaga.</span><span class="sxs-lookup"><span data-stu-id="f284f-104">Require License Acceptance text shows up on item details page for modules that require license acceptance.</span></span> <span data-ttu-id="f284f-105">Licencja dla modułu można wyświetlić, klikając łącze "Wyświetl License.txt".</span><span class="sxs-lookup"><span data-stu-id="f284f-105">License for module can be viewed by clicking on 'View License.txt' link.</span></span>

![Wymagaj akceptacji licencji](../../Images/RequireLicenseAcceptance.png)

<span data-ttu-id="f284f-107">Użytkownicy otrzymują monit, aby zaakceptować licencji podczas instalowania, zapisywanie lub aktualizowanie modułu przy użyciu PowerShellGet lub podczas wdrażania usługi Automatyzacja Azure.</span><span class="sxs-lookup"><span data-stu-id="f284f-107">Users will be prompted to accept the license when installing, saving or updating the module through PowerShellGet or when deploying to Azure Automation.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="f284f-108">Wymaganie akceptacji licencji na potrzeby wdrażania w usłudze Azure Automation</span><span class="sxs-lookup"><span data-stu-id="f284f-108">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="f284f-109">Moduł podczas wdrażania usługi Automatyzacja Azure wymaga akceptacji licencji, interfejsu użytkownika portalu wyświetli informacją o tym zastrzeżenie "akceptacji licencji wymaga tego modułu.</span><span class="sxs-lookup"><span data-stu-id="f284f-109">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="f284f-110">Klikając przycisk OK, akceptujesz postanowienia licencyjne. "</span><span class="sxs-lookup"><span data-stu-id="f284f-110">By clicking OK, you are accepting license terms.'</span></span>

![Wdrażanie na platformie Azure akceptacji licencji wymaga automatyzacji](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="f284f-112">więcej informacji</span><span class="sxs-lookup"><span data-stu-id="f284f-112">More details</span></span>

<span data-ttu-id="f284f-113">[Wymagaj akceptacji licencji w PowerShellGet](../../concepts/module-license-acceptance.md)
[witryny sieci Web usługi Automatyzacja Azure](/azure/automation)</span><span class="sxs-lookup"><span data-stu-id="f284f-113">[Require License Acceptance in PowerShellGet](../../concepts/module-license-acceptance.md)
[Azure Automation website](/azure/automation)</span></span>