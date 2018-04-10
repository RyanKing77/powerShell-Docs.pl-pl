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
---
# <a name="powershellexe-command-line-help"></a>PowerShell.exe Pomoc wiersza polecenia

Może być PowerShell.exe Uruchom sesję programu PowerShell z poziomu wiersza polecenia narzędzia do innego, takich jak Cmd.exe, lub użyć go w wierszu polecenia programu PowerShell, można uruchomić nowej sesji. Aby dostosować sesji, należy użyć parametrów.

## <a name="syntax"></a>Składnia

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

## <a name="parameters"></a>Parametry

### <a name="-encodedcommand-base64encodedcommand"></a>-EncodedCommand <Base64EncodedCommand>

Akceptuje wersji algorytmem base-64 ciąg polecenia. Użyj tego parametru, aby przesłać poleceń programu PowerShell, które wymagają złożonych znaków cudzysłowu lub nawiasy klamrowe.

### <a name="-executionpolicy-executionpolicy"></a>-ExecutionPolicy <ExecutionPolicy>

Ustawia domyślne zasady wykonywania w bieżącej sesji i zapisze go w $env: PSExecutionPolicyPreference zmiennej środowiskowej. Ten parametr nie powoduje zmiany zasad wykonywania programu PowerShell, który jest ustawiony w rejestrze. Aby uzyskać informacje na temat zasad wykonywania programu PowerShell, łącznie z listą prawidłowych wartości zobacz [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

### <a name="-file-filepath-parameters"></a>-Plik <FilePath> \[ <Parameters>]

Uruchamia określony skrypt w zakresie lokalnym ("kropka-powierzając jej ich konserwację"), dzięki czemu funkcje i zmienne, które tworzy skrypt są dostępne w bieżącej sesji. Wprowadź ścieżkę pliku skryptu i wszelkie parametry. **Plik** musi być ostatnim parametrem w wierszu polecenia, ponieważ wszystkie znaki wpisany po **pliku** Nazwa parametru będą interpretowane jako ścieżkę pliku skryptu, a następnie Parametry skryptu i ich wartości.

Parametry skryptu i wartości parametrów, może zawierać wartości **pliku** parametru. Na przykład: `-File .\Get-Script.ps1 -Domain Central` należy pamiętać, że parametry przekazywane do skryptu są przekazywane jako literał ciągi (po interpretacji przez powłokę bieżącego).
Na przykład, jeśli są w cmd.exe i przekazać wartość zmiennej środowiskowej, można skorzystać składni cmd.exe: `powershell -File .\test.ps1 -Sample %windir%` zostały używać składni programu PowerShell, a następnie w tym przykładzie skrypt otrzyma literału "$env: windir", a nie wartość tego zmiennej środowiskowej: `powershell -File .\test.ps1 -Sample $env:windir`

Zazwyczaj parametry przełącznika skryptu są włączone lub pominięty. Na przykład następujące polecenie używa **wszystkie** parametr Get-Script.ps1 pliku skryptu: `-File .\Get-Script.ps1 -All`

### <a name="-inputformat-text--xml"></a>\-InputFormat {tekstu | XML}

Opisuje format danych wysyłanych do programu PowerShell. Prawidłowe wartości to "Text" (ciągi) lub "XML" (format serializacji CLIXML).

### <a name="-mta"></a>-Mta

Zostanie uruchomiony przy użyciu wielowątkowej programu PowerShell. Ten parametr jest wprowadzone w środowisku PowerShell 3.0. W środowisku PowerShell 3.0 jednowątkowego apartamentu (STA) jest ustawieniem domyślnym. W programie PowerShell 2.0 wielowątkowej (MTA) jest ustawieniem domyślnym.

### <a name="-noexit"></a>-NoExit

Nie istnieje po uruchomieniu polecenia uruchomienia.

### <a name="-nologo"></a>-NoLogo

Ukrywa praw autorskich transparentu podczas uruchamiania.

### <a name="-noninteractive"></a>-NonInteractive

Użytkownik nie widzi monitu interakcyjnego.

### <a name="-noprofile"></a>-NoProfile

Nie załadować profilu programu PowerShell.

### <a name="-outputformat-text--xml"></a>-OutputFormat {tekstu | XML}

Określa, jak dane wyjściowe programu PowerShell jest sformatowany. Prawidłowe wartości to "Text" (ciągi) lub "XML" (format serializacji CLIXML).

### <a name="-psconsolefile-filepath"></a>-PSConsoleFile <FilePath>

Ładuje określony plik konsoli programu PowerShell. Wprowadź ścieżkę i nazwę pliku konsoli. Aby utworzyć plik konsoli, należy użyć [ `Export-Console` ](/powershell/module/Microsoft.PowerShell.Core/Export-Console) polecenia cmdlet programu PowerShell.

### <a name="-sta"></a>-Sta

Zostanie uruchomiony przy użyciu jednowątkowego apartamentu programu PowerShell. W środowisku PowerShell 3.0 jednowątkowego apartamentu (STA) jest ustawieniem domyślnym. W programie PowerShell 2.0 wielowątkowej (MTA) jest ustawieniem domyślnym.

### <a name="-version-powershell-version"></a>-Wersja <PowerShell Version>

Rozpoczyna się określona wersja środowiska PowerShell. Określonej wersji musi być zainstalowany w systemie. Jeśli PowerShell 3.0 jest zainstalowany na komputerze, prawidłowe wartości to "w wersji 2.0" i "3.0". Wartość domyślna to "3.0".

Jeśli nie zainstalowano programu PowerShell 3.0, jedyną prawidłową wartością jest "2.0". Inne wartości są ignorowane.

Aby uzyskać więcej informacji, zobacz "[Instalowanie programu Windows PowerShell](../../setup/installing-windows-powershell.md)".

### <a name="-windowstyle-window-style"></a>-WindowStyle <Window style>

Ustawia styl okna w sesji. Prawidłowe wartości to normalny, zminimalizowany, Maximized i Hidden.

### <a name="-command"></a>— Polecenie

Wykonuje podane polecenie (i wszelkie parametry) tak, jakby były wpisywane w wierszu polecenia programu PowerShell, a następnie kończy działanie, chyba że określony jest parametr NoExit.
Zasadniczo tekst po `-Command` są wysyłane w jednym wierszu polecenia środowiska PowerShell (to różni się od tego, jak `-File` obsługuje parametry wysyłane do skryptu).

Możliwe wartości polecenia "-", ciąg. albo blok skryptu. Jeśli ma wartość polecenia "-", tekst polecenia są odczytywane z standardowe dane wejściowe.

Bloki skryptu muszą być ujęte w nawiasy klamrowe ({}). Blok skryptu można określić tylko wtedy, gdy uruchomiony PowerShell.exe w programie PowerShell. Zwrot wyników skryptu powłoki nadrzędnego jako zdeserializowany obiekty XML, a nie na żywo obiekty.

Jeśli wartość polecenia jest ciągiem, **polecenia** musi być ostatnim parametrem w wierszu polecenia, ponieważ znaków wpisane po poleceniu będą interpretowane jako argumenty wiersza polecenia.

Aby zapisać ciąg, który uruchamia polecenie programu PowerShell, użyj formatu:

```powershell
"& {<command>}"
```

gdzie znaki cudzysłowu wskazują ciągu i operator wywołania (&) powoduje, że polecenie do wykonania.

### <a name="-help---"></a>-Help,-?, /?

Pokazuje tego komunikatu. Jeśli piszesz polecenia PowerShell.exe w programie PowerShell, dołączenie wartości parametrów polecenia łącznikiem (-), nie ukośnika (/). Można użyć łącznika lub ukośnika w Cmd.exe.

> [!NOTE]
> Uwaga: W programie PowerShell 2.0, począwszy od niektóre programy, w konsoli środowiska Windows PowerShell LastExitCode 0xc0000142.

## <a name="examples"></a>PRZYKŁADY

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