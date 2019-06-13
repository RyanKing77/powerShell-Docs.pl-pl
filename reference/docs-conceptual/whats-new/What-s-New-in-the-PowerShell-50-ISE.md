---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Jakie s Nowość w programie PowerShell 50 środowiska ISE
ms.openlocfilehash: 52e8926a7320f86f2ab8970a7778faba6a14a714
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030033"
---
# <a name="what39s-new-in-the-windows-powershell-ise"></a>Co&#39;s Nowość w środowisku Windows PowerShell ISE
W tym temacie opisano nowe i zaktualizowane funkcje, które zostały wprowadzone w wersjach programu Windows PowerShell zintegrowane Scripting Environment (ISE).

## <a name="feature-description"></a>Opis funkcji
W środowisku Windows PowerShell ISE jest aplikacją hosta, która pozwala na zapis, uruchamianie i testowanie skryptów i modułów w środowisku graficznym i intuicyjne. Najważniejsze funkcje, takie jak kolorowanie składni karcie zakończenia, debugowania visual, zgodności Unicode i Pomoc kontekstowa zapewniają bogate środowisko obsługi skryptów.

Omówienie programu Windows PowerShell ISE, zobacz [Przegląd Windows PowerShell zintegrowane Scripting środowisko](https://technet.microsoft.com/library/3c1892c2-bf84-4cb6-af26-1f453be9e671).

## <a name="new-and-changed-functionality-in-windows-powershell-ise"></a>Nowe i zmienione funkcje w środowisku Windows PowerShell ISE
W poniższej tabeli wymieniono nowe i zmienione funkcje w tej wersji programu Windows PowerShell ISE w programie Windows PowerShell.

|Funkcja|Windows PowerShell ISE 4.0|Windows PowerShell ISE 3.0|Windows PowerShell ISE 2.0|
|--------------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
|**[IntelliSense](#intellisense)**|X|X||
|**[Fragmenty kodu](#snippets)**|X|X||
|**[Dodatkowe narzędzia](#add-on-tools)**|X|X||
|**[Menedżera ponownego uruchamiania i automatycznego zapisywania](#restart-manager-and-auto-save)**|X|X||
|**[Listy ostatnio używanych](#most-recently-used-list)**|X|X||
|**[Console Pane](#console-pane)**|X|X||
|**[Przełączniki wiersza polecenia](#command-line-switches)**|X|X||
|**[Nowe funkcje edytora](#new-editor-features)**|X|X||
|**[Nowe okno podglądu pomocy](#new-help-viewer-window)**|X|X||
|**[Pokaż polecenia cmdlet](#show-command-cmdlet)**|X|X||

### <a name="intellisense"></a>IntelliSense
**Dodane w środowisku ISE 3.0**

Funkcja IntelliSense jest to funkcja automatycznego uzupełniania, pomoc, która jest częścią środowiska Windows PowerShell ISE. Funkcja IntelliSense wyświetla aktywne menu potencjalnie zgodnych poleceń cmdlet, parametry, wartości parametrów, pliki lub foldery, podczas wpisywania.

**Jakie korzyści zapewnia ta zmiana?**

Dzięki dodaniu funkcji IntelliSense łatwiej jest odnajdywanie poleceń cmdlet i składnię, gdy używasz programu Windows PowerShell ISE do tworzenia skryptów. Aby dowiedzieć się więcej środowiska Windows PowerShell, gdy tworzysz nowe skrypty umożliwia także środowiska Windows PowerShell ISE.

**Co się zmieniło stanie?**

Po wpisaniu polecenia cmdlet programu Windows PowerShell ISE 3.0 lub nowszego, wyświetla przewijany i Zwiększyliśmy menu, co pozwala przeglądać i wybrać odpowiednie polecenia.

### <a name="snippets"></a>Fragmenty kodu
**Dodane w środowisku ISE 3.0**

*Fragmenty kodu* krótki sekcje kodu programu Windows PowerShell, który można wstawić do skryptów tworzenia w środowisku Windows PowerShell ISE. Windows PowerShell ISE jest dostarczany z domyślny zestaw fragmentów. Fragmenty kodu można dodać za pomocą **nowy fragment** polecenia cmdlet podczas pracy w środowisku Windows PowerShell ISE.

**Jakie korzyści zapewnia ta zmiana?**

Za pomocą fragmentów kodu, możesz szybko tworzyć i tworzenia skryptów w celu zautomatyzowania środowiska.

**Co się zmieniło stanie?**

Do na używanie fragmentów kodu w programie Windows PowerShell 3.0 lub nowszej, **Edytuj** menu, kliknij przycisk **Start fragmenty**, lub naciśnij **Ctrl-J**.

### <a name="add-on-tools"></a>Dodatkowe narzędzia
**Dodane w programie PowerShell 3.0**

Windows PowerShell ISE obsługuje teraz dodatku Narzędzia, które są kontrolek Windows Presentation Foundation (WPF), które są dodawane przy użyciu modelu obiektu. Dodatkowe narzędzia może być wyświetlany jako poziomy lub pionowy okienko w konsoli. Wiele narzędzia dodatków w okienku są wyświetlane jako kontrolka z kartami. Można również dodać lub usunąć dodatkowe narzędzia, które są produkowane przez firmy inne niż Microsoft. Aby uzyskać więcej informacji o sposobie importowania lub usuń dodatkowe narzędzia, zobacz [operacji programu Windows PowerShell ISE](https://technet.microsoft.com/library/cc732148.aspx).

**Jakie korzyści zapewnia ta zmiana?**

Dodatki umożliwiają rozszerzanie i dostosowywanie środowiska Windows PowerShell ISE z narzędziami, które mogą poprawić środowisko obsługi skryptów lub dodać funkcje do programu Windows PowerShell ISE.

**Co się zmieniło stanie?**

Dołączono do programu Windows PowerShell ISE 3.0 ani nowszych **polecenia** dodatku. **Polecenia** dodatku pozwala na przeglądanie poleceń cmdlet i dostęp do uzyskania pomocy dotyczącej poleceń cmdlet side-by-side przy użyciu **skryptu** i **konsoli** okienka.

Dodatkowe dodatki można znaleźć przy użyciu **Open dodatku Narzędzia witryny sieci Web** polecenie **dodatki** menu.

### <a name="restart-manager-and-auto-save"></a>Ponownie uruchom Menedżera i automatycznego zapisywania
**Dodane w programie PowerShell 3.0**

Windows PowerShell ISE teraz automatycznie zapisuje Otwórz skrypty co dwie minuty w innej lokalizacji.  Czy program Windows PowerShell ISE przestaje działać, jeśli system operacyjny zostanie ponownie uruchomiony, po ponownym uruchomieniu programu Windows PowerShell ISE, odzyskuje skrypty, które były Otwórz ostatniej sesji, nawet jeśli skrypty nie zostały zapisane.

Aby zmienić interwał zapisywanie automatycznego, uruchom następujące polecenie, w okienku konsoli: **$psise. Options.AutoSaveMinuteInterval**.

**Jakie korzyści zapewnia ta zmiana?**

Teraz możesz pracować w ramach programu Windows PowerShell ISE, wiedząc, Otwórz skrypty są automatycznie zapisywane w przypadku nieoczekiwanego ponownego uruchomienia.

**Co się zmieniło stanie?**

Windows PowerShell ISE 2.0 nie są zapisywane skrypty automatycznie w przypadku ponownego uruchomienia komputera.

### <a name="most-recently-used-list"></a>Listy ostatnio używanych
**Dodane w programie PowerShell 3.0**

Windows PowerShell ISE ma teraz na liście ostatnio używanych plików. Po otwarciu pliku w środowisku Windows PowerShell ISE, plik zostanie dodany do listy ostatnio używanych na **pliku** menu.

Aby zmienić domyślną liczbę plików na liście ostatnio używanych, uruchom następujące polecenie, w okienku konsoli: **$psise. Options.MruCount**.

**Jakie korzyści zapewnia ta zmiana?**

Lista ostatnio używanych umożliwia teraz łatwo uzyskiwać dostęp do często używanych plików.

**Co się zmieniło stanie?**

Windows PowerShell ISE 2.0 nie ma listy ostatnio używanych.

### <a name="console-pane"></a>W okienku konsoli
**Dodane w programie PowerShell 3.0**

Osobne polecenie i okienka danych wyjściowych, które były dostępne w pierwszej wersji programu Windows PowerShell ISE zostały połączone w jednym okienku konsoli. W okienku konsoli jest podobny w funkcji i wygląd typowe konsoli środowiska Windows PowerShell, ale obejmuje następujące ulepszenia (większość są opisane w tym temacie).

- Kolorowanie składni dla tekstu wejściowego (nie tekst danych wyjściowych), w tym składni XML

- IntelliSense

- Parowanie nawiasów klamrowych

- Wskazanie błędu

- Pełna obsługa formatu Unicode

- **F1** pomocy kontekstowej

- **CTRL + F1** kontekstową polecenia Show

- Skryptów złożonych i pomoc techniczna od prawej do lewej

- Obsługa czcionek

- Powiększenie

- Wybierz wiersz i zaznaczania bloku

- Zachowywanie wpisaną zawartość w wierszu polecenia, po naciśnięciu klawisza **się** strzałkę, aby wyświetlić historię w konsoli programu

**Jakie korzyści zapewnia ta zmiana?**

Dodanie tych zmian w okienku konsoli udostępnia środowisko obsługi skryptów bardziej spójny z interfejsem konsoli.

**Co się zmieniło stanie?**

Windows PowerShell ISE 2.0 zawiera osobne polecenie i okienka danych wyjściowych.

### <a name="command-line-switches"></a>Przełączniki wiersza polecenia
**Dodane w programie PowerShell 3.0**

Jeśli program Windows PowerShell ISE można uruchomić z wiersza polecenia (przez wpisanie **powershell_ise.exe**), można dodać następujących nowych przełączników wiersza polecenia.

- *-NoProfile*: Uruchamia program Windows PowerShell ISE bez uruchamiania **$profile**

- *-Help*: Wyświetla okno pomocy

- *-mta*: Windows PowerShell ISE jest uruchamiany w trybie apartamentu wielowątkowych. Domyślny tryb działania w środowisku Windows PowerShell ISE jest w trybie jednowątkowego apartamentu lub *- sta*.

**Jakie korzyści zapewnia ta zmiana?**

Dodanie tych przełączników wiersza polecenia umożliwia kontrolowanie środowiska, w którym działa program Windows PowerShell ISE.

**Co się zmieniło stanie?**

Windows PowerShell ISE 2.0 nie rozpoznaje te przełączniki wiersza polecenia.

### <a name="new-editor-features"></a>Nowe funkcje edytora
**Dodane w programie PowerShell 3.0**

Inne funkcje edycji programu Windows PowerShell ISE:

- **Kolorowanie składni XML**środowiska Windows PowerShell ISE teraz kolorów składni XML w taki sam sposób, zgodnie z jego kolory składni programu Windows PowerShell.

- **Parowanie nawiasów klamrowych** środowiska Windows PowerShell ISE obejmuje parowanie nawiasów klamrowych i wyróżnianie i mogą być używane w następujący sposób: (na przykład za pomocą **przejdź do dopasowania** polecenia lub **Ctrl +]** lokalizuje zamykający nawias klamrowy, jeśli masz wybrane nawiasu otwierającego).

- **Wyświetlanie konspektu** okienko skryptu obsługuje tworzenie konspektu, co umożliwia zwijanie i rozwijanie fragmentów kodu, klikając przycisk plus lub minus loguje się na lewym marginesie. Możesz użyć nawiasów klamrowych lub **#region** i **#endregion** tagów do oznaczania początku lub końcu zwijanej sekcji. Aby rozwinąć lub zwinąć we wszystkich regionach, naciśnij klawisz **Ctrl + M**.

- **Przeciąganie i upuszczanie edycji tekstu**programu Windows PowerShell ISE teraz obsługuje przeciągnij i upuść edycji tekstu. Można wybrać żadnych blok tekstu i przeciągnij go do innej lokalizacji w edytorze lub konsoli, aby przenieść tekstu. Po przytrzymaniu wciśniętego klawisza Ctrl podczas przeciągania zaznaczonego tekstu po zwolnieniu przycisku myszy tekst jest kopiowana do nowej lokalizacji. W tej wersji programu Windows PowerShell ISE, a także poprzednią wersję programu Windows PowerShell ISE gdy przeciągnij i upuść pliki na środowisku Windows PowerShell ISE programu Windows PowerShell ISE otwiera plik.

- **Analizowanie błędów** błędy analizy są wskazane czerwonym podkreśleniem. Po umieszczeniu wskazany błąd tekst etykietki narzędzia wyświetla ten problem, który został znaleziony w kodzie.

- **Powiększenie** procent powiększenia zawartości konsoli można ustawić za pomocą suwaka powiększenia (w prawym dolnym rogu okna środowiska Windows PowerShell ISE) lub przez wprowadzenie polecenia **$psise.options.Zoom** w okienku konsoli.

- **Kopiuj tekst sformatowany i Wklej** kopiowania do Schowka w środowisku Windows PowerShell ISE zachowuje czcionkę, rozmiar i kolor informacji oryginalnego zaznaczenia.

- **Zaznaczenie blokowe** blok tekstu można wybrać, przytrzymując naciśnięty klawisz ALT podczas zaznaczania tekstu w okienku skryptów przy użyciu myszy lub naciskając **Alt + Shift + Strzałka**.

**Jakie korzyści zapewnia ta zmiana?**

Dodatkowe funkcje edycji zapewniają spójniejszą i bardziej zaawansowane środowisko edycji.

**Co się zmieniło stanie?**

Te ulepszenia edycji nie był obecny w programie Windows PowerShell ISE 2.0.

### <a name="new-help-viewer-window"></a>Nowe okno podglądu pomocy
**Dodane w programie PowerShell 3.0**

Jeśli użytkownik naciśnie klawisz **F1** gdy kursor jest w poleceniu cmdlet lub mieć część polecenia cmdlet wyróżniony, nowy Podgląd Pomocy otworzy kontekstowa pomoc na temat polecenia cmdlet wyróżnione. Aby wyświetlić Windows PowerShell o pomoc, wpisz **operatory** w okienku konsoli, a następnie naciśnij klawisz **F1**.

Przed użyciem tej funkcji Pobierz najnowszą wersję tematy Pomocy programu Windows PowerShell z witryny sieci Web firmy Microsoft. Najprostszą metodą pobierania tematy pomocy jest uruchomienie **Update-Help** polecenia cmdlet w okienku konsoli, podczas uruchamiania programu Windows PowerShell ISE jako administrator.

Można zmienić miejsce **F1** klucz wygląda w celu uzyskania pomocy. W **narzędzia**/**opcje** menu na **ustawienia ogólne** , w obszarze **inne ustawienia**, można ustawić lub wyczyścić Zaznacz pole wyboru **używać lokalnej zawartości pomocy zamiast zawartości online**. Jeśli zaznaczone, klient wygląda w pobranej pomocy w folderze modułów pomocy polecenia cmdlet.  Jeśli pole wyboru jest wyczyszczone, klient sprawdza w bibliotece TechNet programu pomocy dotyczącej poleceń cmdlet.

**Jakie korzyści zapewnia ta zmiana?**

Pomoc kontekstowa bez wychodzenia z bieżącego polecenia cmdlet lub skryptu zapewnia bezproblemowe uczenia.

**Co się zmieniło stanie?**

Naciśnięcie klawisza F1 w poprzednich wersjach programu Windows PowerShell ISE otwarty plik pomocy na komputerze lokalnym. W środowisku Windows PowerShell ISE 3.0 i nowszych zostanie otwarte okno zawiera pomoc dotyczącą polecenia cmdlet, które można wyszukiwać i konfigurowalne. To środowisko pomocy jest nowego w programie Windows PowerShell ISE 3.0 i aktualizowalnej pomocy jest nowego w programie Windows PowerShell 3.0.

### <a name="show-command-cmdlet"></a>Pokaż polecenia cmdlet
**Dodane w programie PowerShell 3.0**

**Polecenie Pokaż** polecenie cmdlet umożliwia tworzą lub uruchom polecenie cmdlet lub funkcji, wypełniając w formie graficznej. Formularz pozwala użytkownikom pracę przy użyciu programu Windows PowerShell w środowisku graficznym. **Polecenie Pokaż** również włącza zaawansowanych twórcom skryptów do tworzenia szybkich GUI opartych na środowisku Windows PowerShell.

**Jakie korzyści zapewnia ta zmiana?**

Za pomocą **polecenie Pokaż** w skryptach programu Windows PowerShell można udostępnić użytkownikom pśrodowisku graficznym, z którym są one znane. **Polecenie Pokaż** może również ułatwić użytkownikom wprowadzające, dowiedzieć się więcej środowiska Windows PowerShell.

**Co się zmieniło stanie?**

Polecenie Pokaż jest nowy Windows PowerShell ISE 3.0.

## <a name="see-also"></a>Zobacz też
Aby uzyskać więcej informacji o używaniu programu Windows PowerShell ISE w programie Windows PowerShell zobacz poniższe linki.

- [Eksplorowanie Windows PowerShell zintegrowane środowisko obsługi skryptów](../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
- [Środowiska ISE w witrynie TechNet Wiki](https://social.technet.microsoft.com/wiki/search/searchresults.aspx?q=ISE)
- [Centrum skryptów](https://technet.microsoft.com/scriptcenter/default)
