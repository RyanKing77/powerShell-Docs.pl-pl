---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Strumień informacji
ms.openlocfilehash: c54603cf0dd4f0b69f8147620130f9f29bc3e5ec
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856385"
---
# <a name="information-stream"></a>Strumień informacji

PowerShell 5.0 dodaje nową strukturę **informacji** strumienia do przesyłania danych ze strukturą między skryptu i jej hosta. `Write-Host` został także zaktualizowany i emitowanie jej dane wyjściowe do **informacji** strumienia, w którym można teraz przechwytywania lub wyciszyć go. Nowy `Write-Information` używane z polecenia cmdlet **InformationVariable** i **InformationAction** wspólnych parametrów zapewnia większą elastyczność i możliwości.

Następująca funkcja korzysta z polecenia cmdlet, które zalet nowego **informacji** strumienia.

```powershell
function OutputGusher {
  [CmdletBinding()]
  param()
  Write-Host -ForegroundColor Green 'Preparing to give you output!'
  Write-Host '============================='
  Write-Host 'I ' -ForegroundColor White -NoNewline
  Write-Host '<3 ' -ForegroundColor Red -NoNewline
  Write-Host 'Output' -ForegroundColor White
  Write-Host '============================='

  $p = Get-Process -id $pid
  $p

  Write-Information $p -Tag Process
  Write-Information 'Some spammy logging information' -Tag LogLow
  Write-Information 'Some important logging information' -Tag LogHigh

  Write-Host
  Write-Host -ForegroundColor Green 'SCRIPT COMPLETE!!'
}
```

Poniższe przykłady pokazują wyniki działania tej funkcji.

```powershell
$r = c:\temp\OutputGusher
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================

SCRIPT COMPLETE!!
```

`$r` Zmiennej został przechwycony przetwarzać informacje w zmiennej skryptu `$p`.

```powershell
$r.Id
4008
```

W odróżnieniu od `Write-Host` polecenia cmdlet, za pomocą **InformationVariable** parametru `Write-Information` umożliwia przechwytywanie danych wyjściowych w zmiennej. Za pomocą **Tag**, można utworzyć osobny kanał dla komunikatu wysłanego do **informacji** strumienia.

```powershell
$r = OutputGusher -InformationVariable iv
$ivOutput = $iv | Group-Object -AsHash { $_.Tags[0] } -AsString
$ivOutput
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================
SCRIPT COMPLETE!!

Name                 Value
----                 -----
LogLow               {Some spammy logging information}
LogHigh              {Some important logging information}
Process              {System.Diagnostics.Process (powershell)}
PSHOST               {Preparing to give you output!, =============================, I , <3 ...}
```

Podczas wysyłania wiadomości do **informacji** strumienia za pomocą tagów, a ten komunikat nie jest wyświetlany w aplikacji hosta, ale można pobrać przy użyciu nazwy tagu. Przykład:

```powershell
$iv | where Tags -eq 'LogHigh'
```

```Output
Some important logging information
```