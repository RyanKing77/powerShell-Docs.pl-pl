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
# <a name="selecting-parts-of-objects-select-object"></a>Wybieranie części obiektów (Select-Object)

Możesz użyć **Select-Object** polecenie cmdlet do tworzenia nowych, niestandardowych obiektów programu Windows PowerShell, które zawierają wybrane obiekty używane do tworzenia tych właściwości. Wpisz następujące polecenie, aby utworzyć nowy obiekt, który zawiera tylko nazwę i FreeSpace właściwości klasy Win32_LogicalDisk WMI:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

Typ danych nie może zobaczyć po wykonaniu tego polecenia, ale jeśli możesz przekazać wynik do Get-Member po Select-Object, stwierdzić, że masz nowy typ obiektu, PSCustomObject:

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

Select-Object ma wiele zastosowań. Jeden z nich jest replikowanie danych, które następnie można zmodyfikować. Firma Microsoft może teraz obsłużyć problem, który wystąpił poprzedniej sekcji. Możemy zaktualizować wartość FreeSpace w naszym nowo utworzone obiekty i dane wyjściowe będą zawierać opisową etykietę:

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```