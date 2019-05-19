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
# <a name="information-stream"></a><span data-ttu-id="f4119-103">Strumień informacji</span><span class="sxs-lookup"><span data-stu-id="f4119-103">Information Stream</span></span>

<span data-ttu-id="f4119-104">PowerShell 5.0 dodaje nową strukturę **informacji** strumienia do przesyłania danych ze strukturą między skryptu i jej hosta.</span><span class="sxs-lookup"><span data-stu-id="f4119-104">PowerShell 5.0 adds a new structured **Information** stream to transmit structured data between a script and its host.</span></span> <span data-ttu-id="f4119-105">`Write-Host` został także zaktualizowany i emitowanie jej dane wyjściowe do **informacji** strumienia, w którym można teraz przechwytywania lub wyciszyć go.</span><span class="sxs-lookup"><span data-stu-id="f4119-105">`Write-Host` has also been updated to emit its output to the **Information** stream where you can now capture or silence it.</span></span> <span data-ttu-id="f4119-106">Nowy `Write-Information` używane z polecenia cmdlet **InformationVariable** i **InformationAction** wspólnych parametrów zapewnia większą elastyczność i możliwości.</span><span class="sxs-lookup"><span data-stu-id="f4119-106">The new `Write-Information` cmdlet used with **InformationVariable** and **InformationAction** common parameters enables more flexibility and capability.</span></span>

<span data-ttu-id="f4119-107">Następująca funkcja korzysta z polecenia cmdlet, które zalet nowego **informacji** strumienia.</span><span class="sxs-lookup"><span data-stu-id="f4119-107">The following function uses cmdlets that take advantage of the new **Information** stream.</span></span>

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

<span data-ttu-id="f4119-108">Poniższe przykłady pokazują wyniki działania tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="f4119-108">The following examples show the results of running this function.</span></span>

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

<span data-ttu-id="f4119-109">`$r` Zmiennej został przechwycony przetwarzać informacje w zmiennej skryptu `$p`.</span><span class="sxs-lookup"><span data-stu-id="f4119-109">The `$r` variable has captured the process information in the script variable `$p`.</span></span>

```powershell
$r.Id
4008
```

<span data-ttu-id="f4119-110">W odróżnieniu od `Write-Host` polecenia cmdlet, za pomocą **InformationVariable** parametru `Write-Information` umożliwia przechwytywanie danych wyjściowych w zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f4119-110">Unlike the `Write-Host` cmdlet, using the **InformationVariable** parameter of `Write-Information` allows you to capture the output in a variable.</span></span> <span data-ttu-id="f4119-111">Za pomocą **Tag**, można utworzyć osobny kanał dla komunikatu wysłanego do **informacji** strumienia.</span><span class="sxs-lookup"><span data-stu-id="f4119-111">Using the **Tag**, you can create separate channels for message sent to the **Information** stream.</span></span>

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

<span data-ttu-id="f4119-112">Podczas wysyłania wiadomości do **informacji** strumienia za pomocą tagów, a ten komunikat nie jest wyświetlany w aplikacji hosta, ale można pobrać przy użyciu nazwy tagu.</span><span class="sxs-lookup"><span data-stu-id="f4119-112">When you send a message to the **Information** stream with a tag, that message is not displayed in the host application but can be retrieved using the tag name.</span></span> <span data-ttu-id="f4119-113">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f4119-113">For example:</span></span>

```powershell
$iv | where Tags -eq 'LogHigh'
```

```Output
Some important logging information
```