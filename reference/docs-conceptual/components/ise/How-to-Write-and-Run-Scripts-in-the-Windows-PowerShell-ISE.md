---
ms.date: 08/14/2018
keywords: polecenia cmdlet programu PowerShell
title: Jak pisać i uruchamiać skrypty w środowisku Windows PowerShell ISE
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: 61db5e18f05e8e334cd9ba6dab2cf15dee7390cc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086854"
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a>Jak pisać i uruchamiać skrypty w środowisku Windows PowerShell ISE

W tym artykule opisano sposób tworzenia, edytowania, uruchamiania i zapisać skrypty w okienku skryptów.

## <a name="how-to-create-and-run-scripts"></a>Jak tworzyć i uruchamiać skrypty

Możesz otwierać i edytować pliki programu Windows PowerShell, w okienku skryptów. Plików określonego typu zainteresowania w programie Windows PowerShell są pliki skryptów (ps1), pliki danych skryptu (psd1) i pliki modułów skryptów (.psm1). Następujące typy plików są składni pokolorowane w edytorze okienka Skrypt. Innych popularnych typów plików, który może zostać otwarty w okienku skryptów są pliki konfiguracji (.ps1xml), plików XML i plików tekstowych.

> [!NOTE]
> Zasady wykonywania programu Windows PowerShell Określa, czy można uruchamiać skrypty i załadować profilów programu Windows PowerShell i plików konfiguracji. Domyślne zasady wykonywania Restricted, uniemożliwia wszystkie skrypty uruchamiania i uniemożliwia podczas ładowania profilów. Aby zmienić zasad wykonywania, aby umożliwić profile, aby ładować i być używane, zobacz [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) i [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).

### <a name="to-create-a-new-script-file"></a>Aby utworzyć nowy plik skryptu

Na pasku narzędzi kliknij **New**, lub na **pliku** menu, kliknij przycisk **New**. Utworzony plik pojawia się na nowej karcie pliku w ramach bieżącej karty programu PowerShell. Należy pamiętać, że na kartach programu PowerShell są widoczne tylko w przypadku więcej niż jeden. Domyślnie zostanie utworzony plik typ skryptu (ps1), ale aby można było zapisać przy użyciu nowej nazwy i rozszerzenia. W tej samej karcie programu PowerShell można utworzyć wiele plików skryptów.

### <a name="to-open-an-existing-script"></a>Aby otworzyć istniejący skrypt

Na pasku narzędzi kliknij **Otwórz**, lub na **pliku** menu, kliknij przycisk **Otwórz**. W **Otwórz** oknie dialogowym Wybierz plik, który chcesz otworzyć. Otwarty plik pojawia się na nowej karcie.

### <a name="to-close-a-script-tab"></a>Aby zamknąć kartę skrypt

Kliknij przycisk **Zamknij** ikonę (X) karty plik, który chcesz zamknąć lub wybierz **pliku** menu i kliknij przycisk **Zamknij**.

Jeśli plik został zmieniony od ostatniego zapisu, zostanie wyświetlony monit zapisać lub odrzucić je.

### <a name="to-display-the-file-path"></a>Aby wyświetlić ścieżkę pliku

Na karcie Plik punktu do nazwy pliku. W pełni kwalifikowana ścieżka do pliku skryptu jest wyświetlany w etykietce narzędzia.

### <a name="to-run-a-script"></a>Aby uruchomić skrypt

Na pasku narzędzi kliknij **uruchamianie skryptu**, lub na **pliku** menu, kliknij przycisk **Uruchom**.

### <a name="to-run-a-portion-of-a-script"></a>Aby uruchomić część skryptu

1. W okienku skryptów wybierz części skryptu.
2. Na **pliku** menu, kliknij przycisk **Uruchom zaznaczone**, lub na pasku narzędzi kliknij **Uruchom zaznaczone**.

### <a name="to-stop-a-running-script"></a>Aby zatrzymać uruchamianie skryptu

Istnieje kilka sposobów, aby zatrzymać uruchamianie skryptu.

- Kliknij przycisk **zatrzymać operację** na pasku narzędzi
- Naciśnij klawisze CTRL + BREAK
- Wybierz **pliku** menu i kliknij przycisk **zatrzymać operację**.

Naciśnięcie klawisza **klawisze CTRL + C** działa również, chyba że jakiś tekst jest aktualnie zaznaczona, w którym to przypadku **klawisze CTRL + C** mapuje do funkcji kopiowania zaznaczony tekst.

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a>Jak pisać i edytowanie tekstu w okienku skryptów

Można skopiować, Wytnij, Wklej, znajdowanie i zastępowanie tekstu w okienku skryptów. Można także cofnąć i wykonaj ponownie ostatnią akcję, którą właśnie wykonana. Skróty klawiaturowe do wykonywania tych akcji są tego samego skróty używane dla wszystkich aplikacji Windows.

### <a name="to-enter-text-in-the-script-pane"></a>Wprowadzanie tekstu w okienku skryptu

1. Przesunięcie kursora w okienku skryptów przez kliknięcie w dowolnym miejscu w okienku skryptów lub klikając **przejdź do okienka Skrypt** w **widoku** menu.
2. Utwórz skrypt. Kolorowanie składni i uzupełniania po naciśnięciu tabulatora zapewniają więcej możliwości edycji w środowisku Windows PowerShell ISE.
3. Zobacz [sposobu użycia zakończenie karty w okienku skryptów i okienku konsoli](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) szczegółowe informacje dotyczące korzystania z funkcji uzupełniania kartę pomagające w wpisywania.

### <a name="to-find-text-in-the-script-pane"></a>Aby wyszukać tekst w okienku skryptu

1. Aby wyszukać tekst w dowolnym miejscu, naciśnij klawisz **CTRL + F** lub na **Edytuj** menu, kliknij przycisk **Znajdź w skrypcie**.
2. Aby wyszukać tekst po kursora, naciśnij klawisz **F3** lub na **Edytuj** menu, kliknij przycisk **Znajdź następny w skrypcie**.
3. Aby wyszukać tekst przed kursorem, naciśnij klawisz **SHIFT + F3** lub na **Edytuj** menu, kliknij przycisk **Find Previous w skrypcie**.

### <a name="to-find-and-replace-text-in-the-script-pane"></a>Aby znaleźć i zamienić tekst w okienku skryptu

Naciśnij klawisz **CTRL + H** lub na **Edytuj** menu, kliknij przycisk **zastąpić w skrypcie**. Wprowadź tekst, który ma wyszukiwania oraz tekst zastępczy, naciśnij klawisz **ENTER**.

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a>Aby przejść do określonego wiersza tekstu w okienku skryptu

1. W okienku skryptu naciśnij **CTRL + G** lub na **Edytuj** menu, kliknij przycisk **przejdź do wiersza**.

2. Wprowadź numer wiersza.

### <a name="to-copy-text-in-the-script-pane"></a>Aby skopiować tekst w okienku skryptu

1. W okienku skryptów zaznacz tekst, który chcesz skopiować.

2. Naciśnij klawisz **klawisze CTRL + C** lub na pasku narzędzi kliknij **kopiowania** ikony, lub na **Edytuj** menu, kliknij przycisk **kopiowania**.

### <a name="to-cut-text-in-the-script-pane"></a>Aby wyciąć tekst w okienku skryptu

1. W okienku skryptów zaznacz tekst, który chcesz wyciąć.
2. Naciśnij klawisz **CTRL + X** lub na pasku narzędzi kliknij **Wytnij** ikony, lub na **Edytuj** menu, kliknij przycisk **Wytnij**.

### <a name="to-paste-text-into-the-script-pane"></a>Aby wkleić tekst do okienko skryptu

Naciśnij klawisz **klawisze CTRL + V** lub na pasku narzędzi kliknij **Wklej** ikony, lub na **Edytuj** menu, kliknij przycisk **Wklej**.

### <a name="to-undo-an-action-in-the-script-pane"></a>Aby cofnąć akcję w okienku skryptu

Naciśnij klawisz **CTRL + Z** lub na pasku narzędzi kliknij **Cofnij** ikony, lub na **Edytuj** menu, kliknij przycisk **Cofnij**.

### <a name="to-redo-an-action-in-the-script-pane"></a>Aby ponowić operację w okienku skryptu

Naciśnij klawisz **CTRL + Y** lub na pasku narzędzi kliknij **wykonaj ponownie** ikony, lub na **Edytuj** menu, kliknij przycisk **wykonaj ponownie**.

## <a name="how-to-save-a-script"></a>Jak zapisać skrypt

Gwiazdka pojawia się obok nazwy skryptu, aby oznaczyć plik, który nie został zapisany, ponieważ został zmieniony. Gwiazdka znika, gdy plik jest zapisywany.

### <a name="to-save-a-script"></a>Aby zapisać skrypt

Naciśnij klawisz **CTRL + S** lub na pasku narzędzi kliknij **Zapisz** ikony, lub na **pliku** menu, kliknij przycisk **Zapisz**.

### <a name="to-save-and-name-a-script"></a>Aby zapisać i nazwę skryptu

1. Na **pliku** menu, kliknij przycisk **Zapisz jako**. **Zapisz jako** zostanie wyświetlone okno dialogowe.
2. W **nazwy pliku** wprowadź nazwę dla pliku.
3. W **Zapisz jako typ** wybierz typ pliku. Na przykład w **Zapisz jako typ** wybierz pozycję "skryptów programu PowerShell (\*.ps1)".
4. Kliknij przycisk**Save (Zapisz)**.

### <a name="to-save-a-script-in-ascii-encoding"></a>Aby zapisać skrypt w kodowaniu ASCII

Domyślnie program Windows PowerShell ISE zapisuje nowe pliki skryptu (ps1), pliki danych skryptu (psd1) i pliki modułów skryptów (.psm1) jako Unicode (BigEndianUnicode) domyślnie. Winmgmt do zapisywania skryptu a w innym kodowaniu, takich jak ASCII (ANSI), użyj **Zapisz** lub **zapisem** metod [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md) obiektu.

Poniższe polecenie zapisuje nowy skrypt jako Mój_skrypt.ps1 z kodowaniem ASCII.

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

Następujące polecenie zastępuje bieżącego pliku skryptu z plikiem o takiej samej nazwie, ale z kodowaniem ASCII.

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

Następujące polecenie pobiera kodowanie w bieżącym pliku.

```powershell
$psISE.CurrentFile.encoding
```

Windows PowerShell ISE obsługuje następujące opcje kodowania: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 i domyślne. Wartość domyślna opcja zależy od systemu.

Windows PowerShell ISE nie zmienia się kodowania plików skryptów za pomocą zapisu lub Zapisz jako polecenia.

## <a name="see-also"></a>Zobacz też

- [Eksplorowanie środowiska Windows PowerShell ISE](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
