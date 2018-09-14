---
ms.date: 09/10/2018
contributor: JKeithB
keywords: Galeria, programu powershell, polecenie cmdlet, galerii programu PowerShell
title: Zarządzanie kluczami interfejsu API
ms.openlocfilehash: 954eb27c25babdb8efe50c13caf5f2d287c6b3e3
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45523350"
---
# <a name="managing-api-keys"></a><span data-ttu-id="845df-103">Zarządzanie kluczami interfejsu API</span><span class="sxs-lookup"><span data-stu-id="845df-103">Managing API keys</span></span>

<span data-ttu-id="845df-104">Galeria programu PowerShell obsługuje tworzenie wielu kluczy interfejsu API do obsługuje szeroką gamę publikowania wymagania.</span><span class="sxs-lookup"><span data-stu-id="845df-104">The PowerShell Gallery supports creating multiple API keys to support a range of publishing requirements.</span></span> <span data-ttu-id="845df-105">Klucz interfejsu API można zastosować do co najmniej jeden pakiet, udziela określone uprawnienia i ma datę wygaśnięcia.</span><span class="sxs-lookup"><span data-stu-id="845df-105">An API key can apply to one or more packages, grants specific privileges, and has an expiration date.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="845df-106">Użytkownicy, którzy są publikowane w galerii programu PowerShell, przed wprowadzeniem o określonym zakresie klucze interfejsu API będzie mieć "pełnego dostępu do interfejsu API key".</span><span class="sxs-lookup"><span data-stu-id="845df-106">Users who published to the PowerShell Gallery prior to the introduction of scoped API keys will have a "Full access API key".</span></span> <span data-ttu-id="845df-107">Klucze pełny dostęp nie mają poprawki zabezpieczeń wbudowanych w zakresie klucze interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="845df-107">The full access keys do not have the security improvements built into scoped API keys.</span></span> <span data-ttu-id="845df-108">Klucze pełny dostęp do nigdy nie wygasa i Zastosuj do wszystkich posiadanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="845df-108">The full access keys never expires and apply to everything owned by the user.</span></span> <span data-ttu-id="845df-109">Jeśli usuniesz ten klucz, nie można utworzyć ponownie.</span><span class="sxs-lookup"><span data-stu-id="845df-109">If you delete this key, it cannot be recreated.</span></span>

<span data-ttu-id="845df-110">Na poniższej ilustracji przedstawiono opcje dostępne podczas tworzenia zakresu klucz interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="845df-110">The following image shows the options available when creating a scoped API key.</span></span>

![Tworzenie kluczy interfejsu API](../../Images/PSGallery_KeyScoped.png)

<span data-ttu-id="845df-112">W tym przykładzie utworzyliśmy klucza interfejsu API o nazwie **AzureRMDataFactory**.</span><span class="sxs-lookup"><span data-stu-id="845df-112">In this example, we created an API key named **AzureRMDataFactory**.</span></span> <span data-ttu-id="845df-113">Ta wartość klucza może służyć do wypychania pakietów, których nazwy zaczynają się od "AzureRM.DataFactory" i jest ważny przez 365 dni.</span><span class="sxs-lookup"><span data-stu-id="845df-113">This key value can be used to push packages with names that begin with 'AzureRM.DataFactory' and is valid for 365 days.</span></span> <span data-ttu-id="845df-114">Jest to typowy scenariusz, gdy różne zespoły w obrębie tej samej organizacji działają na różnych pakietach.</span><span class="sxs-lookup"><span data-stu-id="845df-114">This is a typical scenario when different teams within the same organization work on different packages.</span></span> <span data-ttu-id="845df-115">Członkowie zespołu mają klucz, który przyznaje im uprawnienia dla określonego pakietu, które działają z.</span><span class="sxs-lookup"><span data-stu-id="845df-115">The members of the team have a key that grants them privileges for the specific package they work on.</span></span>
<span data-ttu-id="845df-116">Wartość wygaśnięcia uniemożliwia użycie starych lub zapomniane kluczy.</span><span class="sxs-lookup"><span data-stu-id="845df-116">The expiration value prevents the use of stale or forgotten keys.</span></span>

## <a name="using-glob-patterns"></a><span data-ttu-id="845df-117">Przy użyciu wzorców glob</span><span class="sxs-lookup"><span data-stu-id="845df-117">Using glob patterns</span></span>

<span data-ttu-id="845df-118">Jeśli pracujesz na wielu pakietów, można użyć wzorców obsługi symboli wieloznacznych do dopasowania wielu pakietów jako grupa.</span><span class="sxs-lookup"><span data-stu-id="845df-118">If you work on multiple packages, you can use globbing patterns to match multiple packages as a group.</span></span> <span data-ttu-id="845df-119">Uprawnienia klucza interfejsu API dotyczą wszystkie nowe pakiety pasujących do wzorca glob.</span><span class="sxs-lookup"><span data-stu-id="845df-119">API key permissions apply to all new packages matching the glob pattern.</span></span> <span data-ttu-id="845df-120">Na przykład w poprzednim przykładzie użyto **wzorzec Glob** wartość "AzureRM.DataFactory\*".</span><span class="sxs-lookup"><span data-stu-id="845df-120">For example, the previous example uses a **Glob Pattern** value of 'AzureRM.DataFactory\*'.</span></span> <span data-ttu-id="845df-121">Możesz wypychać pakietu o nazwie "AzureRm.DataFactoryV2.Netcore" przy użyciu tego klucza, ponieważ pakiet jest zgodny ze wzorcem glob.</span><span class="sxs-lookup"><span data-stu-id="845df-121">You can push a package named 'AzureRm.DataFactoryV2.Netcore' using this key since the package matches the glob pattern.</span></span>

## <a name="create-api-keys-securely"></a><span data-ttu-id="845df-122">Bezpiecznie Utwórz klucze interfejsu API</span><span class="sxs-lookup"><span data-stu-id="845df-122">Create API keys securely</span></span>

<span data-ttu-id="845df-123">Dla bezpieczeństwa nowo utworzoną wartość klucza nigdy nie są wyświetlane na ekranie i jest dostępna tylko z przycisku kopiowania, jak pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="845df-123">For security, a newly created key value is never shown on the screen and is only available with the Copy button, as shown below.</span></span>

![Uzyskiwanie nową wartość klucza interfejsu API](../../Images/PSGallery_CopyCreatedKey.png)

> [!IMPORTANT]
> <span data-ttu-id="845df-125">Wartość klucza interfejsu API można kopiować tylko natychmiast po utworzeniu, lub Odśwież go.</span><span class="sxs-lookup"><span data-stu-id="845df-125">You can only copy the API key value immediately after creating or refreshing it.</span></span> <span data-ttu-id="845df-126">Nie będą wyświetlane i nie będzie dostępny ponownie po odświeżeniu strony.</span><span class="sxs-lookup"><span data-stu-id="845df-126">It will not be displayed, and will not be accessible again after the page is refreshed.</span></span> <span data-ttu-id="845df-127">Jeśli zgubisz wartości klucza, należy użyć Wygeneruj ponownie klucz i skopiuj klucz, po zostanie ponownie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="845df-127">If you lose the key value, you must use Regenerate, and copy the key after it is regenerated.</span></span>

## <a name="key-permissions-and-expiration"></a><span data-ttu-id="845df-128">Uprawnienia klucza i wygaśnięcia</span><span class="sxs-lookup"><span data-stu-id="845df-128">Key permissions and expiration</span></span>

<span data-ttu-id="845df-129">O określonym zakresie klucze interfejsu API można przypisać dowolny z następujących uprawnień:</span><span class="sxs-lookup"><span data-stu-id="845df-129">Scoped API keys can assign any of the following permissions:</span></span>

- <span data-ttu-id="845df-130">Wypychanie nowych pakietów</span><span class="sxs-lookup"><span data-stu-id="845df-130">Push new packages</span></span>
- <span data-ttu-id="845df-131">Wypychanie nowych lub pakietów aktualizacji</span><span class="sxs-lookup"><span data-stu-id="845df-131">Push new or update packages</span></span>
- <span data-ttu-id="845df-132">Wyrejestrowanie pakietów</span><span class="sxs-lookup"><span data-stu-id="845df-132">Unlist packages</span></span>

<span data-ttu-id="845df-133">Co nowego klucza ma wygaśnięcia.</span><span class="sxs-lookup"><span data-stu-id="845df-133">Every new key has an expiration.</span></span> <span data-ttu-id="845df-134">Wartość dla wygaśnięcia jest mierzony w dniach.</span><span class="sxs-lookup"><span data-stu-id="845df-134">The expiration value is measured in days.</span></span> <span data-ttu-id="845df-135">Możliwe wartości dla wygaśnięcia to:</span><span class="sxs-lookup"><span data-stu-id="845df-135">The possible values for expiration are:</span></span>

- <span data-ttu-id="845df-136">1 dzień</span><span class="sxs-lookup"><span data-stu-id="845df-136">1 day</span></span>
- <span data-ttu-id="845df-137">90 dni</span><span class="sxs-lookup"><span data-stu-id="845df-137">90 days</span></span>
- <span data-ttu-id="845df-138">180 dni</span><span class="sxs-lookup"><span data-stu-id="845df-138">180 days</span></span>
- <span data-ttu-id="845df-139">270 dni</span><span class="sxs-lookup"><span data-stu-id="845df-139">270 days</span></span>
- <span data-ttu-id="845df-140">365 dni (ustawienie domyślne)</span><span class="sxs-lookup"><span data-stu-id="845df-140">365 days (default)</span></span>

<span data-ttu-id="845df-141">Nie można zmienić tych ustawień, gdy klucz zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="845df-141">These settings cannot be changed once the key is created.</span></span> <span data-ttu-id="845df-142">Nie można utworzyć nowego klucza, który nigdy nie wygasa.</span><span class="sxs-lookup"><span data-stu-id="845df-142">You cannot create a new key that never expires.</span></span>

## <a name="editing-and-deleting-existing-api-keys"></a><span data-ttu-id="845df-143">Edytowanie i usuwanie istniejących kluczy interfejsu API</span><span class="sxs-lookup"><span data-stu-id="845df-143">Editing and deleting existing API keys</span></span>

<span data-ttu-id="845df-144">Można zmienić niektórych ustawień istniejącego klucza.</span><span class="sxs-lookup"><span data-stu-id="845df-144">You can change some settings of an existing key.</span></span> <span data-ttu-id="845df-145">Jak wspomniano wcześniej nie można zmodyfikować zakresu zabezpieczeń dla istniejącego klucza interfejsu API lub zmienić czas wygaśnięcia.</span><span class="sxs-lookup"><span data-stu-id="845df-145">As previously noted, you cannot modify the security scope for an existing API key or change the expiration.</span></span> <span data-ttu-id="845df-146">Opcje mogły być zmieniane są wyświetlane w poniższy zrzut ekranu:</span><span class="sxs-lookup"><span data-stu-id="845df-146">The changeable options are shown in the following screenshot:</span></span>

![Uzyskiwanie nową wartość klucza interfejsu API](../../Images/PSGallery_EditAPIKey.png)

<span data-ttu-id="845df-148">Aby zmienić pakietów kontrolowane za pomocą klucza, można wybrać indywidualnych pakietów z listy lub zmień wzorzec glob.</span><span class="sxs-lookup"><span data-stu-id="845df-148">To change the packages controlled by a key, you can choose individual packages from the list or change the glob pattern.</span></span>

<span data-ttu-id="845df-149">Klikając **ponownie wygenerować** tworzy nową wartość klucza.</span><span class="sxs-lookup"><span data-stu-id="845df-149">Clicking **Regenerate** creates a new key value.</span></span> <span data-ttu-id="845df-150">Tak samo jak w przypadku początkowo utworzono klucz, należy najpierw **kopiowania** wartość klucza natychmiast po jego aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="845df-150">Just like when you initially created the key, you must **Copy** the key value immediately after updating it.</span></span> <span data-ttu-id="845df-151">**Kopiowania** opcja jest niedostępna, gdy opuścisz tę stronę.</span><span class="sxs-lookup"><span data-stu-id="845df-151">The **Copy** option is not available once you leave this page.</span></span>

<span data-ttu-id="845df-152">Klikając **Usuń** zostanie wyświetlony komunikat potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="845df-152">Clicking **Delete** displays a confirmation message.</span></span> <span data-ttu-id="845df-153">Po usunięciu klucz będzie można jej używać.</span><span class="sxs-lookup"><span data-stu-id="845df-153">Once a key is deleted, it will be unusable.</span></span>

## <a name="key-expiration"></a><span data-ttu-id="845df-154">Data wygaśnięcia klucza</span><span class="sxs-lookup"><span data-stu-id="845df-154">Key expiration</span></span>

<span data-ttu-id="845df-155">Dziesięć dni przed wygaśnięciem, galerii programu PowerShell wysyła ostrzegawcza wiadomość e-mail właściciela konta, klucza interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="845df-155">Ten days before the expiration, the PowerShell Gallery sends a warning email the account holder of the API key.</span></span> <span data-ttu-id="845df-156">Po wygaśnięciu klucza jest bezużyteczny.</span><span class="sxs-lookup"><span data-stu-id="845df-156">After expiration, the key is unusable.</span></span> <span data-ttu-id="845df-157">Ostrzeżenie jest wyświetlane u góry strony zarządzania kluczami interfejsu API, które są wyświetlane klucze, które nie są już prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="845df-157">A warning message is displayed at the top of the API key management page showing which keys are no longer valid.</span></span> <span data-ttu-id="845df-158">Można wygenerować nową wartość klucza.</span><span class="sxs-lookup"><span data-stu-id="845df-158">You can generate a new key value.</span></span>
