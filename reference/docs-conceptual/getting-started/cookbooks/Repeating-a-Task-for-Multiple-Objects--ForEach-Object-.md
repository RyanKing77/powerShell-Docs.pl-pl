---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Powtarzające się zadania dla wielu obiektów ForEach obiektu
ms.assetid: 6697a12d-2470-4ed6-b5bb-c35e5d525eb6
ms.openlocfilehash: 8b8002af3ade0905421760ce29cdc84b084236e9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a><span data-ttu-id="27c0a-103">Powtarzające się zadania dla wielu obiektów (ForEach-Object)</span><span class="sxs-lookup"><span data-stu-id="27c0a-103">Repeating a Task for Multiple Objects (ForEach-Object)</span></span>

<span data-ttu-id="27c0a-104">**ForEach-Object** polecenia cmdlet używa blokach skryptu i deskryptora $_ dla bieżącego obiektu potoku, aby można było uruchomić polecenie dla każdego obiektu w potoku.</span><span class="sxs-lookup"><span data-stu-id="27c0a-104">The **ForEach-Object** cmdlet uses script blocks and the $_ descriptor for the current pipeline object to let you run a command on each object in the pipeline.</span></span> <span data-ttu-id="27c0a-105">Może być używany do wykonania niektórych zadań skomplikowane.</span><span class="sxs-lookup"><span data-stu-id="27c0a-105">This can be used to perform some complicated tasks.</span></span>

<span data-ttu-id="27c0a-106">Jedna sytuacja, w której może to być przydatne jest manipulowania danymi, aby był bardziej użyteczne.</span><span class="sxs-lookup"><span data-stu-id="27c0a-106">One situation where this can be useful is manipulating data to make it more useful.</span></span> <span data-ttu-id="27c0a-107">Klasa Win32_LogicalDisk z usługi WMI można na przykład do zwracania informacji o ilości wolnego miejsca dla każdego dysku lokalnego.</span><span class="sxs-lookup"><span data-stu-id="27c0a-107">For example, the Win32_LogicalDisk class from WMI can be used to return free space information for each local disk.</span></span> <span data-ttu-id="27c0a-108">Dane są zwracane w postaci liczby bajtów, jednak przypadków, która utrudnia odczytu:</span><span class="sxs-lookup"><span data-stu-id="27c0a-108">The data is returned in terms of bytes, however, which makes it difficult to read:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

<span data-ttu-id="27c0a-109">Nie możemy przekonwertować wartości FreeSpace megabajtów przez podzielenie każdej wartości przez 1024 dwukrotnie; Po pierwszym podział danych jest w kilobajtach, a po drugim podziału jest megabajtów.</span><span class="sxs-lookup"><span data-stu-id="27c0a-109">We can convert the FreeSpace value to megabytes by dividing each value by 1024 twice; after the first division, the data is in kilobytes, and after the second division it is megabytes.</span></span> <span data-ttu-id="27c0a-110">Możesz to zrobić w bloku skryptu ForEach-Object, wpisując:</span><span class="sxs-lookup"><span data-stu-id="27c0a-110">You can do that in a ForEach-Object script block by typing:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

<span data-ttu-id="27c0a-111">Niestety dane wyjściowe są teraz danych bez skojarzone etykiety.</span><span class="sxs-lookup"><span data-stu-id="27c0a-111">Unfortunately, the output is now data with no associated label.</span></span> <span data-ttu-id="27c0a-112">Ponieważ właściwości usługi WMI, takie jak to tylko do odczytu, nie można przekonwertować bezpośrednio FreeSpace.</span><span class="sxs-lookup"><span data-stu-id="27c0a-112">Because WMI properties such as this are read-only, you cannot directly convert FreeSpace.</span></span> <span data-ttu-id="27c0a-113">Jeśli typ to:</span><span class="sxs-lookup"><span data-stu-id="27c0a-113">If you type this:</span></span>

```powershell
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

<span data-ttu-id="27c0a-114">Zostanie wyświetlony komunikat o błędzie:</span><span class="sxs-lookup"><span data-stu-id="27c0a-114">You get an error message:</span></span>

```output
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

<span data-ttu-id="27c0a-115">Dane można zreorganizować przy użyciu niektórych zaawansowanych technik, ale jest prostsze, aby utworzyć nowy obiekt, za pomocą **Select-Object**.</span><span class="sxs-lookup"><span data-stu-id="27c0a-115">You could reorganize the data by using some advanced techniques, but a simpler approach is to create a new object, by using **Select-Object**.</span></span>