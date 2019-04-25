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
# <a name="new-guid"></a><span data-ttu-id="92aa9-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="92aa9-102">New-Guid</span></span>
<span data-ttu-id="92aa9-103">Często skryptu (lub może być pisanie zasobu DSC), masz potrzebę Unikatowy identyfikator.</span><span class="sxs-lookup"><span data-stu-id="92aa9-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="92aa9-104">Identyfikatory GUID działał prawidłowo i łatwo wywoływać klasę identyfikator Guid programu .NET Framework, aby wygenerować, ale o polecenie cmdlet umożliwia dotarcie do każdego dla użytkowników końcowych, którzy nie są już zaznajomieni z klasy .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="92aa9-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="92aa9-105">PS C:\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="92aa9-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="92aa9-106">Guid</span><span class="sxs-lookup"><span data-stu-id="92aa9-106">Guid</span></span>

----

<span data-ttu-id="92aa9-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="92aa9-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>
