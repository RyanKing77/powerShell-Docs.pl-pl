---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: "Wyświetlanie obiektu struktury Get członka"
ms.assetid: a1819ed2-2ef3-453a-b2b0-f3589c550481
ms.openlocfilehash: 618f34bca7bfb76ce5d48ada642a687e279c8aad
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2017
---
# <a name="viewing-object-structure-get-member"></a>Wyświetlanie struktury obiektu (Get Członkowskiego)
Ponieważ obiekty odtworzyć główną rolę w programie Windows PowerShell, istnieje kilka poleceń natywnego zaprojektowane do pracy z dowolnego obiektu typu. Jest jednym z najważniejszych **elementu członkowskiego Get** polecenia.

Najprostsza metoda do analizowania obiektów zwracanych przez polecenie ma przekazać dane wyjściowe tego polecenia, aby **elementu członkowskiego Get** polecenia cmdlet. **Elementu członkowskiego Get** polecenia cmdlet wyświetla posiadanie nazwy typu obiektu i pełną listę jej elementów członkowskich. Liczba elementów, które są zwracane czasami może być utrudnione. Na przykład obiekt procesu mogą mieć członków ponad 100.

Aby wyświetlić wszystkie elementy członkowskie obiektu procesu i strony danych wyjściowych, aby wyświetlić wszystkie, wpisz:

```
PS> Get-Process | Get-Member | Out-Host -Paging
```

Dane wyjściowe tego polecenia będą wyglądać mniej więcej tak:

```
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

Firma Microsoft może wprowadzać tego długą listę informacji bardziej użyteczne filtrując elementy, które chcesz zobaczyć. **Elementu członkowskiego Get** polecenie pozwala na liście tylko elementy członkowskie, które są właściwościami. Istnieje kilka metod właściwości. Polecenie cmdlet wyświetla właściwości dowolnego typu, jeśli firma Microsoft **MemberType elementu członkowskiego Get** wartość **właściwości**. Wynikowa lista jest nadal bardzo długie, ale nieco łatwiejsze w zarządzaniu:

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
> Dozwolone wartości MemberType są AliasProperty, CodeProperty, właściwości, NoteProperty, ScriptProperty, właściwości, PropertySet, metody, CodeMethod, ScriptMethod, metody, ParameterizedProperty, zestaw elementów członkowskich i wszystkie.

Istnieje ponad 60 właściwości dla procesu. Przyczyny, dla której środowiska Windows PowerShell często pokazuje tylko kilka właściwości dla dowolnego dobrze znanego obiektu jest to, że wyświetlane są wszystkie z nich dałby w efekcie bezproblemowego zarządzania ilość informacji.

> [!NOTE]
> Określa sposób wyświetlania typu obiektu przy użyciu informacji zapisanych w plikach XML, których nazwy kończą się w, środowiska Windows PowerShell. format.ps1xml. Formatowanie danych dla procesu obiektów, które są obiektami .NET System.Diagnostics.Process, znajduje się w DotNetTypes.format.ps1xml.

Jeśli potrzebujesz przyjrzeć się właściwości innych niż te, które są domyślnie wyświetlane środowiska Windows PowerShell, należy samodzielnie format danych wyjściowych. Można to zrobić za pomocą poleceń cmdlet formatu.

