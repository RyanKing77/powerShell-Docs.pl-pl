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
<a name="deploy-to-azure-automation"></a>Wdrażanie na usługi Automatyzacja Azure
===========================

Wdróż do przycisku usługi Automatyzacja Azure na stronie szczegółów wdroży element z galerii programu PowerShell do automatyzacji Azure.

![Wdrażanie na przycisku usługi Automatyzacja Azure](Images/DeployToAzureAutomationButton.png)

Po kliknięciu, nastąpi przekierowanie do portalu zarządzania Azure, której użytkownik loguje się przy użyciu poświadczeń konta platformy Azure.
Jeśli element zawiera zależności, wszystkie zależności zostanie wdrożone do automatyzacji Azure również.

Ostrzeżenie: Jeśli tego samego elementu i wersji już istnieje na koncie automatyzacji, jej ponownym wdrożeniem z galerii programu PowerShell spowoduje zastąpienie elementu na Twoim koncie automatyzacji.

Jeśli podczas wdrażania modułu, pojawi się w sekcji modułów w automatyzacji Azure.  Jeśli skrypt zostanie wdrożony, będą wyświetlane w sekcji elementów Runbook usługi Automatyzacja Azure.

Wdrażanie na przycisku automatyzacji Azure można wyłączyć, dodając AzureAutomationNotSupported tag do metadanych elementu.

Aby dowiedzieć się więcej na temat usługi Automatyzacja Azure, zobacz witrynę sieci Web usługi Automatyzacja Azure [witryny sieci Web usługi Automatyzacja Azure](http://azure.microsoft.com/services/automation/).

