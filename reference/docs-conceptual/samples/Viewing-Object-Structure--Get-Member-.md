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
# <a name="viewing-object-structure-get-member"></a><span data-ttu-id="a11b9-103">Wyświetlanie struktury obiektu (Get-Member)</span><span class="sxs-lookup"><span data-stu-id="a11b9-103">Viewing Object Structure (Get-Member)</span></span>

<span data-ttu-id="a11b9-104">Ponieważ obiekty odtworzyć główną rolę w środowisku Windows PowerShell, istnieje kilka poleceń natywnych przeznaczona do pracy z dowolnego wybierane.</span><span class="sxs-lookup"><span data-stu-id="a11b9-104">Because objects play such a central role in Windows PowerShell, there are several native commands designed to work with arbitrary object types.</span></span> <span data-ttu-id="a11b9-105">Jest jednym z najważniejszych **Get-Member** polecenia.</span><span class="sxs-lookup"><span data-stu-id="a11b9-105">The most important one is the **Get-Member** command.</span></span>

<span data-ttu-id="a11b9-106">Najprostsza technika analizowanie obiektów, które zwraca polecenia jest przekazać dane wyjściowe tego polecenia do **Get-Member** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a11b9-106">The simplest technique for analyzing the objects that a command returns is to pipe the output of that command to the **Get-Member** cmdlet.</span></span> <span data-ttu-id="a11b9-107">**Get-Member** polecenia cmdlet, dowiesz się posiadanie nazwy, typu obiektu i pełną listę składowych.</span><span class="sxs-lookup"><span data-stu-id="a11b9-107">The **Get-Member** cmdlet shows you the formal name of the object type and a complete listing of its members.</span></span> <span data-ttu-id="a11b9-108">Liczba elementów, które są zwracane, które czasami może być utrudnione.</span><span class="sxs-lookup"><span data-stu-id="a11b9-108">The number of elements that are returned can sometimes be overwhelming.</span></span> <span data-ttu-id="a11b9-109">Na przykład obiekt proces może mieć ponad 100 elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="a11b9-109">For example, a process object can have over 100 members.</span></span>

<span data-ttu-id="a11b9-110">Aby wyświetlić wszystkie elementy członkowskie obiektu procesu i strony danych wyjściowych, aby można było wyświetlić wszystkie, wpisz:</span><span class="sxs-lookup"><span data-stu-id="a11b9-110">To see all the members of a Process object and page the output so you can view all of it, type:</span></span>

```powershell
Get-Process | Get-Member | Out-Host -Paging
```

<span data-ttu-id="a11b9-111">Dane wyjściowe tego polecenia będą wyglądać mniej więcej tak:</span><span class="sxs-lookup"><span data-stu-id="a11b9-111">The output from this command will look something like this:</span></span>

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

<span data-ttu-id="a11b9-112">Firma Microsoft ułatwia to długą listę informacji bardziej użyteczne, filtrując elementy, które chcesz zobaczyć.</span><span class="sxs-lookup"><span data-stu-id="a11b9-112">We can make this long list of information more usable by filtering for elements we want to see.</span></span> <span data-ttu-id="a11b9-113">**Get-Member** polecenie umożliwia wyświetlenie tylko elementów członkowskich, które są właściwościami.</span><span class="sxs-lookup"><span data-stu-id="a11b9-113">The **Get-Member** command lets you list only members that are properties.</span></span> <span data-ttu-id="a11b9-114">Istnieje kilka postaci właściwości.</span><span class="sxs-lookup"><span data-stu-id="a11b9-114">There are several forms of properties.</span></span> <span data-ttu-id="a11b9-115">Polecenie cmdlet wyświetla właściwości dowolnego typu, jeśli ustawimy **MemberType Get-Member** wartość **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="a11b9-115">The cmdlet displays properties of any type if we set the **Get-Member MemberType** parameter to the value **Properties**.</span></span> <span data-ttu-id="a11b9-116">Wynikowej listy jest nadal bardzo długie, lecz nieco łatwiejsza w zarządzaniu:</span><span class="sxs-lookup"><span data-stu-id="a11b9-116">The resulting list is still very long, but a bit more manageable:</span></span>

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
> <span data-ttu-id="a11b9-117">Dozwolone wartości MemberType to AliasProperty, CodeProperty, właściwości, NoteProperty, ScriptProperty, właściwości, PropertySet, metody, CodeMethod, ScriptMethod, metody, ParameterizedProperty, zestaw elementów członkowskich i wszystkich.</span><span class="sxs-lookup"><span data-stu-id="a11b9-117">The allowed values of MemberType are AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, and All.</span></span>

<span data-ttu-id="a11b9-118">Istnieje ponad 60 właściwości dla procesu.</span><span class="sxs-lookup"><span data-stu-id="a11b9-118">There are over 60 properties for a process.</span></span> <span data-ttu-id="a11b9-119">Powodów, dla którego programu Windows PowerShell są często wyświetlane jest tylko niewielki podzbiór właściwości dla dowolnego obiektu dobrze znanego, przedstawiający wszystkie z nich dałby w efekcie bezproblemowego zarządzania ilość informacji.</span><span class="sxs-lookup"><span data-stu-id="a11b9-119">The reason Windows PowerShell often shows only a handful of properties for any well-known object is that showing all of them would produce an unmanageable amount of information.</span></span>

> [!NOTE]
> <span data-ttu-id="a11b9-120">Program Windows PowerShell określa sposób wyświetlania typu obiektu, korzystając z informacji przechowywanych w plikach XML, które mają nazwy kończące się na. format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="a11b9-120">Windows PowerShell determines how to display an object type by using information stored in XML files that have names ending in .format.ps1xml.</span></span> <span data-ttu-id="a11b9-121">Formatowania danych dla procesu obiektów, które są obiektami .NET System.Diagnostics.Process, są przechowywane w DotNetTypes.format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="a11b9-121">The formatting data for process objects, which are .NET System.Diagnostics.Process objects, is stored in DotNetTypes.format.ps1xml.</span></span>

<span data-ttu-id="a11b9-122">Jeśli zachodzi potrzeba przyjrzeć się właściwości innych niż te, które są domyślnie wyświetlane programu Windows PowerShell, należy sformatować dane wyjściowe, samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="a11b9-122">If you need to look at properties other than those that Windows PowerShell displays by default, you will need to format the output data yourself.</span></span> <span data-ttu-id="a11b9-123">Można to zrobić za pomocą poleceń cmdlet format.</span><span class="sxs-lookup"><span data-stu-id="a11b9-123">This can be done by using the format cmdlets.</span></span>