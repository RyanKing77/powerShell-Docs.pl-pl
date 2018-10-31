---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, programu powershell, polecenie cmdlet, galerii programu PowerShell
title: Wdrażanie w usłudze Azure Automation
ms.openlocfilehash: dc382b1cf3ceaa787f54c555d01e6bd9ba70e680
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004073"
---
# <a name="deploy-to-azure-automation"></a><span data-ttu-id="2a8fa-103">Wdrażanie w usłudze Azure Automation</span><span class="sxs-lookup"><span data-stu-id="2a8fa-103">Deploy to Azure Automation</span></span>

<span data-ttu-id="2a8fa-104">Wdróż do przycisku w usłudze Azure Automation na stronie szczegółów pakietu wdroży pakiet z galerii programu PowerShell w usłudze Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="2a8fa-104">The Deploy to Azure Automation button on the package details page will deploy the package from the PowerShell Gallery to Azure Automation.</span></span>

![Wdrażanie do usługi Azure Automation przycisku](../../Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="2a8fa-106">Po kliknięciu, nastąpi przekierowanie do portalu zarządzania systemu Azure, w której użytkownik loguje się przy użyciu poświadczeń konta platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="2a8fa-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="2a8fa-107">Jeśli pakiet zawiera zależności, wszystkie zależności będą wdrażane do usługi Azure Automation także.</span><span class="sxs-lookup"><span data-stu-id="2a8fa-107">If the package includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

> [!WARNING]
> <span data-ttu-id="2a8fa-108">Jeśli tego samego pakietu i wersji już istnieje na koncie usługi Automation, wdrażania go ponownie z galerii programu PowerShell spowoduje zastąpienie pakietu na koncie usługi Automation.</span><span class="sxs-lookup"><span data-stu-id="2a8fa-108">If the same package and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the package in your Automation account.</span></span>

<span data-ttu-id="2a8fa-109">Jeśli wdrożono moduł, pojawi się w sekcji modułów usługi Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="2a8fa-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="2a8fa-110">W przypadku wdrożenia skryptu pojawi się w sekcji elementów Runbook usługi Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="2a8fa-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="2a8fa-111">Wdrażanie do usługi Azure Automation przycisku można wyłączyć przez dodanie tagu AzureAutomationNotSupported metadanych pakietu.</span><span class="sxs-lookup"><span data-stu-id="2a8fa-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the package metadata.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="2a8fa-112">Wymaganie akceptacji licencji na potrzeby wdrażania w usłudze Azure Automation</span><span class="sxs-lookup"><span data-stu-id="2a8fa-112">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="2a8fa-113">Jeśli moduł jego wdrażanie w usłudze Azure Automation wymaga zaakceptowania licencji, interfejsu użytkownika portalu zostaną wyświetlone powiedzenie zastrzeżenie "ten moduł wymaga zaakceptowania licencji.</span><span class="sxs-lookup"><span data-stu-id="2a8fa-113">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="2a8fa-114">Klikając przycisk OK, akceptujesz postanowienia licencyjne. "</span><span class="sxs-lookup"><span data-stu-id="2a8fa-114">By clicking OK, you are accepting license terms.'</span></span>

![Wdrażanie na platformie Azure Automation, wymaga akceptacji licencji](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="2a8fa-116">Więcej szczegółów</span><span class="sxs-lookup"><span data-stu-id="2a8fa-116">More details</span></span>

- [<span data-ttu-id="2a8fa-117">Wymaganie akceptacji licencji w moduł PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="2a8fa-117">Require License Acceptance in PowerShellGet</span></span>](../../concepts/module-license-acceptance.md)
- [<span data-ttu-id="2a8fa-118">Wymaganie akceptacji licencji w galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="2a8fa-118">Require License Acceptance in PowerShell Gallery</span></span>](packages-that-require-license-acceptance.md)
- [<span data-ttu-id="2a8fa-119">Witryny sieci Web Azure Automation</span><span class="sxs-lookup"><span data-stu-id="2a8fa-119">Azure Automation website</span></span>](http://azure.microsoft.com/services/automation/)
