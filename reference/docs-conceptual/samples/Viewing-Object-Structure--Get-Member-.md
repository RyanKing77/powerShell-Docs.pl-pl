---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Wyświetlanie obiektu struktury Get członka
ms.assetid: a1819ed2-2ef3-453a-b2b0-f3589c550481
ms.openlocfilehash: cc93e45e4306b3d623c1d3d1096dd20c1afc59c8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058849"
---
# <a name="viewing-object-structure-get-member"></a>Wyświetlanie struktury obiektu (Get-Member)

Ponieważ obiekty odtworzyć główną rolę w środowisku Windows PowerShell, istnieje kilka poleceń natywnych przeznaczona do pracy z dowolnego wybierane. Jest jednym z najważniejszych **Get-Member** polecenia.

Najprostsza technika analizowanie obiektów, które zwraca polecenia jest przekazać dane wyjściowe tego polecenia do **Get-Member** polecenia cmdlet. **Get-Member** polecenia cmdlet, dowiesz się posiadanie nazwy, typu obiektu i pełną listę składowych. Liczba elementów, które są zwracane, które czasami może być utrudnione. Na przykład obiekt proces może mieć ponad 100 elementów członkowskich.

Aby wyświetlić wszystkie elementy członkowskie obiektu procesu i strony danych wyjściowych, aby można było wyświetlić wszystkie, wpisz:

```powershell
Get-Process | Get-Member | Out-Host -Paging
```

Dane wyjściowe tego polecenia będą wyglądać mniej więcej tak:

```output
TypeName: System.Diagnostics.Process

Name                           MemberType     Definition
----                           ----------     ----------
Handles                        AliasProperty  Handles = Handlecount
Name                           AliasProperty  Name = ProcessName
NPM                            AliasProperty  NPM = NonpagedSystemMemorySize
PM                             AliasProperty  PM = PagedMemorySize
VM                             AliasProperty  VM = VirtualMemorySize
WS                             AliasProperty  WS = WorkingSet
add_Disposed                   Method         System.Void add_Disposed(Event...
...
```

Firma Microsoft ułatwia to długą listę informacji bardziej użyteczne, filtrując elementy, które chcesz zobaczyć. **Get-Member** polecenie umożliwia wyświetlenie tylko elementów członkowskich, które są właściwościami. Istnieje kilka postaci właściwości. Polecenie cmdlet wyświetla właściwości dowolnego typu, jeśli ustawimy **MemberType Get-Member** wartość **właściwości**. Wynikowej listy jest nadal bardzo długie, lecz nieco łatwiejsza w zarządzaniu:

```
PS> Get-Process | Get-Member -MemberType Properties

   TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
...
ExitCode                   Property       System.Int32 ExitCode {get;}
...
Handle                     Property       System.IntPtr Handle {get;}
...
CPU                        ScriptProperty System.Object CPU {get=$this.Total...
...
Path                       ScriptProperty System.Object Path {get=$this.Main...
...
```

> [!NOTE]
> Dozwolone wartości MemberType to AliasProperty, CodeProperty, właściwości, NoteProperty, ScriptProperty, właściwości, PropertySet, metody, CodeMethod, ScriptMethod, metody, ParameterizedProperty, zestaw elementów członkowskich i wszystkich.

Istnieje ponad 60 właściwości dla procesu. Powodów, dla którego programu Windows PowerShell są często wyświetlane jest tylko niewielki podzbiór właściwości dla dowolnego obiektu dobrze znanego, przedstawiający wszystkie z nich dałby w efekcie bezproblemowego zarządzania ilość informacji.

> [!NOTE]
> Program Windows PowerShell określa sposób wyświetlania typu obiektu, korzystając z informacji przechowywanych w plikach XML, które mają nazwy kończące się na. format.ps1xml. Formatowania danych dla procesu obiektów, które są obiektami .NET System.Diagnostics.Process, są przechowywane w DotNetTypes.format.ps1xml.

Jeśli zachodzi potrzeba przyjrzeć się właściwości innych niż te, które są domyślnie wyświetlane programu Windows PowerShell, należy sformatować dane wyjściowe, samodzielnie. Można to zrobić za pomocą poleceń cmdlet format.