---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, programu powershell, polecenie cmdlet, galerii programu PowerShell
title: Usuwanie elementów
ms.openlocfilehash: 454cd404437bf1c31b9a1b81cd9dd0ac81e6b0f6
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893097"
---
# <a name="deleting-items"></a><span data-ttu-id="6cd4e-103">Usuwanie elementów</span><span class="sxs-lookup"><span data-stu-id="6cd4e-103">Deleting items</span></span>

<span data-ttu-id="6cd4e-104">Galerii programu PowerShell nie obsługuje trwałe usunięcie elementów, ponieważ, każdy, kto jest w zależności od jego pozostałej dostępnej zaburzyłaby.</span><span class="sxs-lookup"><span data-stu-id="6cd4e-104">The PowerShell Gallery does not support permanent deletion of items, because that would break anyone who is depending on it remaining available.</span></span>

<span data-ttu-id="6cd4e-105">Zamiast tego w galerii programu PowerShell obsługuje sposób wyrejestrowanie element, którego może odbywać się na stronie zarządzania elementu w witrynie sieci web.</span><span class="sxs-lookup"><span data-stu-id="6cd4e-105">Instead, the PowerShell Gallery supports a way to 'unlist' an item, which can be done in the item management page on the web site.</span></span>
<span data-ttu-id="6cd4e-106">Gdy element jest nieobecne na liście, go nie są już wyświetlane w polu wyszukiwania i w dowolnym elemencie ofercie w galerii programu PowerShell i korzystanie z poleceń modułu PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="6cd4e-106">When an item is unlisted, it no longer shows up in search and in any item listing, both on the PowerShell Gallery and using PowerShellGet commands.</span></span>
<span data-ttu-id="6cd4e-107">Jednak pozostanie dostępna do pobrania, określając dokładna wersja, która umożliwia zautomatyzowanych skryptów kontynuować pracę.</span><span class="sxs-lookup"><span data-stu-id="6cd4e-107">However, it remains downloadable by specifying its exact version, which is what allows the automated scripts to continue working.</span></span>

<span data-ttu-id="6cd4e-108">Jeśli napotkasz sytuacjach wyjątkowych Jeżeli uważasz, że jeden z elementów, należy usunąć to mogą być obsługiwane ręcznie przez zespół galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6cd4e-108">If you run into an exceptional situation where you think one of your items must be deleted, this can be handled manually by the PowerShell Gallery team.</span></span>
<span data-ttu-id="6cd4e-109">Na przykład jeśli występuje problem naruszenia praw autorskich lub potencjalnie niebezpieczną zawartość, która może być uzasadniony powód, aby go usunąć.</span><span class="sxs-lookup"><span data-stu-id="6cd4e-109">For example, if there is a copyright infringement issue, or potentially harmful content, that could be a valid reason to delete it.</span></span>
<span data-ttu-id="6cd4e-110">Należy przesłać żądanie pomocy technicznej za pośrednictwem [galerii programu PowerShell](http://www.PowerShellGallery.com) w takiej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="6cd4e-110">You should submit a support request through [PowerShell Gallery](http://www.PowerShellGallery.com) in that case.</span></span>