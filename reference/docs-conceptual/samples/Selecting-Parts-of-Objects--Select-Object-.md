---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Wybieranie części obiektów wybierz obiekt
ms.assetid: 72e64b1a-d351-4500-9da3-24d8a71d7a92
ms.openlocfilehash: 323c57ba4462e20d9713fb74732989584f5a993f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684514"
---
# <a name="selecting-parts-of-objects-select-object"></a><span data-ttu-id="6fa63-103">Wybieranie części obiektów (Select-Object)</span><span class="sxs-lookup"><span data-stu-id="6fa63-103">Selecting Parts of Objects (Select-Object)</span></span>

<span data-ttu-id="6fa63-104">Możesz użyć **Select-Object** polecenie cmdlet do tworzenia nowych, niestandardowych obiektów programu Windows PowerShell, które zawierają wybrane obiekty używane do tworzenia tych właściwości.</span><span class="sxs-lookup"><span data-stu-id="6fa63-104">You can use the **Select-Object** cmdlet to create new, custom Windows PowerShell objects that contain properties selected from the objects you use to create them.</span></span> <span data-ttu-id="6fa63-105">Wpisz następujące polecenie, aby utworzyć nowy obiekt, który zawiera tylko nazwę i FreeSpace właściwości klasy Win32_LogicalDisk WMI:</span><span class="sxs-lookup"><span data-stu-id="6fa63-105">Type the following command to create a new object that includes only the Name and FreeSpace properties of the Win32_LogicalDisk WMI class:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

<span data-ttu-id="6fa63-106">Typ danych nie może zobaczyć po wykonaniu tego polecenia, ale jeśli możesz przekazać wynik do Get-Member po Select-Object, stwierdzić, że masz nowy typ obiektu, PSCustomObject:</span><span class="sxs-lookup"><span data-stu-id="6fa63-106">You cannot see the type of data after issuing that command, but if you pipe the result to Get-Member after the Select-Object, you can tell that you have a new type of object, a PSCustomObject:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace| Get-Member

   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       System.Boolean Equals(Object obj)
GetHashCode Method       System.Int32 GetHashCode()
GetType     Method       System.Type GetType()
ToString    Method       System.String ToString()
FreeSpace   NoteProperty  FreeSpace=...
Name        NoteProperty System.String Name=C:
```

<span data-ttu-id="6fa63-107">Select-Object ma wiele zastosowań.</span><span class="sxs-lookup"><span data-stu-id="6fa63-107">Select-Object has many uses.</span></span> <span data-ttu-id="6fa63-108">Jeden z nich jest replikowanie danych, które następnie można zmodyfikować.</span><span class="sxs-lookup"><span data-stu-id="6fa63-108">One of them is replicating data that you can then modify.</span></span> <span data-ttu-id="6fa63-109">Firma Microsoft może teraz obsłużyć problem, który wystąpił poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="6fa63-109">We can now handle the problem we ran across in the previous section.</span></span> <span data-ttu-id="6fa63-110">Możemy zaktualizować wartość FreeSpace w naszym nowo utworzone obiekty i dane wyjściowe będą zawierać opisową etykietę:</span><span class="sxs-lookup"><span data-stu-id="6fa63-110">We can update the value of FreeSpace in our newly-created objects and the output will include the descriptive label:</span></span>

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```