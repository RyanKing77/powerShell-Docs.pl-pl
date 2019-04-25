---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 90fd26f9f27d2398da839b309c17b921bb3b8521
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085330"
---
# <a name="new-guid"></a>New-Guid
Często skryptu (lub może być pisanie zasobu DSC), masz potrzebę Unikatowy identyfikator. Identyfikatory GUID działał prawidłowo i łatwo wywoływać klasę identyfikator Guid programu .NET Framework, aby wygenerować, ale o polecenie cmdlet umożliwia dotarcie do każdego dla użytkowników końcowych, którzy nie są już zaznajomieni z klasy .NET Framework:

PS C:\\&gt; New-Guid

Guid

----

e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
