---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: "Przy użyciu klasy statyczne i metody"
ms.assetid: 418ad766-afa6-4b8c-9a44-471889af7fd9
ms.openlocfilehash: fe41c7d6b45564e7b5bc2b922a18587c9745e26d
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2017
---
# <a name="using-static-classes-and-methods"></a>Przy użyciu klasy statyczne i metody
Nie wszystkie klasy .NET Framework, można utworzyć za pomocą **New-Object**. Na przykład, jeśli próbujesz utworzyć **System.Environment** lub **System.Math** obiekt z **New-Object**, otrzymasz następujące komunikaty o błędach:

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

Te błędy, ponieważ nie istnieje sposób można utworzyć nowego obiektu z tych klas. Te klasy są bibliotek odwołania metod i właściwości, które nie ulegają zmianie stanu. Nie trzeba je utworzyć, możesz po prostu użyć ich. Klasy i metody, takie jak te są nazywane *klasy statyczne* , ponieważ nie są tworzone, zniszczony lub zmienione. Aby to wyczyść udostępniamy przykłady, które używają klasy statyczne.

### <a name="getting-environment-data-with-systemenvironment"></a>Pobieranie danych środowiska z System.Environment
Zwykle pierwszym krokiem podczas pracy z obiektu w programie Windows PowerShell jest na potrzeby dowiedzieć się, jakie elementy członkowskie zawiera element członkowski Get. Z klasy statyczne proces jest nieco inny, ponieważ rzeczywista klasa nie jest obiektem.

#### <a name="referring-to-the-static-systemenvironment-class"></a>Odwołanie do klasy statycznej System.Environment
Mogą odwoływać się do klasy statycznej, wpisując nazwę klasy w nawiasy kwadratowe. Na przykład mogą odwoływać się do **System.Environment** , wpisując nazwę w nawiasach kwadratowych. Dzięki temu przedstawia niektóre informacje typu ogólnego:

```
PS> [System.Environment]

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     False    Environment                              System.Object
```

> [!NOTE]
> Jak wspomniano wcześniej, programu Windows PowerShell automatycznie dołącza "**systemu.**" wpisanie nazwy, gdy używasz **New-Object**. To samo spowodowany przy użyciu nazwy typu w nawiasach kwadratowych, więc można określić  **\[System.Environment]** jako  **\[środowiska]**.

**System.Environment** klasa zawiera ogólne informacje na temat środowiska pracy dla bieżącego procesu, który jest powershell.exe podczas pracy w programie Windows PowerShell.

Jeśli użytkownik próbuje wyświetlić szczegóły dotyczące tej klasy, wpisując  **\[System.Environment] | Element członkowski GET**, typ obiektu jest raportowane jako **System.RuntimeType** , a nie **System.Environment**:

```
PS> [System.Environment] | Get-Member

   TypeName: System.RuntimeType
```

Aby wyświetlić statyczne elementy członkowskie z elementem członkowskim Get, określ **statycznych** parametru:

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

Firma Microsoft można teraz wybrać właściwości z System.Environment.

#### <a name="displaying-static-properties-of-systemenvironment"></a>Wyświetlanie właściwości statycznej System.Environment
Właściwości System.Environment również są statyczne i musi zostać określona w inny sposób niż normalne właściwości. Używamy **::** wskazująca na program Windows PowerShell, która ma być współpracować z statycznej metody lub właściwości. Aby wyświetlić polecenia, który został użyty do uruchomienia programu Windows PowerShell, sprawdzamy **CommandLine** właściwości, wpisując:

```
PS> [System.Environment]::Commandline
"C:\Program Files\Windows PowerShell\v1.0\powershell.exe"
```

Aby sprawdzić wersję systemu operacyjnego, należy wyświetlić właściwości OSVersion, wpisując:

```
PS> [System.Environment]::OSVersion

           Platform ServicePack         Version             VersionString
           -------- -----------         -------             -------------
            Win32NT Service Pack 2      5.1.2600.131072     Microsoft Windows...
```

Można sprawdzić, czy komputer jest zamykany przez wyświetlanie **HasShutdownStarted** właściwości:

```
PS> [System.Environment]::HasShutdownStarted
False
```

### <a name="doing-math-with-systemmath"></a>Wykonanie matematyczne z System.Math
Klasa statyczna System.Math jest przydatne w przypadku wykonywania pewnych operacji matematycznych. Ważne elementy członkowskie **System.Math** przede wszystkim metody, których można wyświetlić przy użyciu **elementu członkowskiego Get**.

> [!NOTE]
> System.Math ma kilka metod o tej samej nazwie, ale różnią się one według typu ich parametrów.

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

Spowoduje to wyświetlenie kilka metod matematycznych. Poniżej przedstawiono listę poleceń, które pokazują, jak działają niektóre typowe metody:

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

