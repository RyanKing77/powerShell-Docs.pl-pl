---
ms.date: 03/15/2018
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Korzystanie z platformy DSC na platformie Microsoft Azure
ms.openlocfilehash: 5b0d577e1fecdeac38c2c5f8e955a2d23b1eb707
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="using-dsc-on-microsoft-azure"></a>Korzystanie z platformy DSC na platformie Microsoft Azure

Pożądanej konfiguracji stanu (DSC) jest obsługiwana na platformie Microsoft Azure za pośrednictwem [Azure konfiguracji żądanego stanu rozszerzenia obsługi](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview) i za pomocą [Konfiguracja DSC automatyzacji Azure](/azure/automation/automation-dsc-overview).

## <a name="azure-desired-state-configuration-extension-handler"></a>Azure żądany stan konfiguracji rozszerzenia obsługi

Rozszerzenia usługi Konfiguracja DSC Azure umożliwia maszyn wirtualnych hostowanych na platformie Microsoft Azure mają być zarządzane w usłudze Konfiguracja DSC.
Aby uzyskać więcej informacji, zobacz następujące tematy:

- [Azure żądany stan konfiguracji rozszerzenia obsługi](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview)
- [VMSS systemu Windows i konfiguracji żądanego stanu przy użyciu szablonów usługi Azure Resource Manager](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-template)
- [Przekazywania poświadczeń do obsługi rozszerzenia usługi Konfiguracja DSC Azure](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-credentials)
- [Historia rozszerzenia konfiguracji Azure żądany stan](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a>Azure Automation DSC

[Usługi Automatyzacja Azure](https://azure.microsoft.com/services/automation/) umożliwia zarządzanie konfiguracji DSC, zasobów i węzły zarządzane przy użyciu w obrębie platformy Azure. Aby uzyskać więcej informacji, zobacz następujące tematy:

- [Azure Automation DSC](/azure/automation/automation-dsc-overview)
- [Wprowadzenie do korzystania z usługi Konfiguracja DSC automatyzacji Azure](/azure/automation/automation-dsc-getting-started)
- [Dołączania komputerów do zarządzania przez Konfiguracja DSC automatyzacji Azure](/azure/automation/automation-dsc-onboarding)