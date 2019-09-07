---
ms.date: 09/06/2019
keywords: PowerShell, polecenie cmdlet
title: Co nowego w programie PowerShell 5,0 ISE
ms.openlocfilehash: a719baef0da1600f0a5377e1b72c81b67e37eef2
ms.sourcegitcommit: a74ae7ed089301992fed201fbe55d827a622afa0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70746228"
---
# <a name="whats-new-in-the-windows-powershell-50-ise"></a>Co nowego w programie Windows PowerShell 5,0 ISE

W tym temacie objaśniono nowe i zaktualizowane funkcje, które zostały wprowadzone w wersjach środowiska Windows PowerShell Integrated Scripting Environment (ISE).

## <a name="feature-description"></a>Opis funkcji

Windows PowerShell ISE to aplikacja hosta, która umożliwia pisanie, uruchamianie i testowanie skryptów oraz modułów w graficznym i intuicyjnym środowisku. Kluczowe funkcje, takie jak kodowanie, uzupełnianie kart, debugowanie wizualizacji, zgodność ze standardem Unicode i pomoc kontekstową, zapewniają bogate środowisko tworzenia skryptów.

Aby uzyskać więcej informacji, zobacz [wprowadzenie Windows PowerShell ISE](../components/ise/Introducing-the-Windows-PowerShell-ISE.md).

W poniższej tabeli wymieniono nowe i zmienione funkcje tej wersji Windows PowerShell ISE w programie Windows PowerShell.

## <a name="intellisense"></a>IntelliSense

> Dodano w ISE 3,0

IntelliSense to funkcja automatycznego uzupełniania, która jest częścią Windows PowerShell ISE.
Funkcja IntelliSense wyświetla menu możliwe do kliknięcia, które mogą być dopasowane do poleceń cmdlet, parametrów, wartości parametrów, plików lub folderów podczas wpisywania.

**Jaką wartość ma dodać ta zmiana?**

Przy dodawaniu funkcji IntelliSense łatwiejsze jest odnajdywanie poleceń cmdlet i składni w przypadku używania Windows PowerShell ISE do tworzenia skryptów. Możesz również użyć Windows PowerShell ISE, aby poznać środowisko Windows PowerShell podczas tworzenia nowych skryptów.

**Co działa inaczej?**

Po wpisaniu poleceń cmdlet w Windows PowerShell ISE wyświetlane jest menu przewijane i możliwe do kliknięcia, umożliwiające przeglądanie i wybieranie odpowiednich poleceń.

## <a name="snippets"></a>Fragmenty kodu

> Dodano w ISE 3,0

*Fragmenty* kodu to krótkie sekcje programu Windows PowerShell Code, które można wstawić do skryptów tworzonych w Windows PowerShell ISE. Windows PowerShell ISE zawiera domyślny zestaw fragmentów kodu. Można dodać fragmenty kodu za pomocą `New-Snippet` polecenia cmdlet podczas pracy w Windows PowerShell ISE.

**Jaką wartość ma dodać ta zmiana?**

Za pomocą fragmentów kodu można szybko tworzyć i tworzyć skrypty do automatyzowania środowiska.

**Co działa inaczej?**

Aby użyć fragmentów kodu w programie Windows PowerShell 3,0 lub nowszym, w menu **Edycja** kliknij polecenie **Rozpocznij fragmenty kodu**lub naciśnij klawisz <kbd>Ctrl</kbd>+<kbd>J</kbd>.

## <a name="add-on-tools"></a>Narzędzia dodatków

> Dodano w programie PowerShell 3,0

Windows PowerShell ISE teraz obsługuje narzędzia dodatków przy użyciu modelu obiektów. Te dodatki są kontrolkami Windows Presentation Foundation (WPF), które są wyświetlane jako okienko pionowe lub poziome w konsoli programu. Wiele narzędzi dodatków w okienku jest wyświetlanych jako kontrolka z kartami. Możesz również dodawać lub usuwać narzędzia dodatków, które są tworzone przez strony inne niż firmy Microsoft. Aby uzyskać więcej informacji, zobacz [cel modelu obiektów skryptów Windows PowerShell ISE](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).

**Jaką wartość ma dodać ta zmiana?**

Dodatki umożliwiają rozszerzanie i dostosowywanie Windows PowerShell ISE za pomocą narzędzi, które dodają funkcje i wzbogacają obsługę skryptów.

**Co działa inaczej?**

Windows PowerShell ISE 3,0 i nowsze są dołączone do dodatku **Commands** . Dodatek **polecenia** umożliwia przeglądanie poleceń cmdlet i dostęp do pomocy dotyczącej poleceń cmdlet obok siebie przy użyciu okienek **skryptu** i **konsoli** .

Dodatkowe dodatki można znaleźć za pomocą polecenia **Otwórz witrynę internetową narzędzia dodatków** w menu **Dodatki** .

## <a name="restart-manager-and-auto-save"></a>Uruchom ponownie Menedżera i automatycznie Zapisz

> Dodano w programie PowerShell 3,0

Windows PowerShell ISE teraz automatycznie zapisuje otwarte skrypty co dwie minuty, w osobnej lokalizacji. Po ponownym uruchomieniu Windows PowerShell ISE po nieoczekiwanym awarii lub ponownym uruchomieniu program odzyskuje skrypty otwarte w ostatniej sesji, nawet jeśli skrypty nie zostały zapisane.

Aby zmienić interwał automatycznego zapisywania, uruchom następujące polecenie w okienku konsoli: `$psise.Options.AutoSaveMinuteInterval`.

**Jaką wartość ma dodać ta zmiana?**

Teraz możesz korzystać z Windows PowerShell ISE, wiedząc, że otwarte skrypty są zapisywane automatycznie.

**Co działa inaczej?**

Windows PowerShell ISE 2,0 nie zapisuje skryptów automatycznie.

## <a name="most-recently-used-list"></a>Lista ostatnio używanych

> Dodano w programie PowerShell 3,0

Windows PowerShell ISE teraz zawiera listę ostatnio używanych plików. Po otwarciu pliku w Windows PowerShell ISE, plik zostanie dodany do listy ostatnio używane w menu **plik** .

Aby zmienić domyślną liczbę plików na ostatnio używanej liście, uruchom następujące polecenie w okienku konsoli: `$psise.Options.MruCount`.

**Jaką wartość ma dodać ta zmiana?**

Teraz można korzystać z listy ostatnio używanych plików, aby łatwo uzyskać dostęp do często używanych danych.

**Co działa inaczej?**

Windows PowerShell ISE 2,0 nie ma ostatnio używanej listy.

## <a name="console-pane"></a>Okienko konsoli

> Dodano w programie PowerShell 3,0

Osobne okienka poleceń i danych wyjściowych, które były dostępne w pierwszej wersji Windows PowerShell ISE, zostały połączone w jednym okienku konsoli. Okienko konsoli jest podobne do funkcji i wyglądu typowej konsoli programu Windows PowerShell, ale zawiera następujące udoskonalenia:

- Kolorowanie składni dla tekstu wejściowego (nie tekstu wyjściowego), w tym składni XML
- IntelliSense
- Dopasowywanie nawiasów klamrowych
- Wskazanie błędu
- Pełna obsługa standardu Unicode
- <kbd>Klawisz F1</kbd> — pomoc kontekstowa
- <kbd></kbd>Ctrl+<kbd>F1</kbd> z kontekstem Pokaż polecenie
- Złożony skrypt i pomoc techniczna od prawej do lewej
- Obsługa czcionek
- Powiększenie
- Tryby wyboru wiersza i wyboru bloku
- Zachowywanie wpisanej zawartości w wierszu polecenia po naciśnięciu <kbd>strzałki</kbd> w celu wyświetlenia historii w konsoli

**Jaką wartość ma dodać ta zmiana?**

Dodanie tych zmian w okienku konsoli zapewnia obsługę skryptów, która jest bardziej spójna z interfejsem konsoli.

**Co działa inaczej?**

Windows PowerShell ISE 2,0 ma oddzielne okienka poleceń i danych wyjściowych.

## <a name="command-line-switches"></a>Przełączniki wiersza polecenia

> Dodano w programie PowerShell 3,0

Po rozpoczęciu Windows PowerShell ISE z wiersza polecenia (przez wpisanie **powershell_ise. exe**) można dodać następujące nowe przełączniki wiersza polecenia.

- `-NoProfile`: Uruchamia Windows PowerShell ISE bez uruchamiania`$profile`
- `-Help`: Wyświetla okno Pomoc
- `-mta`: Uruchamia Windows PowerShell ISE w trybie wielowątkowej komórki. Domyślny tryb operacji dla Windows PowerShell ISE jest trybem apartamentu jednowątkowego lub `-sta`.

**Jaką wartość ma dodać ta zmiana?**

Dodanie tych przełączników wiersza polecenia pozwala kontrolować środowisko, w którym działa Windows PowerShell ISE.

**Co działa inaczej?**

Windows PowerShell ISE 2,0 nie rozpoznaje tych przełączników wiersza polecenia.

## <a name="new-editor-features"></a>Nowe funkcje edytora

> Dodano w programie PowerShell 3,0

Inne funkcje edycji Windows PowerShell ISE obejmują:

- **Kolorowanie składni XML** — Windows PowerShell ISE teraz kolory składni XML w taki sam sposób jak składnia programu Windows PowerShell.
- **Dopasowywanie nawiasów klamrowych** — Windows PowerShell ISE obejmuje Dopasowywanie nawiasów klamrowych i wyróżnianie, a także może być używane w następujący sposób: (na przykład za pomocą polecenia **Przejdź do dopasowania** lub <kbd>klawisza Ctrl</kbd>+<kbd>)</kbd> lokalizuje zamykający nawias klamrowy, jeśli ma zaznaczone nawiasy otwierające).
- **Widok konspektu** Okienko skrypt obsługuje konspekt, który umożliwia zwijanie lub rozwijanie sekcji kodu przez kliknięcie znaku plus lub minus na lewym marginesie. Aby oznaczyć początek lub koniec sekcji zwijanej `#endregion` , można użyć nawiasów klamrowych lub `#region` tagów i. Aby rozwinąć lub zwinąć wszystkie regiony, naciśnij klawisz <kbd>Ctrl</kbd>+<kbd>M</kbd>.
- **Edytowanie tekstu metodą "przeciągnij i upuść** " — Windows PowerShell ISE teraz obsługuje edycję tekstu metodą "przeciągnij i upuść". Można wybrać dowolny blok tekstu i przeciągnąć ten tekst do innej lokalizacji w edytorze lub konsoli programu w celu przeniesienia tekstu. Jeśli przytrzymasz wciśnięty klawisz <kbd>Ctrl</kbd> podczas przeciągania zaznaczonego tekstu, po zwolnieniu przycisku myszy tekst zostanie skopiowany do nowej lokalizacji. W tej wersji Windows PowerShell ISE, gdy przeciągasz i upuszczasz pliki na Windows PowerShell ISE, Windows PowerShell ISE otwiera plik.
- **Wyświetlanie** błędów analizy — błędy analizy są oznaczone czerwonymi podkreśleniami. Po umieszczeniu wskaźnika myszy nad wskazanym błędem tekst etykietki narzędzia zawiera problem znaleziony w kodzie.
- **Powiększenie** — procent powiększenia zawartości konsoli można ustawić za pomocą suwaka powiększenia (w prawym dolnym rogu okna Windows PowerShell ISE) lub wprowadzając polecenie `$psise.options.Zoom` w okienku konsoli.
- **Kopiowanie tekstu sformatowanego i wklejanie** do schowka w Windows PowerShell ISE zachowuje czcionkę, rozmiar i informacje o kolorze oryginalnego zaznaczenia.
- **Zaznaczenie blokowe** — można wybrać blok tekstu, przytrzymując wciśnięty klawisz <kbd>Alt</kbd> podczas zaznaczania tekstu w okienku skrypt za pomocą myszy lub naciskając klawisz <kbd>Alt</kbd>+<kbd>SHIFT</kbd>+<kbd>strzałkę</kbd>.

**Jaką wartość ma dodać ta zmiana?**

Dodatkowe funkcje edycji zapewniają bardziej spójne i wydajne Edytowanie środowiska.

**Co działa inaczej?**

Te ulepszenia edycji nie były obecne w Windows PowerShell ISE 2,0.

## <a name="new-help-viewer-window"></a>Nowe okno podglądu pomocy

> Dodano w programie PowerShell 3,0

Jeśli naciśniesz klawisz <kbd>F1</kbd> , gdy kursor znajduje się w poleceniu cmdlet lub że masz część polecenia cmdlet, w nowym podglądzie pomocy zostanie otwarta pomoc kontekstowa o wyróżnionym poleceniu cmdlet. Aby wyświetlić **Informacje o** pomocy programu Windows PowerShell `operators` , wpisz w okienku konsoli, a następnie naciśnij klawisz <kbd>F1</kbd>.

Przed użyciem tej funkcji należy pobrać najnowszą wersję tematów pomocy programu Windows PowerShell z witryny sieci Web firmy Microsoft. Najprostszą metodą pobierania tematów pomocy jest uruchomienie `Update-Help` polecenia cmdlet w okienku konsoli programu podczas uruchamiania Windows PowerShell ISE jako administrator.

Można zmienić miejsce, w którym będzie wyglądał klawisz <kbd>F1</kbd> w celu uzyskania pomocy. W menu**Opcje** **narzędzi**/na karcie **Ustawienia ogólne** w obszarze **inne ustawienia**możesz ustawić lub wyczyścić pole wyboru **Użyj lokalnej zawartości pomocy zamiast zawartości online**. Po zaznaczeniu tej opcji klient szuka pomocy poleceń cmdlet w pobranej pomocy znalezionej w folderze moduły. Jeśli pole wyboru jest wyczyszczone, klient szuka pomocy w trybie online.

**Jaką wartość ma dodać ta zmiana?**

Pomoc kontekstowa bez opuszczania bieżącego polecenia cmdlet lub skryptu zapewnia zintegrowane środowisko szkoleniowe.

**Co działa inaczej?**

Naciśnij klawisz <kbd>F1</kbd> w poprzednich wersjach Windows PowerShell ISE otworzyć plik pomocy na komputerze lokalnym. W Windows PowerShell ISE 3,0 i nowszych zostanie otwarte okno zawierające pomoc dla polecenia cmdlet, które można wyszukiwać i konfigurować. To środowisko pomocy jest nowe dla Windows PowerShell ISE 3,0 i aktualizowalnej pomocy jest Nowość w programie Windows PowerShell 3,0.

## <a name="show-command-cmdlet"></a>Show-Command — polecenie cmdlet

> Dodano w programie PowerShell 3,0

`Show-Command` Polecenie cmdlet umożliwia tworzenie lub uruchamianie poleceń cmdlet lub funkcji przez wypełnienie formularza graficznego. Formularz umożliwia użytkownikom współpracę z programem Windows PowerShell w środowisku graficznym.
`Show-Command`umożliwia również zaawansowanym skryptom tworzenie szybkiego interfejsu GUI opartego na programie Windows PowerShell.

**Jaką wartość ma dodać ta zmiana?**

Korzystając `Show-Command` ze skryptów programu Windows PowerShell, możesz udostępnić użytkownikom środowisko graficzne, za pomocą którego są one znane. `Show-Command`może również pomóc użytkownikom wprowadzającym informacje w programie Windows PowerShell.

**Co działa inaczej?**

`Show-Command`jest nowym Windows PowerShell ISE 3,0.

## <a name="see-also"></a>Zobacz też

Aby uzyskać więcej informacji o korzystaniu z Windows PowerShell ISE, zobacz [Eksplorowanie środowiska Windows PowerShell Integrated Scripting Environment](../getting-started/fundamental/exploring-the-windows-powershell-ise.md).
