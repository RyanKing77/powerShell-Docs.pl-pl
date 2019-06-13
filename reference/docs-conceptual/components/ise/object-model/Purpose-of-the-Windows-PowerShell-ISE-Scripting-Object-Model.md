---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE
ms.openlocfilehash: e59593ef06911c709e92fa7a1eabd96d2636ca30
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030912"
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a>Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE

Obiekty są skojarzone z formularza i funkcji programu Windows PowerShell zintegrowane Scripting Environment (ISE). Dokumentacja modelu obiektów zawiera szczegóły dotyczące elementu członkowskiego, właściwości i metod, które ujawniają te obiekty. Przedstawione przykłady pokazują, jak można użyć skryptów bezpośrednio uzyskiwać dostęp do tych metod i właściwości. Model obiektów programu obsługi skryptów ułatwia następującego zakresu zadań.

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a>Dostosowywanie wyglądu programu Windows PowerShell ISE

Aby zmodyfikować opcje i ustawienia aplikacji, można użyć modelu obiektów. Na przykład można zmodyfikować je w następujący sposób:

- Możesz zmienić kolor błędy, ostrzeżenia, pełne dane wyjściowe, a dane wyjściowe debugowania.
- Można uzyskać lub ustawić kolory tła dla okienka polecenia, w okienku danych wyjściowych i w okienku skryptu.
- Możesz ustawić kolor pierwszego planu dla tego okienka danych wyjściowych.
- Można ustawić nazwę czcionki i rozmiar czcionki dla środowiska Windows PowerShell ISE.
- Można skonfigurować ostrzeżenia. To ustawienie zawiera ostrzeżenia, które są wydawane, gdy plik jest otwarty w wiele kart programu PowerShell lub po uruchomieniu skryptu w pliku, zanim plik został zapisany.
- Możesz przełączać się między widokiem, w których side-by-side okienku skryptów i okienku danych wyjściowych i widok gdzie okienko skryptu znajduje się na szczycie okienko danych wyjściowych. Można zadokować okienka polecenia do dolnej lub górnej części okienka danych wyjściowych.

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a>Zwiększanie funkcjonalności programu Windows PowerShell ISE

Model obiektów umożliwia rozszerzanie funkcjonalności programu Windows PowerShell ISE. Na przykład możesz wykonywać następujące czynności:

- Dodawanie i modyfikowanie wystąpienie programu Windows PowerShell ISE, sam. Można na przykład, aby zmienić menu, dodawaniu nowych elementów menu i mapowanie nowe elementy menu do skryptów.
- Tworzenie skryptów, wykonujących niektóre zadania, które można wykonać za pomocą poleceń menu i przycisków w środowisku Windows PowerShell ISE. Na przykład można dodać, usunąć lub wybierz kartę programu PowerShell.
- Uzupełnienie zadania, które mogą być wykonywane za pomocą poleceń menu i przycisków. Na przykład można zmienić kartę programu PowerShell.
- Manipulowanie buforów tekstu dla okienka polecenia, w okienku danych wyjściowych i w okienku skryptu, które są skojarzone z plikiem. Na przykład możesz wykonywać następujące czynności:
  - Pobierz lub ustaw cały tekst.
  - Pobierz lub ustaw zaznaczonego tekstu.
  - Uruchamianie skryptu lub uruchom wybrane części skryptu.
  - Przewiń o wiersz w widoku.
  - Wstaw tekst w położeniu karetki.
  - Wybierz w bloku tekstu.
  - Pobierz ostatni numer wiersza.
- Wykonaj operacje na plikach. Na przykład możesz wykonywać następujące czynności:
  - Otwórz plik, Zapisz plik lub zapisać plik, używając innej nazwy.
  - Ustal, czy plik został zmieniony od czasu ostatniego zapisania.
  - Pobierz nazwę pliku.
  - Wybierz plik.

## <a name="automating-tasks"></a>Automatyzacja zadań

Model obiektów programu obsługi skryptów umożliwia tworzenie skróty klawiaturowe dla często wykonywane operacje.

## <a name="see-also"></a>Zobacz też

- [Hierarchia modeli obiektów środowiska ISE](The-ISE-Object-Model-Hierarchy.md)
