---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Jak używać okienka konsoli w środowisku Windows PowerShell ISE
ms.openlocfilehash: 114be19b86d98d829620a3718649bc3a3256cb07
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030566"
---
# <a name="how-to-use-the-console-pane-in-the-windows-powershell-ise"></a>Jak używać okienka konsoli w środowisku Windows PowerShell ISE

W okienku konsoli w Windows PowerShell zintegrowane Scripting Environment (ISE) działa tak samo jak autonomiczne okna konsoli środowiska Windows PowerShell ISE.

Aby uruchamiać polecenia w okienku konsoli, wpisz polecenie, a następnie naciśnij klawisz ENTER. Aby wprowadzić kilka poleceń, które mają być wykonywane w kolejności, należy wpisać SHIFT + ENTER między poleceniami. Zobacz [sposobu użycia zakończenie karty w okienku skryptów i okienku konsoli](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) Aby uzyskać pomoc podczas wpisywania poleceń.

Aby zakończyć polecenia, na pasku narzędzi, kliknij **zatrzymać operację**, lub naciśnij klawisze CTRL + BREAK. CTRL + C umożliwia również polecenie zatrzymania, jeśli kontekst jest jednoznaczna. Na przykład jeśli zaznaczono tekst w okienku bieżącego następnie klawisze CTRL + C mapuje operacji kopiowania.

Począwszy od programu Windows PowerShell w wersji 3, okienko danych wyjściowych zostało połączone z okienka konsoli. To ma tę zaletę zachowuje się jak autonomiczną konsolę programu Windows PowerShell i eliminuje różnice w procedurach, które były potrzebne, jeśli zostały one oddzielne. Możesz:

- Zaznacz i skopiuj tekst z okienka konsoli do Schowka w celu wklejania w innym oknie. Zaznacz tekst, kliknij i przytrzymaj myszy w okienku danych wyjściowych podczas przeciągania myszy nad tekstem, które mają być przechwytywane. Można również użyć klawiszy strzałek kursora podczas przechowywania **SHIFT** dalsze Zaznaczanie tekstu. Następnie naciśnij klawisze CTRL + C lub kliknij przycisk **kopiowania** ikonę na pasku narzędzi.

- Wklej zaznaczony tekst w bieżącym położeniu kursora. Kliknij przycisk **Wklej** ikonę na pasku narzędzi.

- Wyczyść cały tekst w okienku konsoli. Aby wyczyścić w okienku konsoli, można kliknąć **wyczyść okienku konsoli** ikonę na pasku narzędzi lub uruchom polecenie **Clear-Host** lub jego alias **zgodny ze specyfikacją**.

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do programu Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
