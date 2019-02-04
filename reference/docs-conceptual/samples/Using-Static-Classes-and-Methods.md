---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Używanie metod i klas statycznych
ms.assetid: 418ad766-afa6-4b8c-9a44-471889af7fd9
ms.openlocfilehash: 0f2b02c3a40365ad0335118b057a4e548c9f6535
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687034"
---
# <a name="using-static-classes-and-methods"></a>Używanie metod i klas statycznych
Nie wszystkie klasy .NET Framework, można utworzyć za pomocą **New-Object**. Na przykład, Jeśli spróbujesz utworzyć **System.Environment** lub **System.Math** obiekt z **New-Object**, uzyskasz następujące komunikaty o błędach:

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

Te błędy, ponieważ nie istnieje żaden sposób, aby utworzyć nowy obiekt z tych klas. Te klasy są odwołanie do biblioteki, metod i właściwości, które nie zmieniają stan. Nie trzeba je utworzyć, można po prostu ich użyć. Klasy i metody, takie jak te są nazywane *klas statycznych* ponieważ nie są tworzone, zniszczone lub zmienione. Aby było jasne, firma Microsoft udostępni przykłady, które używają klas statycznych.

### <a name="getting-environment-data-with-systemenvironment"></a>Pobieranie danych środowiskowych z System.Environment
Pierwszym krokiem w pracy z obiektu w programie Windows PowerShell jest zwykle, użyj Get-Member, aby dowiedzieć się, jakie elementy członkowskie zawiera. Przy użyciu klas statycznych proces jest nieco inny, ponieważ rzeczywista klasa nie jest obiektem.

#### <a name="referring-to-the-static-systemenvironment-class"></a>Odwołujące się do klasy statycznej System.Environment
Mogą odwoływać się do klasy statycznej, wpisując nazwę klasy w nawiasy kwadratowe. Na przykład, można się odwoływać do **System.Environment** , wpisując nazwę w nawiasy kwadratowe. Ten sposób są wyświetlane niektóre informacje typu ogólnego:

```
PS> [System.Environment]

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     False    Environment                              System.Object
```

> [!NOTE]
> Jak wspomniano wcześniej, programu Windows PowerShell automatycznie dołącza "**systemu.**" Aby wpisz nazwy użytkowników, gdy używasz **New-Object**. Tak samo się dzieje, gdy za pomocą nazwy typu w nawiasach kwadratowych, aby można było wprowadzić  **\[System.Environment]** jako  **\[środowiska]**.

**System.Environment** klasa zawiera ogólne informacje o środowisku pracy dla bieżącego procesu, który jest powershell.exe podczas pracy w programie Windows PowerShell.

Jeśli próbujesz wyświetlić szczegóły tej klasy, wpisując  **\[System.Environment] | Get-Member**, typ obiektu jest zgłaszany jako **System.RuntimeType** , a nie **System.Environment**:

```
PS> [System.Environment] | Get-Member

   TypeName: System.RuntimeType
```

Aby wyświetlić statyczne elementy członkowskie z elementem członkowskim Get, należy określić **statyczne** parametru:

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

Firma Microsoft można teraz wybrać właściwości, aby wyświetlić z System.Environment.

#### <a name="displaying-static-properties-of-systemenvironment"></a>Wyświetlanie właściwości statycznej System.Environment

Właściwości System.Environment również są statyczne i musi być określona w inny sposób niż normalny właściwości. Używamy **::** do wskazania do programu Windows PowerShell, które chcemy pracować statycznej metody lub właściwości. Aby wyświetlić polecenia, który został użyty do uruchomienia programu Windows PowerShell, możemy sprawdzić **CommandLine** właściwość, wpisując:

```
PS> [System.Environment]::Commandline
"C:\Program Files\Windows PowerShell\v1.0\powershell.exe"
```

Aby sprawdzić wersję systemu operacyjnego, należy wyświetlić właściwość OSVersion, wpisując:

```
PS> [System.Environment]::OSVersion

           Platform ServicePack         Version             VersionString
           -------- -----------         -------             -------------
            Win32NT Service Pack 2      5.1.2600.131072     Microsoft Windows...
```

Można sprawdzić, czy komputer jest w trakcie zamykania, wyświetlając **HasShutdownStarted** właściwości:

```
PS> [System.Environment]::HasShutdownStarted
False
```

### <a name="doing-math-with-systemmath"></a>Wykonując Math z System.Math

Klasa statyczna System.Math jest przydatne w przypadku wykonywania pewnych operacji matematycznych. Ważne elementy członkowskie **System.Math** są głównie metody, które można też wyświetlać za pomocą **Get-Member**.

> [!NOTE]
> System.Math ma kilka metod o tej samej nazwie, ale są one rozróżniane według rodzaju ich parametrów.

Wpisz następujące polecenie, aby wyświetlić listę metod **System.Math** klasy.

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

Spowoduje to wyświetlenie kilka metod matematyczne. Poniżej przedstawiono listę poleceń, które pokazują, jak działają niektóre typowe metody:

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