---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: "Jakie s nowego w środowisku PowerShell 50 ISE"
ms.assetid: 38648d47-7c27-4b37-a40e-ad29948519c2
ms.openlocfilehash: 9fd25a4759602bebf2b5df2c17d0c816a15e5e2b
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="what39s-new-in-the-windows-powershell-ise"></a><span data-ttu-id="f0dc6-103">Co&#39;s nowego w środowisku Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="f0dc6-103">What&#39;s New in the Windows PowerShell ISE</span></span>
<span data-ttu-id="f0dc6-104">W tym temacie opisano nowe i zaktualizowane funkcje, które zostały wprowadzone w wersjach programu Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="f0dc6-104">This topic explains the new and updated features that have been introduced in versions of Windows PowerShell  Integrated Scripting Environment (ISE).</span></span>

## <a name="feature-description"></a><span data-ttu-id="f0dc6-105">Opis funkcji</span><span class="sxs-lookup"><span data-stu-id="f0dc6-105">Feature description</span></span>
<span data-ttu-id="f0dc6-106">Windows PowerShell ISE to aplikacja hosta, która umożliwia zapis, uruchamianie i testowanie skryptów i modułów w środowisku graficznym i intuicyjne.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-106">The Windows PowerShell ISE is a host application that enables you to write, run, and test scripts and modules in a graphical and intuitive environment.</span></span> <span data-ttu-id="f0dc6-107">Najważniejsze funkcje takie jak kolorowanie składni, karcie ukończenia, debugowania visual zgodności Unicode i Pomoc kontekstowa zapewniają bogate środowisko obsługi skryptów.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-107">Key features such as syntax-coloring, tab completion, visual debugging, Unicode compliance, and context-sensitive Help provide a rich scripting experience.</span></span>

<span data-ttu-id="f0dc6-108">Omówienie programu Windows PowerShell ISE, zobacz [omówienie Windows PowerShell zintegrowane skryptów środowiska](https://technet.microsoft.com/library/3c1892c2-bf84-4cb6-af26-1f453be9e671).</span><span class="sxs-lookup"><span data-stu-id="f0dc6-108">For an overview of Windows PowerShell ISE, see [Windows PowerShell Integrated Scripting Environment overview](https://technet.microsoft.com/library/3c1892c2-bf84-4cb6-af26-1f453be9e671).</span></span>

## <a name="new-and-changed-functionality-in-windows-powershell-ise"></a><span data-ttu-id="f0dc6-109">Nowe i zmienione funkcje w środowisku Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="f0dc6-109">New and changed functionality in Windows PowerShell ISE</span></span>
<span data-ttu-id="f0dc6-110">W poniższej tabeli przedstawiono nowe i zmienione funkcje w tej wersji programu Windows PowerShell ISE w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-110">The following table lists the new and changed features for this release of Windows PowerShell ISE in Windows PowerShell.</span></span>

|<span data-ttu-id="f0dc6-111">Funkcja</span><span class="sxs-lookup"><span data-stu-id="f0dc6-111">Feature/functionality</span></span>|<span data-ttu-id="f0dc6-112">Windows PowerShell ISE 4.0</span><span class="sxs-lookup"><span data-stu-id="f0dc6-112">Windows PowerShell ISE 4.0</span></span>|<span data-ttu-id="f0dc6-113">Windows PowerShell ISE 3.0</span><span class="sxs-lookup"><span data-stu-id="f0dc6-113">Windows PowerShell ISE 3.0</span></span>|<span data-ttu-id="f0dc6-114">Windows PowerShell ISE 2.0</span><span class="sxs-lookup"><span data-stu-id="f0dc6-114">Windows PowerShell ISE 2.0</span></span>|
|--------------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
|<span data-ttu-id="f0dc6-115">**[IntelliSense](#intellisense)**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-115">**[IntelliSense](#intellisense)**</span></span>|<span data-ttu-id="f0dc6-116">X</span><span class="sxs-lookup"><span data-stu-id="f0dc6-116">X</span></span>|<span data-ttu-id="f0dc6-117">X</span><span class="sxs-lookup"><span data-stu-id="f0dc6-117">X</span></span>||
|<span data-ttu-id="f0dc6-118">**[Wstawki kodu programu](#snippets)**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-118">**[Snippets](#snippets)**</span></span>|<span data-ttu-id="f0dc6-119">X</span><span class="sxs-lookup"><span data-stu-id="f0dc6-119">X</span></span>|<span data-ttu-id="f0dc6-120">X</span><span class="sxs-lookup"><span data-stu-id="f0dc6-120">X</span></span>||
|<span data-ttu-id="f0dc6-121">**[Dodatkowe narzędzia](#add-on-tools)**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-121">**[Add-on Tools](#add-on-tools)**</span></span>|<span data-ttu-id="f0dc6-122">X</span><span class="sxs-lookup"><span data-stu-id="f0dc6-122">X</span></span>|<span data-ttu-id="f0dc6-123">X</span><span class="sxs-lookup"><span data-stu-id="f0dc6-123">X</span></span>||
|<span data-ttu-id="f0dc6-124">**[Menedżer ponownego uruchamiania i automatycznego zapisywania](#restart-manager-and-auto-save)**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-124">**[Restart Manager and Auto-save](#restart-manager-and-auto-save)**</span></span>|<span data-ttu-id="f0dc6-125">X</span><span class="sxs-lookup"><span data-stu-id="f0dc6-125">X</span></span>|<span data-ttu-id="f0dc6-126">X</span><span class="sxs-lookup"><span data-stu-id="f0dc6-126">X</span></span>||
|<span data-ttu-id="f0dc6-127">**[Lista ostatnio używanych](#most-recently-used-list)**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-127">**[Most-recently used list](#most-recently-used-list)**</span></span>|<span data-ttu-id="f0dc6-128">X</span><span class="sxs-lookup"><span data-stu-id="f0dc6-128">X</span></span>|<span data-ttu-id="f0dc6-129">X</span><span class="sxs-lookup"><span data-stu-id="f0dc6-129">X</span></span>||
|<span data-ttu-id="f0dc6-130">**[W okienku konsoli](#console-pane)**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-130">**[Console Pane](#console-pane)**</span></span>|<span data-ttu-id="f0dc6-131">X</span><span class="sxs-lookup"><span data-stu-id="f0dc6-131">X</span></span>|<span data-ttu-id="f0dc6-132">X</span><span class="sxs-lookup"><span data-stu-id="f0dc6-132">X</span></span>||
|<span data-ttu-id="f0dc6-133">**[Przełączniki wiersza polecenia](#command-line-switches)**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-133">**[Command-line switches](#command-line-switches)**</span></span>|<span data-ttu-id="f0dc6-134">X</span><span class="sxs-lookup"><span data-stu-id="f0dc6-134">X</span></span>|<span data-ttu-id="f0dc6-135">X</span><span class="sxs-lookup"><span data-stu-id="f0dc6-135">X</span></span>||
|<span data-ttu-id="f0dc6-136">**[Nowe funkcje edytora](#new-editor-features)**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-136">**[New editor features](#new-editor-features)**</span></span>|<span data-ttu-id="f0dc6-137">X</span><span class="sxs-lookup"><span data-stu-id="f0dc6-137">X</span></span>|<span data-ttu-id="f0dc6-138">X</span><span class="sxs-lookup"><span data-stu-id="f0dc6-138">X</span></span>||
|<span data-ttu-id="f0dc6-139">**[Nowe okno podglądu pomocy](#new-help-viewer-window)**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-139">**[New Help viewer window](#new-help-viewer-window)**</span></span>|<span data-ttu-id="f0dc6-140">X</span><span class="sxs-lookup"><span data-stu-id="f0dc6-140">X</span></span>|<span data-ttu-id="f0dc6-141">X</span><span class="sxs-lookup"><span data-stu-id="f0dc6-141">X</span></span>||
|<span data-ttu-id="f0dc6-142">**[Pokaż polecenia cmdlet](#show-command-cmdlet)**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-142">**[Show-Command cmdlet](#show-command-cmdlet)**</span></span>|<span data-ttu-id="f0dc6-143">X</span><span class="sxs-lookup"><span data-stu-id="f0dc6-143">X</span></span>|<span data-ttu-id="f0dc6-144">X</span><span class="sxs-lookup"><span data-stu-id="f0dc6-144">X</span></span>||

### <a name="intellisense"></a><span data-ttu-id="f0dc6-145">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="f0dc6-145">IntelliSense</span></span>
<span data-ttu-id="f0dc6-146">**Dodane w ISE 3.0**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-146">**Added in ISE 3.0**</span></span>

<span data-ttu-id="f0dc6-147">IntelliSense to funkcja automatycznego uzupełniania pomocy, która jest częścią programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-147">IntelliSense is an automatic-completion assistance feature that is part of Windows PowerShell ISE.</span></span> <span data-ttu-id="f0dc6-148">Funkcja IntelliSense wyświetla aktywne menu potencjalnie zgodnych poleceń cmdlet, parametry, wartości parametrów, plików lub folderów podczas pisania.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-148">IntelliSense displays clickable menus of potentially matching cmdlets, parameters, parameter values, files, or folders as you type.</span></span>

<span data-ttu-id="f0dc6-149">**Jakie korzyści zapewnia ta zmiana?**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-149">**What value does this change add?**</span></span>

<span data-ttu-id="f0dc6-150">Z dodatkiem IntelliSense łatwiej jest odnajdywanie poleceń cmdlet i składni, korzystając z programu Windows PowerShell ISE do tworzenia skryptów.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-150">With the addition of IntelliSense, it is easier to discover cmdlets and syntax when you use Windows PowerShell ISE to create scripts.</span></span> <span data-ttu-id="f0dc6-151">Aby dowiedzieć się więcej środowiska Windows PowerShell, podczas tworzenia nowego skryptów umożliwia także programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-151">You can also use Windows PowerShell ISE to learn Windows PowerShell while you create new scripts.</span></span>

<span data-ttu-id="f0dc6-152">**Co się zmieniło stanie?**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-152">**What works differently?**</span></span>

<span data-ttu-id="f0dc6-153">Podczas wpisywania poleceń cmdlet programu Windows PowerShell ISE 3.0 lub nowszego, wyświetla przewijanego i aktywne menu, umożliwiając Przeglądaj i wybierz odpowiednie polecenia.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-153">When you type cmdlets in the Windows PowerShell ISE 3.0 or later, a scrollable and clickable menu displays, allowing you to browse and select the appropriate commands.</span></span>

### <a name="snippets"></a><span data-ttu-id="f0dc6-154">Wstawki kodu programu</span><span class="sxs-lookup"><span data-stu-id="f0dc6-154">Snippets</span></span>
<span data-ttu-id="f0dc6-155">**Dodane w ISE 3.0**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-155">**Added in ISE 3.0**</span></span>

<span data-ttu-id="f0dc6-156">*Wstawki kodu programu* są krótkich fragmentów kodu programu Windows PowerShell, który można wstawić do skryptów tworzenia w środowisku Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-156">*Snippets* are short sections of Windows PowerShell code that you can insert into the scripts you create in Windows PowerShell ISE.</span></span> <span data-ttu-id="f0dc6-157">Windows PowerShell ISE jest dostarczany z domyślnym zestawem fragmentów.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-157">Windows PowerShell ISE comes with a default set of snippets.</span></span> <span data-ttu-id="f0dc6-158">Wstawki kodu programu można dodać za pomocą **nowy fragment** polecenia cmdlet podczas pracy w środowisku Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-158">You can add snippets by using the **New-Snippet** cmdlet while working in Windows PowerShell ISE.</span></span>

<span data-ttu-id="f0dc6-159">**Jakie korzyści zapewnia ta zmiana?**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-159">**What value does this change add?**</span></span>

<span data-ttu-id="f0dc6-160">Przy użyciu fragmentów, można szybko utworzyć i tworzenia skryptów do automatyzacji środowiska.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-160">By using snippets, you can quickly assemble and create scripts to automate your environment.</span></span>

<span data-ttu-id="f0dc6-161">**Co się zmieniło stanie?**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-161">**What works differently?**</span></span>

<span data-ttu-id="f0dc6-162">Umożliwia wstawki na w programie Windows PowerShell 3.0 lub nowszej, **Edytuj** menu, kliknij przycisk **Start wstawki**, lub naciśnij klawisz **Ctrl-J**.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-162">To use snippets in Windows PowerShell 3.0 or later, on the **Edit** menu, click **Start Snippets**, or press **Ctrl-J**.</span></span>

### <a name="add-on-tools"></a><span data-ttu-id="f0dc6-163">Dodatkowe narzędzia</span><span class="sxs-lookup"><span data-stu-id="f0dc6-163">Add-on tools</span></span>
<span data-ttu-id="f0dc6-164">**Dodane w programie PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-164">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="f0dc6-165">Windows PowerShell ISE obsługuje teraz dodatkowe narzędzia, które kontrolki Windows Presentation Foundation (WPF), które są dodawane przy użyciu modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-165">Windows PowerShell ISE now supports add-on tools, which are Windows Presentation Foundation (WPF) controls that are added by using the object model.</span></span> <span data-ttu-id="f0dc6-166">Dodatkowe narzędzia mogą być wyświetlane jako pionowy czy poziomy okienko w konsoli.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-166">Add-on tools can be displayed as a vertical or horizontal pane in the console.</span></span> <span data-ttu-id="f0dc6-167">Wiele dodatków w okienku są wyświetlane jako formant z kartami.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-167">Multiple add-on tools in a pane are displayed as a tabbed control.</span></span> <span data-ttu-id="f0dc6-168">Można również dodać lub usunąć dodatkowe narzędzia, które są tworzone przez strony firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-168">You can also add or remove add-on tools that are produced by non-Microsoft parties.</span></span> <span data-ttu-id="f0dc6-169">Aby uzyskać więcej informacji o sposobie importowania lub usuń dodatkowe narzędzia, zobacz [operacje programu Windows PowerShell ISE](http://technet.microsoft.com/library/cc732148.aspx).</span><span class="sxs-lookup"><span data-stu-id="f0dc6-169">For more information about how to import or remove add-on tools, see [Windows PowerShell ISE Operations](http://technet.microsoft.com/library/cc732148.aspx).</span></span>

<span data-ttu-id="f0dc6-170">**Jakie korzyści zapewnia ta zmiana?**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-170">**What value does this change add?**</span></span>

<span data-ttu-id="f0dc6-171">Dodatki umożliwiają rozszerzanie i dostosowywanie programu Windows PowerShell ISE z narzędziami, które mogą poprawić obsługę skryptów lub dodać funkcje do programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-171">Add-ons allow you to extend and customize Windows PowerShell ISE with tools that can enhance your scripting experience or add functionality to Windows PowerShell ISE.</span></span>

<span data-ttu-id="f0dc6-172">**Co się zmieniło stanie?**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-172">**What works differently?**</span></span>

<span data-ttu-id="f0dc6-173">Wyposażone w środowisku Windows PowerShell ISE 3.0 i nowszych **polecenia** dodatku.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-173">Windows PowerShell ISE 3.0 and later come with the **Commands** add-on.</span></span> <span data-ttu-id="f0dc6-174">**Polecenia** dodatek umożliwia przeglądanie poleceń cmdlet i dostępu Pomoc na temat polecenia cmdlet side-by-side z **skryptu** i **konsoli** okienka.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-174">The **Commands** add-on allows you to browse cmdlets, and access help about the cmdlets side-by-side with the **Script** and **Console** Panes.</span></span>

<span data-ttu-id="f0dc6-175">Dodatkowe dodatki znajduje się za pomocą **witryny sieci Web otwórz dodatkowe narzędzia** na **dodatki** menu.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-175">Additional add-ons can be found by using the **Open Add-on Tools Website** command on the **Add-ons** menu.</span></span>

### <a name="restart-manager-and-auto-save"></a><span data-ttu-id="f0dc6-176">Ponownie uruchom Menedżera i automatycznego zapisywania</span><span class="sxs-lookup"><span data-stu-id="f0dc6-176">Restart manager and auto-save</span></span>
<span data-ttu-id="f0dc6-177">**Dodane w programie PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-177">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="f0dc6-178">Windows PowerShell ISE teraz automatycznie zapisuje Otwórz skrypty co dwie minuty w innej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-178">Windows PowerShell ISE now automatically saves your open scripts every two minutes, in a separate location.</span></span>  <span data-ttu-id="f0dc6-179">Czy programu Windows PowerShell ISE przestanie działać, jeśli system operacyjny zostanie ponownie uruchomiony, po uruchomieniu programu Windows PowerShell ISE, odzyskuje skrypty, które były Otwórz podczas ostatniej sesji, nawet jeśli skrypty nie zostały zapisane.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-179">If Windows PowerShell ISE stops working, or if the operating system is restarted, after Windows PowerShell ISE restarts, it recovers scripts that were open in the last session, even if the scripts were not saved.</span></span>

<span data-ttu-id="f0dc6-180">Aby zmienić interwał automatycznego zapisywania, uruchom następujące polecenie, w okienku konsoli: **$psise. Options.AutoSaveMinuteInterval**.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-180">To change the automatic saving interval, run the following command in the Console pane: **$psise.Options.AutoSaveMinuteInterval**.</span></span>

<span data-ttu-id="f0dc6-181">**Jakie korzyści zapewnia ta zmiana?**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-181">**What value does this change add?**</span></span>

<span data-ttu-id="f0dc6-182">Teraz możesz pracować w środowisku Windows PowerShell ISE wiedząc, że Otwórz skrypty są automatycznie zapisywane w przypadku nieoczekiwane ponowne uruchomienie.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-182">You can now work within Windows PowerShell ISE knowing that your open scripts are automatically saved in the event of an unexpected restart.</span></span>

<span data-ttu-id="f0dc6-183">**Co się zmieniło stanie?**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-183">**What works differently?**</span></span>

<span data-ttu-id="f0dc6-184">Program Windows PowerShell ISE 2.0 nie jest zapisywany skrypty automatycznie w przypadku ponownego uruchomienia komputera.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-184">Windows PowerShell ISE 2.0 does not save the scripts automatically in the event of a restart.</span></span>

### <a name="most-recently-used-list"></a><span data-ttu-id="f0dc6-185">Lista ostatnio używanych</span><span class="sxs-lookup"><span data-stu-id="f0dc6-185">Most-recently used list</span></span>
<span data-ttu-id="f0dc6-186">**Dodane w programie PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-186">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="f0dc6-187">Windows PowerShell ISE ma teraz listy ostatnio używanych plików.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-187">Windows PowerShell ISE now has a most-recently used list for files.</span></span> <span data-ttu-id="f0dc6-188">Po otwarciu pliku w środowisku Windows PowerShell ISE, plik zostanie dodany do listy ostatnio używanych na **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-188">When you open a file in Windows PowerShell ISE, the file is added to the most-recently used list on the **File** menu.</span></span>

<span data-ttu-id="f0dc6-189">Aby zmienić domyślną liczbę plików z listy ostatnio używanych, uruchom następujące polecenie, w okienku konsoli: **$psise. Options.MruCount**.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-189">To change the default number of files in the most-recently used list, run the following command in the Console Pane: **$psise.Options.MruCount**.</span></span>

<span data-ttu-id="f0dc6-190">**Jakie korzyści zapewnia ta zmiana?**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-190">**What value does this change add?**</span></span>

<span data-ttu-id="f0dc6-191">Lista ostatnio używanych umożliwia teraz łatwo uzyskiwać dostęp do często używanych plików.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-191">You can now use the most-recently used list to easily access your frequently-used files.</span></span>

<span data-ttu-id="f0dc6-192">**Co się zmieniło stanie?**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-192">**What works differently?**</span></span>

<span data-ttu-id="f0dc6-193">Program Windows PowerShell ISE 2.0 nie ma listy ostatnio używanych.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-193">Windows PowerShell ISE 2.0 does not have a most-recently used list.</span></span>

### <a name="console-pane"></a><span data-ttu-id="f0dc6-194">W okienku konsoli</span><span class="sxs-lookup"><span data-stu-id="f0dc6-194">Console Pane</span></span>
<span data-ttu-id="f0dc6-195">**Dodane w programie PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-195">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="f0dc6-196">Oddzielne polecenia i okienka wyjściowego, które były dostępne w pierwszej wersji programu Windows PowerShell ISE zostały połączone w jednym okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-196">The separate Command and Output Panes that were available in the first release of Windows PowerShell ISE have been combined into a single Console Pane.</span></span> <span data-ttu-id="f0dc6-197">W okienku konsoli jest podobnych funkcji i wyglądu do typowych konsoli środowiska Windows PowerShell, ale zawiera następujące ulepszenia (większość są opisane w tym temacie).</span><span class="sxs-lookup"><span data-stu-id="f0dc6-197">The Console Pane is similar in function and appearance to a typical Windows PowerShell console, but it includes the following enhancements (most are described in this topic).</span></span>

- <span data-ttu-id="f0dc6-198">Kolorowanie składni dla tekstu wejściowego (nie tekstu wyjściowego), w tym składni XML</span><span class="sxs-lookup"><span data-stu-id="f0dc6-198">Syntax coloring for input text (not output text), including XML syntax</span></span>

- <span data-ttu-id="f0dc6-199">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="f0dc6-199">IntelliSense</span></span>

- <span data-ttu-id="f0dc6-200">Parowanie nawiasów klamrowych</span><span class="sxs-lookup"><span data-stu-id="f0dc6-200">Brace matching</span></span>

- <span data-ttu-id="f0dc6-201">Wskazanie błędu</span><span class="sxs-lookup"><span data-stu-id="f0dc6-201">Error indication</span></span>

- <span data-ttu-id="f0dc6-202">Pełna obsługa formatu Unicode</span><span class="sxs-lookup"><span data-stu-id="f0dc6-202">Full Unicode support</span></span>

- <span data-ttu-id="f0dc6-203">**F1** pomocy kontekstowej</span><span class="sxs-lookup"><span data-stu-id="f0dc6-203">**F1** context-sensitive help</span></span>

- <span data-ttu-id="f0dc6-204">**CTRL + F1** kontekstowa Pokaż — polecenie</span><span class="sxs-lookup"><span data-stu-id="f0dc6-204">**Ctrl+F1** context-sensitive Show-Command</span></span>

- <span data-ttu-id="f0dc6-205">Złożonym i pomocy technicznej od prawej do lewej</span><span class="sxs-lookup"><span data-stu-id="f0dc6-205">Complex script and right-to-left support</span></span>

- <span data-ttu-id="f0dc6-206">Obsługa czcionek</span><span class="sxs-lookup"><span data-stu-id="f0dc6-206">Font support</span></span>

- <span data-ttu-id="f0dc6-207">Powiększenie</span><span class="sxs-lookup"><span data-stu-id="f0dc6-207">Zoom</span></span>

- <span data-ttu-id="f0dc6-208">Tryby wierszu wybierz i wybierz bloku</span><span class="sxs-lookup"><span data-stu-id="f0dc6-208">Line-select and block-select modes</span></span>

- <span data-ttu-id="f0dc6-209">Zachowania wpisaną zawartość w wierszu polecenia, po naciśnięciu **się** strzałkę, aby wyświetlić historię w konsoli programu</span><span class="sxs-lookup"><span data-stu-id="f0dc6-209">Preservation of typed content at the command line when you press the **Up** arrow to view history in the console</span></span>

<span data-ttu-id="f0dc6-210">**Jakie korzyści zapewnia ta zmiana?**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-210">**What value does this change add?**</span></span>

<span data-ttu-id="f0dc6-211">Dodanie tych zmian w okienku konsoli udostępnia środowisko obsługi skryptów bardziej spójny z interfejsem konsoli.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-211">The addition of these Console Pane changes provides a scripting experience that is more consistent with the console interface.</span></span>

<span data-ttu-id="f0dc6-212">**Co się zmieniło stanie?**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-212">**What works differently?**</span></span>

<span data-ttu-id="f0dc6-213">Program Windows PowerShell ISE 2.0 ma oddzielne polecenia i okienka wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-213">Windows PowerShell ISE 2.0 has separate Command and Output Panes.</span></span>

### <a name="command-line-switches"></a><span data-ttu-id="f0dc6-214">Przełączniki wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="f0dc6-214">Command-line switches</span></span>
<span data-ttu-id="f0dc6-215">**Dodane w programie PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-215">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="f0dc6-216">Jeśli w wierszu polecenia można uruchomić programu Windows PowerShell ISE (przez wpisanie **powershell_ise.exe**), można dodać następujących nowych przełączników wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-216">If you start Windows PowerShell ISE from the command line (by typing **powershell_ise.exe**), you can add the following new command-line switches.</span></span>

- <span data-ttu-id="f0dc6-217">*-NoProfile*: uruchamia programu Windows PowerShell ISE bez uruchamiania **$profile**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-217">*-NoProfile*: Starts Windows PowerShell ISE without running **$profile**</span></span>

- <span data-ttu-id="f0dc6-218">*-Help*: Wyświetla okna Pomoc</span><span class="sxs-lookup"><span data-stu-id="f0dc6-218">*-Help*: Displays a Help window</span></span>

- <span data-ttu-id="f0dc6-219">*-mta*: uruchamia programu Windows PowerShell ISE w trybie apartment wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-219">*-mta*: Starts Windows PowerShell ISE in multithreaded apartment mode.</span></span> <span data-ttu-id="f0dc6-220">Domyślny tryb działania programu Windows PowerShell ISE jest tryb jednowątkowego apartamentu lub *- sta*.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-220">The default operation mode for Windows PowerShell ISE is single-threaded apartment mode, or *-sta*.</span></span>

<span data-ttu-id="f0dc6-221">**Jakie korzyści zapewnia ta zmiana?**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-221">**What value does this change add?**</span></span>

<span data-ttu-id="f0dc6-222">Dodanie tych przełączników wiersza polecenia umożliwia kontrolowanie środowisko, w którym działa program Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-222">The addition of these command-line switches allows you to control the environment in which the Windows PowerShell ISE runs.</span></span>

<span data-ttu-id="f0dc6-223">**Co się zmieniło stanie?**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-223">**What works differently?**</span></span>

<span data-ttu-id="f0dc6-224">Program Windows PowerShell ISE 2.0 nie rozpoznaje te przełączniki wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-224">Windows PowerShell ISE 2.0 does not recognize these command-line switches.</span></span>

### <a name="new-editor-features"></a><span data-ttu-id="f0dc6-225">Nowe funkcje edytora</span><span class="sxs-lookup"><span data-stu-id="f0dc6-225">New editor features</span></span>
<span data-ttu-id="f0dc6-226">**Dodane w programie PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-226">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="f0dc6-227">Inne funkcje edycji programu Windows PowerShell ISE:</span><span class="sxs-lookup"><span data-stu-id="f0dc6-227">Other Windows PowerShell ISE editing features include:</span></span>

- <span data-ttu-id="f0dc6-228">**Kolorowanie składni XML**programu Windows PowerShell ISE teraz kolory składni XML w taki sam sposób jak kolory jego składnię Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-228">**XML syntax coloring**Windows PowerShell ISE now colors XML syntax in the same way as it colors Windows PowerShell syntax.</span></span>

- <span data-ttu-id="f0dc6-229">**Dopasowywanie nawiasu klamrowego** programu Windows PowerShell ISE zawiera nawias klamrowy dopasowywania i wyróżnianie i mogą być używane w następujący sposób: (na przykład za pomocą **przejdź do dopasowania** polecenia lub **Ctrl +]** lokalizuje zamykający nawias klamrowy, jeśli masz nawiasu otwierającego zaznaczona).</span><span class="sxs-lookup"><span data-stu-id="f0dc6-229">**Brace matching** Windows PowerShell ISE includes brace matching and highlighting, and can be used in the following ways: (for example, using the **Go to Match** command or **Ctrl + ]** locates the closing brace, if you have an opening brace selected).</span></span>

- <span data-ttu-id="f0dc6-230">**Wyświetlanie konspektu** okienko skryptu obsługuje tworzenie konspektu, co pozwala zwijanie lub rozwijanie fragmentów kodu, klikając przycisk plus lub minus zaloguje się na lewym marginesie.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-230">**Outline view** The Script Pane supports outlining, which allows collapsing or expanding sections of code by clicking plus or minus signs in the left margin.</span></span> <span data-ttu-id="f0dc6-231">Można użyć nawiasów klamrowych lub **#region** i **#endregion** znaczniki, aby oznaczyć początek lub koniec zwijanej sekcji.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-231">You can use braces or the **#region** and **#endregion** tags to mark the beginning or end of a collapsible section.</span></span> <span data-ttu-id="f0dc6-232">Aby rozwinąć lub zwinąć wszystkich regionów, naciśnij klawisz **Ctrl + M**.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-232">To expand or collapse all regions, press **Ctrl + M**.</span></span>

- <span data-ttu-id="f0dc6-233">**Przeciągnij i upuść edycji tekstu**programu Windows PowerShell ISE teraz obsługuje przeciągania i upuszczania, edycję tekstu.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-233">**Drag and drop text editing**Windows PowerShell ISE now supports drag and drop text editing.</span></span> <span data-ttu-id="f0dc6-234">Można wybrać bloku tekstu i przeciągnij go do innej lokalizacji w edytorze lub konsoli przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-234">You can select any block of text and drag that text to another location in the editor or the console to move the text.</span></span> <span data-ttu-id="f0dc6-235">Przytrzymując klawisz Ctrl podczas przeciągania zaznaczonego tekstu po zwolnieniu przycisku myszy tekst jest kopiowana do nowej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-235">If you hold down the Ctrl key while you drag the selected text, when you release the mouse button the text is copied to the new location.</span></span> <span data-ttu-id="f0dc6-236">W tej wersji programu Windows PowerShell ISE, jak również we wcześniejszej wersji programu Windows PowerShell ISE przeciągnij i upuść pliki na środowisku Windows PowerShell ISE, programu Windows PowerShell ISE otwartego pliku.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-236">In this version of Windows PowerShell ISE, as well as the previous version of Windows PowerShell ISE, when you drag and drop files onto Windows PowerShell ISE, Windows PowerShell ISE opens the file.</span></span>

- <span data-ttu-id="f0dc6-237">**Przeanalizować wyświetlania błędów** błędy analizy są oznaczone czerwoną podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-237">**Parse error display** Parse errors are indicated with red underlines.</span></span> <span data-ttu-id="f0dc6-238">Po umieszczeniu na wskazanych błąd, tekst etykietki narzędzia wyświetlany problem, który został znaleziony w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-238">When you hover over an indicated error, tooltip text displays the problem that was found in the code.</span></span>

- <span data-ttu-id="f0dc6-239">**Powiększenie** powiększenia konsoli "™ s zawartość można ustawić za pomocą suwaka powiększenia (w prawym dolnym rogu okna programu Windows PowerShell ISE) lub przez wprowadzenie polecenia **$psise.options.Zoom** w okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-239">**Zoom** The zoom percentage of the console'™s content can be set by using the zoom slider (in the lower right corner of Windows PowerShell ISE window), or by entering the command **$psise.options.Zoom** in the Console Pane.</span></span>

- <span data-ttu-id="f0dc6-240">**Sformatowanego tekstu kopiowania i wklejania** kopiowania do Schowka w środowisku Windows PowerShell ISE zachowuje czcionki, rozmiaru i informacji o kolorze oryginalnego zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-240">**Rich text copy and paste** Copying to the clipboard in Windows PowerShell ISE preserves the font, size, and color information of the original selection.</span></span>

- <span data-ttu-id="f0dc6-241">**Blokowanie wybór** można wybrać bloku tekstu przez trzymając wciśnięty klawisz ALT Zaznaczanie tekstu w okienku skryptów myszą lub naciśnięcie **Alt + Shift + Strzałka w**.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-241">**Block selection** You can select a block of text by holding down the ALT key while selecting text in the Script Pane with your mouse, or by pressing **Alt+Shift+Arrow**.</span></span>

<span data-ttu-id="f0dc6-242">**Jakie korzyści zapewnia ta zmiana?**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-242">**What value does this change add?**</span></span>

<span data-ttu-id="f0dc6-243">Dodatkowe funkcje edycji zapewnić spójność i wydajne środowisko edycji.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-243">The additional editing features provide a more consistent and powerful editing environment.</span></span>

<span data-ttu-id="f0dc6-244">**Co się zmieniło stanie?**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-244">**What works differently?**</span></span>

<span data-ttu-id="f0dc6-245">Te ulepszenia edycji nie jest obecny w programie Windows PowerShell ISE 2.0.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-245">These editing enhancements were not present in Windows PowerShell ISE 2.0.</span></span>

### <a name="new-help-viewer-window"></a><span data-ttu-id="f0dc6-246">Nowe okno podglądu pomocy</span><span class="sxs-lookup"><span data-stu-id="f0dc6-246">New Help viewer window</span></span>
<span data-ttu-id="f0dc6-247">**Dodane w programie PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-247">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="f0dc6-248">Jeśli naciśniesz **F1** gdy kursor jest w użyciu polecenia cmdlet lub mieć część polecenia cmdlet wyróżnione, nowy Podgląd pomocy otwiera Pomoc kontekstową o wyróżnione polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-248">If you press **F1** when your cursor is in a cmdlet, or you have part of a cmdlet highlighted, the new Help viewer opens context-sensitive Help about the highlighted cmdlet.</span></span> <span data-ttu-id="f0dc6-249">Aby wyświetlić Windows PowerShell o pomoc, wpisz **operatory** w okienku konsoli, a następnie naciśnij klawisz **F1**.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-249">To display Windows PowerShell About help, type  **operators** in the console pane, and then press **F1**.</span></span>

<span data-ttu-id="f0dc6-250">Przed użyciem tej funkcji, należy pobrać najnowszej wersji tematy Pomocy programu Windows PowerShell z witryny sieci Web firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-250">Before you use this feature, download the most current version of Windows PowerShell Help topics from the Microsoft website.</span></span> <span data-ttu-id="f0dc6-251">Pobieranie tematy pomocy najprostszą metodą jest uruchomienie **Update-Help** polecenia cmdlet w okienku konsoli w przypadku uruchamiania programu Windows PowerShell ISE jako administrator.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-251">The simplest method for downloading the Help topics is to run the **Update-Help** cmdlet in the Console Pane when running Windows PowerShell ISE as administrator.</span></span>

<span data-ttu-id="f0dc6-252">Gdzie można zmienić **F1** klucz wygląda, aby uzyskać pomoc.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-252">You can alter where the **F1** key looks for Help.</span></span> <span data-ttu-id="f0dc6-253">W **narzędzia**/**opcje** menu na **ustawienia ogólne** , w obszarze **inne ustawienia**, możesz zaznaczyć lub wyczyścić pole wyboru **Użyj lokalnej zawartości pomocy zamiast zawartości online**.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-253">In the **Tools**/**Options** menu, on the **General Settings** tab, under **Other Settings**, you can set or clear the checkbox **Use local help content instead of online content**.</span></span> <span data-ttu-id="f0dc6-254">Jeśli zaznaczone, klient wygląda w pobranej pomocy w folderze modułów pomocy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-254">If checked, then the client looks for the cmdlet Help in the downloaded Help found in the modules folder.</span></span>  <span data-ttu-id="f0dc6-255">Jeśli pole wyboru jest wyczyszczone, klient wyszukuje w bibliotece TechNet programu pomocy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-255">If the checkbox is cleared, then the client looks on the TechNet library for the cmdlet help.</span></span>

<span data-ttu-id="f0dc6-256">**Jakie korzyści zapewnia ta zmiana?**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-256">**What value does this change add?**</span></span>

<span data-ttu-id="f0dc6-257">Pomoc kontekstowa bez opuszczania z bieżącego polecenia cmdlet lub skryptu zapewnia bezproblemowe learning.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-257">Context-sensitive Help without leaving your current cmdlet or script provides a seamless learning experience.</span></span>

<span data-ttu-id="f0dc6-258">**Co się zmieniło stanie?**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-258">**What works differently?**</span></span>

<span data-ttu-id="f0dc6-259">Naciśnięcie klawisza F1 w poprzednich wersjach programu Windows PowerShell ISE otworzyć plik pomocy na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-259">Pressing F1 in previous versions of Windows PowerShell ISE opened the help file on the local computer.</span></span> <span data-ttu-id="f0dc6-260">W środowisku Windows PowerShell ISE 3.0 i nowszych zostanie otwarte okno zawiera pomoc dla polecenia cmdlet, które można wyszukiwać i można skonfigurować.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-260">In Windows PowerShell ISE 3.0 and later, a window opens that contains the help for the cmdlet that is searchable and configurable.</span></span> <span data-ttu-id="f0dc6-261">Tego środowiska Pomoc jest nowego w środowisku Windows PowerShell ISE 3.0 i aktualizowalnej pomocy są nowe w programie Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-261">This Help experience is new for Windows PowerShell ISE 3.0, and Updatable Help is new for Windows PowerShell 3.0.</span></span>

### <a name="show-command-cmdlet"></a><span data-ttu-id="f0dc6-262">Pokaż polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="f0dc6-262">Show-Command cmdlet</span></span>
<span data-ttu-id="f0dc6-263">**Dodane w programie PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-263">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="f0dc6-264">**Pokaż polecenie** polecenie cmdlet umożliwia utworzenie lub uruchom polecenie cmdlet lub funkcja wypełniając formie graficznej.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-264">The **Show-Command** cmdlet enables you to compose or run a cmdlet or function by filling in a graphical form.</span></span> <span data-ttu-id="f0dc6-265">Formularz umożliwia użytkownikom pracy przy użyciu programu Windows PowerShell w środowisku graficznym.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-265">The form lets users work with Windows PowerShell in a graphical environment.</span></span> <span data-ttu-id="f0dc6-266">**Pokaż polecenia** również umożliwia zaawansowane twórcom skryptów do utworzenia szybkiego GUI opartych na środowisku Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-266">**Show-Command** also enables advanced scripters to create a quick Windows PowerShell-based GUI.</span></span>

<span data-ttu-id="f0dc6-267">**Jakie korzyści zapewnia ta zmiana?**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-267">**What value does this change add?**</span></span>

<span data-ttu-id="f0dc6-268">Za pomocą **Pokaż polecenia** w skryptach środowiska Windows PowerShell, można udostępnić użytkownikom środowisko graficzne, z którym są znane.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-268">By using **Show-Command** in your Windows PowerShell scripts, you can provide your users with the graphical environment with which they are familiar.</span></span> <span data-ttu-id="f0dc6-269">**Pokaż polecenia** może również ułatwić użytkownikom wprowadzające informacje programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-269">**Show-Command** can also help introductory users learn Windows PowerShell.</span></span>

<span data-ttu-id="f0dc6-270">**Co się zmieniło stanie?**</span><span class="sxs-lookup"><span data-stu-id="f0dc6-270">**What works differently?**</span></span>

<span data-ttu-id="f0dc6-271">Pokaż polecenia jest nowy Windows PowerShell ISE 3.0.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-271">Show-Command is new Windows PowerShell ISE 3.0.</span></span>

## <a name="see-also"></a><span data-ttu-id="f0dc6-272">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f0dc6-272">See also</span></span>
<span data-ttu-id="f0dc6-273">Aby uzyskać więcej informacji o korzystaniu z programu Windows PowerShell ISE w programie Windows PowerShell zobacz następujące łącza.</span><span class="sxs-lookup"><span data-stu-id="f0dc6-273">For more information about using Windows PowerShell ISE in Windows PowerShell, see the following links.</span></span>

- [<span data-ttu-id="f0dc6-274">Eksploracja Windows PowerShell zintegrowane środowisko obsługi skryptów</span><span class="sxs-lookup"><span data-stu-id="f0dc6-274">Exploring the Windows PowerShell Integrated Scripting Environment</span></span>](../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
- [<span data-ttu-id="f0dc6-275">ISE w witrynie TechNet Wiki</span><span class="sxs-lookup"><span data-stu-id="f0dc6-275">ISE on the TechNet Wiki</span></span>](http://social.technet.microsoft.com/wiki/search/searchresults.aspx?q=ISE)
- [<span data-ttu-id="f0dc6-276">Centrum skryptów</span><span class="sxs-lookup"><span data-stu-id="f0dc6-276">Script Center</span></span>](http://technet.microsoft.com/scriptcenter/default)

