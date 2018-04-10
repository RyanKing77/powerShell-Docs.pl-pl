---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: baa35e9acd24d6f6155acf617a0d2c2210742af7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="detailed-information-about-lcm-state"></a>Szczegółowe informacje na temat stanu LCM

Wprowadzono ulepszenia udostępnia szczegółowe informacje o stanie LCM. LCMState, zwracane przez Get-DscLocalConfigurationManager teraz może zawierać następujące wartości:

* **W stanie bezczynności**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

Dodano także właściwością LCMStateDetail, zawierający więcej informacji o stanie.