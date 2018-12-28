---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Jak używać okienka konsoli w środowisku Windows PowerShell ISE
ms.assetid: 44d67705-87c7-4a69-a53e-6471fdebb757
ms.openlocfilehash: 5bbbdd3b1f0324ff1a4f2298459f58640c4dc9a6
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405378"
---
# <a name="how-to-use-the-console-pane-in-the-windows-powershell-ise"></a>Jak używać okienka konsoli w środowisku Windows PowerShell ISE

W okienku konsoli w Windows PowerShell zintegrowane Scripting Environment (ISE) działa tak samo jak autonomiczne okna konsoli środowiska Windows PowerShell ISE.

Aby uruchamiać polecenia w okienku konsoli, wpisz polecenie, a następnie naciśnij klawisz ENTER. Aby wprowadzić kilka poleceń, które mają być wykonywane w kolejności, należy wpisać SHIFT + ENTER między poleceniami. Zobacz [sposobu użycia zakończenie karty w okienku skryptów i okienku konsoli](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) Aby uzyskać pomoc podczas wpisywania poleceń.

Aby zakończyć polecenia, na pasku narzędzi, kliknij **zatrzymać operację**, lub naciśnij klawisze CTRL + BREAK. CTRL + C umożliwia również polecenie zatrzymania, jeśli kontekst jest jednoznaczna. Na przykład jeśli zaznaczono tekst w okienku bieżącego następnie klawisze CTRL + C mapuje operacji kopiowania.

Począwszy od programu Windows PowerShell w wersji 3, okienko danych wyjściowych zostało połączone z okienka konsoli. To ma tę zaletę zachowuje się jak autonomiczną konsolę programu Windows PowerShell i eliminuje różnice w procedurach, które były potrzebne, jeśli zostały one oddzielne. Można:

- Zaznacz i skopiuj tekst z okienka konsoli do Schowka w celu wklejania w innym oknie. Zaznacz tekst, kliknij i przytrzymaj myszy w okienku danych wyjściowych podczas przeciągania myszy nad tekstem, które mają być przechwytywane. Można również użyć klawiszy strzałek kursora podczas przechowywania **SHIFT** dalsze Zaznaczanie tekstu. Następnie naciśnij klawisze CTRL + C lub kliknij przycisk **kopiowania** ikonę na pasku narzędzi.

- Wklej zaznaczony tekst w bieżącym położeniu kursora. Kliknij przycisk **Wklej** ikonę na pasku narzędzi.

- Wyczyść cały tekst w okienku konsoli. Aby wyczyścić w okienku konsoli, można kliknąć **wyczyść okienku konsoli** ikonę na pasku narzędzi lub uruchom polecenie **Clear-Host** lub jego alias **zgodny ze specyfikacją**.

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do programu Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)