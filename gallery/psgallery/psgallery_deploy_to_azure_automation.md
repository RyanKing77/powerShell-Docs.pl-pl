---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: Galeria, programu powershell, polecenia cmdlet, psgallery
title: psgallery_deploy_to_azure_automation
ms.openlocfilehash: 223acbcc2f6cd4f15e1ee55d3f2f68df851cd902
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
<a name="deploy-to-azure-automation"></a><span data-ttu-id="8ca0a-103">Wdrażanie na usługi Automatyzacja Azure</span><span class="sxs-lookup"><span data-stu-id="8ca0a-103">Deploy to Azure Automation</span></span>
===========================

<span data-ttu-id="8ca0a-104">Wdróż do przycisku usługi Automatyzacja Azure na stronie szczegółów wdroży element z galerii programu PowerShell do automatyzacji Azure.</span><span class="sxs-lookup"><span data-stu-id="8ca0a-104">The Deploy to Azure Automation button on the item details page will deploy the item from the PowerShell Gallery to Azure Automation.</span></span>

![Wdrażanie na przycisku usługi Automatyzacja Azure](Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="8ca0a-106">Po kliknięciu, nastąpi przekierowanie do portalu zarządzania Azure, której użytkownik loguje się przy użyciu poświadczeń konta platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="8ca0a-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="8ca0a-107">Jeśli element zawiera zależności, wszystkie zależności zostanie wdrożone do automatyzacji Azure również.</span><span class="sxs-lookup"><span data-stu-id="8ca0a-107">If the item includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

<span data-ttu-id="8ca0a-108">Ostrzeżenie: Jeśli tego samego elementu i wersji już istnieje na koncie automatyzacji, jej ponownym wdrożeniem z galerii programu PowerShell spowoduje zastąpienie elementu na Twoim koncie automatyzacji.</span><span class="sxs-lookup"><span data-stu-id="8ca0a-108">WARNING:  If the same item and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the item in your Automation account.</span></span>

<span data-ttu-id="8ca0a-109">Jeśli podczas wdrażania modułu, pojawi się w sekcji modułów w automatyzacji Azure.</span><span class="sxs-lookup"><span data-stu-id="8ca0a-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="8ca0a-110">Jeśli skrypt zostanie wdrożony, będą wyświetlane w sekcji elementów Runbook usługi Automatyzacja Azure.</span><span class="sxs-lookup"><span data-stu-id="8ca0a-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="8ca0a-111">Wdrażanie na przycisku automatyzacji Azure można wyłączyć, dodając AzureAutomationNotSupported tag do metadanych elementu.</span><span class="sxs-lookup"><span data-stu-id="8ca0a-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the item metadata.</span></span>

<span data-ttu-id="8ca0a-112">Aby dowiedzieć się więcej na temat usługi Automatyzacja Azure, zobacz witrynę sieci Web usługi Automatyzacja Azure [witryny sieci Web usługi Automatyzacja Azure](http://azure.microsoft.com/services/automation/).</span><span class="sxs-lookup"><span data-stu-id="8ca0a-112">To learn more about Azure Automation, see the Azure Automation website [Azure Automation website](http://azure.microsoft.com/services/automation/).</span></span>

