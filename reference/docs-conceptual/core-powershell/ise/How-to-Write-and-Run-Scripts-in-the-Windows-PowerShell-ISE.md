---
ms.date: 08/14/2018
keywords: polecenia cmdlet programu PowerShell
title: Jak pisać i uruchamiać skrypty w środowisku Windows PowerShell ISE
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: 943752df2ecd3fce715dda0ca7ade97186620560
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133822"
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a><span data-ttu-id="eca08-103">Jak pisać i uruchamiać skrypty w środowisku Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="eca08-103">How to Write and Run Scripts in the Windows PowerShell ISE</span></span>

<span data-ttu-id="eca08-104">W tym artykule opisano sposób tworzenia, edytowania, uruchamiania i zapisać skrypty w okienku skryptów.</span><span class="sxs-lookup"><span data-stu-id="eca08-104">This article describes how to create, edit, run, and save scripts in the Script Pane.</span></span>

## <a name="how-to-create-and-run-scripts"></a><span data-ttu-id="eca08-105">Jak tworzyć i uruchamiać skrypty</span><span class="sxs-lookup"><span data-stu-id="eca08-105">How to create and run scripts</span></span>

<span data-ttu-id="eca08-106">Możesz otwierać i edytować pliki programu Windows PowerShell, w okienku skryptów.</span><span class="sxs-lookup"><span data-stu-id="eca08-106">You can open and edit Windows PowerShell files in the Script Pane.</span></span> <span data-ttu-id="eca08-107">Plików określonego typu zainteresowania w programie Windows PowerShell są pliki skryptów (ps1), pliki danych skryptu (psd1) i pliki modułów skryptów (.psm1).</span><span class="sxs-lookup"><span data-stu-id="eca08-107">Specific file types of interest in Windows PowerShell are script files (.ps1), script data files (.psd1), and script module files (.psm1).</span></span> <span data-ttu-id="eca08-108">Następujące typy plików są składni pokolorowane w edytorze okienka Skrypt.</span><span class="sxs-lookup"><span data-stu-id="eca08-108">These file types are syntax colored in the Script Pane editor.</span></span> <span data-ttu-id="eca08-109">Innych popularnych typów plików, który może zostać otwarty w okienku skryptów są pliki konfiguracji (.ps1xml), plików XML i plików tekstowych.</span><span class="sxs-lookup"><span data-stu-id="eca08-109">Other common file types you may open in the Script Pane are configuration files (.ps1xml), XML files, and text files.</span></span>

> [!NOTE]
> <span data-ttu-id="eca08-110">Zasady wykonywania programu Windows PowerShell Określa, czy można uruchamiać skrypty i załadować profilów programu Windows PowerShell i plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="eca08-110">The Windows PowerShell execution policy determines whether you can run scripts and load Windows PowerShell profiles and configuration files.</span></span> <span data-ttu-id="eca08-111">Domyślne zasady wykonywania Restricted, uniemożliwia wszystkie skrypty uruchamiania i uniemożliwia podczas ładowania profilów.</span><span class="sxs-lookup"><span data-stu-id="eca08-111">The default execution policy, Restricted, prevents all scripts from running, and prevents loading profiles.</span></span> <span data-ttu-id="eca08-112">Aby zmienić zasad wykonywania, aby umożliwić profile, aby ładować i być używane, zobacz [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) i [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).</span><span class="sxs-lookup"><span data-stu-id="eca08-112">To change the execution policy to allow profiles to load and be used, see [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) and [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).</span></span>

### <a name="to-create-a-new-script-file"></a><span data-ttu-id="eca08-113">Aby utworzyć nowy plik skryptu</span><span class="sxs-lookup"><span data-stu-id="eca08-113">To create a new script file</span></span>

<span data-ttu-id="eca08-114">Na pasku narzędzi kliknij **New**, lub na **pliku** menu, kliknij przycisk **New**.</span><span class="sxs-lookup"><span data-stu-id="eca08-114">On the toolbar, click **New**, or on the **File** menu, click **New**.</span></span> <span data-ttu-id="eca08-115">Utworzony plik pojawia się na nowej karcie pliku w ramach bieżącej karty programu PowerShell. Należy pamiętać, że na kartach programu PowerShell są widoczne tylko w przypadku więcej niż jeden.</span><span class="sxs-lookup"><span data-stu-id="eca08-115">The created file appears in a new file tab under the current PowerShell tab. Remember that the PowerShell tabs are only visible when there are more than one.</span></span> <span data-ttu-id="eca08-116">Domyślnie zostanie utworzony plik typ skryptu (ps1), ale aby można było zapisać przy użyciu nowej nazwy i rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="eca08-116">By default a file of type script (.ps1) is created, but it can be saved with a new name and extension.</span></span> <span data-ttu-id="eca08-117">W tej samej karcie programu PowerShell można utworzyć wiele plików skryptów.</span><span class="sxs-lookup"><span data-stu-id="eca08-117">Multiple script files can be created in the same PowerShell tab.</span></span>

### <a name="to-open-an-existing-script"></a><span data-ttu-id="eca08-118">Aby otworzyć istniejący skrypt</span><span class="sxs-lookup"><span data-stu-id="eca08-118">To open an existing script</span></span>

<span data-ttu-id="eca08-119">Na pasku narzędzi kliknij **Otwórz**, lub na **pliku** menu, kliknij przycisk **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="eca08-119">On the toolbar, click **Open**, or on the **File** menu, click **Open**.</span></span> <span data-ttu-id="eca08-120">W **Otwórz** oknie dialogowym Wybierz plik, który chcesz otworzyć.</span><span class="sxs-lookup"><span data-stu-id="eca08-120">In the **Open** dialog box, select the file you want to open.</span></span> <span data-ttu-id="eca08-121">Otwarty plik pojawia się na nowej karcie.</span><span class="sxs-lookup"><span data-stu-id="eca08-121">The opened file appears in a new tab.</span></span>

### <a name="to-close-a-script-tab"></a><span data-ttu-id="eca08-122">Aby zamknąć kartę skrypt</span><span class="sxs-lookup"><span data-stu-id="eca08-122">To close a script tab</span></span>

<span data-ttu-id="eca08-123">Kliknij przycisk **Zamknij** ikonę (X) karty plik, który chcesz zamknąć lub wybierz **pliku** menu i kliknij przycisk **Zamknij**.</span><span class="sxs-lookup"><span data-stu-id="eca08-123">Click the **Close** icon (X) of the file tab you want to close or select the **File** menu and click **Close**.</span></span>

<span data-ttu-id="eca08-124">Jeśli plik został zmieniony od ostatniego zapisu, zostanie wyświetlony monit zapisać lub odrzucić je.</span><span class="sxs-lookup"><span data-stu-id="eca08-124">If the file has been altered since it was last saved, you're prompted to save or discard it.</span></span>

### <a name="to-display-the-file-path"></a><span data-ttu-id="eca08-125">Aby wyświetlić ścieżkę pliku</span><span class="sxs-lookup"><span data-stu-id="eca08-125">To display the file path</span></span>

<span data-ttu-id="eca08-126">Na karcie Plik punktu do nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="eca08-126">On the file tab, point to the file name.</span></span> <span data-ttu-id="eca08-127">W pełni kwalifikowana ścieżka do pliku skryptu jest wyświetlany w etykietce narzędzia.</span><span class="sxs-lookup"><span data-stu-id="eca08-127">The fully qualified path to the script file appears in a tooltip.</span></span>

### <a name="to-run-a-script"></a><span data-ttu-id="eca08-128">Aby uruchomić skrypt</span><span class="sxs-lookup"><span data-stu-id="eca08-128">To run a script</span></span>

<span data-ttu-id="eca08-129">Na pasku narzędzi kliknij **uruchamianie skryptu**, lub na **pliku** menu, kliknij przycisk **Uruchom**.</span><span class="sxs-lookup"><span data-stu-id="eca08-129">On the toolbar, click **Run Script**, or on the **File** menu, click **Run**.</span></span>

### <a name="to-run-a-portion-of-a-script"></a><span data-ttu-id="eca08-130">Aby uruchomić część skryptu</span><span class="sxs-lookup"><span data-stu-id="eca08-130">To run a portion of a script</span></span>

1. <span data-ttu-id="eca08-131">W okienku skryptów wybierz części skryptu.</span><span class="sxs-lookup"><span data-stu-id="eca08-131">In the Script Pane, select a portion of a script.</span></span>
2. <span data-ttu-id="eca08-132">Na **pliku** menu, kliknij przycisk **Uruchom zaznaczone**, lub na pasku narzędzi kliknij **Uruchom zaznaczone**.</span><span class="sxs-lookup"><span data-stu-id="eca08-132">On the **File** menu, click **Run Selection**, or on the toolbar, click **Run Selection**.</span></span>

### <a name="to-stop-a-running-script"></a><span data-ttu-id="eca08-133">Aby zatrzymać uruchamianie skryptu</span><span class="sxs-lookup"><span data-stu-id="eca08-133">To stop a running script</span></span>

<span data-ttu-id="eca08-134">Istnieje kilka sposobów, aby zatrzymać uruchamianie skryptu.</span><span class="sxs-lookup"><span data-stu-id="eca08-134">There are several ways to stop a running script.</span></span>

- <span data-ttu-id="eca08-135">Kliknij przycisk **zatrzymać operację** na pasku narzędzi</span><span class="sxs-lookup"><span data-stu-id="eca08-135">Click **Stop Operation** on the toolbar</span></span>
- <span data-ttu-id="eca08-136">Naciśnij klawisze CTRL + BREAK</span><span class="sxs-lookup"><span data-stu-id="eca08-136">Press CTRL+BREAK</span></span>
- <span data-ttu-id="eca08-137">Wybierz **pliku** menu i kliknij przycisk **zatrzymać operację**.</span><span class="sxs-lookup"><span data-stu-id="eca08-137">Select the **File** menu and click **Stop Operation**.</span></span>

<span data-ttu-id="eca08-138">Naciśnięcie klawisza **klawisze CTRL + C** działa również, chyba że jakiś tekst jest aktualnie zaznaczona, w którym to przypadku **klawisze CTRL + C** mapuje do funkcji kopiowania zaznaczony tekst.</span><span class="sxs-lookup"><span data-stu-id="eca08-138">Pressing **CTRL+C** also works unless some text is currently selected, in which case **CTRL+C** maps to the copy function for the selected text.</span></span>

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a><span data-ttu-id="eca08-139">Jak pisać i edytowanie tekstu w okienku skryptów</span><span class="sxs-lookup"><span data-stu-id="eca08-139">How to write and edit text in the Script Pane</span></span>

<span data-ttu-id="eca08-140">Można skopiować, Wytnij, Wklej, znajdowanie i zastępowanie tekstu w okienku skryptów.</span><span class="sxs-lookup"><span data-stu-id="eca08-140">You can copy, cut, paste, find, and replace text in the Script Pane.</span></span> <span data-ttu-id="eca08-141">Można także cofnąć i wykonaj ponownie ostatnią akcję, którą właśnie wykonana.</span><span class="sxs-lookup"><span data-stu-id="eca08-141">You can also undo and redo the last action you just performed.</span></span> <span data-ttu-id="eca08-142">Skróty klawiaturowe do wykonywania tych akcji są tego samego skróty używane dla wszystkich aplikacji Windows.</span><span class="sxs-lookup"><span data-stu-id="eca08-142">The keyboard shortcuts for these actions are the same shortcuts used for all Windows applications.</span></span>

### <a name="to-enter-text-in-the-script-pane"></a><span data-ttu-id="eca08-143">Wprowadzanie tekstu w okienku skryptu</span><span class="sxs-lookup"><span data-stu-id="eca08-143">To enter text in the Script Pane</span></span>

1. <span data-ttu-id="eca08-144">Przesunięcie kursora w okienku skryptów przez kliknięcie w dowolnym miejscu w okienku skryptów lub klikając **przejdź do okienka Skrypt** w **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="eca08-144">Move the cursor to the Script Pane by clicking anywhere in the Script Pane, or by clicking **Go to Script Pane** in the **View** menu.</span></span>
2. <span data-ttu-id="eca08-145">Utwórz skrypt.</span><span class="sxs-lookup"><span data-stu-id="eca08-145">Create a script.</span></span> <span data-ttu-id="eca08-146">Kolorowanie składni i uzupełniania po naciśnięciu tabulatora zapewniają więcej możliwości edycji w środowisku Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="eca08-146">Syntax coloring and tab completion provide a richer editing experience in Windows PowerShell ISE.</span></span>
3. <span data-ttu-id="eca08-147">Zobacz [sposobu użycia zakończenie karty w okienku skryptów i okienku konsoli](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) szczegółowe informacje dotyczące korzystania z funkcji uzupełniania kartę pomagające w wpisywania.</span><span class="sxs-lookup"><span data-stu-id="eca08-147">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for details about using the tab completion feature to help in typing.</span></span>

### <a name="to-find-text-in-the-script-pane"></a><span data-ttu-id="eca08-148">Aby wyszukać tekst w okienku skryptu</span><span class="sxs-lookup"><span data-stu-id="eca08-148">To find text in the Script Pane</span></span>

1. <span data-ttu-id="eca08-149">Aby wyszukać tekst w dowolnym miejscu, naciśnij klawisz **CTRL + F** lub na **Edytuj** menu, kliknij przycisk **Znajdź w skrypcie**.</span><span class="sxs-lookup"><span data-stu-id="eca08-149">To find text anywhere, press **CTRL+F** or, on the **Edit** menu, click **Find in Script**.</span></span>
2. <span data-ttu-id="eca08-150">Aby wyszukać tekst po kursora, naciśnij klawisz **F3** lub na **Edytuj** menu, kliknij przycisk **Znajdź następny w skrypcie**.</span><span class="sxs-lookup"><span data-stu-id="eca08-150">To find text after the cursor, press **F3** or, on the **Edit** menu, click **Find Next in Script**.</span></span>
3. <span data-ttu-id="eca08-151">Aby wyszukać tekst przed kursorem, naciśnij klawisz **SHIFT + F3** lub na **Edytuj** menu, kliknij przycisk **Find Previous w skrypcie**.</span><span class="sxs-lookup"><span data-stu-id="eca08-151">To find text before the cursor, press **SHIFT+F3** or, on the **Edit** menu, click **Find Previous in Script**.</span></span>

### <a name="to-find-and-replace-text-in-the-script-pane"></a><span data-ttu-id="eca08-152">Aby znaleźć i zamienić tekst w okienku skryptu</span><span class="sxs-lookup"><span data-stu-id="eca08-152">To find and replace text in the Script Pane</span></span>

<span data-ttu-id="eca08-153">Naciśnij klawisz **CTRL + H** lub na **Edytuj** menu, kliknij przycisk **zastąpić w skrypcie**.</span><span class="sxs-lookup"><span data-stu-id="eca08-153">Press **CTRL+H** or, on the **Edit** menu, click **Replace in Script**.</span></span> <span data-ttu-id="eca08-154">Wprowadź tekst, który ma wyszukiwania oraz tekst zastępczy, naciśnij klawisz **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="eca08-154">Enter the text you want to find and the replacement text, then press **ENTER**.</span></span>

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a><span data-ttu-id="eca08-155">Aby przejść do określonego wiersza tekstu w okienku skryptu</span><span class="sxs-lookup"><span data-stu-id="eca08-155">To go to a particular line of text in the Script Pane</span></span>

1. <span data-ttu-id="eca08-156">W okienku skryptu naciśnij **CTRL + G** lub na **Edytuj** menu, kliknij przycisk **przejdź do wiersza**.</span><span class="sxs-lookup"><span data-stu-id="eca08-156">In the Script Pane, press **CTRL+G** or, on the **Edit** menu, click **Go to Line**.</span></span>

2. <span data-ttu-id="eca08-157">Wprowadź numer wiersza.</span><span class="sxs-lookup"><span data-stu-id="eca08-157">Enter a line number.</span></span>

### <a name="to-copy-text-in-the-script-pane"></a><span data-ttu-id="eca08-158">Aby skopiować tekst w okienku skryptu</span><span class="sxs-lookup"><span data-stu-id="eca08-158">To copy text in the Script Pane</span></span>

1. <span data-ttu-id="eca08-159">W okienku skryptów zaznacz tekst, który chcesz skopiować.</span><span class="sxs-lookup"><span data-stu-id="eca08-159">In the Script Pane, select the text that you want to copy.</span></span>

2. <span data-ttu-id="eca08-160">Naciśnij klawisz **klawisze CTRL + C** lub na pasku narzędzi kliknij **kopiowania** ikony, lub na **Edytuj** menu, kliknij przycisk **kopiowania**.</span><span class="sxs-lookup"><span data-stu-id="eca08-160">Press **CTRL+C** or, on the toolbar, click the **Copy** icon, or on the **Edit** menu, click **Copy**.</span></span>

### <a name="to-cut-text-in-the-script-pane"></a><span data-ttu-id="eca08-161">Aby wyciąć tekst w okienku skryptu</span><span class="sxs-lookup"><span data-stu-id="eca08-161">To cut text in the Script Pane</span></span>

1. <span data-ttu-id="eca08-162">W okienku skryptów zaznacz tekst, który chcesz wyciąć.</span><span class="sxs-lookup"><span data-stu-id="eca08-162">In the Script Pane, select the text that you want to cut.</span></span>
2. <span data-ttu-id="eca08-163">Naciśnij klawisz **CTRL + X** lub na pasku narzędzi kliknij **Wytnij** ikony, lub na **Edytuj** menu, kliknij przycisk **Wytnij**.</span><span class="sxs-lookup"><span data-stu-id="eca08-163">Press **CTRL+X** or, on the toolbar, click the **Cut** icon, or on the **Edit** menu, click **Cut**.</span></span>

### <a name="to-paste-text-into-the-script-pane"></a><span data-ttu-id="eca08-164">Aby wkleić tekst do okienko skryptu</span><span class="sxs-lookup"><span data-stu-id="eca08-164">To paste text into the Script Pane</span></span>

<span data-ttu-id="eca08-165">Naciśnij klawisz **klawisze CTRL + V** lub na pasku narzędzi kliknij **Wklej** ikony, lub na **Edytuj** menu, kliknij przycisk **Wklej**.</span><span class="sxs-lookup"><span data-stu-id="eca08-165">Press **CTRL+V** or, on the toolbar, click the **Paste** icon, or on the **Edit** menu, click **Paste**.</span></span>

### <a name="to-undo-an-action-in-the-script-pane"></a><span data-ttu-id="eca08-166">Aby cofnąć akcję w okienku skryptu</span><span class="sxs-lookup"><span data-stu-id="eca08-166">To undo an action in the Script Pane</span></span>

<span data-ttu-id="eca08-167">Naciśnij klawisz **CTRL + Z** lub na pasku narzędzi kliknij **Cofnij** ikony, lub na **Edytuj** menu, kliknij przycisk **Cofnij**.</span><span class="sxs-lookup"><span data-stu-id="eca08-167">Press **CTRL+Z** or, on the toolbar, click the **Undo** icon, or on the **Edit** menu, click **Undo**.</span></span>

### <a name="to-redo-an-action-in-the-script-pane"></a><span data-ttu-id="eca08-168">Aby ponowić operację w okienku skryptu</span><span class="sxs-lookup"><span data-stu-id="eca08-168">To redo an action in the Script Pane</span></span>

<span data-ttu-id="eca08-169">Naciśnij klawisz **CTRL + Y** lub na pasku narzędzi kliknij **wykonaj ponownie** ikony, lub na **Edytuj** menu, kliknij przycisk **wykonaj ponownie**.</span><span class="sxs-lookup"><span data-stu-id="eca08-169">Press **CTRL+Y** or, on the toolbar, click the **Redo** icon, or on the **Edit** menu, click **Redo**.</span></span>

## <a name="how-to-save-a-script"></a><span data-ttu-id="eca08-170">Jak zapisać skrypt</span><span class="sxs-lookup"><span data-stu-id="eca08-170">How to save a script</span></span>

<span data-ttu-id="eca08-171">Gwiazdka pojawia się obok nazwy skryptu, aby oznaczyć plik, który nie został zapisany, ponieważ został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="eca08-171">An asterisk appears next to the script name to mark a file that hasn't been saved since it was changed.</span></span> <span data-ttu-id="eca08-172">Gwiazdka znika, gdy plik jest zapisywany.</span><span class="sxs-lookup"><span data-stu-id="eca08-172">The asterisk disappears when the file is saved.</span></span>

### <a name="to-save-a-script"></a><span data-ttu-id="eca08-173">Aby zapisać skrypt</span><span class="sxs-lookup"><span data-stu-id="eca08-173">To save a script</span></span>

<span data-ttu-id="eca08-174">Naciśnij klawisz **CTRL + S** lub na pasku narzędzi kliknij **Zapisz** ikony, lub na **pliku** menu, kliknij przycisk **Zapisz**.</span><span class="sxs-lookup"><span data-stu-id="eca08-174">Press **CTRL+S** or, on the toolbar, click the **Save** icon, or on the **File** menu, click **Save**.</span></span>

### <a name="to-save-and-name-a-script"></a><span data-ttu-id="eca08-175">Aby zapisać i nazwę skryptu</span><span class="sxs-lookup"><span data-stu-id="eca08-175">To save and name a script</span></span>

1. <span data-ttu-id="eca08-176">Na **pliku** menu, kliknij przycisk **Zapisz jako**.</span><span class="sxs-lookup"><span data-stu-id="eca08-176">On the **File** menu, click **Save As**.</span></span> <span data-ttu-id="eca08-177">**Zapisz jako** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="eca08-177">The **Save As** dialog box will appear.</span></span>
2. <span data-ttu-id="eca08-178">W **nazwy pliku** wprowadź nazwę dla pliku.</span><span class="sxs-lookup"><span data-stu-id="eca08-178">In the **File name** box, enter a name for the file.</span></span>
3. <span data-ttu-id="eca08-179">W **Zapisz jako typ** wybierz typ pliku.</span><span class="sxs-lookup"><span data-stu-id="eca08-179">In the **Save as type** box, select a file type.</span></span> <span data-ttu-id="eca08-180">Na przykład w **Zapisz jako typ** wybierz pozycję "skryptów programu PowerShell (\*.ps1)".</span><span class="sxs-lookup"><span data-stu-id="eca08-180">For example, in the **Save as type** box, select 'PowerShell Scripts (\*.ps1)'.</span></span>
4. <span data-ttu-id="eca08-181">Kliknij przycisk**Save (Zapisz)**.</span><span class="sxs-lookup"><span data-stu-id="eca08-181">Click **Save**.</span></span>

### <a name="to-save-a-script-in-ascii-encoding"></a><span data-ttu-id="eca08-182">Aby zapisać skrypt w kodowaniu ASCII</span><span class="sxs-lookup"><span data-stu-id="eca08-182">To save a script in ASCII encoding</span></span>

<span data-ttu-id="eca08-183">Domyślnie program Windows PowerShell ISE zapisuje nowe pliki skryptu (ps1), pliki danych skryptu (psd1) i pliki modułów skryptów (.psm1) jako Unicode (BigEndianUnicode) domyślnie. Winmgmt do zapisywania skryptu a w innym kodowaniu, takich jak ASCII (ANSI), użyj **Zapisz** lub **zapisem** metod [$psISE.CurrentFile](the-ise-object-model-hierarchy.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="eca08-183">By default, Windows PowerShell ISE saves new script files (.ps1), script data files (.psd1), and script module files (.psm1) as Unicode (BigEndianUnicode) by default.Â To save a script in another encoding, such as ASCII (ANSI), use the **Save** or **SaveAs** methods on the [$psISE.CurrentFile](the-ise-object-model-hierarchy.md) object.</span></span>

<span data-ttu-id="eca08-184">Poniższe polecenie zapisuje nowy skrypt jako Mój_skrypt.ps1 z kodowaniem ASCII.</span><span class="sxs-lookup"><span data-stu-id="eca08-184">The following command saves a new script as MyScript.ps1 with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

<span data-ttu-id="eca08-185">Następujące polecenie zastępuje bieżącego pliku skryptu z plikiem o takiej samej nazwie, ale z kodowaniem ASCII.</span><span class="sxs-lookup"><span data-stu-id="eca08-185">The following command replaces the current script file with a file with the same name, but with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

<span data-ttu-id="eca08-186">Następujące polecenie pobiera kodowanie w bieżącym pliku.</span><span class="sxs-lookup"><span data-stu-id="eca08-186">The following command gets the encoding of the current file.</span></span>

```powershell
$psISE.CurrentFile.encoding
```

<span data-ttu-id="eca08-187">Windows PowerShell ISE obsługuje następujące opcje kodowania: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 i domyślne.</span><span class="sxs-lookup"><span data-stu-id="eca08-187">Windows PowerShell ISE supports the following encoding options: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8, and Default.</span></span> <span data-ttu-id="eca08-188">Wartość domyślna opcja zależy od systemu.</span><span class="sxs-lookup"><span data-stu-id="eca08-188">The value of the Default option varies with the system.</span></span>

<span data-ttu-id="eca08-189">Windows PowerShell ISE nie zmienia się kodowania plików skryptów za pomocą zapisu lub Zapisz jako polecenia.</span><span class="sxs-lookup"><span data-stu-id="eca08-189">Windows PowerShell ISE doesn't change the encoding of script files when you use the Save or Save As commands.</span></span>

## <a name="see-also"></a><span data-ttu-id="eca08-190">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eca08-190">See Also</span></span>

- [<span data-ttu-id="eca08-191">Eksplorowanie środowiska Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="eca08-191">Exploring the Windows PowerShell ISE</span></span>](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
