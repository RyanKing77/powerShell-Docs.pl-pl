---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Eksplorowanie środowiska Windows PowerShell ISE
ms.assetid: e0d2c6e8-5126-40e7-a1e1-d1cff29fe94a
ms.openlocfilehash: 059651f159fb2636a93167709134788e90d062b8
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405371"
---
# <a name="exploring-the-windows-powershell-ise"></a>Eksplorowanie środowiska Windows PowerShell ISE

Windows PowerShell® zintegrowane Scripting Environment (ISE) umożliwia tworzenie, uruchamianie i debugowanie poleceń i skryptów. Środowiska Windows PowerShell ISE składa się z na pasku menu, karty programu Windows PowerShell, pasek narzędzi, skrypt karty, okienku skryptów, okienku konsoli, pasek stanu, suwak rozmiar tekstu i pomocy kontekstowej.

> [!NOTE]
> Począwszy od programu Windows PowerShell ISE 3.0 polecenia i okienka danych wyjściowych zostały połączone w jednym okienku konsoli.

## <a name="menu-bar"></a>Pasek menu

Na pasku menu znajdują **pliku**, **Edytuj**, **widoku**, **narzędzia**, **debugowania**,  **Dodatki**, i **pomocy** menu. Przyciski na pasku menu umożliwiają wykonywanie zadań związanych z pisanie i uruchamianie skryptów i uruchamianie poleceń w środowisku Windows PowerShell ISE. Ponadto [narzędzie dodatek](../../core-powershell/ise/The-ISEAddOnTool-Object.md) może zostać umieszczony na pasku menu, uruchamiając skrypty, które używają [hierarchia modeli obiektów środowiska ISE](../../core-powershell/ise/The-ISE-Object-Model-Hierarchy.md).

> [!NOTE]
> W programie Windows PowerShell ISE 2.0 **narzędzia** i **dodatki** menu nie był obecny.

## <a name="windows-powershell-tabs"></a>Windows PowerShell karty

Na karcie programu Windows PowerShell to środowisko, w którym jest uruchamiany skrypt programu Windows PowerShell. W środowisku Windows PowerShell ISE, aby utworzyć oddzielne środowiska, na komputerze lokalnym lub na komputerach zdalnych, możesz otworzyć nowe karty programu Windows PowerShell. Może mieć maksymalnie osiem PowerShell jednocześnie Otwórz karty.

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
|**Wyczyść okienko danych wyjściowych**|Czyści całą zawartość w okienku danych wyjściowych.|
|**Cofnij**|Odwraca akcję, która właśnie została wykonana.|
|**Wykonaj ponownie**|Wykonuje akcję, która została właśnie cofnięte.|
|**Uruchom skrypt**|Uruchamia skrypt.|
|**Uruchom zaznaczone**|Uruchamia wybrane części skryptu.|
|**Zatrzymaj wykonywanie**|Zatrzymuje skrypt, który jest uruchomiony.|
|**Nowa karta programu PowerShell zdalnego**|Tworzy nową kartę programu PowerShell, która ustanawia sesję na komputerze zdalnym. Okno dialogowe pojawia się i wyświetli monit o wprowadzenie szczegółowe informacje wymagane do nawiązania połączenia zdalnego.|
|**Rozpocznij PowerShell.exe**|Otwiera konsolę programu PowerShell.|
|**Pokaż pierwsze okienko skryptu**|Przenosi okienko skryptu do góry na ekranie.|
|**Pokaż okienko skryptu na prawo**|Przenosi skryptu w okienku po prawej stronie na ekranie.|
|**Pokaż okienko skryptu zmaksymalizowany**|Maksymalizuje okienko skryptu.|

## <a name="script-tab"></a>Karta skryptu

Wyświetla nazwy skryptu, który jest edytowany. Możesz kliknąć kartę skrypt, aby wybrać skryptu, który chcesz edytować.

Po wskazaniu karcie skrypt w etykietce narzędzia pojawi się w pełni kwalifikowana ścieżka do pliku skryptu.

## <a name="script-pane"></a>Okienko skryptu

Umożliwia tworzenie i uruchamianie skryptów. Można otworzyć, edytować i uruchamiać skrypty istniejących w okienku skryptów.

## <a name="output-pane"></a>Okienko danych wyjściowych

Wyświetla wyniki poleceń i skryptów, które zostały uruchomione. Można również skopiować i wyczyścić zawartość w okienku danych wyjściowych.

## <a name="command-pane"></a>W okienku poleceń

Umożliwia pisanie poleceń. W okienku poleceń, można uruchomić polecenie jeden wiersz lub wielowierszowym polecenia. Naciśnij klawisze SHIFT + ENTER, aby wprowadzić każdego wiersza polecenia wielowierszowy, a następnie naciśnij klawisz ENTER po ostatni wiersz, aby wykonać polecenie wielowierszowe. Wiersz wyświetlany u góry okienka polecenia zawiera ścieżkę do bieżącego katalogu roboczego.

## <a name="status-bar"></a>Pasek stanu

Umożliwia sprawdzenie, czy polecenia i skrypty uruchamiane są pełne. Na pasku stanu jest u dołu ekranu. Zaznaczonych części komunikaty o błędach są wyświetlane na pasku stanu.

## <a name="text-size-slider"></a>Rozmiar tekstu suwaka

Zwiększa lub zmniejsza rozmiar tekstu na ekranie.

## <a name="help"></a>Pomoc

Pomoc dla programu Windows PowerShell ISE jest dostępna w sieci Web w bibliotece TechNet. Pomoc można otworzyć, klikając **pomocy programu Windows PowerShell ISE** na **pomocy** menu lub naciskając klawisz F1 w dowolnym miejscu poza gdy kursor znajduje się na nazwę polecenia cmdlet w okienku skryptów i okienku konsoli. Z **pomocy** menu można również uruchomić polecenie cmdlet Update-Help i wyświetlić okno polecenia, który ułatwia konstruowanie poleceń zawierająca wszystkie parametry dla polecenia cmdlet, a umożliwiając Podaj parametry w formularz, łatwy w użyciu.

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do programu Windows PowerShell ISE](../../core-powershell/ise/Introducing-the-Windows-PowerShell-ISE.md)