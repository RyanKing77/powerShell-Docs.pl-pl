---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 2627b9d02788bd31a5384587406df533faf2cfaf
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="script-tracing-and-logging"></a>Śledzenie i rejestrowanie skryptów

Gdy ma już środowiska Windows PowerShell **LogPipelineExecutionDetails** zasad grupy ustawień dziennika wywołanie polecenia cmdlet, język skryptów dla środowiska PowerShell ma wystarczająco dużo funkcje, które możesz chcieć logowania i/lub inspekcji. Nowa funkcja śledzenia szczegółowy skrypt umożliwia szczegółowe śledzenie i analizy użycia skryptów środowiska Windows PowerShell w systemie. Po włączeniu śledzenia szczegółowy skrypt programu Windows PowerShell dzienników wszystkich blokach skryptu w dzienniku zdarzeń ETW **Microsoft-Windows-PowerShell/Operational**. Jeśli blok skryptu tworzy innego bloku skryptu (na przykład skrypt, który wywołuje polecenie cmdlet Invoke-Expression w ciągu), tym wynikowy bloku skryptu jest również rejestrowane.

Rejestrowanie tych zdarzeń można włączyć za pomocą **Włącz rejestrowanie bloku skryptu PowerShell** ustawienia zasad grupy (w Szablony administracyjne -> składniki systemu Windows -> środowiska Windows PowerShell).

Dostępne są następujące zdarzenia:

| Kanał | Operacyjne                                 |
|---------|---------------------------------------------|
| Poziom   | Verbose                                     |
| Kod operacji  | Utworzenie                                      |
| Zadanie    | CommandStart                                |
| Słowo kluczowe | Obszarze działania                                    |
| Identyfikator zdarzenia | Engine_ScriptBlockCompiled (0x1008 = 4104)  |
| Wiadomość | Tworzenie tekstu Scriptblock (%1 z %2): </br> %3 </br> Blok skryptu ID: %4 |


Tekst osadzone w wiadomości jest zakres bloku skryptu skompilowany. Identyfikator jest identyfikatorem GUID, który jest zachowywana przez cały okres istnienia blok skryptu.

Po włączeniu pełnego rejestrowania zapisy funkcji rozpoczęcia i zakończenia znaczników:

| Kanał | Operacyjne                                            |
|---------|--------------------------------------------------------|
| Poziom   | Verbose                                                |
| Kod operacji  | Otwórz (/ zamknięcie)                                         |
| Zadanie    | CommandStart (/ CommandStop)                           |
| Słowo kluczowe | Obszarze działania                                               |
| Identyfikator zdarzenia | Blok skryptu\_wywołania\_Start\_szczegółów (0x1009 = 4105) / </br> Blok skryptu\_wywołania\_pełną\_szczegółów (0x100A = 4106) |
| Wiadomość | Wprowadzenie (/ ukończone) wywołanie ScriptBlock identyfikator: %1 </br> Identyfikator działania: %2 |

Identyfikator to identyfikator GUID reprezentujący bloku skryptu (która może zostać skorelowane zdarzenia o identyfikatorze 0x1008) i identyfikator obszaru działania reprezentuje obszaru działania, w którym uruchomiono ten blok skryptu.

Znaki procentu w komunikat dotyczący wywołania reprezentują strukturalnych właściwości ETW. Gdy są zamieniane na rzeczywiste wartości w treści wiadomości, bardziej niezawodny sposób uzyskiwać do nich dostęp jest pobierania wiadomości za pomocą polecenia cmdlet Get-WinEvent, a następnie użyć **właściwości** tablicy wiadomości.

Oto przykład jak ta funkcja może ułatwić dekodowania złośliwego Próba szyfrowania i zasłaniają skryptu:

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

Uruchomiona generuje następujące wpisy dziennika:

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

Jeśli długość bloku skryptu przekracza co ETW jest w stanie akcji w pojedyncze zdarzenie, skrypt programu Windows PowerShell dzieli się na wielu części. Oto przykładowy kod, aby ponownie połączyć skryptu z jego komunikaty dziennika:

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } | Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

Podobnie jak w przypadku wszystkich systemów rejestrowania mające buforu przechowywania ograniczone (tj. dzienniki zdarzeń systemu Windows), jest jeden atak tej infrastruktury do wypełniania dziennika fałszywe zdarzenia, aby ukryć dowód wcześniej. Aby zabezpieczyć się na ataki, upewnij się, że masz jakiegoś zbierania dzienników zdarzeń — konfiguracja (np. Windows funkcji przekazywania zdarzeń, [analizie atakujący dokonuje monitorowania dziennika zdarzeń systemu Windows z](http://www.nsa.gov/ia/_files/app/Spotting_the_Adversary_with_Windows_Event_Log_Monitoring.pdf)) można przenieść dzienniki zdarzeń wylogowuje na komputerze jako najszybciej, jak to możliwe.
