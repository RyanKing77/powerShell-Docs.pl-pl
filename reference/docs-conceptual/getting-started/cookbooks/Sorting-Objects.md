---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Sortowanie obiektów
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 272d550a67b206f9924ebe143eca2f5906c0a304
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30949982"
---
# <a name="sorting-objects"></a>Sortowanie obiektów

Firma Microsoft organizowanie wyświetlanych danych, aby ułatwić skanowania za pomocą **sortowania obiektu** polecenia cmdlet. **Obiekt sortowania** przyjmuje nazwę jednego lub więcej właściwości do sortowania i zwraca dane posortowane według wartości tych właściwości.

Należy wziąć pod uwagę wyświetlania Win32_SystemDriver wystąpienia problemu. Jeśli chcemy posortować według **stanu** , a następnie według **nazwa**, możemy go, wpisując:

```powershell
Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap
```

Chociaż jest długotrwałą wyświetlania, można wyświetlić elementy z takim samym stanie zgrupowane:

```output
Name           State   Started DisplayName
----           -----   ------- -----------
ACPI           Running    True Microsoft ACPI Driver
AFD            Running    True AFD
AmdK7          Running    True AMD K7 Processor Driver
AsyncMac       Running    True RAS Asynchronous Media Driver
...
Abiosdsk       Stopped   False Abiosdsk
ACPIEC         Stopped   False ACPIEC
aec            Stopped   False Microsoft Kernel Acoustic Echo Canceller
...
```

Możesz także obiekty można sortować w kolejności odwrotnej, określając **malejąco** parametru. Odwraca kolejność sortowania, dzięki czemu nazwy są sortowane w kolejności alfabetycznej odwrotnej i liczby są sortowane według malejących rozmiar.

```
PS> Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name -Descending | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap

Name           State   Started DisplayName
----           -----   ------- -----------
WS2IFSL        Stopped   False Windows Socket 2.0 Non-IFS Service Provider Supp
                               ort Environment
wceusbsh       Stopped   False Windows CE USB Serial Host Driver...
...
wdmaud         Running    True Microsoft WINMM WDM Audio Compatibility Driver
Wanarp         Running    True Remote Access IP ARP Driver
...
```