---
ms.date: 08/14/2018
keywords: polecenia cmdlet programu PowerShell
title: PowerShell.exe — pomoc wiersza polecenia
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 0a11ebb11d29adf5853c232b3aa10bc72f92bf0c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688826"
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="22724-103">Pomoc w wierszu polecenia PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="22724-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="22724-104">Można użyć PowerShell.exe do uruchomienia sesji programu PowerShell z wiersza polecenia z innego narzędzia, takiego jak Cmd.exe, lub użyć w wierszu polecenia programu PowerShell, aby rozpocząć nową sesję.</span><span class="sxs-lookup"><span data-stu-id="22724-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="22724-105">Parametry służą do dostosowywania sesji.</span><span class="sxs-lookup"><span data-stu-id="22724-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="22724-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="22724-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="22724-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="22724-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="22724-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="22724-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="22724-109">Akceptuje wersji algorytmem base-64 ciągu polecenia.</span><span class="sxs-lookup"><span data-stu-id="22724-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="22724-110">Użyj tego parametru, aby przesłać poleceń do programu PowerShell, które wymagają złożonych znaków cudzysłowu lub nawiasów klamrowych.</span><span class="sxs-lookup"><span data-stu-id="22724-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="22724-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="22724-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="22724-112">Domyślne zasady wykonywania dla bieżącej sesji i zapisuje je w $env: zmienna środowiskowa PSExecutionPolicyPreference.</span><span class="sxs-lookup"><span data-stu-id="22724-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="22724-113">Ten parametr nie powoduje zmiany zasad wykonywania programu PowerShell, który jest ustawiony w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="22724-113">This parameter doesn't change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="22724-114">Aby uzyskać informacje na temat zasad wykonywania programu PowerShell, łącznie z listą prawidłowych wartości, zobacz [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="22724-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="22724-115">-Pliku <FilePath> \[ <Parameters>]</span><span class="sxs-lookup"><span data-stu-id="22724-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="22724-116">Wykonuje określony skrypt w zakresie lokalnym ("dot Source"), dzięki czemu funkcje i zmienne, utworzonych przez skrypt są dostępne w bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="22724-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="22724-117">Wprowadź ścieżkę pliku skryptu oraz wszelkie parametry.</span><span class="sxs-lookup"><span data-stu-id="22724-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="22724-118">**Plik** musi być ostatnim parametrem w poleceniu.</span><span class="sxs-lookup"><span data-stu-id="22724-118">**File** must be the last parameter in the command.</span></span> <span data-ttu-id="22724-119">Wszystkie wartości po **— plik** parametru są interpretowane jako skrypt ścieżkę pliku i parametry przekazywane do tego skryptu.</span><span class="sxs-lookup"><span data-stu-id="22724-119">All values typed after the **-File** parameter are interpreted as the script file path and parameters passed to that script.</span></span>

<span data-ttu-id="22724-120">Parametry przekazane do skryptu są przekazywane jako ciągi literałowe po interpretacji w bieżącej powłoce.</span><span class="sxs-lookup"><span data-stu-id="22724-120">Parameters passed to the script are passed as literal strings, after interpretation by the current shell.</span></span> <span data-ttu-id="22724-121">Na przykład jeśli znajdują się w cmd.exe i mają być przekazywane wartości zmiennej środowiskowej, użyj składni cmd.exe: `powershell.exe -File .\test.ps1 -TestParam %windir%`</span><span class="sxs-lookup"><span data-stu-id="22724-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell.exe -File .\test.ps1 -TestParam %windir%`</span></span>

<span data-ttu-id="22724-122">Natomiast uruchomione `powershell.exe -File .\test.ps1 -TestParam $env:windir` w wynikach cmd.exe w skrypcie odbiera literału ciągu `$env:windir` ponieważ go nie ma specjalnego znaczenia do bieżącej powłoce cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="22724-122">In contrast, running `powershell.exe -File .\test.ps1 -TestParam $env:windir` in cmd.exe results in the script receiving the literal string `$env:windir` because it has no special meaning to the current cmd.exe shell.</span></span>
<span data-ttu-id="22724-123">`$env:windir` Styl Odnośnik zmiennej środowiskowej _można_ można używać wewnątrz `-Command` parametru, ponieważ ma ona będzie interpretowany jako kod programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="22724-123">The `$env:windir` style of environment variable reference _can_ be used inside a `-Command` parameter, since there it will be interpreted as PowerShell code.</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="22724-124">\-InputFormat {tekstu | XML}</span><span class="sxs-lookup"><span data-stu-id="22724-124">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="22724-125">Opisuje format danych wysyłanych do programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="22724-125">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="22724-126">Prawidłowe wartości to "Text" (ciągi tekstowe) lub "XML" (w formacie CLIXML serializacji).</span><span class="sxs-lookup"><span data-stu-id="22724-126">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="22724-127">-Mta</span><span class="sxs-lookup"><span data-stu-id="22724-127">-Mta</span></span>

<span data-ttu-id="22724-128">Uruchamia programu PowerShell przy użyciu modelu wielowątkowości.</span><span class="sxs-lookup"><span data-stu-id="22724-128">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="22724-129">Ten parametr został wprowadzony w środowisku PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="22724-129">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="22724-130">W środowisku PowerShell 3.0 apartamentem jednowątkowym (przedziale STA) jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="22724-130">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="22724-131">W programie PowerShell 2.0 wielowątkowej (MTA) jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="22724-131">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="22724-132">-NoExit</span><span class="sxs-lookup"><span data-stu-id="22724-132">-NoExit</span></span>

<span data-ttu-id="22724-133">Nie zakończyć działanie po uruchomieniu polecenia uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="22724-133">Doesn't exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="22724-134">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="22724-134">-NoLogo</span></span>

<span data-ttu-id="22724-135">Ukrywa praw autorskich transparentu podczas uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="22724-135">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="22724-136">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="22724-136">-NonInteractive</span></span>

<span data-ttu-id="22724-137">Użytkownik nie widzi monitu interakcyjnego.</span><span class="sxs-lookup"><span data-stu-id="22724-137">Doesn't present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="22724-138">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="22724-138">-NoProfile</span></span>

<span data-ttu-id="22724-139">Nie jest ładowana profilu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="22724-139">Doesn't load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="22724-140">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="22724-140">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="22724-141">Określa sposób formatowania danych wyjściowych za pomocą programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="22724-141">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="22724-142">Prawidłowe wartości to "Text" (ciągi tekstowe) lub "XML" (w formacie CLIXML serializacji).</span><span class="sxs-lookup"><span data-stu-id="22724-142">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="22724-143">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="22724-143">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="22724-144">Ładuje określony plik konsoli programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="22724-144">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="22724-145">Wprowadź ścieżkę i nazwę pliku konsoli.</span><span class="sxs-lookup"><span data-stu-id="22724-145">Enter the path and name of the console file.</span></span> <span data-ttu-id="22724-146">Aby utworzyć plik konsoli, należy użyć [ `Export-Console` ](/powershell/module/Microsoft.PowerShell.Core/Export-Console) polecenia cmdlet programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="22724-146">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="22724-147">-Sta</span><span class="sxs-lookup"><span data-stu-id="22724-147">-Sta</span></span>

<span data-ttu-id="22724-148">Uruchamia programu PowerShell przy użyciu apartamentem jednowątkowym.</span><span class="sxs-lookup"><span data-stu-id="22724-148">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="22724-149">W środowisku PowerShell 3.0 apartamentem jednowątkowym (przedziale STA) jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="22724-149">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="22724-150">W programie PowerShell 2.0 wielowątkowej (MTA) jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="22724-150">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="22724-151">-Version <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="22724-151">-Version <PowerShell Version></span></span>

<span data-ttu-id="22724-152">Rozpoczyna się określonej wersji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="22724-152">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="22724-153">Określonej wersji musi być zainstalowany w systemie.</span><span class="sxs-lookup"><span data-stu-id="22724-153">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="22724-154">Jeśli program PowerShell 3.0 jest zainstalowana na komputerze, prawidłowe wartości to "2.0" i "3.0".</span><span class="sxs-lookup"><span data-stu-id="22724-154">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="22724-155">Wartość domyślna to "3.0".</span><span class="sxs-lookup"><span data-stu-id="22724-155">The default value is "3.0".</span></span>

<span data-ttu-id="22724-156">Jeśli program PowerShell 3.0 nie jest zainstalowany, jedyna prawidłowa wartość to "w wersji 2.0".</span><span class="sxs-lookup"><span data-stu-id="22724-156">If PowerShell 3.0 isn't installed, the only valid value is "2.0".</span></span> <span data-ttu-id="22724-157">Inne wartości są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="22724-157">Other values are ignored.</span></span>

<span data-ttu-id="22724-158">Aby uzyskać więcej informacji, zobacz [Instalowanie programu Windows PowerShell](../../setup/installing-windows-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="22724-158">For more information, see [Installing Windows PowerShell](../../setup/installing-windows-powershell.md).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="22724-159">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="22724-159">-WindowStyle <Window style></span></span>

<span data-ttu-id="22724-160">Ustawia styl okna sesji.</span><span class="sxs-lookup"><span data-stu-id="22724-160">Sets the window style for the session.</span></span> <span data-ttu-id="22724-161">Prawidłowe wartości to: Normalny, zminimalizowany, Maximized i ukryty.</span><span class="sxs-lookup"><span data-stu-id="22724-161">Valid values are Normal, Minimized, Maximized, and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="22724-162">— Polecenie</span><span class="sxs-lookup"><span data-stu-id="22724-162">-Command</span></span>

<span data-ttu-id="22724-163">Wykonuje określoną polecenia (przy użyciu żadnych parametrów), tak, jakby były one użyte w wierszu polecenia programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="22724-163">Executes the specified commands (with any parameters) as though they were typed at the PowerShell command prompt.</span></span>
<span data-ttu-id="22724-164">Po wykonaniu PowerShell kończy działanie, chyba że **NoExit** określono parametr.</span><span class="sxs-lookup"><span data-stu-id="22724-164">After execution, PowerShell exits unless the **NoExit** parameter is specified.</span></span>
<span data-ttu-id="22724-165">Dowolny tekst po `-Command` jest wysyłany jako jeden wiersz polecenia dla programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="22724-165">Any text after `-Command` is sent as a single command line to PowerShell.</span></span>
<span data-ttu-id="22724-166">To różni się od tego, jak `-File` obsługuje parametry wysłane do skryptu.</span><span class="sxs-lookup"><span data-stu-id="22724-166">This is different from how `-File` handles parameters sent to a script.</span></span>

<span data-ttu-id="22724-167">Wartość `-Command` może być "-", ciąg lub blok skryptu.</span><span class="sxs-lookup"><span data-stu-id="22724-167">The value of `-Command` can be "-", a string, or a script block.</span></span>
<span data-ttu-id="22724-168">Wyniki polecenia są zwracane do powłoki nadrzędnego jako po deserializacji obiektów XML, nie na żywo obiektów.</span><span class="sxs-lookup"><span data-stu-id="22724-168">The results of the command are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="22724-169">Jeśli wartość `-Command` jest "-", tekst polecenia jest do odczytu ze standardowego wejścia.</span><span class="sxs-lookup"><span data-stu-id="22724-169">If the value of `-Command` is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="22724-170">Gdy wartość `-Command` jest ciągiem, **polecenia** _musi_ być ostatnim parametrem określona, ponieważ wszystkie znaki wpisane po polecenia są interpretowane jako argumenty wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="22724-170">When the value of `-Command` is a string, **Command** _must_ be the last parameter specified because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="22724-171">**Polecenia** parametru akceptuje tylko blok skryptu do wykonania po jego rozpoznaje wartość przekazana do `-Command` jako typu blok skryptu.</span><span class="sxs-lookup"><span data-stu-id="22724-171">The **Command** parameter only accepts a script block for execution when it can recognize the value passed to `-Command` as a ScriptBlock type.</span></span>
<span data-ttu-id="22724-172">Jest to _tylko_ możliwe podczas uruchamiania PowerShell.exe z innego hosta programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="22724-172">This is _only_ possible when running PowerShell.exe from another PowerShell host.</span></span>
<span data-ttu-id="22724-173">ScriptBlock typu mogą być zawarte w istniejących zmiennych, zwracane wyrażenie lub przeanalizowany, programu PowerShell host jako blok skryptu literału, ujęte w nawiasy klamrowe `{}`, zanim został przekazany do PowerShell.exe.</span><span class="sxs-lookup"><span data-stu-id="22724-173">The ScriptBlock type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces `{}`, before being passed to PowerShell.exe.</span></span>

<span data-ttu-id="22724-174">W cmd.exe, znajduje się coś takiego jak blok skryptu (lub ScriptBlock typu), więc wartość przekazana do **polecenia** będzie _zawsze_ jest ciąg.</span><span class="sxs-lookup"><span data-stu-id="22724-174">In cmd.exe, there is no such thing as a script block (or ScriptBlock type), so the value passed to **Command** will _always_ be a string.</span></span>
<span data-ttu-id="22724-175">Można napisać blok skryptu wewnątrz ciągu, ale zamiast wykonywana będzie ona działać dokładnie tak, jakby wpisany w wierszu programu PowerShell typowe drukowanie zawartość skryptu blokady powrót do Ciebie.</span><span class="sxs-lookup"><span data-stu-id="22724-175">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="22724-176">Ciąg przekazywany do `-Command` nadal będą wykonywane jako programu PowerShell, więc nawiasów klamrowych blok skryptu często nie są wymagane w pierwszej kolejności podczas uruchamiania z cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="22724-176">A string passed to `-Command` will still be executed as PowerShell, so the script block curly braces are often not required in the first place when running from cmd.exe.</span></span>
<span data-ttu-id="22724-177">Wykonanie bloku skryptu wbudowane, zdefiniowane wewnątrz ciągu, [operator wywołania](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` można użyć:</span><span class="sxs-lookup"><span data-stu-id="22724-177">To execute an inline script block defined inside a string, the [call operator](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` can be used:</span></span>

```console
"& {<command>}"
```

### <a name="-help---"></a><span data-ttu-id="22724-178">-Help,-?, /?</span><span class="sxs-lookup"><span data-stu-id="22724-178">-Help, -?, /?</span></span>

<span data-ttu-id="22724-179">Przedstawia składnię powershell.exe.</span><span class="sxs-lookup"><span data-stu-id="22724-179">Shows the syntax of powershell.exe.</span></span> <span data-ttu-id="22724-180">Jeśli piszesz polecenia PowerShell.exe w programie PowerShell, należy poprzedzić parametry polecenia łącznikiem (-), nie ukośnika (/).</span><span class="sxs-lookup"><span data-stu-id="22724-180">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="22724-181">Można użyć łącznika lub ukośnikiem w Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="22724-181">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="22724-182">Uwaga dotycząca rozwiązywania problemów: W programie PowerShell 2.0 począwszy niektóre programy w programie Windows PowerShell, konsola nie LastExitCode 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="22724-182">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="22724-183">PRZYKŁADY</span><span class="sxs-lookup"><span data-stu-id="22724-183">EXAMPLES</span></span>

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
