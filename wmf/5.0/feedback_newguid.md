---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 2d6b4e3045bc8cff90576c345d1ccb97b2487426
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="new-guid"></a><span data-ttu-id="bf072-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="bf072-102">New-Guid</span></span>
<span data-ttu-id="bf072-103">Często skryptu (lub prawdopodobnie zapisywania zasobu DSC), muszą zapewnić Unikatowy identyfikator.</span><span class="sxs-lookup"><span data-stu-id="bf072-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="bf072-104">Identyfikatory GUID działał prawidłowo i ułatwia wywołać go wygenerować klasy identyfikatora Guid programu .NET Framework, ale po użyciu polecenia cmdlet powoduje, że to mogą szybciej odnajdywać dla użytkowników końcowych, którzy nie są już znasz klasy .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="bf072-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="bf072-105">PS C:\\ &gt; nowego identyfikatora Guid</span><span class="sxs-lookup"><span data-stu-id="bf072-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="bf072-106">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="bf072-106">Guid</span></span>

----

<span data-ttu-id="bf072-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="bf072-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>
