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
# <a name="script-tracing-and-logging"></a>Śledzenie i rejestrowanie skryptów

Gdy program PowerShell jest już **LogPipelineExecutionDetails** zasad grupy ustawień dziennika wywołanie polecenia cmdlet, język skryptów programu PowerShell ma kilka funkcji, które możesz chcieć logowania i inspekcji. Nowa funkcja szczegółowe śledzenie skrypt zawiera szczegółowe śledzenie i analizy działania skryptu programu PowerShell w systemie. Po włączeniu śledzenia szczegółowy skrypt programu PowerShell rejestruje w dzienniku zdarzeń ETW wszystkich blokach skryptu **Microsoft-Windows-PowerShell/Operational**. Jeśli blok skryptu tworzy innego bloku skryptu, na przykład przez wywołanie metody `Invoke-Expression`, blok skryptu wywoływana również rejestrowana.

Rejestrowanie jest włączone za pomocą **mogą włączyć rejestrowanie programu PowerShell skrypt bloku** ustawienie zasad grupy w **Szablony administracyjne** -> **składników Windows**  ->  **Programu Windows PowerShell**.

Dostępne są następujące zdarzenia:

| Kanał |                               Operacyjne                               |
| ------- | ----------------------------------------------------------------------- |
| Poziom   | Verbose                                                                 |
| OpCode  | Utworzenie                                                                  |
| Zadanie    | CommandStart                                                            |
| Słowo kluczowe | obszar działania                                                                |
| Identyfikator zdarzenia | Engine_ScriptBlockCompiled (0x1008 = 4104)                              |
| Wiadomość | Tworzenie tekstu Scriptblock (%1 %2): </br> %3 </br> Blok skryptu, identyfikator: %4 |


Tekst osadzony w wiadomości znajduje się w zakresie bloku skryptu skompilowany. Identyfikator jest identyfikatorem GUID, który został zachowany na potrzeby cyklu życia w bloku skryptu.

Po włączeniu pełnego rejestrowania, zapisuje funkcji początku i końcu znaczniki:

| Kanał |                                 Operacyjne                                |
| ------- | -------------------------------------------------------------------------- |
| Poziom   | Verbose                                                                    |
| OpCode  | Otwórz / Zamknij                                                               |
| Zadanie    | CommandStart / CommandStop                                                 |
| Słowo kluczowe | obszar działania                                                                   |
| Identyfikator zdarzenia | Blok skryptu\_wywołania\_Start\_szczegółów (0x1009 = 4105) / </br> Blok skryptu\_wywołania\_pełną\_szczegółów (0x100A = 4106) |
| Wiadomość | Pracę / ukończone wywołania ScriptBlock identyfikator: %1 </br> Identyfikator działania: %2 |

Identyfikator jest identyfikator GUID reprezentujący blok skryptu, (które mogą zostać skorelowane zdarzenia o identyfikatorze 0x1008) i identyfikator obszaru działania reprezentuje obszar działania, w którym uruchomiono ten blok skryptu.

Procentu w komunikacie wywołania reprezentują ze strukturą właściwości funkcji ETW. Zostaną zastąpione rzeczywistymi wartościami w tekście komunikatu bardziej niezawodny sposób dostępu do nich polega na pobieranie komunikatów za pomocą polecenia cmdlet Get-WinEvent, a następnie użyj **właściwości** tablicy wiadomości.

Oto przykład jak ta funkcja może pomóc Odkodowywanie złośliwe próby do szyfrowania i zaciemniania skryptu:

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

Uruchomiony generuje następujące wpisy dziennika:

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

Jeśli długość bloku skryptu przekracza pojemność to pojedyncze zdarzenie, skrypt programu PowerShell dzieli się na wiele części. Poniżej przedstawiono przykładowy kod służący do ponownego połączenia skryptu z jego komunikaty dziennika:

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } |
  Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

Podobnie jak w przypadku wszystkich systemów rejestrowania, masz bufora przechowywania ograniczone, jednym ze sposobów na ataki tej infrastruktury jest zalać dziennika ze zdarzeniami fałszywe, aby ukryć dowód wcześniej. Aby zabezpieczyć się przed tego rodzaju atak, upewnij się, że pewnego rodzaju zbieranie dzienników zdarzeń, konfigurowanie funkcji przekazywania zdarzeń Windows. Aby uzyskać więcej informacji, zobacz [dotyczące Osoba planująca atak przy użyciu funkcji monitorowania dziennika zdarzeń Windows](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm).