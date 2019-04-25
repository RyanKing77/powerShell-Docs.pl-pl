---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, programu powershell, polecenie cmdlet, galerii programu PowerShell
title: Zarządzanie właścicielami pakietu
ms.openlocfilehash: 5cf26a7195ac446177cbb7f3a055e8e0a78569cc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084151"
---
# <a name="managing-package-owners"></a><span data-ttu-id="78c06-103">Zarządzanie właścicielami pakietu</span><span class="sxs-lookup"><span data-stu-id="78c06-103">Managing package owners</span></span>

<span data-ttu-id="78c06-104">Własność pakietu w galerii programu PowerShell jest definiowany przez Wydawca pakietu do galerii.</span><span class="sxs-lookup"><span data-stu-id="78c06-104">Ownership of a package in the PowerShell Gallery is defined by who published the package to the gallery.</span></span>
<span data-ttu-id="78c06-105">Czasami te metadane musi być zarządzana poza publikowania początkowego pakietu, co oznacza, że metadane właściciel musi być modyfikowalny, gdy pakiet, sama nie jest.</span><span class="sxs-lookup"><span data-stu-id="78c06-105">Sometimes this metadata needs to be managed beyond the initial package publishing, which means the owner metadata needs to be mutable while the package itself is not.</span></span>

<span data-ttu-id="78c06-106">Wszyscy właściciele pakietu są elementami równorzędnymi.</span><span class="sxs-lookup"><span data-stu-id="78c06-106">All package owners are peers.</span></span>
<span data-ttu-id="78c06-107">Oznacza to, że właścicielem dowolnego pakietu można opublikować nową wersję pakietu.</span><span class="sxs-lookup"><span data-stu-id="78c06-107">This means any package owner can publish a new version of an package.</span></span> <span data-ttu-id="78c06-108">Oznacza to również, że dowolnego pakietu właściciel będzie mógł usunąć innego właściciela pakietu.</span><span class="sxs-lookup"><span data-stu-id="78c06-108">It also means that any package owner can remove any other package owner.</span></span>
<span data-ttu-id="78c06-109">Nie ma właściciela ma urząd więcej niż innych właścicieli.</span><span class="sxs-lookup"><span data-stu-id="78c06-109">No owner has more authority than other owners.</span></span>

## <a name="setting-a-packages-initial-owner"></a><span data-ttu-id="78c06-110">Ustawienie pierwotny właściciel pakietu</span><span class="sxs-lookup"><span data-stu-id="78c06-110">Setting a Package's Initial Owner</span></span>

<span data-ttu-id="78c06-111">Po opublikowaniu nowego pakietu do galerii programu PowerShell pierwotny właściciel jest zdefiniowana przez użytkownika, który opublikowany pakiet.</span><span class="sxs-lookup"><span data-stu-id="78c06-111">When a new package is published to PowerShell Gallery, the initial owner is defined by the user that published the package.</span></span> <span data-ttu-id="78c06-112">Jest to określane przez którego interfejs API klucz został użyty w poleceniu cmdlet Publish-Module.</span><span class="sxs-lookup"><span data-stu-id="78c06-112">This is determined by whose API key was used in the Publish-Module cmdlet.</span></span>

## <a name="adding-owners"></a><span data-ttu-id="78c06-113">Dodawanie właścicieli</span><span class="sxs-lookup"><span data-stu-id="78c06-113">Adding Owners</span></span>

<span data-ttu-id="78c06-114">Gdy pakiet został opublikowany w galerii programu PowerShell, jest łatwo zaprosić dodatkowe użytkowników stają się właścicieli pakietu.</span><span class="sxs-lookup"><span data-stu-id="78c06-114">Once a package has been published to the PowerShell Gallery, it's easy to invite additional users to become owners of a package.</span></span>

1. <span data-ttu-id="78c06-115">[Zaloguj się na](https://powershellgallery.com/users/account/LogOn) w galerii programu PowerShell przy użyciu konta, który jest bieżącym właścicielem pakietu.</span><span class="sxs-lookup"><span data-stu-id="78c06-115">[Log on](https://powershellgallery.com/users/account/LogOn) to the PowerShell Gallery with the account that is the current owner of a package.</span></span>
2. <span data-ttu-id="78c06-116">Przejdź do strony pakietu za pomocą karty "Items", wyszukiwanie lub klikając swoją nazwę użytkownika, a następnie [ **Zarządzanie pakietami Moje**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="78c06-116">Navigate to a package page using the 'Items' tab, searching, or clicking your username and then [**Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="78c06-117">Po zalogowaniu się jako właściciel pakietu, znajduje się zarządzania właścicielami link po lewej stronie kliknij pozycję.</span><span class="sxs-lookup"><span data-stu-id="78c06-117">When logged on as an package's owner, there is a 'Manage Owners' link on the left side to click.</span></span>
4. <span data-ttu-id="78c06-118">Wprowadź nazwę użytkownika osoby, które chcesz dodać jako właściciela, a następnie kliknij przycisk "Dodaj".</span><span class="sxs-lookup"><span data-stu-id="78c06-118">Enter the username of the person to add as an owner and click 'Add'.</span></span>
5. <span data-ttu-id="78c06-119">Wiadomość e-mail zostanie przesłany do nowego współwłaściciel jako zaproszenie, aby stać się właścicielem pakietu.</span><span class="sxs-lookup"><span data-stu-id="78c06-119">An email is then sent to the new co-owner, as an invitation to become an owner of a package.</span></span>
6. <span data-ttu-id="78c06-120">Po użytkownik kliknie łącze, są one pełne współwłaściciel z pełną kontrolą nad pakietu, w tym możliwość usuwania innych użytkowników, jako właścicieli.</span><span class="sxs-lookup"><span data-stu-id="78c06-120">Once that user clicks the link, they are a full co-owner with full control over a package, including the ability to remove other users as owners.</span></span>

<span data-ttu-id="78c06-121">**UWAGA**: Do momentu nowego właściciela potwierdzi własność, ich *nie będzie* wymieniony jako właściciel pakietu.</span><span class="sxs-lookup"><span data-stu-id="78c06-121">**NOTE**: Until the new owner confirms ownership, they *will not* be listed as an owner of a package.</span></span>
<span data-ttu-id="78c06-122">Podczas wyświetlania **zarządzania właścicielami** stronie zostanie wyświetlony wpis "oczekuje na zatwierdzenie" w bieżącym właścicieli.</span><span class="sxs-lookup"><span data-stu-id="78c06-122">When viewing the **Manage Owners** page, you will see a "pending approval" entry in the current owners.</span></span>
<span data-ttu-id="78c06-123">Czy można usunąć zaproszenia; tak samo, jak można usuwać innych właścicieli.</span><span class="sxs-lookup"><span data-stu-id="78c06-123">That invitation can be removed; just as other owners can be removed.</span></span>
<span data-ttu-id="78c06-124">Ten proces zaproszenia uniemożliwia użytkownikom błędnie dodawania innych użytkowników jako właścicieli swoich pakietów.</span><span class="sxs-lookup"><span data-stu-id="78c06-124">This process of invitations prevents users from falsely adding other users as owners of their packages.</span></span>

<span data-ttu-id="78c06-125">Należy pamiętać, że metadane "Autorzy" czysto dowolny tekst; tylko "właściciele" są kontrolowane.</span><span class="sxs-lookup"><span data-stu-id="78c06-125">Note that the "Authors" metadata is purely freeform text; only "Owners" are controlled.</span></span>


## <a name="removing-owners"></a><span data-ttu-id="78c06-126">Usuwanie właścicieli</span><span class="sxs-lookup"><span data-stu-id="78c06-126">Removing Owners</span></span>

<span data-ttu-id="78c06-127">Jeśli pakiet ma wielu właścicielom, a jeden musi zostać usunięte, proces jest prosty:</span><span class="sxs-lookup"><span data-stu-id="78c06-127">When a package has multiple owners and one needs to be removed, the process is simple:</span></span>

1. <span data-ttu-id="78c06-128">[Zaloguj się na](https://powershellgallery.com/users/account/LogOn) do galerii programu PowerShell przy użyciu konta, który jest bieżącym właścicielem pakietu;</span><span class="sxs-lookup"><span data-stu-id="78c06-128">[Log on](https://powershellgallery.com/users/account/LogOn) to PowerShell Gallery with the account that is the current owner of a package;</span></span>
2. <span data-ttu-id="78c06-129">Przejdź do strony pakietu, za pomocą karty pakietów, wyszukiwanie lub klikając swoją nazwę użytkownika i następnie [ **Zarządzanie pakietami Moje**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="78c06-129">Navigate to a package page using the Packages tab, searching, or clicking your username and then [**Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="78c06-130">Po zalogowaniu się jako właściciel pakietu, po lewej stronie kliknij pozycję; znajduje się link zarządzania właścicielami</span><span class="sxs-lookup"><span data-stu-id="78c06-130">When logged on as a package's owner, there is a 'Manage Owners' link on the left side to click;</span></span>
4. <span data-ttu-id="78c06-131">Kliknij link "remove" obok właściciela, który ma zostać usunięty.</span><span class="sxs-lookup"><span data-stu-id="78c06-131">Click the 'remove' link next to the owner to be removed.</span></span>



## <a name="transferring-package-ownership"></a><span data-ttu-id="78c06-132">Przenoszenia własności pakietu</span><span class="sxs-lookup"><span data-stu-id="78c06-132">Transferring Package Ownership</span></span>

<span data-ttu-id="78c06-133">Czasami uzyskujemy żądania pomocy technicznej, aby przenieść własność pakietu z jednego użytkownika do innej, ale prawie zawsze można zrobić to samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="78c06-133">We sometimes get support requests to transfer package ownership from one user to another, but you can almost always accomplish this yourself.</span></span>
<span data-ttu-id="78c06-134">Przenoszenia własności z jednego użytkownika do innego jest po prostu kombinacją dwóch funkcji wymienionych powyżej.</span><span class="sxs-lookup"><span data-stu-id="78c06-134">Transferring ownership from one user to another is simply a combination of the two features above.</span></span>

1. <span data-ttu-id="78c06-135">Bieżący właściciel zaprasza nowemu użytkownikowi stają się współwłaściciela i nowy użytkownik akceptuje zaproszenie;</span><span class="sxs-lookup"><span data-stu-id="78c06-135">The current owner invites the new user to become a co-owner and the new user accepts the invite;</span></span>
2. <span data-ttu-id="78c06-136">Nowy użytkownik usuwa stare użytkownika z listy właścicieli.</span><span class="sxs-lookup"><span data-stu-id="78c06-136">The new user removes the old user from the list of owners.</span></span>

<span data-ttu-id="78c06-137">To żądanie stał się obszarze kilka formularze, ale proces działa tak samo.</span><span class="sxs-lookup"><span data-stu-id="78c06-137">This request has come in under a couple forms but the process works the same.</span></span>

- <span data-ttu-id="78c06-138">Własność pakietu uległ zmianie z jednej dla deweloperów do innego</span><span class="sxs-lookup"><span data-stu-id="78c06-138">The package ownership is changing from one developer to another</span></span>
- <span data-ttu-id="78c06-139">Pakiet został przypadkowej publikacji przy użyciu nieprawidłowego konta</span><span class="sxs-lookup"><span data-stu-id="78c06-139">The package was accidentally published using the wrong account</span></span>


## <a name="orphaned-packages"></a><span data-ttu-id="78c06-140">Pakiety oddzielone</span><span class="sxs-lookup"><span data-stu-id="78c06-140">Orphaned Packages</span></span>

<span data-ttu-id="78c06-141">Wystąpił jeden ostatni scenariusz, ale nie wiele razy.</span><span class="sxs-lookup"><span data-stu-id="78c06-141">One last scenario has occurred, but not many times.</span></span>
<span data-ttu-id="78c06-142">Pakiety stały porzucone i jedyne konto właściciela pakietu, nie można dodać nowego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="78c06-142">Packages have become orphans and the only package owner account cannot be used to add new owners.</span></span>
<span data-ttu-id="78c06-143">Poniżej przedstawiono kilka przykładów tego scenariusza:</span><span class="sxs-lookup"><span data-stu-id="78c06-143">Here are some examples of this scenario:</span></span>

- <span data-ttu-id="78c06-144">Konto właściciela jest skojarzona z adresem e-mail, który już nie istnieje, a użytkownik zapomniał hasła</span><span class="sxs-lookup"><span data-stu-id="78c06-144">The owner's account is associated with an email address that no longer exists and the user has forgotten their password</span></span>
- <span data-ttu-id="78c06-145">Zarejestrowany właściciel opuścił firmę, który tworzy pakiet i nie można nawiązać połączenia, aby zaktualizować własność pakietu</span><span class="sxs-lookup"><span data-stu-id="78c06-145">The registered owner has left the company that produces the package and cannot be reached to update the package ownership</span></span>
- <span data-ttu-id="78c06-146">Ze względu na usterkę, która ma wpływ tylko na kilka pakietów pakiet jest z jakiegoś powodu ownerless w galerii</span><span class="sxs-lookup"><span data-stu-id="78c06-146">Due to a bug that has only affected a handful of packages, the package is somehow ownerless on the gallery</span></span>

<span data-ttu-id="78c06-147">Administratorzy galerii programu PowerShell można uzyskać dostęp do łącza zarządzania właścicielami dla dowolnego pakietu.</span><span class="sxs-lookup"><span data-stu-id="78c06-147">The PowerShell Gallery Administrators can access the 'Manage Owners' link for any package.</span></span>
<span data-ttu-id="78c06-148">Jeśli masz prawowitego właściciela pakietu i nie można osiągnąć bieżący właściciel do uzyskania uprawnień właściciela, użyj link "Zgłoś nadużycie" w galerii do osiągnięcia Administratorzy galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="78c06-148">If you are the rightful owner of a package and cannot reach the current owner to gain ownership permissions, then use the 'Report Abuse' link on the gallery to reach the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="78c06-149">Firma Microsoft będzie następnie wykonaj proces zweryfikowanie Twojej własności pakietu.</span><span class="sxs-lookup"><span data-stu-id="78c06-149">We will then follow a process to verify your ownership of the package.</span></span>
<span data-ttu-id="78c06-150">Jeśli określamy, czy powinien być właścicielem pakietu, firma Microsoft będzie użyć łącza zarządzania właścicielami pakietu, osoby i wysłać Ci zaproszenie, aby stać się właścicielem.</span><span class="sxs-lookup"><span data-stu-id="78c06-150">If we determine you should be an owner of the package, we will use the 'Manage Owners' link for the package ourselves and send you the invite to become an owner.</span></span>
<span data-ttu-id="78c06-151">Firma Microsoft będzie to zrobić tylko po zweryfikowaniu, że powinno być właścicielem, a ten proces zależy od okoliczności.</span><span class="sxs-lookup"><span data-stu-id="78c06-151">We will only do this after verifying that you should be an owner and the process for this varies by circumstances.</span></span>
<span data-ttu-id="78c06-152">Często firma Microsoft będzie używany adres URL projektu pakietu w celu znalezienia sposób skontaktuj się z właścicielem projektu, ale firma Microsoft może również używać usługi Twitter, w wiadomości E-mail lub w inny sposób kontaktu z działem właściciel projektu.</span><span class="sxs-lookup"><span data-stu-id="78c06-152">Often times, we will use the package's Project URL to find a way to contact the project owner, but we may also use Twitter, Email, or other means for contacting the project owner.</span></span>
