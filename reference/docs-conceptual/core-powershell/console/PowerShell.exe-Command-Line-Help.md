---
ms.date: 08/14/2018
keywords: polecenia cmdlet programu PowerShell
title: PowerShell.exe — pomoc wiersza polecenia
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: c7f35511e876e8e5189d8a2b949555603d43f731
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133848"
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="68166-103">Pomoc w wierszu polecenia PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="68166-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="68166-104">Można użyć PowerShell.exe do uruchomienia sesji programu PowerShell z wiersza polecenia z innego narzędzia, takiego jak Cmd.exe, lub użyć w wierszu polecenia programu PowerShell, aby rozpocząć nową sesję.</span><span class="sxs-lookup"><span data-stu-id="68166-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="68166-105">Parametry służą do dostosowywania sesji.</span><span class="sxs-lookup"><span data-stu-id="68166-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="68166-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="68166-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="68166-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="68166-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="68166-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="68166-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="68166-109">Akceptuje wersji algorytmem base-64 ciągu polecenia.</span><span class="sxs-lookup"><span data-stu-id="68166-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="68166-110">Użyj tego parametru, aby przesłać poleceń do programu PowerShell, które wymagają złożonych znaków cudzysłowu lub nawiasów klamrowych.</span><span class="sxs-lookup"><span data-stu-id="68166-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="68166-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="68166-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="68166-112">Domyślne zasady wykonywania dla bieżącej sesji i zapisuje je w $env: zmienna środowiskowa PSExecutionPolicyPreference.</span><span class="sxs-lookup"><span data-stu-id="68166-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="68166-113">Ten parametr nie powoduje zmiany zasad wykonywania programu PowerShell, który jest ustawiony w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="68166-113">This parameter doesn't change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="68166-114">Aby uzyskać informacje na temat zasad wykonywania programu PowerShell, łącznie z listą prawidłowych wartości, zobacz [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="68166-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="68166-115">-Pliku <FilePath> \[ <Parameters>]</span><span class="sxs-lookup"><span data-stu-id="68166-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="68166-116">Wykonuje określony skrypt w zakresie lokalnym ("dot Source"), dzięki czemu funkcje i zmienne, utworzonych przez skrypt są dostępne w bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="68166-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="68166-117">Wprowadź ścieżkę pliku skryptu oraz wszelkie parametry.</span><span class="sxs-lookup"><span data-stu-id="68166-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="68166-118">**Plik** musi być ostatnim parametrem w poleceniu.</span><span class="sxs-lookup"><span data-stu-id="68166-118">**File** must be the last parameter in the command.</span></span> <span data-ttu-id="68166-119">Wszystkie wartości po **— plik** parametru są interpretowane jako skrypt ścieżkę pliku i parametry przekazywane do tego skryptu.</span><span class="sxs-lookup"><span data-stu-id="68166-119">All values typed after the **-File** parameter are interpreted as the script file path and parameters passed to that script.</span></span>

<span data-ttu-id="68166-120">Parametry przekazane do skryptu są przekazywane jako ciąg literału (po interpretacja w bieżącej powłoce).</span><span class="sxs-lookup"><span data-stu-id="68166-120">Parameters passed to the script are passed as literal strings (after interpretation by the current shell).</span></span> <span data-ttu-id="68166-121">Na przykład, jeśli znajdują się w cmd.exe i mają być przekazywane wartości zmiennej środowiskowej, można użyć składni cmd.exe: `powershell -File .\test.ps1 -Sample %windir%` w tym przykładzie skrypt otrzymuje literału `$env:windir` , a nie wartość tej zmiennej środowiskowej: `powershell -File .\test.ps1 -Sample $env:windir`</span><span class="sxs-lookup"><span data-stu-id="68166-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` In this example, the script receives the literal string `$env:windir` and not the value of that environmental variable: `powershell -File .\test.ps1 -Sample $env:windir`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="68166-122">\-InputFormat {tekstu | XML}</span><span class="sxs-lookup"><span data-stu-id="68166-122">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="68166-123">Opisuje format danych wysyłanych do programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="68166-123">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="68166-124">Prawidłowe wartości to "Text" (ciągi tekstowe) lub "XML" (w formacie CLIXML serializacji).</span><span class="sxs-lookup"><span data-stu-id="68166-124">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="68166-125">-Mta</span><span class="sxs-lookup"><span data-stu-id="68166-125">-Mta</span></span>

<span data-ttu-id="68166-126">Uruchamia programu PowerShell przy użyciu modelu wielowątkowości.</span><span class="sxs-lookup"><span data-stu-id="68166-126">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="68166-127">Ten parametr został wprowadzony w środowisku PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="68166-127">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="68166-128">W środowisku PowerShell 3.0 apartamentem jednowątkowym (przedziale STA) jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="68166-128">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="68166-129">W programie PowerShell 2.0 wielowątkowej (MTA) jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="68166-129">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="68166-130">-NoExit</span><span class="sxs-lookup"><span data-stu-id="68166-130">-NoExit</span></span>

<span data-ttu-id="68166-131">Nie zakończyć działanie po uruchomieniu polecenia uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="68166-131">Doesn't exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="68166-132">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="68166-132">-NoLogo</span></span>

<span data-ttu-id="68166-133">Ukrywa praw autorskich transparentu podczas uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="68166-133">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="68166-134">-Nieinterakcyjnym</span><span class="sxs-lookup"><span data-stu-id="68166-134">-NonInteractive</span></span>

<span data-ttu-id="68166-135">Użytkownik nie widzi monitu interakcyjnego.</span><span class="sxs-lookup"><span data-stu-id="68166-135">Doesn't present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="68166-136">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="68166-136">-NoProfile</span></span>

<span data-ttu-id="68166-137">Nie jest ładowana profilu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="68166-137">Doesn't load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="68166-138">-OutputFormat {tekstu | XML}</span><span class="sxs-lookup"><span data-stu-id="68166-138">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="68166-139">Określa sposób formatowania danych wyjściowych za pomocą programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="68166-139">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="68166-140">Prawidłowe wartości to "Text" (ciągi tekstowe) lub "XML" (w formacie CLIXML serializacji).</span><span class="sxs-lookup"><span data-stu-id="68166-140">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="68166-141">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="68166-141">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="68166-142">Ładuje określony plik konsoli programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="68166-142">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="68166-143">Wprowadź ścieżkę i nazwę pliku konsoli.</span><span class="sxs-lookup"><span data-stu-id="68166-143">Enter the path and name of the console file.</span></span> <span data-ttu-id="68166-144">Aby utworzyć plik konsoli, należy użyć [ `Export-Console` ](/powershell/module/Microsoft.PowerShell.Core/Export-Console) polecenia cmdlet programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="68166-144">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="68166-145">-STA.</span><span class="sxs-lookup"><span data-stu-id="68166-145">-Sta</span></span>

<span data-ttu-id="68166-146">Uruchamia programu PowerShell przy użyciu apartamentem jednowątkowym.</span><span class="sxs-lookup"><span data-stu-id="68166-146">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="68166-147">W środowisku PowerShell 3.0 apartamentem jednowątkowym (przedziale STA) jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="68166-147">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="68166-148">W programie PowerShell 2.0 wielowątkowej (MTA) jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="68166-148">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="68166-149">-Version <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="68166-149">-Version <PowerShell Version></span></span>

<span data-ttu-id="68166-150">Rozpoczyna się określonej wersji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="68166-150">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="68166-151">Określonej wersji musi być zainstalowany w systemie.</span><span class="sxs-lookup"><span data-stu-id="68166-151">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="68166-152">Jeśli program PowerShell 3.0 jest zainstalowana na komputerze, prawidłowe wartości to "2.0" i "3.0".</span><span class="sxs-lookup"><span data-stu-id="68166-152">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="68166-153">Wartość domyślna to "3.0".</span><span class="sxs-lookup"><span data-stu-id="68166-153">The default value is "3.0".</span></span>

<span data-ttu-id="68166-154">Jeśli program PowerShell 3.0 nie jest zainstalowany, jedyna prawidłowa wartość to "w wersji 2.0".</span><span class="sxs-lookup"><span data-stu-id="68166-154">If PowerShell 3.0 isn't installed, the only valid value is "2.0".</span></span> <span data-ttu-id="68166-155">Inne wartości są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="68166-155">Other values are ignored.</span></span>

<span data-ttu-id="68166-156">Aby uzyskać więcej informacji, zobacz [Instalowanie programu Windows PowerShell](../../setup/installing-windows-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="68166-156">For more information, see [Installing Windows PowerShell](../../setup/installing-windows-powershell.md).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="68166-157">-Nazwa_okna <Window style></span><span class="sxs-lookup"><span data-stu-id="68166-157">-WindowStyle <Window style></span></span>

<span data-ttu-id="68166-158">Ustawia styl okna sesji.</span><span class="sxs-lookup"><span data-stu-id="68166-158">Sets the window style for the session.</span></span> <span data-ttu-id="68166-159">Prawidłowe wartości to: Normalny, zminimalizowany, Maximized i ukryty.</span><span class="sxs-lookup"><span data-stu-id="68166-159">Valid values are Normal, Minimized, Maximized, and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="68166-160">— Polecenie</span><span class="sxs-lookup"><span data-stu-id="68166-160">-Command</span></span>

<span data-ttu-id="68166-161">Wykonuje określoną polecenia (przy użyciu żadnych parametrów), tak, jakby były one użyte w wierszu polecenia programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="68166-161">Executes the specified commands (with any parameters) as though they were typed at the PowerShell command prompt.</span></span> <span data-ttu-id="68166-162">Po wykonaniu PowerShell kończy działanie, chyba że `-NoExit` określono parametr.</span><span class="sxs-lookup"><span data-stu-id="68166-162">After execution, PowerShell exits unless the `-NoExit` parameter is specified.</span></span>
<span data-ttu-id="68166-163">Dowolny tekst po `-Command` jest wysyłany jako jeden wiersz polecenia dla programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="68166-163">Any text after `-Command` is sent as a single command line to PowerShell.</span></span> <span data-ttu-id="68166-164">To różni się od tego, jak `-File` obsługuje parametry wysłane do skryptu.</span><span class="sxs-lookup"><span data-stu-id="68166-164">This is different from how `-File` handles parameters sent to a script.</span></span>

<span data-ttu-id="68166-165">Wartość polecenia może być "-", ciąg.</span><span class="sxs-lookup"><span data-stu-id="68166-165">The value of Command can be "-", a string.</span></span> <span data-ttu-id="68166-166">lub blok skryptu.</span><span class="sxs-lookup"><span data-stu-id="68166-166">or a script block.</span></span> <span data-ttu-id="68166-167">Jeśli ma wartość polecenia "-", tekst polecenia jest do odczytu ze standardowego wejścia.</span><span class="sxs-lookup"><span data-stu-id="68166-167">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="68166-168">Bloki skryptu muszą być ujęte w nawiasy klamrowe ({}).</span><span class="sxs-lookup"><span data-stu-id="68166-168">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="68166-169">Blok skryptu można określić tylko wtedy, gdy uruchomiony PowerShell.exe w programie PowerShell.</span><span class="sxs-lookup"><span data-stu-id="68166-169">You can specify a script block only when running PowerShell.exe in PowerShell.</span></span> <span data-ttu-id="68166-170">Wyniki skryptu są zwracane do powłoki nadrzędnego jako po deserializacji obiektów XML, nie na żywo obiektów.</span><span class="sxs-lookup"><span data-stu-id="68166-170">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="68166-171">Jeśli wartość polecenia jest ciągiem, **polecenia** musi być ostatnim parametrem w wierszu polecenia, ponieważ wszystkie znaki wpisane po polecenia są interpretowane jako argumenty wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="68166-171">If the value of Command is a string, **Command** must be the last parameter in the command, because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="68166-172">Aby zapisać ciąg, który uruchamia polecenia programu PowerShell, użyj formatu:</span><span class="sxs-lookup"><span data-stu-id="68166-172">To write a string that runs a PowerShell command, use the format:</span></span>

```powershell
"& {<command>}"
```

<span data-ttu-id="68166-173">Znaki cudzysłowu wskazują ciągu i invoke operator (&) powoduje, że polecenie do wykonania.</span><span class="sxs-lookup"><span data-stu-id="68166-173">The quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="68166-174">-Help,-?, /?</span><span class="sxs-lookup"><span data-stu-id="68166-174">-Help, -?, /?</span></span>

<span data-ttu-id="68166-175">Przedstawia składnię powershell.exe.</span><span class="sxs-lookup"><span data-stu-id="68166-175">Shows the syntax of powershell.exe.</span></span> <span data-ttu-id="68166-176">Jeśli piszesz polecenia PowerShell.exe w programie PowerShell, należy poprzedzić parametry polecenia łącznikiem (-), nie ukośnika (/).</span><span class="sxs-lookup"><span data-stu-id="68166-176">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="68166-177">Można użyć łącznika lub ukośnikiem w Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="68166-177">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="68166-178">Uwaga dotycząca rozwiązywania problemów: W programie PowerShell 2.0, począwszy od niektóre programy w programie Windows PowerShell, konsola nie LastExitCode 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="68166-178">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="68166-179">PRZYKŁADY</span><span class="sxs-lookup"><span data-stu-id="68166-179">EXAMPLES</span></span>

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
