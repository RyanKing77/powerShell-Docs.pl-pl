---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeria, programu powershell, polecenia cmdlet, psgallery
title: Usuwanie elementów
ms.openlocfilehash: f82d80a35f51227c4671bd2b15a7d1c16f0ba0a8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="deleting-items"></a><span data-ttu-id="83b43-103">Usuwanie elementów</span><span class="sxs-lookup"><span data-stu-id="83b43-103">Deleting items</span></span>

<span data-ttu-id="83b43-104">Galerii programu PowerShell nie obsługuje trwałe usunięcie elementów, ponieważ który spowoduje przerwanie każdego, kto jest w zależności od jego pozostałej dostępnej.</span><span class="sxs-lookup"><span data-stu-id="83b43-104">The PowerShell Gallery does not support permanent deletion of items, because that would break anyone who is depending on it remaining available.</span></span>

<span data-ttu-id="83b43-105">Zamiast tego w galerii programu PowerShell obsługuje sposób unlist elementu, można to zrobić na stronie Zarządzanie elementu w witrynie sieci web.</span><span class="sxs-lookup"><span data-stu-id="83b43-105">Instead, the PowerShell Gallery supports a way to 'unlist' an item, which can be done in the item management page on the web site.</span></span>
<span data-ttu-id="83b43-106">Gdy element jest nieznajdujące się na liście, jest już wyświetlane w wyszukiwania i wyświetlania w galerii programu PowerShell i za pomocą poleceń PowerShellGet dowolnego elementu.</span><span class="sxs-lookup"><span data-stu-id="83b43-106">When an item is unlisted, it no longer shows up in search and in any item listing, both on the PowerShell Gallery and using PowerShellGet commands.</span></span>
<span data-ttu-id="83b43-107">Jednak pozostanie dostępna do pobrania przez określenie dokładnej wersji, czyli, co umożliwia zautomatyzowanych skryptów kontynuować pracę.</span><span class="sxs-lookup"><span data-stu-id="83b43-107">However, it remains downloadable by specifying its exact version, which is what allows the automated scripts to continue working.</span></span>

<span data-ttu-id="83b43-108">Jeśli wystąpiły wyjątkowej sytuacji, gdy uważasz, że jeden z elementów muszą zostać usunięte, może to ręcznie obsługiwanych przez zespół galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="83b43-108">If you run into an exceptional situation where you think one of your items must be deleted, this can be handled manually by the PowerShell Gallery team.</span></span>
<span data-ttu-id="83b43-109">Na przykład jeśli istnieje problem praw autorskich lub potencjalnie niebezpieczną zawartość, którego można prawidłowej przyczyny go usunąć.</span><span class="sxs-lookup"><span data-stu-id="83b43-109">For example, if there is a copyright infringement issue, or potentially harmful content, that could be a valid reason to delete it.</span></span>
<span data-ttu-id="83b43-110">Należy przesłać żądanie obsługi za pomocą [galerii programu PowerShell] (http://www.PowerShellGallery.com) w takiej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="83b43-110">You should submit a support request through [PowerShell Gallery] (http://www.PowerShellGallery.com) in that case.</span></span>