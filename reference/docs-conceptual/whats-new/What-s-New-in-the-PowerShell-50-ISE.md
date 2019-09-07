---
ms.date: 09/06/2019
keywords: PowerShell, polecenie cmdlet
title: Co nowego w programie PowerShell 5,0 ISE
ms.openlocfilehash: a719baef0da1600f0a5377e1b72c81b67e37eef2
ms.sourcegitcommit: a74ae7ed089301992fed201fbe55d827a622afa0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70746228"
---
# <a name="whats-new-in-the-windows-powershell-50-ise"></a><span data-ttu-id="2b4ad-103">Co nowego w programie Windows PowerShell 5,0 ISE</span><span class="sxs-lookup"><span data-stu-id="2b4ad-103">What's New in the Windows PowerShell 5.0 ISE</span></span>

<span data-ttu-id="2b4ad-104">W tym temacie objaśniono nowe i zaktualizowane funkcje, które zostały wprowadzone w wersjach środowiska Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="2b4ad-104">This topic explains the new and updated features that have been introduced in versions of Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="feature-description"></a><span data-ttu-id="2b4ad-105">Opis funkcji</span><span class="sxs-lookup"><span data-stu-id="2b4ad-105">Feature description</span></span>

<span data-ttu-id="2b4ad-106">Windows PowerShell ISE to aplikacja hosta, która umożliwia pisanie, uruchamianie i testowanie skryptów oraz modułów w graficznym i intuicyjnym środowisku.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-106">The Windows PowerShell ISE is a host application that enables you to write, run, and test scripts and modules in a graphical and intuitive environment.</span></span> <span data-ttu-id="2b4ad-107">Kluczowe funkcje, takie jak kodowanie, uzupełnianie kart, debugowanie wizualizacji, zgodność ze standardem Unicode i pomoc kontekstową, zapewniają bogate środowisko tworzenia skryptów.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-107">Key features such as syntax-coloring, tab completion, visual debugging, Unicode compliance, and context-sensitive Help provide a rich scripting experience.</span></span>

<span data-ttu-id="2b4ad-108">Aby uzyskać więcej informacji, zobacz [wprowadzenie Windows PowerShell ISE](../components/ise/Introducing-the-Windows-PowerShell-ISE.md).</span><span class="sxs-lookup"><span data-stu-id="2b4ad-108">For more information, see [Introducing the Windows PowerShell ISE](../components/ise/Introducing-the-Windows-PowerShell-ISE.md).</span></span>

<span data-ttu-id="2b4ad-109">W poniższej tabeli wymieniono nowe i zmienione funkcje tej wersji Windows PowerShell ISE w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-109">The following table lists the new and changed features for this release of Windows PowerShell ISE in Windows PowerShell.</span></span>

## <a name="intellisense"></a><span data-ttu-id="2b4ad-110">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="2b4ad-110">IntelliSense</span></span>

> <span data-ttu-id="2b4ad-111">Dodano w ISE 3,0</span><span class="sxs-lookup"><span data-stu-id="2b4ad-111">Added in ISE 3.0</span></span>

<span data-ttu-id="2b4ad-112">IntelliSense to funkcja automatycznego uzupełniania, która jest częścią Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-112">IntelliSense is an automatic-completion assistance feature that is part of Windows PowerShell ISE.</span></span>
<span data-ttu-id="2b4ad-113">Funkcja IntelliSense wyświetla menu możliwe do kliknięcia, które mogą być dopasowane do poleceń cmdlet, parametrów, wartości parametrów, plików lub folderów podczas wpisywania.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-113">IntelliSense displays clickable menus of potentially matching cmdlets, parameters, parameter values, files, or folders as you type.</span></span>

<span data-ttu-id="2b4ad-114">**Jaką wartość ma dodać ta zmiana?**</span><span class="sxs-lookup"><span data-stu-id="2b4ad-114">**What value does this change add?**</span></span>

<span data-ttu-id="2b4ad-115">Przy dodawaniu funkcji IntelliSense łatwiejsze jest odnajdywanie poleceń cmdlet i składni w przypadku używania Windows PowerShell ISE do tworzenia skryptów.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-115">With the addition of IntelliSense, it's easier to discover cmdlets and syntax when you use Windows PowerShell ISE to create scripts.</span></span> <span data-ttu-id="2b4ad-116">Możesz również użyć Windows PowerShell ISE, aby poznać środowisko Windows PowerShell podczas tworzenia nowych skryptów.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-116">You can also use Windows PowerShell ISE to learn Windows PowerShell while you create new scripts.</span></span>

<span data-ttu-id="2b4ad-117">**Co działa inaczej?**</span><span class="sxs-lookup"><span data-stu-id="2b4ad-117">**What works differently?**</span></span>

<span data-ttu-id="2b4ad-118">Po wpisaniu poleceń cmdlet w Windows PowerShell ISE wyświetlane jest menu przewijane i możliwe do kliknięcia, umożliwiające przeglądanie i wybieranie odpowiednich poleceń.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-118">When you type cmdlets in the Windows PowerShell ISE, a scrollable and clickable menu displays, allowing you to browse and select the appropriate commands.</span></span>

## <a name="snippets"></a><span data-ttu-id="2b4ad-119">Fragmenty kodu</span><span class="sxs-lookup"><span data-stu-id="2b4ad-119">Snippets</span></span>

> <span data-ttu-id="2b4ad-120">Dodano w ISE 3,0</span><span class="sxs-lookup"><span data-stu-id="2b4ad-120">Added in ISE 3.0</span></span>

<span data-ttu-id="2b4ad-121">*Fragmenty* kodu to krótkie sekcje programu Windows PowerShell Code, które można wstawić do skryptów tworzonych w Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-121">*Snippets* are short sections of Windows PowerShell code that you can insert into the scripts you create in Windows PowerShell ISE.</span></span> <span data-ttu-id="2b4ad-122">Windows PowerShell ISE zawiera domyślny zestaw fragmentów kodu.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-122">Windows PowerShell ISE comes with a default set of snippets.</span></span> <span data-ttu-id="2b4ad-123">Można dodać fragmenty kodu za pomocą `New-Snippet` polecenia cmdlet podczas pracy w Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-123">You can add snippets by using the `New-Snippet` cmdlet while working in Windows PowerShell ISE.</span></span>

<span data-ttu-id="2b4ad-124">**Jaką wartość ma dodać ta zmiana?**</span><span class="sxs-lookup"><span data-stu-id="2b4ad-124">**What value does this change add?**</span></span>

<span data-ttu-id="2b4ad-125">Za pomocą fragmentów kodu można szybko tworzyć i tworzyć skrypty do automatyzowania środowiska.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-125">By using snippets, you can quickly assemble and create scripts to automate your environment.</span></span>

<span data-ttu-id="2b4ad-126">**Co działa inaczej?**</span><span class="sxs-lookup"><span data-stu-id="2b4ad-126">**What works differently?**</span></span>

<span data-ttu-id="2b4ad-127">Aby użyć fragmentów kodu w programie Windows PowerShell 3,0 lub nowszym, w menu **Edycja** kliknij polecenie **Rozpocznij fragmenty kodu**lub naciśnij klawisz <kbd>Ctrl</kbd>+<kbd>J</kbd>.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-127">To use snippets in Windows PowerShell 3.0 or later, on the **Edit** menu, click **Start Snippets**, or press <kbd>Ctrl</kbd>+<kbd>J</kbd>.</span></span>

## <a name="add-on-tools"></a><span data-ttu-id="2b4ad-128">Narzędzia dodatków</span><span class="sxs-lookup"><span data-stu-id="2b4ad-128">Add-on tools</span></span>

> <span data-ttu-id="2b4ad-129">Dodano w programie PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="2b4ad-129">Added in PowerShell 3.0</span></span>

<span data-ttu-id="2b4ad-130">Windows PowerShell ISE teraz obsługuje narzędzia dodatków przy użyciu modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-130">Windows PowerShell ISE now supports add-on tools using the object model.</span></span> <span data-ttu-id="2b4ad-131">Te dodatki są kontrolkami Windows Presentation Foundation (WPF), które są wyświetlane jako okienko pionowe lub poziome w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-131">These add-ons are Windows Presentation Foundation (WPF) controls that are displayed as a vertical or horizontal pane in the console.</span></span> <span data-ttu-id="2b4ad-132">Wiele narzędzi dodatków w okienku jest wyświetlanych jako kontrolka z kartami.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-132">Multiple add-on tools in a pane are displayed as a tabbed control.</span></span> <span data-ttu-id="2b4ad-133">Możesz również dodawać lub usuwać narzędzia dodatków, które są tworzone przez strony inne niż firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-133">You can also add or remove add-on tools that are produced by non-Microsoft parties.</span></span> <span data-ttu-id="2b4ad-134">Aby uzyskać więcej informacji, zobacz [cel modelu obiektów skryptów Windows PowerShell ISE](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).</span><span class="sxs-lookup"><span data-stu-id="2b4ad-134">For more information, see [The Purpose of the Windows PowerShell ISE Scripting Object Model](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).</span></span>

<span data-ttu-id="2b4ad-135">**Jaką wartość ma dodać ta zmiana?**</span><span class="sxs-lookup"><span data-stu-id="2b4ad-135">**What value does this change add?**</span></span>

<span data-ttu-id="2b4ad-136">Dodatki umożliwiają rozszerzanie i dostosowywanie Windows PowerShell ISE za pomocą narzędzi, które dodają funkcje i wzbogacają obsługę skryptów.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-136">Add-ons allow you to extend and customize Windows PowerShell ISE with tools that add functionality and enhance your scripting experience.</span></span>

<span data-ttu-id="2b4ad-137">**Co działa inaczej?**</span><span class="sxs-lookup"><span data-stu-id="2b4ad-137">**What works differently?**</span></span>

<span data-ttu-id="2b4ad-138">Windows PowerShell ISE 3,0 i nowsze są dołączone do dodatku **Commands** .</span><span class="sxs-lookup"><span data-stu-id="2b4ad-138">Windows PowerShell ISE 3.0 and later come with the **Commands** add-on.</span></span> <span data-ttu-id="2b4ad-139">Dodatek **polecenia** umożliwia przeglądanie poleceń cmdlet i dostęp do pomocy dotyczącej poleceń cmdlet obok siebie przy użyciu okienek **skryptu** i **konsoli** .</span><span class="sxs-lookup"><span data-stu-id="2b4ad-139">The **Commands** add-on allows you to browse cmdlets, and access help about the cmdlets side-by-side with the **Script** and **Console** Panes.</span></span>

<span data-ttu-id="2b4ad-140">Dodatkowe dodatki można znaleźć za pomocą polecenia **Otwórz witrynę internetową narzędzia dodatków** w menu **Dodatki** .</span><span class="sxs-lookup"><span data-stu-id="2b4ad-140">Additional add-ons can be found by using the **Open Add-on Tools Website** command on the **Add-ons** menu.</span></span>

## <a name="restart-manager-and-auto-save"></a><span data-ttu-id="2b4ad-141">Uruchom ponownie Menedżera i automatycznie Zapisz</span><span class="sxs-lookup"><span data-stu-id="2b4ad-141">Restart manager and auto-save</span></span>

> <span data-ttu-id="2b4ad-142">Dodano w programie PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="2b4ad-142">Added in PowerShell 3.0</span></span>

<span data-ttu-id="2b4ad-143">Windows PowerShell ISE teraz automatycznie zapisuje otwarte skrypty co dwie minuty, w osobnej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-143">Windows PowerShell ISE now automatically saves your open scripts every two minutes, in a separate location.</span></span> <span data-ttu-id="2b4ad-144">Po ponownym uruchomieniu Windows PowerShell ISE po nieoczekiwanym awarii lub ponownym uruchomieniu program odzyskuje skrypty otwarte w ostatniej sesji, nawet jeśli skrypty nie zostały zapisane.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-144">When Windows PowerShell ISE restarts after an unexpected crash or reboot, it recovers scripts that were open in the last session, even if the scripts weren't saved.</span></span>

<span data-ttu-id="2b4ad-145">Aby zmienić interwał automatycznego zapisywania, uruchom następujące polecenie w okienku konsoli: `$psise.Options.AutoSaveMinuteInterval`.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-145">To change the automatic saving interval, run the following command in the Console pane: `$psise.Options.AutoSaveMinuteInterval`.</span></span>

<span data-ttu-id="2b4ad-146">**Jaką wartość ma dodać ta zmiana?**</span><span class="sxs-lookup"><span data-stu-id="2b4ad-146">**What value does this change add?**</span></span>

<span data-ttu-id="2b4ad-147">Teraz możesz korzystać z Windows PowerShell ISE, wiedząc, że otwarte skrypty są zapisywane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-147">You can now work within Windows PowerShell ISE knowing that your open scripts are automatically saved.</span></span>

<span data-ttu-id="2b4ad-148">**Co działa inaczej?**</span><span class="sxs-lookup"><span data-stu-id="2b4ad-148">**What works differently?**</span></span>

<span data-ttu-id="2b4ad-149">Windows PowerShell ISE 2,0 nie zapisuje skryptów automatycznie.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-149">Windows PowerShell ISE 2.0 doesn't save the scripts automatically.</span></span>

## <a name="most-recently-used-list"></a><span data-ttu-id="2b4ad-150">Lista ostatnio używanych</span><span class="sxs-lookup"><span data-stu-id="2b4ad-150">Most-recently used list</span></span>

> <span data-ttu-id="2b4ad-151">Dodano w programie PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="2b4ad-151">Added in PowerShell 3.0</span></span>

<span data-ttu-id="2b4ad-152">Windows PowerShell ISE teraz zawiera listę ostatnio używanych plików.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-152">Windows PowerShell ISE now has a most-recently used list for files.</span></span> <span data-ttu-id="2b4ad-153">Po otwarciu pliku w Windows PowerShell ISE, plik zostanie dodany do listy ostatnio używane w menu **plik** .</span><span class="sxs-lookup"><span data-stu-id="2b4ad-153">When you open a file in Windows PowerShell ISE, the file is added to the most-recently used list on the **File** menu.</span></span>

<span data-ttu-id="2b4ad-154">Aby zmienić domyślną liczbę plików na ostatnio używanej liście, uruchom następujące polecenie w okienku konsoli: `$psise.Options.MruCount`.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-154">To change the default number of files in the most-recently used list, run the following command in the Console Pane: `$psise.Options.MruCount`.</span></span>

<span data-ttu-id="2b4ad-155">**Jaką wartość ma dodać ta zmiana?**</span><span class="sxs-lookup"><span data-stu-id="2b4ad-155">**What value does this change add?**</span></span>

<span data-ttu-id="2b4ad-156">Teraz można korzystać z listy ostatnio używanych plików, aby łatwo uzyskać dostęp do często używanych danych.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-156">You can now use the most-recently used list to easily access your frequently used files.</span></span>

<span data-ttu-id="2b4ad-157">**Co działa inaczej?**</span><span class="sxs-lookup"><span data-stu-id="2b4ad-157">**What works differently?**</span></span>

<span data-ttu-id="2b4ad-158">Windows PowerShell ISE 2,0 nie ma ostatnio używanej listy.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-158">Windows PowerShell ISE 2.0 doesn't have a most-recently used list.</span></span>

## <a name="console-pane"></a><span data-ttu-id="2b4ad-159">Okienko konsoli</span><span class="sxs-lookup"><span data-stu-id="2b4ad-159">Console Pane</span></span>

> <span data-ttu-id="2b4ad-160">Dodano w programie PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="2b4ad-160">Added in PowerShell 3.0</span></span>

<span data-ttu-id="2b4ad-161">Osobne okienka poleceń i danych wyjściowych, które były dostępne w pierwszej wersji Windows PowerShell ISE, zostały połączone w jednym okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-161">The separate Command and Output Panes that were available in the first release of Windows PowerShell ISE have been combined into a single Console Pane.</span></span> <span data-ttu-id="2b4ad-162">Okienko konsoli jest podobne do funkcji i wyglądu typowej konsoli programu Windows PowerShell, ale zawiera następujące udoskonalenia:</span><span class="sxs-lookup"><span data-stu-id="2b4ad-162">The Console Pane is similar in function and appearance to a typical Windows PowerShell console, but it includes the following enhancements:</span></span>

- <span data-ttu-id="2b4ad-163">Kolorowanie składni dla tekstu wejściowego (nie tekstu wyjściowego), w tym składni XML</span><span class="sxs-lookup"><span data-stu-id="2b4ad-163">Syntax coloring for input text (not output text), including XML syntax</span></span>
- <span data-ttu-id="2b4ad-164">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="2b4ad-164">IntelliSense</span></span>
- <span data-ttu-id="2b4ad-165">Dopasowywanie nawiasów klamrowych</span><span class="sxs-lookup"><span data-stu-id="2b4ad-165">Brace matching</span></span>
- <span data-ttu-id="2b4ad-166">Wskazanie błędu</span><span class="sxs-lookup"><span data-stu-id="2b4ad-166">Error indication</span></span>
- <span data-ttu-id="2b4ad-167">Pełna obsługa standardu Unicode</span><span class="sxs-lookup"><span data-stu-id="2b4ad-167">Full Unicode support</span></span>
- <span data-ttu-id="2b4ad-168"><kbd>Klawisz F1</kbd> — pomoc kontekstowa</span><span class="sxs-lookup"><span data-stu-id="2b4ad-168"><kbd>F1</kbd> context-sensitive help</span></span>
- <span data-ttu-id="2b4ad-169"><kbd></kbd>Ctrl+<kbd>F1</kbd> z kontekstem Pokaż polecenie</span><span class="sxs-lookup"><span data-stu-id="2b4ad-169"><kbd>Ctrl</kbd>+<kbd>F1</kbd> context-sensitive Show-Command</span></span>
- <span data-ttu-id="2b4ad-170">Złożony skrypt i pomoc techniczna od prawej do lewej</span><span class="sxs-lookup"><span data-stu-id="2b4ad-170">Complex script and right-to-left support</span></span>
- <span data-ttu-id="2b4ad-171">Obsługa czcionek</span><span class="sxs-lookup"><span data-stu-id="2b4ad-171">Font support</span></span>
- <span data-ttu-id="2b4ad-172">Powiększenie</span><span class="sxs-lookup"><span data-stu-id="2b4ad-172">Zoom</span></span>
- <span data-ttu-id="2b4ad-173">Tryby wyboru wiersza i wyboru bloku</span><span class="sxs-lookup"><span data-stu-id="2b4ad-173">Line-select and block-select modes</span></span>
- <span data-ttu-id="2b4ad-174">Zachowywanie wpisanej zawartości w wierszu polecenia po naciśnięciu <kbd>strzałki</kbd> w celu wyświetlenia historii w konsoli</span><span class="sxs-lookup"><span data-stu-id="2b4ad-174">Preservation of typed content at the command line when you press the <kbd>UpArrow</kbd> to view history in the console</span></span>

<span data-ttu-id="2b4ad-175">**Jaką wartość ma dodać ta zmiana?**</span><span class="sxs-lookup"><span data-stu-id="2b4ad-175">**What value does this change add?**</span></span>

<span data-ttu-id="2b4ad-176">Dodanie tych zmian w okienku konsoli zapewnia obsługę skryptów, która jest bardziej spójna z interfejsem konsoli.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-176">The addition of these Console Pane changes provides a scripting experience that is more consistent with the console interface.</span></span>

<span data-ttu-id="2b4ad-177">**Co działa inaczej?**</span><span class="sxs-lookup"><span data-stu-id="2b4ad-177">**What works differently?**</span></span>

<span data-ttu-id="2b4ad-178">Windows PowerShell ISE 2,0 ma oddzielne okienka poleceń i danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-178">Windows PowerShell ISE 2.0 has separate Command and Output Panes.</span></span>

## <a name="command-line-switches"></a><span data-ttu-id="2b4ad-179">Przełączniki wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="2b4ad-179">Command-line switches</span></span>

> <span data-ttu-id="2b4ad-180">Dodano w programie PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="2b4ad-180">Added in PowerShell 3.0</span></span>

<span data-ttu-id="2b4ad-181">Po rozpoczęciu Windows PowerShell ISE z wiersza polecenia (przez wpisanie **powershell_ise. exe**) można dodać następujące nowe przełączniki wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-181">If you start Windows PowerShell ISE from the command line (by typing **powershell_ise.exe**), you can add the following new command-line switches.</span></span>

- <span data-ttu-id="2b4ad-182">`-NoProfile`: Uruchamia Windows PowerShell ISE bez uruchamiania`$profile`</span><span class="sxs-lookup"><span data-stu-id="2b4ad-182">`-NoProfile`: Starts Windows PowerShell ISE without running `$profile`</span></span>
- <span data-ttu-id="2b4ad-183">`-Help`: Wyświetla okno Pomoc</span><span class="sxs-lookup"><span data-stu-id="2b4ad-183">`-Help`: Displays a Help window</span></span>
- <span data-ttu-id="2b4ad-184">`-mta`: Uruchamia Windows PowerShell ISE w trybie wielowątkowej komórki.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-184">`-mta`: Starts Windows PowerShell ISE in multithreaded apartment mode.</span></span> <span data-ttu-id="2b4ad-185">Domyślny tryb operacji dla Windows PowerShell ISE jest trybem apartamentu jednowątkowego lub `-sta`.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-185">The default operation mode for Windows PowerShell ISE is single-threaded apartment mode, or `-sta`.</span></span>

<span data-ttu-id="2b4ad-186">**Jaką wartość ma dodać ta zmiana?**</span><span class="sxs-lookup"><span data-stu-id="2b4ad-186">**What value does this change add?**</span></span>

<span data-ttu-id="2b4ad-187">Dodanie tych przełączników wiersza polecenia pozwala kontrolować środowisko, w którym działa Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-187">The addition of these command-line switches allows you to control the environment in which the Windows PowerShell ISE runs.</span></span>

<span data-ttu-id="2b4ad-188">**Co działa inaczej?**</span><span class="sxs-lookup"><span data-stu-id="2b4ad-188">**What works differently?**</span></span>

<span data-ttu-id="2b4ad-189">Windows PowerShell ISE 2,0 nie rozpoznaje tych przełączników wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-189">Windows PowerShell ISE 2.0 doesn't recognize these command-line switches.</span></span>

## <a name="new-editor-features"></a><span data-ttu-id="2b4ad-190">Nowe funkcje edytora</span><span class="sxs-lookup"><span data-stu-id="2b4ad-190">New editor features</span></span>

> <span data-ttu-id="2b4ad-191">Dodano w programie PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="2b4ad-191">Added in PowerShell 3.0</span></span>

<span data-ttu-id="2b4ad-192">Inne funkcje edycji Windows PowerShell ISE obejmują:</span><span class="sxs-lookup"><span data-stu-id="2b4ad-192">Other Windows PowerShell ISE editing features include:</span></span>

- <span data-ttu-id="2b4ad-193">**Kolorowanie składni XML** — Windows PowerShell ISE teraz kolory składni XML w taki sam sposób jak składnia programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-193">**XML syntax coloring** - Windows PowerShell ISE now colors XML syntax in the same way as it colors Windows PowerShell syntax.</span></span>
- <span data-ttu-id="2b4ad-194">**Dopasowywanie nawiasów klamrowych** — Windows PowerShell ISE obejmuje Dopasowywanie nawiasów klamrowych i wyróżnianie, a także może być używane w następujący sposób: (na przykład za pomocą polecenia **Przejdź do dopasowania** lub <kbd>klawisza Ctrl</kbd>+<kbd>)</kbd> lokalizuje zamykający nawias klamrowy, jeśli ma zaznaczone nawiasy otwierające).</span><span class="sxs-lookup"><span data-stu-id="2b4ad-194">**Brace matching** - Windows PowerShell ISE includes brace matching and highlighting, and can be used in the following ways: (for example, using the **Go to Match** command or <kbd>Ctrl</kbd>+<kbd>]</kbd> locates the closing brace, if you have an opening brace selected).</span></span>
- <span data-ttu-id="2b4ad-195">**Widok konspektu** Okienko skrypt obsługuje konspekt, który umożliwia zwijanie lub rozwijanie sekcji kodu przez kliknięcie znaku plus lub minus na lewym marginesie.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-195">**Outline view** The Script Pane supports outlining, which allows collapsing or expanding sections of code by clicking plus or minus signs in the left margin.</span></span> <span data-ttu-id="2b4ad-196">Aby oznaczyć początek lub koniec sekcji zwijanej `#endregion` , można użyć nawiasów klamrowych lub `#region` tagów i.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-196">You can use braces or the `#region` and `#endregion` tags to mark the beginning or end of a collapsible section.</span></span> <span data-ttu-id="2b4ad-197">Aby rozwinąć lub zwinąć wszystkie regiony, naciśnij klawisz <kbd>Ctrl</kbd>+<kbd>M</kbd>.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-197">To expand or collapse all regions, press <kbd>Ctrl</kbd>+<kbd>M</kbd>.</span></span>
- <span data-ttu-id="2b4ad-198">**Edytowanie tekstu metodą "przeciągnij i upuść** " — Windows PowerShell ISE teraz obsługuje edycję tekstu metodą "przeciągnij i upuść".</span><span class="sxs-lookup"><span data-stu-id="2b4ad-198">**Drag and drop text editing** - Windows PowerShell ISE now supports drag and drop text editing.</span></span> <span data-ttu-id="2b4ad-199">Można wybrać dowolny blok tekstu i przeciągnąć ten tekst do innej lokalizacji w edytorze lub konsoli programu w celu przeniesienia tekstu.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-199">You can select any block of text and drag that text to another location in the editor or the console to move the text.</span></span> <span data-ttu-id="2b4ad-200">Jeśli przytrzymasz wciśnięty klawisz <kbd>Ctrl</kbd> podczas przeciągania zaznaczonego tekstu, po zwolnieniu przycisku myszy tekst zostanie skopiowany do nowej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-200">If you hold down the <kbd>Ctrl</kbd> key while you drag the selected text, when you release the mouse button the text is copied to the new location.</span></span> <span data-ttu-id="2b4ad-201">W tej wersji Windows PowerShell ISE, gdy przeciągasz i upuszczasz pliki na Windows PowerShell ISE, Windows PowerShell ISE otwiera plik.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-201">In this version of Windows PowerShell ISE, when you drag and drop files onto Windows PowerShell ISE, Windows PowerShell ISE opens the file.</span></span>
- <span data-ttu-id="2b4ad-202">**Wyświetlanie** błędów analizy — błędy analizy są oznaczone czerwonymi podkreśleniami.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-202">**Parse error display** - Parse errors are indicated with red underlines.</span></span> <span data-ttu-id="2b4ad-203">Po umieszczeniu wskaźnika myszy nad wskazanym błędem tekst etykietki narzędzia zawiera problem znaleziony w kodzie.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-203">When you hover over an indicated error, tooltip text displays the problem that was found in the code.</span></span>
- <span data-ttu-id="2b4ad-204">**Powiększenie** — procent powiększenia zawartości konsoli można ustawić za pomocą suwaka powiększenia (w prawym dolnym rogu okna Windows PowerShell ISE) lub wprowadzając polecenie `$psise.options.Zoom` w okienku konsoli.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-204">**Zoom** - The zoom percentage of the console's content can be set by using the zoom slider (in the lower right corner of Windows PowerShell ISE window), or by entering the command `$psise.options.Zoom` in the Console Pane.</span></span>
- <span data-ttu-id="2b4ad-205">**Kopiowanie tekstu sformatowanego i wklejanie** do schowka w Windows PowerShell ISE zachowuje czcionkę, rozmiar i informacje o kolorze oryginalnego zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-205">**Rich text copy and paste** - Copying to the clipboard in Windows PowerShell ISE preserves the font, size, and color information of the original selection.</span></span>
- <span data-ttu-id="2b4ad-206">**Zaznaczenie blokowe** — można wybrać blok tekstu, przytrzymując wciśnięty klawisz <kbd>Alt</kbd> podczas zaznaczania tekstu w okienku skrypt za pomocą myszy lub naciskając klawisz <kbd>Alt</kbd>+<kbd>SHIFT</kbd>+<kbd>strzałkę</kbd>.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-206">**Block selection** - You can select a block of text by holding down the <kbd>ALT</kbd> key while selecting text in the Script Pane with your mouse, or by pressing <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>Arrow</kbd>.</span></span>

<span data-ttu-id="2b4ad-207">**Jaką wartość ma dodać ta zmiana?**</span><span class="sxs-lookup"><span data-stu-id="2b4ad-207">**What value does this change add?**</span></span>

<span data-ttu-id="2b4ad-208">Dodatkowe funkcje edycji zapewniają bardziej spójne i wydajne Edytowanie środowiska.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-208">The additional editing features provide a more consistent and powerful editing environment.</span></span>

<span data-ttu-id="2b4ad-209">**Co działa inaczej?**</span><span class="sxs-lookup"><span data-stu-id="2b4ad-209">**What works differently?**</span></span>

<span data-ttu-id="2b4ad-210">Te ulepszenia edycji nie były obecne w Windows PowerShell ISE 2,0.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-210">These editing enhancements weren't present in Windows PowerShell ISE 2.0.</span></span>

## <a name="new-help-viewer-window"></a><span data-ttu-id="2b4ad-211">Nowe okno podglądu pomocy</span><span class="sxs-lookup"><span data-stu-id="2b4ad-211">New Help viewer window</span></span>

> <span data-ttu-id="2b4ad-212">Dodano w programie PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="2b4ad-212">Added in PowerShell 3.0</span></span>

<span data-ttu-id="2b4ad-213">Jeśli naciśniesz klawisz <kbd>F1</kbd> , gdy kursor znajduje się w poleceniu cmdlet lub że masz część polecenia cmdlet, w nowym podglądzie pomocy zostanie otwarta pomoc kontekstowa o wyróżnionym poleceniu cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-213">If you press <kbd>F1</kbd> when your cursor is in a cmdlet, or you have part of a cmdlet highlighted, the new Help viewer opens context-sensitive Help about the highlighted cmdlet.</span></span> <span data-ttu-id="2b4ad-214">Aby wyświetlić **Informacje o** pomocy programu Windows PowerShell `operators` , wpisz w okienku konsoli, a następnie naciśnij klawisz <kbd>F1</kbd>.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-214">To display Windows PowerShell **About** help, type `operators` in the console pane, and then press <kbd>F1</kbd>.</span></span>

<span data-ttu-id="2b4ad-215">Przed użyciem tej funkcji należy pobrać najnowszą wersję tematów pomocy programu Windows PowerShell z witryny sieci Web firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-215">Before you use this feature, download the most current version of Windows PowerShell Help topics from the Microsoft website.</span></span> <span data-ttu-id="2b4ad-216">Najprostszą metodą pobierania tematów pomocy jest uruchomienie `Update-Help` polecenia cmdlet w okienku konsoli programu podczas uruchamiania Windows PowerShell ISE jako administrator.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-216">The simplest method for downloading the Help topics is to run the `Update-Help` cmdlet in the Console Pane when running Windows PowerShell ISE as administrator.</span></span>

<span data-ttu-id="2b4ad-217">Można zmienić miejsce, w którym będzie wyglądał klawisz <kbd>F1</kbd> w celu uzyskania pomocy.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-217">You can alter where the <kbd>F1</kbd> key looks for Help.</span></span> <span data-ttu-id="2b4ad-218">W menu**Opcje** **narzędzi**/na karcie **Ustawienia ogólne** w obszarze **inne ustawienia**możesz ustawić lub wyczyścić pole wyboru **Użyj lokalnej zawartości pomocy zamiast zawartości online**.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-218">In the **Tools**/**Options** menu, on the **General Settings** tab, under **Other Settings**, you can set or clear the checkbox **Use local help content instead of online content**.</span></span> <span data-ttu-id="2b4ad-219">Po zaznaczeniu tej opcji klient szuka pomocy poleceń cmdlet w pobranej pomocy znalezionej w folderze moduły.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-219">When checked, the client looks for the cmdlet Help in the downloaded Help found in the modules folder.</span></span> <span data-ttu-id="2b4ad-220">Jeśli pole wyboru jest wyczyszczone, klient szuka pomocy w trybie online.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-220">If the checkbox is cleared, the client looks for help online.</span></span>

<span data-ttu-id="2b4ad-221">**Jaką wartość ma dodać ta zmiana?**</span><span class="sxs-lookup"><span data-stu-id="2b4ad-221">**What value does this change add?**</span></span>

<span data-ttu-id="2b4ad-222">Pomoc kontekstowa bez opuszczania bieżącego polecenia cmdlet lub skryptu zapewnia zintegrowane środowisko szkoleniowe.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-222">Context-sensitive Help without leaving your current cmdlet or script provides an integrated learning experience.</span></span>

<span data-ttu-id="2b4ad-223">**Co działa inaczej?**</span><span class="sxs-lookup"><span data-stu-id="2b4ad-223">**What works differently?**</span></span>

<span data-ttu-id="2b4ad-224">Naciśnij klawisz <kbd>F1</kbd> w poprzednich wersjach Windows PowerShell ISE otworzyć plik pomocy na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-224">Pressing <kbd>F1</kbd> in previous versions of Windows PowerShell ISE opened the help file on the local computer.</span></span> <span data-ttu-id="2b4ad-225">W Windows PowerShell ISE 3,0 i nowszych zostanie otwarte okno zawierające pomoc dla polecenia cmdlet, które można wyszukiwać i konfigurować.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-225">In Windows PowerShell ISE 3.0 and later, a window opens that contains the help for the cmdlet that is searchable and configurable.</span></span> <span data-ttu-id="2b4ad-226">To środowisko pomocy jest nowe dla Windows PowerShell ISE 3,0 i aktualizowalnej pomocy jest Nowość w programie Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-226">This Help experience is new for Windows PowerShell ISE 3.0, and Updatable Help is new for Windows PowerShell 3.0.</span></span>

## <a name="show-command-cmdlet"></a><span data-ttu-id="2b4ad-227">Show-Command — polecenie cmdlet</span><span class="sxs-lookup"><span data-stu-id="2b4ad-227">Show-Command cmdlet</span></span>

> <span data-ttu-id="2b4ad-228">Dodano w programie PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="2b4ad-228">Added in PowerShell 3.0</span></span>

<span data-ttu-id="2b4ad-229">`Show-Command` Polecenie cmdlet umożliwia tworzenie lub uruchamianie poleceń cmdlet lub funkcji przez wypełnienie formularza graficznego.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-229">The `Show-Command` cmdlet enables you to compose or run a cmdlet or function by filling in a graphical form.</span></span> <span data-ttu-id="2b4ad-230">Formularz umożliwia użytkownikom współpracę z programem Windows PowerShell w środowisku graficznym.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-230">The form lets users work with Windows PowerShell in a graphical environment.</span></span>
<span data-ttu-id="2b4ad-231">`Show-Command`umożliwia również zaawansowanym skryptom tworzenie szybkiego interfejsu GUI opartego na programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-231">`Show-Command` also enables advanced scripters to create a quick Windows PowerShell-based GUI.</span></span>

<span data-ttu-id="2b4ad-232">**Jaką wartość ma dodać ta zmiana?**</span><span class="sxs-lookup"><span data-stu-id="2b4ad-232">**What value does this change add?**</span></span>

<span data-ttu-id="2b4ad-233">Korzystając `Show-Command` ze skryptów programu Windows PowerShell, możesz udostępnić użytkownikom środowisko graficzne, za pomocą którego są one znane.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-233">By using `Show-Command` in your Windows PowerShell scripts, you can provide your users with the graphical environment with which they're familiar.</span></span> <span data-ttu-id="2b4ad-234">`Show-Command`może również pomóc użytkownikom wprowadzającym informacje w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-234">`Show-Command` can also help introductory users learn Windows PowerShell.</span></span>

<span data-ttu-id="2b4ad-235">**Co działa inaczej?**</span><span class="sxs-lookup"><span data-stu-id="2b4ad-235">**What works differently?**</span></span>

<span data-ttu-id="2b4ad-236">`Show-Command`jest nowym Windows PowerShell ISE 3,0.</span><span class="sxs-lookup"><span data-stu-id="2b4ad-236">`Show-Command` is new Windows PowerShell ISE 3.0.</span></span>

## <a name="see-also"></a><span data-ttu-id="2b4ad-237">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b4ad-237">See also</span></span>

<span data-ttu-id="2b4ad-238">Aby uzyskać więcej informacji o korzystaniu z Windows PowerShell ISE, zobacz [Eksplorowanie środowiska Windows PowerShell Integrated Scripting Environment](../getting-started/fundamental/exploring-the-windows-powershell-ise.md).</span><span class="sxs-lookup"><span data-stu-id="2b4ad-238">For more information about using Windows PowerShell ISE, see [Exploring the Windows PowerShell Integrated Scripting Environment](../getting-started/fundamental/exploring-the-windows-powershell-ise.md).</span></span>
