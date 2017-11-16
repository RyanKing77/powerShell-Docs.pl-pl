---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: "Powtarzające się zadania dla wielu obiektów ForEach obiektu"
ms.assetid: 6697a12d-2470-4ed6-b5bb-c35e5d525eb6
ms.openlocfilehash: 33ae2c76a512a651ba1b91d15d876608f0d43ccc
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2017
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a>Powtarzające się zadania dla wielu obiektów (ForEach-Object)
**ForEach-Object** polecenia cmdlet używa blokach skryptu i deskryptora $_ dla bieżącego obiektu potoku, aby można było uruchomić polecenie dla każdego obiektu w potoku. Może być używany do wykonania niektórych zadań skomplikowane.

Jedna sytuacja, w której może to być przydatne jest manipulowania danymi, aby był bardziej użyteczne. Klasa Win32_LogicalDisk z usługi WMI można na przykład do zwracania informacji o ilości wolnego miejsca dla każdego dysku lokalnego. Dane są zwracane w postaci liczby bajtów, jednak przypadków, która utrudnia odczytu:

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

Nie możemy przekonwertować wartości FreeSpace megabajtów przez podzielenie każdej wartości przez 1024 dwukrotnie; Po pierwszym podział danych jest w kilobajtach, a po drugim podziału jest megabajtów. Możesz to zrobić w bloku skryptu ForEach-Object, wpisując:

```
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

Niestety dane wyjściowe są teraz danych bez skojarzone etykiety. Ponieważ właściwości usługi WMI, takie jak to tylko do odczytu, nie można przekonwertować bezpośrednio FreeSpace. Jeśli typ to:

```
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

Zostanie wyświetlony komunikat o błędzie:

```
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

Dane można zreorganizować przy użyciu niektórych zaawansowanych technik, ale jest prostsze, aby utworzyć nowy obiekt, za pomocą **Select-Object**.

