---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Dodatek 2 Tworzenie niestandardowego skrótu programu PowerShell
ms.assetid: 5d4fd421-5d43-4ec7-86fd-acfe887b066e
ms.openlocfilehash: e8081b7a64d313c8ef4bbccf95f250445dd68ad9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="appendix-2---creating-a-custom-powershell-shortcut"></a>Dodatek 2 — Tworzenie skrótu niestandardowego programu PowerShell

Poniższa procedura opisuje sposób tworzenia skrótu do programu Windows PowerShell, który ma kilka opcji wygodny dostosowane.

1. Utwórz skrót, który wskazuje Powershell.exe.

2. Kliknij prawym przyciskiem myszy skrót, a następnie kliknij przycisk **właściwości**.

3. Kliknij przycisk **Opcje** kartę.

4. W **edytować opcje** zaznacz **szybkiej edycji** pole wyboru.

    To ustawienie pozwala wybrać tekst w oknie konsoli środowiska Windows PowerShell, przeciągając lewego przycisku myszy, a dzięki temu można skopiować tekst do Schowka, naciskając klawisz ENTER lub przez kliknięcie prawym przyciskiem myszy.

5. W **edytować opcje** zaznacz **tryb wstawiania** pole wyboru. To ustawienie umożliwia kliknij prawym przyciskiem myszy w oknie konsoli, aby automatycznie Wklej tekst ze Schowka.

6. W **historii poleceń** sekcji, wpisz lub wybierz liczbę z zakresu od 1 do 999 w **rozmiar buforu** pole. To ustawienie kod maszynowy poleceń, które będą znajdować się w buforze konsoli.

7. W **historii poleceń** zaznacz **Odrzuć stare duplikaty** pole wyboru w celu wyeliminowania powtarzających poleceń z buforu konsoli.

8. Kliknij przycisk **układu** kartę.

9. W **buforu ekranu** wpisz liczbę z zakresu od 1 do 9999 w **wysokość** pole. Wysokość reprezentuje liczbę wierszy danych wyjściowych, które są buforowane. Jest to maksymalna liczba wierszy, przechowywane przez wyświetlanie podczas przewijania okna konsoli. Jeśli ta liczba jest niższa niż wysokość pokazano **rozmiar okna** sekcji wysokości rozmiaru okna automatycznie zostanie zmniejszona do tej samej wartości.

10. W **rozmiar okna** wpisz liczbę z zakresu od 1 do 9999 szerokości. To oznacza liczbę znaków, które są wyświetlane w oknie konsoli. Domyślna szerokość to 80 i formatowanie danych wyjściowych programu Windows PowerShell jest przeznaczony dla tej szerokości.

11. Jeśli chcesz umieścić konsoli w określonym punkcie na pulpicie, gdy jest otwarta, wyczyść **wybór pozycji okna przez system** pole wyboru w **położenie okna** sekcji, a następnie zmień wartości w  **Po lewej** i **górnej** pól **położenie okna** sekcji.

12. Kliknij przycisk **OK**.