---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Eksplorowanie środowiska Windows PowerShell ISE
ms.assetid: e0d2c6e8-5126-40e7-a1e1-d1cff29fe94a
ms.openlocfilehash: 059651f159fb2636a93167709134788e90d062b8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952277"
---
# <a name="exploring-the-windows-powershell-ise"></a>Eksplorowanie środowiska Windows PowerShell ISE

Windows PowerShell® Integrated Scripting Environment (ISE) służy do tworzenia, uruchamiania i debugowanie poleceń i skryptów. Programu Windows PowerShell ISE składa się z paska menu, kart środowiska Windows PowerShell, paska narzędzi, karty skryptu, okienko skryptu, okienku konsoli, paska stanu, suwak rozmiar tekstu i Pomoc kontekstowa.

> [!NOTE]
> Począwszy od programu Windows PowerShell ISE 3.0 polecenia i okienka wyjściowego zostały połączone w jednym okienku konsoli.

## <a name="menu-bar"></a>Pasek menu

Pasek menu zawiera **pliku**, **Edytuj**, **widoku**, **narzędzia**, **debugowania**,  **Dodatki**, i **pomocy** menu. Przyciski na pasku menu umożliwiają wykonywanie zadań związanych z pisania i uruchomione skrypty i uruchomionych poleceń programu Windows PowerShell ISE. Ponadto [dodatkowe narzędzia](../../core-powershell/ise/The-ISEAddOnTool-Object.md) może być umieszczany na pasku menu, uruchamiając skrypty, które używają [hierarchii modelu obiektu ISE](../../core-powershell/ise/The-ISE-Object-Model-Hierarchy.md).

> [!NOTE]
> W programie Windows PowerShell ISE 2.0 **narzędzia** i **dodatki** menu nie były widoczne.

## <a name="windows-powershell-tabs"></a>Windows PowerShell karty

Na karcie środowiska Windows PowerShell jest środowisko, w którym uruchamia skrypt programu Windows PowerShell. Możesz otworzyć nowych kartach programu Windows PowerShell dla programu Windows PowerShell ISE utworzyć oddzielne środowiska, na komputerze lokalnym lub komputerach zdalnych. Może mieć maksymalnie osiem PowerShell jednocześnie Otwórz karty.

## <a name="toolbar"></a>Pasek narzędzi

Następujące przyciski znajdują się na pasku narzędzi.

|Przycisk|Funkcja|
|----------|------------|
|**Nowy**|Zostanie otwarty nowy skrypt.|
|**Otwórz**|Otwiera istniejący skrypt lub plik.|
|**Zapisywanie**|Zapisuje skryptu lub pliku.|
|**Cut**|Wycina zaznaczony tekst i kopiuje go do Schowka.|
|**Kopiuj**|Kopiuje zaznaczony tekst do Schowka.|
|**Wklej**|Wkleja zawartość Schowka w lokalizacji kursora.|
|**Wyczyść okienku danych wyjściowych**|Czyści całą zawartość w okienku danych wyjściowych.|
|**Cofnij**|Odwraca akcję, która właśnie została wykonana.|
|**Wykonaj ponownie**|Wykonuje akcję, która została właśnie cofnąć.|
|**Uruchom skrypt**|Uruchamia skrypt.|
|**Uruchom zaznaczenia**|Uruchamia wybrane części skryptu.|
|**Zatrzymuje wykonywanie**|Zatrzymuje skrypt, który jest uruchomiony.|
|**Nowa karta zdalne programu PowerShell**|Tworzy nową kartę programu PowerShell, który ustanawia sesję na komputerze zdalnym. Okno dialogowe zostanie wyświetlone i wyświetli monit o wprowadzenie szczegółowe informacje wymagane do nawiązania połączenia zdalnego.|
|**Uruchom PowerShell.exe**|Otwiera konsolę programu PowerShell.|
|**Pokaż pierwsze okienko skryptu**|Przenosi okienka Skrypt do góry na ekranie.|
|**Pokaż okienko skryptu prawo**|Przenosi okienko skryptu z prawej strony na ekranie.|
|**Pokaż okienko skryptu zmaksymalizowane**|Maksymalizuje okienku skryptów.|

## <a name="script-tab"></a>Karta skryptu

Wyświetla nazwę skryptu, którą edytujesz. Możesz kliknąć kartę skryptu, aby wybrać skryptu, który chcesz edytować.

Po wskazaniu kartę skrypt w pełni kwalifikowana ścieżka do pliku skryptu jest wyświetlany w etykietce narzędzia.

## <a name="script-pane"></a>Okienko skryptu

Umożliwia tworzenie i uruchamianie skryptów. Można otwierać, edytować i uruchamiać skrypty istniejących w okienku skryptów.

## <a name="output-pane"></a>W okienku danych wyjściowych

Wyświetla wyniki poleceń i skryptów, które zostało uruchomione. Można również skopiować i wyczyścić zawartość w okienku danych wyjściowych.

## <a name="command-pane"></a>Polecenie Okienko

Służy do tworzenia poleceń. W okienku polecenie można uruchomić polecenie jeden wiersz lub wielowierszowy polecenia. Naciśnij klawisz SHIFT + ENTER, aby wprowadzić każdego wiersza polecenia wielowierszowy, a następnie naciśnij klawisz ENTER po ostatnim wierszu można wykonać polecenia wielowierszowy. Wiersz wyświetlany u góry okienka polecenia zawiera ścieżkę do bieżącego katalogu roboczego.

## <a name="status-bar"></a>Pasek stanu

Służy do sprawdzenia, czy poleceń i skryptów, uruchamiane są kompletne. Na pasku stanu jest u dołu ekranu. Zaznaczonych części komunikaty o błędach są wyświetlane na pasku stanu.

## <a name="text-size-slider"></a>Rozmiar tekstu suwaka

Zwiększa lub zmniejsza rozmiar tekstu na ekranie.

## <a name="help"></a>Pomoc

Pomoc dla środowiska Windows PowerShell ISE jest dostępna w sieci Web w bibliotece TechNet. Pomocy można otworzyć, klikając **pomocy programu Windows PowerShell ISE** na **pomocy** menu lub naciskając klawisz F1 w dowolnym z wyjątkiem gdy kursor znajduje się na nazwę polecenia cmdlet w okienku skryptów lub w okienku konsoli. Z **pomocy** menu można również uruchomić polecenie cmdlet Update-Help i wyświetlić okno polecenia, który ułatwia konstruowanie polecenia przedstawiający wszystkich parametrów dla polecenia cmdlet, a dzięki któremu można podać parametrów w Formularz łatwy w użyciu.

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do programu Windows PowerShell ISE](../../core-powershell/ise/Introducing-the-Windows-PowerShell-ISE.md)