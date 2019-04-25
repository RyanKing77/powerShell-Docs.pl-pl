---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 57152e9f62c34600df63a2db8e9683928e825d93
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085800"
---
# <a name="detailed-information-about-lcm-state"></a>Szczegółowe informacje na temat stanu LCM

Wprowadziliśmy ulepszenia w szczegółowe informacje na temat stanu LCM udostępnianie. LCMState, który jest zwracany przez Get-DscLocalConfigurationManager może teraz zawierać następujące wartości:

* **Bezczynności (%)**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

Dodaliśmy również właściwość LCMStateDetail, który zawiera więcej informacji o stanie.
