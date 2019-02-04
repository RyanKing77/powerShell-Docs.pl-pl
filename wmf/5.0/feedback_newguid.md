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
# <a name="new-guid"></a><span data-ttu-id="7babd-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="7babd-102">New-Guid</span></span>
<span data-ttu-id="7babd-103">Często skryptu (lub może być pisanie zasobu DSC), masz potrzebę Unikatowy identyfikator.</span><span class="sxs-lookup"><span data-stu-id="7babd-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="7babd-104">Identyfikatory GUID działał prawidłowo i łatwo wywoływać klasę identyfikator Guid programu .NET Framework, aby wygenerować, ale o polecenie cmdlet umożliwia dotarcie do każdego dla użytkowników końcowych, którzy nie są już zaznajomieni z klasy .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="7babd-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="7babd-105">PS C:\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="7babd-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="7babd-106">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="7babd-106">Guid</span></span>

----

<span data-ttu-id="7babd-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="7babd-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>
