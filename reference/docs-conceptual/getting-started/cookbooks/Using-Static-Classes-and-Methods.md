---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Używanie metod i klas statycznych
ms.assetid: 418ad766-afa6-4b8c-9a44-471889af7fd9
ms.openlocfilehash: 0f2b02c3a40365ad0335118b057a4e548c9f6535
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="using-static-classes-and-methods"></a><span data-ttu-id="3d7a0-103">Używanie metod i klas statycznych</span><span class="sxs-lookup"><span data-stu-id="3d7a0-103">Using Static Classes and Methods</span></span>
<span data-ttu-id="3d7a0-104">Nie wszystkie klasy .NET Framework, można utworzyć za pomocą **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-104">Not all .NET Framework classes can be created by using **New-Object**.</span></span> <span data-ttu-id="3d7a0-105">Na przykład, jeśli próbujesz utworzyć **System.Environment** lub **System.Math** obiekt z **New-Object**, otrzymasz następujące komunikaty o błędach:</span><span class="sxs-lookup"><span data-stu-id="3d7a0-105">For example, if you try to create a **System.Environment** or a **System.Math** object with **New-Object**, you will get the following error messages:</span></span>

```
PS> New-Object System.Environment
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Environment.
At line:1 char:11
+ New-Object  <<<< System.Environment

PS> New-Object System.Math
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Math.
At line:1 char:11
+ New-Object  <<<< System.Math
```

<span data-ttu-id="3d7a0-106">Te błędy, ponieważ nie istnieje sposób można utworzyć nowego obiektu z tych klas.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-106">These errors occur because there is no way to create a new object from these classes.</span></span> <span data-ttu-id="3d7a0-107">Te klasy są bibliotek odwołania metod i właściwości, które nie ulegają zmianie stanu.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-107">These classes are reference libraries of methods and properties that do not change state.</span></span> <span data-ttu-id="3d7a0-108">Nie trzeba je utworzyć, możesz po prostu użyć ich.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-108">You don't need to create them, you simply use them.</span></span> <span data-ttu-id="3d7a0-109">Klasy i metody, takie jak te są nazywane *klasy statyczne* , ponieważ nie są tworzone, zniszczony lub zmienione.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-109">Classes and methods such as these are called *static classes* because they are not created, destroyed, or changed.</span></span> <span data-ttu-id="3d7a0-110">Aby to wyczyść udostępniamy przykłady, które używają klasy statyczne.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-110">To make this clear we will provide examples that use static classes.</span></span>

### <a name="getting-environment-data-with-systemenvironment"></a><span data-ttu-id="3d7a0-111">Pobieranie danych środowiska z System.Environment</span><span class="sxs-lookup"><span data-stu-id="3d7a0-111">Getting Environment Data with System.Environment</span></span>
<span data-ttu-id="3d7a0-112">Zwykle pierwszym krokiem podczas pracy z obiektu w programie Windows PowerShell jest na potrzeby dowiedzieć się, jakie elementy członkowskie zawiera element członkowski Get.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-112">Usually, the first step in working with an object in Windows PowerShell is to use Get-Member to find out what members it contains.</span></span> <span data-ttu-id="3d7a0-113">Z klasy statyczne proces jest nieco inny, ponieważ rzeczywista klasa nie jest obiektem.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-113">With static classes, the process is a little different because the actual class is not an object.</span></span>

#### <a name="referring-to-the-static-systemenvironment-class"></a><span data-ttu-id="3d7a0-114">Odwołanie do klasy statycznej System.Environment</span><span class="sxs-lookup"><span data-stu-id="3d7a0-114">Referring to the Static System.Environment Class</span></span>
<span data-ttu-id="3d7a0-115">Mogą odwoływać się do klasy statycznej, wpisując nazwę klasy w nawiasy kwadratowe.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-115">You can refer to a static class by surrounding the class name with square brackets.</span></span> <span data-ttu-id="3d7a0-116">Na przykład mogą odwoływać się do **System.Environment** , wpisując nazwę w nawiasach kwadratowych.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-116">For example, you can refer to **System.Environment** by typing the name within brackets.</span></span> <span data-ttu-id="3d7a0-117">Dzięki temu przedstawia niektóre informacje typu ogólnego:</span><span class="sxs-lookup"><span data-stu-id="3d7a0-117">Doing so displays some generic type information:</span></span>

```
PS> [System.Environment]

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     False    Environment                              System.Object
```

> [!NOTE]
> <span data-ttu-id="3d7a0-118">Jak wspomniano wcześniej, programu Windows PowerShell automatycznie dołącza "**systemu.**"</span><span class="sxs-lookup"><span data-stu-id="3d7a0-118">As we mentioned previously, Windows PowerShell automatically prepends '**System.**'</span></span> <span data-ttu-id="3d7a0-119">wpisanie nazwy, gdy używasz **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-119">to type names when you use **New-Object**.</span></span> <span data-ttu-id="3d7a0-120">To samo spowodowany przy użyciu nazwy typu w nawiasach kwadratowych, więc można określić  **\[System.Environment]** jako  **\[środowiska]**.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-120">The same thing happens when using a bracketed type name, so you can specify **\[System.Environment]** as **\[Environment]**.</span></span>

<span data-ttu-id="3d7a0-121">**System.Environment** klasa zawiera ogólne informacje na temat środowiska pracy dla bieżącego procesu, który jest powershell.exe podczas pracy w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-121">The **System.Environment** class contains general information about the working environment for the current process, which is powershell.exe when working within Windows PowerShell.</span></span>

<span data-ttu-id="3d7a0-122">Jeśli użytkownik próbuje wyświetlić szczegóły dotyczące tej klasy, wpisując  **\[System.Environment] | Element członkowski GET**, typ obiektu jest raportowane jako **System.RuntimeType** , a nie **System.Environment**:</span><span class="sxs-lookup"><span data-stu-id="3d7a0-122">If you try to view details of this class by typing **\[System.Environment] | Get-Member**, the object type is reported as being **System.RuntimeType** , not **System.Environment**:</span></span>

```
PS> [System.Environment] | Get-Member

   TypeName: System.RuntimeType
```

<span data-ttu-id="3d7a0-123">Aby wyświetlić statyczne elementy członkowskie z elementem członkowskim Get, określ **statycznych** parametru:</span><span class="sxs-lookup"><span data-stu-id="3d7a0-123">To view static members with Get-Member, specify the **Static** parameter:</span></span>

```
PS> [System.Environment] | Get-Member -Static

   TypeName: System.Environment

Name                       MemberType Definition
----                       ---------- ----------
Equals                     Method     static System.Boolean Equals(Object ob...
Exit                       Method     static System.Void Exit(Int32 exitCode)
...
CommandLine                Property   static System.String CommandLine {get;}
CurrentDirectory           Property   static System.String CurrentDirectory ...
ExitCode                   Property   static System.Int32 ExitCode {get;set;}
HasShutdownStarted         Property   static System.Boolean HasShutdownStart...
MachineName                Property   static System.String MachineName {get;}
NewLine                    Property   static System.String NewLine {get;}
OSVersion                  Property   static System.OperatingSystem OSVersio...
ProcessorCount             Property   static System.Int32 ProcessorCount {get;}
StackTrace                 Property   static System.String StackTrace {get;}
SystemDirectory            Property   static System.String SystemDirectory {...
TickCount                  Property   static System.Int32 TickCount {get;}
UserDomainName             Property   static System.String UserDomainName {g...
UserInteractive            Property   static System.Boolean UserInteractive ...
UserName                   Property   static System.String UserName {get;}
Version                    Property   static System.Version Version {get;}
WorkingSet                 Property   static System.Int64 WorkingSet {get;}
TickCount                               ExitCode
```

<span data-ttu-id="3d7a0-124">Firma Microsoft można teraz wybrać właściwości z System.Environment.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-124">We can now select properties to view from System.Environment.</span></span>

#### <a name="displaying-static-properties-of-systemenvironment"></a><span data-ttu-id="3d7a0-125">Wyświetlanie właściwości statycznej System.Environment</span><span class="sxs-lookup"><span data-stu-id="3d7a0-125">Displaying Static Properties of System.Environment</span></span>

<span data-ttu-id="3d7a0-126">Właściwości System.Environment również są statyczne i musi zostać określona w inny sposób niż normalne właściwości.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-126">The properties of System.Environment are also static, and must be specified in a different way than normal properties.</span></span> <span data-ttu-id="3d7a0-127">Używamy **::** wskazująca na program Windows PowerShell, która ma być współpracować z statycznej metody lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-127">We use **::** to indicate to Windows PowerShell that we want to work with a static method or property.</span></span> <span data-ttu-id="3d7a0-128">Aby wyświetlić polecenia, który został użyty do uruchomienia programu Windows PowerShell, sprawdzamy **CommandLine** właściwości, wpisując:</span><span class="sxs-lookup"><span data-stu-id="3d7a0-128">To see the command that was used to launch Windows PowerShell, we check the **CommandLine** property by typing:</span></span>

```
PS> [System.Environment]::Commandline
"C:\Program Files\Windows PowerShell\v1.0\powershell.exe"
```

<span data-ttu-id="3d7a0-129">Aby sprawdzić wersję systemu operacyjnego, należy wyświetlić właściwości OSVersion, wpisując:</span><span class="sxs-lookup"><span data-stu-id="3d7a0-129">To check the operating system version, display the OSVersion property by typing:</span></span>

```
PS> [System.Environment]::OSVersion

           Platform ServicePack         Version             VersionString
           -------- -----------         -------             -------------
            Win32NT Service Pack 2      5.1.2600.131072     Microsoft Windows...
```

<span data-ttu-id="3d7a0-130">Można sprawdzić, czy komputer jest zamykany przez wyświetlanie **HasShutdownStarted** właściwości:</span><span class="sxs-lookup"><span data-stu-id="3d7a0-130">We can check whether the computer is in the process of shutting down by displaying the **HasShutdownStarted** property:</span></span>

```
PS> [System.Environment]::HasShutdownStarted
False
```

### <a name="doing-math-with-systemmath"></a><span data-ttu-id="3d7a0-131">Wykonanie matematyczne z System.Math</span><span class="sxs-lookup"><span data-stu-id="3d7a0-131">Doing Math with System.Math</span></span>

<span data-ttu-id="3d7a0-132">Klasa statyczna System.Math jest przydatne w przypadku wykonywania pewnych operacji matematycznych.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-132">The System.Math static class is useful for performing some mathematical operations.</span></span> <span data-ttu-id="3d7a0-133">Ważne elementy członkowskie **System.Math** przede wszystkim metody, których można wyświetlić przy użyciu **elementu członkowskiego Get**.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-133">The important members of **System.Math** are mostly methods, which we can display by using **Get-Member**.</span></span>

> [!NOTE]
> <span data-ttu-id="3d7a0-134">System.Math ma kilka metod o tej samej nazwie, ale różnią się one według typu ich parametrów.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-134">System.Math has several methods with the same name, but they are distinguished by the type of their parameters.</span></span>

<span data-ttu-id="3d7a0-135">Wpisz następujące polecenie, aby wyświetlić listę metod **System.Math** klasy.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-135">Type the following command to list the methods of the **System.Math** class.</span></span>

```
PS> [System.Math] | Get-Member -Static -MemberType Methods

   TypeName: System.Math

Name            MemberType Definition
----            ---------- ----------
Abs             Method     static System.Single Abs(Single value), static Sy...
Acos            Method     static System.Double Acos(Double d)
Asin            Method     static System.Double Asin(Double d)
Atan            Method     static System.Double Atan(Double d)
Atan2           Method     static System.Double Atan2(Double y, Double x)
BigMul          Method     static System.Int64 BigMul(Int32 a, Int32 b)
Ceiling         Method     static System.Double Ceiling(Double a), static Sy...
Cos             Method     static System.Double Cos(Double d)
Cosh            Method     static System.Double Cosh(Double value)
DivRem          Method     static System.Int32 DivRem(Int32 a, Int32 b, Int3...
Equals          Method     static System.Boolean Equals(Object objA, Object ...
Exp             Method     static System.Double Exp(Double d)
Floor           Method     static System.Double Floor(Double d), static Syst...
IEEERemainder   Method     static System.Double IEEERemainder(Double x, Doub...
Log             Method     static System.Double Log(Double d), static System...
Log10           Method     static System.Double Log10(Double d)
Max             Method     static System.SByte Max(SByte val1, SByte val2), ...
Min             Method     static System.SByte Min(SByte val1, SByte val2), ...
Pow             Method     static System.Double Pow(Double x, Double y)
ReferenceEquals Method     static System.Boolean ReferenceEquals(Object objA...
Round           Method     static System.Double Round(Double a), static Syst...
Sign            Method     static System.Int32 Sign(SByte value), static Sys...
Sin             Method     static System.Double Sin(Double a)
Sinh            Method     static System.Double Sinh(Double value)
Sqrt            Method     static System.Double Sqrt(Double d)
Tan             Method     static System.Double Tan(Double a)
Tanh            Method     static System.Double Tanh(Double value)
Truncate        Method     static System.Decimal Truncate(Decimal d), static...
```

<span data-ttu-id="3d7a0-136">Spowoduje to wyświetlenie kilka metod matematycznych.</span><span class="sxs-lookup"><span data-stu-id="3d7a0-136">This displays several mathematical methods.</span></span> <span data-ttu-id="3d7a0-137">Poniżej przedstawiono listę poleceń, które pokazują, jak działają niektóre typowe metody:</span><span class="sxs-lookup"><span data-stu-id="3d7a0-137">Here is a list of commands that demonstrate how some of the common methods work:</span></span>

```
PS> [System.Math]::Sqrt(9)
3
PS> [System.Math]::Pow(2,3)
8
PS> [System.Math]::Floor(3.3)
3
PS> [System.Math]::Floor(-3.3)
-4
PS> [System.Math]::Ceiling(3.3)
4
PS> [System.Math]::Ceiling(-3.3)
-3
PS> [System.Math]::Max(2,7)
7
PS> [System.Math]::Min(2,7)
2
PS> [System.Math]::Truncate(9.3)
9
PS> [System.Math]::Truncate(-9.3)
-9
```