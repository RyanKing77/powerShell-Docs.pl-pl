---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeria, programu powershell, polecenia cmdlet, psgallery
title: Wdrażanie w usłudze Azure Automation
ms.openlocfilehash: 1efdc289228d3a6962302d12ccf44143ce63a806
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="deploy-to-azure-automation"></a>Wdrażanie w usłudze Azure Automation

Wdróż do przycisku usługi Automatyzacja Azure na stronie szczegółów wdroży element z galerii programu PowerShell do automatyzacji Azure.

![Wdrażanie na przycisku usługi Automatyzacja Azure](../../Images/DeployToAzureAutomationButton.png)

Po kliknięciu, nastąpi przekierowanie do portalu zarządzania Azure, której użytkownik loguje się przy użyciu poświadczeń konta platformy Azure.
Jeśli element zawiera zależności, wszystkie zależności zostanie wdrożone do automatyzacji Azure również.

> [!WARNING]
> Jeśli tego samego elementu i wersji już istnieje na koncie automatyzacji, jej ponownym wdrożeniem z galerii programu PowerShell spowoduje zastąpienie elementu na Twoim koncie automatyzacji.

Jeśli podczas wdrażania modułu, pojawi się w sekcji modułów w automatyzacji Azure.  Jeśli skrypt zostanie wdrożony, będą wyświetlane w sekcji elementów Runbook usługi Automatyzacja Azure.

Wdrażanie na przycisku automatyzacji Azure można wyłączyć, dodając AzureAutomationNotSupported tag do metadanych elementu.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Wymaganie akceptacji licencji na potrzeby wdrażania w usłudze Azure Automation

Moduł podczas wdrażania usługi Automatyzacja Azure wymaga akceptacji licencji, interfejsu użytkownika portalu wyświetli informacją o tym zastrzeżenie "akceptacji licencji wymaga tego modułu. Klikając przycisk OK, akceptujesz postanowienia licencyjne. "

![Wdrażanie na platformie Azure akceptacji licencji wymaga automatyzacji](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>więcej informacji

- [Wymagaj akceptacji licencji w PowerShellGet](../../concepts/module-license-acceptance.md)
- [Wymagaj akceptacji licencji w galerii programu PowerShell](items-that-require-license-acceptance.md)
- [Witryny usługi Automatyzacja Azure](http://azure.microsoft.com/services/automation/)
