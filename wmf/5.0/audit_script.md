---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 2627b9d02788bd31a5384587406df533faf2cfaf
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="script-tracing-and-logging"></a><span data-ttu-id="11d0f-102">Śledzenie i rejestrowanie skryptów</span><span class="sxs-lookup"><span data-stu-id="11d0f-102">Script Tracing and Logging</span></span>

<span data-ttu-id="11d0f-103">Gdy ma już środowiska Windows PowerShell **LogPipelineExecutionDetails** zasad grupy ustawień dziennika wywołanie polecenia cmdlet, język skryptów dla środowiska PowerShell ma wystarczająco dużo funkcje, które możesz chcieć logowania i/lub inspekcji.</span><span class="sxs-lookup"><span data-stu-id="11d0f-103">While Windows PowerShell already has the **LogPipelineExecutionDetails** Group Policy setting to log the invocation of cmdlets, PowerShell’s scripting language has plenty of features that you might want to log and/or audit.</span></span> <span data-ttu-id="11d0f-104">Nowa funkcja śledzenia szczegółowy skrypt umożliwia szczegółowe śledzenie i analizy użycia skryptów środowiska Windows PowerShell w systemie.</span><span class="sxs-lookup"><span data-stu-id="11d0f-104">The new Detailed Script Tracing feature lets you enable detailed tracking and analysis of Windows PowerShell scripting use on a system.</span></span> <span data-ttu-id="11d0f-105">Po włączeniu śledzenia szczegółowy skrypt programu Windows PowerShell dzienników wszystkich blokach skryptu w dzienniku zdarzeń ETW **Microsoft-Windows-PowerShell/Operational**.</span><span class="sxs-lookup"><span data-stu-id="11d0f-105">After you enable detailed script tracing, Windows PowerShell logs all script blocks to the ETW event log, **Microsoft-Windows-PowerShell/Operational**.</span></span> <span data-ttu-id="11d0f-106">Jeśli blok skryptu tworzy innego bloku skryptu (na przykład skrypt, który wywołuje polecenie cmdlet Invoke-Expression w ciągu), tym wynikowy bloku skryptu jest również rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="11d0f-106">If a script block creates another script block (for example, a script that calls the Invoke-Expression cmdlet on a string), that resulting script block is logged as well.</span></span>

<span data-ttu-id="11d0f-107">Rejestrowanie tych zdarzeń można włączyć za pomocą **Włącz rejestrowanie bloku skryptu PowerShell** ustawienia zasad grupy (w Szablony administracyjne -> składniki systemu Windows -> środowiska Windows PowerShell).</span><span class="sxs-lookup"><span data-stu-id="11d0f-107">Logging of these events can be enabled through the **Turn on PowerShell Script Block Logging** Group Policy setting (in Administrative Templates -> Windows Components -> Windows PowerShell).</span></span>

<span data-ttu-id="11d0f-108">Dostępne są następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="11d0f-108">The events are:</span></span>

| <span data-ttu-id="11d0f-109">Kanał</span><span class="sxs-lookup"><span data-stu-id="11d0f-109">Channel</span></span> | <span data-ttu-id="11d0f-110">Operacyjne</span><span class="sxs-lookup"><span data-stu-id="11d0f-110">Operational</span></span>                                 |
|---------|---------------------------------------------|
| <span data-ttu-id="11d0f-111">Poziom</span><span class="sxs-lookup"><span data-stu-id="11d0f-111">Level</span></span>   | <span data-ttu-id="11d0f-112">Verbose</span><span class="sxs-lookup"><span data-stu-id="11d0f-112">Verbose</span></span>                                     |
| <span data-ttu-id="11d0f-113">Kod operacji</span><span class="sxs-lookup"><span data-stu-id="11d0f-113">Opcode</span></span>  | <span data-ttu-id="11d0f-114">Utworzenie</span><span class="sxs-lookup"><span data-stu-id="11d0f-114">Create</span></span>                                      |
| <span data-ttu-id="11d0f-115">Zadanie</span><span class="sxs-lookup"><span data-stu-id="11d0f-115">Task</span></span>    | <span data-ttu-id="11d0f-116">CommandStart</span><span class="sxs-lookup"><span data-stu-id="11d0f-116">CommandStart</span></span>                                |
| <span data-ttu-id="11d0f-117">Słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="11d0f-117">Keyword</span></span> | <span data-ttu-id="11d0f-118">Obszarze działania</span><span class="sxs-lookup"><span data-stu-id="11d0f-118">Runspace</span></span>                                    |
| <span data-ttu-id="11d0f-119">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="11d0f-119">EventId</span></span> | <span data-ttu-id="11d0f-120">Engine_ScriptBlockCompiled (0x1008 = 4104)</span><span class="sxs-lookup"><span data-stu-id="11d0f-120">Engine_ScriptBlockCompiled (0x1008 = 4104)</span></span>  |
| <span data-ttu-id="11d0f-121">Wiadomość</span><span class="sxs-lookup"><span data-stu-id="11d0f-121">Message</span></span> | <span data-ttu-id="11d0f-122">Tworzenie tekstu Scriptblock (%1 z %2):</span><span class="sxs-lookup"><span data-stu-id="11d0f-122">Creating Scriptblock text (%1 of %2):</span></span> </br> <span data-ttu-id="11d0f-123">%3</span><span class="sxs-lookup"><span data-stu-id="11d0f-123">%3</span></span> </br> <span data-ttu-id="11d0f-124">Blok skryptu ID: %4</span><span class="sxs-lookup"><span data-stu-id="11d0f-124">ScriptBlock ID: %4</span></span> |


<span data-ttu-id="11d0f-125">Tekst osadzone w wiadomości jest zakres bloku skryptu skompilowany.</span><span class="sxs-lookup"><span data-stu-id="11d0f-125">The text embedded in the message is the extent of the script block compiled.</span></span> <span data-ttu-id="11d0f-126">Identyfikator jest identyfikatorem GUID, który jest zachowywana przez cały okres istnienia blok skryptu.</span><span class="sxs-lookup"><span data-stu-id="11d0f-126">The ID is a GUID that is retained for the life of the script block.</span></span>

<span data-ttu-id="11d0f-127">Po włączeniu pełnego rejestrowania zapisy funkcji rozpoczęcia i zakończenia znaczników:</span><span class="sxs-lookup"><span data-stu-id="11d0f-127">When you enable verbose logging, the feature writes begin and end markers:</span></span>

| <span data-ttu-id="11d0f-128">Kanał</span><span class="sxs-lookup"><span data-stu-id="11d0f-128">Channel</span></span> | <span data-ttu-id="11d0f-129">Operacyjne</span><span class="sxs-lookup"><span data-stu-id="11d0f-129">Operational</span></span>                                            |
|---------|--------------------------------------------------------|
| <span data-ttu-id="11d0f-130">Poziom</span><span class="sxs-lookup"><span data-stu-id="11d0f-130">Level</span></span>   | <span data-ttu-id="11d0f-131">Verbose</span><span class="sxs-lookup"><span data-stu-id="11d0f-131">Verbose</span></span>                                                |
| <span data-ttu-id="11d0f-132">Kod operacji</span><span class="sxs-lookup"><span data-stu-id="11d0f-132">Opcode</span></span>  | <span data-ttu-id="11d0f-133">Otwórz (/ zamknięcie)</span><span class="sxs-lookup"><span data-stu-id="11d0f-133">Open (/ Close)</span></span>                                         |
| <span data-ttu-id="11d0f-134">Zadanie</span><span class="sxs-lookup"><span data-stu-id="11d0f-134">Task</span></span>    | <span data-ttu-id="11d0f-135">CommandStart (/ CommandStop)</span><span class="sxs-lookup"><span data-stu-id="11d0f-135">CommandStart (/ CommandStop)</span></span>                           |
| <span data-ttu-id="11d0f-136">Słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="11d0f-136">Keyword</span></span> | <span data-ttu-id="11d0f-137">Obszarze działania</span><span class="sxs-lookup"><span data-stu-id="11d0f-137">Runspace</span></span>                                               |
| <span data-ttu-id="11d0f-138">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="11d0f-138">EventId</span></span> | <span data-ttu-id="11d0f-139">Blok skryptu\_wywołania\_Start\_szczegółów (0x1009 = 4105) /</span><span class="sxs-lookup"><span data-stu-id="11d0f-139">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span></span> </br> <span data-ttu-id="11d0f-140">Blok skryptu\_wywołania\_pełną\_szczegółów (0x100A = 4106)</span><span class="sxs-lookup"><span data-stu-id="11d0f-140">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span></span> |
| <span data-ttu-id="11d0f-141">Wiadomość</span><span class="sxs-lookup"><span data-stu-id="11d0f-141">Message</span></span> | <span data-ttu-id="11d0f-142">Wprowadzenie (/ ukończone) wywołanie ScriptBlock identyfikator: %1</span><span class="sxs-lookup"><span data-stu-id="11d0f-142">Started (/ Completed) invocation of ScriptBlock ID: %1</span></span> </br> <span data-ttu-id="11d0f-143">Identyfikator działania: %2</span><span class="sxs-lookup"><span data-stu-id="11d0f-143">Runspace ID: %2</span></span> |

<span data-ttu-id="11d0f-144">Identyfikator to identyfikator GUID reprezentujący bloku skryptu (która może zostać skorelowane zdarzenia o identyfikatorze 0x1008) i identyfikator obszaru działania reprezentuje obszaru działania, w którym uruchomiono ten blok skryptu.</span><span class="sxs-lookup"><span data-stu-id="11d0f-144">The ID is the GUID representing the script block (that can be correlated with event ID 0x1008), and the Runspace ID represents the runspace in which this script block was run.</span></span>

<span data-ttu-id="11d0f-145">Znaki procentu w komunikat dotyczący wywołania reprezentują strukturalnych właściwości ETW.</span><span class="sxs-lookup"><span data-stu-id="11d0f-145">Percent signs in the invocation message represent structured ETW properties.</span></span> <span data-ttu-id="11d0f-146">Gdy są zamieniane na rzeczywiste wartości w treści wiadomości, bardziej niezawodny sposób uzyskiwać do nich dostęp jest pobierania wiadomości za pomocą polecenia cmdlet Get-WinEvent, a następnie użyć **właściwości** tablicy wiadomości.</span><span class="sxs-lookup"><span data-stu-id="11d0f-146">While they are replaced with the actual values in the message text, a more robust way to access them is to retrieve the message with the Get-WinEvent cmdlet, and then use the **Properties** array of the message.</span></span>

<span data-ttu-id="11d0f-147">Oto przykład jak ta funkcja może ułatwić dekodowania złośliwego Próba szyfrowania i zasłaniają skryptu:</span><span class="sxs-lookup"><span data-stu-id="11d0f-147">Here's an example of how this functionality can help unwrap a malicious attempt to encrypt and obfuscate a script:</span></span>

```powershell
## Malware
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)

    ## XOR “encryption”
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)
}

$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
Invoke-Expression $decrypted
```

<span data-ttu-id="11d0f-148">Uruchomiona generuje następujące wpisy dziennika:</span><span class="sxs-lookup"><span data-stu-id="11d0f-148">Running this generates the following log entries:</span></span>

```
Compiling Scriptblock text (1 of 1):
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)
    ## XOR "encryption"
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)

}
ScriptBlock ID: ad8ae740-1f33-42aa-8dfc-1314411877e3

Compiling Scriptblock text (1 of 1):
$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
ScriptBlock ID: ba11c155-d34c-4004-88e3-6502ecb50f52

Compiling Scriptblock text (1 of 1):
Invoke-Expression $decrypted
ScriptBlock ID: 856c01ca-85d7-4989-b47f-e6a09ee4eeb3

Compiling Scriptblock text (1 of 1):
Write-Host 'Pwnd'
ScriptBlock ID: 5e618414-4e77-48e3-8f65-9a863f54b4c8
```

Jeśli długość bloku skryptu przekracza co ETW jest w stanie akcji w pojedyncze zdarzenie, skrypt programu Windows PowerShell dzieli się na wielu części. <span data-ttu-id="11d0f-150">Oto przykładowy kod, aby ponownie połączyć skryptu z jego komunikaty dziennika:</span><span class="sxs-lookup"><span data-stu-id="11d0f-150">Here is sample code to recombine a script from its log messages:</span></span>

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } | Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

<span data-ttu-id="11d0f-151">Podobnie jak w przypadku wszystkich systemów rejestrowania mające buforu przechowywania ograniczone (tj. dzienniki zdarzeń systemu Windows), jest jeden atak tej infrastruktury do wypełniania dziennika fałszywe zdarzenia, aby ukryć dowód wcześniej.</span><span class="sxs-lookup"><span data-stu-id="11d0f-151">As with all logging systems that have a limited retention buffer (i.e. ETW logs), one attack against this infrastructure is to flood the log with spurious events to hide earlier evidence.</span></span> <span data-ttu-id="11d0f-152">Aby zabezpieczyć się na ataki, upewnij się, że masz jakiegoś zbierania dzienników zdarzeń — konfiguracja (np. Windows funkcji przekazywania zdarzeń, [analizie atakujący dokonuje monitorowania dziennika zdarzeń systemu Windows z](http://www.nsa.gov/ia/_files/app/Spotting_the_Adversary_with_Windows_Event_Log_Monitoring.pdf)) można przenieść dzienniki zdarzeń wylogowuje na komputerze jako najszybciej, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="11d0f-152">To protect yourself from this attack, ensure that you have some form of event log collection set up (i.e., Windows Event Forwarding, [Spotting the Adversary with Windows Event Log Monitoring](http://www.nsa.gov/ia/_files/app/Spotting_the_Adversary_with_Windows_Event_Log_Monitoring.pdf)) to move event logs off of the computer as soon as possible.</span></span>
