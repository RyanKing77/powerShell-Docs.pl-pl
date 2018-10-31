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
# <a name="deploy-to-azure-automation"></a>Wdrażanie w usłudze Azure Automation

Wdróż do przycisku w usłudze Azure Automation na stronie szczegółów pakietu wdroży pakiet z galerii programu PowerShell w usłudze Azure Automation.

![Wdrażanie do usługi Azure Automation przycisku](../../Images/DeployToAzureAutomationButton.png)

Po kliknięciu, nastąpi przekierowanie do portalu zarządzania systemu Azure, w której użytkownik loguje się przy użyciu poświadczeń konta platformy Azure.
Jeśli pakiet zawiera zależności, wszystkie zależności będą wdrażane do usługi Azure Automation także.

> [!WARNING]
> Jeśli tego samego pakietu i wersji już istnieje na koncie usługi Automation, wdrażania go ponownie z galerii programu PowerShell spowoduje zastąpienie pakietu na koncie usługi Automation.

Jeśli wdrożono moduł, pojawi się w sekcji modułów usługi Azure Automation.  W przypadku wdrożenia skryptu pojawi się w sekcji elementów Runbook usługi Azure Automation.

Wdrażanie do usługi Azure Automation przycisku można wyłączyć przez dodanie tagu AzureAutomationNotSupported metadanych pakietu.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Wymaganie akceptacji licencji na potrzeby wdrażania w usłudze Azure Automation

Jeśli moduł jego wdrażanie w usłudze Azure Automation wymaga zaakceptowania licencji, interfejsu użytkownika portalu zostaną wyświetlone powiedzenie zastrzeżenie "ten moduł wymaga zaakceptowania licencji. Klikając przycisk OK, akceptujesz postanowienia licencyjne. "

![Wdrażanie na platformie Azure Automation, wymaga akceptacji licencji](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>Więcej szczegółów

- [Wymaganie akceptacji licencji w moduł PowerShellGet](../../concepts/module-license-acceptance.md)
- [Wymaganie akceptacji licencji w galerii programu PowerShell](packages-that-require-license-acceptance.md)
- [Witryny sieci Web Azure Automation](http://azure.microsoft.com/services/automation/)
