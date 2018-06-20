---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: PowerShell.exe — pomoc wiersza polecenia
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 60b6a7e310821a4092b0972b7abbdae0e2d5f738
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952583"
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="d837c-103">PowerShell.exe Pomoc wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="d837c-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="d837c-104">Może być PowerShell.exe Uruchom sesję programu PowerShell z poziomu wiersza polecenia narzędzia do innego, takich jak Cmd.exe, lub użyć go w wierszu polecenia programu PowerShell, można uruchomić nowej sesji.</span><span class="sxs-lookup"><span data-stu-id="d837c-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="d837c-105">Aby dostosować sesji, należy użyć parametrów.</span><span class="sxs-lookup"><span data-stu-id="d837c-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="d837c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d837c-106">Syntax</span></span>

```syntax
PowerShell[.exe]
       [-Command { - | <script-block> [-args <arg-array>]
                     | <string> [<CommandParameters>] } ]
       [-EncodedCommand <Base64EncodedCommand>]
       [-ExecutionPolicy <ExecutionPolicy>]
       [-File <FilePath> [<Args>]]
       [-InputFormat {Text | XML}]
       [-Mta]
       [-NoExit]
       [-NoLogo]
       [-NonInteractive]
       [-NoProfile]
       [-OutputFormat {Text | XML}]
       [-PSConsoleFile <FilePath> | -Version <PowerShell version>]
       [-Sta]
       [-WindowStyle <style>]

PowerShell[.exe] -Help | -? | /?
```

## <a name="parameters"></a><span data-ttu-id="d837c-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="d837c-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="d837c-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="d837c-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="d837c-109">Akceptuje wersji algorytmem base-64 ciąg polecenia.</span><span class="sxs-lookup"><span data-stu-id="d837c-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="d837c-110">Użyj tego parametru, aby przesłać poleceń programu PowerShell, które wymagają złożonych znaków cudzysłowu lub nawiasy klamrowe.</span><span class="sxs-lookup"><span data-stu-id="d837c-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="d837c-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="d837c-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="d837c-112">Ustawia domyślne zasady wykonywania w bieżącej sesji i zapisze go w $env: PSExecutionPolicyPreference zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="d837c-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="d837c-113">Ten parametr nie powoduje zmiany zasad wykonywania programu PowerShell, który jest ustawiony w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="d837c-113">This parameter does not change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="d837c-114">Aby uzyskać informacje na temat zasad wykonywania programu PowerShell, łącznie z listą prawidłowych wartości zobacz [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="d837c-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="d837c-115">-Plik <FilePath> \[ <Parameters>]</span><span class="sxs-lookup"><span data-stu-id="d837c-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="d837c-116">Uruchamia określony skrypt w zakresie lokalnym ("kropka-powierzając jej ich konserwację"), dzięki czemu funkcje i zmienne, które tworzy skrypt są dostępne w bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="d837c-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="d837c-117">Wprowadź ścieżkę pliku skryptu i wszelkie parametry.</span><span class="sxs-lookup"><span data-stu-id="d837c-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="d837c-118">**Plik** musi być ostatnim parametrem w wierszu polecenia, ponieważ wszystkie znaki wpisany po **pliku** Nazwa parametru będą interpretowane jako ścieżkę pliku skryptu, a następnie Parametry skryptu i ich wartości.</span><span class="sxs-lookup"><span data-stu-id="d837c-118">**File** must be the last parameter in the command, because all characters typed after the **File** parameter name are interpreted as the script file path followed by the script parameters and their values.</span></span>

<span data-ttu-id="d837c-119">Parametry skryptu i wartości parametrów, może zawierać wartości **pliku** parametru.</span><span class="sxs-lookup"><span data-stu-id="d837c-119">You can include the parameters of a script, and parameter values, in the value of the **File** parameter.</span></span> <span data-ttu-id="d837c-120">Na przykład: `-File .\Get-Script.ps1 -Domain Central` należy pamiętać, że parametry przekazywane do skryptu są przekazywane jako literał ciągi (po interpretacji przez powłokę bieżącego).</span><span class="sxs-lookup"><span data-stu-id="d837c-120">For example: `-File .\Get-Script.ps1 -Domain Central` Note that parameters passed to the script are passed as literal strings (after interpretation by the current shell).</span></span>
<span data-ttu-id="d837c-121">Na przykład, jeśli są w cmd.exe i przekazać wartość zmiennej środowiskowej, można skorzystać składni cmd.exe: `powershell -File .\test.ps1 -Sample %windir%` zostały używać składni programu PowerShell, a następnie w tym przykładzie skrypt otrzyma literału "$env: windir", a nie wartość tego zmiennej środowiskowej: `powershell -File .\test.ps1 -Sample $env:windir`</span><span class="sxs-lookup"><span data-stu-id="d837c-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` If you were to use PowerShell syntax, then in this example your script would receive the literal "$env:windir" and not the value of that environmental variable: `powershell -File .\test.ps1 -Sample $env:windir`</span></span>

<span data-ttu-id="d837c-122">Zazwyczaj parametry przełącznika skryptu są włączone lub pominięty.</span><span class="sxs-lookup"><span data-stu-id="d837c-122">Typically, the switch parameters of a script are either included or omitted.</span></span> <span data-ttu-id="d837c-123">Na przykład następujące polecenie używa **wszystkie** parametr Get-Script.ps1 pliku skryptu: `-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="d837c-123">For example, the following command uses the **All** parameter of the Get-Script.ps1 script file: `-File .\Get-Script.ps1 -All`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="d837c-124">\-InputFormat {tekstu | XML}</span><span class="sxs-lookup"><span data-stu-id="d837c-124">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="d837c-125">Opisuje format danych wysyłanych do programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d837c-125">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="d837c-126">Prawidłowe wartości to "Text" (ciągi) lub "XML" (format serializacji CLIXML).</span><span class="sxs-lookup"><span data-stu-id="d837c-126">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="d837c-127">-Mta</span><span class="sxs-lookup"><span data-stu-id="d837c-127">-Mta</span></span>

<span data-ttu-id="d837c-128">Zostanie uruchomiony przy użyciu wielowątkowej programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d837c-128">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="d837c-129">Ten parametr jest wprowadzone w środowisku PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="d837c-129">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="d837c-130">W środowisku PowerShell 3.0 jednowątkowego apartamentu (STA) jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="d837c-130">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="d837c-131">W programie PowerShell 2.0 wielowątkowej (MTA) jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="d837c-131">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="d837c-132">-NoExit</span><span class="sxs-lookup"><span data-stu-id="d837c-132">-NoExit</span></span>

<span data-ttu-id="d837c-133">Nie istnieje po uruchomieniu polecenia uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="d837c-133">Does not exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="d837c-134">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="d837c-134">-NoLogo</span></span>

<span data-ttu-id="d837c-135">Ukrywa praw autorskich transparentu podczas uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="d837c-135">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="d837c-136">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="d837c-136">-NonInteractive</span></span>

<span data-ttu-id="d837c-137">Użytkownik nie widzi monitu interakcyjnego.</span><span class="sxs-lookup"><span data-stu-id="d837c-137">Does not present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="d837c-138">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="d837c-138">-NoProfile</span></span>

<span data-ttu-id="d837c-139">Nie załadować profilu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d837c-139">Does not load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="d837c-140">-OutputFormat {tekstu | XML}</span><span class="sxs-lookup"><span data-stu-id="d837c-140">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="d837c-141">Określa, jak dane wyjściowe programu PowerShell jest sformatowany.</span><span class="sxs-lookup"><span data-stu-id="d837c-141">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="d837c-142">Prawidłowe wartości to "Text" (ciągi) lub "XML" (format serializacji CLIXML).</span><span class="sxs-lookup"><span data-stu-id="d837c-142">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="d837c-143">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="d837c-143">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="d837c-144">Ładuje określony plik konsoli programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d837c-144">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="d837c-145">Wprowadź ścieżkę i nazwę pliku konsoli.</span><span class="sxs-lookup"><span data-stu-id="d837c-145">Enter the path and name of the console file.</span></span> <span data-ttu-id="d837c-146">Aby utworzyć plik konsoli, należy użyć [ `Export-Console` ](/powershell/module/Microsoft.PowerShell.Core/Export-Console) polecenia cmdlet programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d837c-146">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="d837c-147">-Sta</span><span class="sxs-lookup"><span data-stu-id="d837c-147">-Sta</span></span>

<span data-ttu-id="d837c-148">Zostanie uruchomiony przy użyciu jednowątkowego apartamentu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d837c-148">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="d837c-149">W środowisku PowerShell 3.0 jednowątkowego apartamentu (STA) jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="d837c-149">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="d837c-150">W programie PowerShell 2.0 wielowątkowej (MTA) jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="d837c-150">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="d837c-151">-Wersja <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="d837c-151">-Version <PowerShell Version></span></span>

<span data-ttu-id="d837c-152">Rozpoczyna się określona wersja środowiska PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d837c-152">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="d837c-153">Określonej wersji musi być zainstalowany w systemie.</span><span class="sxs-lookup"><span data-stu-id="d837c-153">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="d837c-154">Jeśli PowerShell 3.0 jest zainstalowany na komputerze, prawidłowe wartości to "w wersji 2.0" i "3.0".</span><span class="sxs-lookup"><span data-stu-id="d837c-154">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="d837c-155">Wartość domyślna to "3.0".</span><span class="sxs-lookup"><span data-stu-id="d837c-155">The default value is "3.0".</span></span>

<span data-ttu-id="d837c-156">Jeśli nie zainstalowano programu PowerShell 3.0, jedyną prawidłową wartością jest "2.0".</span><span class="sxs-lookup"><span data-stu-id="d837c-156">If PowerShell 3.0 is not installed, the only valid value is "2.0".</span></span> <span data-ttu-id="d837c-157">Inne wartości są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="d837c-157">Other values are ignored.</span></span>

<span data-ttu-id="d837c-158">Aby uzyskać więcej informacji, zobacz "[Instalowanie programu Windows PowerShell](../../setup/installing-windows-powershell.md)".</span><span class="sxs-lookup"><span data-stu-id="d837c-158">For more information, see "[Installing Windows PowerShell](../../setup/installing-windows-powershell.md)".</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="d837c-159">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="d837c-159">-WindowStyle <Window style></span></span>

<span data-ttu-id="d837c-160">Ustawia styl okna w sesji.</span><span class="sxs-lookup"><span data-stu-id="d837c-160">Sets the window style for the session.</span></span> <span data-ttu-id="d837c-161">Prawidłowe wartości to normalny, zminimalizowany, Maximized i Hidden.</span><span class="sxs-lookup"><span data-stu-id="d837c-161">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="d837c-162">— Polecenie</span><span class="sxs-lookup"><span data-stu-id="d837c-162">-Command</span></span>

<span data-ttu-id="d837c-163">Wykonuje podane polecenie (i wszelkie parametry) tak, jakby były wpisywane w wierszu polecenia programu PowerShell, a następnie kończy działanie, chyba że określony jest parametr NoExit.</span><span class="sxs-lookup"><span data-stu-id="d837c-163">Executes the specified commands (and any parameters) as though they were typed at the PowerShell command prompt, and then exits, unless the NoExit parameter is specified.</span></span>
<span data-ttu-id="d837c-164">Zasadniczo tekst po `-Command` są wysyłane w jednym wierszu polecenia środowiska PowerShell (to różni się od tego, jak `-File` obsługuje parametry wysyłane do skryptu).</span><span class="sxs-lookup"><span data-stu-id="d837c-164">Essentially, any text after `-Command` is sent as a single command line to PowerShell (this is different from how `-File` handles parameters sent to a script).</span></span>

<span data-ttu-id="d837c-165">Możliwe wartości polecenia "-", ciąg.</span><span class="sxs-lookup"><span data-stu-id="d837c-165">The value of Command can be "-", a string.</span></span> <span data-ttu-id="d837c-166">albo blok skryptu.</span><span class="sxs-lookup"><span data-stu-id="d837c-166">or a script block.</span></span> <span data-ttu-id="d837c-167">Jeśli ma wartość polecenia "-", tekst polecenia są odczytywane z standardowe dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="d837c-167">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="d837c-168">Bloki skryptu muszą być ujęte w nawiasy klamrowe ({}).</span><span class="sxs-lookup"><span data-stu-id="d837c-168">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="d837c-169">Blok skryptu można określić tylko wtedy, gdy uruchomiony PowerShell.exe w programie PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d837c-169">You can specify a script block only when running PowerShell.exe in PowerShell.</span></span> <span data-ttu-id="d837c-170">Zwrot wyników skryptu powłoki nadrzędnego jako zdeserializowany obiekty XML, a nie na żywo obiekty.</span><span class="sxs-lookup"><span data-stu-id="d837c-170">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="d837c-171">Jeśli wartość polecenia jest ciągiem, **polecenia** musi być ostatnim parametrem w wierszu polecenia, ponieważ znaków wpisane po poleceniu będą interpretowane jako argumenty wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="d837c-171">If the value of Command is a string, **Command** must be the last parameter in the command, because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="d837c-172">Aby zapisać ciąg, który uruchamia polecenie programu PowerShell, użyj formatu:</span><span class="sxs-lookup"><span data-stu-id="d837c-172">To write a string that runs a PowerShell command, use the format:</span></span>

```powershell
"& {<command>}"
```

<span data-ttu-id="d837c-173">gdzie znaki cudzysłowu wskazują ciągu i operator wywołania (&) powoduje, że polecenie do wykonania.</span><span class="sxs-lookup"><span data-stu-id="d837c-173">where the quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="d837c-174">-Help,-?, /?</span><span class="sxs-lookup"><span data-stu-id="d837c-174">-Help, -?, /?</span></span>

<span data-ttu-id="d837c-175">Pokazuje tego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="d837c-175">Shows this message.</span></span> <span data-ttu-id="d837c-176">Jeśli piszesz polecenia PowerShell.exe w programie PowerShell, dołączenie wartości parametrów polecenia łącznikiem (-), nie ukośnika (/).</span><span class="sxs-lookup"><span data-stu-id="d837c-176">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="d837c-177">Można użyć łącznika lub ukośnika w Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="d837c-177">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="d837c-178">Uwaga: W programie PowerShell 2.0, począwszy od niektóre programy, w konsoli środowiska Windows PowerShell LastExitCode 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="d837c-178">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="d837c-179">PRZYKŁADY</span><span class="sxs-lookup"><span data-stu-id="d837c-179">EXAMPLES</span></span>

```powershell
# Create a new PowerShell session and load a saved console file
PowerShell -PSConsoleFile sqlsnapin.psc1

# Create a new PowerShell V2 session with text input, XML output, and no logo
PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

# Execute a PowerShell Command in a session
PowerShell -Command "Get-EventLog -LogName security"

# Run a script block in a session
PowerShell -Command {Get-EventLog -LogName security}

# An alternate way to run a command in a new session
PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```