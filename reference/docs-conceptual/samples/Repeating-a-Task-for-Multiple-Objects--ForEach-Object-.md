---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Powtarzanie zadania dla wielu obiektów ForEach obiektu
ms.openlocfilehash: 1442507c4213476f65df3401c1021f8d0fc31956
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030805"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a>Powtarzanie zadania dla wielu obiektów (ForEach-Object)

**ForEach-Object** polecenie cmdlet używa Bloki skryptu i `$_` deskryptora dla bieżącego obiektu potoku umożliwić, możesz uruchomić polecenie dla każdego obiektu w potoku. Może to służyć do wykonania niektórych zadań skomplikowane.

Jedna sytuacja, w których może to być przydatne jest manipulowanie danymi, aby zwiększyć jej użyteczność. Na przykład Klasa Win32_LogicalDisk WMI może służyć do zwracania informacji wolnego miejsca dla każdego dysku lokalnego. Dane są zwracane się pod względem bajtów, ale, co czyni go trudno odczytać:

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

Możemy przekonwertować wartości FreeSpace megabajtów przez podzielenie każdej wartości przez 1024 dwukrotnie; Po wykonaniu dzielenia pierwszego dane znajdują się w kilobajtach, a po wykonaniu dzielenia drugi jest w megabajtach. Możesz to zrobić w bloku skryptu ForEach-Object, wpisując:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

Niestety dane wyjściowe są teraz danych bez skojarzonych etykiety. Ponieważ właściwości usługi WMI, takie jak to tylko do odczytu, nie można bezpośrednio przekonwertować FreeSpace. Jeśli wpiszesz to:

```powershell
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

Otrzymasz komunikat o błędzie:

```output
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

Dane można uporządkować przy użyciu kilka zaawansowanych technik, ale jest prostszej metody, aby utworzyć nowy obiekt, za pomocą **Select-Object**.
