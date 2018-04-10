---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeria, programu powershell, polecenia cmdlet, psgallery
title: Element Zarządzanie właścicielami
ms.openlocfilehash: e550b74ebde00cfbb154dbf4fb1fa4ae0582e029
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="managing-item-owners"></a>Element Zarządzanie właścicielami

Własność elementu w galerii programu PowerShell jest zdefiniowana przez wydawca elementu w galerii.
Czasami metadanych musi być zarządzany poza publikowanie początkowego elementu, co oznacza, że metadane właściciela musi być modyfikowalną podczas elementu nie jest.

Wszystkich właścicieli elementu są elementami równorzędnymi.
Oznacza to, że wszystkie właściciel elementu można opublikować nową wersję elementu. Oznacza to również usunąć inne właściciel elementu żadnych właściciel elementu.
Właściciel nie ma urząd więcej niż inne właścicieli.

## <a name="setting-an-items-initial-owner"></a>Ustawienie właściciel początkowy elementu

Po opublikowaniu nowego elementu galerii programu PowerShell pierwotny właściciel jest zdefiniowana przez użytkownika, która wydała elementu. Jest to określane przez interfejs API którego klucz był używany w poleceniu cmdlet Publish-Module.

## <a name="adding-owners"></a>Dodawanie właścicieli

Po opublikowaniu elementu w galerii programu PowerShell, jest bardzo proste zaprosić dodatkowym użytkownikom stają się właścicieli elementu.

1. [Zaloguj się na](https://powershellgallery.com/users/account/LogOn) do galerii programu PowerShell przy użyciu konta, który jest bieżącym właścicielem elementu.
2. Przejdź do strony elementu przy użyciu karty "Elementy", wyszukiwanie lub kliknięcie nazwy użytkownika, a następnie [ **Zarządzanie Moje elementy**](https://www.powershellgallery.com/account/Packages).
3. Po zalogowaniu się jako właściciel elementu, brak zarządzania właścicielami link po lewej stronie kliknij.
4. Wprowadź nazwę użytkownika osoby, które chcesz dodać jako właściciela, a następnie kliknij przycisk "Dodaj".
5. Wiadomość e-mail zostanie przesłany do nowego współwłaściciel jako zaproszenie do staje się właścicielem elementu.
6. Gdy użytkownik kliknie łącze, są pełne współwłaściciel pełną kontrolę nad elementem, w tym możliwość usunięcia innym użytkownikom jako właścicieli.

**Uwaga**: dopóki nowy właściciel potwierdzi własność, ich *nie* był wyświetlany jako właściciel elementu.
Podczas wyświetlania **zarządzania właścicielami** strony, zobaczysz wpis "oczekuje na zatwierdzenie" w bieżącym właścicieli.
Czy można usunąć zaproszenia; Podobnie jak inne właściciele mogą zostać usunięte.
Ten proces zaproszenia uniemożliwia użytkownikom fałszywie Dodawanie innym użytkownikom jako właściciele ich elementów.

Należy pamiętać, że metadane "Autorzy" czysto dowolny tekst; tylko "właściciele" są kontrolowane.


## <a name="removing-owners"></a>Usuwanie właścicieli
Gdy element ma wiele właścicieli i jeden musi zostać usunięte, proces jest prosty:

1. [Zaloguj się na](https://powershellgallery.com/users/account/LogOn) do galerii programu PowerShell przy użyciu konta, który jest bieżącym właścicielem elementu;
2. Przejdź do strony elementu przy użyciu karty elementów, wyszukiwanie lub kliknięcie nazwy użytkownika, a następnie [ **Zarządzanie Moje elementy**](https://www.powershellgallery.com/account/Packages).
3. Po zalogowaniu się jako właściciel elementu, jest łączem zarządzania właścicielami po lewej stronie kliknij;
4. Kliknij łącze "Usuń" obok właściciel ma zostać usunięty.



## <a name="transferring-item-ownership"></a>Przeniesieniem własności elementu
Czasami uzyskujemy żądania pomocy technicznej do przeniesienia elementu własności od jednego użytkownika do drugiego, ale prawie zawsze można wykonać to samodzielnie.
Przesyłania własność z jednego użytkownika to po prostu kombinacja dwie funkcje powyżej.

1. Bieżący właściciel zaprasza nowego użytkownika, który staje się właścicielem wspólnej i nowy użytkownik akceptuje zaproszenie;
2. Nowy użytkownik usuwa stare użytkownika z listy właścicieli.

To żądanie trybu obszarze kilka formularze, ale proces działa tak samo.

* Własność elementu jest zmiana z jednej developer do innego
* Element przypadkowo została opublikowana przy użyciu nieprawidłowego konta


## <a name="orphaned-items"></a>Elementy oddzielone
Wystąpił jeden ostatni scenariusz, ale nie wiele razy.
Elementy stały się porzucone, a tylko konta właściciela elementu nie można dodać nowego użytkownika.
Oto kilka przykładów tego scenariusza:

* Konto właściciela jest skojarzone z adresu e-mail, który już nie istnieje i użytkownik zapomniał hasła
* Zarejestrowany właściciel odejścia z firmy, która produkuje elementu i nie można nawiązać połączenia, aby zaktualizować własność elementu
* Z powodu błędu, który ma wpływ tylko na kilka elementów element jest z jakiegoś powodu ownerless w galerii

Administratorzy galerii programu PowerShell mają dostęp do zarządzania właścicielami łącze dla każdego elementu.
Jeśli jesteś właścicielem prawowitego elementu i nie może uzyskać dostępu do bieżącego właściciela uzyskują uprawnienia właściciela, użyj link "Zgłaszania nadużyć" w galerii nawiązać Administratorzy galerii programu PowerShell.
Firma Microsoft będzie korzystać procesu zweryfikowanie prawa własności elementu.
Czy możemy określić powinien być właścicielem elementu, możemy użyć łącza zarządzania właścicielami dla elementu, nad i wysłać zaproszenie do staje się właścicielem.
Firma Microsoft będzie tylko w tym po zweryfikowaniu, że powinny być właścicielem, a dla tego procesu zależy od okoliczności.
Często, aby znaleźć sposób, aby skontaktować się z właścicielem projektu używamy adres URL projektu do elementu, ale firma Microsoft może również używać Twitter, poczty E-mail lub w inny sposób kontaktu z działem właściciel projektu.