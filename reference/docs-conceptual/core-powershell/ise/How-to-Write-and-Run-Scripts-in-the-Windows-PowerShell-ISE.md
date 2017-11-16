---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: "Jak napisać i uruchamianie skryptów w środowisku Windows PowerShell ISE"
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: dd3055df8c84195f0145b1a058f1d17c9c382f33
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2017
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a>Jak napisać i uruchamianie skryptów w środowisku Windows PowerShell ISE
W tym temacie opisano sposób tworzenia, edytowania, uruchamianie i zapisywanie skryptów w okienku skryptów.

## <a name="how-to-create-and-run-scripts"></a>Jak utworzyć i uruchomić skrypty
Można otwierać i edytować pliki środowiska Windows PowerShell w okienku skryptów. Typy plików określonych zainteresowań w programie Windows PowerShell są plików skryptu (ps1), pliki danych skryptu (psd1) i pliki modułu skryptu (.psm1). Następujące typy plików są składni pokolorowane w edytorze okienku skryptów. Innych popularnych typów plików, który może zostać otwarty w okienku skryptów są pliki konfiguracji (.ps1xml), plików XML i plików tekstowych.

> [!NOTE]
> Zasady wykonywania programu Windows PowerShell Określa, czy można uruchamiać skrypty i załadować profilów programu Windows PowerShell i plików konfiguracji. Domyślne zasady wykonywania Restricted, uniemożliwiają uruchamianie wszystkich skryptów i uniemożliwia profile ładowania. Aby zmienić zasady wykonywania umożliwia profile ładować i być używany, zobacz [Set-ExecutionPolicy [PSITPro5_Security]](https://technet.microsoft.com/en-us/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) i [about_Signing [4]](https://technet.microsoft.com/en-us/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).

### <a name="to-create-a-new-script-file"></a>Aby utworzyć nowy plik skryptu
Na pasku narzędzi kliknij **nowy** , lub na **pliku** menu, kliknij przycisk **nowy**. Utworzony plik pojawi się na nowej karcie pliku na karcie bieżącego środowiska PowerShell. Należy pamiętać, że na kartach programu PowerShell są widoczne tylko w przypadku istnieje więcej niż jeden. Domyślnie jest tworzony plik typ skryptu (ps1), ale można zapisać przy użyciu nowej nazwy i rozszerzenia. W tej samej karcie PowerShell można utworzyć wiele plików skryptów.

### <a name="to-open-an-existing-script"></a>Aby otworzyć istniejący skrypt
Na pasku narzędzi kliknij **Otwórz**, lub na **pliku** menu, kliknij przycisk **Otwórz**. W **Otwórz** oknie dialogowym Wybierz plik, który chcesz otworzyć. Otwarty plik pojawi się na nowej karcie.

### <a name="to-close-a-script-tab"></a>Aby zamknąć kartę skryptu
Kliknij kartę skrypt skryptu, który ma zostać zamknięte, a następnie wykonaj jedną z następujących czynności:

1. Kliknij przycisk **Zamknij** ikonę (X) na karcie skryptu.

2. Na **pliku** menu, kliknij przycisk **Zamknij**.

Jeśli plik został zmieniony od ostatniego zapisu, monit zachować lub odrzucić go.

### <a name="to-display-the-file-path"></a>Aby wyświetlić ścieżkę pliku
Na karcie Plik wskaż nazwę pliku. W pełni kwalifikowana ścieżka do pliku skryptu jest wyświetlany w etykietce narzędzia.

### <a name="to-run-a-script"></a>Aby uruchomić skrypt
Na pasku narzędzi kliknij **Uruchom skrypt**, lub na **pliku** menu, kliknij przycisk **Uruchom**.

### <a name="to-run-a-portion-of-a-script"></a>Aby uruchomić część skryptu

1. W okienku skryptów wybierz część skryptu.

2. Na **pliku** menu, kliknij przycisk **Uruchom zaznaczenie**, lub na pasku narzędzi kliknij **Uruchom zaznaczenie**.

### <a name="to-stop-a-running-script"></a>Aby zatrzymać uruchamianie skryptu
Na pasku narzędzi kliknij **zatrzymać operację**, naciśnij klawisze CTRL + BREAK, lub na **pliku** menu, kliknij przycisk **zatrzymać operację**. Naciśnięcie przycisku **klawisze CTRL + C** ma również zastosowanie, chyba że niektóre jest aktualnie zaznaczony tekst, w którym to przypadku **klawisze CTRL + C** mapuje funkcji kopiowania zaznaczonego tekstu.

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a>Jak napisać i edycji tekstu w okienku skryptów
Wykonaj następujące kroki, aby edytować tekst w okienku skryptów. Można kopiowanie, wycinanie, Wklej, Znajdź i Zamień tekst. Można także cofnąć i wykonaj ponownie ostatnią akcję wykonaną po prostu. Skróty klawiaturowe do wykonywania tych akcji są takie same jak dla wszystkich aplikacji systemu Windows.

### <a name="to-enter-text-in-the-script-pane"></a>Wprowadzanie tekstu w okienku skryptów

1. Ustaw kursor w okienku skryptów, klikając w dowolnym miejscu w okienku skryptów lub przez kliknięcie przycisku **przejdź do okienka skryptu** w **widoku** menu.

2. Utwórz skrypt. Kolorowanie składni i uzupełniania po naciśnięciu tabulatora Uczyń tę więcej możliwości w środowisku Windows PowerShell ISE.

3. Zobacz [sposobu użycia karty uzupełniania w okienku skryptów i okienku konsoli](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) szczegóły dotyczące używania funkcję uzupełniania kartę ułatwić wpisywania.

### <a name="to-find-text-in-the-script-pane"></a>Aby wyszukać tekst w okienku skryptów

1. Aby wyszukać tekst w dowolnym miejscu, naciśnij klawisz **CTRL + F** lub na **Edytuj** menu, kliknij przycisk **Znajdź w skrypcie**.

2. Aby wyszukać tekst po kursora, naciśnij klawisz **F3** lub na **Edytuj** menu, kliknij przycisk **Znajdź następny w skrypcie**.

3. Aby wyszukać tekst przed kursorem, naciśnij klawisz **SHIFT + F3** lub na **Edytuj** menu, kliknij przycisk **Znajdź poprzednie w skrypcie**.

### <a name="to-find-and-replace-text-in-the-script-pane"></a>Do znajdowania i zamieniania tekstu w okienku skryptów
Naciśnij klawisz **klawiszy CTRL + H** lub na **Edytuj** menu, kliknij przycisk **Zamień w skrypcie**. Wprowadzić tekst do wyszukania i tekst, z którym chcesz go zastąpić, a następnie naciśnij klawisz **ENTER**.

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a>Aby przejść do określonego wiersza tekstu w okienku skryptów

1. W okienku skryptów, naciśnij klawisz **klawiszy CTRL + G** lub na **Edytuj** menu, kliknij przycisk **przejdź do wiersza**.

2. Wprowadź numer wiersza.

### <a name="to-copy-text-in-the-script-pane"></a>Aby skopiować tekst w okienku skryptów

1. W okienku skryptów zaznacz tekst, który chcesz skopiować.

2. Naciśnij klawisz **klawisze CTRL + C** lub na pasku narzędzi kliknij **kopiowania** ikony, lub na **Edytuj** menu, kliknij przycisk **kopiowania**.

### <a name="to-cut-text-in-the-script-pane"></a>Aby wyciąć tekst w okienku skryptów

1. W okienku skryptów zaznacz tekst, który chcesz wyciąć.

2. Naciśnij klawisz **CTRL + X** lub na pasku narzędzi kliknij **Wytnij** ikony, lub na **Edytuj** menu, kliknij przycisk **Wytnij**.

### <a name="to-paste-text-into-the-script-pane"></a>Wklej tekst w okienku skryptów
Naciśnij klawisz **klawisze CTRL + V** lub na pasku narzędzi kliknij **Wklej** ikony, lub na **Edytuj** menu, kliknij przycisk **Wklej**.

### <a name="to-undo-an-action-in-the-script-pane"></a>Cofnięcie akcji w okienku skryptów
Naciśnij klawisz **CTRL + Z** lub na pasku narzędzi kliknij **Cofnij** ikony, lub na **Edytuj** menu, kliknij przycisk **Cofnij**.

### <a name="to-redo-an-action-in-the-script-pane"></a>Aby ponowić operację w okienku skryptów
Naciśnij klawisz **CTRL + Y** lub na pasku narzędzi kliknij **wykonaj ponownie** ikony, lub na **Edytuj** menu, kliknij przycisk **wykonaj ponownie**.

## <a name="how-to-save-a-script"></a>Jak zapisać skryptu
Wykonaj następujące kroki, aby zapisać i nazwę skryptu. Gwiazdka pojawia się obok nazwy skryptu do oznaczania plików, które nie zostały zapisane, ponieważ została zmieniona. Gwiazdka zniknie po zapisaniu pliku.

### <a name="to-save-a-script"></a>Aby zapisać skryptu
Naciśnij klawisz **CTRL + S** lub na pasku narzędzi kliknij **zapisać** ikony, lub na **pliku** menu, kliknij przycisk **zapisać**.

### <a name="to-save-and-name-a-script"></a>Aby zapisać i nazwa skryptu

1. Na **pliku** menu, kliknij przycisk **Zapisz jako**. **Zapisz jako** zostanie wyświetlone okno dialogowe.

2. W **nazwę pliku** wprowadź nazwę pliku.

3. W **Zapisz jako typ** wybierz typ pliku. Na przykład w **Zapisz jako typ** wybierz pozycję "œPowerShell skryptów (\* .ps1)".

4. Kliknij przycisk**Save (Zapisz)**.

### <a name="to-save-a-script-in-ascii-encoding"></a>Aby zapisać skrypt w kodowanie ASCII
Domyślnie program Windows PowerShell ISE zapisuje nowych plików skryptu (ps1), pliki danych skryptu (psd1) i pliki modułu skryptu (.psm1) jako Unicode (BigEndianUnicode) domyślnie. Â można zapisać skrypt a inne kodowanie, takich jak ASCII (ANSI), użyj **zapisać** lub **SaveAs** metod [$psISE.CurrentFile](https://technet.microsoft.com/en-us/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile) obiektu.

Poniższe polecenie zapisuje nowy skrypt jako Mój_skrypt.ps1 z kodowaniem ASCII.

```
$psise.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

Polecenie zastępuje bieżącego pliku skryptu plik o takiej samej nazwie, ale z kodowaniem ASCII.

```
$psise.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

Polecenie pobiera kodowanie bieżącego pliku.

```
$psise.CurrentFile.encoding
```

Windows PowerShell ISE obsługuje następujące opcje kodowania: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 i domyślne. Wartość domyślna opcja zmienia się w systemie.

Windows PowerShell ISE nie zmienia kodowanie skrypty, które zostały utworzone przez w innych edytorach, nawet jeśli używasz Zapisz lub Zapisz jako polecenia w środowisku Windows PowerShell ISE.

## <a name="see-also"></a>Zobacz też
- [Przy użyciu programu Windows PowerShell ISE](Using-the-Windows-PowerShell-ISE.md)

