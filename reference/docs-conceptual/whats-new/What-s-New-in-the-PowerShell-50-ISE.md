---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: "Jakie s nowego w środowisku PowerShell 50 ISE"
ms.assetid: 38648d47-7c27-4b37-a40e-ad29948519c2
ms.openlocfilehash: 9fd25a4759602bebf2b5df2c17d0c816a15e5e2b
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="what39s-new-in-the-windows-powershell-ise"></a>Co&#39;s nowego w środowisku Windows PowerShell ISE
W tym temacie opisano nowe i zaktualizowane funkcje, które zostały wprowadzone w wersjach programu Windows PowerShell Integrated Scripting Environment (ISE).

## <a name="feature-description"></a>Opis funkcji
Windows PowerShell ISE to aplikacja hosta, która umożliwia zapis, uruchamianie i testowanie skryptów i modułów w środowisku graficznym i intuicyjne. Najważniejsze funkcje takie jak kolorowanie składni, karcie ukończenia, debugowania visual zgodności Unicode i Pomoc kontekstowa zapewniają bogate środowisko obsługi skryptów.

Omówienie programu Windows PowerShell ISE, zobacz [omówienie Windows PowerShell zintegrowane skryptów środowiska](https://technet.microsoft.com/library/3c1892c2-bf84-4cb6-af26-1f453be9e671).

## <a name="new-and-changed-functionality-in-windows-powershell-ise"></a>Nowe i zmienione funkcje w środowisku Windows PowerShell ISE
W poniższej tabeli przedstawiono nowe i zmienione funkcje w tej wersji programu Windows PowerShell ISE w programie Windows PowerShell.

|Funkcja|Windows PowerShell ISE 4.0|Windows PowerShell ISE 3.0|Windows PowerShell ISE 2.0|
|--------------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
|**[IntelliSense](#intellisense)**|X|X||
|**[Wstawki kodu programu](#snippets)**|X|X||
|**[Dodatkowe narzędzia](#add-on-tools)**|X|X||
|**[Menedżer ponownego uruchamiania i automatycznego zapisywania](#restart-manager-and-auto-save)**|X|X||
|**[Lista ostatnio używanych](#most-recently-used-list)**|X|X||
|**[W okienku konsoli](#console-pane)**|X|X||
|**[Przełączniki wiersza polecenia](#command-line-switches)**|X|X||
|**[Nowe funkcje edytora](#new-editor-features)**|X|X||
|**[Nowe okno podglądu pomocy](#new-help-viewer-window)**|X|X||
|**[Pokaż polecenia cmdlet](#show-command-cmdlet)**|X|X||

### <a name="intellisense"></a>IntelliSense
**Dodane w ISE 3.0**

IntelliSense to funkcja automatycznego uzupełniania pomocy, która jest częścią programu Windows PowerShell ISE. Funkcja IntelliSense wyświetla aktywne menu potencjalnie zgodnych poleceń cmdlet, parametry, wartości parametrów, plików lub folderów podczas pisania.

**Jakie korzyści zapewnia ta zmiana?**

Z dodatkiem IntelliSense łatwiej jest odnajdywanie poleceń cmdlet i składni, korzystając z programu Windows PowerShell ISE do tworzenia skryptów. Aby dowiedzieć się więcej środowiska Windows PowerShell, podczas tworzenia nowego skryptów umożliwia także programu Windows PowerShell ISE.

**Co się zmieniło stanie?**

Podczas wpisywania poleceń cmdlet programu Windows PowerShell ISE 3.0 lub nowszego, wyświetla przewijanego i aktywne menu, umożliwiając Przeglądaj i wybierz odpowiednie polecenia.

### <a name="snippets"></a>Wstawki kodu programu
**Dodane w ISE 3.0**

*Wstawki kodu programu* są krótkich fragmentów kodu programu Windows PowerShell, który można wstawić do skryptów tworzenia w środowisku Windows PowerShell ISE. Windows PowerShell ISE jest dostarczany z domyślnym zestawem fragmentów. Wstawki kodu programu można dodać za pomocą **nowy fragment** polecenia cmdlet podczas pracy w środowisku Windows PowerShell ISE.

**Jakie korzyści zapewnia ta zmiana?**

Przy użyciu fragmentów, można szybko utworzyć i tworzenia skryptów do automatyzacji środowiska.

**Co się zmieniło stanie?**

Umożliwia wstawki na w programie Windows PowerShell 3.0 lub nowszej, **Edytuj** menu, kliknij przycisk **Start wstawki**, lub naciśnij klawisz **Ctrl-J**.

### <a name="add-on-tools"></a>Dodatkowe narzędzia
**Dodane w programie PowerShell 3.0**

Windows PowerShell ISE obsługuje teraz dodatkowe narzędzia, które kontrolki Windows Presentation Foundation (WPF), które są dodawane przy użyciu modelu obiektów. Dodatkowe narzędzia mogą być wyświetlane jako pionowy czy poziomy okienko w konsoli. Wiele dodatków w okienku są wyświetlane jako formant z kartami. Można również dodać lub usunąć dodatkowe narzędzia, które są tworzone przez strony firmy Microsoft. Aby uzyskać więcej informacji o sposobie importowania lub usuń dodatkowe narzędzia, zobacz [operacje programu Windows PowerShell ISE](http://technet.microsoft.com/library/cc732148.aspx).

**Jakie korzyści zapewnia ta zmiana?**

Dodatki umożliwiają rozszerzanie i dostosowywanie programu Windows PowerShell ISE z narzędziami, które mogą poprawić obsługę skryptów lub dodać funkcje do programu Windows PowerShell ISE.

**Co się zmieniło stanie?**

Wyposażone w środowisku Windows PowerShell ISE 3.0 i nowszych **polecenia** dodatku. **Polecenia** dodatek umożliwia przeglądanie poleceń cmdlet i dostępu Pomoc na temat polecenia cmdlet side-by-side z **skryptu** i **konsoli** okienka.

Dodatkowe dodatki znajduje się za pomocą **witryny sieci Web otwórz dodatkowe narzędzia** na **dodatki** menu.

### <a name="restart-manager-and-auto-save"></a>Ponownie uruchom Menedżera i automatycznego zapisywania
**Dodane w programie PowerShell 3.0**

Windows PowerShell ISE teraz automatycznie zapisuje Otwórz skrypty co dwie minuty w innej lokalizacji.  Czy programu Windows PowerShell ISE przestanie działać, jeśli system operacyjny zostanie ponownie uruchomiony, po uruchomieniu programu Windows PowerShell ISE, odzyskuje skrypty, które były Otwórz podczas ostatniej sesji, nawet jeśli skrypty nie zostały zapisane.

Aby zmienić interwał automatycznego zapisywania, uruchom następujące polecenie, w okienku konsoli: **$psise. Options.AutoSaveMinuteInterval**.

**Jakie korzyści zapewnia ta zmiana?**

Teraz możesz pracować w środowisku Windows PowerShell ISE wiedząc, że Otwórz skrypty są automatycznie zapisywane w przypadku nieoczekiwane ponowne uruchomienie.

**Co się zmieniło stanie?**

Program Windows PowerShell ISE 2.0 nie jest zapisywany skrypty automatycznie w przypadku ponownego uruchomienia komputera.

### <a name="most-recently-used-list"></a>Lista ostatnio używanych
**Dodane w programie PowerShell 3.0**

Windows PowerShell ISE ma teraz listy ostatnio używanych plików. Po otwarciu pliku w środowisku Windows PowerShell ISE, plik zostanie dodany do listy ostatnio używanych na **pliku** menu.

Aby zmienić domyślną liczbę plików z listy ostatnio używanych, uruchom następujące polecenie, w okienku konsoli: **$psise. Options.MruCount**.

**Jakie korzyści zapewnia ta zmiana?**

Lista ostatnio używanych umożliwia teraz łatwo uzyskiwać dostęp do często używanych plików.

**Co się zmieniło stanie?**

Program Windows PowerShell ISE 2.0 nie ma listy ostatnio używanych.

### <a name="console-pane"></a>W okienku konsoli
**Dodane w programie PowerShell 3.0**

Oddzielne polecenia i okienka wyjściowego, które były dostępne w pierwszej wersji programu Windows PowerShell ISE zostały połączone w jednym okienku konsoli. W okienku konsoli jest podobnych funkcji i wyglądu do typowych konsoli środowiska Windows PowerShell, ale zawiera następujące ulepszenia (większość są opisane w tym temacie).

- Kolorowanie składni dla tekstu wejściowego (nie tekstu wyjściowego), w tym składni XML

- IntelliSense

- Parowanie nawiasów klamrowych

- Wskazanie błędu

- Pełna obsługa formatu Unicode

- **F1** pomocy kontekstowej

- **CTRL + F1** kontekstowa Pokaż — polecenie

- Złożonym i pomocy technicznej od prawej do lewej

- Obsługa czcionek

- Powiększenie

- Tryby wierszu wybierz i wybierz bloku

- Zachowania wpisaną zawartość w wierszu polecenia, po naciśnięciu **się** strzałkę, aby wyświetlić historię w konsoli programu

**Jakie korzyści zapewnia ta zmiana?**

Dodanie tych zmian w okienku konsoli udostępnia środowisko obsługi skryptów bardziej spójny z interfejsem konsoli.

**Co się zmieniło stanie?**

Program Windows PowerShell ISE 2.0 ma oddzielne polecenia i okienka wyjściowego.

### <a name="command-line-switches"></a>Przełączniki wiersza polecenia
**Dodane w programie PowerShell 3.0**

Jeśli w wierszu polecenia można uruchomić programu Windows PowerShell ISE (przez wpisanie **powershell_ise.exe**), można dodać następujących nowych przełączników wiersza polecenia.

- *-NoProfile*: uruchamia programu Windows PowerShell ISE bez uruchamiania **$profile**

- *-Help*: Wyświetla okna Pomoc

- *-mta*: uruchamia programu Windows PowerShell ISE w trybie apartment wielowątkowych. Domyślny tryb działania programu Windows PowerShell ISE jest tryb jednowątkowego apartamentu lub *- sta*.

**Jakie korzyści zapewnia ta zmiana?**

Dodanie tych przełączników wiersza polecenia umożliwia kontrolowanie środowisko, w którym działa program Windows PowerShell ISE.

**Co się zmieniło stanie?**

Program Windows PowerShell ISE 2.0 nie rozpoznaje te przełączniki wiersza polecenia.

### <a name="new-editor-features"></a>Nowe funkcje edytora
**Dodane w programie PowerShell 3.0**

Inne funkcje edycji programu Windows PowerShell ISE:

- **Kolorowanie składni XML**programu Windows PowerShell ISE teraz kolory składni XML w taki sam sposób jak kolory jego składnię Windows PowerShell.

- **Dopasowywanie nawiasu klamrowego** programu Windows PowerShell ISE zawiera nawias klamrowy dopasowywania i wyróżnianie i mogą być używane w następujący sposób: (na przykład za pomocą **przejdź do dopasowania** polecenia lub **Ctrl +]** lokalizuje zamykający nawias klamrowy, jeśli masz nawiasu otwierającego zaznaczona).

- **Wyświetlanie konspektu** okienko skryptu obsługuje tworzenie konspektu, co pozwala zwijanie lub rozwijanie fragmentów kodu, klikając przycisk plus lub minus zaloguje się na lewym marginesie. Można użyć nawiasów klamrowych lub **#region** i **#endregion** znaczniki, aby oznaczyć początek lub koniec zwijanej sekcji. Aby rozwinąć lub zwinąć wszystkich regionów, naciśnij klawisz **Ctrl + M**.

- **Przeciągnij i upuść edycji tekstu**programu Windows PowerShell ISE teraz obsługuje przeciągania i upuszczania, edycję tekstu. Można wybrać bloku tekstu i przeciągnij go do innej lokalizacji w edytorze lub konsoli przesunięcia. Przytrzymując klawisz Ctrl podczas przeciągania zaznaczonego tekstu po zwolnieniu przycisku myszy tekst jest kopiowana do nowej lokalizacji. W tej wersji programu Windows PowerShell ISE, jak również we wcześniejszej wersji programu Windows PowerShell ISE przeciągnij i upuść pliki na środowisku Windows PowerShell ISE, programu Windows PowerShell ISE otwartego pliku.

- **Przeanalizować wyświetlania błędów** błędy analizy są oznaczone czerwoną podkreślenia. Po umieszczeniu na wskazanych błąd, tekst etykietki narzędzia wyświetlany problem, który został znaleziony w kodzie.

- **Powiększenie** powiększenia konsoli "™ s zawartość można ustawić za pomocą suwaka powiększenia (w prawym dolnym rogu okna programu Windows PowerShell ISE) lub przez wprowadzenie polecenia **$psise.options.Zoom** w okienku konsoli.

- **Sformatowanego tekstu kopiowania i wklejania** kopiowania do Schowka w środowisku Windows PowerShell ISE zachowuje czcionki, rozmiaru i informacji o kolorze oryginalnego zaznaczenia.

- **Blokowanie wybór** można wybrać bloku tekstu przez trzymając wciśnięty klawisz ALT Zaznaczanie tekstu w okienku skryptów myszą lub naciśnięcie **Alt + Shift + Strzałka w**.

**Jakie korzyści zapewnia ta zmiana?**

Dodatkowe funkcje edycji zapewnić spójność i wydajne środowisko edycji.

**Co się zmieniło stanie?**

Te ulepszenia edycji nie jest obecny w programie Windows PowerShell ISE 2.0.

### <a name="new-help-viewer-window"></a>Nowe okno podglądu pomocy
**Dodane w programie PowerShell 3.0**

Jeśli naciśniesz **F1** gdy kursor jest w użyciu polecenia cmdlet lub mieć część polecenia cmdlet wyróżnione, nowy Podgląd pomocy otwiera Pomoc kontekstową o wyróżnione polecenie cmdlet. Aby wyświetlić Windows PowerShell o pomoc, wpisz **operatory** w okienku konsoli, a następnie naciśnij klawisz **F1**.

Przed użyciem tej funkcji, należy pobrać najnowszej wersji tematy Pomocy programu Windows PowerShell z witryny sieci Web firmy Microsoft. Pobieranie tematy pomocy najprostszą metodą jest uruchomienie **Update-Help** polecenia cmdlet w okienku konsoli w przypadku uruchamiania programu Windows PowerShell ISE jako administrator.

Gdzie można zmienić **F1** klucz wygląda, aby uzyskać pomoc. W **narzędzia**/**opcje** menu na **ustawienia ogólne** , w obszarze **inne ustawienia**, możesz zaznaczyć lub wyczyścić pole wyboru **Użyj lokalnej zawartości pomocy zamiast zawartości online**. Jeśli zaznaczone, klient wygląda w pobranej pomocy w folderze modułów pomocy polecenia cmdlet.  Jeśli pole wyboru jest wyczyszczone, klient wyszukuje w bibliotece TechNet programu pomocy polecenia cmdlet.

**Jakie korzyści zapewnia ta zmiana?**

Pomoc kontekstowa bez opuszczania z bieżącego polecenia cmdlet lub skryptu zapewnia bezproblemowe learning.

**Co się zmieniło stanie?**

Naciśnięcie klawisza F1 w poprzednich wersjach programu Windows PowerShell ISE otworzyć plik pomocy na komputerze lokalnym. W środowisku Windows PowerShell ISE 3.0 i nowszych zostanie otwarte okno zawiera pomoc dla polecenia cmdlet, które można wyszukiwać i można skonfigurować. Tego środowiska Pomoc jest nowego w środowisku Windows PowerShell ISE 3.0 i aktualizowalnej pomocy są nowe w programie Windows PowerShell 3.0.

### <a name="show-command-cmdlet"></a>Pokaż polecenia cmdlet
**Dodane w programie PowerShell 3.0**

**Pokaż polecenie** polecenie cmdlet umożliwia utworzenie lub uruchom polecenie cmdlet lub funkcja wypełniając formie graficznej. Formularz umożliwia użytkownikom pracy przy użyciu programu Windows PowerShell w środowisku graficznym. **Pokaż polecenia** również umożliwia zaawansowane twórcom skryptów do utworzenia szybkiego GUI opartych na środowisku Windows PowerShell.

**Jakie korzyści zapewnia ta zmiana?**

Za pomocą **Pokaż polecenia** w skryptach środowiska Windows PowerShell, można udostępnić użytkownikom środowisko graficzne, z którym są znane. **Pokaż polecenia** może również ułatwić użytkownikom wprowadzające informacje programu Windows PowerShell.

**Co się zmieniło stanie?**

Pokaż polecenia jest nowy Windows PowerShell ISE 3.0.

## <a name="see-also"></a>Zobacz też
Aby uzyskać więcej informacji o korzystaniu z programu Windows PowerShell ISE w programie Windows PowerShell zobacz następujące łącza.

- [Eksploracja Windows PowerShell zintegrowane środowisko obsługi skryptów](../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
- [ISE w witrynie TechNet Wiki](http://social.technet.microsoft.com/wiki/search/searchresults.aspx?q=ISE)
- [Centrum skryptów](http://technet.microsoft.com/scriptcenter/default)

