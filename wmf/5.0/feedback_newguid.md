---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
ms.openlocfilehash: bb2e7b99d14c790bdd3df2f5c729275b96a659fc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="new-guid"></a><span data-ttu-id="c8a8b-102">Nowy identyfikator Guid</span><span class="sxs-lookup"><span data-stu-id="c8a8b-102">New-Guid</span></span>
<span data-ttu-id="c8a8b-103">Często skryptu (lub prawdopodobnie zapisywania zasobu DSC), muszą zapewnić Unikatowy identyfikator.</span><span class="sxs-lookup"><span data-stu-id="c8a8b-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="c8a8b-104">Identyfikatory GUID działał prawidłowo i ułatwia wywołać go wygenerować klasy identyfikatora Guid programu .NET Framework, ale po użyciu polecenia cmdlet powoduje, że to mogą szybciej odnajdywać dla użytkowników końcowych, którzy nie są już znasz klasy .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="c8a8b-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="c8a8b-105">PS C:\\ &gt; nowego identyfikatora Guid</span><span class="sxs-lookup"><span data-stu-id="c8a8b-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="c8a8b-106">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="c8a8b-106">Guid</span></span>

----

<span data-ttu-id="c8a8b-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="c8a8b-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>

