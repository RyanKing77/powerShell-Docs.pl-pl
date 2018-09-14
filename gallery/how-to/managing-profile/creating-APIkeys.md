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
# <a name="managing-api-keys"></a>Zarządzanie kluczami interfejsu API

Galeria programu PowerShell obsługuje tworzenie wielu kluczy interfejsu API do obsługuje szeroką gamę publikowania wymagania. Klucz interfejsu API można zastosować do co najmniej jeden pakiet, udziela określone uprawnienia i ma datę wygaśnięcia.

> [!IMPORTANT]
> Użytkownicy, którzy są publikowane w galerii programu PowerShell, przed wprowadzeniem o określonym zakresie klucze interfejsu API będzie mieć "pełnego dostępu do interfejsu API key". Klucze pełny dostęp nie mają poprawki zabezpieczeń wbudowanych w zakresie klucze interfejsu API. Klucze pełny dostęp do nigdy nie wygasa i Zastosuj do wszystkich posiadanych przez użytkownika. Jeśli usuniesz ten klucz, nie można utworzyć ponownie.

Na poniższej ilustracji przedstawiono opcje dostępne podczas tworzenia zakresu klucz interfejsu API.

![Tworzenie kluczy interfejsu API](../../Images/PSGallery_KeyScoped.png)

W tym przykładzie utworzyliśmy klucza interfejsu API o nazwie **AzureRMDataFactory**. Ta wartość klucza może służyć do wypychania pakietów, których nazwy zaczynają się od "AzureRM.DataFactory" i jest ważny przez 365 dni. Jest to typowy scenariusz, gdy różne zespoły w obrębie tej samej organizacji działają na różnych pakietach. Członkowie zespołu mają klucz, który przyznaje im uprawnienia dla określonego pakietu, które działają z.
Wartość wygaśnięcia uniemożliwia użycie starych lub zapomniane kluczy.

## <a name="using-glob-patterns"></a>Przy użyciu wzorców glob

Jeśli pracujesz na wielu pakietów, można użyć wzorców obsługi symboli wieloznacznych do dopasowania wielu pakietów jako grupa. Uprawnienia klucza interfejsu API dotyczą wszystkie nowe pakiety pasujących do wzorca glob. Na przykład w poprzednim przykładzie użyto **wzorzec Glob** wartość "AzureRM.DataFactory*". Możesz wypychać pakietu o nazwie "AzureRm.DataFactoryV2.Netcore" przy użyciu tego klucza, ponieważ pakiet jest zgodny ze wzorcem glob.

## <a name="create-api-keys-securely"></a>Bezpiecznie Utwórz klucze interfejsu API

Dla bezpieczeństwa nowo utworzoną wartość klucza nigdy nie są wyświetlane na ekranie i jest dostępna tylko z przycisku kopiowania, jak pokazano poniżej.

![Uzyskiwanie nową wartość klucza interfejsu API](../../Images/PSGallery_CopyCreatedKey.png)

> [!IMPORTANT]
> Wartość klucza interfejsu API można kopiować tylko natychmiast po utworzeniu, lub Odśwież go. Nie będą wyświetlane i nie będzie dostępny ponownie po odświeżeniu strony. Jeśli zgubisz wartości klucza, należy użyć Wygeneruj ponownie klucz i skopiuj klucz, po zostanie ponownie wygenerowany.

## <a name="key-permissions-and-expiration"></a>Uprawnienia klucza i wygaśnięcia

O określonym zakresie klucze interfejsu API można przypisać dowolny z następujących uprawnień:

- Wypychanie nowych pakietów
- Wypychanie nowych lub pakietów aktualizacji
- Wyrejestrowanie pakietów

Co nowego klucza ma wygaśnięcia. Wartość dla wygaśnięcia jest mierzony w dniach. Możliwe wartości dla wygaśnięcia to:

- 1 dzień
- 90 dni
- 180 dni
- 270 dni
- 365 dni (ustawienie domyślne)

Nie można zmienić tych ustawień, gdy klucz zostanie utworzony. Nie można utworzyć nowego klucza, który nigdy nie wygasa.

## <a name="editing-and-deleting-existing-api-keys"></a>Edytowanie i usuwanie istniejących kluczy interfejsu API

Można zmienić niektórych ustawień istniejącego klucza. Jak wspomniano wcześniej nie można zmodyfikować zakresu zabezpieczeń dla istniejącego klucza interfejsu API lub zmienić czas wygaśnięcia. Opcje mogły być zmieniane są wyświetlane w poniższy zrzut ekranu:

![Uzyskiwanie nową wartość klucza interfejsu API](../../Images/PSGallery_EditAPIKey.png)

Aby zmienić pakietów kontrolowane za pomocą klucza, można wybrać indywidualnych pakietów z listy lub zmień wzorzec glob.

Klikając **ponownie wygenerować** tworzy nową wartość klucza. Tak samo jak w przypadku początkowo utworzono klucz, należy najpierw **kopiowania** wartość klucza natychmiast po jego aktualizacji. **Kopiowania** opcja jest niedostępna, gdy opuścisz tę stronę.

Klikając **Usuń** zostanie wyświetlony komunikat potwierdzenia. Po usunięciu klucz będzie można jej używać.

## <a name="key-expiration"></a>Data wygaśnięcia klucza

Dziesięć dni przed wygaśnięciem, galerii programu PowerShell wysyła ostrzegawcza wiadomość e-mail właściciela konta, klucza interfejsu API. Po wygaśnięciu klucza jest bezużyteczny. Ostrzeżenie jest wyświetlane u góry strony zarządzania kluczami interfejsu API, które są wyświetlane klucze, które nie są już prawidłowe. Można wygenerować nową wartość klucza.
