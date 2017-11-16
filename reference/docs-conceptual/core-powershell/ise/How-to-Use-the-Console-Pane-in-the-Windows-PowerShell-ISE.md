---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: "Jak używać okienku konsoli w środowisku Windows PowerShell ISE"
ms.assetid: 44d67705-87c7-4a69-a53e-6471fdebb757
ms.openlocfilehash: 59e97bbc12269d855c4f3715171636647d4cc634
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2017
---
# <a name="how-to-use-the-console-pane-in-the-windows-powershell-ise"></a>Jak używać okienku konsoli w środowisku Windows PowerShell ISE
W okienku konsoli w Windows PowerShell Integrated Scripting Environment (ISE) działa tak samo jak autonomiczny okna konsoli programu Windows PowerShell ISE.

Aby uruchomić polecenie w okienku konsoli, wpisz polecenie, a następnie naciśnij klawisz ENTER. Aby wprowadzić wiele poleceń, które mają być wykonywane w kolejności, wpisz SHIFT + ENTER między poleceń. Zobacz [sposobu użycia karty uzupełniania w okienku skryptów i okienku konsoli](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) pomoc w wpisywania poleceń.

Aby zatrzymać polecenia na pasku narzędzi, kliknij przycisk **zatrzymać operację**, lub naciśnij klawisze CTRL + BREAK. Polecenie zatrzymania, jeśli kontekst jest jednoznaczne umożliwia także klawisze CTRL + C. Na przykład jeśli tekst został wybrany w okienku bieżący, następnie klawisze CTRL + C mapuje operacji kopiowania.

Począwszy od programu Windows PowerShell w wersji 3, w okienku danych wyjściowych zostało połączone z okienka konsoli. To przynosi korzyści związane z zachowuje się jak autonomiczną konsolę programu Windows PowerShell i eliminuje różnice w procedurach, które były potrzebne, jeśli zostały one oddzielne. Można:

- Zaznacz i skopiuj tekst z okienka konsoli do Schowka wklejania w innym oknie. Zaznacz tekst, kliknij i przytrzymaj myszy w okienku danych wyjściowych podczas przeciągania myszy nad tekstem, które mają być przechwytywane. Można również użyj klawiszy strzałek kursora podczas gospodarstwa **SHIFT** zaznacz tekst. Następnie naciśnij klawisze CTRL + C lub kliknij przycisk **kopiowania** ikonę na pasku narzędzi.

- Wklej zaznaczonego tekstu w bieżącym położeniu kursora. Kliknij przycisk **Wklej** ikonę na pasku narzędzi.

- Wyczyść cały tekst w okienku konsoli. Aby wyczyścić okienku konsoli, można kliknąć **wyczyść okienku konsoli** ikonę na pasku narzędzi lub uruchom polecenie **Clear-Host** lub jego alias **ze specyfikacją cls**.

## <a name="see-also"></a>Zobacz też
- [Przy użyciu programu Windows PowerShell ISE](Using-the-Windows-PowerShell-ISE.md)

