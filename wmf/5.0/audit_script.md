---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 28cd186ab3a08a0da4ff81f5a21514f239770d13
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058084"
---
# <a name="script-tracing-and-logging"></a><span data-ttu-id="0b353-102">Śledzenie i rejestrowanie skryptów</span><span class="sxs-lookup"><span data-stu-id="0b353-102">Script Tracing and Logging</span></span>

<span data-ttu-id="0b353-103">Gdy już programu Windows PowerShell **LogPipelineExecutionDetails** zasad grupy ustawień dziennika wywołanie polecenia cmdlet, język skryptów programu PowerShell ma wystarczająco dużo funkcji, które warto rejestrować i/lub inspekcji.</span><span class="sxs-lookup"><span data-stu-id="0b353-103">While Windows PowerShell already has the **LogPipelineExecutionDetails** Group Policy setting to log the invocation of cmdlets, PowerShell’s scripting language has plenty of features that you might want to log and/or audit.</span></span> <span data-ttu-id="0b353-104">Nowa funkcja szczegółowe śledzenie skrypt umożliwia szczegółowe śledzenie i analizy użycia skryptów programu Windows PowerShell w systemie.</span><span class="sxs-lookup"><span data-stu-id="0b353-104">The new Detailed Script Tracing feature lets you enable detailed tracking and analysis of Windows PowerShell scripting use on a system.</span></span> <span data-ttu-id="0b353-105">Po włączeniu skryptu szczegółowe śledzenie, programu Windows PowerShell dzienników wszystkich blokach skryptu w dzienniku zdarzeń ETW **Microsoft-Windows-PowerShell/Operational**.</span><span class="sxs-lookup"><span data-stu-id="0b353-105">After you enable detailed script tracing, Windows PowerShell logs all script blocks to the ETW event log, **Microsoft-Windows-PowerShell/Operational**.</span></span> <span data-ttu-id="0b353-106">Jeśli blok skryptu tworzy innego bloku skryptu (na przykład skrypt, który wywołuje polecenie cmdlet Invoke-Expression w ciągu), również jest rejestrowane tego wynikowy bloku skryptu.</span><span class="sxs-lookup"><span data-stu-id="0b353-106">If a script block creates another script block (for example, a script that calls the Invoke-Expression cmdlet on a string), that resulting script block is logged as well.</span></span>

<span data-ttu-id="0b353-107">Rejestrowanie tych zdarzeń, można włączyć za pomocą **mogą włączyć rejestrowanie programu PowerShell skrypt bloku** ustawienia zasad grupy (w Szablony administracyjne -> składniki Windows -> środowisko Windows PowerShell).</span><span class="sxs-lookup"><span data-stu-id="0b353-107">Logging of these events can be enabled through the **Turn on PowerShell Script Block Logging** Group Policy setting (in Administrative Templates -> Windows Components -> Windows PowerShell).</span></span>

<span data-ttu-id="0b353-108">Dostępne są następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="0b353-108">The events are:</span></span>

| <span data-ttu-id="0b353-109">Kanał</span><span class="sxs-lookup"><span data-stu-id="0b353-109">Channel</span></span> | <span data-ttu-id="0b353-110">Operacyjne</span><span class="sxs-lookup"><span data-stu-id="0b353-110">Operational</span></span>                                 |
|---------|---------------------------------------------|
| <span data-ttu-id="0b353-111">Poziom</span><span class="sxs-lookup"><span data-stu-id="0b353-111">Level</span></span>   | <span data-ttu-id="0b353-112">Pełny</span><span class="sxs-lookup"><span data-stu-id="0b353-112">Verbose</span></span>                                     |
| <span data-ttu-id="0b353-113">OpCode</span><span class="sxs-lookup"><span data-stu-id="0b353-113">Opcode</span></span>  | <span data-ttu-id="0b353-114">Utworzenie</span><span class="sxs-lookup"><span data-stu-id="0b353-114">Create</span></span>                                      |
| <span data-ttu-id="0b353-115">Zadanie</span><span class="sxs-lookup"><span data-stu-id="0b353-115">Task</span></span>    | <span data-ttu-id="0b353-116">CommandStart</span><span class="sxs-lookup"><span data-stu-id="0b353-116">CommandStart</span></span>                                |
| <span data-ttu-id="0b353-117">Słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="0b353-117">Keyword</span></span> | <span data-ttu-id="0b353-118">obszar działania</span><span class="sxs-lookup"><span data-stu-id="0b353-118">Runspace</span></span>                                    |
| <span data-ttu-id="0b353-119">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="0b353-119">EventId</span></span> | <span data-ttu-id="0b353-120">Engine_ScriptBlockCompiled (0x1008 = 4104)</span><span class="sxs-lookup"><span data-stu-id="0b353-120">Engine_ScriptBlockCompiled (0x1008 = 4104)</span></span>  |
| <span data-ttu-id="0b353-121">Wiadomość</span><span class="sxs-lookup"><span data-stu-id="0b353-121">Message</span></span> | <span data-ttu-id="0b353-122">Tworzenie tekstu Scriptblock (%1 %2):</span><span class="sxs-lookup"><span data-stu-id="0b353-122">Creating Scriptblock text (%1 of %2):</span></span> </br> <span data-ttu-id="0b353-123">%3</span><span class="sxs-lookup"><span data-stu-id="0b353-123">%3</span></span> </br> <span data-ttu-id="0b353-124">Blok skryptu, identyfikator: %4</span><span class="sxs-lookup"><span data-stu-id="0b353-124">ScriptBlock ID: %4</span></span> |


<span data-ttu-id="0b353-125">Tekst osadzony w wiadomości znajduje się w zakresie bloku skryptu skompilowany.</span><span class="sxs-lookup"><span data-stu-id="0b353-125">The text embedded in the message is the extent of the script block compiled.</span></span> <span data-ttu-id="0b353-126">Identyfikator jest identyfikatorem GUID, który został zachowany na potrzeby cyklu życia w bloku skryptu.</span><span class="sxs-lookup"><span data-stu-id="0b353-126">The ID is a GUID that is retained for the life of the script block.</span></span>

<span data-ttu-id="0b353-127">Po włączeniu pełnego rejestrowania, zapisuje funkcji początku i końcu znaczniki:</span><span class="sxs-lookup"><span data-stu-id="0b353-127">When you enable verbose logging, the feature writes begin and end markers:</span></span>

| <span data-ttu-id="0b353-128">Kanał</span><span class="sxs-lookup"><span data-stu-id="0b353-128">Channel</span></span> | <span data-ttu-id="0b353-129">Operacyjne</span><span class="sxs-lookup"><span data-stu-id="0b353-129">Operational</span></span>                                            |
|---------|--------------------------------------------------------|
| <span data-ttu-id="0b353-130">Poziom</span><span class="sxs-lookup"><span data-stu-id="0b353-130">Level</span></span>   | <span data-ttu-id="0b353-131">Pełny</span><span class="sxs-lookup"><span data-stu-id="0b353-131">Verbose</span></span>                                                |
| <span data-ttu-id="0b353-132">OpCode</span><span class="sxs-lookup"><span data-stu-id="0b353-132">Opcode</span></span>  | <span data-ttu-id="0b353-133">Otwórz (/ zamykanie)</span><span class="sxs-lookup"><span data-stu-id="0b353-133">Open (/ Close)</span></span>                                         |
| <span data-ttu-id="0b353-134">Zadanie</span><span class="sxs-lookup"><span data-stu-id="0b353-134">Task</span></span>    | <span data-ttu-id="0b353-135">CommandStart (/ CommandStop)</span><span class="sxs-lookup"><span data-stu-id="0b353-135">CommandStart (/ CommandStop)</span></span>                           |
| <span data-ttu-id="0b353-136">Słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="0b353-136">Keyword</span></span> | <span data-ttu-id="0b353-137">obszar działania</span><span class="sxs-lookup"><span data-stu-id="0b353-137">Runspace</span></span>                                               |
| <span data-ttu-id="0b353-138">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="0b353-138">EventId</span></span> | <span data-ttu-id="0b353-139">Blok skryptu\_wywołania\_Start\_szczegółów (0x1009 = 4105) /</span><span class="sxs-lookup"><span data-stu-id="0b353-139">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span></span> </br> <span data-ttu-id="0b353-140">Blok skryptu\_wywołania\_pełną\_szczegółów (0x100A = 4106)</span><span class="sxs-lookup"><span data-stu-id="0b353-140">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span></span> |
| <span data-ttu-id="0b353-141">Wiadomość</span><span class="sxs-lookup"><span data-stu-id="0b353-141">Message</span></span> | <span data-ttu-id="0b353-142">Wprowadzenie (/ ukończone) wywołanie ScriptBlock identyfikator: %1</span><span class="sxs-lookup"><span data-stu-id="0b353-142">Started (/ Completed) invocation of ScriptBlock ID: %1</span></span> </br> <span data-ttu-id="0b353-143">Identyfikator działania: %2</span><span class="sxs-lookup"><span data-stu-id="0b353-143">Runspace ID: %2</span></span> |

<span data-ttu-id="0b353-144">Identyfikator jest identyfikator GUID reprezentujący blok skryptu, (które mogą zostać skorelowane zdarzenia o identyfikatorze 0x1008) i identyfikator obszaru działania reprezentuje obszar działania, w którym uruchomiono ten blok skryptu.</span><span class="sxs-lookup"><span data-stu-id="0b353-144">The ID is the GUID representing the script block (that can be correlated with event ID 0x1008), and the Runspace ID represents the runspace in which this script block was run.</span></span>

<span data-ttu-id="0b353-145">Procentu w komunikacie wywołania reprezentują ze strukturą właściwości funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="0b353-145">Percent signs in the invocation message represent structured ETW properties.</span></span> <span data-ttu-id="0b353-146">Zostaną zastąpione rzeczywistymi wartościami w tekście komunikatu bardziej niezawodny sposób dostępu do nich polega na pobieranie komunikatów za pomocą polecenia cmdlet Get-WinEvent, a następnie użyj **właściwości** tablicy wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0b353-146">While they are replaced with the actual values in the message text, a more robust way to access them is to retrieve the message with the Get-WinEvent cmdlet, and then use the **Properties** array of the message.</span></span>

<span data-ttu-id="0b353-147">Oto przykład jak ta funkcja może pomóc Odkodowywanie złośliwe próby do szyfrowania i zaciemniania skryptu:</span><span class="sxs-lookup"><span data-stu-id="0b353-147">Here's an example of how this functionality can help unwrap a malicious attempt to encrypt and obfuscate a script:</span></span>

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

<span data-ttu-id="0b353-148">Uruchomiony generuje następujące wpisy dziennika:</span><span class="sxs-lookup"><span data-stu-id="0b353-148">Running this generates the following log entries:</span></span>

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

Jeśli długość bloku skryptu przekracza, co jest zdolny do akcji w pojedyncze zdarzenie ETW, skrypt programu Windows PowerShell dzieli się na wiele części. <span data-ttu-id="0b353-150">Poniżej przedstawiono przykładowy kod służący do ponownego połączenia skryptu z jego komunikaty dziennika:</span><span class="sxs-lookup"><span data-stu-id="0b353-150">Here is sample code to recombine a script from its log messages:</span></span>

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } | Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

<span data-ttu-id="0b353-151">Podobnie jak w przypadku wszystkich systemów rejestrowania, masz bufora ograniczone przechowywania (np. dzienniki zdarzeń systemu Windows), co ataku tej infrastruktury jest zalać dziennika ze zdarzeniami fałszywe, aby ukryć dowód wcześniej.</span><span class="sxs-lookup"><span data-stu-id="0b353-151">As with all logging systems that have a limited retention buffer (i.e. ETW logs), one attack against this infrastructure is to flood the log with spurious events to hide earlier evidence.</span></span> <span data-ttu-id="0b353-152">Aby zabezpieczyć się przed tego rodzaju atak, upewnij się, że pewnego rodzaju skonfigurować zbieranie danych dziennika zdarzeń (czyli Windows funkcji przekazywania zdarzeń, [dotyczące Osoba planująca atak przy użyciu funkcji monitorowania dziennika zdarzeń Windows](https://www.iad.gov/iad/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm)) przenieść dzienniki zdarzeń się komputera jako najszybciej, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="0b353-152">To protect yourself from this attack, ensure that you have some form of event log collection set up (i.e., Windows Event Forwarding, [Spotting the Adversary with Windows Event Log Monitoring](https://www.iad.gov/iad/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm)) to move event logs off of the computer as soon as possible.</span></span>
