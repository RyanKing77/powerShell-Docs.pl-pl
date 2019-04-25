---
ms.date: 03/15/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Korzystanie z platformy DSC na platformie Microsoft Azure
ms.openlocfilehash: 54a317a415ff12c3d270897f414cba88716f0728
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079884"
---
# <a name="using-dsc-on-microsoft-azure"></a>Korzystanie z platformy DSC na platformie Microsoft Azure

Desired State Configuration (DSC) jest obsługiwana w systemie Microsoft Azure za pośrednictwem [procedury obsługi rozszerzenia Azure Desired State Configuration](/azure/virtual-machines/extensions/dsc-overview) i [usługi Azure Automation DSC](/azure/automation/automation-dsc-overview).

## <a name="azure-desired-state-configuration-extension-handler"></a>Obsługa rozszerzenia Azure Desired State Configuration

Rozszerzenie DSC na platformie Azure umożliwia maszyn wirtualnych hostowanych na platformie Microsoft Azure były zarządzane za pomocą DSC.
Aby uzyskać więcej informacji, zobacz następujące tematy:

- [Obsługa rozszerzenia Azure Desired State Configuration](/azure/virtual-machines/extensions/dsc-overview)
- [Windows skalowania maszyn wirtualnych i Desired State Configuration przy użyciu szablonów usługi Azure Resource Manager](/azure/virtual-machines/extensions/dsc-template)
- [Przekazywanie poświadczeń do obsługi rozszerzenia DSC na platformie Azure](/azure/virtual-machines/extensions/dsc-credentials)
- [Historia rozszerzenia platformy Azure Desired State Configuration](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a>Azure Automation DSC

[Usługi Azure Automation](https://azure.microsoft.com/en-us/services/automation/) umożliwia zarządzanie konfiguracjami DSC, zasoby i węzły zarządzane z w obrębie platformy Azure. Aby uzyskać więcej informacji, zobacz następujące tematy:

- [Azure Automation DSC](/azure/automation/automation-dsc-overview)
- [Wprowadzenie do usługi Azure Automation DSC](/azure/automation/automation-dsc-getting-started)
- [Dołączanie maszyn w celu zarządzania przez usługi Azure Automation DSC](/azure/automation/automation-dsc-onboarding)