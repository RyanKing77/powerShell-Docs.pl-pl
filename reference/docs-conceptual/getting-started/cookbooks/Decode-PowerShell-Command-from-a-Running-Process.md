---
ms.date: 11/13/2018
keywords: polecenia cmdlet programu PowerShell
title: Dekodowanie polecenia programu PowerShell z uruchomionego procesu
author: randomnote1
ms.openlocfilehash: a0602070a8c5b60ce0bb09e227690f48d970a868
ms.sourcegitcommit: 91786b03704fbd2d185f674df0bc67faddfb6288
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2018
ms.locfileid: "51619256"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a><span data-ttu-id="cee19-103">Dekodowanie polecenia programu PowerShell z uruchomionego procesu</span><span class="sxs-lookup"><span data-stu-id="cee19-103">Decode a PowerShell command from a running process</span></span>

<span data-ttu-id="cee19-104">Czasami może być PowerShell proces uruchomiony, która zajmuje znaczną ilość zasobów.</span><span class="sxs-lookup"><span data-stu-id="cee19-104">At times, you may have a PowerShell process running that is taking up a large amount of resources.</span></span>
<span data-ttu-id="cee19-105">Ten proces może być uruchomiony w kontekście [harmonogram zadań][] zadania lub [Agent programu SQL Server][] zadania.</span><span class="sxs-lookup"><span data-stu-id="cee19-105">This process could be running in the context of a [Task Scheduler][] job or a [SQL Server Agent][] job.</span></span> <span data-ttu-id="cee19-106">W przypadku wielu procesów programu PowerShell, uruchomionych, może być trudne, należy wiedzieć, który proces reprezentuje problem.</span><span class="sxs-lookup"><span data-stu-id="cee19-106">Where there are multiple PowerShell processes running, it can be difficult to know which process represents the problem.</span></span> <span data-ttu-id="cee19-107">W tym artykule przedstawiono sposób dekodowania blok skryptu, który proces programu PowerShell jest obecnie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="cee19-107">This article shows how to decode a script block that a PowerShell process is currently running.</span></span>

## <a name="create-a-long-running-process"></a><span data-ttu-id="cee19-108">Tworzenie długo uruchomionego procesu</span><span class="sxs-lookup"><span data-stu-id="cee19-108">Create a long running process</span></span>

<span data-ttu-id="cee19-109">Aby zademonstrować, w tym scenariuszu, Otwórz nowe okno programu PowerShell i uruchom następujący kod.</span><span class="sxs-lookup"><span data-stu-id="cee19-109">To demonstrate this scenario, open a new PowerShell window and run the following code.</span></span> <span data-ttu-id="cee19-110">Wykonuje polecenia programu PowerShell, który wyświetla liczbę co minutę przez 10 minut.</span><span class="sxs-lookup"><span data-stu-id="cee19-110">It executes a PowerShell command that outputs a number every minute for 10 minutes.</span></span>

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

## <a name="view-the-process"></a><span data-ttu-id="cee19-111">Widok procesu</span><span class="sxs-lookup"><span data-stu-id="cee19-111">View the process</span></span>

<span data-ttu-id="cee19-112">Treść polecenia, które program PowerShell jest wykonywany jest przechowywany w **CommandLine** właściwość [Win32_Process][] klasy.</span><span class="sxs-lookup"><span data-stu-id="cee19-112">The body of the command which PowerShell is executing is stored in the **CommandLine** property of the [Win32_Process][] class.</span></span> <span data-ttu-id="cee19-113">Jeśli polecenie jest [zakodowane polecenia][], **CommandLine** właściwość zawiera ciąg "EncodedCommand".</span><span class="sxs-lookup"><span data-stu-id="cee19-113">If the command is an [encoded command][], the **CommandLine** property contains the string "EncodedCommand".</span></span> <span data-ttu-id="cee19-114">Korzystając z tych informacji, polecenie zakodowany można cofnąć zaciemnionego za pośrednictwem następującego procesu.</span><span class="sxs-lookup"><span data-stu-id="cee19-114">Using this information, the encoded command can be de-obfuscated via the following process.</span></span>

<span data-ttu-id="cee19-115">Uruchom program PowerShell jako Administrator.</span><span class="sxs-lookup"><span data-stu-id="cee19-115">Start PowerShell as Administrator.</span></span> <span data-ttu-id="cee19-116">Jest to istotne, że program PowerShell jest uruchomione jako administrator, w przeciwnym razie są zwracane żadne wyniki podczas wykonywania zapytań względem uruchomionych procesów.</span><span class="sxs-lookup"><span data-stu-id="cee19-116">It is vital that PowerShell is running as administrator, otherwise no results are returned when querying the running processes.</span></span>

<span data-ttu-id="cee19-117">Wykonaj następujące polecenie, aby wszystkie procesy programu PowerShell, które ma zakodowany polecenia:</span><span class="sxs-lookup"><span data-stu-id="cee19-117">Execute the following command to get all of the PowerShell processes that have an encoded command:</span></span>

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

<span data-ttu-id="cee19-118">Następujące polecenie tworzy niestandardowy obiekt programu PowerShell, który zawiera identyfikator procesu i zakodowany polecenia.</span><span class="sxs-lookup"><span data-stu-id="cee19-118">The following command creates a custom PowerShell object that contains the process ID and the encoded command.</span></span>

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

<span data-ttu-id="cee19-119">Teraz zakodowany polecenie może zostać odczytany.</span><span class="sxs-lookup"><span data-stu-id="cee19-119">Now the encoded command can be decoded.</span></span> <span data-ttu-id="cee19-120">Poniższy fragment kodu iteruje przez obiekt szczegóły polecenia dekoduje zakodowany polecenia i dodaje zdekodowany polecenia obiektu w celu bliższego zbadania problemu.</span><span class="sxs-lookup"><span data-stu-id="cee19-120">The following snippet iterates over the command details object, decodes the encoded command, and adds the decoded command back to the object for further investigation.</span></span>

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

<span data-ttu-id="cee19-121">Polecenie zdekodowany teraz można wyświetlić, wybierając właściwość zdekodowany polecenia.</span><span class="sxs-lookup"><span data-stu-id="cee19-121">The decoded command can now be reviewed by selecting the decoded command property.</span></span>

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

[Harmonogram zadań]: /windows/desktop/TaskSchd/task-scheduler-start-page
[Task Scheduler]: /windows/desktop/TaskSchd/task-scheduler-start-page
[Agent programu SQL Server]: /sql/ssms/agent/sql-server-agent
[SQL Server Agent]: /sql/ssms/agent/sql-server-agent
[Win32_Process]: /windows/desktop/CIMWin32Prov/win32-process
[zakodowane polecenia]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
[encoded command]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
