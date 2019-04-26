---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Powtarzanie zadania dla wielu obiektów ForEach obiektu
ms.assetid: 6697a12d-2470-4ed6-b5bb-c35e5d525eb6
ms.openlocfilehash: 64d85edad4a6931b2376b95b6d1f5b4d5194399f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086174"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a><span data-ttu-id="39ecc-103">Powtarzanie zadania dla wielu obiektów (ForEach-Object)</span><span class="sxs-lookup"><span data-stu-id="39ecc-103">Repeating a Task for Multiple Objects (ForEach-Object)</span></span>

<span data-ttu-id="39ecc-104">**ForEach-Object** polecenie cmdlet używa Bloki skryptu i `$_` deskryptora dla bieżącego obiektu potoku umożliwić, możesz uruchomić polecenie dla każdego obiektu w potoku.</span><span class="sxs-lookup"><span data-stu-id="39ecc-104">The **ForEach-Object** cmdlet uses script blocks and the `$_` descriptor for the current pipeline object to let you run a command on each object in the pipeline.</span></span> <span data-ttu-id="39ecc-105">Może to służyć do wykonania niektórych zadań skomplikowane.</span><span class="sxs-lookup"><span data-stu-id="39ecc-105">This can be used to perform some complicated tasks.</span></span>

<span data-ttu-id="39ecc-106">Jedna sytuacja, w których może to być przydatne jest manipulowanie danymi, aby zwiększyć jej użyteczność.</span><span class="sxs-lookup"><span data-stu-id="39ecc-106">One situation where this can be useful is manipulating data to make it more useful.</span></span> <span data-ttu-id="39ecc-107">Na przykład Klasa Win32_LogicalDisk WMI może służyć do zwracania informacji wolnego miejsca dla każdego dysku lokalnego.</span><span class="sxs-lookup"><span data-stu-id="39ecc-107">For example, the Win32_LogicalDisk class from WMI can be used to return free space information for each local disk.</span></span> <span data-ttu-id="39ecc-108">Dane są zwracane się pod względem bajtów, ale, co czyni go trudno odczytać:</span><span class="sxs-lookup"><span data-stu-id="39ecc-108">The data is returned in terms of bytes, however, which makes it difficult to read:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

<span data-ttu-id="39ecc-109">Możemy przekonwertować wartości FreeSpace megabajtów przez podzielenie każdej wartości przez 1024 dwukrotnie; Po wykonaniu dzielenia pierwszego dane znajdują się w kilobajtach, a po wykonaniu dzielenia drugi jest w megabajtach.</span><span class="sxs-lookup"><span data-stu-id="39ecc-109">We can convert the FreeSpace value to megabytes by dividing each value by 1024 twice; after the first division, the data is in kilobytes, and after the second division it is megabytes.</span></span> <span data-ttu-id="39ecc-110">Możesz to zrobić w bloku skryptu ForEach-Object, wpisując:</span><span class="sxs-lookup"><span data-stu-id="39ecc-110">You can do that in a ForEach-Object script block by typing:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

<span data-ttu-id="39ecc-111">Niestety dane wyjściowe są teraz danych bez skojarzonych etykiety.</span><span class="sxs-lookup"><span data-stu-id="39ecc-111">Unfortunately, the output is now data with no associated label.</span></span> <span data-ttu-id="39ecc-112">Ponieważ właściwości usługi WMI, takie jak to tylko do odczytu, nie można bezpośrednio przekonwertować FreeSpace.</span><span class="sxs-lookup"><span data-stu-id="39ecc-112">Because WMI properties such as this are read-only, you cannot directly convert FreeSpace.</span></span> <span data-ttu-id="39ecc-113">Jeśli wpiszesz to:</span><span class="sxs-lookup"><span data-stu-id="39ecc-113">If you type this:</span></span>

```powershell
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

<span data-ttu-id="39ecc-114">Otrzymasz komunikat o błędzie:</span><span class="sxs-lookup"><span data-stu-id="39ecc-114">You get an error message:</span></span>

```output
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

<span data-ttu-id="39ecc-115">Dane można uporządkować przy użyciu kilka zaawansowanych technik, ale jest prostszej metody, aby utworzyć nowy obiekt, za pomocą **Select-Object**.</span><span class="sxs-lookup"><span data-stu-id="39ecc-115">You could reorganize the data by using some advanced techniques, but a simpler approach is to create a new object, by using **Select-Object**.</span></span>