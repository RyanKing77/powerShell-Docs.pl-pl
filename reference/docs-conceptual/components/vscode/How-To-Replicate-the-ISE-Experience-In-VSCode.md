---
title: Jak replikować środowiska ISE w programie Visual Studio Code
description: Jak replikować środowiska ISE w programie Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: 0ac38985a842a0dfc6118d0ae7116d12e1579daf
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655539"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="76260-103">Jak replikować środowiska ISE w programie Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="76260-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="76260-104">Rozszerzenie programu PowerShell dla programu VSCode nie Szukaj równoważności funkcji pełną przy użyciu programu PowerShell ISE, są funkcje aby usprawnić środowisko programu VSCode stosować bardziej naturalne użytkownikom środowiska ISE.</span><span class="sxs-lookup"><span data-stu-id="76260-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="76260-105">Ten dokument usiłuje ustawienia listy, które można skonfigurować w VSCode, aby ułatwić bardziej powszechnie znane w porównaniu do środowiska ISE.</span><span class="sxs-lookup"><span data-stu-id="76260-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="76260-106">Powiązania klawiszy</span><span class="sxs-lookup"><span data-stu-id="76260-106">Key bindings</span></span>

| <span data-ttu-id="76260-107">Funkcja</span><span class="sxs-lookup"><span data-stu-id="76260-107">Function</span></span>                              | <span data-ttu-id="76260-108">Powiązanie środowiska ISE</span><span class="sxs-lookup"><span data-stu-id="76260-108">ISE Binding</span></span>                  | <span data-ttu-id="76260-109">Powiązanie programu VSCode</span><span class="sxs-lookup"><span data-stu-id="76260-109">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="76260-110">Przerwij i przerwać debugera</span><span class="sxs-lookup"><span data-stu-id="76260-110">Interrupt and break debugger</span></span>          | <span data-ttu-id="76260-111"><kbd>CTRL</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="76260-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="76260-112"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="76260-112"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="76260-113">Wykonaj bieżący wiersz/wyróżniony tekst</span><span class="sxs-lookup"><span data-stu-id="76260-113">Execute current line/highlighted text</span></span> | <span data-ttu-id="76260-114"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="76260-114"><kbd>F8</kbd></span></span>                | <span data-ttu-id="76260-115"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="76260-115"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="76260-116">Dostępne fragmenty kodu list</span><span class="sxs-lookup"><span data-stu-id="76260-116">List available snippets</span></span>               | <span data-ttu-id="76260-117"><kbd>CTRL</kbd>+<kbd>"j"</kbd></span><span class="sxs-lookup"><span data-stu-id="76260-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="76260-118"><kbd>CTRL</kbd>+<kbd>Alt</kbd>+<kbd>"j"</kbd></span><span class="sxs-lookup"><span data-stu-id="76260-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="76260-119">Powiązania niestandardowe klucza</span><span class="sxs-lookup"><span data-stu-id="76260-119">Custom Key bindings</span></span>

<span data-ttu-id="76260-120">Możesz [skonfigurować własne powiązania klawiszy](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) w VSCode także.</span><span class="sxs-lookup"><span data-stu-id="76260-120">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="tab-completion"></a><span data-ttu-id="76260-121">Uzupełnianie po naciśnięciu tabulatora</span><span class="sxs-lookup"><span data-stu-id="76260-121">Tab completion</span></span>

<span data-ttu-id="76260-122">Aby włączyć bardziej przypominające ISE uzupełniania po naciśnięciu tabulatora, należy dodać ustawienie:</span><span class="sxs-lookup"><span data-stu-id="76260-122">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> <span data-ttu-id="76260-123">To ustawienie zostało dodane bezpośrednio do programu VSCode (a nie w rozszerzeniu).</span><span class="sxs-lookup"><span data-stu-id="76260-123">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="76260-124">Jego zachowanie jest określana przez VSCode bezpośrednio i nie można zmienić przez rozszerzenie.</span><span class="sxs-lookup"><span data-stu-id="76260-124">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="76260-125">Nie szczególnym uwzględnieniem konsoli podczas wykonywania</span><span class="sxs-lookup"><span data-stu-id="76260-125">No focus on console when executing</span></span>

<span data-ttu-id="76260-126">Aby utrzymać uwagę w edytorze podczas wykonywania za pomocą <kbd>F8</kbd>:</span><span class="sxs-lookup"><span data-stu-id="76260-126">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

<span data-ttu-id="76260-127">Wartość domyślna to `true` potrzeby ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="76260-127">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="76260-128">Nie uruchamiaj zintegrowana Konsola przy uruchamianiu</span><span class="sxs-lookup"><span data-stu-id="76260-128">Don't start integrated console on startup</span></span>

<span data-ttu-id="76260-129">Aby zatrzymać zintegrowana Konsola podczas uruchamiania, należy ustawić:</span><span class="sxs-lookup"><span data-stu-id="76260-129">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="76260-130">Tło procesu programu PowerShell nadal rozpocznie się, ponieważ zapewniający intellisense, analizy skryptu, nawigacji symboli, itp. Jednak konsoli nie był już wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="76260-130">The background PowerShell process will still start since that provides intellisense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="76260-131">Przyjęto założenie, że pliki są PowerShell domyślnie</span><span class="sxs-lookup"><span data-stu-id="76260-131">Assume files are PowerShell by default</span></span>

<span data-ttu-id="76260-132">Aby wprowadzić nowy/bez nazwy plików, zarejestruj się jako programu PowerShell, domyślnie:</span><span class="sxs-lookup"><span data-stu-id="76260-132">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a><span data-ttu-id="76260-133">Schemat kolorów</span><span class="sxs-lookup"><span data-stu-id="76260-133">Color scheme</span></span>

<span data-ttu-id="76260-134">Są dostępne dla programu VSCode się Edytor wyglądała znacznie bardziej jak środowiska ISE liczby motywów ISE.</span><span class="sxs-lookup"><span data-stu-id="76260-134">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="76260-135">W [Paleta poleceń] typu `theme` można pobrać `Preferences: Color Theme` i naciśnij klawisz <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="76260-135">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="76260-136">Z listy rozwijanej wybierz `PowerShell ISE`.</span><span class="sxs-lookup"><span data-stu-id="76260-136">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="76260-137">Ten motyw można ustawić w ustawieniach za pomocą:</span><span class="sxs-lookup"><span data-stu-id="76260-137">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a><span data-ttu-id="76260-138">Eksplorator polecenia programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="76260-138">PowerShell Command Explorer</span></span>

<span data-ttu-id="76260-139">Dzięki rozłożeniu pracy [ @corbob ](https://github.com/corbob), rozszerzenie programu PowerShell ma początku własne polecenia Eksploratora.</span><span class="sxs-lookup"><span data-stu-id="76260-139">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="76260-140">W [Paleta poleceń], wprowadź `PowerShell Command Explorer` i naciśnij klawisz <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="76260-140">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="76260-141">Otwórz w środowisku ISE</span><span class="sxs-lookup"><span data-stu-id="76260-141">Open in the ISE</span></span>

<span data-ttu-id="76260-142">Jeśli znajdą się chce otworzyć plik w środowisku ISE mimo to, możesz użyć <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="76260-142">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="76260-143">Inne zasoby</span><span class="sxs-lookup"><span data-stu-id="76260-143">Other resources</span></span>

- <span data-ttu-id="76260-144">ma 4sysops [doskonałe artykułu](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) na temat konfigurowania programu VSCode bardziej, takich jak środowiska ISE.</span><span class="sxs-lookup"><span data-stu-id="76260-144">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="76260-145">Mike F Robbins ma [doskonałe wpis](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) na temat konfigurowania programu VSCode.</span><span class="sxs-lookup"><span data-stu-id="76260-145">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="76260-146">Dowiedz się, programu PowerShell ma [doskonałą zapisu w górę](https://www.learnpwsh.com/setup-vs-code-for-powershell/) na temat pobierania programu VSCode konfiguracji dla programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="76260-146">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="76260-147">Więcej ustawień</span><span class="sxs-lookup"><span data-stu-id="76260-147">More settings</span></span>

<span data-ttu-id="76260-148">Jeśli znasz więcej sposobów tworzenia możesz lepiej zapoznać się dla użytkowników w środowisku ISE programu VSCode przyczyniają się do tego dokumentu. Jeśli jest Konfiguracja zgodności, czego szukasz, ale nie można odnaleźć dowolny sposób, aby ją włączyć, [Otwórz problem](https://github.com/PowerShell/vscode-powershell/issues/new/choose) i Pytaj do woli!</span><span class="sxs-lookup"><span data-stu-id="76260-148">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="76260-149">Zawsze nam miło do akceptowania żądań ściągnięcia oraz kod wniesiony przez także!</span><span class="sxs-lookup"><span data-stu-id="76260-149">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="76260-150">Wskazówki dotyczące programu VSCode</span><span class="sxs-lookup"><span data-stu-id="76260-150">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="76260-151">Paleta poleceń</span><span class="sxs-lookup"><span data-stu-id="76260-151">Command Palette</span></span>

<span data-ttu-id="76260-152"><kbd>F1</kbd> lub <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd> + <kbd> Przenieś</kbd>+<kbd>P</kbd> w systemie macOS)</span><span class="sxs-lookup"><span data-stu-id="76260-152"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="76260-153">Wygodny sposób wykonywania poleceń w VSCode.</span><span class="sxs-lookup"><span data-stu-id="76260-153">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="76260-154">Aby uzyskać więcej informacji, zobacz [VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span><span class="sxs-lookup"><span data-stu-id="76260-154">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[Paleta poleceń]: #command-palette
[Command Palette]: #command-palette
