---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, programu powershell, polecenie cmdlet, galerii programu PowerShell
title: Zarządzanie właścicielami pakietu
ms.openlocfilehash: 5cf26a7195ac446177cbb7f3a055e8e0a78569cc
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004124"
---
# <a name="managing-package-owners"></a>Zarządzanie właścicielami pakietu

Własność pakietu w galerii programu PowerShell jest definiowany przez Wydawca pakietu do galerii.
Czasami te metadane musi być zarządzana poza publikowania początkowego pakietu, co oznacza, że metadane właściciel musi być modyfikowalny, gdy pakiet, sama nie jest.

Wszyscy właściciele pakietu są elementami równorzędnymi.
Oznacza to, że właścicielem dowolnego pakietu można opublikować nową wersję pakietu. Oznacza to również, że dowolnego pakietu właściciel będzie mógł usunąć innego właściciela pakietu.
Nie ma właściciela ma urząd więcej niż innych właścicieli.

## <a name="setting-a-packages-initial-owner"></a>Ustawienie pierwotny właściciel pakietu

Po opublikowaniu nowego pakietu do galerii programu PowerShell pierwotny właściciel jest zdefiniowana przez użytkownika, który opublikowany pakiet. Jest to określane przez którego interfejs API klucz został użyty w poleceniu cmdlet Publish-Module.

## <a name="adding-owners"></a>Dodawanie właścicieli

Gdy pakiet został opublikowany w galerii programu PowerShell, jest łatwo zaprosić dodatkowe użytkowników stają się właścicieli pakietu.

1. [Zaloguj się na](https://powershellgallery.com/users/account/LogOn) w galerii programu PowerShell przy użyciu konta, który jest bieżącym właścicielem pakietu.
2. Przejdź do strony pakietu za pomocą karty "Items", wyszukiwanie lub klikając swoją nazwę użytkownika, a następnie [ **Zarządzanie pakietami Moje**](https://www.powershellgallery.com/account/Packages).
3. Po zalogowaniu się jako właściciel pakietu, znajduje się zarządzania właścicielami link po lewej stronie kliknij pozycję.
4. Wprowadź nazwę użytkownika osoby, które chcesz dodać jako właściciela, a następnie kliknij przycisk "Dodaj".
5. Wiadomość e-mail zostanie przesłany do nowego współwłaściciel jako zaproszenie, aby stać się właścicielem pakietu.
6. Po użytkownik kliknie łącze, są one pełne współwłaściciel z pełną kontrolą nad pakietu, w tym możliwość usuwania innych użytkowników, jako właścicieli.

**Uwaga**: aż nowego właściciela potwierdzi własność, ich *nie będzie* wymieniony jako właściciel pakietu.
Podczas wyświetlania **zarządzania właścicielami** stronie zostanie wyświetlony wpis "oczekuje na zatwierdzenie" w bieżącym właścicieli.
Czy można usunąć zaproszenia; tak samo, jak można usuwać innych właścicieli.
Ten proces zaproszenia uniemożliwia użytkownikom błędnie dodawania innych użytkowników jako właścicieli swoich pakietów.

Należy pamiętać, że metadane "Autorzy" czysto dowolny tekst; tylko "właściciele" są kontrolowane.


## <a name="removing-owners"></a>Usuwanie właścicieli

Jeśli pakiet ma wielu właścicielom, a jeden musi zostać usunięte, proces jest prosty:

1. [Zaloguj się na](https://powershellgallery.com/users/account/LogOn) do galerii programu PowerShell przy użyciu konta, który jest bieżącym właścicielem pakietu;
2. Przejdź do strony pakietu, za pomocą karty pakietów, wyszukiwanie lub klikając swoją nazwę użytkownika i następnie [ **Zarządzanie pakietami Moje**](https://www.powershellgallery.com/account/Packages).
3. Po zalogowaniu się jako właściciel pakietu, po lewej stronie kliknij pozycję; znajduje się link zarządzania właścicielami
4. Kliknij link "remove" obok właściciela, który ma zostać usunięty.



## <a name="transferring-package-ownership"></a>Przenoszenia własności pakietu

Czasami uzyskujemy żądania pomocy technicznej, aby przenieść własność pakietu z jednego użytkownika do innej, ale prawie zawsze można zrobić to samodzielnie.
Przenoszenia własności z jednego użytkownika do innego jest po prostu kombinacją dwóch funkcji wymienionych powyżej.

1. Bieżący właściciel zaprasza nowemu użytkownikowi stają się współwłaściciela i nowy użytkownik akceptuje zaproszenie;
2. Nowy użytkownik usuwa stare użytkownika z listy właścicieli.

To żądanie stał się obszarze kilka formularze, ale proces działa tak samo.

- Własność pakietu uległ zmianie z jednej dla deweloperów do innego
- Pakiet został przypadkowej publikacji przy użyciu nieprawidłowego konta


## <a name="orphaned-packages"></a>Pakiety oddzielone

Wystąpił jeden ostatni scenariusz, ale nie wiele razy.
Pakiety stały porzucone i jedyne konto właściciela pakietu, nie można dodać nowego użytkownika.
Poniżej przedstawiono kilka przykładów tego scenariusza:

- Konto właściciela jest skojarzona z adresem e-mail, który już nie istnieje, a użytkownik zapomniał hasła
- Zarejestrowany właściciel opuścił firmę, który tworzy pakiet i nie można nawiązać połączenia, aby zaktualizować własność pakietu
- Ze względu na usterkę, która ma wpływ tylko na kilka pakietów pakiet jest z jakiegoś powodu ownerless w galerii

Administratorzy galerii programu PowerShell można uzyskać dostęp do łącza zarządzania właścicielami dla dowolnego pakietu.
Jeśli masz prawowitego właściciela pakietu i nie można osiągnąć bieżący właściciel do uzyskania uprawnień właściciela, użyj link "Zgłoś nadużycie" w galerii do osiągnięcia Administratorzy galerii programu PowerShell.
Firma Microsoft będzie następnie wykonaj proces zweryfikowanie Twojej własności pakietu.
Jeśli określamy, czy powinien być właścicielem pakietu, firma Microsoft będzie użyć łącza zarządzania właścicielami pakietu, osoby i wysłać Ci zaproszenie, aby stać się właścicielem.
Firma Microsoft będzie to zrobić tylko po zweryfikowaniu, że powinno być właścicielem, a ten proces zależy od okoliczności.
Często firma Microsoft będzie używany adres URL projektu pakietu w celu znalezienia sposób skontaktuj się z właścicielem projektu, ale firma Microsoft może również używać usługi Twitter, w wiadomości E-mail lub w inny sposób kontaktu z działem właściciel projektu.
