---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Jakie s Nowość w programie PowerShell 50 środowiska ISE
ms.assetid: 38648d47-7c27-4b37-a40e-ad29948519c2
ms.openlocfilehash: f05e3f3f95c8ceec6e843b8a1c79e6f092e1b87b
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320588"
---
# <a name="what39s-new-in-the-windows-powershell-ise"></a><span data-ttu-id="f996a-103">Co&#39;s Nowość w środowisku Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="f996a-103">What&#39;s New in the Windows PowerShell ISE</span></span>
<span data-ttu-id="f996a-104">W tym temacie opisano nowe i zaktualizowane funkcje, które zostały wprowadzone w wersjach programu Windows PowerShell zintegrowane Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="f996a-104">This topic explains the new and updated features that have been introduced in versions of Windows PowerShell  Integrated Scripting Environment (ISE).</span></span>

## <a name="feature-description"></a><span data-ttu-id="f996a-105">Opis funkcji</span><span class="sxs-lookup"><span data-stu-id="f996a-105">Feature description</span></span>
<span data-ttu-id="f996a-106">W środowisku Windows PowerShell ISE jest aplikacją hosta, która pozwala na zapis, uruchamianie i testowanie skryptów i modułów w środowisku graficznym i intuicyjne.</span><span class="sxs-lookup"><span data-stu-id="f996a-106">The Windows PowerShell ISE is a host application that enables you to write, run, and test scripts and modules in a graphical and intuitive environment.</span></span> <span data-ttu-id="f996a-107">Najważniejsze funkcje, takie jak kolorowanie składni karcie zakończenia, debugowania visual, zgodności Unicode i Pomoc kontekstowa zapewniają bogate środowisko obsługi skryptów.</span><span class="sxs-lookup"><span data-stu-id="f996a-107">Key features such as syntax-coloring, tab completion, visual debugging, Unicode compliance, and context-sensitive Help provide a rich scripting experience.</span></span>

<span data-ttu-id="f996a-108">Omówienie programu Windows PowerShell ISE, zobacz [Przegląd Windows PowerShell zintegrowane Scripting środowisko](https://technet.microsoft.com/library/3c1892c2-bf84-4cb6-af26-1f453be9e671).</span><span class="sxs-lookup"><span data-stu-id="f996a-108">For an overview of Windows PowerShell ISE, see [Windows PowerShell Integrated Scripting Environment overview](https://technet.microsoft.com/library/3c1892c2-bf84-4cb6-af26-1f453be9e671).</span></span>

## <a name="new-and-changed-functionality-in-windows-powershell-ise"></a><span data-ttu-id="f996a-109">Nowe i zmienione funkcje w środowisku Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="f996a-109">New and changed functionality in Windows PowerShell ISE</span></span>
<span data-ttu-id="f996a-110">W poniższej tabeli wymieniono nowe i zmienione funkcje w tej wersji programu Windows PowerShell ISE w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f996a-110">The following table lists the new and changed features for this release of Windows PowerShell ISE in Windows PowerShell.</span></span>

|<span data-ttu-id="f996a-111">Funkcja</span><span class="sxs-lookup"><span data-stu-id="f996a-111">Feature/functionality</span></span>|<span data-ttu-id="f996a-112">Windows PowerShell ISE 4.0</span><span class="sxs-lookup"><span data-stu-id="f996a-112">Windows PowerShell ISE 4.0</span></span>|<span data-ttu-id="f996a-113">Windows PowerShell ISE 3.0</span><span class="sxs-lookup"><span data-stu-id="f996a-113">Windows PowerShell ISE 3.0</span></span>|<span data-ttu-id="f996a-114">Windows PowerShell ISE 2.0</span><span class="sxs-lookup"><span data-stu-id="f996a-114">Windows PowerShell ISE 2.0</span></span>|
|--------------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
|<span data-ttu-id="f996a-115">**[IntelliSense](#intellisense)**</span><span class="sxs-lookup"><span data-stu-id="f996a-115">**[IntelliSense](#intellisense)**</span></span>|<span data-ttu-id="f996a-116">X</span><span class="sxs-lookup"><span data-stu-id="f996a-116">X</span></span>|<span data-ttu-id="f996a-117">X</span><span class="sxs-lookup"><span data-stu-id="f996a-117">X</span></span>||
|<span data-ttu-id="f996a-118">**[Fragmenty kodu](#snippets)**</span><span class="sxs-lookup"><span data-stu-id="f996a-118">**[Snippets](#snippets)**</span></span>|<span data-ttu-id="f996a-119">X</span><span class="sxs-lookup"><span data-stu-id="f996a-119">X</span></span>|<span data-ttu-id="f996a-120">X</span><span class="sxs-lookup"><span data-stu-id="f996a-120">X</span></span>||
|<span data-ttu-id="f996a-121">**[Dodatkowe narzędzia](#add-on-tools)**</span><span class="sxs-lookup"><span data-stu-id="f996a-121">**[Add-on Tools](#add-on-tools)**</span></span>|<span data-ttu-id="f996a-122">X</span><span class="sxs-lookup"><span data-stu-id="f996a-122">X</span></span>|<span data-ttu-id="f996a-123">X</span><span class="sxs-lookup"><span data-stu-id="f996a-123">X</span></span>||
|<span data-ttu-id="f996a-124">**[Menedżera ponownego uruchamiania i automatycznego zapisywania](#restart-manager-and-auto-save)**</span><span class="sxs-lookup"><span data-stu-id="f996a-124">**[Restart Manager and Auto-save](#restart-manager-and-auto-save)**</span></span>|<span data-ttu-id="f996a-125">X</span><span class="sxs-lookup"><span data-stu-id="f996a-125">X</span></span>|<span data-ttu-id="f996a-126">X</span><span class="sxs-lookup"><span data-stu-id="f996a-126">X</span></span>||
|<span data-ttu-id="f996a-127">**[Listy ostatnio używanych](#most-recently-used-list)**</span><span class="sxs-lookup"><span data-stu-id="f996a-127">**[Most-recently used list](#most-recently-used-list)**</span></span>|<span data-ttu-id="f996a-128">X</span><span class="sxs-lookup"><span data-stu-id="f996a-128">X</span></span>|<span data-ttu-id="f996a-129">X</span><span class="sxs-lookup"><span data-stu-id="f996a-129">X</span></span>||
|<span data-ttu-id="f996a-130">**[W okienku konsoli](#console-pane)**</span><span class="sxs-lookup"><span data-stu-id="f996a-130">**[Console Pane](#console-pane)**</span></span>|<span data-ttu-id="f996a-131">X</span><span class="sxs-lookup"><span data-stu-id="f996a-131">X</span></span>|<span data-ttu-id="f996a-132">X</span><span class="sxs-lookup"><span data-stu-id="f996a-132">X</span></span>||
|<span data-ttu-id="f996a-133">**[Przełączniki wiersza polecenia](#command-line-switches)**</span><span class="sxs-lookup"><span data-stu-id="f996a-133">**[Command-line switches](#command-line-switches)**</span></span>|<span data-ttu-id="f996a-134">X</span><span class="sxs-lookup"><span data-stu-id="f996a-134">X</span></span>|<span data-ttu-id="f996a-135">X</span><span class="sxs-lookup"><span data-stu-id="f996a-135">X</span></span>||
|<span data-ttu-id="f996a-136">**[Nowe funkcje edytora](#new-editor-features)**</span><span class="sxs-lookup"><span data-stu-id="f996a-136">**[New editor features](#new-editor-features)**</span></span>|<span data-ttu-id="f996a-137">X</span><span class="sxs-lookup"><span data-stu-id="f996a-137">X</span></span>|<span data-ttu-id="f996a-138">X</span><span class="sxs-lookup"><span data-stu-id="f996a-138">X</span></span>||
|<span data-ttu-id="f996a-139">**[Nowe okno podglądu pomocy](#new-help-viewer-window)**</span><span class="sxs-lookup"><span data-stu-id="f996a-139">**[New Help viewer window](#new-help-viewer-window)**</span></span>|<span data-ttu-id="f996a-140">X</span><span class="sxs-lookup"><span data-stu-id="f996a-140">X</span></span>|<span data-ttu-id="f996a-141">X</span><span class="sxs-lookup"><span data-stu-id="f996a-141">X</span></span>||
|<span data-ttu-id="f996a-142">**[Pokaż polecenia cmdlet](#show-command-cmdlet)**</span><span class="sxs-lookup"><span data-stu-id="f996a-142">**[Show-Command cmdlet](#show-command-cmdlet)**</span></span>|<span data-ttu-id="f996a-143">X</span><span class="sxs-lookup"><span data-stu-id="f996a-143">X</span></span>|<span data-ttu-id="f996a-144">X</span><span class="sxs-lookup"><span data-stu-id="f996a-144">X</span></span>||

### <a name="intellisense"></a><span data-ttu-id="f996a-145">Funkcja IntelliSense</span><span class="sxs-lookup"><span data-stu-id="f996a-145">IntelliSense</span></span>
<span data-ttu-id="f996a-146">**Dodane w środowisku ISE 3.0**</span><span class="sxs-lookup"><span data-stu-id="f996a-146">**Added in ISE 3.0**</span></span>

<span data-ttu-id="f996a-147">Funkcja IntelliSense jest to funkcja automatycznego uzupełniania, pomoc, która jest częścią środowiska Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f996a-147">IntelliSense is an automatic-completion assistance feature that is part of Windows PowerShell ISE.</span></span> <span data-ttu-id="f996a-148">Funkcja IntelliSense wyświetla aktywne menu potencjalnie zgodnych poleceń cmdlet, parametry, wartości parametrów, pliki lub foldery, podczas wpisywania.</span><span class="sxs-lookup"><span data-stu-id="f996a-148">IntelliSense displays clickable menus of potentially matching cmdlets, parameters, parameter values, files, or folders as you type.</span></span>

<span data-ttu-id="f996a-149">**Jakie korzyści zapewnia ta zmiana?**</span><span class="sxs-lookup"><span data-stu-id="f996a-149">**What value does this change add?**</span></span>

<span data-ttu-id="f996a-150">Dzięki dodaniu funkcji IntelliSense łatwiej jest odnajdywanie poleceń cmdlet i składnię, gdy używasz programu Windows PowerShell ISE do tworzenia skryptów.</span><span class="sxs-lookup"><span data-stu-id="f996a-150">With the addition of IntelliSense, it is easier to discover cmdlets and syntax when you use Windows PowerShell ISE to create scripts.</span></span> <span data-ttu-id="f996a-151">Aby dowiedzieć się więcej środowiska Windows PowerShell, gdy tworzysz nowe skrypty umożliwia także środowiska Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f996a-151">You can also use Windows PowerShell ISE to learn Windows PowerShell while you create new scripts.</span></span>

<span data-ttu-id="f996a-152">**Co się zmieniło stanie?**</span><span class="sxs-lookup"><span data-stu-id="f996a-152">**What works differently?**</span></span>

<span data-ttu-id="f996a-153">Po wpisaniu polecenia cmdlet programu Windows PowerShell ISE 3.0 lub nowszego, wyświetla przewijany i Zwiększyliśmy menu, co pozwala przeglądać i wybrać odpowiednie polecenia.</span><span class="sxs-lookup"><span data-stu-id="f996a-153">When you type cmdlets in the Windows PowerShell ISE 3.0 or later, a scrollable and clickable menu displays, allowing you to browse and select the appropriate commands.</span></span>

### <a name="snippets"></a><span data-ttu-id="f996a-154">Fragmenty kodu</span><span class="sxs-lookup"><span data-stu-id="f996a-154">Snippets</span></span>
<span data-ttu-id="f996a-155">**Dodane w środowisku ISE 3.0**</span><span class="sxs-lookup"><span data-stu-id="f996a-155">**Added in ISE 3.0**</span></span>

<span data-ttu-id="f996a-156">*Fragmenty kodu* krótki sekcje kodu programu Windows PowerShell, który można wstawić do skryptów tworzenia w środowisku Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f996a-156">*Snippets* are short sections of Windows PowerShell code that you can insert into the scripts you create in Windows PowerShell ISE.</span></span> <span data-ttu-id="f996a-157">Windows PowerShell ISE jest dostarczany z domyślny zestaw fragmentów.</span><span class="sxs-lookup"><span data-stu-id="f996a-157">Windows PowerShell ISE comes with a default set of snippets.</span></span> <span data-ttu-id="f996a-158">Fragmenty kodu można dodać za pomocą **nowy fragment** polecenia cmdlet podczas pracy w środowisku Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f996a-158">You can add snippets by using the **New-Snippet** cmdlet while working in Windows PowerShell ISE.</span></span>

<span data-ttu-id="f996a-159">**Jakie korzyści zapewnia ta zmiana?**</span><span class="sxs-lookup"><span data-stu-id="f996a-159">**What value does this change add?**</span></span>

<span data-ttu-id="f996a-160">Za pomocą fragmentów kodu, możesz szybko tworzyć i tworzenia skryptów w celu zautomatyzowania środowiska.</span><span class="sxs-lookup"><span data-stu-id="f996a-160">By using snippets, you can quickly assemble and create scripts to automate your environment.</span></span>

<span data-ttu-id="f996a-161">**Co się zmieniło stanie?**</span><span class="sxs-lookup"><span data-stu-id="f996a-161">**What works differently?**</span></span>

<span data-ttu-id="f996a-162">Do na używanie fragmentów kodu w programie Windows PowerShell 3.0 lub nowszej, **Edytuj** menu, kliknij przycisk **Start fragmenty**, lub naciśnij **Ctrl-J**.</span><span class="sxs-lookup"><span data-stu-id="f996a-162">To use snippets in Windows PowerShell 3.0 or later, on the **Edit** menu, click **Start Snippets**, or press **Ctrl-J**.</span></span>

### <a name="add-on-tools"></a><span data-ttu-id="f996a-163">Dodatkowe narzędzia</span><span class="sxs-lookup"><span data-stu-id="f996a-163">Add-on tools</span></span>
<span data-ttu-id="f996a-164">**Dodane w programie PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="f996a-164">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="f996a-165">Windows PowerShell ISE obsługuje teraz dodatku Narzędzia, które są kontrolek Windows Presentation Foundation (WPF), które są dodawane przy użyciu modelu obiektu.</span><span class="sxs-lookup"><span data-stu-id="f996a-165">Windows PowerShell ISE now supports add-on tools, which are Windows Presentation Foundation (WPF) controls that are added by using the object model.</span></span> <span data-ttu-id="f996a-166">Dodatkowe narzędzia może być wyświetlany jako poziomy lub pionowy okienko w konsoli.</span><span class="sxs-lookup"><span data-stu-id="f996a-166">Add-on tools can be displayed as a vertical or horizontal pane in the console.</span></span> <span data-ttu-id="f996a-167">Wiele narzędzia dodatków w okienku są wyświetlane jako kontrolka z kartami.</span><span class="sxs-lookup"><span data-stu-id="f996a-167">Multiple add-on tools in a pane are displayed as a tabbed control.</span></span> <span data-ttu-id="f996a-168">Można również dodać lub usunąć dodatkowe narzędzia, które są produkowane przez firmy inne niż Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f996a-168">You can also add or remove add-on tools that are produced by non-Microsoft parties.</span></span> <span data-ttu-id="f996a-169">Aby uzyskać więcej informacji o sposobie importowania lub usuń dodatkowe narzędzia, zobacz [operacji programu Windows PowerShell ISE](https://technet.microsoft.com/library/cc732148.aspx).</span><span class="sxs-lookup"><span data-stu-id="f996a-169">For more information about how to import or remove add-on tools, see [Windows PowerShell ISE Operations](https://technet.microsoft.com/library/cc732148.aspx).</span></span>

<span data-ttu-id="f996a-170">**Jakie korzyści zapewnia ta zmiana?**</span><span class="sxs-lookup"><span data-stu-id="f996a-170">**What value does this change add?**</span></span>

<span data-ttu-id="f996a-171">Dodatki umożliwiają rozszerzanie i dostosowywanie środowiska Windows PowerShell ISE z narzędziami, które mogą poprawić środowisko obsługi skryptów lub dodać funkcje do programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f996a-171">Add-ons allow you to extend and customize Windows PowerShell ISE with tools that can enhance your scripting experience or add functionality to Windows PowerShell ISE.</span></span>

<span data-ttu-id="f996a-172">**Co się zmieniło stanie?**</span><span class="sxs-lookup"><span data-stu-id="f996a-172">**What works differently?**</span></span>

<span data-ttu-id="f996a-173">Dołączono do programu Windows PowerShell ISE 3.0 ani nowszych **polecenia** dodatku.</span><span class="sxs-lookup"><span data-stu-id="f996a-173">Windows PowerShell ISE 3.0 and later come with the **Commands** add-on.</span></span> <span data-ttu-id="f996a-174">**Polecenia** dodatku pozwala na przeglądanie poleceń cmdlet i dostęp do uzyskania pomocy dotyczącej poleceń cmdlet side-by-side przy użyciu **skryptu** i **konsoli** okienka.</span><span class="sxs-lookup"><span data-stu-id="f996a-174">The **Commands** add-on allows you to browse cmdlets, and access help about the cmdlets side-by-side with the **Script** and **Console** Panes.</span></span>

<span data-ttu-id="f996a-175">Dodatkowe dodatki można znaleźć przy użyciu **Open dodatku Narzędzia witryny sieci Web** polecenie **dodatki** menu.</span><span class="sxs-lookup"><span data-stu-id="f996a-175">Additional add-ons can be found by using the **Open Add-on Tools Website** command on the **Add-ons** menu.</span></span>

### <a name="restart-manager-and-auto-save"></a><span data-ttu-id="f996a-176">Ponownie uruchom Menedżera i automatycznego zapisywania</span><span class="sxs-lookup"><span data-stu-id="f996a-176">Restart manager and auto-save</span></span>
<span data-ttu-id="f996a-177">**Dodane w programie PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="f996a-177">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="f996a-178">Windows PowerShell ISE teraz automatycznie zapisuje Otwórz skrypty co dwie minuty w innej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="f996a-178">Windows PowerShell ISE now automatically saves your open scripts every two minutes, in a separate location.</span></span>  <span data-ttu-id="f996a-179">Czy program Windows PowerShell ISE przestaje działać, jeśli system operacyjny zostanie ponownie uruchomiony, po ponownym uruchomieniu programu Windows PowerShell ISE, odzyskuje skrypty, które były Otwórz ostatniej sesji, nawet jeśli skrypty nie zostały zapisane.</span><span class="sxs-lookup"><span data-stu-id="f996a-179">If Windows PowerShell ISE stops working, or if the operating system is restarted, after Windows PowerShell ISE restarts, it recovers scripts that were open in the last session, even if the scripts were not saved.</span></span>

<span data-ttu-id="f996a-180">Aby zmienić interwał zapisywanie automatycznego, uruchom następujące polecenie, w okienku konsoli: **$psise. Options.AutoSaveMinuteInterval**.</span><span class="sxs-lookup"><span data-stu-id="f996a-180">To change the automatic saving interval, run the following command in the Console pane: **$psise.Options.AutoSaveMinuteInterval**.</span></span>

<span data-ttu-id="f996a-181">**Jakie korzyści zapewnia ta zmiana?**</span><span class="sxs-lookup"><span data-stu-id="f996a-181">**What value does this change add?**</span></span>

<span data-ttu-id="f996a-182">Teraz możesz pracować w ramach programu Windows PowerShell ISE, wiedząc, Otwórz skrypty są automatycznie zapisywane w przypadku nieoczekiwanego ponownego uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="f996a-182">You can now work within Windows PowerShell ISE knowing that your open scripts are automatically saved in the event of an unexpected restart.</span></span>

<span data-ttu-id="f996a-183">**Co się zmieniło stanie?**</span><span class="sxs-lookup"><span data-stu-id="f996a-183">**What works differently?**</span></span>

<span data-ttu-id="f996a-184">Windows PowerShell ISE 2.0 nie są zapisywane skrypty automatycznie w przypadku ponownego uruchomienia komputera.</span><span class="sxs-lookup"><span data-stu-id="f996a-184">Windows PowerShell ISE 2.0 does not save the scripts automatically in the event of a restart.</span></span>

### <a name="most-recently-used-list"></a><span data-ttu-id="f996a-185">Listy ostatnio używanych</span><span class="sxs-lookup"><span data-stu-id="f996a-185">Most-recently used list</span></span>
<span data-ttu-id="f996a-186">**Dodane w programie PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="f996a-186">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="f996a-187">Windows PowerShell ISE ma teraz na liście ostatnio używanych plików.</span><span class="sxs-lookup"><span data-stu-id="f996a-187">Windows PowerShell ISE now has a most-recently used list for files.</span></span> <span data-ttu-id="f996a-188">Po otwarciu pliku w środowisku Windows PowerShell ISE, plik zostanie dodany do listy ostatnio używanych na **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="f996a-188">When you open a file in Windows PowerShell ISE, the file is added to the most-recently used list on the **File** menu.</span></span>

<span data-ttu-id="f996a-189">Aby zmienić domyślną liczbę plików na liście ostatnio używanych, uruchom następujące polecenie, w okienku konsoli: **$psise. Options.MruCount**.</span><span class="sxs-lookup"><span data-stu-id="f996a-189">To change the default number of files in the most-recently used list, run the following command in the Console Pane: **$psise.Options.MruCount**.</span></span>

<span data-ttu-id="f996a-190">**Jakie korzyści zapewnia ta zmiana?**</span><span class="sxs-lookup"><span data-stu-id="f996a-190">**What value does this change add?**</span></span>

<span data-ttu-id="f996a-191">Lista ostatnio używanych umożliwia teraz łatwo uzyskiwać dostęp do często używanych plików.</span><span class="sxs-lookup"><span data-stu-id="f996a-191">You can now use the most-recently used list to easily access your frequently-used files.</span></span>

<span data-ttu-id="f996a-192">**Co się zmieniło stanie?**</span><span class="sxs-lookup"><span data-stu-id="f996a-192">**What works differently?**</span></span>

<span data-ttu-id="f996a-193">Windows PowerShell ISE 2.0 nie ma listy ostatnio używanych.</span><span class="sxs-lookup"><span data-stu-id="f996a-193">Windows PowerShell ISE 2.0 does not have a most-recently used list.</span></span>

### <a name="console-pane"></a><span data-ttu-id="f996a-194">W okienku konsoli</span><span class="sxs-lookup"><span data-stu-id="f996a-194">Console Pane</span></span>
<span data-ttu-id="f996a-195">**Dodane w programie PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="f996a-195">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="f996a-196">Osobne polecenie i okienka danych wyjściowych, które były dostępne w pierwszej wersji programu Windows PowerShell ISE zostały połączone w jednym okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="f996a-196">The separate Command and Output Panes that were available in the first release of Windows PowerShell ISE have been combined into a single Console Pane.</span></span> <span data-ttu-id="f996a-197">W okienku konsoli jest podobny w funkcji i wygląd typowe konsoli środowiska Windows PowerShell, ale obejmuje następujące ulepszenia (większość są opisane w tym temacie).</span><span class="sxs-lookup"><span data-stu-id="f996a-197">The Console Pane is similar in function and appearance to a typical Windows PowerShell console, but it includes the following enhancements (most are described in this topic).</span></span>

- <span data-ttu-id="f996a-198">Kolorowanie składni dla tekstu wejściowego (nie tekst danych wyjściowych), w tym składni XML</span><span class="sxs-lookup"><span data-stu-id="f996a-198">Syntax coloring for input text (not output text), including XML syntax</span></span>

- <span data-ttu-id="f996a-199">Funkcja IntelliSense</span><span class="sxs-lookup"><span data-stu-id="f996a-199">IntelliSense</span></span>

- <span data-ttu-id="f996a-200">Parowanie nawiasów klamrowych</span><span class="sxs-lookup"><span data-stu-id="f996a-200">Brace matching</span></span>

- <span data-ttu-id="f996a-201">Wskazanie błędu</span><span class="sxs-lookup"><span data-stu-id="f996a-201">Error indication</span></span>

- <span data-ttu-id="f996a-202">Pełna obsługa formatu Unicode</span><span class="sxs-lookup"><span data-stu-id="f996a-202">Full Unicode support</span></span>

- <span data-ttu-id="f996a-203">**F1** pomocy kontekstowej</span><span class="sxs-lookup"><span data-stu-id="f996a-203">**F1** context-sensitive help</span></span>

- <span data-ttu-id="f996a-204">**CTRL + F1** kontekstową polecenia Show</span><span class="sxs-lookup"><span data-stu-id="f996a-204">**Ctrl+F1** context-sensitive Show-Command</span></span>

- <span data-ttu-id="f996a-205">Skryptów złożonych i pomoc techniczna od prawej do lewej</span><span class="sxs-lookup"><span data-stu-id="f996a-205">Complex script and right-to-left support</span></span>

- <span data-ttu-id="f996a-206">Obsługa czcionek</span><span class="sxs-lookup"><span data-stu-id="f996a-206">Font support</span></span>

- <span data-ttu-id="f996a-207">Powiększenie</span><span class="sxs-lookup"><span data-stu-id="f996a-207">Zoom</span></span>

- <span data-ttu-id="f996a-208">Wybierz wiersz i zaznaczania bloku</span><span class="sxs-lookup"><span data-stu-id="f996a-208">Line-select and block-select modes</span></span>

- <span data-ttu-id="f996a-209">Zachowywanie wpisaną zawartość w wierszu polecenia, po naciśnięciu klawisza **się** strzałkę, aby wyświetlić historię w konsoli programu</span><span class="sxs-lookup"><span data-stu-id="f996a-209">Preservation of typed content at the command line when you press the **Up** arrow to view history in the console</span></span>

<span data-ttu-id="f996a-210">**Jakie korzyści zapewnia ta zmiana?**</span><span class="sxs-lookup"><span data-stu-id="f996a-210">**What value does this change add?**</span></span>

<span data-ttu-id="f996a-211">Dodanie tych zmian w okienku konsoli udostępnia środowisko obsługi skryptów bardziej spójny z interfejsem konsoli.</span><span class="sxs-lookup"><span data-stu-id="f996a-211">The addition of these Console Pane changes provides a scripting experience that is more consistent with the console interface.</span></span>

<span data-ttu-id="f996a-212">**Co się zmieniło stanie?**</span><span class="sxs-lookup"><span data-stu-id="f996a-212">**What works differently?**</span></span>

<span data-ttu-id="f996a-213">Windows PowerShell ISE 2.0 zawiera osobne polecenie i okienka danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="f996a-213">Windows PowerShell ISE 2.0 has separate Command and Output Panes.</span></span>

### <a name="command-line-switches"></a><span data-ttu-id="f996a-214">Przełączniki wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="f996a-214">Command-line switches</span></span>
<span data-ttu-id="f996a-215">**Dodane w programie PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="f996a-215">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="f996a-216">Jeśli program Windows PowerShell ISE można uruchomić z wiersza polecenia (przez wpisanie **powershell_ise.exe**), można dodać następujących nowych przełączników wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="f996a-216">If you start Windows PowerShell ISE from the command line (by typing **powershell_ise.exe**), you can add the following new command-line switches.</span></span>

- <span data-ttu-id="f996a-217">*-NoProfile*: uruchamia Windows PowerShell ISE bez uruchamiania **$profile**</span><span class="sxs-lookup"><span data-stu-id="f996a-217">*-NoProfile*: Starts Windows PowerShell ISE without running **$profile**</span></span>

- <span data-ttu-id="f996a-218">*-Help*: Wyświetla okno pomocy</span><span class="sxs-lookup"><span data-stu-id="f996a-218">*-Help*: Displays a Help window</span></span>

- <span data-ttu-id="f996a-219">*-mta*: uruchamia Windows PowerShell ISE w trybie apartamentu wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="f996a-219">*-mta*: Starts Windows PowerShell ISE in multithreaded apartment mode.</span></span> <span data-ttu-id="f996a-220">Domyślny tryb działania w środowisku Windows PowerShell ISE jest w trybie jednowątkowego apartamentu lub *- sta*.</span><span class="sxs-lookup"><span data-stu-id="f996a-220">The default operation mode for Windows PowerShell ISE is single-threaded apartment mode, or *-sta*.</span></span>

<span data-ttu-id="f996a-221">**Jakie korzyści zapewnia ta zmiana?**</span><span class="sxs-lookup"><span data-stu-id="f996a-221">**What value does this change add?**</span></span>

<span data-ttu-id="f996a-222">Dodanie tych przełączników wiersza polecenia umożliwia kontrolowanie środowiska, w którym działa program Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f996a-222">The addition of these command-line switches allows you to control the environment in which the Windows PowerShell ISE runs.</span></span>

<span data-ttu-id="f996a-223">**Co się zmieniło stanie?**</span><span class="sxs-lookup"><span data-stu-id="f996a-223">**What works differently?**</span></span>

<span data-ttu-id="f996a-224">Windows PowerShell ISE 2.0 nie rozpoznaje te przełączniki wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="f996a-224">Windows PowerShell ISE 2.0 does not recognize these command-line switches.</span></span>

### <a name="new-editor-features"></a><span data-ttu-id="f996a-225">Nowe funkcje edytora</span><span class="sxs-lookup"><span data-stu-id="f996a-225">New editor features</span></span>
<span data-ttu-id="f996a-226">**Dodane w programie PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="f996a-226">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="f996a-227">Inne funkcje edycji programu Windows PowerShell ISE:</span><span class="sxs-lookup"><span data-stu-id="f996a-227">Other Windows PowerShell ISE editing features include:</span></span>

- <span data-ttu-id="f996a-228">**Kolorowanie składni XML**środowiska Windows PowerShell ISE teraz kolorów składni XML w taki sam sposób, zgodnie z jego kolory składni programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f996a-228">**XML syntax coloring**Windows PowerShell ISE now colors XML syntax in the same way as it colors Windows PowerShell syntax.</span></span>

- <span data-ttu-id="f996a-229">**Parowanie nawiasów klamrowych** środowiska Windows PowerShell ISE obejmuje parowanie nawiasów klamrowych i wyróżnianie i mogą być używane w następujący sposób: (na przykład za pomocą **przejdź do dopasowania** polecenia lub **Ctrl +]** lokalizuje zamykający nawias klamrowy, jeśli masz wybrane nawiasu otwierającego).</span><span class="sxs-lookup"><span data-stu-id="f996a-229">**Brace matching** Windows PowerShell ISE includes brace matching and highlighting, and can be used in the following ways: (for example, using the **Go to Match** command or **Ctrl + ]** locates the closing brace, if you have an opening brace selected).</span></span>

- <span data-ttu-id="f996a-230">**Wyświetlanie konspektu** okienko skryptu obsługuje tworzenie konspektu, co umożliwia zwijanie i rozwijanie fragmentów kodu, klikając przycisk plus lub minus loguje się na lewym marginesie.</span><span class="sxs-lookup"><span data-stu-id="f996a-230">**Outline view** The Script Pane supports outlining, which allows collapsing or expanding sections of code by clicking plus or minus signs in the left margin.</span></span> <span data-ttu-id="f996a-231">Możesz użyć nawiasów klamrowych lub **#region** i **#endregion** tagów do oznaczania początku lub końcu zwijanej sekcji.</span><span class="sxs-lookup"><span data-stu-id="f996a-231">You can use braces or the **#region** and **#endregion** tags to mark the beginning or end of a collapsible section.</span></span> <span data-ttu-id="f996a-232">Aby rozwinąć lub zwinąć we wszystkich regionach, naciśnij klawisz **Ctrl + M**.</span><span class="sxs-lookup"><span data-stu-id="f996a-232">To expand or collapse all regions, press **Ctrl + M**.</span></span>

- <span data-ttu-id="f996a-233">**Przeciąganie i upuszczanie edycji tekstu**programu Windows PowerShell ISE teraz obsługuje przeciągnij i upuść edycji tekstu.</span><span class="sxs-lookup"><span data-stu-id="f996a-233">**Drag and drop text editing**Windows PowerShell ISE now supports drag and drop text editing.</span></span> <span data-ttu-id="f996a-234">Można wybrać żadnych blok tekstu i przeciągnij go do innej lokalizacji w edytorze lub konsoli, aby przenieść tekstu.</span><span class="sxs-lookup"><span data-stu-id="f996a-234">You can select any block of text and drag that text to another location in the editor or the console to move the text.</span></span> <span data-ttu-id="f996a-235">Po przytrzymaniu wciśniętego klawisza Ctrl podczas przeciągania zaznaczonego tekstu po zwolnieniu przycisku myszy tekst jest kopiowana do nowej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="f996a-235">If you hold down the Ctrl key while you drag the selected text, when you release the mouse button the text is copied to the new location.</span></span> <span data-ttu-id="f996a-236">W tej wersji programu Windows PowerShell ISE, a także poprzednią wersję programu Windows PowerShell ISE gdy przeciągnij i upuść pliki na środowisku Windows PowerShell ISE programu Windows PowerShell ISE otwiera plik.</span><span class="sxs-lookup"><span data-stu-id="f996a-236">In this version of Windows PowerShell ISE, as well as the previous version of Windows PowerShell ISE, when you drag and drop files onto Windows PowerShell ISE, Windows PowerShell ISE opens the file.</span></span>

- <span data-ttu-id="f996a-237">**Analizowanie błędów** błędy analizy są wskazane czerwonym podkreśleniem.</span><span class="sxs-lookup"><span data-stu-id="f996a-237">**Parse error display** Parse errors are indicated with red underlines.</span></span> <span data-ttu-id="f996a-238">Po umieszczeniu wskazany błąd tekst etykietki narzędzia wyświetla ten problem, który został znaleziony w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f996a-238">When you hover over an indicated error, tooltip text displays the problem that was found in the code.</span></span>

- <span data-ttu-id="f996a-239">**Powiększenie** powiększenia konsoli "™ s zawartość można ustawić za pomocą suwaka powiększenia (w prawym dolnym rogu okna środowiska Windows PowerShell ISE) lub przez wprowadzenie polecenia **$psise.options.Zoom** w okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="f996a-239">**Zoom** The zoom percentage of the console'™s content can be set by using the zoom slider (in the lower right corner of Windows PowerShell ISE window), or by entering the command **$psise.options.Zoom** in the Console Pane.</span></span>

- <span data-ttu-id="f996a-240">**Kopiuj tekst sformatowany i Wklej** kopiowania do Schowka w środowisku Windows PowerShell ISE zachowuje czcionkę, rozmiar i kolor informacji oryginalnego zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="f996a-240">**Rich text copy and paste** Copying to the clipboard in Windows PowerShell ISE preserves the font, size, and color information of the original selection.</span></span>

- <span data-ttu-id="f996a-241">**Zaznaczenie blokowe** blok tekstu można wybrać, przytrzymując naciśnięty klawisz ALT podczas zaznaczania tekstu w okienku skryptów przy użyciu myszy lub naciskając **Alt + Shift + Strzałka**.</span><span class="sxs-lookup"><span data-stu-id="f996a-241">**Block selection** You can select a block of text by holding down the ALT key while selecting text in the Script Pane with your mouse, or by pressing **Alt+Shift+Arrow**.</span></span>

<span data-ttu-id="f996a-242">**Jakie korzyści zapewnia ta zmiana?**</span><span class="sxs-lookup"><span data-stu-id="f996a-242">**What value does this change add?**</span></span>

<span data-ttu-id="f996a-243">Dodatkowe funkcje edycji zapewniają spójniejszą i bardziej zaawansowane środowisko edycji.</span><span class="sxs-lookup"><span data-stu-id="f996a-243">The additional editing features provide a more consistent and powerful editing environment.</span></span>

<span data-ttu-id="f996a-244">**Co się zmieniło stanie?**</span><span class="sxs-lookup"><span data-stu-id="f996a-244">**What works differently?**</span></span>

<span data-ttu-id="f996a-245">Te ulepszenia edycji nie był obecny w programie Windows PowerShell ISE 2.0.</span><span class="sxs-lookup"><span data-stu-id="f996a-245">These editing enhancements were not present in Windows PowerShell ISE 2.0.</span></span>

### <a name="new-help-viewer-window"></a><span data-ttu-id="f996a-246">Nowe okno podglądu pomocy</span><span class="sxs-lookup"><span data-stu-id="f996a-246">New Help viewer window</span></span>
<span data-ttu-id="f996a-247">**Dodane w programie PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="f996a-247">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="f996a-248">Jeśli użytkownik naciśnie klawisz **F1** gdy kursor jest w poleceniu cmdlet lub mieć część polecenia cmdlet wyróżniony, nowy Podgląd Pomocy otworzy kontekstowa pomoc na temat polecenia cmdlet wyróżnione.</span><span class="sxs-lookup"><span data-stu-id="f996a-248">If you press **F1** when your cursor is in a cmdlet, or you have part of a cmdlet highlighted, the new Help viewer opens context-sensitive Help about the highlighted cmdlet.</span></span> <span data-ttu-id="f996a-249">Aby wyświetlić Windows PowerShell o pomoc, wpisz **operatory** w okienku konsoli, a następnie naciśnij klawisz **F1**.</span><span class="sxs-lookup"><span data-stu-id="f996a-249">To display Windows PowerShell About help, type  **operators** in the console pane, and then press **F1**.</span></span>

<span data-ttu-id="f996a-250">Przed użyciem tej funkcji Pobierz najnowszą wersję tematy Pomocy programu Windows PowerShell z witryny sieci Web firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f996a-250">Before you use this feature, download the most current version of Windows PowerShell Help topics from the Microsoft website.</span></span> <span data-ttu-id="f996a-251">Najprostszą metodą pobierania tematy pomocy jest uruchomienie **Update-Help** polecenia cmdlet w okienku konsoli, podczas uruchamiania programu Windows PowerShell ISE jako administrator.</span><span class="sxs-lookup"><span data-stu-id="f996a-251">The simplest method for downloading the Help topics is to run the **Update-Help** cmdlet in the Console Pane when running Windows PowerShell ISE as administrator.</span></span>

<span data-ttu-id="f996a-252">Można zmienić miejsce **F1** klucz wygląda w celu uzyskania pomocy.</span><span class="sxs-lookup"><span data-stu-id="f996a-252">You can alter where the **F1** key looks for Help.</span></span> <span data-ttu-id="f996a-253">W **narzędzia**/**opcje** menu na **ustawienia ogólne** , w obszarze **inne ustawienia**, można ustawić lub wyczyścić Zaznacz pole wyboru **używać lokalnej zawartości pomocy zamiast zawartości online**.</span><span class="sxs-lookup"><span data-stu-id="f996a-253">In the **Tools**/**Options** menu, on the **General Settings** tab, under **Other Settings**, you can set or clear the checkbox **Use local help content instead of online content**.</span></span> <span data-ttu-id="f996a-254">Jeśli zaznaczone, klient wygląda w pobranej pomocy w folderze modułów pomocy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f996a-254">If checked, then the client looks for the cmdlet Help in the downloaded Help found in the modules folder.</span></span>  <span data-ttu-id="f996a-255">Jeśli pole wyboru jest wyczyszczone, klient sprawdza w bibliotece TechNet programu pomocy dotyczącej poleceń cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f996a-255">If the checkbox is cleared, then the client looks on the TechNet library for the cmdlet help.</span></span>

<span data-ttu-id="f996a-256">**Jakie korzyści zapewnia ta zmiana?**</span><span class="sxs-lookup"><span data-stu-id="f996a-256">**What value does this change add?**</span></span>

<span data-ttu-id="f996a-257">Pomoc kontekstowa bez wychodzenia z bieżącego polecenia cmdlet lub skryptu zapewnia bezproblemowe uczenia.</span><span class="sxs-lookup"><span data-stu-id="f996a-257">Context-sensitive Help without leaving your current cmdlet or script provides a seamless learning experience.</span></span>

<span data-ttu-id="f996a-258">**Co się zmieniło stanie?**</span><span class="sxs-lookup"><span data-stu-id="f996a-258">**What works differently?**</span></span>

<span data-ttu-id="f996a-259">Naciśnięcie klawisza F1 w poprzednich wersjach programu Windows PowerShell ISE otwarty plik pomocy na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="f996a-259">Pressing F1 in previous versions of Windows PowerShell ISE opened the help file on the local computer.</span></span> <span data-ttu-id="f996a-260">W środowisku Windows PowerShell ISE 3.0 i nowszych zostanie otwarte okno zawiera pomoc dotyczącą polecenia cmdlet, które można wyszukiwać i konfigurowalne.</span><span class="sxs-lookup"><span data-stu-id="f996a-260">In Windows PowerShell ISE 3.0 and later, a window opens that contains the help for the cmdlet that is searchable and configurable.</span></span> <span data-ttu-id="f996a-261">To środowisko pomocy jest nowego w programie Windows PowerShell ISE 3.0 i aktualizowalnej pomocy jest nowego w programie Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="f996a-261">This Help experience is new for Windows PowerShell ISE 3.0, and Updatable Help is new for Windows PowerShell 3.0.</span></span>

### <a name="show-command-cmdlet"></a><span data-ttu-id="f996a-262">Pokaż polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="f996a-262">Show-Command cmdlet</span></span>
<span data-ttu-id="f996a-263">**Dodane w programie PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="f996a-263">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="f996a-264">**Polecenie Pokaż** polecenie cmdlet umożliwia tworzą lub uruchom polecenie cmdlet lub funkcji, wypełniając w formie graficznej.</span><span class="sxs-lookup"><span data-stu-id="f996a-264">The **Show-Command** cmdlet enables you to compose or run a cmdlet or function by filling in a graphical form.</span></span> <span data-ttu-id="f996a-265">Formularz pozwala użytkownikom pracę przy użyciu programu Windows PowerShell w środowisku graficznym.</span><span class="sxs-lookup"><span data-stu-id="f996a-265">The form lets users work with Windows PowerShell in a graphical environment.</span></span> <span data-ttu-id="f996a-266">**Polecenie Pokaż** również włącza zaawansowanych twórcom skryptów do tworzenia szybkich GUI opartych na środowisku Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f996a-266">**Show-Command** also enables advanced scripters to create a quick Windows PowerShell-based GUI.</span></span>

<span data-ttu-id="f996a-267">**Jakie korzyści zapewnia ta zmiana?**</span><span class="sxs-lookup"><span data-stu-id="f996a-267">**What value does this change add?**</span></span>

<span data-ttu-id="f996a-268">Za pomocą **polecenie Pokaż** w skryptach programu Windows PowerShell można udostępnić użytkownikom pśrodowisku graficznym, z którym są one znane.</span><span class="sxs-lookup"><span data-stu-id="f996a-268">By using **Show-Command** in your Windows PowerShell scripts, you can provide your users with the graphical environment with which they are familiar.</span></span> <span data-ttu-id="f996a-269">**Polecenie Pokaż** może również ułatwić użytkownikom wprowadzające, dowiedzieć się więcej środowiska Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f996a-269">**Show-Command** can also help introductory users learn Windows PowerShell.</span></span>

<span data-ttu-id="f996a-270">**Co się zmieniło stanie?**</span><span class="sxs-lookup"><span data-stu-id="f996a-270">**What works differently?**</span></span>

<span data-ttu-id="f996a-271">Polecenie Pokaż jest nowy Windows PowerShell ISE 3.0.</span><span class="sxs-lookup"><span data-stu-id="f996a-271">Show-Command is new Windows PowerShell ISE 3.0.</span></span>

## <a name="see-also"></a><span data-ttu-id="f996a-272">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f996a-272">See also</span></span>
<span data-ttu-id="f996a-273">Aby uzyskać więcej informacji o używaniu programu Windows PowerShell ISE w programie Windows PowerShell zobacz poniższe linki.</span><span class="sxs-lookup"><span data-stu-id="f996a-273">For more information about using Windows PowerShell ISE in Windows PowerShell, see the following links.</span></span>

- [<span data-ttu-id="f996a-274">Eksplorowanie Windows PowerShell zintegrowane środowisko obsługi skryptów</span><span class="sxs-lookup"><span data-stu-id="f996a-274">Exploring the Windows PowerShell Integrated Scripting Environment</span></span>](../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
- [<span data-ttu-id="f996a-275">Środowiska ISE w witrynie TechNet Wiki</span><span class="sxs-lookup"><span data-stu-id="f996a-275">ISE on the TechNet Wiki</span></span>](https://social.technet.microsoft.com/wiki/search/searchresults.aspx?q=ISE)
- [<span data-ttu-id="f996a-276">Centrum skryptów</span><span class="sxs-lookup"><span data-stu-id="f996a-276">Script Center</span></span>](https://technet.microsoft.com/scriptcenter/default)