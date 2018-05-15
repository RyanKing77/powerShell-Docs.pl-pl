---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeria, programu powershell, polecenia cmdlet, psgallery
title: Usuwanie elementów
ms.openlocfilehash: 5af66c5b7edf8f0d7049a98ed4dd10b13d4e9471
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="deleting-items"></a><span data-ttu-id="1c1d4-103">Usuwanie elementów</span><span class="sxs-lookup"><span data-stu-id="1c1d4-103">Deleting items</span></span>

<span data-ttu-id="1c1d4-104">Galerii programu PowerShell nie obsługuje trwałe usunięcie elementów, ponieważ który spowoduje przerwanie każdego, kto jest w zależności od jego pozostałej dostępnej.</span><span class="sxs-lookup"><span data-stu-id="1c1d4-104">The PowerShell Gallery does not support permanent deletion of items, because that would break anyone who is depending on it remaining available.</span></span>

<span data-ttu-id="1c1d4-105">Zamiast tego w galerii programu PowerShell obsługuje sposób unlist elementu, można to zrobić na stronie Zarządzanie elementu w witrynie sieci web.</span><span class="sxs-lookup"><span data-stu-id="1c1d4-105">Instead, the PowerShell Gallery supports a way to 'unlist' an item, which can be done in the item management page on the web site.</span></span>
<span data-ttu-id="1c1d4-106">Gdy element jest nieznajdujące się na liście, jest już wyświetlane w wyszukiwania i wyświetlania w galerii programu PowerShell i za pomocą poleceń PowerShellGet dowolnego elementu.</span><span class="sxs-lookup"><span data-stu-id="1c1d4-106">When an item is unlisted, it no longer shows up in search and in any item listing, both on the PowerShell Gallery and using PowerShellGet commands.</span></span>
<span data-ttu-id="1c1d4-107">Jednak pozostanie dostępna do pobrania przez określenie dokładnej wersji, czyli, co umożliwia zautomatyzowanych skryptów kontynuować pracę.</span><span class="sxs-lookup"><span data-stu-id="1c1d4-107">However, it remains downloadable by specifying its exact version, which is what allows the automated scripts to continue working.</span></span>

<span data-ttu-id="1c1d4-108">Jeśli wystąpiły wyjątkowej sytuacji, gdy uważasz, że jeden z elementów muszą zostać usunięte, może to ręcznie obsługiwanych przez zespół galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1c1d4-108">If you run into an exceptional situation where you think one of your items must be deleted, this can be handled manually by the PowerShell Gallery team.</span></span>
<span data-ttu-id="1c1d4-109">Na przykład jeśli istnieje problem praw autorskich lub potencjalnie niebezpieczną zawartość, którego można prawidłowej przyczyny go usunąć.</span><span class="sxs-lookup"><span data-stu-id="1c1d4-109">For example, if there is a copyright infringement issue, or potentially harmful content, that could be a valid reason to delete it.</span></span>
<span data-ttu-id="1c1d4-110">Należy przesłać żądanie obsługi za pomocą [galerii programu PowerShell] (http://www.PowerShellGallery.com) w takiej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="1c1d4-110">You should submit a support request through [PowerShell Gallery] (http://www.PowerShellGallery.com) in that case.</span></span>