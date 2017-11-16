---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: "Wybieranie części obiektów wybierz obiekt"
ms.assetid: 72e64b1a-d351-4500-9da3-24d8a71d7a92
ms.openlocfilehash: 8c9633e80f63e1d474c46fa772108aee4f79751d
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2017
---
# <a name="selecting-parts-of-objects-select-object"></a><span data-ttu-id="e6a28-103">Zaznaczanie części obiektów (Select-Object)</span><span class="sxs-lookup"><span data-stu-id="e6a28-103">Selecting Parts of Objects (Select-Object)</span></span>
<span data-ttu-id="e6a28-104">Można użyć **Select-Object** , aby utworzyć nowy, niestandardowy obiektów programu Windows PowerShell, które zawierają wybrane obiekty używane do tworzenia tych właściwości.</span><span class="sxs-lookup"><span data-stu-id="e6a28-104">You can use the **Select-Object** cmdlet to create new, custom Windows PowerShell objects that contain properties selected from the objects you use to create them.</span></span> <span data-ttu-id="e6a28-105">Wpisz następujące polecenie, aby utworzyć nowy obiekt zawierający tylko nazwę i FreeSpace właściwości klasy Win32_LogicalDisk WMI:</span><span class="sxs-lookup"><span data-stu-id="e6a28-105">Type the following command to create a new object that includes only the Name and FreeSpace properties of the Win32_LogicalDisk WMI class:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

<span data-ttu-id="e6a28-106">Typ danych nie może zobaczyć po wykonaniu tego polecenia, ale jeśli możesz przekazać wynik do elementu członkowskiego Get po Select-Object, można określić, czy masz nowy typ obiektu, PSCustomObject:</span><span class="sxs-lookup"><span data-stu-id="e6a28-106">You cannot see the type of data after issuing that command, but if you pipe the result to Get-Member after the Select-Object, you can tell that you have a new type of object, a PSCustomObject:</span></span>

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

<span data-ttu-id="e6a28-107">Select-Object ma wiele zastosowań.</span><span class="sxs-lookup"><span data-stu-id="e6a28-107">Select-Object has many uses.</span></span> <span data-ttu-id="e6a28-108">Jeden z nich jest replikowanie danych, które można modyfikować.</span><span class="sxs-lookup"><span data-stu-id="e6a28-108">One of them is replicating data that you can then modify.</span></span> <span data-ttu-id="e6a28-109">Firma Microsoft może teraz obsłużyć problemu, który wystąpił poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="e6a28-109">We can now handle the problem we ran across in the previous section.</span></span> <span data-ttu-id="e6a28-110">Możemy zaktualizować wartości FreeSpace w naszym nowo tworzonych obiektów i dane wyjściowe będą zawierać opisową etykietę:</span><span class="sxs-lookup"><span data-stu-id="e6a28-110">We can update the value of FreeSpace in our newly-created objects and the output will include the descriptive label:</span></span>

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```

