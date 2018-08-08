---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Powtarzanie zadania dla wielu obiektów ForEach obiektu
ms.assetid: 6697a12d-2470-4ed6-b5bb-c35e5d525eb6
ms.openlocfilehash: 64d85edad4a6931b2376b95b6d1f5b4d5194399f
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587265"
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