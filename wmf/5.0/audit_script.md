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
# <a name="script-tracing-and-logging"></a>Śledzenie i rejestrowanie skryptów

Gdy już programu Windows PowerShell **LogPipelineExecutionDetails** zasad grupy ustawień dziennika wywołanie polecenia cmdlet, język skryptów programu PowerShell ma wystarczająco dużo funkcji, które warto rejestrować i/lub inspekcji. Nowa funkcja szczegółowe śledzenie skrypt umożliwia szczegółowe śledzenie i analizy użycia skryptów programu Windows PowerShell w systemie. Po włączeniu skryptu szczegółowe śledzenie, programu Windows PowerShell dzienników wszystkich blokach skryptu w dzienniku zdarzeń ETW **Microsoft-Windows-PowerShell/Operational**. Jeśli blok skryptu tworzy innego bloku skryptu (na przykład skrypt, który wywołuje polecenie cmdlet Invoke-Expression w ciągu), również jest rejestrowane tego wynikowy bloku skryptu.

Rejestrowanie tych zdarzeń, można włączyć za pomocą **mogą włączyć rejestrowanie programu PowerShell skrypt bloku** ustawienia zasad grupy (w Szablony administracyjne -> składniki Windows -> środowisko Windows PowerShell).

Dostępne są następujące zdarzenia:

| Kanał | Operacyjne                                 |
|---------|---------------------------------------------|
| Poziom   | Pełny                                     |
| OpCode  | Utworzenie                                      |
| Zadanie    | CommandStart                                |
| Słowo kluczowe | obszar działania                                    |
| Identyfikator zdarzenia | Engine_ScriptBlockCompiled (0x1008 = 4104)  |
| Wiadomość | Tworzenie tekstu Scriptblock (%1 %2): </br> %3 </br> Blok skryptu, identyfikator: %4 |


Tekst osadzony w wiadomości znajduje się w zakresie bloku skryptu skompilowany. Identyfikator jest identyfikatorem GUID, który został zachowany na potrzeby cyklu życia w bloku skryptu.

Po włączeniu pełnego rejestrowania, zapisuje funkcji początku i końcu znaczniki:

| Kanał | Operacyjne                                            |
|---------|--------------------------------------------------------|
| Poziom   | Pełny                                                |
| OpCode  | Otwórz (/ zamykanie)                                         |
| Zadanie    | CommandStart (/ CommandStop)                           |
| Słowo kluczowe | obszar działania                                               |
| Identyfikator zdarzenia | Blok skryptu\_wywołania\_Start\_szczegółów (0x1009 = 4105) / </br> Blok skryptu\_wywołania\_pełną\_szczegółów (0x100A = 4106) |
| Wiadomość | Wprowadzenie (/ ukończone) wywołanie ScriptBlock identyfikator: %1 </br> Identyfikator działania: %2 |

Identyfikator jest identyfikator GUID reprezentujący blok skryptu, (które mogą zostać skorelowane zdarzenia o identyfikatorze 0x1008) i identyfikator obszaru działania reprezentuje obszar działania, w którym uruchomiono ten blok skryptu.

Procentu w komunikacie wywołania reprezentują ze strukturą właściwości funkcji ETW. Zostaną zastąpione rzeczywistymi wartościami w tekście komunikatu bardziej niezawodny sposób dostępu do nich polega na pobieranie komunikatów za pomocą polecenia cmdlet Get-WinEvent, a następnie użyj **właściwości** tablicy wiadomości.

Oto przykład jak ta funkcja może pomóc Odkodowywanie złośliwe próby do szyfrowania i zaciemniania skryptu:

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

Uruchomiony generuje następujące wpisy dziennika:

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

Jeśli długość bloku skryptu przekracza, co jest zdolny do akcji w pojedyncze zdarzenie ETW, skrypt programu Windows PowerShell dzieli się na wiele części. Poniżej przedstawiono przykładowy kod służący do ponownego połączenia skryptu z jego komunikaty dziennika:

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } | Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

Podobnie jak w przypadku wszystkich systemów rejestrowania, masz bufora ograniczone przechowywania (np. dzienniki zdarzeń systemu Windows), co ataku tej infrastruktury jest zalać dziennika ze zdarzeniami fałszywe, aby ukryć dowód wcześniej. Aby zabezpieczyć się przed tego rodzaju atak, upewnij się, że pewnego rodzaju skonfigurować zbieranie danych dziennika zdarzeń (czyli Windows funkcji przekazywania zdarzeń, [dotyczące Osoba planująca atak przy użyciu funkcji monitorowania dziennika zdarzeń Windows](https://www.iad.gov/iad/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm)) przenieść dzienniki zdarzeń się komputera jako najszybciej, jak to możliwe.
