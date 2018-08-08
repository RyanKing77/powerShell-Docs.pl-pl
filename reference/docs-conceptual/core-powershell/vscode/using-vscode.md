---
title: Używanie programu Visual Studio Code do tworzenia aplikacji programu PowerShell
description: Używanie programu Visual Studio Code do tworzenia aplikacji programu PowerShell
ms.date: 08/06/2018
ms.openlocfilehash: f8e1e9af257037fc7bd74549e4197c9a1695e952
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587435"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="d14f7-103">Używanie programu Visual Studio Code do tworzenia aplikacji programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="d14f7-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="d14f7-104">Oprócz [PowerShell ISE][ise], programu PowerShell jest również dobrze jest obsługiwany w programie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="d14f7-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="d14f7-105">Ponadto środowiska ISE nie jest obsługiwana przy użyciu programu PowerShell Core, chociaż program Visual Studio Code jest przeznaczony dla programu PowerShell Core na wszystkich platformach (Windows, macOS i Linux)</span><span class="sxs-lookup"><span data-stu-id="d14f7-105">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="d14f7-106">Można użyć programu Visual Studio Code na Windows przy użyciu programu PowerShell w wersji 5 przy użyciu systemu Windows 10 lub dzięki zainstalowaniu [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) dla niskiego poziomu OSs Windows (Windows 8.1, itp.).</span><span class="sxs-lookup"><span data-stu-id="d14f7-106">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="d14f7-107">Przed jej rozpoczęciem, upewnij się, że program PowerShell znajduje się w Twoim systemie.</span><span class="sxs-lookup"><span data-stu-id="d14f7-107">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="d14f7-108">W przypadku nowoczesnych obciążeń w Windows, macOS i Linux zobacz:</span><span class="sxs-lookup"><span data-stu-id="d14f7-108">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="d14f7-109">[Instalowanie programu PowerShell Core w systemie Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="d14f7-109">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="d14f7-110">[Instalowanie programu PowerShell Core w systemie macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="d14f7-110">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="d14f7-111">[Instalowanie programu PowerShell Core w Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="d14f7-111">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="d14f7-112">W przypadku tradycyjnych obciążeń programu Windows PowerShell, zobacz [Instalowanie programu Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="d14f7-112">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="d14f7-113">Edytowanie w programie Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="d14f7-113">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="d14f7-114">1. Instalowanie programu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="d14f7-114">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="d14f7-115">**Linux**: postępuj zgodnie z instrukcjami instalacji na [uruchomiony program VS Code w systemie Linux](https://code.visualstudio.com/docs/setup/linux) strony</span><span class="sxs-lookup"><span data-stu-id="d14f7-115">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="d14f7-116">**System macOS**: postępuj zgodnie z instrukcjami instalacji na [uruchomiony program VS Code w systemie macOS](https://code.visualstudio.com/docs/setup/mac) strony</span><span class="sxs-lookup"><span data-stu-id="d14f7-116">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="d14f7-117">W systemie macOS należy zainstalować protokół OpenSSL rozszerzenia programu PowerShell, do prawidłowego działania.</span><span class="sxs-lookup"><span data-stu-id="d14f7-117">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
  > <span data-ttu-id="d14f7-118">W tym celu najłatwiej zainstalował [Homebrew](http://brew.sh/) , a następnie uruchom `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="d14f7-118">The easiest way to accomplish this is to install [Homebrew](http://brew.sh/) and then run `brew install openssl`.</span></span>
  > <span data-ttu-id="d14f7-119">Program VS Code można obecnie załadować rozszerzeń programu PowerShell pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d14f7-119">VS Code can now load the the PowerShell extension successfully.</span></span>

- <span data-ttu-id="d14f7-120">**Windows**: postępuj zgodnie z instrukcjami instalacji na [uruchomiony program VS Code w Windows](https://code.visualstudio.com/docs/setup/windows) strony</span><span class="sxs-lookup"><span data-stu-id="d14f7-120">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="d14f7-121">2. Instalowanie rozszerzenia programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="d14f7-121">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="d14f7-122">Uruchomienie programu Visual Studio Code aplikacji przez:</span><span class="sxs-lookup"><span data-stu-id="d14f7-122">Launch the Visual Studio Code app by:</span></span>
  - <span data-ttu-id="d14f7-123">**Windows**: wpisywanie `code` w sesji programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="d14f7-123">**Windows**: typing `code` in your PowerShell session</span></span>
  - <span data-ttu-id="d14f7-124">**Linux**: wpisywanie `code` w terminalu</span><span class="sxs-lookup"><span data-stu-id="d14f7-124">**Linux**: typing `code` in your terminal</span></span>
  - <span data-ttu-id="d14f7-125">**System macOS**: wpisywanie `code` w terminalu</span><span class="sxs-lookup"><span data-stu-id="d14f7-125">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="d14f7-126">Uruchom **szybkiego otwierania** , naciskając klawisz **Ctrl + P** (**Cmd + P** na komputerze Mac).</span><span class="sxs-lookup"><span data-stu-id="d14f7-126">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="d14f7-127">W szybkiego otwierania wpisz `ext install powershell` i kliknij przycisk **Enter**.</span><span class="sxs-lookup"><span data-stu-id="d14f7-127">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="d14f7-128">**Rozszerzenia** zostanie otwarty widok na pasku bocznym.</span><span class="sxs-lookup"><span data-stu-id="d14f7-128">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="d14f7-129">Zaznacz rozszerzenie programu PowerShell firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d14f7-129">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="d14f7-130">Powinny zostać wyświetlone informacje, takie jak poniżej:</span><span class="sxs-lookup"><span data-stu-id="d14f7-130">You should see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="d14f7-132">Kliknij przycisk **zainstalować** przycisku na rozszerzeniu programu PowerShell firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d14f7-132">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="d14f7-133">Po zakończeniu instalacji zostanie wyświetlony **zainstalować** przechodzi przycisk **Załaduj ponownie**.</span><span class="sxs-lookup"><span data-stu-id="d14f7-133">After the install, you see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="d14f7-134">Kliknij pozycję **Załaduj ponownie**.</span><span class="sxs-lookup"><span data-stu-id="d14f7-134">Click on **Reload**.</span></span>
- <span data-ttu-id="d14f7-135">Visual Studio Code po Załaduj ponownie, wszystko jest gotowe do edycji.</span><span class="sxs-lookup"><span data-stu-id="d14f7-135">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="d14f7-136">Na przykład, aby utworzyć nowy plik, kliknij przycisk **Plik -> Nowy**.</span><span class="sxs-lookup"><span data-stu-id="d14f7-136">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="d14f7-137">Aby zapisać go, kliknij przycisk **Plik -> Zapisz** a następnie podaj nazwę pliku, teraz załóżmy, że `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="d14f7-137">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="d14f7-138">Aby zamknąć plik, kliknij symbol "x" obok nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="d14f7-138">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="d14f7-139">Aby zakończyć działanie programu Visual Studio Code, **Plik -> Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="d14f7-139">To exit Visual Studio Code, **File->Exit**.</span></span>

#### <a name="using-a-specific-installed-version-of-powershell"></a><span data-ttu-id="d14f7-140">Przy użyciu określonych zainstalowanej wersji programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="d14f7-140">Using a specific installed version of PowerShell</span></span>

<span data-ttu-id="d14f7-141">Jeśli użytkownik chce określoną instalacją programu PowerShell za pomocą programu Visual Studio Code, należy dodać nową zmienną do pliku ustawień użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d14f7-141">If you wish to use a specific installation of PowerShell with Visual Studio Code, you need to add a new variable to your user settings file.</span></span>

1. <span data-ttu-id="d14f7-142">Kliknij przycisk **Plik -> Preferencje -> Ustawienia**</span><span class="sxs-lookup"><span data-stu-id="d14f7-142">Click **File -> Preferences -> Settings**</span></span>
1. <span data-ttu-id="d14f7-143">Są wyświetlane dwa okienka edytora.</span><span class="sxs-lookup"><span data-stu-id="d14f7-143">Two editor panes appear.</span></span>
   <span data-ttu-id="d14f7-144">W okienku najdalej z prawej strony (`settings.json`), wstawić ustawienie poniżej odpowiednie dla Twojego systemu operacyjnego gdzieś między dwoma nawiasów klamrowych (`{` i `}`) i Zastąp **\<wersji\>** z zainstalowaną wersją programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d14f7-144">In the right-most pane (`settings.json`), insert the setting below appropriate for your OS somewhere between the two curly brackets (`{` and `}`) and replace **\<version\>** with the installed PowerShell version:</span></span>

   ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
   ```

1. <span data-ttu-id="d14f7-145">Zastąp ustawienia ścieżki do żądanego pliku wykonywalnego programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="d14f7-145">Replace the setting with the path to the desired PowerShell executable</span></span>
1. <span data-ttu-id="d14f7-146">Zapisz plik ustawień i ponownie uruchom Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="d14f7-146">Save the settings file and restart Visual Studio Code</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="d14f7-147">Ustawienia konfiguracji dla programu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="d14f7-147">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="d14f7-148">Wykonując kroki opisane w poprzednim akapicie można dodać ustawień konfiguracji w `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="d14f7-148">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="d14f7-149">Zalecamy następujące ustawienia konfiguracji dla programu Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="d14f7-149">We recommend the following configuration settings for Visual Studio Code:</span></span>

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="d14f7-150">Debugowanie za pomocą programu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="d14f7-150">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="d14f7-151">Obszar roboczy bez debugowania</span><span class="sxs-lookup"><span data-stu-id="d14f7-151">No-workspace debugging</span></span>

<span data-ttu-id="d14f7-152">Począwszy od wersji programu Visual Studio Code 1.9 można debugować skrypty programu PowerShell, bez konieczności otwierania folderu zawierającego skrypt programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d14f7-152">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span>
<span data-ttu-id="d14f7-153">Po prostu otwórz pliku skryptu programu PowerShell, za pomocą **Plik -> Otwórz plik...** , ustaw punkt przerwania w wierszu (naciśnij klawisz F9), a następnie naciśnij klawisz F5, aby rozpocząć debugowanie.</span><span class="sxs-lookup"><span data-stu-id="d14f7-153">Simply open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span>
<span data-ttu-id="d14f7-154">Powinien zostać wyświetlony w okienku Akcje debugowania są wyświetlane, co pozwala na przerwanie w debugerze, krok, wznowienie i zatrzymać debugowanie.</span><span class="sxs-lookup"><span data-stu-id="d14f7-154">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="d14f7-155">Debugowanie obszaru roboczego</span><span class="sxs-lookup"><span data-stu-id="d14f7-155">Workspace debugging</span></span>

<span data-ttu-id="d14f7-156">Obszar roboczy profilowanie odnosi się do debugowania w kontekście folder, który został otwarty w programie Visual Studio Code przy użyciu **Otwórz Folder...**  z **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="d14f7-156">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="d14f7-157">Folder, który można otworzyć, jest zazwyczaj do folderu projektu programu PowerShell i/lub w katalogu głównym repozytorium Git.</span><span class="sxs-lookup"><span data-stu-id="d14f7-157">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="d14f7-158">Nawet w tym trybie można uruchomić debugowania aktualnie zaznaczonego skryptu programu PowerShell, po prostu naciskając klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="d14f7-158">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="d14f7-159">Jednakże debugowanie obszaru roboczego umożliwia definiowanie wielu konfiguracji debugowania innych niż po prostu debugowania aktualnie otwarty plik.</span><span class="sxs-lookup"><span data-stu-id="d14f7-159">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="d14f7-160">Na przykład można dodać konfiguracji do:</span><span class="sxs-lookup"><span data-stu-id="d14f7-160">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="d14f7-161">Uruchom testy usług Pester w debugerze</span><span class="sxs-lookup"><span data-stu-id="d14f7-161">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="d14f7-162">Uruchom określony plik z argumentami w debugerze</span><span class="sxs-lookup"><span data-stu-id="d14f7-162">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="d14f7-163">Uruchomienie interaktywnej sesji w debugerze</span><span class="sxs-lookup"><span data-stu-id="d14f7-163">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="d14f7-164">Dołącz debuger do procesu hosta programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="d14f7-164">Attach the debugger to a PowerShell host process</span></span>

  <span data-ttu-id="d14f7-165">Wykonaj następujące kroki, aby utworzyć plik konfiguracji debugowania:</span><span class="sxs-lookup"><span data-stu-id="d14f7-165">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="d14f7-166">Otwórz **debugowania** widoku, naciskając klawisz **Ctrl + Shift + D** (**Cmd + Shift + D** na komputerze Mac).</span><span class="sxs-lookup"><span data-stu-id="d14f7-166">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
  2. <span data-ttu-id="d14f7-167">Naciśnij klawisz **Konfiguruj** ikonę koła zębatego w pasku narzędzi.</span><span class="sxs-lookup"><span data-stu-id="d14f7-167">Press the **Configure** gear icon in the toolbar.</span></span>
  3. <span data-ttu-id="d14f7-168">Visual Studio Code wyświetli monit o **wybierz środowisko**.</span><span class="sxs-lookup"><span data-stu-id="d14f7-168">Visual Studio Code prompts you to **Select Environment**.</span></span>
  <span data-ttu-id="d14f7-169">Wybierz **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="d14f7-169">Choose **PowerShell**.</span></span>

  <span data-ttu-id="d14f7-170">Gdy to zrobisz, Visual Studio Code tworzy katalog i plik ".vscode\launch.json" w katalogu głównym folderu obszaru roboczego.</span><span class="sxs-lookup"><span data-stu-id="d14f7-170">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
  <span data-ttu-id="d14f7-171">Jest to, gdzie są przechowywane z konfiguracji debugowania.</span><span class="sxs-lookup"><span data-stu-id="d14f7-171">This is where your debug configuration is stored.</span></span> <span data-ttu-id="d14f7-172">Jeśli pliki znajdują się w repozytorium Git, zazwyczaj chcesz zatwierdzić pliku launch.json.</span><span class="sxs-lookup"><span data-stu-id="d14f7-172">If your files are in a Git repository, you typically want to commit the launch.json file.</span></span>
  <span data-ttu-id="d14f7-173">Zawartość pliku launch.json są:</span><span class="sxs-lookup"><span data-stu-id="d14f7-173">The contents of the launch.json file are:</span></span>

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

  <span data-ttu-id="d14f7-174">Reprezentuje typowe scenariusze debugowania.</span><span class="sxs-lookup"><span data-stu-id="d14f7-174">This represents the common debug scenarios.</span></span>
  <span data-ttu-id="d14f7-175">Jednak po otwarciu tego pliku w edytorze można zobaczyć **Dodawanie konfiguracji...**  przycisku.</span><span class="sxs-lookup"><span data-stu-id="d14f7-175">However, when you open this file in the editor, you see an **Add Configuration...** button.</span></span>
  <span data-ttu-id="d14f7-176">Można nacisnąć ten przycisk, aby dodać większą liczbę konfiguracji debugowania programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d14f7-176">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="d14f7-177">Jedna konfiguracja przydatna, aby dodać jest **programu PowerShell: Uruchom skryptu**.</span><span class="sxs-lookup"><span data-stu-id="d14f7-177">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
  <span data-ttu-id="d14f7-178">W przypadku tej konfiguracji można określić specjalny plik z argumentów opcjonalnych, które powinien zostać uruchomiony po każdym naciśnięciu klawisza F5 niezależnie od tego, plik, który jest aktualnie aktywne w edytorze.</span><span class="sxs-lookup"><span data-stu-id="d14f7-178">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

  <span data-ttu-id="d14f7-179">Gdy zostanie nawiązane z konfiguracji debugowania, możesz wybrać konfigurację, która ma być używany podczas sesji debugowania, wybierając jedną z listy rozwijanej w konfiguracji debugowania **debugowania** narzędzi widoku.</span><span class="sxs-lookup"><span data-stu-id="d14f7-179">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

  <span data-ttu-id="d14f7-180">Istnieje kilka blogi, które mogą być przydatne ułatwią Ci rozpoczęcie pracy przy użyciu rozszerzenia programu PowerShell dla programu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="d14f7-180">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code</span></span>

<span data-ttu-id="d14f7-181">Program Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="d14f7-181">Visual Studio Code:</span></span>

- <span data-ttu-id="d14f7-182">[Rozszerzenie programu PowerShell][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="d14f7-182">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="d14f7-183">[Twórz i Debuguj skrypty programu PowerShell w programie Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="d14f7-183">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="d14f7-184">[Wskazówki dotyczące kodu programu Visual Studio do debugowania][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="d14f7-184">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="d14f7-185">[Debugowanie programu PowerShell w programie Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="d14f7-185">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="d14f7-186">[Wprowadzenie do rozwoju środowiska PowerShell w programie Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="d14f7-186">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="d14f7-187">[Visual Studio Code edytowanie funkcje opracowywania programu PowerShell — część 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="d14f7-187">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="d14f7-188">[Visual Studio Code edytowanie funkcje opracowywania programu PowerShell — część 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="d14f7-188">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="d14f7-189">[Debugowanie skryptu programu PowerShell w programie Visual Studio Code — część 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="d14f7-189">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="d14f7-190">[Debugowanie skryptu programu PowerShell w programie Visual Studio Code — część 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="d14f7-190">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise-guide.md
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

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="d14f7-191">Rozszerzenie programu PowerShell dla programu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="d14f7-191">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="d14f7-192">Kod źródłowy rozszerzenia programu PowerShell można znaleźć na [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="d14f7-192">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>