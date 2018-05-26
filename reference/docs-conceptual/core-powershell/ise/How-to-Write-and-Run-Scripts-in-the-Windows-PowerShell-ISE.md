---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Jak pisać i uruchamiać skrypty w środowisku Windows PowerShell ISE
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: 4d7c5352ef1dac6f63a50433676068f83a920db5
ms.sourcegitcommit: 735ccab3fb3834ccd8559fab6700b798e8e5ffbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a><span data-ttu-id="c059c-103">Jak pisać i uruchamiać skrypty w środowisku Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="c059c-103">How to Write and Run Scripts in the Windows PowerShell ISE</span></span>

<span data-ttu-id="c059c-104">W tym temacie opisano sposób tworzenia, edytowania, uruchamianie i zapisywanie skryptów w okienku skryptów.</span><span class="sxs-lookup"><span data-stu-id="c059c-104">This topic describes how to create, edit, run, and save scripts in the Script Pane.</span></span>

## <a name="how-to-create-and-run-scripts"></a><span data-ttu-id="c059c-105">Jak utworzyć i uruchomić skrypty</span><span class="sxs-lookup"><span data-stu-id="c059c-105">How to create and run scripts</span></span>

<span data-ttu-id="c059c-106">Można otwierać i edytować pliki środowiska Windows PowerShell w okienku skryptów.</span><span class="sxs-lookup"><span data-stu-id="c059c-106">You can open and edit Windows PowerShell files in the Script Pane.</span></span> <span data-ttu-id="c059c-107">Typy plików określonych zainteresowań w programie Windows PowerShell są plików skryptu (ps1), pliki danych skryptu (psd1) i pliki modułu skryptu (.psm1).</span><span class="sxs-lookup"><span data-stu-id="c059c-107">Specific file types of interest in Windows PowerShell are script files (.ps1), script data files (.psd1), and script module files (.psm1).</span></span> <span data-ttu-id="c059c-108">Następujące typy plików są składni pokolorowane w edytorze okienku skryptów.</span><span class="sxs-lookup"><span data-stu-id="c059c-108">These file types are syntax colored in the Script Pane editor.</span></span> <span data-ttu-id="c059c-109">Innych popularnych typów plików, który może zostać otwarty w okienku skryptów są pliki konfiguracji (.ps1xml), plików XML i plików tekstowych.</span><span class="sxs-lookup"><span data-stu-id="c059c-109">Other common file types you may open in the Script Pane are configuration files (.ps1xml), XML files, and text files.</span></span>

> [!NOTE]
> <span data-ttu-id="c059c-110">Zasady wykonywania programu Windows PowerShell Określa, czy można uruchamiać skrypty i załadować profilów programu Windows PowerShell i plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c059c-110">The Windows PowerShell execution policy determines whether you can run scripts and load Windows PowerShell profiles and configuration files.</span></span> <span data-ttu-id="c059c-111">Domyślne zasady wykonywania Restricted, uniemożliwiają uruchamianie wszystkich skryptów i uniemożliwia profile ładowania.</span><span class="sxs-lookup"><span data-stu-id="c059c-111">The default execution policy, Restricted, prevents all scripts from running, and prevents loading profiles.</span></span> <span data-ttu-id="c059c-112">Aby zmienić zasady wykonywania umożliwia profile ładować i być używany, zobacz [Set-ExecutionPolicy [PSITPro5_Security]](https://technet.microsoft.com/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) i [about_Signing [4]](https://technet.microsoft.com/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).</span><span class="sxs-lookup"><span data-stu-id="c059c-112">To change the execution policy to allow profiles to load and be used, see [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) and [about_Signing [v4]](https://technet.microsoft.com/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).</span></span>

### <a name="to-create-a-new-script-file"></a><span data-ttu-id="c059c-113">Aby utworzyć nowy plik skryptu</span><span class="sxs-lookup"><span data-stu-id="c059c-113">To create a new script file</span></span>

<span data-ttu-id="c059c-114">Na pasku narzędzi kliknij **nowy** , lub na **pliku** menu, kliknij przycisk **nowy**.</span><span class="sxs-lookup"><span data-stu-id="c059c-114">On the toolbar, click **New** , or on the **File** menu, click **New**.</span></span> <span data-ttu-id="c059c-115">Utworzony plik pojawi się na nowej karcie pliku na karcie bieżącego środowiska PowerShell. Należy pamiętać, że na kartach programu PowerShell są widoczne tylko w przypadku istnieje więcej niż jeden.</span><span class="sxs-lookup"><span data-stu-id="c059c-115">The created file appears in a new file tab under the current PowerShell tab. Remember that the PowerShell tabs are only visible when there are more than one.</span></span> <span data-ttu-id="c059c-116">Domyślnie jest tworzony plik typ skryptu (ps1), ale można zapisać przy użyciu nowej nazwy i rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="c059c-116">By default a file of type script (.ps1) is created, but it can be saved with a new name and extension.</span></span> <span data-ttu-id="c059c-117">W tej samej karcie PowerShell można utworzyć wiele plików skryptów.</span><span class="sxs-lookup"><span data-stu-id="c059c-117">Multiple script files can be created in the same PowerShell tab.</span></span>

### <a name="to-open-an-existing-script"></a><span data-ttu-id="c059c-118">Aby otworzyć istniejący skrypt</span><span class="sxs-lookup"><span data-stu-id="c059c-118">To open an existing script</span></span>

<span data-ttu-id="c059c-119">Na pasku narzędzi kliknij **Otwórz**, lub na **pliku** menu, kliknij przycisk **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="c059c-119">On the toolbar, click **Open**, or on the **File** menu, click **Open**.</span></span> <span data-ttu-id="c059c-120">W **Otwórz** oknie dialogowym Wybierz plik, który chcesz otworzyć.</span><span class="sxs-lookup"><span data-stu-id="c059c-120">In the **Open** dialog box, select the file you want to open.</span></span> <span data-ttu-id="c059c-121">Otwarty plik pojawi się na nowej karcie.</span><span class="sxs-lookup"><span data-stu-id="c059c-121">The opened file appears in a new tab.</span></span>

### <a name="to-close-a-script-tab"></a><span data-ttu-id="c059c-122">Aby zamknąć kartę skryptu</span><span class="sxs-lookup"><span data-stu-id="c059c-122">To close a script tab</span></span>

<span data-ttu-id="c059c-123">Kliknij kartę skrypt skryptu, który ma zostać zamknięte, a następnie wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="c059c-123">Click the script tab of the script you want to close, then do one of the following:</span></span>

1. <span data-ttu-id="c059c-124">Kliknij przycisk **Zamknij** ikonę (X) na karcie skryptu.</span><span class="sxs-lookup"><span data-stu-id="c059c-124">Click the **Close** icon (X) on the script tab.</span></span>

2. <span data-ttu-id="c059c-125">Na **pliku** menu, kliknij przycisk **Zamknij**.</span><span class="sxs-lookup"><span data-stu-id="c059c-125">On the **File** menu, click **Close**.</span></span>

<span data-ttu-id="c059c-126">Jeśli plik został zmieniony od ostatniego zapisu, monit zachować lub odrzucić go.</span><span class="sxs-lookup"><span data-stu-id="c059c-126">If the file has been altered since it was last saved, you are prompted to save or discard it.</span></span>

### <a name="to-display-the-file-path"></a><span data-ttu-id="c059c-127">Aby wyświetlić ścieżkę pliku</span><span class="sxs-lookup"><span data-stu-id="c059c-127">To display the file path</span></span>

<span data-ttu-id="c059c-128">Na karcie Plik wskaż nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="c059c-128">On the file tab, point to the file name.</span></span> <span data-ttu-id="c059c-129">W pełni kwalifikowana ścieżka do pliku skryptu jest wyświetlany w etykietce narzędzia.</span><span class="sxs-lookup"><span data-stu-id="c059c-129">The fully qualified path to the script file appears in a tooltip.</span></span>

### <a name="to-run-a-script"></a><span data-ttu-id="c059c-130">Aby uruchomić skrypt</span><span class="sxs-lookup"><span data-stu-id="c059c-130">To run a script</span></span>

<span data-ttu-id="c059c-131">Na pasku narzędzi kliknij **Uruchom skrypt**, lub na **pliku** menu, kliknij przycisk **Uruchom**.</span><span class="sxs-lookup"><span data-stu-id="c059c-131">On the toolbar, click **Run Script**, or on the **File** menu, click **Run**.</span></span>

### <a name="to-run-a-portion-of-a-script"></a><span data-ttu-id="c059c-132">Aby uruchomić część skryptu</span><span class="sxs-lookup"><span data-stu-id="c059c-132">To run a portion of a script</span></span>

1. <span data-ttu-id="c059c-133">W okienku skryptów wybierz część skryptu.</span><span class="sxs-lookup"><span data-stu-id="c059c-133">In the Script Pane, select a portion of a script.</span></span>

2. <span data-ttu-id="c059c-134">Na **pliku** menu, kliknij przycisk **Uruchom zaznaczenie**, lub na pasku narzędzi kliknij **Uruchom zaznaczenie**.</span><span class="sxs-lookup"><span data-stu-id="c059c-134">On the **File** menu, click **Run Selection**, or on the toolbar, click **Run Selection**.</span></span>

### <a name="to-stop-a-running-script"></a><span data-ttu-id="c059c-135">Aby zatrzymać uruchamianie skryptu</span><span class="sxs-lookup"><span data-stu-id="c059c-135">To stop a running script</span></span>

<span data-ttu-id="c059c-136">Na pasku narzędzi kliknij **zatrzymać operację**, naciśnij klawisze CTRL + BREAK, lub na **pliku** menu, kliknij przycisk **zatrzymać operację**.</span><span class="sxs-lookup"><span data-stu-id="c059c-136">On the toolbar, click **Stop Operation**, press CTRL+BREAK, or on the **File** menu, click **Stop Operation**.</span></span> <span data-ttu-id="c059c-137">Naciśnięcie przycisku **klawisze CTRL + C** ma również zastosowanie, chyba że niektóre jest aktualnie zaznaczony tekst, w którym to przypadku **klawisze CTRL + C** mapuje funkcji kopiowania zaznaczonego tekstu.</span><span class="sxs-lookup"><span data-stu-id="c059c-137">Pressing **CTRL+C** also works unless some text is currently selected, in which case **CTRL+C** maps to the copy function for the selected text.</span></span>

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a><span data-ttu-id="c059c-138">Jak napisać i edycji tekstu w okienku skryptów</span><span class="sxs-lookup"><span data-stu-id="c059c-138">How to write and edit text in the Script Pane</span></span>

<span data-ttu-id="c059c-139">Wykonaj następujące kroki, aby edytować tekst w okienku skryptów.</span><span class="sxs-lookup"><span data-stu-id="c059c-139">Use the following steps to edit text in the Script Pane.</span></span> <span data-ttu-id="c059c-140">Można kopiowanie, wycinanie, Wklej, Znajdź i Zamień tekst.</span><span class="sxs-lookup"><span data-stu-id="c059c-140">You can copy, cut, paste, find, and replace text.</span></span> <span data-ttu-id="c059c-141">Można także cofnąć i wykonaj ponownie ostatnią akcję wykonaną po prostu.</span><span class="sxs-lookup"><span data-stu-id="c059c-141">You can also undo and redo the last action you just performed.</span></span> <span data-ttu-id="c059c-142">Skróty klawiaturowe do wykonywania tych akcji są takie same jak dla wszystkich aplikacji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="c059c-142">The keyboard shortcuts for performing these actions are the same as those used for all Windows applications.</span></span>

### <a name="to-enter-text-in-the-script-pane"></a><span data-ttu-id="c059c-143">Wprowadzanie tekstu w okienku skryptów</span><span class="sxs-lookup"><span data-stu-id="c059c-143">To enter text in the Script Pane</span></span>

1. <span data-ttu-id="c059c-144">Ustaw kursor w okienku skryptów, klikając w dowolnym miejscu w okienku skryptów lub przez kliknięcie przycisku **przejdź do okienka skryptu** w **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="c059c-144">Move the cursor to the Script Pane by clicking anywhere in the Script Pane, or by clicking **Go to Script Pane** in the **View** menu.</span></span>

2. <span data-ttu-id="c059c-145">Utwórz skrypt.</span><span class="sxs-lookup"><span data-stu-id="c059c-145">Create a script.</span></span> <span data-ttu-id="c059c-146">Kolorowanie składni i uzupełniania po naciśnięciu tabulatora Uczyń tę więcej możliwości w środowisku Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="c059c-146">Syntax coloring and tab completion make this a richer experience in Windows PowerShell ISE.</span></span>

3. <span data-ttu-id="c059c-147">Zobacz [sposobu użycia karty uzupełniania w okienku skryptów i okienku konsoli](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) szczegóły dotyczące używania funkcję uzupełniania kartę ułatwić wpisywania.</span><span class="sxs-lookup"><span data-stu-id="c059c-147">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for details about using the tab completion feature to help in typing.</span></span>

### <a name="to-find-text-in-the-script-pane"></a><span data-ttu-id="c059c-148">Aby wyszukać tekst w okienku skryptów</span><span class="sxs-lookup"><span data-stu-id="c059c-148">To find text in the Script Pane</span></span>

1. <span data-ttu-id="c059c-149">Aby wyszukać tekst w dowolnym miejscu, naciśnij klawisz **CTRL + F** lub na **Edytuj** menu, kliknij przycisk **Znajdź w skrypcie**.</span><span class="sxs-lookup"><span data-stu-id="c059c-149">To find text anywhere, press **CTRL+F** or, on the **Edit** menu, click **Find in Script**.</span></span>

2. <span data-ttu-id="c059c-150">Aby wyszukać tekst po kursora, naciśnij klawisz **F3** lub na **Edytuj** menu, kliknij przycisk **Znajdź następny w skrypcie**.</span><span class="sxs-lookup"><span data-stu-id="c059c-150">To find text after the cursor, press **F3** or, on the **Edit** menu, click **Find Next in Script**.</span></span>

3. <span data-ttu-id="c059c-151">Aby wyszukać tekst przed kursorem, naciśnij klawisz **SHIFT + F3** lub na **Edytuj** menu, kliknij przycisk **Znajdź poprzednie w skrypcie**.</span><span class="sxs-lookup"><span data-stu-id="c059c-151">To find text before the cursor, press **SHIFT+F3** or, on the **Edit** menu, click **Find Previous in Script**.</span></span>

### <a name="to-find-and-replace-text-in-the-script-pane"></a><span data-ttu-id="c059c-152">Do znajdowania i zamieniania tekstu w okienku skryptów</span><span class="sxs-lookup"><span data-stu-id="c059c-152">To find and replace text in the Script Pane</span></span>

<span data-ttu-id="c059c-153">Naciśnij klawisz **CTRL + H** lub na **Edytuj** menu, kliknij przycisk **Zamień w skrypcie**.</span><span class="sxs-lookup"><span data-stu-id="c059c-153">Press **CTRL+H** or, on the **Edit** menu, click **Replace in Script**.</span></span> <span data-ttu-id="c059c-154">Wprowadzić tekst do wyszukania i tekst, z którym chcesz go zastąpić, a następnie naciśnij klawisz **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="c059c-154">Enter both the text you want to find and the text with which you want to replace it, and then press **ENTER**.</span></span>

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a><span data-ttu-id="c059c-155">Aby przejść do określonego wiersza tekstu w okienku skryptów</span><span class="sxs-lookup"><span data-stu-id="c059c-155">To go to a particular line of text in the Script Pane</span></span>

1. <span data-ttu-id="c059c-156">W okienku skryptów, naciśnij klawisz **klawiszy CTRL + G** lub na **Edytuj** menu, kliknij przycisk **przejdź do wiersza**.</span><span class="sxs-lookup"><span data-stu-id="c059c-156">In the Script Pane, press **CTRL+G** or, on the **Edit** menu, click **Go to Line**.</span></span>

2. <span data-ttu-id="c059c-157">Wprowadź numer wiersza.</span><span class="sxs-lookup"><span data-stu-id="c059c-157">Enter a line number.</span></span>

### <a name="to-copy-text-in-the-script-pane"></a><span data-ttu-id="c059c-158">Aby skopiować tekst w okienku skryptów</span><span class="sxs-lookup"><span data-stu-id="c059c-158">To copy text in the Script Pane</span></span>

1. <span data-ttu-id="c059c-159">W okienku skryptów zaznacz tekst, który chcesz skopiować.</span><span class="sxs-lookup"><span data-stu-id="c059c-159">In the Script Pane, select the text that you want to copy.</span></span>

2. <span data-ttu-id="c059c-160">Naciśnij klawisz **klawisze CTRL + C** lub na pasku narzędzi kliknij **kopiowania** ikony, lub na **Edytuj** menu, kliknij przycisk **kopiowania**.</span><span class="sxs-lookup"><span data-stu-id="c059c-160">Press **CTRL+C** or, on the toolbar, click the **Copy** icon, or on the **Edit** menu, click **Copy**.</span></span>

### <a name="to-cut-text-in-the-script-pane"></a><span data-ttu-id="c059c-161">Aby wyciąć tekst w okienku skryptów</span><span class="sxs-lookup"><span data-stu-id="c059c-161">To cut text in the Script Pane</span></span>

1. <span data-ttu-id="c059c-162">W okienku skryptów zaznacz tekst, który chcesz wyciąć.</span><span class="sxs-lookup"><span data-stu-id="c059c-162">In the Script Pane, select the text that you want to cut.</span></span>

2. <span data-ttu-id="c059c-163">Naciśnij klawisz **CTRL + X** lub na pasku narzędzi kliknij **Wytnij** ikony, lub na **Edytuj** menu, kliknij przycisk **Wytnij**.</span><span class="sxs-lookup"><span data-stu-id="c059c-163">Press **CTRL+X** or, on the toolbar, click the **Cut** icon, or on the **Edit** menu, click **Cut**.</span></span>

### <a name="to-paste-text-into-the-script-pane"></a><span data-ttu-id="c059c-164">Wklej tekst w okienku skryptów</span><span class="sxs-lookup"><span data-stu-id="c059c-164">To paste text into the Script Pane</span></span>

<span data-ttu-id="c059c-165">Naciśnij klawisz **klawisze CTRL + V** lub na pasku narzędzi kliknij **Wklej** ikony, lub na **Edytuj** menu, kliknij przycisk **Wklej**.</span><span class="sxs-lookup"><span data-stu-id="c059c-165">Press **CTRL+V** or, on the toolbar, click the **Paste** icon, or on the **Edit** menu, click **Paste**.</span></span>

### <a name="to-undo-an-action-in-the-script-pane"></a><span data-ttu-id="c059c-166">Cofnięcie akcji w okienku skryptów</span><span class="sxs-lookup"><span data-stu-id="c059c-166">To undo an action in the Script Pane</span></span>

<span data-ttu-id="c059c-167">Naciśnij klawisz **CTRL + Z** lub na pasku narzędzi kliknij **Cofnij** ikony, lub na **Edytuj** menu, kliknij przycisk **Cofnij**.</span><span class="sxs-lookup"><span data-stu-id="c059c-167">Press **CTRL+Z** or, on the toolbar, click the **Undo** icon, or on the **Edit** menu, click **Undo**.</span></span>

### <a name="to-redo-an-action-in-the-script-pane"></a><span data-ttu-id="c059c-168">Aby ponowić operację w okienku skryptów</span><span class="sxs-lookup"><span data-stu-id="c059c-168">To redo an action in the Script Pane</span></span>

<span data-ttu-id="c059c-169">Naciśnij klawisz **CTRL + Y** lub na pasku narzędzi kliknij **wykonaj ponownie** ikony, lub na **Edytuj** menu, kliknij przycisk **wykonaj ponownie**.</span><span class="sxs-lookup"><span data-stu-id="c059c-169">Press **CTRL+Y** or, on the toolbar, click the **Redo** icon, or on the **Edit** menu, click **Redo**.</span></span>

## <a name="how-to-save-a-script"></a><span data-ttu-id="c059c-170">Jak zapisać skryptu</span><span class="sxs-lookup"><span data-stu-id="c059c-170">How to save a script</span></span>

<span data-ttu-id="c059c-171">Wykonaj następujące kroki, aby zapisać i nazwę skryptu.</span><span class="sxs-lookup"><span data-stu-id="c059c-171">Use the following steps to save and name a script.</span></span> <span data-ttu-id="c059c-172">Gwiazdka pojawia się obok nazwy skryptu do oznaczania plików, które nie zostały zapisane, ponieważ została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="c059c-172">An asterisk appears next to the script name to mark a file that has not been saved since it was altered.</span></span> <span data-ttu-id="c059c-173">Gwiazdka zniknie po zapisaniu pliku.</span><span class="sxs-lookup"><span data-stu-id="c059c-173">The asterisk disappears when the file is saved.</span></span>

### <a name="to-save-a-script"></a><span data-ttu-id="c059c-174">Aby zapisać skryptu</span><span class="sxs-lookup"><span data-stu-id="c059c-174">To save a script</span></span>

<span data-ttu-id="c059c-175">Naciśnij klawisz **CTRL + S** lub na pasku narzędzi kliknij **zapisać** ikony, lub na **pliku** menu, kliknij przycisk **zapisać**.</span><span class="sxs-lookup"><span data-stu-id="c059c-175">Press **CTRL+S** or, on the toolbar, click the **Save** icon, or on the **File** menu, click **Save**.</span></span>

### <a name="to-save-and-name-a-script"></a><span data-ttu-id="c059c-176">Aby zapisać i nazwa skryptu</span><span class="sxs-lookup"><span data-stu-id="c059c-176">To save and name a script</span></span>

1. <span data-ttu-id="c059c-177">Na **pliku** menu, kliknij przycisk **Zapisz jako**.</span><span class="sxs-lookup"><span data-stu-id="c059c-177">On the **File** menu, click **Save As**.</span></span> <span data-ttu-id="c059c-178">**Zapisz jako** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="c059c-178">The **Save As** dialog box will appear.</span></span>

2. <span data-ttu-id="c059c-179">W **nazwę pliku** wprowadź nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="c059c-179">In the **File name** box, enter a name for the file.</span></span>

3. <span data-ttu-id="c059c-180">W **Zapisz jako typ** wybierz typ pliku.</span><span class="sxs-lookup"><span data-stu-id="c059c-180">In the **Save as type** box, select a file type.</span></span> <span data-ttu-id="c059c-181">Na przykład w **Zapisz jako typ** wybierz pozycję "œPowerShell skryptów (\* .ps1)".</span><span class="sxs-lookup"><span data-stu-id="c059c-181">For example, in the **Save as type** box, select 'œPowerShell Scripts (\* .ps1)'.</span></span>

4. <span data-ttu-id="c059c-182">Kliknij przycisk**Save (Zapisz)**.</span><span class="sxs-lookup"><span data-stu-id="c059c-182">Click **Save**.</span></span>

### <a name="to-save-a-script-in-ascii-encoding"></a><span data-ttu-id="c059c-183">Aby zapisać skrypt w kodowanie ASCII</span><span class="sxs-lookup"><span data-stu-id="c059c-183">To save a script in ASCII encoding</span></span>

<span data-ttu-id="c059c-184">Domyślnie program Windows PowerShell ISE zapisuje nowych plików skryptu (ps1), pliki danych skryptu (psd1) i pliki modułu skryptu (.psm1) jako Unicode (BigEndianUnicode) domyślnie. Â można zapisać skrypt a inne kodowanie, takich jak ASCII (ANSI), użyj **zapisać** lub **SaveAs** metod [$psISE.CurrentFile](https://technet.microsoft.com/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile) obiektu.</span><span class="sxs-lookup"><span data-stu-id="c059c-184">By default, Windows PowerShell ISE saves new script files (.ps1), script data files (.psd1), and script module files (.psm1) as Unicode (BigEndianUnicode) by default.Â To save a script in another encoding, such as ASCII (ANSI), use the **Save** or **SaveAs** methods on the [$psISE.CurrentFile](https://technet.microsoft.com/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile) object.</span></span>

<span data-ttu-id="c059c-185">Poniższe polecenie zapisuje nowy skrypt jako Mój_skrypt.ps1 z kodowaniem ASCII.</span><span class="sxs-lookup"><span data-stu-id="c059c-185">The following command saves a new script as MyScript.ps1 with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

<span data-ttu-id="c059c-186">Polecenie zastępuje bieżącego pliku skryptu plik o takiej samej nazwie, ale z kodowaniem ASCII.</span><span class="sxs-lookup"><span data-stu-id="c059c-186">The following command replaces the current script file with a file with the same name, but with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

<span data-ttu-id="c059c-187">Polecenie pobiera kodowanie bieżącego pliku.</span><span class="sxs-lookup"><span data-stu-id="c059c-187">The following command gets the encoding of the current file.</span></span>

```powershell
$psISE.CurrentFile.encoding
```

<span data-ttu-id="c059c-188">Windows PowerShell ISE obsługuje następujące opcje kodowania: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 i domyślne.</span><span class="sxs-lookup"><span data-stu-id="c059c-188">Windows PowerShell ISE supports the following encoding options: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 and Default.</span></span> <span data-ttu-id="c059c-189">Wartość domyślna opcja zmienia się w systemie.</span><span class="sxs-lookup"><span data-stu-id="c059c-189">The value of the Default option varies with the system.</span></span>

<span data-ttu-id="c059c-190">Windows PowerShell ISE nie zmienia kodowanie skrypty, które zostały utworzone przez w innych edytorach, nawet jeśli używasz Zapisz lub Zapisz jako polecenia w środowisku Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="c059c-190">Windows PowerShell ISE does not change the encoding of scripts that were created by in other editors, even when you use the Save or Save As commands in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="c059c-191">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c059c-191">See Also</span></span>

- [<span data-ttu-id="c059c-192">Eksplorowanie środowiska Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="c059c-192">Exploring the Windows PowerShell ISE</span></span>](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)