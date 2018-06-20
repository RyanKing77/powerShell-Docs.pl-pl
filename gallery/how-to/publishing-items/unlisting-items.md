---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, programu powershell, polecenia cmdlet, psgallery
title: Usuwanie elementów z listy
ms.openlocfilehash: bdcceba0ba18ade6a1d0f94602fd8d0f64af8936
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187541"
---
# <a name="unlisting-items"></a><span data-ttu-id="92ab4-103">Usuwanie elementów z listy</span><span class="sxs-lookup"><span data-stu-id="92ab4-103">Unlisting items</span></span>

<span data-ttu-id="92ab4-104">**Dlaczego jest usunięcie elementu z galerii programu PowerShell, które nie są widoczne jako opcja?**</span><span class="sxs-lookup"><span data-stu-id="92ab4-104">**Why is removing an item from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="92ab4-105">Galerii programu PowerShell nie obsługuje użytkowników trwałe usunięcie ich elementów.</span><span class="sxs-lookup"><span data-stu-id="92ab4-105">The PowerShell Gallery does not support users permanently deleting their items.</span></span>
<span data-ttu-id="92ab4-106">Dzięki temu inne osoby do podjęcia zależności elementów bez obaw o możliwości podziałów w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="92ab4-106">This enables others to take dependencies on your items without worrying about possible breaks in the future.</span></span>
<span data-ttu-id="92ab4-107">Na przykład jeśli moduł Pester zależy od modułu platformy Azure i moduł Azure zostanie usunięty z galerii, a następnie użytkownik może już używa modułu Pester.</span><span class="sxs-lookup"><span data-stu-id="92ab4-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then user can no longer uses the Pester module.</span></span>

<span data-ttu-id="92ab4-108">Zamiast usuwania elementu, jednak użytkownik może unlist go zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="92ab4-108">Instead of removing an item, however, you can unlist it instead.</span></span>

<span data-ttu-id="92ab4-109">**Jaki jest unlisting elementu w galerii programu PowerShell zrobić?**</span><span class="sxs-lookup"><span data-stu-id="92ab4-109">**What does unlisting an item on PowerShell Gallery do?**</span></span>

<span data-ttu-id="92ab4-110">Unlisting elementów, takich jak moduł lub skryptu w galerii programu PowerShell spowoduje usunięcie jej z karty elementów. Ponadto nie będzie wykrywalny, przy użyciu pasek wyszukiwania nieznajdujące się na liście elementów.</span><span class="sxs-lookup"><span data-stu-id="92ab4-110">Unlisting an item such as module or script on PowerShell Gallery will remove it from the Items tab. In addition, unlisted items will not be discoverable using the search bar.</span></span>
<span data-ttu-id="92ab4-111">Jedynym sposobem na pobranie elementu nieznajdujące się na liście jest określenie dokładnej nazwy i wersji elementu.</span><span class="sxs-lookup"><span data-stu-id="92ab4-111">The only way to download an unlisted item is to specify the exact name and version of the item.</span></span>
<span data-ttu-id="92ab4-112">W związku z tym unlisting elementu nie będę powodować utraty inne moduły lub skrypty, które od niego zależne.</span><span class="sxs-lookup"><span data-stu-id="92ab4-112">Because of this, the unlisting of an item will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="92ab4-113">Aby unlist tego elementu, można znaleźć na stronie Szczegóły elementu, a następnie usuń element.</span><span class="sxs-lookup"><span data-stu-id="92ab4-113">To unlist your item, visit the item details page and select 'Delete Item'.</span></span> <span data-ttu-id="92ab4-114">Usuń zaznaczenie pola wyboru "Lista", a następnie kliknij przycisk Zapisz.</span><span class="sxs-lookup"><span data-stu-id="92ab4-114">Uncheck the 'Listed' checkbox, and click Save.</span></span>

<span data-ttu-id="92ab4-115">**Jak usunąć element?**</span><span class="sxs-lookup"><span data-stu-id="92ab4-115">**How can I remove an item?**</span></span>

<span data-ttu-id="92ab4-116">Jeśli wystąpią scenariusza, gdy jest konieczne usunięcie elementu skontaktuj się z administratorami w galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="92ab4-116">If you experience a scenario where item deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="92ab4-117">Usuwanie prawidłowe scenariusze są następujące:</span><span class="sxs-lookup"><span data-stu-id="92ab4-117">Valid deletion scenarios are:</span></span>
- <span data-ttu-id="92ab4-118">Problemy dotyczące praw autorskich.</span><span class="sxs-lookup"><span data-stu-id="92ab4-118">Issues of copyright infringement.</span></span>
- <span data-ttu-id="92ab4-119">Element zawiera potencjalnie niebezpieczną zawartość.</span><span class="sxs-lookup"><span data-stu-id="92ab4-119">Item contains potentially harmful content.</span></span>
- <span data-ttu-id="92ab4-120">Element zawiera poufne dane.</span><span class="sxs-lookup"><span data-stu-id="92ab4-120">Item contains sensitive data.</span></span>

<span data-ttu-id="92ab4-121">Aby przesłać, Usuń element żądanie administratorom galerii programu PowerShell, odwiedź stronę szczegółów tego elementu, a następnie wybierz się z pomocą techniczną.</span><span class="sxs-lookup"><span data-stu-id="92ab4-121">To submit a Delete Item Request to the PowerShell Gallery Administrators, visit your item's detail page and select Contact Support.</span></span>