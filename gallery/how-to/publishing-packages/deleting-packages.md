---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, programu powershell, polecenie cmdlet, galerii programu PowerShell
title: Usuwanie pakietów
ms.openlocfilehash: ca5e68fcad52e4c7561d2c2b3858228652f22e0b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684976"
---
# <a name="deleting-packages"></a><span data-ttu-id="ff58e-103">Usuwanie pakietów</span><span class="sxs-lookup"><span data-stu-id="ff58e-103">Deleting Packages</span></span>

<span data-ttu-id="ff58e-104">Galeria programu PowerShell nie obsługuje trwałego usunięcia pakietów, ponieważ, każdy, kto jest w zależności od jego pozostałej dostępnej zaburzyłaby.</span><span class="sxs-lookup"><span data-stu-id="ff58e-104">The PowerShell Gallery does not support permanent deletion of packages, because that would break anyone who is depending on it remaining available.</span></span>

<span data-ttu-id="ff58e-105">Zamiast tego w galerii programu PowerShell obsługuje sposób wyrejestrowanie pakietu, co można zrobić na stronie pakiet zarządzania, w witrynie sieci web.</span><span class="sxs-lookup"><span data-stu-id="ff58e-105">Instead, the PowerShell Gallery supports a way to 'unlist' a package, which can be done in the package management page on the web site.</span></span>
<span data-ttu-id="ff58e-106">Gdy pakiet jest nieobecne na liście, go nie jest już wyświetlana w polu wyszukiwania i w dowolnym pakiecie ofercie w galerii programu PowerShell i korzystanie z poleceń modułu PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="ff58e-106">When a package is unlisted, it no longer shows up in search and in any package listing, both on the PowerShell Gallery and using PowerShellGet commands.</span></span>
<span data-ttu-id="ff58e-107">Jednak pozostanie dostępna do pobrania, określając dokładna wersja, która umożliwia zautomatyzowanych skryptów kontynuować pracę.</span><span class="sxs-lookup"><span data-stu-id="ff58e-107">However, it remains downloadable by specifying its exact version, which is what allows the automated scripts to continue working.</span></span>

<span data-ttu-id="ff58e-108">Jeśli napotkasz sytuacjach wyjątkowych Jeżeli uważasz, że jeden z pakietów, należy usunąć to mogą być obsługiwane ręcznie przez zespół galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ff58e-108">If you run into an exceptional situation where you think one of your packages must be deleted, this can be handled manually by the PowerShell Gallery team.</span></span>
<span data-ttu-id="ff58e-109">Na przykład jeśli występuje problem naruszenia praw autorskich lub potencjalnie niebezpieczną zawartość, która może być uzasadniony powód, aby go usunąć.</span><span class="sxs-lookup"><span data-stu-id="ff58e-109">For example, if there is a copyright infringement issue, or potentially harmful content, that could be a valid reason to delete it.</span></span>
<span data-ttu-id="ff58e-110">Należy przesłać żądanie pomocy technicznej za pośrednictwem [galerii programu PowerShell](http://www.PowerShellGallery.com) w takiej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="ff58e-110">You should submit a support request through [PowerShell Gallery](http://www.PowerShellGallery.com) in that case.</span></span>
