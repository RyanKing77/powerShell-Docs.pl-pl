---
ms.date: 11/13/2018
keywords: polecenia cmdlet programu PowerShell
title: Dekodowanie polecenia programu PowerShell z uruchomionego procesu
author: randomnote1
ms.openlocfilehash: a6c01d8edf67aba6c47350a97cc0ceec4801ad29
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470970"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a>Dekodowanie polecenia programu PowerShell z uruchomionego procesu

Czasami może być PowerShell proces uruchomiony, która zajmuje znaczną ilość zasobów.
Ten proces może być uruchomiony w kontekście [Task Scheduler][] zadania lub [Agent programu SQL Server][] zadania. W przypadku wielu procesów programu PowerShell, uruchomionych, może być trudne, należy wiedzieć, który proces reprezentuje problem. W tym artykule przedstawiono sposób dekodowania blok skryptu, który proces programu PowerShell jest obecnie uruchomiony.

## <a name="create-a-long-running-process"></a>Tworzenie długo uruchomionego procesu

Aby zademonstrować, w tym scenariuszu, Otwórz nowe okno programu PowerShell i uruchom następujący kod. Wykonuje polecenia programu PowerShell, który wyświetla liczbę co minutę przez 10 minut.

```powershell
powershell.exe -Command {
    $i = 1
    while ( $i -le 10 )
    {
        Write-Output -InputObject $i
        Start-Sleep -Seconds 60
        $i++
    }
}
```

## <a name="view-the-process"></a>Widok procesu

Treść polecenia, które program PowerShell jest wykonywany jest przechowywany w **CommandLine** właściwość [Win32_Process][] klasy. Jeśli polecenie jest poleceniem zakodowany **CommandLine** właściwość zawiera ciąg "EncodedCommand". Korzystając z tych informacji, polecenie zakodowany można cofnąć zaciemnionego za pośrednictwem następującego procesu.

Uruchom program PowerShell jako Administrator. Jest to istotne, że program PowerShell jest uruchomione jako administrator, w przeciwnym razie są zwracane żadne wyniki podczas wykonywania zapytań względem uruchomionych procesów.

Wykonaj następujące polecenie, aby wszystkie procesy programu PowerShell, które ma zakodowany polecenia:

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

Następujące polecenie tworzy niestandardowy obiekt programu PowerShell, który zawiera identyfikator procesu i zakodowany polecenia.

```powershell
$commandDetails = $powerShellProcesses | Select-Object -Property ProcessId,
@{
    name       = 'EncodedCommand'
    expression = {
        if ( $_.CommandLine -match 'encodedCommand (.*) -inputFormat' )
        {
            return $matches[1]
        }
    }
}
```

Teraz zakodowany polecenie może zostać odczytany. Poniższy fragment kodu iteruje przez obiekt szczegóły polecenia dekoduje zakodowany polecenia i dodaje zdekodowany polecenia obiektu w celu bliższego zbadania problemu.

```powershell
$commandDetails | ForEach-Object -Process {
    # Get the current process
    $currentProcess = $_

    # Convert the Base 64 string to a Byte Array
    $commandBytes = [System.Convert]::FromBase64String($currentProcess.EncodedCommand)

    # Convert the Byte Array to a string
    $decodedCommand = [System.Text.Encoding]::Unicode.GetString($commandBytes)

    # Add the decoded command back to the object
    $commandDetails |
        Where-Object -FilterScript { $_.ProcessId -eq $_.ProcessId } |
        Add-Member -MemberType NoteProperty -Name DecodedCommand -Value $decodedCommand
}
$commandDetails[0]
```

Polecenie zdekodowany teraz można wyświetlić, wybierając właściwość zdekodowany polecenia.

```output
ProcessId      : 8752
EncodedCommand : IAAKAAoACgAgAAoAIAAgACAAIAAkAGkAIAA9ACAAMQAgAAoACgAKACAACgAgACAAIAAgAHcAaABpAGwAZQAgACgAIAAkAGkAIAAtAG
                 wAZQAgADEAMAAgACkAIAAKAAoACgAgAAoAIAAgACAAIAB7ACAACgAKAAoAIAAKACAAIAAgACAAIAAgACAAIABXAHIAaQB0AGUALQBP
                 AHUAdABwAHUAdAAgAC0ASQBuAHAAdQB0AE8AYgBqAGUAYwB0ACAAJABpACAACgAKAAoAIAAKACAAIAAgACAAIAAgACAAIABTAHQAYQ
                 ByAHQALQBTAGwAZQBlAHAAIAAtAFMAZQBjAG8AbgBkAHMAIAA2ADAAIAAKAAoACgAgAAoAIAAgACAAIAAgACAAIAAgACQAaQArACsA
                 IAAKAAoACgAgAAoAIAAgACAAIAB9ACAACgAKAAoAIAAKAA==
DecodedCommand :
                     $i = 1

                     while ( $i -le 10 )

                     {

                         Write-Output -InputObject $i

                         Start-Sleep -Seconds 60

                         $i++

                     }
```

[Task Scheduler]: /windows/desktop/TaskSchd/task-scheduler-start-page
[Agent programu SQL Server]: /sql/ssms/agent/sql-server-agent
[Win32_Process]: /windows/desktop/CIMWin32Prov/win32-process
