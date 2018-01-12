# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="98592-101">Przy użyciu kodu programu Visual Studio do tworzenia środowiska PowerShell</span><span class="sxs-lookup"><span data-stu-id="98592-101">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="98592-102">Oprócz [PowerShell ISE][ise], programu PowerShell jest również powszechnie obsługiwanych w programie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="98592-102">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="98592-103">Ponadto ISE nie jest obsługiwane podstawowych programu PowerShell, podczas Visual Studio Code jest obsługiwana dla środowiska PowerShell rdzeni na wszystkich platformach (z systemem Windows, system macOS i Linux)</span><span class="sxs-lookup"><span data-stu-id="98592-103">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="98592-104">Możesz użyć programu Visual Studio Code w systemie Windows przy użyciu programu PowerShell w wersji 5 przy użyciu systemu Windows 10 lub instalując [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) dla niskiego poziomu OSs systemu Windows (Windows 8.1, itp.).</span><span class="sxs-lookup"><span data-stu-id="98592-104">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="98592-105">Przed uruchomieniem go, upewnij się, że programu PowerShell znajduje się w tym systemie.</span><span class="sxs-lookup"><span data-stu-id="98592-105">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="98592-106">W przypadku nowoczesnych obciążeń w systemie Windows macOS i Linux, zobacz:</span><span class="sxs-lookup"><span data-stu-id="98592-106">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="98592-107">[Instalowanie programu PowerShell Core na macOS i Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="98592-107">[Installing PowerShell Core on macOS and Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="98592-108">[Instalowanie programu PowerShell Core w systemie Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="98592-108">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="98592-109">Dla tradycyjnych obciążeń programu Windows PowerShell, zobacz [Instalowanie programu Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="98592-109">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="98592-110">Edytowanie kodu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="98592-110">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="98592-111">1. Instalowanie programu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="98592-111">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="98592-112">**Linux**: postępuj zgodnie z instrukcjami instalacji [uruchomić kod programu VS w systemie Linux](https://code.visualstudio.com/docs/setup/linux) strony</span><span class="sxs-lookup"><span data-stu-id="98592-112">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="98592-113">**System macOS**: postępuj zgodnie z instrukcjami instalacji [uruchomić kod VS na macOS](https://code.visualstudio.com/docs/setup/mac) strony</span><span class="sxs-lookup"><span data-stu-id="98592-113">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

> [!IMPORTANT]
> <span data-ttu-id="98592-114">Na macOS należy zainstalować biblioteki OpenSSL rozszerzenia programu PowerShell, aby działać poprawnie.</span><span class="sxs-lookup"><span data-stu-id="98592-114">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
> <span data-ttu-id="98592-115">Najprostszym sposobem, w tym celu jest zainstalowanie [Homebrew](http://brew.sh/) , a następnie uruchom `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="98592-115">The easiest way to accomplish this is to install [Homebrew](http://brew.sh/) and then run `brew install openssl`.</span></span>
> <span data-ttu-id="98592-116">Teraz będzie można pomyślnie załadować rozszerzenia programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="98592-116">The PowerShell extension will now be able to load successfully.</span></span>

- <span data-ttu-id="98592-117">**Windows**: postępuj zgodnie z instrukcjami instalacji [uruchomić kod programu VS w systemie Windows](https://code.visualstudio.com/docs/setup/windows) strony</span><span class="sxs-lookup"><span data-stu-id="98592-117">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="98592-118">2. Instalowanie rozszerzenia programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="98592-118">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="98592-119">Uruchom program Visual Studio Code aplikacji przez:</span><span class="sxs-lookup"><span data-stu-id="98592-119">Launch the Visual Studio Code app by:</span></span>
    - <span data-ttu-id="98592-120">**Windows**: wpisywanie `code` w sesji programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="98592-120">**Windows**: typing `code` in your PowerShell session</span></span>
    - <span data-ttu-id="98592-121">**Linux**: wpisywanie `code` w terminalu</span><span class="sxs-lookup"><span data-stu-id="98592-121">**Linux**: typing `code` in your terminal</span></span>
    - <span data-ttu-id="98592-122">**System macOS**: wpisywanie `code` w terminalu</span><span class="sxs-lookup"><span data-stu-id="98592-122">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="98592-123">Uruchom **szybkie Otwórz** naciskając **Ctrl + P** (**Cmd + P** dla komputerów Mac).</span><span class="sxs-lookup"><span data-stu-id="98592-123">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="98592-124">W polu Szybkie Otwórz wpisz `ext install powershell` i trafień **Enter**.</span><span class="sxs-lookup"><span data-stu-id="98592-124">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="98592-125">**Rozszerzenia** widok zostanie otwarty na pasku bocznym.</span><span class="sxs-lookup"><span data-stu-id="98592-125">The **Extensions** view will open on the Side Bar.</span></span> <span data-ttu-id="98592-126">Wybierz rozszerzenia programu PowerShell firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="98592-126">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="98592-127">Powinny pojawić się dane, takich jak poniżej:</span><span class="sxs-lookup"><span data-stu-id="98592-127">You will see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="98592-129">Kliknij przycisk **zainstalować** przycisk rozszerzenia programu PowerShell firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="98592-129">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="98592-130">Po zakończeniu instalacji, zobaczysz **zainstalować** przycisk przechodzi w **Załaduj ponownie**.</span><span class="sxs-lookup"><span data-stu-id="98592-130">After the install, you will see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="98592-131">Polecenie **Załaduj ponownie**.</span><span class="sxs-lookup"><span data-stu-id="98592-131">Click on **Reload**.</span></span>
- <span data-ttu-id="98592-132">Visual Studio Code po Załaduj ponownie, możesz przystąpić do edycji.</span><span class="sxs-lookup"><span data-stu-id="98592-132">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="98592-133">Na przykład, aby utworzyć nowy plik, kliknij przycisk **Plik -> New**.</span><span class="sxs-lookup"><span data-stu-id="98592-133">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="98592-134">Aby zapisać je, kliknij przycisk **Plik -> Zapisz** , a następnie wprowadź nazwę pliku, teraz załóżmy `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="98592-134">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="98592-135">Aby zamknąć plik, kliknij pozycję "x" obok nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="98592-135">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="98592-136">Aby zakończyć działanie programu Visual Studio Code, **Plik -> Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="98592-136">To exit Visual Studio Code, **File->Exit**.</span></span>

#### <a name="using-a-specific-installed-version-of-powershell"></a><span data-ttu-id="98592-137">Przy użyciu określonych zainstalowana wersja programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="98592-137">Using a specific installed version of PowerShell</span></span>

<span data-ttu-id="98592-138">Jeśli chcesz używać określonego instalacji programu PowerShell z kodem Visual Studio, należy dodać nową zmienną do pliku ustawień użytkownika.</span><span class="sxs-lookup"><span data-stu-id="98592-138">If you wish to use a specific installation of PowerShell with Visual Studio Code, you will need to add a new variable to your user settings file.</span></span>

1. <span data-ttu-id="98592-139">Kliknij przycisk **Plik -> Preferencje -> Ustawienia**</span><span class="sxs-lookup"><span data-stu-id="98592-139">Click **File -> Preferences -> Settings**</span></span>
1. <span data-ttu-id="98592-140">Pojawi się dwie części edytora.</span><span class="sxs-lookup"><span data-stu-id="98592-140">Two editor panes will appear.</span></span>
   <span data-ttu-id="98592-141">W okienku prawej krawędzi (`settings.json`), włóż do poniższych ustawień odpowiedni dla Twojego systemu operacyjnego między dwoma nawiasów klamrowych (`{` i `}`) i Zastąp  *<version>*  z zainstalowana Wersja programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="98592-141">In the right-most pane (`settings.json`), insert the setting below appropriate for your OS somewhere between the two curly brackets (`{` and `}`) and replace *<version>* with the installed PowerShell version:</span></span>

  ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
  ```
1. <span data-ttu-id="98592-142">Zastąp ustawienia ścieżka do żądanego pliku wykonywalnego programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="98592-142">Replace the setting with the path to the desired PowerShell executable</span></span>
1. <span data-ttu-id="98592-143">Zapisz plik ustawień i ponownie uruchom Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="98592-143">Save the settings file and restart Visual Studio Code</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="98592-144">Ustawienia konfiguracji dla programu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="98592-144">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="98592-145">Wykonując kroki opisane w poprzednim akapicie można dodać ustawienia konfiguracji w `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="98592-145">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="98592-146">Zaleca się następujące ustawienia konfiguracji dla programu Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="98592-146">We recommend the following configuration settings for Visual Studio Code:</span></span>

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="98592-147">Profilowanie kodu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="98592-147">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="98592-148">Obszar roboczy bez debugowania</span><span class="sxs-lookup"><span data-stu-id="98592-148">No-workspace debugging</span></span>

<span data-ttu-id="98592-149">Począwszy od wersji programu Visual Studio Code 1.9 można debugować skryptów programu PowerShell bez konieczności otwierania folder zawierający skrypt programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="98592-149">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span>
<span data-ttu-id="98592-150">Po prostu otwórz plik skryptu programu PowerShell z **Plik -> Otwórz plik...** , ustaw punkt przerwania w wierszu (naciśnij klawisz F9), a następnie naciśnij klawisz F5, aby rozpocząć debugowania.</span><span class="sxs-lookup"><span data-stu-id="98592-150">Simply open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span>
<span data-ttu-id="98592-151">Zostanie wyświetlony w okienku Akcje debugowania są wyświetlane, co pozwala podzielić debugera, krok, wznowienie i zatrzymanie debugowania.</span><span class="sxs-lookup"><span data-stu-id="98592-151">You will see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="98592-152">Debugowanie obszaru roboczego</span><span class="sxs-lookup"><span data-stu-id="98592-152">Workspace debugging</span></span>

<span data-ttu-id="98592-153">Obszar roboczy debugowania odwołuje się do debugowania w kontekście folderu, który został otwarty w programie Visual Studio Code przy użyciu **Otwórz Folder...**  z **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="98592-153">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="98592-154">Folder, który można otworzyć jest zwykle folderu projektu programu PowerShell i/lub katalogu głównego repozytorium Git.</span><span class="sxs-lookup"><span data-stu-id="98592-154">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="98592-155">Nawet w tym trybie można uruchomić debugowania aktualnie zaznaczonego skryptu PowerShell po prostu naciskając klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="98592-155">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="98592-156">Jednak debugowania obszaru roboczego można zdefiniować wiele konfiguracji debugowania, niż tylko debugowanie aktualnie otwarty plik.</span><span class="sxs-lookup"><span data-stu-id="98592-156">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="98592-157">Na przykład można dodać konfiguracji, aby:</span><span class="sxs-lookup"><span data-stu-id="98592-157">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="98592-158">Uruchom testy Pester w debugerze</span><span class="sxs-lookup"><span data-stu-id="98592-158">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="98592-159">Uruchom określony plik z argumentami w debugerze</span><span class="sxs-lookup"><span data-stu-id="98592-159">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="98592-160">Uruchamianie sesji interaktywnej w debugerze</span><span class="sxs-lookup"><span data-stu-id="98592-160">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="98592-161">Dołącz debuger do procesu hosta programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="98592-161">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="98592-162">Wykonaj następujące kroki, aby utworzyć plik konfiguracji debugowania:</span><span class="sxs-lookup"><span data-stu-id="98592-162">Follow these steps to create your debug configuration file:</span></span>

1. <span data-ttu-id="98592-163">Otwórz **debugowania** widoku naciskając **Ctrl + Shift + D** (**Cmd + Shift + D** dla komputerów Mac).</span><span class="sxs-lookup"><span data-stu-id="98592-163">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
1. <span data-ttu-id="98592-164">Naciśnij klawisz **Konfiguruj** koło zębate ikonę na pasku narzędzi.</span><span class="sxs-lookup"><span data-stu-id="98592-164">Press the **Configure** gear icon in the toolbar.</span></span>
1. <span data-ttu-id="98592-165">Visual Studio Code spowoduje wyświetlenie monitu o **wybierz środowisko**.</span><span class="sxs-lookup"><span data-stu-id="98592-165">Visual Studio Code will prompt you to **Select Environment**.</span></span>
   <span data-ttu-id="98592-166">Wybierz **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="98592-166">Choose **PowerShell**.</span></span>

   <span data-ttu-id="98592-167">Gdy to zrobisz, Visual Studio Code tworzy katalog i plik ".vscode\launch.json" w katalogu głównym folderu roboczego.</span><span class="sxs-lookup"><span data-stu-id="98592-167">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
   <span data-ttu-id="98592-168">Jest to przechowywania konfiguracji debugowania.</span><span class="sxs-lookup"><span data-stu-id="98592-168">This is where your debug configuration is stored.</span></span> <span data-ttu-id="98592-169">Jeśli pliki znajdują się w repozytorium Git, zwykle można przekazać plik launch.json.</span><span class="sxs-lookup"><span data-stu-id="98592-169">If your files are in a Git repository, you will typically want to commit the launch.json file.</span></span>
   <span data-ttu-id="98592-170">Zawartość pliku launch.json są:</span><span class="sxs-lookup"><span data-stu-id="98592-170">The contents of the launch.json file are:</span></span>

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

<span data-ttu-id="98592-171">Reprezentuje typowe scenariusze debugowania.</span><span class="sxs-lookup"><span data-stu-id="98592-171">This represents the common debug scenarios.</span></span>
<span data-ttu-id="98592-172">Jednak po otwarciu tego pliku w edytorze, zobaczysz **Dodawanie konfiguracji...**  przycisku.</span><span class="sxs-lookup"><span data-stu-id="98592-172">However, when you open this file in the editor, you will see an **Add Configuration...** button.</span></span>
<span data-ttu-id="98592-173">Można nacisnąć przycisk, aby dodać więcej konfiguracji debugowania programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="98592-173">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="98592-174">Jest jedną konfigurację przydatną, aby dodać **środowiska PowerShell: uruchamianie skryptu**.</span><span class="sxs-lookup"><span data-stu-id="98592-174">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
<span data-ttu-id="98592-175">W tej konfiguracji można określić specjalny plik z argumentów opcjonalnych, które można uruchomić przy każdym naciśnięciu klawisza F5 niezależnie od tego, który plik jest aktualnie aktywne w edytorze.</span><span class="sxs-lookup"><span data-stu-id="98592-175">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

<span data-ttu-id="98592-176">Po ustanowieniu z konfiguracji debugowania, można wybrać konfigurację, która ma być używany podczas sesji debugowania, wybierając jedną z listy rozwijanej w konfiguracji debugowania **debugowania** narzędzi widoku.</span><span class="sxs-lookup"><span data-stu-id="98592-176">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="98592-177">Istnieje kilka blogów, które mogą być pomocne ułatwiających rozpoczęcie pracy przy użyciu rozszerzenia programu PowerShell dla programu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="98592-177">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code</span></span>

- <span data-ttu-id="98592-178">Kod Visual Studio: [rozszerzenia programu PowerShell][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="98592-178">Visual Studio Code: [PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="98592-179">[Zapis i debugowania skryptów programu PowerShell w programie Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="98592-179">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="98592-180">[Debugowanie wskazówki kodu programu Visual Studio][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="98592-180">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="98592-181">[Debugowanie programu PowerShell w programie Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="98592-181">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="98592-182">[Wprowadzenie do rozwoju programu PowerShell w programie Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="98592-182">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="98592-183">[Visual Studio Code edycji funkcje do tworzenia aplikacji programu PowerShell — część 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="98592-183">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="98592-184">[Visual Studio Code edycji funkcje do tworzenia aplikacji programu PowerShell — część 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="98592-184">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="98592-185">[Debugowanie skryptów programu PowerShell w programie Visual Studio Code — część 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="98592-185">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="98592-186">[Debugowanie skryptów programu PowerShell w programie Visual Studio Code — część 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="98592-186">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise-guide.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-macOS-and-Linux.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]:https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]:https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]:https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]:https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]:https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="98592-187">Rozszerzenie programu PowerShell dla programu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="98592-187">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="98592-188">Kod źródłowy rozszerzenia programu PowerShell można znaleźć w [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="98592-188">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
