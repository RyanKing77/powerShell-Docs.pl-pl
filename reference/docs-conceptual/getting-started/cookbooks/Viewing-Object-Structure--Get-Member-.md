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
# <a name="viewing-object-structure-get-member"></a><span data-ttu-id="e038c-103">Wyświetlanie struktury obiektu (Get Członkowskiego)</span><span class="sxs-lookup"><span data-stu-id="e038c-103">Viewing Object Structure (Get-Member)</span></span>
<span data-ttu-id="e038c-104">Ponieważ obiekty odtworzyć główną rolę w programie Windows PowerShell, istnieje kilka poleceń natywnego zaprojektowane do pracy z dowolnego obiektu typu.</span><span class="sxs-lookup"><span data-stu-id="e038c-104">Because objects play such a central role in Windows PowerShell, there are several native commands designed to work with arbitrary object types.</span></span> <span data-ttu-id="e038c-105">Jest jednym z najważniejszych **elementu członkowskiego Get** polecenia.</span><span class="sxs-lookup"><span data-stu-id="e038c-105">The most important one is the **Get-Member** command.</span></span>

<span data-ttu-id="e038c-106">Najprostsza metoda do analizowania obiektów zwracanych przez polecenie ma przekazać dane wyjściowe tego polecenia, aby **elementu członkowskiego Get** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e038c-106">The simplest technique for analyzing the objects that a command returns is to pipe the output of that command to the **Get-Member** cmdlet.</span></span> <span data-ttu-id="e038c-107">**Elementu członkowskiego Get** polecenia cmdlet wyświetla posiadanie nazwy typu obiektu i pełną listę jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="e038c-107">The **Get-Member** cmdlet shows you the formal name of the object type and a complete listing of its members.</span></span> <span data-ttu-id="e038c-108">Liczba elementów, które są zwracane czasami może być utrudnione.</span><span class="sxs-lookup"><span data-stu-id="e038c-108">The number of elements that are returned can sometimes be overwhelming.</span></span> <span data-ttu-id="e038c-109">Na przykład obiekt procesu mogą mieć członków ponad 100.</span><span class="sxs-lookup"><span data-stu-id="e038c-109">For example, a process object can have over 100 members.</span></span>

<span data-ttu-id="e038c-110">Aby wyświetlić wszystkie elementy członkowskie obiektu procesu i strony danych wyjściowych, aby wyświetlić wszystkie, wpisz:</span><span class="sxs-lookup"><span data-stu-id="e038c-110">To see all the members of a Process object and page the output so you can view all of it, type:</span></span>

```
PS> Get-Process | Get-Member | Out-Host -Paging
```

<span data-ttu-id="e038c-111">Dane wyjściowe tego polecenia będą wyglądać mniej więcej tak:</span><span class="sxs-lookup"><span data-stu-id="e038c-111">The output from this command will look something like this:</span></span>

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

<span data-ttu-id="e038c-112">Firma Microsoft może wprowadzać tego długą listę informacji bardziej użyteczne filtrując elementy, które chcesz zobaczyć.</span><span class="sxs-lookup"><span data-stu-id="e038c-112">We can make this long list of information more usable by filtering for elements we want to see.</span></span> <span data-ttu-id="e038c-113">**Elementu członkowskiego Get** polecenie pozwala na liście tylko elementy członkowskie, które są właściwościami.</span><span class="sxs-lookup"><span data-stu-id="e038c-113">The **Get-Member** command lets you list only members that are properties.</span></span> <span data-ttu-id="e038c-114">Istnieje kilka metod właściwości.</span><span class="sxs-lookup"><span data-stu-id="e038c-114">There are several forms of properties.</span></span> <span data-ttu-id="e038c-115">Polecenie cmdlet wyświetla właściwości dowolnego typu, jeśli firma Microsoft **MemberType elementu członkowskiego Get** wartość **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="e038c-115">The cmdlet displays properties of any type if we set the **Get-Member MemberType** parameter to the value **Properties**.</span></span> <span data-ttu-id="e038c-116">Wynikowa lista jest nadal bardzo długie, ale nieco łatwiejsze w zarządzaniu:</span><span class="sxs-lookup"><span data-stu-id="e038c-116">The resulting list is still very long, but a bit more manageable:</span></span>

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
> <span data-ttu-id="e038c-117">Dozwolone wartości MemberType są AliasProperty, CodeProperty, właściwości, NoteProperty, ScriptProperty, właściwości, PropertySet, metody, CodeMethod, ScriptMethod, metody, ParameterizedProperty, zestaw elementów członkowskich i wszystkie.</span><span class="sxs-lookup"><span data-stu-id="e038c-117">The allowed values of MemberType are AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, and All.</span></span>

<span data-ttu-id="e038c-118">Istnieje ponad 60 właściwości dla procesu.</span><span class="sxs-lookup"><span data-stu-id="e038c-118">There are over 60 properties for a process.</span></span> <span data-ttu-id="e038c-119">Przyczyny, dla której środowiska Windows PowerShell często pokazuje tylko kilka właściwości dla dowolnego dobrze znanego obiektu jest to, że wyświetlane są wszystkie z nich dałby w efekcie bezproblemowego zarządzania ilość informacji.</span><span class="sxs-lookup"><span data-stu-id="e038c-119">The reason Windows PowerShell often shows only a handful of properties for any well-known object is that showing all of them would produce an unmanageable amount of information.</span></span>

> [!NOTE]
> <span data-ttu-id="e038c-120">Określa sposób wyświetlania typu obiektu przy użyciu informacji zapisanych w plikach XML, których nazwy kończą się w, środowiska Windows PowerShell. format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="e038c-120">Windows PowerShell determines how to display an object type by using information stored in XML files that have names ending in .format.ps1xml.</span></span> <span data-ttu-id="e038c-121">Formatowanie danych dla procesu obiektów, które są obiektami .NET System.Diagnostics.Process, znajduje się w DotNetTypes.format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="e038c-121">The formatting data for process objects, which are .NET System.Diagnostics.Process objects, is stored in DotNetTypes.format.ps1xml.</span></span>

<span data-ttu-id="e038c-122">Jeśli potrzebujesz przyjrzeć się właściwości innych niż te, które są domyślnie wyświetlane środowiska Windows PowerShell, należy samodzielnie format danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="e038c-122">If you need to look at properties other than those that Windows PowerShell displays by default, you will need to format the output data yourself.</span></span> <span data-ttu-id="e038c-123">Można to zrobić za pomocą poleceń cmdlet formatu.</span><span class="sxs-lookup"><span data-stu-id="e038c-123">This can be done by using the format cmdlets.</span></span>

