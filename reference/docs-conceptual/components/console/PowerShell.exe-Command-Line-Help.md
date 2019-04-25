---
ms.date: 08/14/2018
keywords: polecenia cmdlet programu PowerShell
title: PowerShell.exe — pomoc wiersza polecenia
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 0a11ebb11d29adf5853c232b3aa10bc72f92bf0c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058517"
---
# <a name="powershellexe-command-line-help"></a>Pomoc w wierszu polecenia PowerShell.exe

Można użyć PowerShell.exe do uruchomienia sesji programu PowerShell z wiersza polecenia z innego narzędzia, takiego jak Cmd.exe, lub użyć w wierszu polecenia programu PowerShell, aby rozpocząć nową sesję. Parametry służą do dostosowywania sesji.

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

Akceptuje wersji algorytmem base-64 ciągu polecenia. Użyj tego parametru, aby przesłać poleceń do programu PowerShell, które wymagają złożonych znaków cudzysłowu lub nawiasów klamrowych.

### <a name="-executionpolicy-executionpolicy"></a>-ExecutionPolicy <ExecutionPolicy>

Domyślne zasady wykonywania dla bieżącej sesji i zapisuje je w $env: zmienna środowiskowa PSExecutionPolicyPreference. Ten parametr nie powoduje zmiany zasad wykonywania programu PowerShell, który jest ustawiony w rejestrze. Aby uzyskać informacje na temat zasad wykonywania programu PowerShell, łącznie z listą prawidłowych wartości, zobacz [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

### <a name="-file-filepath-parameters"></a>-Pliku <FilePath> \[ <Parameters>]

Wykonuje określony skrypt w zakresie lokalnym ("dot Source"), dzięki czemu funkcje i zmienne, utworzonych przez skrypt są dostępne w bieżącej sesji. Wprowadź ścieżkę pliku skryptu oraz wszelkie parametry. **Plik** musi być ostatnim parametrem w poleceniu. Wszystkie wartości po **— plik** parametru są interpretowane jako skrypt ścieżkę pliku i parametry przekazywane do tego skryptu.

Parametry przekazane do skryptu są przekazywane jako ciągi literałowe po interpretacji w bieżącej powłoce. Na przykład jeśli znajdują się w cmd.exe i mają być przekazywane wartości zmiennej środowiskowej, użyj składni cmd.exe: `powershell.exe -File .\test.ps1 -TestParam %windir%`

Natomiast uruchomione `powershell.exe -File .\test.ps1 -TestParam $env:windir` w wynikach cmd.exe w skrypcie odbiera literału ciągu `$env:windir` ponieważ go nie ma specjalnego znaczenia do bieżącej powłoce cmd.exe.
`$env:windir` Styl Odnośnik zmiennej środowiskowej _można_ można używać wewnątrz `-Command` parametru, ponieważ ma ona będzie interpretowany jako kod programu PowerShell.

### <a name="-inputformat-text--xml"></a>\-InputFormat {tekstu | XML}

Opisuje format danych wysyłanych do programu PowerShell. Prawidłowe wartości to "Text" (ciągi tekstowe) lub "XML" (w formacie CLIXML serializacji).

### <a name="-mta"></a>-Mta

Uruchamia programu PowerShell przy użyciu modelu wielowątkowości. Ten parametr został wprowadzony w środowisku PowerShell 3.0. W środowisku PowerShell 3.0 apartamentem jednowątkowym (przedziale STA) jest ustawieniem domyślnym. W programie PowerShell 2.0 wielowątkowej (MTA) jest ustawieniem domyślnym.

### <a name="-noexit"></a>-NoExit

Nie zakończyć działanie po uruchomieniu polecenia uruchamiania.

### <a name="-nologo"></a>-NoLogo

Ukrywa praw autorskich transparentu podczas uruchamiania.

### <a name="-noninteractive"></a>-NonInteractive

Użytkownik nie widzi monitu interakcyjnego.

### <a name="-noprofile"></a>-NoProfile

Nie jest ładowana profilu programu PowerShell.

### <a name="-outputformat-text--xml"></a>-OutputFormat {Text | XML}

Określa sposób formatowania danych wyjściowych za pomocą programu PowerShell. Prawidłowe wartości to "Text" (ciągi tekstowe) lub "XML" (w formacie CLIXML serializacji).

### <a name="-psconsolefile-filepath"></a>-PSConsoleFile <FilePath>

Ładuje określony plik konsoli programu PowerShell. Wprowadź ścieżkę i nazwę pliku konsoli. Aby utworzyć plik konsoli, należy użyć [ `Export-Console` ](/powershell/module/Microsoft.PowerShell.Core/Export-Console) polecenia cmdlet programu PowerShell.

### <a name="-sta"></a>-Sta

Uruchamia programu PowerShell przy użyciu apartamentem jednowątkowym. W środowisku PowerShell 3.0 apartamentem jednowątkowym (przedziale STA) jest ustawieniem domyślnym. W programie PowerShell 2.0 wielowątkowej (MTA) jest ustawieniem domyślnym.

### <a name="-version-powershell-version"></a>-Version <PowerShell Version>

Rozpoczyna się określonej wersji programu PowerShell. Określonej wersji musi być zainstalowany w systemie. Jeśli program PowerShell 3.0 jest zainstalowana na komputerze, prawidłowe wartości to "2.0" i "3.0". Wartość domyślna to "3.0".

Jeśli program PowerShell 3.0 nie jest zainstalowany, jedyna prawidłowa wartość to "w wersji 2.0". Inne wartości są ignorowane.

Aby uzyskać więcej informacji, zobacz [Instalowanie programu Windows PowerShell](../../setup/installing-windows-powershell.md).

### <a name="-windowstyle-window-style"></a>-WindowStyle <Window style>

Ustawia styl okna sesji. Prawidłowe wartości to: Normalny, zminimalizowany, Maximized i ukryty.

### <a name="-command"></a>— Polecenie

Wykonuje określoną polecenia (przy użyciu żadnych parametrów), tak, jakby były one użyte w wierszu polecenia programu PowerShell.
Po wykonaniu PowerShell kończy działanie, chyba że **NoExit** określono parametr.
Dowolny tekst po `-Command` jest wysyłany jako jeden wiersz polecenia dla programu PowerShell.
To różni się od tego, jak `-File` obsługuje parametry wysłane do skryptu.

Wartość `-Command` może być "-", ciąg lub blok skryptu.
Wyniki polecenia są zwracane do powłoki nadrzędnego jako po deserializacji obiektów XML, nie na żywo obiektów.

Jeśli wartość `-Command` jest "-", tekst polecenia jest do odczytu ze standardowego wejścia.

Gdy wartość `-Command` jest ciągiem, **polecenia** _musi_ być ostatnim parametrem określona, ponieważ wszystkie znaki wpisane po polecenia są interpretowane jako argumenty wiersza polecenia.

**Polecenia** parametru akceptuje tylko blok skryptu do wykonania po jego rozpoznaje wartość przekazana do `-Command` jako typu blok skryptu.
Jest to _tylko_ możliwe podczas uruchamiania PowerShell.exe z innego hosta programu PowerShell.
ScriptBlock typu mogą być zawarte w istniejących zmiennych, zwracane wyrażenie lub przeanalizowany, programu PowerShell host jako blok skryptu literału, ujęte w nawiasy klamrowe `{}`, zanim został przekazany do PowerShell.exe.

W cmd.exe, znajduje się coś takiego jak blok skryptu (lub ScriptBlock typu), więc wartość przekazana do **polecenia** będzie _zawsze_ jest ciąg.
Można napisać blok skryptu wewnątrz ciągu, ale zamiast wykonywana będzie ona działać dokładnie tak, jakby wpisany w wierszu programu PowerShell typowe drukowanie zawartość skryptu blokady powrót do Ciebie.

Ciąg przekazywany do `-Command` nadal będą wykonywane jako programu PowerShell, więc nawiasów klamrowych blok skryptu często nie są wymagane w pierwszej kolejności podczas uruchamiania z cmd.exe.
Wykonanie bloku skryptu wbudowane, zdefiniowane wewnątrz ciągu, [operator wywołania](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` można użyć:

```console
"& {<command>}"
```

### <a name="-help---"></a>-Help,-?, /?

Przedstawia składnię powershell.exe. Jeśli piszesz polecenia PowerShell.exe w programie PowerShell, należy poprzedzić parametry polecenia łącznikiem (-), nie ukośnika (/). Można użyć łącznika lub ukośnikiem w Cmd.exe.

> [!NOTE]
> Uwaga dotycząca rozwiązywania problemów: W programie PowerShell 2.0 począwszy niektóre programy w programie Windows PowerShell, konsola nie LastExitCode 0xc0000142.

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
