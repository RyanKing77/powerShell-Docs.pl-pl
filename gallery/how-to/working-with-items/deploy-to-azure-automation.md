---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, programu powershell, polecenia cmdlet, psgallery
title: Wdrażanie w usłudze Azure Automation
ms.openlocfilehash: ced67809387a85e089259edf6b091d68e58ba6a7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="deploy-to-azure-automation"></a><span data-ttu-id="b360b-103">Wdrażanie w usłudze Azure Automation</span><span class="sxs-lookup"><span data-stu-id="b360b-103">Deploy to Azure Automation</span></span>

<span data-ttu-id="b360b-104">Wdróż do przycisku usługi Automatyzacja Azure na stronie szczegółów wdroży element z galerii programu PowerShell do automatyzacji Azure.</span><span class="sxs-lookup"><span data-stu-id="b360b-104">The Deploy to Azure Automation button on the item details page will deploy the item from the PowerShell Gallery to Azure Automation.</span></span>

![Wdrażanie na przycisku usługi Automatyzacja Azure](../../Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="b360b-106">Po kliknięciu, nastąpi przekierowanie do portalu zarządzania Azure, której użytkownik loguje się przy użyciu poświadczeń konta platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="b360b-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="b360b-107">Jeśli element zawiera zależności, wszystkie zależności zostanie wdrożone do automatyzacji Azure również.</span><span class="sxs-lookup"><span data-stu-id="b360b-107">If the item includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

> [!WARNING]
> <span data-ttu-id="b360b-108">Jeśli tego samego elementu i wersji już istnieje na koncie automatyzacji, jej ponownym wdrożeniem z galerii programu PowerShell spowoduje zastąpienie elementu na Twoim koncie automatyzacji.</span><span class="sxs-lookup"><span data-stu-id="b360b-108">If the same item and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the item in your Automation account.</span></span>

<span data-ttu-id="b360b-109">Jeśli podczas wdrażania modułu, pojawi się w sekcji modułów w automatyzacji Azure.</span><span class="sxs-lookup"><span data-stu-id="b360b-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="b360b-110">Jeśli skrypt zostanie wdrożony, będą wyświetlane w sekcji elementów Runbook usługi Automatyzacja Azure.</span><span class="sxs-lookup"><span data-stu-id="b360b-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="b360b-111">Wdrażanie na przycisku automatyzacji Azure można wyłączyć, dodając AzureAutomationNotSupported tag do metadanych elementu.</span><span class="sxs-lookup"><span data-stu-id="b360b-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the item metadata.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="b360b-112">Wymaganie akceptacji licencji na potrzeby wdrażania w usłudze Azure Automation</span><span class="sxs-lookup"><span data-stu-id="b360b-112">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="b360b-113">Moduł podczas wdrażania usługi Automatyzacja Azure wymaga akceptacji licencji, interfejsu użytkownika portalu wyświetli informacją o tym zastrzeżenie "akceptacji licencji wymaga tego modułu.</span><span class="sxs-lookup"><span data-stu-id="b360b-113">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="b360b-114">Klikając przycisk OK, akceptujesz postanowienia licencyjne. "</span><span class="sxs-lookup"><span data-stu-id="b360b-114">By clicking OK, you are accepting license terms.'</span></span>

![Wdrażanie na platformie Azure akceptacji licencji wymaga automatyzacji](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="b360b-116">więcej informacji</span><span class="sxs-lookup"><span data-stu-id="b360b-116">More details</span></span>

- [<span data-ttu-id="b360b-117">Wymagaj akceptacji licencji w PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="b360b-117">Require License Acceptance in PowerShellGet</span></span>](../../concepts/module-license-acceptance.md)
- [<span data-ttu-id="b360b-118">Wymagaj akceptacji licencji w galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="b360b-118">Require License Acceptance in PowerShell Gallery</span></span>](items-that-require-license-acceptance.md)
- [<span data-ttu-id="b360b-119">Witryny usługi Automatyzacja Azure</span><span class="sxs-lookup"><span data-stu-id="b360b-119">Azure Automation website</span></span>](http://azure.microsoft.com/services/automation/)
