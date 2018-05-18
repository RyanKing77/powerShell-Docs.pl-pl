---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, programu powershell, polecenia cmdlet, psgallery
title: Zarządzanie właścicielami elementów
ms.openlocfilehash: 10d2a433253162847028e157b5bac47b23406469
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="managing-item-owners"></a><span data-ttu-id="f4e42-103">Zarządzanie właścicielami elementów</span><span class="sxs-lookup"><span data-stu-id="f4e42-103">Managing item owners</span></span>

<span data-ttu-id="f4e42-104">Własność elementu w galerii programu PowerShell jest zdefiniowana przez wydawca elementu w galerii.</span><span class="sxs-lookup"><span data-stu-id="f4e42-104">Ownership of an item in the PowerShell Gallery is defined by who published the item to the gallery.</span></span>
<span data-ttu-id="f4e42-105">Czasami metadanych musi być zarządzany poza publikowanie początkowego elementu, co oznacza, że metadane właściciela musi być modyfikowalną podczas elementu nie jest.</span><span class="sxs-lookup"><span data-stu-id="f4e42-105">Sometimes this metadata needs to be managed beyond the initial item publishing, which means the owner metadata needs to be mutable while the item itself is not.</span></span>

<span data-ttu-id="f4e42-106">Wszystkich właścicieli elementu są elementami równorzędnymi.</span><span class="sxs-lookup"><span data-stu-id="f4e42-106">All item owners are peers.</span></span>
<span data-ttu-id="f4e42-107">Oznacza to, że wszystkie właściciel elementu można opublikować nową wersję elementu.</span><span class="sxs-lookup"><span data-stu-id="f4e42-107">This means any item owner can publish a new version of an item.</span></span> <span data-ttu-id="f4e42-108">Oznacza to również usunąć inne właściciel elementu żadnych właściciel elementu.</span><span class="sxs-lookup"><span data-stu-id="f4e42-108">It also means that any item owner can remove any other item owner.</span></span>
<span data-ttu-id="f4e42-109">Właściciel nie ma urząd więcej niż inne właścicieli.</span><span class="sxs-lookup"><span data-stu-id="f4e42-109">No owner has more authority than other owners.</span></span>

## <a name="setting-an-items-initial-owner"></a><span data-ttu-id="f4e42-110">Ustawienie właściciel początkowy elementu</span><span class="sxs-lookup"><span data-stu-id="f4e42-110">Setting an Item's Initial Owner</span></span>

<span data-ttu-id="f4e42-111">Po opublikowaniu nowego elementu galerii programu PowerShell pierwotny właściciel jest zdefiniowana przez użytkownika, która wydała elementu.</span><span class="sxs-lookup"><span data-stu-id="f4e42-111">When a new item is published to PowerShell Gallery, the initial owner is defined by the user that published the item.</span></span> <span data-ttu-id="f4e42-112">Jest to określane przez interfejs API którego klucz był używany w poleceniu cmdlet Publish-Module.</span><span class="sxs-lookup"><span data-stu-id="f4e42-112">This is determined by whose API key was used in the Publish-Module cmdlet.</span></span>

## <a name="adding-owners"></a><span data-ttu-id="f4e42-113">Dodawanie właścicieli</span><span class="sxs-lookup"><span data-stu-id="f4e42-113">Adding Owners</span></span>

<span data-ttu-id="f4e42-114">Po opublikowaniu elementu w galerii programu PowerShell, jest bardzo proste zaprosić dodatkowym użytkownikom stają się właścicieli elementu.</span><span class="sxs-lookup"><span data-stu-id="f4e42-114">Once an item has been published to the PowerShell Gallery, it's easy to invite additional users to become owners of an item.</span></span>

1. <span data-ttu-id="f4e42-115">[Zaloguj się na](https://powershellgallery.com/users/account/LogOn) do galerii programu PowerShell przy użyciu konta, który jest bieżącym właścicielem elementu.</span><span class="sxs-lookup"><span data-stu-id="f4e42-115">[Log on](https://powershellgallery.com/users/account/LogOn) to the PowerShell Gallery with the account that is the current owner of an item.</span></span>
2. <span data-ttu-id="f4e42-116">Przejdź do strony elementu przy użyciu karty "Elementy", wyszukiwanie lub kliknięcie nazwy użytkownika, a następnie [ **Zarządzanie Moje elementy**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="f4e42-116">Navigate to an item page using the 'Items' tab, searching, or clicking your username and then [**Manage My Items**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="f4e42-117">Po zalogowaniu się jako właściciel elementu, brak zarządzania właścicielami link po lewej stronie kliknij.</span><span class="sxs-lookup"><span data-stu-id="f4e42-117">When logged on as an item's owner, there is a 'Manage Owners' link on the left side to click.</span></span>
4. <span data-ttu-id="f4e42-118">Wprowadź nazwę użytkownika osoby, które chcesz dodać jako właściciela, a następnie kliknij przycisk "Dodaj".</span><span class="sxs-lookup"><span data-stu-id="f4e42-118">Enter the username of the person to add as an owner and click 'Add'.</span></span>
5. <span data-ttu-id="f4e42-119">Wiadomość e-mail zostanie przesłany do nowego współwłaściciel jako zaproszenie do staje się właścicielem elementu.</span><span class="sxs-lookup"><span data-stu-id="f4e42-119">An email is then sent to the new co-owner, as an invitation to become an owner of an item.</span></span>
6. <span data-ttu-id="f4e42-120">Gdy użytkownik kliknie łącze, są pełne współwłaściciel pełną kontrolę nad elementem, w tym możliwość usunięcia innym użytkownikom jako właścicieli.</span><span class="sxs-lookup"><span data-stu-id="f4e42-120">Once that user clicks the link, they are a full co-owner with full control over an item, including the ability to remove other users as owners.</span></span>

<span data-ttu-id="f4e42-121">**Uwaga**: dopóki nowy właściciel potwierdzi własność, ich *nie* był wyświetlany jako właściciel elementu.</span><span class="sxs-lookup"><span data-stu-id="f4e42-121">**NOTE**: Until the new owner confirms ownership, they *will not* be listed as an owner of an item.</span></span>
<span data-ttu-id="f4e42-122">Podczas wyświetlania **zarządzania właścicielami** strony, zobaczysz wpis "oczekuje na zatwierdzenie" w bieżącym właścicieli.</span><span class="sxs-lookup"><span data-stu-id="f4e42-122">When viewing the **Manage Owners** page, you will see a "pending approval" entry in the current owners.</span></span>
<span data-ttu-id="f4e42-123">Czy można usunąć zaproszenia; Podobnie jak inne właściciele mogą zostać usunięte.</span><span class="sxs-lookup"><span data-stu-id="f4e42-123">That invitation can be removed; just as other owners can be removed.</span></span>
<span data-ttu-id="f4e42-124">Ten proces zaproszenia uniemożliwia użytkownikom fałszywie Dodawanie innym użytkownikom jako właściciele ich elementów.</span><span class="sxs-lookup"><span data-stu-id="f4e42-124">This process of invitations prevents users from falsely adding other users as owners of their items.</span></span>

<span data-ttu-id="f4e42-125">Należy pamiętać, że metadane "Autorzy" czysto dowolny tekst; tylko "właściciele" są kontrolowane.</span><span class="sxs-lookup"><span data-stu-id="f4e42-125">Note that the "Authors" metadata is purely freeform text; only "Owners" are controlled.</span></span>


## <a name="removing-owners"></a><span data-ttu-id="f4e42-126">Usuwanie właścicieli</span><span class="sxs-lookup"><span data-stu-id="f4e42-126">Removing Owners</span></span>

<span data-ttu-id="f4e42-127">Gdy element ma wiele właścicieli i jeden musi zostać usunięte, proces jest prosty:</span><span class="sxs-lookup"><span data-stu-id="f4e42-127">When an item has multiple owners and one needs to be removed, the process is simple:</span></span>

1. <span data-ttu-id="f4e42-128">[Zaloguj się na](https://powershellgallery.com/users/account/LogOn) do galerii programu PowerShell przy użyciu konta, który jest bieżącym właścicielem elementu;</span><span class="sxs-lookup"><span data-stu-id="f4e42-128">[Log on](https://powershellgallery.com/users/account/LogOn) to PowerShell Gallery with the account that is the current owner of an item;</span></span>
2. <span data-ttu-id="f4e42-129">Przejdź do strony elementu przy użyciu karty elementów, wyszukiwanie lub kliknięcie nazwy użytkownika, a następnie [ **Zarządzanie Moje elementy**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="f4e42-129">Navigate to an item page using the Items tab, searching, or clicking your username and then [**Manage My Items**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="f4e42-130">Po zalogowaniu się jako właściciel elementu, jest łączem zarządzania właścicielami po lewej stronie kliknij;</span><span class="sxs-lookup"><span data-stu-id="f4e42-130">When logged on as an item's owner, there is a 'Manage Owners' link on the left side to click;</span></span>
4. <span data-ttu-id="f4e42-131">Kliknij łącze "Usuń" obok właściciel ma zostać usunięty.</span><span class="sxs-lookup"><span data-stu-id="f4e42-131">Click the 'remove' link next to the owner to be removed.</span></span>



## <a name="transferring-item-ownership"></a><span data-ttu-id="f4e42-132">Przeniesieniem własności elementu</span><span class="sxs-lookup"><span data-stu-id="f4e42-132">Transferring Item Ownership</span></span>

<span data-ttu-id="f4e42-133">Czasami uzyskujemy żądania pomocy technicznej do przeniesienia elementu własności od jednego użytkownika do drugiego, ale prawie zawsze można wykonać to samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="f4e42-133">We sometimes get support requests to transfer item ownership from one user to another, but you can almost always accomplish this yourself.</span></span>
<span data-ttu-id="f4e42-134">Przesyłania własność z jednego użytkownika to po prostu kombinacja dwie funkcje powyżej.</span><span class="sxs-lookup"><span data-stu-id="f4e42-134">Transferring ownership from one user to another is simply a combination of the two features above.</span></span>

1. <span data-ttu-id="f4e42-135">Bieżący właściciel zaprasza nowego użytkownika, który staje się właścicielem wspólnej i nowy użytkownik akceptuje zaproszenie;</span><span class="sxs-lookup"><span data-stu-id="f4e42-135">The current owner invites the new user to become a co-owner and the new user accepts the invite;</span></span>
2. <span data-ttu-id="f4e42-136">Nowy użytkownik usuwa stare użytkownika z listy właścicieli.</span><span class="sxs-lookup"><span data-stu-id="f4e42-136">The new user removes the old user from the list of owners.</span></span>

<span data-ttu-id="f4e42-137">To żądanie trybu obszarze kilka formularze, ale proces działa tak samo.</span><span class="sxs-lookup"><span data-stu-id="f4e42-137">This request has come in under a couple forms but the process works the same.</span></span>

- <span data-ttu-id="f4e42-138">Własność elementu jest zmiana z jednej developer do innego</span><span class="sxs-lookup"><span data-stu-id="f4e42-138">The item ownership is changing from one developer to another</span></span>
- <span data-ttu-id="f4e42-139">Element przypadkowo została opublikowana przy użyciu nieprawidłowego konta</span><span class="sxs-lookup"><span data-stu-id="f4e42-139">The item was accidentally published using the wrong account</span></span>


## <a name="orphaned-items"></a><span data-ttu-id="f4e42-140">Elementy oddzielone</span><span class="sxs-lookup"><span data-stu-id="f4e42-140">Orphaned Items</span></span>

<span data-ttu-id="f4e42-141">Wystąpił jeden ostatni scenariusz, ale nie wiele razy.</span><span class="sxs-lookup"><span data-stu-id="f4e42-141">One last scenario has occurred, but not many times.</span></span>
<span data-ttu-id="f4e42-142">Elementy stały się porzucone, a tylko konta właściciela elementu nie można dodać nowego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f4e42-142">Items have become orphans and the only item owner account cannot be used to add new owners.</span></span>
<span data-ttu-id="f4e42-143">Oto kilka przykładów tego scenariusza:</span><span class="sxs-lookup"><span data-stu-id="f4e42-143">Here are some examples of this scenario:</span></span>

- <span data-ttu-id="f4e42-144">Konto właściciela jest skojarzone z adresu e-mail, który już nie istnieje i użytkownik zapomniał hasła</span><span class="sxs-lookup"><span data-stu-id="f4e42-144">The owner's account is associated with an email address that no longer exists and the user has forgotten their password</span></span>
- <span data-ttu-id="f4e42-145">Zarejestrowany właściciel odejścia z firmy, która produkuje elementu i nie można nawiązać połączenia, aby zaktualizować własność elementu</span><span class="sxs-lookup"><span data-stu-id="f4e42-145">The registered owner has left the company that produces the item and cannot be reached to update the item ownership</span></span>
- <span data-ttu-id="f4e42-146">Z powodu błędu, który ma wpływ tylko na kilka elementów element jest z jakiegoś powodu ownerless w galerii</span><span class="sxs-lookup"><span data-stu-id="f4e42-146">Due to a bug that has only affected a handful of items, the item is somehow ownerless on the gallery</span></span>

<span data-ttu-id="f4e42-147">Administratorzy galerii programu PowerShell mają dostęp do zarządzania właścicielami łącze dla każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="f4e42-147">The PowerShell Gallery Administrators can access the 'Manage Owners' link for any item.</span></span>
<span data-ttu-id="f4e42-148">Jeśli jesteś właścicielem prawowitego elementu i nie może uzyskać dostępu do bieżącego właściciela uzyskują uprawnienia właściciela, użyj link "Zgłaszania nadużyć" w galerii nawiązać Administratorzy galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f4e42-148">If you are the rightful owner of a item and cannot reach the current owner to gain ownership permissions, then use the 'Report Abuse' link on the gallery to reach the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="f4e42-149">Firma Microsoft będzie korzystać procesu zweryfikowanie prawa własności elementu.</span><span class="sxs-lookup"><span data-stu-id="f4e42-149">We will then follow a process to verify your ownership of the item.</span></span>
<span data-ttu-id="f4e42-150">Czy możemy określić powinien być właścicielem elementu, możemy użyć łącza zarządzania właścicielami dla elementu, nad i wysłać zaproszenie do staje się właścicielem.</span><span class="sxs-lookup"><span data-stu-id="f4e42-150">If we determine you should be an owner of the item, we will use the 'Manage Owners' link for the item ourselves and send you the invite to become an owner.</span></span>
<span data-ttu-id="f4e42-151">Firma Microsoft będzie tylko w tym po zweryfikowaniu, że powinny być właścicielem, a dla tego procesu zależy od okoliczności.</span><span class="sxs-lookup"><span data-stu-id="f4e42-151">We will only do this after verifying that you should be an owner and the process for this varies by circumstances.</span></span>
<span data-ttu-id="f4e42-152">Często, aby znaleźć sposób, aby skontaktować się z właścicielem projektu używamy adres URL projektu do elementu, ale firma Microsoft może również używać Twitter, poczty E-mail lub w inny sposób kontaktu z działem właściciel projektu.</span><span class="sxs-lookup"><span data-stu-id="f4e42-152">Often times, we will use the item's Project URL to find a way to contact the project owner, but we may also use Twitter, Email, or other means for contacting the project owner.</span></span>