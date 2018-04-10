---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE
ms.assetid: d176a131-ab0c-43ee-80c1-f824ab8e4a05
ms.openlocfilehash: fd5ac2c34b173d4eba7636bb5760b1ac9abb4277
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a>Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE

Obiekt jest skojarzony z formularza i funkcji programu Windows PowerShell Integrated Scripting Environment (ISE). Odwołanie do obiektu modelu zawiera szczegółowe informacje dotyczące elementu członkowskiego, właściwości i metody, które udostępniają te obiekty. Aby pokazać, jak używać skryptów bezpośredni dostęp do tych metod i właściwości przedstawione przykłady. Skryptów model obiektów ułatwia następującego zakresu zadań.

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a>Dostosowywanie wyglądu programu Windows PowerShell ISE

Model obiektów można użyć w celu zmodyfikowania ustawień aplikacji i opcje. Na przykład można je zmodyfikować w następujący sposób:

- Można zmienić kolor błędy, ostrzeżenia, pełne dane wyjściowe i danych wyjściowych debugowania.
- Można pobrać lub ustawić kolory tła okienka polecenia, w okienku danych wyjściowych i w okienku skryptów.
- Kolor pierwszego planu w okienku danych wyjściowych.
- Można ustawić nazwę czcionki i rozmiar czcionki dla programu Windows PowerShell ISE.
- Można skonfigurować ostrzeżenia. To ustawienie obejmuje ostrzeżenia, które są wydawane, gdy plik jest otwarty w wielu kartach programu PowerShell lub uruchamianie skryptu w pliku przed plik został zapisany.
- Można przełączać się między widokiem skutkującej side-by-side okienko skryptu i w okienku danych wyjściowych oraz widok przypadku okienka Skrypt u góry w okienku danych wyjściowych. W okienku polecenie dokowany do dolnej lub górnej części okienka wyjściowego.

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a>Rozszerzanie funkcji programu Windows PowerShell ISE

Model obiektów służy do rozszerzania funkcji programu Windows PowerShell ISE. Można na przykład:

- Dodawanie i modyfikowanie wystąpienie programu Windows PowerShell ISE samej siebie. Na przykład aby zmienić menu, należy dodać nowe elementy menu i mapy skryptów nowych elementów menu.
- Tworzenie skryptów, które wykonać kilka zadań, które można wykonać za pomocą poleceń menu i przycisków w środowisku Windows PowerShell ISE. Na przykład można dodać, usunąć lub wybierz kartę programu PowerShell.
- Dopełnienia zadania, które mogą być wykonywane za pomocą poleceń menu i przycisków. Na przykład można zmienić na karcie środowiska PowerShell.
- Manipulowanie buforów tekst okienko poleceń, w okienku danych wyjściowych i w okienku skryptów, które są skojarzone z plikiem. Można na przykład:
  - GET lub set cały tekst.
  - GET lub set zaznaczonego tekstu.
  - Uruchom skrypt lub uruchom wybrane części skryptu.
  - Przewiń wiersz do widoku.
  - Wstawianie tekstu w położeniu karetki.
  - Wybierz blok tekstu.
  - Pobierz ostatni numer wiersza.
- Wykonaj operacje na plikach. Można na przykład:
  - Otwórz plik, Zapisz plik lub zapisać plik przy użyciu innej nazwy.
  - Ustal, czy plik został zmieniony od czasu ostatniego zapisania.
  - Pobierz nazwę pliku.
  - Wybierz plik.

## <a name="automating-tasks"></a>Automatyzacja zadań

Model obiektu skryptów służy do tworzenia skróty klawiaturowe dla często operacji.

## <a name="see-also"></a>Zobacz też

- [Hierarchia modeli obiektów środowiska ISE](The-ISE-Object-Model-Hierarchy.md)