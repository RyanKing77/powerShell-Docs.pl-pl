---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Dodatek 2 Tworzenie niestandardowego skrótu programu PowerShell
ms.assetid: 5d4fd421-5d43-4ec7-86fd-acfe887b066e
ms.openlocfilehash: e8081b7a64d313c8ef4bbccf95f250445dd68ad9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687643"
---
# <a name="appendix-2---creating-a-custom-powershell-shortcut"></a>Dodatek 2 — Tworzenie niestandardowego skrótu programu PowerShell

Poniższa procedura opisuje sposób tworzenia skrótu do programu PowerShell Windows, który ma kilka opcji wygodne dostosowane.

1. Utwórz skrót, który wskazuje na Powershell.exe.

2. Kliknij prawym przyciskiem myszy skrót, a następnie kliknij przycisk **właściwości**.

3. Kliknij przycisk **Opcje** kartę.

4. W **opcje edytowania** zaznacz **szybkiej edycji** pole wyboru.

    To ustawienie umożliwia zaznacz tekst w oknie konsoli środowiska Windows PowerShell przez przeciągnięcie lewym przyciskiem myszy, a dzięki temu można skopiować tekst do Schowka, naciskając klawisz ENTER lub klikając prawym przyciskiem myszy przycisk myszy.

5. W **opcje edytowania** zaznacz **tryb wstawiania** pole wyboru. To ustawienie umożliwia kliknij prawym przyciskiem myszy w oknie konsoli, aby automatycznie Wklej tekst ze Schowka.

6. W **historii poleceń** sekcji, wpisz lub wybierz liczbę z zakresu od 1 do 999 w **rozmiar buforu** pole. To ustawia liczbę wpisanych poleceń, które będą znajdować się w buforze konsoli.

7. W **historii poleceń** zaznacz **Odrzuć stare duplikaty** pole wyboru w celu wyeliminowania powtarzających poleceń z buforu konsoli.

8. Kliknij przycisk **układu** kartę.

9. W **buforu ekranu** sekcji, wpisz liczbę z zakresu od 1 do 9999 w **wysokość** pole. Wysokość reprezentuje liczbę wierszy danych wyjściowych, które są buforowane. Jest to maksymalna liczba wierszy zachowana na potrzeby wyświetlania podczas przewijania w oknie konsoli. Jeśli ta liczba jest niższa niż wysokość objętego **rozmiar okna** sekcji wysokości rozmiaru okna automatycznie zostanie zredukowana do tej samej wartości.

10. W **rozmiar okna** sekcji, wpisz liczbę z zakresu od 1 do 9999 szerokości. Reprezentuje liczbę znaków, które są wyświetlane w oknie konsoli. Domyślna szerokość to 80 i formatowanie danych wyjściowych programu Windows PowerShell jest przeznaczony dla tej szerokości.

11. Jeśli chcesz umieścić konsoli w określonym punkcie na pulpicie, gdy zostanie otwarta, wyczyść **wybór pozycji okna przez system** pole wyboru w **położenie okna** sekcji, a następnie zmień wartości w  **Po lewej stronie** i **górnej** pola **położenie okna** sekcji.

12. Kliknij przycisk **OK**.