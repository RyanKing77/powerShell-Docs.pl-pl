---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Ułatwienia dostępu w środowisku Windows PowerShell ISE
ms.assetid: a078f9d1-dd6b-4323-b16d-0622cd993aa8
ms.openlocfilehash: 78a001dbe43a0b005d10a817e05e4cc7a72f5bd0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058458"
---
# <a name="accessibility-in-windows-powershell-ise"></a>Ułatwienia dostępu w środowisku Windows PowerShell ISE

W tym temacie opisano funkcje ułatwień dostępu programu Windows PowerShell zintegrowane Scripting Environment (ISE), które mogą być przydatne.

* [Jak zmienić rozmiar i położenie konsoli i okienka skryptu](#how-to-change-the-size-and-location-of-the-console-and-script-panes)
* [Skróty klawiaturowe do edycji tekstu](#keyboard-shortcuts-for-editing-text)
* [Skróty klawiaturowe do uruchamiania skryptów](#keyboard-shortcuts-for-running-scripts)
* [Skróty klawiaturowe do dostosowywania widoku](#keyboard-shortcuts-for-customizing-the-view)
* [Skróty klawiaturowe dla debugowania skryptów](#keyboard-shortcuts-for-debugging-scripts)
* [Skróty klawiaturowe dla karty programu Windows PowerShell](#keyboard-shortcuts-for-windows-powershell-tabs)
* [Skróty klawiaturowe, uruchamianie i kończenie](#keyboard-shortcuts-for-starting-and-exiting)

Firma Microsoft dokłada wszelkich starań, aby jej produkty i usługi były coraz łatwiejsze w użytkowaniu. Poniższe tematy zawierają informacje o funkcjach, produktach i usługach powodujących, że program Windows PowerShell ISE bardziej dostępny dla osób niepełnosprawnych.

Windows PowerShell ISE obsługuje trybu wysokiego kontrastu. Dla niedowidzących punkt przerwania informacje są dostępne za pośrednictwem poleceń cmdlet do zarządzania punkty przerwania, takich jak [Get PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) i [PSBreakpoint zestaw](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420). Aby uzyskać więcej informacji, zobacz sekcję "Jak zarządzanie punktami przerwania" w [jak debugować skrypty w środowisku Windows PowerShell ISE](How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md). Oprócz funkcji ułatwień dostępu i narzędzi firmy Microsoft Windows następujące funkcje ułatwiają środowiska Windows PowerShell ISE dostęp dla osób niepełnosprawnych:

- Skróty klawiaturowe

- Tabela kolorowania składni i możliwość modyfikowania kilka innych ustawień kolorów przy użyciu [$psISE.Options](https://technet.microsoft.com/library/75e2a76f-f3d1-490b-ad5d-e3829946aabb) obiekt obsługi skryptów.

- Zmiana rozmiaru tekstu

## <a name="how-to-change-the-size-and-location-of-the-console-and-script-panes"></a>Jak zmienić rozmiar i położenie konsoli i okienka skryptu

Aby zmienić rozmiar i położenie okienka konsoli i w okienku skryptu, można użyć następujące kroki. Po ponownym otwarciu programu Windows PowerShell ISE, rozmiar i położenie wprowadzone zmiany zostaną zachowane.

### <a name="to-resize-the-script-pane-and-console-pane"></a>Zmiana rozmiaru w okienku skryptów i okienku konsoli

1. Zatrzymaj wskaźnik myszy na linię podziału między okienku skryptów i okienku konsoli.

2. Gdy kursor zmienia kształt strzałki dwukierunkowej, przeciągnij krawędź, aby zmienić rozmiar okienka.

### <a name="to-move-the-script-pane-and-console-pane"></a>Aby przenieść w okienku skryptów i okienku konsoli

Wykonaj jedną z następujących czynności:

- Aby przenieść okienko skryptu powyżej w okienku konsoli, naciśnij klawisz **CTRL + 1** lub na pasku narzędzi kliknij **Pokaż pierwsze okienko skryptu** ikony, lub w **widoku** menu, kliknij przycisk **Pokaż Skrypt w górnym okienku**.

- Aby przenieść skrypt w okienku po prawej stronie w okienku konsoli, naciśnij **CTRL + 2** lub na pasku narzędzi kliknij **Pokaż skryptu w okienku po prawej stronie** ikonę lub **widoku** menu, kliknij **Pokaż okienko skryptu prawo**.

- Aby zmaksymalizować w okienku skryptu, naciśnij klawisz **CTRL + 3** lub na pasku narzędzi kliknij **Pokaż zmaksymalizowane okienko skryptu** ikony, lub w **widoku** menu, kliknij przycisk **Pokaż skrypt Panel zmaksymalizowany**.

- Kliknij, aby zmaksymalizować w okienku konsoli i ukrywa okienko skryptu na prawej krawędzi wiersz kart, **ukryć okienko skryptu** ikonę w obszarze **widoku** menu, kliknij, aby usunąć zaznaczenie **Pokaż okienko skryptu** opcji menu.

- Aby wyświetlić okienko skryptu, jeśli w okienku konsoli jest zmaksymalizowane, prawej krawędzi wiersz kart, kliknij przycisk **Pokaż okienko skryptu** ikonę lub **widoku** menu, kliknij, aby wybrać **Pokaż skrypt W okienku** opcji menu.

## <a name="keyboard-shortcuts-for-editing-text"></a>Skróty klawiaturowe do edycji tekstu

Podczas edytowania tekstu, można użyć następujących skrótów klawiaturowych.

|Akcja|Skróty klawiaturowe|Używanie w|
|----------|----------------------|----------|
|**Kopiuj**|CTRL+C|Okienku skryptów i okienku konsoli|
|**Cut**|CTRL+X|Okienku skryptów i okienku konsoli|
|**Znajdź w skrypcie**|CTRL+F|Okienko skryptu|
|**Znajdź następny w skrypcie**|F3|Okienko skryptu|
|**Znajdź poprzedni w skrypcie**|SHIFT+F3|Okienko skryptu|
|**Wklej**|CTRL + V|Okienku skryptów i okienku konsoli|
|**Wykonaj ponownie**|CTRL+Y|Okienku skryptów i okienku konsoli|
|**Zastąp w skrypcie**|CTRL+H|Okienko skryptu|
|**Zapisywanie**|CTRL+S|Okienko skryptu|
|**Zaznacz wszystko**|CTRL + A|Okienku skryptów i okienku konsoli|
|**Cofnij**|CTRL+Z|Okienku skryptów i okienku konsoli|

## <a name="keyboard-shortcuts-for-running-scripts"></a>Skróty klawiaturowe do uruchamiania skryptów

Podczas uruchamiania skryptów w okienku skryptu, można użyć następujących skrótów klawiaturowych.

|Akcja|Skrót klawiaturowy|
|----------|---------------------|
|**Nowy**|CTRL+N|
|**Otwórz**|CTRL+O|
|**Run**|F5|
|**Uruchom zaznaczone**|F8|
|**Zatrzymaj wykonywanie**|CTRL+BREAK. CTRL + C, mogą służyć podczas kontekstu jest jednoznaczna, (gdy nie ma żadnego tekstu, zaznaczona).|
|**Karta** (do następnego skryptu)|CTRL + TAB **Uwaga:** TAB, aby dalej skrypt działa tylko wtedy, gdy masz jedną kartę programu PowerShell, Otwórz lub w przypadku, gdy masz więcej niż jedną kartę programu PowerShell, Otwórz, ale fokus znajduje się w okienku skryptów.|
|**Karta** (do poprzedniego skryptu)|CTRL + SHIFT + TAB **Uwaga:** TAB, aby poprzedni skrypt działa, jeśli masz tylko jedną kartę programu PowerShell, Otwórz lub jeśli masz więcej niż jedną kartę programu PowerShell, Otwórz, a fokus znajduje się w okienku skryptów.|

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>Skróty klawiaturowe do dostosowywania widoku

Aby dostosować widok, w środowisku Windows PowerShell ISE, można użyć następujących skrótów klawiaturowych. Są one dostępne z wszystkich okienkach w aplikacji.

|Akcja|Skrót klawiaturowy|
|----------|---------------------|
|**Przejdź do okienka konsoli**|CTRL+D|
|**Przejdź do okienka skryptu**|CTRL+I|
|**Pokaż okienko skryptu**|CTRL+R|
|**Ukryj okienko skryptu**|CTRL+R|
||
|**Przenieś w górę okienko skryptu**|CTRL+1|
|**Przesuń w prawo okienko skryptu**|CTRL+2|
|**Maksymalizuj okienko skryptu**|CTRL+3|
|**Powiększ**|CTRL+PLUS SIGN|
|**Pomniejsz**|CTRL + ZNAK MINUS|

## <a name="keyboard-shortcuts-for-debugging-scripts"></a>Skróty klawiaturowe dla debugowania skryptów

Podczas debugowania skryptów, można użyć następujących skrótów klawiaturowych.

|Akcja|Skrót klawiaturowy|Używanie w|
|----------|---------------------|----------|
|**Uruchom/Kontynuuj**|F5|W okienku skryptu, podczas debugowania skryptu|
|**Wkrocz**|F11|W okienku skryptu, podczas debugowania skryptu|
|**Przekrocz nad**|F10|W okienku skryptu, podczas debugowania skryptu|
|**Wyjdź**|SHIFT+F11|W okienku skryptu, podczas debugowania skryptu|
|**Wyświetl stos wywołań**|CTRL+SHIFT+D|W okienku skryptu, podczas debugowania skryptu|
|**Lista punktów przerwania**|CTRL+SHIFT+L|W okienku skryptu, podczas debugowania skryptu|
|**Przełącz punkt przerwania**|F9|W okienku skryptu, podczas debugowania skryptu|
|**Usuń wszystkie punkty przerwania**|CTRL+SHIFT+F9|W okienku skryptu, podczas debugowania skryptu|
|**Zatrzymaj debuger**|SHIFT+F5|W okienku skryptu, podczas debugowania skryptu|

> [!NOTE]
>
> Umożliwia także skróty klawiaturowe, zaprojektowana z myślą o konsoli programu Windows PowerShell podczas debugowania skryptów w środowisku Windows PowerShell ISE. Aby użyć tych skrótów, możesz wpisz skrót w okienku konsoli i naciśnij klawisz ENTER.

|Akcja|Skrót klawiaturowy|Używanie w|
|----------|---------------------|----------|
|**Continue**|C|W okienku konsoli, podczas debugowania skryptu|
|**Wkrocz**|S|W okienku konsoli, podczas debugowania skryptu|
|**Przekrocz nad**|V|W okienku konsoli, podczas debugowania skryptu|
|**Wyjdź**|O|W okienku konsoli, podczas debugowania skryptu|
|**Powtórz ostatnie polecenie** (dla krok po kroku lub Przekrocz)|ENTER|W okienku konsoli, podczas debugowania skryptu|
|**Wyświetl stos wywołań**|K|W okienku konsoli, podczas debugowania skryptu|
|**Zatrzymaj debugowanie**|PYTANIA I ODPOWIEDZI|W okienku konsoli, podczas debugowania skryptu|
|**Lista skryptu**|L|W okienku konsoli, podczas debugowania skryptu|
|**Wyświetlenie konsoli poleceń debugowania**|H lub?|W okienku konsoli, podczas debugowania skryptu|

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Skróty klawiaturowe dla karty programu Windows PowerShell

Można użyć następujących skrótów klawiatury, korzystając z karty programu Windows PowerShell.

|Akcja|Skrót klawiaturowy|
|----------|---------------------|
|**Zamknij kartę programu PowerShell**|CTRL+W|
|**Nowa karta programu PowerShell**|CTRL+T|
|**Poprzedniej karty programu PowerShell**|CTRL+SHIFT+TAB. Ten skrót działa tylko wtedy, gdy żadne pliki nie są otwarte na każdej z kart programu PowerShell.|
|**Następna karta środowiska Windows PowerShell**|CTRL+TAB. Ten skrót działa tylko wtedy, gdy żadne pliki nie są otwarte na każdej z kart programu PowerShell.|

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>Skróty klawiaturowe, uruchamianie i kończenie

Można użyć następujących skrótów klawiatury, aby uruchomić konsolę programu Windows PowerShell (PowerShell.exe) lub, aby zamknąć program Windows PowerShell ISE.

|Akcja|Skrót klawiaturowy|
|----------|---------------------|
|**Exit**|ALT+F4|
|**Rozpocznij PowerShell.exe** (konsoli środowiska Windows PowerShell)|CTRL+SHIFT+P|

## <a name="see-also"></a>Zobacz też

[Wprowadzenie do programu Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)