---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 90fd26f9f27d2398da839b309c17b921bb3b8521
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685109"
---
# <a name="new-guid"></a>New-Guid
Często skryptu (lub może być pisanie zasobu DSC), masz potrzebę Unikatowy identyfikator. Identyfikatory GUID działał prawidłowo i łatwo wywoływać klasę identyfikator Guid programu .NET Framework, aby wygenerować, ale o polecenie cmdlet umożliwia dotarcie do każdego dla użytkowników końcowych, którzy nie są już zaznajomieni z klasy .NET Framework:

PS C:\\&gt; New-Guid

Identyfikator GUID

----

e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
