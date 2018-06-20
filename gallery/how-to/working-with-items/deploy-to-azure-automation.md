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
ms.locfileid: "34219338"
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
