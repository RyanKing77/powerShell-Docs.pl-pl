---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeria, programu powershell, polecenia cmdlet, psgallery
title: psgallery_deploy_to_azure_automation
ms.openlocfilehash: 8da4eabead6a419dc0c01c74335c06bf8be25d0c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
<a name="deploy-to-azure-automation"></a><span data-ttu-id="ceb06-103">Wdrażanie w usłudze Azure Automation</span><span class="sxs-lookup"><span data-stu-id="ceb06-103">Deploy to Azure Automation</span></span>
===========================

<span data-ttu-id="ceb06-104">Wdróż do przycisku usługi Automatyzacja Azure na stronie szczegółów wdroży element z galerii programu PowerShell do automatyzacji Azure.</span><span class="sxs-lookup"><span data-stu-id="ceb06-104">The Deploy to Azure Automation button on the item details page will deploy the item from the PowerShell Gallery to Azure Automation.</span></span>

![Wdrażanie na przycisku usługi Automatyzacja Azure](Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="ceb06-106">Po kliknięciu, nastąpi przekierowanie do portalu zarządzania Azure, której użytkownik loguje się przy użyciu poświadczeń konta platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="ceb06-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="ceb06-107">Jeśli element zawiera zależności, wszystkie zależności zostanie wdrożone do automatyzacji Azure również.</span><span class="sxs-lookup"><span data-stu-id="ceb06-107">If the item includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

<span data-ttu-id="ceb06-108">Ostrzeżenie: Jeśli tego samego elementu i wersji już istnieje na koncie automatyzacji, jej ponownym wdrożeniem z galerii programu PowerShell spowoduje zastąpienie elementu na Twoim koncie automatyzacji.</span><span class="sxs-lookup"><span data-stu-id="ceb06-108">WARNING:  If the same item and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the item in your Automation account.</span></span>

<span data-ttu-id="ceb06-109">Jeśli podczas wdrażania modułu, pojawi się w sekcji modułów w automatyzacji Azure.</span><span class="sxs-lookup"><span data-stu-id="ceb06-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="ceb06-110">Jeśli skrypt zostanie wdrożony, będą wyświetlane w sekcji elementów Runbook usługi Automatyzacja Azure.</span><span class="sxs-lookup"><span data-stu-id="ceb06-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="ceb06-111">Wdrażanie na przycisku automatyzacji Azure można wyłączyć, dodając AzureAutomationNotSupported tag do metadanych elementu.</span><span class="sxs-lookup"><span data-stu-id="ceb06-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the item metadata.</span></span>

<span data-ttu-id="ceb06-112">Aby dowiedzieć się więcej na temat usługi Automatyzacja Azure, zobacz witrynę sieci Web usługi Automatyzacja Azure [witryny sieci Web usługi Automatyzacja Azure](http://azure.microsoft.com/services/automation/).</span><span class="sxs-lookup"><span data-stu-id="ceb06-112">To learn more about Azure Automation, see the Azure Automation website [Azure Automation website](http://azure.microsoft.com/services/automation/).</span></span>