---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: Galeria, programu powershell, polecenia cmdlet, psgallery
title: psgallery_unlist_items
ms.openlocfilehash: 8fa09c77e144f14bf0fd3493dff7650897100715
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="unlisting-items"></a><span data-ttu-id="d34d9-103">Elementy unlisting</span><span class="sxs-lookup"><span data-stu-id="d34d9-103">Unlisting items</span></span>

<span data-ttu-id="d34d9-104">**Dlaczego jest usunięcie elementu z galerii programu PowerShell, które nie są widoczne jako opcja?**</span><span class="sxs-lookup"><span data-stu-id="d34d9-104">**Why is removing an item from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="d34d9-105">Galerii programu PowerShell nie obsługuje użytkowników trwałe usunięcie ich elementów.</span><span class="sxs-lookup"><span data-stu-id="d34d9-105">The PowerShell Gallery does not support users permanently deleting their items.</span></span> <span data-ttu-id="d34d9-106">Dzięki temu inne osoby do podjęcia zależności elementów bez obaw o możliwości podziałów w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="d34d9-106">This enables others to take dependencies on your items without worrying about possible breaks in the future.</span></span> <span data-ttu-id="d34d9-107">Na przykład jeśli moduł Pester zależy od modułu platformy Azure i moduł Azure zostanie usunięty z galerii, a następnie użytkownik może już używa modułu Pester.</span><span class="sxs-lookup"><span data-stu-id="d34d9-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then user can no longer uses the Pester module.</span></span>

<span data-ttu-id="d34d9-108">Zamiast usuwania elementu, jednak użytkownik może unlist go zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="d34d9-108">Instead of removing an item, however, you can unlist it instead.</span></span>

<span data-ttu-id="d34d9-109">**Jaki jest unlisting elementu w galerii programu PowerShell zrobić?**</span><span class="sxs-lookup"><span data-stu-id="d34d9-109">**What does unlisting an item on PowerShell Gallery do?**</span></span>

<span data-ttu-id="d34d9-110">Unlisting elementów, takich jak moduł lub skryptu w galerii programu PowerShell spowoduje usunięcie jej z karty elementów.</span><span class="sxs-lookup"><span data-stu-id="d34d9-110">Unlisting an item such as module or script on PowerShell Gallery will remove it from the Items tab.</span></span>
<span data-ttu-id="d34d9-111">Ponadto nie będzie wykrywalny, przy użyciu pasek wyszukiwania nieznajdujące się na liście elementów.</span><span class="sxs-lookup"><span data-stu-id="d34d9-111">In addition, unlisted items will not be discoverable using the search bar.</span></span>
<span data-ttu-id="d34d9-112">Jedynym sposobem na pobranie elementu nieznajdujące się na liście jest określenie dokładnej nazwy i wersji elementu.</span><span class="sxs-lookup"><span data-stu-id="d34d9-112">The only way to download an unlisted item is to specify the exact name and version of the item.</span></span>
<span data-ttu-id="d34d9-113">W związku z tym unlisting elementu nie będę powodować utraty inne moduły lub skrypty, które od niego zależne.</span><span class="sxs-lookup"><span data-stu-id="d34d9-113">Because of this, the unlisting of an item will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="d34d9-114">Aby unlist tego elementu, można znaleźć na stronie Szczegóły elementu, a następnie usuń element.</span><span class="sxs-lookup"><span data-stu-id="d34d9-114">To unlist your item, visit the item details page and select 'Delete Item'.</span></span> <span data-ttu-id="d34d9-115">Usuń zaznaczenie pola wyboru "Lista", a następnie kliknij przycisk Zapisz.</span><span class="sxs-lookup"><span data-stu-id="d34d9-115">Uncheck the 'Listed' checkbox, and click Save.</span></span>

<span data-ttu-id="d34d9-116">**Jak usunąć element?**</span><span class="sxs-lookup"><span data-stu-id="d34d9-116">**How can I remove an item?**</span></span>

<span data-ttu-id="d34d9-117">Jeśli wystąpią scenariusza, gdy jest konieczne usunięcie elementu skontaktuj się z administratorami w galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d34d9-117">If you experience a scenario where item deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="d34d9-118">Usuwanie prawidłowe scenariusze są następujące:</span><span class="sxs-lookup"><span data-stu-id="d34d9-118">Valid deletion scenarios are:</span></span>
- <span data-ttu-id="d34d9-119">Problemy dotyczące praw autorskich.</span><span class="sxs-lookup"><span data-stu-id="d34d9-119">Issues of copyright infringement.</span></span>
- <span data-ttu-id="d34d9-120">Element zawiera potencjalnie niebezpieczną zawartość.</span><span class="sxs-lookup"><span data-stu-id="d34d9-120">Item contains potentially harmful content.</span></span>
- <span data-ttu-id="d34d9-121">Element zawiera poufne dane.</span><span class="sxs-lookup"><span data-stu-id="d34d9-121">Item contains sensitive data.</span></span>

<span data-ttu-id="d34d9-122">Aby przesłać, Usuń element żądanie administratorom galerii programu PowerShell, odwiedź stronę szczegółów tego elementu, a następnie wybierz się z pomocą techniczną.</span><span class="sxs-lookup"><span data-stu-id="d34d9-122">To submit a Delete Item Request to the PowerShell Gallery Administrators, visit your item's detail page and select Contact Support.</span></span>  


