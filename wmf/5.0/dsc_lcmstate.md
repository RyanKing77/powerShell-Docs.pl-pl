---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
ms.openlocfilehash: 4fc146f84588d368ac3eb819e3acb4cb8c5d8793
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="detailed-information-about-lcm-state"></a>Szczegółowe informacje na temat stanu LCM

Wprowadzono ulepszenia udostępnia szczegółowe informacje o stanie LCM. LCMState, zwracane przez Get-DscLocalConfigurationManager teraz może zawierać następujące wartości:

* **W stanie bezczynności**
* **Zajęty**
* **PendingReboot**
* **PendingConfiguration**

Dodano także właściwością LCMStateDetail, zawierający więcej informacji o stanie.

