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
<a name="deploy-to-azure-automation"></a>Wdrażanie w usłudze Azure Automation
===========================

Wdróż do przycisku usługi Automatyzacja Azure na stronie szczegółów wdroży element z galerii programu PowerShell do automatyzacji Azure.

![Wdrażanie na przycisku usługi Automatyzacja Azure](Images/DeployToAzureAutomationButton.png)

Po kliknięciu, nastąpi przekierowanie do portalu zarządzania Azure, której użytkownik loguje się przy użyciu poświadczeń konta platformy Azure.
Jeśli element zawiera zależności, wszystkie zależności zostanie wdrożone do automatyzacji Azure również.

Ostrzeżenie: Jeśli tego samego elementu i wersji już istnieje na koncie automatyzacji, jej ponownym wdrożeniem z galerii programu PowerShell spowoduje zastąpienie elementu na Twoim koncie automatyzacji.

Jeśli podczas wdrażania modułu, pojawi się w sekcji modułów w automatyzacji Azure.  Jeśli skrypt zostanie wdrożony, będą wyświetlane w sekcji elementów Runbook usługi Automatyzacja Azure.

Wdrażanie na przycisku automatyzacji Azure można wyłączyć, dodając AzureAutomationNotSupported tag do metadanych elementu.

Aby dowiedzieć się więcej na temat usługi Automatyzacja Azure, zobacz witrynę sieci Web usługi Automatyzacja Azure [witryny sieci Web usługi Automatyzacja Azure](http://azure.microsoft.com/services/automation/).