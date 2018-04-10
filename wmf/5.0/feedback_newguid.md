---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 91c115c7f0553cd5edf7fecf04e6a5c71c0a1aa2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="new-guid"></a><span data-ttu-id="18bcc-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="18bcc-102">New-Guid</span></span>
<span data-ttu-id="18bcc-103">Często skryptu (lub prawdopodobnie zapisywania zasobu DSC), muszą zapewnić Unikatowy identyfikator.</span><span class="sxs-lookup"><span data-stu-id="18bcc-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="18bcc-104">Identyfikatory GUID działał prawidłowo i ułatwia wywołać go wygenerować klasy identyfikatora Guid programu .NET Framework, ale po użyciu polecenia cmdlet powoduje, że to mogą szybciej odnajdywać dla użytkowników końcowych, którzy nie są już znasz klasy .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="18bcc-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="18bcc-105">PS C:\\ &gt; nowego identyfikatora Guid</span><span class="sxs-lookup"><span data-stu-id="18bcc-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="18bcc-106">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="18bcc-106">Guid</span></span>

----

<span data-ttu-id="18bcc-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="18bcc-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>