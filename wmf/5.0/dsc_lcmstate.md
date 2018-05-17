---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: db9b48c188b3bfe2e20c06875606a285922f55a6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="detailed-information-about-lcm-state"></a>Szczegółowe informacje na temat stanu LCM

Wprowadzono ulepszenia udostępnia szczegółowe informacje o stanie LCM. LCMState, zwracane przez Get-DscLocalConfigurationManager teraz może zawierać następujące wartości:

* **W stanie bezczynności**
* **Zajęty**
* **PendingReboot**
* **PendingConfiguration**

Dodano także właściwością LCMStateDetail, zawierający więcej informacji o stanie.
