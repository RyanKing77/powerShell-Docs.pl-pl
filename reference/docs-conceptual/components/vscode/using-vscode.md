---
title: Używanie programu Visual Studio Code do tworzenia aplikacji programu PowerShell
description: Używanie programu Visual Studio Code do tworzenia aplikacji programu PowerShell
ms.date: 08/06/2018
ms.openlocfilehash: 0d796460511b273771eacb03d0df4d90e1e9c322
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854398"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="2a52b-103">Używanie programu Visual Studio Code do tworzenia aplikacji programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="2a52b-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="2a52b-104">Oprócz [PowerShell ISE][ise], programu PowerShell jest również dobrze jest obsługiwany w programie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="2a52b-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="2a52b-105">Ponadto środowiska ISE nie jest obsługiwana przy użyciu programu PowerShell Core, chociaż program Visual Studio Code jest przeznaczony dla programu PowerShell Core na wszystkich platformach (Windows, macOS i Linux)</span><span class="sxs-lookup"><span data-stu-id="2a52b-105">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="2a52b-106">Można użyć programu Visual Studio Code na Windows przy użyciu programu PowerShell w wersji 5 przy użyciu systemu Windows 10 lub dzięki zainstalowaniu [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) dla niskiego poziomu OSs Windows (Windows 8.1, itp.).</span><span class="sxs-lookup"><span data-stu-id="2a52b-106">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="2a52b-107">Przed jej rozpoczęciem, upewnij się, że program PowerShell znajduje się w Twoim systemie.</span><span class="sxs-lookup"><span data-stu-id="2a52b-107">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="2a52b-108">W przypadku nowoczesnych obciążeń w Windows, macOS i Linux zobacz:</span><span class="sxs-lookup"><span data-stu-id="2a52b-108">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="2a52b-109">[Instalowanie programu PowerShell Core w systemie Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="2a52b-109">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="2a52b-110">[Instalowanie programu PowerShell Core w systemie macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="2a52b-110">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="2a52b-111">[Instalowanie programu PowerShell Core w Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="2a52b-111">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="2a52b-112">W przypadku tradycyjnych obciążeń programu Windows PowerShell, zobacz [Instalowanie programu Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="2a52b-112">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="2a52b-113">Edytowanie w programie Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="2a52b-113">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="2a52b-114">1. Instalowanie programu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="2a52b-114">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="2a52b-115">**Linux**: postępuj zgodnie z instrukcjami instalacji na [uruchomiony program VS Code w systemie Linux](https://code.visualstudio.com/docs/setup/linux) strony</span><span class="sxs-lookup"><span data-stu-id="2a52b-115">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="2a52b-116">**System macOS**: postępuj zgodnie z instrukcjami instalacji na [uruchomiony program VS Code w systemie macOS](https://code.visualstudio.com/docs/setup/mac) strony</span><span class="sxs-lookup"><span data-stu-id="2a52b-116">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="2a52b-117">W systemie macOS należy zainstalować protokół OpenSSL rozszerzenia programu PowerShell, do prawidłowego działania.</span><span class="sxs-lookup"><span data-stu-id="2a52b-117">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
  > <span data-ttu-id="2a52b-118">W tym celu najłatwiej zainstalował [Homebrew](https://brew.sh/) , a następnie uruchom `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="2a52b-118">The easiest way to accomplish this is to install [Homebrew](https://brew.sh/) and then run `brew install openssl`.</span></span>
  > <span data-ttu-id="2a52b-119">Program VS Code można teraz pomyślnie załadować rozszerzenia programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2a52b-119">VS Code can now load the PowerShell extension successfully.</span></span>

- <span data-ttu-id="2a52b-120">**Windows**: postępuj zgodnie z instrukcjami instalacji na [uruchomiony program VS Code w Windows](https://code.visualstudio.com/docs/setup/windows) strony</span><span class="sxs-lookup"><span data-stu-id="2a52b-120">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="2a52b-121">2. Instalowanie rozszerzenia programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="2a52b-121">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="2a52b-122">Uruchomienie programu Visual Studio Code aplikacji przez:</span><span class="sxs-lookup"><span data-stu-id="2a52b-122">Launch the Visual Studio Code app by:</span></span>
  - <span data-ttu-id="2a52b-123">**Windows**: wpisywanie `code` w sesji programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="2a52b-123">**Windows**: typing `code` in your PowerShell session</span></span>
  - <span data-ttu-id="2a52b-124">**Linux**: wpisywanie `code` w terminalu</span><span class="sxs-lookup"><span data-stu-id="2a52b-124">**Linux**: typing `code` in your terminal</span></span>
  - <span data-ttu-id="2a52b-125">**System macOS**: wpisywanie `code` w terminalu</span><span class="sxs-lookup"><span data-stu-id="2a52b-125">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="2a52b-126">Uruchom **szybkiego otwierania** , naciskając klawisz **Ctrl + P** (**Cmd + P** na komputerze Mac).</span><span class="sxs-lookup"><span data-stu-id="2a52b-126">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="2a52b-127">W szybkiego otwierania wpisz `ext install powershell` i kliknij przycisk **Enter**.</span><span class="sxs-lookup"><span data-stu-id="2a52b-127">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="2a52b-128">**Rozszerzenia** zostanie otwarty widok na pasku bocznym.</span><span class="sxs-lookup"><span data-stu-id="2a52b-128">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="2a52b-129">Zaznacz rozszerzenie programu PowerShell firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2a52b-129">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="2a52b-130">Powinny zostać wyświetlone informacje, takie jak poniżej:</span><span class="sxs-lookup"><span data-stu-id="2a52b-130">You should see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="2a52b-132">Kliknij przycisk **zainstalować** przycisku na rozszerzeniu programu PowerShell firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2a52b-132">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="2a52b-133">Po zakończeniu instalacji zostanie wyświetlony **zainstalować** przechodzi przycisk **Załaduj ponownie**.</span><span class="sxs-lookup"><span data-stu-id="2a52b-133">After the install, you see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="2a52b-134">Kliknij pozycję **Załaduj ponownie**.</span><span class="sxs-lookup"><span data-stu-id="2a52b-134">Click on **Reload**.</span></span>
- <span data-ttu-id="2a52b-135">Visual Studio Code po Załaduj ponownie, wszystko jest gotowe do edycji.</span><span class="sxs-lookup"><span data-stu-id="2a52b-135">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="2a52b-136">Na przykład, aby utworzyć nowy plik, kliknij przycisk **Plik -> Nowy**.</span><span class="sxs-lookup"><span data-stu-id="2a52b-136">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="2a52b-137">Aby zapisać go, kliknij przycisk **Plik -> Zapisz** a następnie podaj nazwę pliku, teraz załóżmy, że `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="2a52b-137">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="2a52b-138">Aby zamknąć plik, kliknij symbol "x" obok nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="2a52b-138">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="2a52b-139">Aby zakończyć działanie programu Visual Studio Code, **Plik -> Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="2a52b-139">To exit Visual Studio Code, **File->Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="2a52b-140">Instalowanie rozszerzenia programu PowerShell w systemach z ograniczeniami</span><span class="sxs-lookup"><span data-stu-id="2a52b-140">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="2a52b-141">Niektóre systemy są konfigurowane w sposób, który wymaga wszystkie podpisy kod do kontroli, a zatem Edytor programu PowerShell usługi ręcznie zatwierdzić do uruchomienia w systemie.</span><span class="sxs-lookup"><span data-stu-id="2a52b-141">Some systems are set up in a way that requires all code signatures to be checked and thus requires PowerShell Editor Services to be manually approved to run on the system.</span></span>
<span data-ttu-id="2a52b-142">Aktualizacji zasad grupy, który zmienia zasady wykonywania jest prawdopodobną przyczyną, jeśli zainstalowano rozszerzenie programu PowerShell, ale zbliżają się błąd, taki jak:</span><span class="sxs-lookup"><span data-stu-id="2a52b-142">A Group Policy update that changes execution policy is a likely cause if you have installed the PowerShell extension but are reaching an error like:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="2a52b-143">Aby ręcznie zatwierdzić usług Edytor programu PowerShell, a tym samym rozszerzenie programu PowerShell dla programu VSCode Otwórz program PowerShell, wiersz polecenia:</span><span class="sxs-lookup"><span data-stu-id="2a52b-143">To manually approve PowerShell Editor Services and thus the PowerShell extension for VSCode open a PowerShell prompt and run:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="2a52b-144">Zostanie wyświetlony monit z "Czy chcesz uruchamiać oprogramowania z tego wydawcy niezaufanych?"</span><span class="sxs-lookup"><span data-stu-id="2a52b-144">You are prompted with "Do you want to run software from this untrusted publisher?"</span></span>
<span data-ttu-id="2a52b-145">Typ `R` do uruchomienia pliku.</span><span class="sxs-lookup"><span data-stu-id="2a52b-145">Type `R` to run the file.</span></span> <span data-ttu-id="2a52b-146">Następnie otwórz w programie Visual Studio Code i sprawdź, czy rozszerzenia programu PowerShell działa prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="2a52b-146">Then, open Visual Studio Code and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="2a52b-147">Jeśli nadal masz problemy, wprowadzenie, Daj nam znać na [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span><span class="sxs-lookup"><span data-stu-id="2a52b-147">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

#### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="2a52b-148">Wybieranie wersji programu PowerShell do korzystania z rozszerzeniem</span><span class="sxs-lookup"><span data-stu-id="2a52b-148">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="2a52b-149">Za pomocą programu PowerShell Core instalowanie side-by-side przy użyciu programu Windows PowerShell jest teraz możliwe do określonej wersji programu PowerShell z rozszerzeniem programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2a52b-149">With PowerShell Core installing side-by-side with Windows PowerShell, is it now possible to a particular version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="2a52b-150">Należy użyć następującego poniższe kroki, aby wybrać wersję:</span><span class="sxs-lookup"><span data-stu-id="2a52b-150">Use the following these steps to choose the version:</span></span>

1. <span data-ttu-id="2a52b-151">Otwórz paletę poleceń (<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> na Windows i Linux, <kbd>Cmd</kbd> + <kbd>Shift</kbd>+<kbd>P</kbd> w systemie macOS).</span><span class="sxs-lookup"><span data-stu-id="2a52b-151">Open the command pallet (<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on Windows & Linux, <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS).</span></span>
1. <span data-ttu-id="2a52b-152">Wyszukaj "Sesja".</span><span class="sxs-lookup"><span data-stu-id="2a52b-152">Search for "Session".</span></span>
1. <span data-ttu-id="2a52b-153">Kliknij pozycję "programu PowerShell: Pokaż Menu sesji".</span><span class="sxs-lookup"><span data-stu-id="2a52b-153">Click on "PowerShell: Show Session Menu".</span></span>
1. <span data-ttu-id="2a52b-154">Wybierz wersję programu PowerShell, którego chcesz użyć z listy — na przykład programu PowerShell Core"".</span><span class="sxs-lookup"><span data-stu-id="2a52b-154">Choose the version of PowerShell you want to use from the list - for example, "PowerShell Core".</span></span>

>[!IMPORTANT]
> <span data-ttu-id="2a52b-155">Ta funkcja sprawdza kilka znanych ścieżek w różnych systemach operacyjnych, aby odnaleźć lokalizacji instalacji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2a52b-155">This feature looks at a few well-known paths on different operating systems to discover install locations of PowerShell.</span></span> <span data-ttu-id="2a52b-156">Po zainstalowaniu programu PowerShell — typowej lokalizacji go może nie być wyświetlana początkowo w Menu sesji.</span><span class="sxs-lookup"><span data-stu-id="2a52b-156">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="2a52b-157">Możesz rozszerzyć menu sesji przez [Dodawanie własnych niestandardowych ścieżek](#adding-your-own-powershell-paths-to-the-session-menu) zgodnie z poniższym opisem.</span><span class="sxs-lookup"><span data-stu-id="2a52b-157">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

>[!NOTE]
> <span data-ttu-id="2a52b-158">Istnieje inny sposób, aby przejść do menu sesji.</span><span class="sxs-lookup"><span data-stu-id="2a52b-158">There is another way to get to the session menu.</span></span> <span data-ttu-id="2a52b-159">Po otwarciu w edytorze pliku programu PowerShell zostanie wyświetlony numer wersji zielony w prawym dolnym rogu.</span><span class="sxs-lookup"><span data-stu-id="2a52b-159">When a PowerShell file is open in your editor, you see a green version number in the bottom right.</span></span> <span data-ttu-id="2a52b-160">Klikając ten numer wersji zostanie wyświetlone menu sesji.</span><span class="sxs-lookup"><span data-stu-id="2a52b-160">Clicking this version number will bring you to the session menu.</span></span>

##### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="2a52b-161">Dodawanie własnego ścieżki programu PowerShell do menu sesji</span><span class="sxs-lookup"><span data-stu-id="2a52b-161">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="2a52b-162">Do menu sesji za pomocą ustawienia programu VS Code, możesz dodać inne ścieżki pliku wykonywalnego programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2a52b-162">You can add other PowerShell executable paths to the session menu through a VS Code setting.</span></span>

<span data-ttu-id="2a52b-163">Dodaj element do listy `powershell.powerShellAdditionalExePaths` lub utworzyć listę, jeśli nie istnieje w Twojej `settings.json`:</span><span class="sxs-lookup"><span data-stu-id="2a52b-163">Add an item to the list  `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],
    
    // other settings...
}
```

<span data-ttu-id="2a52b-164">Każdy element musi mieć:</span><span class="sxs-lookup"><span data-stu-id="2a52b-164">Each item must have:</span></span>

* <span data-ttu-id="2a52b-165">`exePath`: Ścieżka do `pwsh` lub `powershell` pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="2a52b-165">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
* <span data-ttu-id="2a52b-166">`versionName`: Tekst, który będzie wyświetlany w menu sesji.</span><span class="sxs-lookup"><span data-stu-id="2a52b-166">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="2a52b-167">Można ustawić domyślną wersję programu PowerShell do użycia przy użyciu `powershell.powerShellDefaultVersion` ustawienie przez ustawienie, to w tekście wyświetlane w menu sesji (zwane również `versionName` w ostatnim ustawieniu):</span><span class="sxs-lookup"><span data-stu-id="2a52b-167">You can set the default PowerShell version to use using the `powershell.powerShellDefaultVersion` setting by setting this to the text displayed in the session menu (aka the `versionName` in the last setting):</span></span>

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],
    
    "powershell.powerShellDefaultVersion": "Downloaded PowerShell",
    
    // other settings...
}
```

<span data-ttu-id="2a52b-168">Po ustawieniu to ustawienie, uruchom ponownie program Visual Studio Code, lub użyj "dla deweloperów: Ponowne załadowanie okna"akcji wiersza polecenia palety ponownie załadować bieżące okno vscode.</span><span class="sxs-lookup"><span data-stu-id="2a52b-168">Once you've set this setting, restart Visual Studio Code or use the the "Developer: Reload Window" command pallet action to reload the current vscode window.</span></span>

<span data-ttu-id="2a52b-169">Po otwarciu menu sesji, zostanie wyświetlona swoje dodatkowe wersje programu PowerShell!</span><span class="sxs-lookup"><span data-stu-id="2a52b-169">If you open the session menu, you will now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="2a52b-170">Jeśli tworzysz Środowisko PowerShell ze źródła, to doskonały sposób na poziomie lokalnych kompilacji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2a52b-170">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="2a52b-171">Ustawienia konfiguracji dla programu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="2a52b-171">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="2a52b-172">Wykonując kroki opisane w poprzednim akapicie można dodać ustawień konfiguracji w `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="2a52b-172">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="2a52b-173">Zalecamy następujące ustawienia konfiguracji dla programu Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="2a52b-173">We recommend the following configuration settings for Visual Studio Code:</span></span>

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="2a52b-174">Jeśli nie chcesz, aby te ustawienia mają wpływ na wszystkie typy plików, programu VSCode umożliwia także konfiguracje między językami.</span><span class="sxs-lookup"><span data-stu-id="2a52b-174">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="2a52b-175">Utwórz ustawienie określonego języka, umieszczając ustawienia `[<language-name>]` pola.</span><span class="sxs-lookup"><span data-stu-id="2a52b-175">Create a language specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="2a52b-176">Przykład:</span><span class="sxs-lookup"><span data-stu-id="2a52b-176">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="2a52b-177">Aby uzyskać więcej informacji o pliku kodowania w programie VS Code, zobacz [zrozumienie kodowanie pliku](understanding-file-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="2a52b-177">For more information about file encoding in VS Code, see [Understanding file encoding](understanding-file-encoding.md).</span></span>

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="2a52b-178">Debugowanie za pomocą programu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="2a52b-178">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="2a52b-179">Obszar roboczy bez debugowania</span><span class="sxs-lookup"><span data-stu-id="2a52b-179">No-workspace debugging</span></span>

<span data-ttu-id="2a52b-180">Począwszy od wersji programu Visual Studio Code 1.9 można debugować skrypty programu PowerShell, bez konieczności otwierania folderu zawierającego skrypt programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2a52b-180">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span> <span data-ttu-id="2a52b-181">Otwórz plik skryptu programu PowerShell przy użyciu **Plik -> Otwórz plik...** , ustaw punkt przerwania w wierszu (naciśnij klawisz F9), a następnie naciśnij klawisz F5, aby rozpocząć debugowanie.</span><span class="sxs-lookup"><span data-stu-id="2a52b-181">Open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span> <span data-ttu-id="2a52b-182">Powinien zostać wyświetlony w okienku Akcje debugowania są wyświetlane, co pozwala na przerwanie w debugerze, krok, wznowienie i zatrzymać debugowanie.</span><span class="sxs-lookup"><span data-stu-id="2a52b-182">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="2a52b-183">Debugowanie obszaru roboczego</span><span class="sxs-lookup"><span data-stu-id="2a52b-183">Workspace debugging</span></span>

<span data-ttu-id="2a52b-184">Obszar roboczy profilowanie odnosi się do debugowania w kontekście folder, który został otwarty w programie Visual Studio Code przy użyciu **Otwórz Folder...**  z **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="2a52b-184">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="2a52b-185">Folder, który można otworzyć, jest zazwyczaj do folderu projektu programu PowerShell i/lub w katalogu głównym repozytorium Git.</span><span class="sxs-lookup"><span data-stu-id="2a52b-185">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="2a52b-186">Nawet w tym trybie można uruchomić debugowania aktualnie zaznaczonego skryptu programu PowerShell, po prostu naciskając klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="2a52b-186">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="2a52b-187">Jednakże debugowanie obszaru roboczego umożliwia definiowanie wielu konfiguracji debugowania innych niż po prostu debugowania aktualnie otwarty plik.</span><span class="sxs-lookup"><span data-stu-id="2a52b-187">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="2a52b-188">Na przykład można dodać konfiguracji do:</span><span class="sxs-lookup"><span data-stu-id="2a52b-188">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="2a52b-189">Uruchom testy usług Pester w debugerze</span><span class="sxs-lookup"><span data-stu-id="2a52b-189">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="2a52b-190">Uruchom określony plik z argumentami w debugerze</span><span class="sxs-lookup"><span data-stu-id="2a52b-190">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="2a52b-191">Uruchomienie interaktywnej sesji w debugerze</span><span class="sxs-lookup"><span data-stu-id="2a52b-191">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="2a52b-192">Dołącz debuger do procesu hosta programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="2a52b-192">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="2a52b-193">Wykonaj następujące kroki, aby utworzyć plik konfiguracji debugowania:</span><span class="sxs-lookup"><span data-stu-id="2a52b-193">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="2a52b-194">Otwórz **debugowania** widoku, naciskając klawisz **Ctrl + Shift + D** (**Cmd + Shift + D** na komputerze Mac).</span><span class="sxs-lookup"><span data-stu-id="2a52b-194">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
  2. <span data-ttu-id="2a52b-195">Naciśnij klawisz **Konfiguruj** ikonę koła zębatego w pasku narzędzi.</span><span class="sxs-lookup"><span data-stu-id="2a52b-195">Press the **Configure** gear icon in the toolbar.</span></span>
  3. <span data-ttu-id="2a52b-196">Visual Studio Code wyświetli monit o **wybierz środowisko**.</span><span class="sxs-lookup"><span data-stu-id="2a52b-196">Visual Studio Code prompts you to **Select Environment**.</span></span> <span data-ttu-id="2a52b-197">Wybierz **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="2a52b-197">Choose **PowerShell**.</span></span>

  <span data-ttu-id="2a52b-198">Gdy to zrobisz, Visual Studio Code tworzy katalog i plik ".vscode\launch.json" w katalogu głównym folderu obszaru roboczego.</span><span class="sxs-lookup"><span data-stu-id="2a52b-198">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
  <span data-ttu-id="2a52b-199">Jest to, gdzie są przechowywane z konfiguracji debugowania.</span><span class="sxs-lookup"><span data-stu-id="2a52b-199">This is where your debug configuration is stored.</span></span> <span data-ttu-id="2a52b-200">Jeśli pliki znajdują się w repozytorium Git, zazwyczaj chcesz zatwierdzić pliku launch.json.</span><span class="sxs-lookup"><span data-stu-id="2a52b-200">If your files are in a Git repository, you typically want to commit the launch.json file.</span></span>
  <span data-ttu-id="2a52b-201">Zawartość pliku launch.json są:</span><span class="sxs-lookup"><span data-stu-id="2a52b-201">The contents of the launch.json file are:</span></span>

  ```json
  {
    "version": "0.2.0",
    "configurations": [
        {
            "type": "PowerShell",
            "request": "launch",
            "name": "PowerShell Launch (current file)",
            "script": "${file}",
            "args": [],
            "cwd": "${file}"
        },
        {
            "type": "PowerShell",
            "request": "attach",
            "name": "PowerShell Attach to Host Process",
            "processId": "${command.PickPSHostProcess}",
            "runspaceId": 1
        },
        {
            "type": "PowerShell",
            "request": "launch",
            "name": "PowerShell Interactive Session",
            "cwd": "${workspaceRoot}"
        }
    ]
  }
  ```

  <span data-ttu-id="2a52b-202">Reprezentuje typowe scenariusze debugowania.</span><span class="sxs-lookup"><span data-stu-id="2a52b-202">This represents the common debug scenarios.</span></span>
  <span data-ttu-id="2a52b-203">Jednak po otwarciu tego pliku w edytorze można zobaczyć **Dodawanie konfiguracji...**  przycisku.</span><span class="sxs-lookup"><span data-stu-id="2a52b-203">However, when you open this file in the editor, you see an **Add Configuration...** button.</span></span>
  <span data-ttu-id="2a52b-204">Można nacisnąć ten przycisk, aby dodać większą liczbę konfiguracji debugowania programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2a52b-204">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="2a52b-205">Jedna konfiguracja przydatna, aby dodać jest **programu PowerShell: Uruchom skrypt**.</span><span class="sxs-lookup"><span data-stu-id="2a52b-205">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
  <span data-ttu-id="2a52b-206">W przypadku tej konfiguracji można określić specjalny plik z argumentów opcjonalnych, które powinien zostać uruchomiony po każdym naciśnięciu klawisza F5 niezależnie od tego, plik, który jest aktualnie aktywne w edytorze.</span><span class="sxs-lookup"><span data-stu-id="2a52b-206">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

  <span data-ttu-id="2a52b-207">Gdy zostanie nawiązane z konfiguracji debugowania, możesz wybrać konfigurację, która ma być używany podczas sesji debugowania, wybierając jedną z listy rozwijanej w konfiguracji debugowania **debugowania** narzędzi widoku.</span><span class="sxs-lookup"><span data-stu-id="2a52b-207">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="2a52b-208">Istnieje kilka blogi, które mogą być przydatne ułatwią Ci rozpoczęcie pracy przy użyciu rozszerzenia programu PowerShell dla programu Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="2a52b-208">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="2a52b-209">[Rozszerzenie programu PowerShell][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="2a52b-209">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="2a52b-210">[Twórz i Debuguj skrypty programu PowerShell w programie Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="2a52b-210">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="2a52b-211">[Wskazówki dotyczące kodu programu Visual Studio do debugowania][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="2a52b-211">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="2a52b-212">[Debugowanie programu PowerShell w programie Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="2a52b-212">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="2a52b-213">[Wprowadzenie do rozwoju środowiska PowerShell w programie Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="2a52b-213">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="2a52b-214">[Visual Studio Code edytowanie funkcje opracowywania programu PowerShell — część 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="2a52b-214">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="2a52b-215">[Visual Studio Code edytowanie funkcje opracowywania programu PowerShell — część 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="2a52b-215">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="2a52b-216">[Debugowanie skryptu programu PowerShell w programie Visual Studio Code — część 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="2a52b-216">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="2a52b-217">[Debugowanie skryptu programu PowerShell w programie Visual Studio Code — część 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="2a52b-217">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../setup/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="2a52b-218">Rozszerzenie programu PowerShell dla programu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="2a52b-218">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="2a52b-219">Kod źródłowy rozszerzenia programu PowerShell można znaleźć na [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="2a52b-219">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
