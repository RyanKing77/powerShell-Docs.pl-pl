---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Ułatwienia dostępu w środowisku Windows PowerShell ISE
ms.assetid: a078f9d1-dd6b-4323-b16d-0622cd993aa8
ms.openlocfilehash: 272dd502ff9d220e82236c93cbffaf4e12054cfe
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34482985"
---
# <a name="accessibility-in-windows-powershell-ise"></a>Ułatwienia dostępu w środowisku Windows PowerShell ISE

W tym temacie opisano funkcje ułatwień dostępu z systemu Windows PowerShell Integrated Scripting Environment (ISE), które mogą być przydatne.

* [Jak zmienić rozmiar i położenie konsoli i okienka skryptu](#how-to-change-the-size-and-location-of-the-console-and-script-panes)
* [Skróty klawiaturowe do edycji tekstu](#keyboard-shortcuts-for-editing-text)
* [Skróty klawiaturowe do uruchamiania skryptów](#keyboard-shortcuts-for-running-scripts)
* [Skróty klawiaturowe dostosowywania widoku](#keyboard-shortcuts-for-customizing-the-view)
* [Skróty klawiaturowe do debugowania skryptów](#keyboard-shortcuts-for-debugging-scripts)
* [Skróty klawiaturowe dla kart środowiska Windows PowerShell](#keyboard-shortcuts-for-windows-powershell-tabs)
* [Skróty klawiaturowe, uruchamianie i kończenie](#keyboard-shortcuts-for-starting-and-exiting)

Firma Microsoft dokłada wszelkich starań, aby jej produkty i usługi były coraz łatwiejsze w użytkowaniu. Poniższe tematy zawierają informacje dotyczące funkcji, produktów i usług, które ułatwiają dostęp do programu Windows PowerShell ISE dla osób niepełnosprawnych.

Windows PowerShell ISE obsługuje tryb dużego kontrastu. Dla niedowidzących punkt przerwania informacje są dostępne za pomocą poleceń cmdlet do zarządzania punktów przerwania, takich jak [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) i [PSBreakpoint zestawu](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420). Aby uzyskać więcej informacji skontaktuj się w temacie jak zarządzać punktów przerwania w [jak debugowanie skryptów w środowisku Windows PowerShell ISE](../core-powershell/ise/How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md). Oprócz funkcji ułatwień dostępu i narzędzi w systemie Microsoft Windows następujące funkcje ułatwiają programu Windows PowerShell ISE dostęp dla osób niepełnosprawnych:

- Skróty klawiaturowe

- Tabela kolorowanie składni i uprawnienia do modyfikowania kilka innych ustawień kolorów przy użyciu [$psISE.Options](https://technet.microsoft.com/library/75e2a76f-f3d1-490b-ad5d-e3829946aabb) obiekt skryptów.

- Zmień rozmiar tekstu

## <a name="how-to-change-the-size-and-location-of-the-console-and-script-panes"></a>Jak zmienić rozmiar i położenie konsoli i okienka skryptu

Poniższe kroki umożliwia zmieniać rozmiar i położenie w okienku konsoli i w okienku skryptów. Po ponownym otwarciu programu Windows PowerShell ISE, rozmiar i położenie wprowadzone zmiany zostaną zachowane.

### <a name="to-resize-the-script-pane-and-console-pane"></a>Aby zmienić rozmiar okienka Skrypt i okienku konsoli

1. Zatrzymaj wskaźnik myszy na linii podziału między okienku skryptów i okienku konsoli.

2. Gdy wskaźnik myszy zmieni się podwójna strzałka, przeciągnij obramowanie, aby zmienić rozmiar okienka.

### <a name="to-move-the-script-pane-and-console-pane"></a>Aby przenieść okienko skryptu i w okienku konsoli

Wykonaj jedną z następujących czynności:

- Aby przenieść okienko skryptu powyżej w okienku konsoli, naciśnij klawisz **CTRL + 1** lub na pasku narzędzi kliknij **Pokaż pierwsze okienko skryptu** ikony, lub w **widoku** menu, kliknij przycisk **Pokaż Skrypt w górnym okienku**.

- Aby przenieść okienko skryptu konsoli w okienku po prawej stronie, naciśnij klawisz **CTRL + 2** lub na pasku narzędzi kliknij przycisk **Pokaż prawym okienku skryptu** ikony, lub w **widoku** menu, kliknij przycisk **Pokaż okienko skryptu prawo**.

- Aby zmaksymalizować okienku skryptów, naciśnij klawisz **CTRL + 3** lub na pasku narzędzi kliknij **Pokaż zmaksymalizowane okienko skryptu** ikony, lub w **widoku** menu, kliknij przycisk **Pokaż skryptu Okienko zmaksymalizowane**.

- Aby zmaksymalizować okienku konsoli i ukrywanie okienka skryptu do prawej krawędzi wiersz kart, kliknij przycisk **ukryć okienko skryptu** ikonę w **widoku** menu, kliknij, aby usunąć zaznaczenie **Pokaż okienko skryptu** opcji menu.

- Wyświetlany w okienku skryptów, gdy w okienku konsoli jest zmaksymalizowane na prawej krawędzi wiersz kart, kliknij przycisk **Pokaż okienko skryptu** ikony, lub w **widoku** menu, kliknij, aby wybrać **Pokaż skryptu Okienko** opcji menu.

## <a name="keyboard-shortcuts-for-editing-text"></a>Skróty klawiaturowe do edycji tekstu

Podczas edytowania tekstu, można użyć następujących skrótów klawiaturowych.

|Akcja|Skróty klawiaturowe|Użyj w|
|----------|----------------------|----------|
|**Kopiuj**|CTRL+C|Skrypt, okienko konsoli|
|**Cut**|CTRL+X|Skrypt, okienko konsoli|
|**Znajdź w skrypcie**|CTRL+F|Okienko skryptu|
|**Znajdź następny w skrypcie**|F3|Okienko skryptu|
|**Znajdź poprzedni w skrypcie**|SHIFT+F3|Okienko skryptu|
|**Wklej**|CTRL + V|Skrypt, okienko konsoli|
|**Wykonaj ponownie**|CTRL+Y|Skrypt, okienko konsoli|
|**Zastąp w skrypcie**|CTRL+H|Okienko skryptu|
|**Zapisywanie**|CTRL+S|Okienko skryptu|
|**Zaznacz wszystko**|CTRL + A|Skrypt, okienko konsoli|
|**Cofnij**|CTRL+Z|Skrypt, okienko konsoli|

## <a name="keyboard-shortcuts-for-running-scripts"></a>Skróty klawiaturowe do uruchamiania skryptów

Podczas uruchamiania skryptów w okienku skryptów, można użyć następujących skrótów klawiaturowych.

|Akcja|Skróty klawiaturowe|
|----------|---------------------|
|**Nowy**|CTRL+N|
|**Otwórz**|CTRL+O|
|**Run**|F5|
|**Uruchom zaznaczenia**|F8|
|**Zatrzymuje wykonywanie**|CTRL+BREAK. CTRL + C można można użyć, gdy kontekst jest jednoznaczne (Jeśli nie podano tekstu wybrane).|
|**Karta** (do następnego skryptu)|CTRL + TAB **Uwaga:** Tab do następnego skryptu działa tylko wtedy, gdy masz pojedynczej karcie programu PowerShell, Otwórz, lub gdy ma więcej niż jedną kartę programu PowerShell, Otwórz, ale skupiono się w okienku skryptów.|
|**Karta** (do poprzedniego skryptu)|CTRL + SHIFT + TAB **Uwaga:** kartę do poprzedniego skryptu działa, jeśli masz tylko jedną Otwórz kartę programu PowerShell lub jeśli masz więcej niż jedną kartę programu PowerShell, Otwórz, a skupiono się w okienku skryptów.|

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>Skróty klawiaturowe dostosowywania widoku

Następujące skróty klawiaturowe służy do dostosowywania widoku w środowisku Windows PowerShell ISE. Są one dostępne z wszystkich okienka w aplikacji.

|Akcja|Skróty klawiaturowe|
|----------|---------------------|
|**Przejdź do okienka konsoli**|CTRL+D|
|**Przejdź do okienka skryptu**|CTRL+I|
|**Pokaż okienko skryptu**|CTRL+R|
|**Ukrywanie okienka skryptu**|CTRL+R|
||
|**Przenieś w górę okienko skryptu**|CTRL+1|
|**Okienko skryptu w prawo**|CTRL+2|
|**Maksymalizuj okienko skryptu**|CTRL+3|
|**Powiększenie**|CTRL+PLUS SIGN|
|**Pomniejszenie**|CTRL + ZNAK MINUS|

## <a name="keyboard-shortcuts-for-debugging-scripts"></a>Skróty klawiaturowe do debugowania skryptów

Podczas debugowania skryptów, można użyć następujących skrótów klawiaturowych.

|Akcja|Skróty klawiaturowe|Użyj w|
|----------|---------------------|----------|
|**Uruchom/Kontynuuj**|F5|W okienku skryptów, podczas debugowania skryptu|
|**Wkrocz**|F11|W okienku skryptów, podczas debugowania skryptu|
|**Przekrocz**|F10|W okienku skryptów, podczas debugowania skryptu|
|**Wyjdź**|SHIFT+F11|W okienku skryptów, podczas debugowania skryptu|
|**Stos wywołań wyświetlania**|CTRL+SHIFT+D|W okienku skryptów, podczas debugowania skryptu|
|**Lista punktów przerwania**|CTRL+SHIFT+L|W okienku skryptów, podczas debugowania skryptu|
|**Przełącz punkt przerwania**|F9|W okienku skryptów, podczas debugowania skryptu|
|**Usuń wszystkie punkty przerwania**|CTRL+SHIFT+F9|W okienku skryptów, podczas debugowania skryptu|
|**Zatrzymaj debugera**|SHIFT+F5|W okienku skryptów, podczas debugowania skryptu|

> ![Uwaga](../core-powershell/web-access/images/Note.jpeg)**Uwaga**
>
> Umożliwia także skróty klawiaturowe przeznaczone do konsoli środowiska Windows PowerShell, gdy debugowanie skryptów w środowisku Windows PowerShell ISE. Te skróty używane, należy wpisać skrótu w okienku konsoli i naciśnij klawisz ENTER.

|Akcja|Skróty klawiaturowe|Użyj w|
|----------|---------------------|----------|
|**Kontynuuj**|C|W okienku konsoli, podczas debugowania skryptu|
|**Wkrocz**|S|W okienku konsoli, podczas debugowania skryptu|
|**Przekrocz**|V|W okienku konsoli, podczas debugowania skryptu|
|**Wyjdź**|O|W okienku konsoli, podczas debugowania skryptu|
|**Powtórz ostatnie polecenie** (dla Wkrocz do lub Przekrocz)|ENTER|W okienku konsoli, podczas debugowania skryptu|
|**Stos wywołań wyświetlania**|K|W okienku konsoli, podczas debugowania skryptu|
|**Zatrzymaj debugowanie**|PYTANIA I ODPOWIEDZI|W okienku konsoli, podczas debugowania skryptu|
|**Lista skryptu**|L|W okienku konsoli, podczas debugowania skryptu|
|**Wyświetlenie konsoli debugowania poleceń**|H lub?|W okienku konsoli, podczas debugowania skryptu|

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Skróty klawiaturowe dla kart środowiska Windows PowerShell

Można użyć następujących skrótów klawiaturowych, korzystając z kart środowiska Windows PowerShell.

|Akcja|Skróty klawiaturowe|
|----------|---------------------|
|**Zamknij kartę programu PowerShell**|CTRL+W|
|**Nowa karta programu PowerShell**|CTRL+T|
|**Poprzedniej karty środowiska PowerShell**|CTRL+SHIFT+TAB. Ten skrót działa tylko wtedy, gdy żadne pliki nie są otwarte na każdej z kart środowiska PowerShell.|
|**Następna karta środowiska Windows PowerShell**|CTRL+TAB. Ten skrót działa tylko wtedy, gdy żadne pliki nie są otwarte na każdej z kart środowiska PowerShell.|

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>Skróty klawiaturowe, uruchamianie i kończenie

Można użyć następujących skrótów klawiaturowych, aby uruchomić konsolę programu Windows PowerShell (PowerShell.exe) lub aby zakończyć działanie programu Windows PowerShell ISE.

|Akcja|Skróty klawiaturowe|
|----------|---------------------|
|**Exit**|ALT+F4|
|**Uruchom PowerShell.exe** (konsoli środowiska Windows PowerShell)|CTRL+SHIFT+P|

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do programu Windows PowerShell ISE](../core-powershell/ise/Introducing-the-Windows-PowerShell-ISE.md)