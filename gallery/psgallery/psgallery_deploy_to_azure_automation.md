---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: Galeria, programu powershell, polecenia cmdlet, psgallery
title: psgallery_deploy_to_azure_automation
ms.openlocfilehash: 91f48fb43d7fb099e34ce5d3b3b632e3cb119d64
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
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

Aby dowiedzieć się więcej na temat usługi Automatyzacja Azure, zobacz witrynę sieci Web usługi Automatyzacja Azure [witryny sieci Web usługi Automatyzacja Azure](http://azure.microsoft.com/en-us/services/automation/).

