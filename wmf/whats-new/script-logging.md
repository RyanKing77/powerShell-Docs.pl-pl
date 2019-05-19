---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Śledzenie i rejestrowanie skryptów
ms.openlocfilehash: 6b7e5022cb4c974da5ddb3d670b5808dc9fb7bdc
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856154"
---
# <a name="script-tracing-and-logging"></a><span data-ttu-id="e9c9f-103">Śledzenie i rejestrowanie skryptów</span><span class="sxs-lookup"><span data-stu-id="e9c9f-103">Script Tracing and Logging</span></span>

<span data-ttu-id="e9c9f-104">Gdy program PowerShell jest już **LogPipelineExecutionDetails** zasad grupy ustawień dziennika wywołanie polecenia cmdlet, język skryptów programu PowerShell ma kilka funkcji, które możesz chcieć logowania i inspekcji.</span><span class="sxs-lookup"><span data-stu-id="e9c9f-104">While PowerShell already has the **LogPipelineExecutionDetails** Group Policy setting to log the invocation of cmdlets, PowerShell's scripting language has several features that you might want to log and audit.</span></span> <span data-ttu-id="e9c9f-105">Nowa funkcja szczegółowe śledzenie skrypt zawiera szczegółowe śledzenie i analizy działania skryptu programu PowerShell w systemie.</span><span class="sxs-lookup"><span data-stu-id="e9c9f-105">The new Detailed Script Tracing feature provides detailed tracking and analysis of PowerShell script activity on a system.</span></span> <span data-ttu-id="e9c9f-106">Po włączeniu śledzenia szczegółowy skrypt programu PowerShell rejestruje w dzienniku zdarzeń ETW wszystkich blokach skryptu **Microsoft-Windows-PowerShell/Operational**.</span><span class="sxs-lookup"><span data-stu-id="e9c9f-106">After enabling detailed script tracing, PowerShell logs all script blocks to the ETW event log, **Microsoft-Windows-PowerShell/Operational**.</span></span> <span data-ttu-id="e9c9f-107">Jeśli blok skryptu tworzy innego bloku skryptu, na przykład przez wywołanie metody `Invoke-Expression`, blok skryptu wywoływana również rejestrowana.</span><span class="sxs-lookup"><span data-stu-id="e9c9f-107">If a script block creates another script block, for example, by calling `Invoke-Expression`, the invoked script block also logged.</span></span>

<span data-ttu-id="e9c9f-108">Rejestrowanie jest włączone za pomocą **mogą włączyć rejestrowanie programu PowerShell skrypt bloku** ustawienie zasad grupy w **Szablony administracyjne** -> **składników Windows**  ->  **Programu Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="e9c9f-108">Logging is enabled through the **Turn on PowerShell Script Block Logging** Group Policy setting in **Administrative Templates** -> **Windows Components** -> **Windows PowerShell**.</span></span>

<span data-ttu-id="e9c9f-109">Dostępne są następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="e9c9f-109">The events are:</span></span>

| <span data-ttu-id="e9c9f-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="e9c9f-110">Channel</span></span> |                               <span data-ttu-id="e9c9f-111">Operacyjne</span><span class="sxs-lookup"><span data-stu-id="e9c9f-111">Operational</span></span>                               |
| ------- | ----------------------------------------------------------------------- |
| <span data-ttu-id="e9c9f-112">Poziom</span><span class="sxs-lookup"><span data-stu-id="e9c9f-112">Level</span></span>   | <span data-ttu-id="e9c9f-113">Verbose</span><span class="sxs-lookup"><span data-stu-id="e9c9f-113">Verbose</span></span>                                                                 |
| <span data-ttu-id="e9c9f-114">OpCode</span><span class="sxs-lookup"><span data-stu-id="e9c9f-114">Opcode</span></span>  | <span data-ttu-id="e9c9f-115">Utworzenie</span><span class="sxs-lookup"><span data-stu-id="e9c9f-115">Create</span></span>                                                                  |
| <span data-ttu-id="e9c9f-116">Zadanie</span><span class="sxs-lookup"><span data-stu-id="e9c9f-116">Task</span></span>    | <span data-ttu-id="e9c9f-117">CommandStart</span><span class="sxs-lookup"><span data-stu-id="e9c9f-117">CommandStart</span></span>                                                            |
| <span data-ttu-id="e9c9f-118">Słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="e9c9f-118">Keyword</span></span> | <span data-ttu-id="e9c9f-119">obszar działania</span><span class="sxs-lookup"><span data-stu-id="e9c9f-119">Runspace</span></span>                                                                |
| <span data-ttu-id="e9c9f-120">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="e9c9f-120">EventId</span></span> | <span data-ttu-id="e9c9f-121">Engine_ScriptBlockCompiled (0x1008 = 4104)</span><span class="sxs-lookup"><span data-stu-id="e9c9f-121">Engine_ScriptBlockCompiled (0x1008 = 4104)</span></span>                              |
| <span data-ttu-id="e9c9f-122">Wiadomość</span><span class="sxs-lookup"><span data-stu-id="e9c9f-122">Message</span></span> | <span data-ttu-id="e9c9f-123">Tworzenie tekstu Scriptblock (%1 %2):</span><span class="sxs-lookup"><span data-stu-id="e9c9f-123">Creating Scriptblock text (%1 of %2):</span></span> </br> <span data-ttu-id="e9c9f-124">%3</span><span class="sxs-lookup"><span data-stu-id="e9c9f-124">%3</span></span> </br> <span data-ttu-id="e9c9f-125">Blok skryptu, identyfikator: %4</span><span class="sxs-lookup"><span data-stu-id="e9c9f-125">ScriptBlock ID: %4</span></span> |


<span data-ttu-id="e9c9f-126">Tekst osadzony w wiadomości znajduje się w zakresie bloku skryptu skompilowany.</span><span class="sxs-lookup"><span data-stu-id="e9c9f-126">The text embedded in the message is the extent of the script block compiled.</span></span> <span data-ttu-id="e9c9f-127">Identyfikator jest identyfikatorem GUID, który został zachowany na potrzeby cyklu życia w bloku skryptu.</span><span class="sxs-lookup"><span data-stu-id="e9c9f-127">The ID is a GUID that is retained for the life of the script block.</span></span>

<span data-ttu-id="e9c9f-128">Po włączeniu pełnego rejestrowania, zapisuje funkcji początku i końcu znaczniki:</span><span class="sxs-lookup"><span data-stu-id="e9c9f-128">When you enable verbose logging, the feature writes begin and end markers:</span></span>

| <span data-ttu-id="e9c9f-129">Kanał</span><span class="sxs-lookup"><span data-stu-id="e9c9f-129">Channel</span></span> |                                 <span data-ttu-id="e9c9f-130">Operacyjne</span><span class="sxs-lookup"><span data-stu-id="e9c9f-130">Operational</span></span>                                |
| ------- | -------------------------------------------------------------------------- |
| <span data-ttu-id="e9c9f-131">Poziom</span><span class="sxs-lookup"><span data-stu-id="e9c9f-131">Level</span></span>   | <span data-ttu-id="e9c9f-132">Verbose</span><span class="sxs-lookup"><span data-stu-id="e9c9f-132">Verbose</span></span>                                                                    |
| <span data-ttu-id="e9c9f-133">OpCode</span><span class="sxs-lookup"><span data-stu-id="e9c9f-133">Opcode</span></span>  | <span data-ttu-id="e9c9f-134">Otwórz / Zamknij</span><span class="sxs-lookup"><span data-stu-id="e9c9f-134">Open / Close</span></span>                                                               |
| <span data-ttu-id="e9c9f-135">Zadanie</span><span class="sxs-lookup"><span data-stu-id="e9c9f-135">Task</span></span>    | <span data-ttu-id="e9c9f-136">CommandStart / CommandStop</span><span class="sxs-lookup"><span data-stu-id="e9c9f-136">CommandStart / CommandStop</span></span>                                                 |
| <span data-ttu-id="e9c9f-137">Słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="e9c9f-137">Keyword</span></span> | <span data-ttu-id="e9c9f-138">obszar działania</span><span class="sxs-lookup"><span data-stu-id="e9c9f-138">Runspace</span></span>                                                                   |
| <span data-ttu-id="e9c9f-139">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="e9c9f-139">EventId</span></span> | <span data-ttu-id="e9c9f-140">Blok skryptu\_wywołania\_Start\_szczegółów (0x1009 = 4105) /</span><span class="sxs-lookup"><span data-stu-id="e9c9f-140">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span></span> </br> <span data-ttu-id="e9c9f-141">Blok skryptu\_wywołania\_pełną\_szczegółów (0x100A = 4106)</span><span class="sxs-lookup"><span data-stu-id="e9c9f-141">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span></span> |
| <span data-ttu-id="e9c9f-142">Wiadomość</span><span class="sxs-lookup"><span data-stu-id="e9c9f-142">Message</span></span> | <span data-ttu-id="e9c9f-143">Pracę / ukończone wywołania ScriptBlock identyfikator: %1</span><span class="sxs-lookup"><span data-stu-id="e9c9f-143">Started / Completed invocation of ScriptBlock ID: %1</span></span> </br> <span data-ttu-id="e9c9f-144">Identyfikator działania: %2</span><span class="sxs-lookup"><span data-stu-id="e9c9f-144">Runspace ID: %2</span></span> |

<span data-ttu-id="e9c9f-145">Identyfikator jest identyfikator GUID reprezentujący blok skryptu, (które mogą zostać skorelowane zdarzenia o identyfikatorze 0x1008) i identyfikator obszaru działania reprezentuje obszar działania, w którym uruchomiono ten blok skryptu.</span><span class="sxs-lookup"><span data-stu-id="e9c9f-145">The ID is the GUID representing the script block (that can be correlated with event ID 0x1008), and the Runspace ID represents the runspace in which this script block was run.</span></span>

<span data-ttu-id="e9c9f-146">Procentu w komunikacie wywołania reprezentują ze strukturą właściwości funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="e9c9f-146">Percent signs in the invocation message represent structured ETW properties.</span></span> <span data-ttu-id="e9c9f-147">Zostaną zastąpione rzeczywistymi wartościami w tekście komunikatu bardziej niezawodny sposób dostępu do nich polega na pobieranie komunikatów za pomocą polecenia cmdlet Get-WinEvent, a następnie użyj **właściwości** tablicy wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e9c9f-147">While they are replaced with the actual values in the message text, a more robust way to access them is to retrieve the message with the Get-WinEvent cmdlet, and then use the **Properties** array of the message.</span></span>

<span data-ttu-id="e9c9f-148">Oto przykład jak ta funkcja może pomóc Odkodowywanie złośliwe próby do szyfrowania i zaciemniania skryptu:</span><span class="sxs-lookup"><span data-stu-id="e9c9f-148">Here's an example of how this functionality can help unwrap a malicious attempt to encrypt and obfuscate a script:</span></span>

```powershell
## Malware
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

$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
Invoke-Expression $decrypted
```

<span data-ttu-id="e9c9f-149">Uruchomiony generuje następujące wpisy dziennika:</span><span class="sxs-lookup"><span data-stu-id="e9c9f-149">Running this generates the following log entries:</span></span>

```Output
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

Jeśli długość bloku skryptu przekracza pojemność to pojedyncze zdarzenie, skrypt programu PowerShell dzieli się na wiele części. <span data-ttu-id="e9c9f-151">Poniżej przedstawiono przykładowy kod służący do ponownego połączenia skryptu z jego komunikaty dziennika:</span><span class="sxs-lookup"><span data-stu-id="e9c9f-151">Here is sample code to recombine a script from its log messages:</span></span>

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } |
  Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

<span data-ttu-id="e9c9f-152">Podobnie jak w przypadku wszystkich systemów rejestrowania, masz bufora przechowywania ograniczone, jednym ze sposobów na ataki tej infrastruktury jest zalać dziennika ze zdarzeniami fałszywe, aby ukryć dowód wcześniej.</span><span class="sxs-lookup"><span data-stu-id="e9c9f-152">As with all logging systems that have a limited retention buffer, one way to attack this infrastructure is to flood the log with spurious events to hide earlier evidence.</span></span> <span data-ttu-id="e9c9f-153">Aby zabezpieczyć się przed tego rodzaju atak, upewnij się, że pewnego rodzaju zbieranie dzienników zdarzeń, konfigurowanie funkcji przekazywania zdarzeń Windows.</span><span class="sxs-lookup"><span data-stu-id="e9c9f-153">To protect yourself from this attack, ensure that you have some form of event log collection set up Windows Event Forwarding.</span></span> <span data-ttu-id="e9c9f-154">Aby uzyskać więcej informacji, zobacz [dotyczące Osoba planująca atak przy użyciu funkcji monitorowania dziennika zdarzeń Windows](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm).</span><span class="sxs-lookup"><span data-stu-id="e9c9f-154">For more information, see [Spotting the Adversary with Windows Event Log Monitoring](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm).</span></span>