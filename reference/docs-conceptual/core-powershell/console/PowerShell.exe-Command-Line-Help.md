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

Parametry przekazane do skryptu są przekazywane jako ciąg literału (po interpretacja w bieżącej powłoce). Na przykład, jeśli znajdują się w cmd.exe i mają być przekazywane wartości zmiennej środowiskowej, można użyć składni cmd.exe: `powershell -File .\test.ps1 -Sample %windir%` w tym przykładzie skrypt otrzymuje literału `$env:windir` , a nie wartość tej zmiennej środowiskowej: `powershell -File .\test.ps1 -Sample $env:windir`

### <a name="-inputformat-text--xml"></a>\-InputFormat {tekstu | XML}

Opisuje format danych wysyłanych do programu PowerShell. Prawidłowe wartości to "Text" (ciągi tekstowe) lub "XML" (w formacie CLIXML serializacji).

### <a name="-mta"></a>-Mta

Uruchamia programu PowerShell przy użyciu modelu wielowątkowości. Ten parametr został wprowadzony w środowisku PowerShell 3.0. W środowisku PowerShell 3.0 apartamentem jednowątkowym (przedziale STA) jest ustawieniem domyślnym. W programie PowerShell 2.0 wielowątkowej (MTA) jest ustawieniem domyślnym.

### <a name="-noexit"></a>-NoExit

Nie zakończyć działanie po uruchomieniu polecenia uruchamiania.

### <a name="-nologo"></a>-NoLogo

Ukrywa praw autorskich transparentu podczas uruchamiania.

### <a name="-noninteractive"></a>-Nieinterakcyjnym

Użytkownik nie widzi monitu interakcyjnego.

### <a name="-noprofile"></a>-NoProfile

Nie jest ładowana profilu programu PowerShell.

### <a name="-outputformat-text--xml"></a>-OutputFormat {tekstu | XML}

Określa sposób formatowania danych wyjściowych za pomocą programu PowerShell. Prawidłowe wartości to "Text" (ciągi tekstowe) lub "XML" (w formacie CLIXML serializacji).

### <a name="-psconsolefile-filepath"></a>-PSConsoleFile <FilePath>

Ładuje określony plik konsoli programu PowerShell. Wprowadź ścieżkę i nazwę pliku konsoli. Aby utworzyć plik konsoli, należy użyć [ `Export-Console` ](/powershell/module/Microsoft.PowerShell.Core/Export-Console) polecenia cmdlet programu PowerShell.

### <a name="-sta"></a>-STA.

Uruchamia programu PowerShell przy użyciu apartamentem jednowątkowym. W środowisku PowerShell 3.0 apartamentem jednowątkowym (przedziale STA) jest ustawieniem domyślnym. W programie PowerShell 2.0 wielowątkowej (MTA) jest ustawieniem domyślnym.

### <a name="-version-powershell-version"></a>-Version <PowerShell Version>

Rozpoczyna się określonej wersji programu PowerShell. Określonej wersji musi być zainstalowany w systemie. Jeśli program PowerShell 3.0 jest zainstalowana na komputerze, prawidłowe wartości to "2.0" i "3.0". Wartość domyślna to "3.0".

Jeśli program PowerShell 3.0 nie jest zainstalowany, jedyna prawidłowa wartość to "w wersji 2.0". Inne wartości są ignorowane.

Aby uzyskać więcej informacji, zobacz [Instalowanie programu Windows PowerShell](../../setup/installing-windows-powershell.md).

### <a name="-windowstyle-window-style"></a>-Nazwa_okna <Window style>

Ustawia styl okna sesji. Prawidłowe wartości to: Normalny, zminimalizowany, Maximized i ukryty.

### <a name="-command"></a>— Polecenie

Wykonuje określoną polecenia (przy użyciu żadnych parametrów), tak, jakby były one użyte w wierszu polecenia programu PowerShell. Po wykonaniu PowerShell kończy działanie, chyba że `-NoExit` określono parametr.
Dowolny tekst po `-Command` jest wysyłany jako jeden wiersz polecenia dla programu PowerShell. To różni się od tego, jak `-File` obsługuje parametry wysłane do skryptu.

Wartość polecenia może być "-", ciąg. lub blok skryptu. Jeśli ma wartość polecenia "-", tekst polecenia jest do odczytu ze standardowego wejścia.

Bloki skryptu muszą być ujęte w nawiasy klamrowe ({}). Blok skryptu można określić tylko wtedy, gdy uruchomiony PowerShell.exe w programie PowerShell. Wyniki skryptu są zwracane do powłoki nadrzędnego jako po deserializacji obiektów XML, nie na żywo obiektów.

Jeśli wartość polecenia jest ciągiem, **polecenia** musi być ostatnim parametrem w wierszu polecenia, ponieważ wszystkie znaki wpisane po polecenia są interpretowane jako argumenty wiersza polecenia.

Aby zapisać ciąg, który uruchamia polecenia programu PowerShell, użyj formatu:

```powershell
"& {<command>}"
```

Znaki cudzysłowu wskazują ciągu i invoke operator (&) powoduje, że polecenie do wykonania.

### <a name="-help---"></a>-Help,-?, /?

Przedstawia składnię powershell.exe. Jeśli piszesz polecenia PowerShell.exe w programie PowerShell, należy poprzedzić parametry polecenia łącznikiem (-), nie ukośnika (/). Można użyć łącznika lub ukośnikiem w Cmd.exe.

> [!NOTE]
> Uwaga dotycząca rozwiązywania problemów: W programie PowerShell 2.0, począwszy od niektóre programy w programie Windows PowerShell, konsola nie LastExitCode 0xc0000142.

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
