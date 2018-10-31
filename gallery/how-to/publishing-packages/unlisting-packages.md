---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, programu powershell, polecenie cmdlet, galerii programu PowerShell
title: Usuwanie pakietów
ms.openlocfilehash: fb66fd23dae1d4640056a764c31426f61f56d910
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004096"
---
# <a name="unlisting-packages"></a><span data-ttu-id="7264d-103">Unlisting pakietów</span><span class="sxs-lookup"><span data-stu-id="7264d-103">Unlisting Packages</span></span>

<span data-ttu-id="7264d-104">**Dlaczego jest usunięcie pakietu z galerii programu PowerShell, które nie są widoczne jako opcja?**</span><span class="sxs-lookup"><span data-stu-id="7264d-104">**Why is removing a package from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="7264d-105">Galeria programu PowerShell nie obsługuje użytkowników trwale swoich pakietów.</span><span class="sxs-lookup"><span data-stu-id="7264d-105">The PowerShell Gallery does not support users permanently deleting their packages.</span></span>
<span data-ttu-id="7264d-106">Dzięki temu inne osoby do podjęcia zależności pakietów bez konieczności martwienia się o przerwy możliwe w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="7264d-106">This enables others to take dependencies on your packages without worrying about possible breaks in the future.</span></span>
<span data-ttu-id="7264d-107">Na przykład jeśli moduł usług Pester zależy od modułu platformy Azure i platformy Azure zostanie on usunięty z galerii, wówczas użytkownik może już nie korzysta z modułu usług Pester.</span><span class="sxs-lookup"><span data-stu-id="7264d-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then user can no longer uses the Pester module.</span></span>

<span data-ttu-id="7264d-108">Zamiast usuwania pakietu, jednak użytkownik może wyrejestrowanie go zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="7264d-108">Instead of removing an package, however, you can unlist it instead.</span></span>

<span data-ttu-id="7264d-109">**Ile kosztuje, usuwanie, czy pakiet w galerii programu PowerShell?**</span><span class="sxs-lookup"><span data-stu-id="7264d-109">**What does unlisting a package on PowerShell Gallery do?**</span></span>

<span data-ttu-id="7264d-110">Usuwanie pakietów, takich jak moduł lub skryptu w galerii programu PowerShell spowoduje usunięcie go z karty pakietów. Ponadto nie będzie wykrywalny, korzystając z paska wyszukiwania nieznajdujące się na liście pakietów.</span><span class="sxs-lookup"><span data-stu-id="7264d-110">Unlisting a package such as module or script on PowerShell Gallery will remove it from the Packages tab. In addition, unlisted packages will not be discoverable using the search bar.</span></span>
<span data-ttu-id="7264d-111">Jedynym sposobem, aby pobrać pakiet nieznajdujące się na liście jest określenie dokładnej nazwy i wersji pakietu.</span><span class="sxs-lookup"><span data-stu-id="7264d-111">The only way to download an unlisted package is to specify the exact name and version of the package.</span></span>
<span data-ttu-id="7264d-112">W związku z tym usuwanie pakietu nie będę powodować inne moduły lub skrypty, które od niego zależne.</span><span class="sxs-lookup"><span data-stu-id="7264d-112">Because of this, the unlisting of an package will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="7264d-113">Wyrejestrowanie pakietu, można znaleźć na stronie szczegółów pakietu i wybierz pozycję "Usuń Module".</span><span class="sxs-lookup"><span data-stu-id="7264d-113">To unlist your package, visit the package details page and select 'Delete Module'.</span></span> <span data-ttu-id="7264d-114">Usuń zaznaczenie pola wyboru "Lista", a następnie kliknij przycisk Zapisz.</span><span class="sxs-lookup"><span data-stu-id="7264d-114">Uncheck the 'Listed' checkbox, and click Save.</span></span>

<span data-ttu-id="7264d-115">**Jak usunąć pakiet?**</span><span class="sxs-lookup"><span data-stu-id="7264d-115">**How can I remove an package?**</span></span>

<span data-ttu-id="7264d-116">Występują scenariusz, w których jest konieczne usunięcie pakietów, skontaktuj się z administratorami galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7264d-116">If you experience a scenario where package deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="7264d-117">Prawidłowe usunięcie scenariusze są następujące:</span><span class="sxs-lookup"><span data-stu-id="7264d-117">Valid deletion scenarios are:</span></span>
- <span data-ttu-id="7264d-118">Problemy dotyczące praw autorskich.</span><span class="sxs-lookup"><span data-stu-id="7264d-118">Issues of copyright infringement.</span></span>
- <span data-ttu-id="7264d-119">Pakiet zawiera potencjalnie niebezpieczną zawartość.</span><span class="sxs-lookup"><span data-stu-id="7264d-119">Package contains potentially harmful content.</span></span>
- <span data-ttu-id="7264d-120">Pakiet zawiera dane poufne.</span><span class="sxs-lookup"><span data-stu-id="7264d-120">Package contains sensitive data.</span></span>

<span data-ttu-id="7264d-121">Aby przesłać żądanie, usuń pakiet żądania do administratorów galerii programu PowerShell, odwiedź stronę szczegółów Twojego pakietu i wybierz pozycję Kontakt z pomocą techniczną.</span><span class="sxs-lookup"><span data-stu-id="7264d-121">To submit a Delete Package Request to the PowerShell Gallery Administrators, visit your package's detail page and select Contact Support.</span></span>
