---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Dodatek 2 Tworzenie niestandardowego skrótu programu PowerShell
ms.openlocfilehash: 6f1a6a8187b1797103e3620b2cf9155978807ea5
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030302"
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
