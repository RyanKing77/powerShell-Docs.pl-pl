---
title: Dodanie parametru ustawia do polecenia Cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameter sets [PowerShell Programmer's Guide]
ms.assetid: a6131db4-fd6e-45f1-bd47-17e7174afd56
caps.latest.revision: 8
ms.openlocfilehash: b02a2e0d4b0a27c261b0bc05febda7826ad5276e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849098"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a>Dodawanie zestawu parametrów do polecenia cmdlet

W tej sekcji opisano sposób dodawania zestawami parametrów do polecenia cmdlet Stop-Proc (opisanego w [Tworzenie polecenia Cmdlet, który modyfikuje System](./creating-a-cmdlet-that-modifies-the-system.md)). Podobnie jak w innych Stop-Proc poleceń cmdlet opisane w tym przewodnik, to polecenie cmdlet próbuje zatrzymać procesy, które są pobierane za pomocą polecenia cmdlet Get-Proc (opisanego w [tworzenia Your pierwsze polecenie Cmdlet](./creating-a-cmdlet-without-parameters.md)).

Tematy w tej sekcji są następujące:

- [Warto poznać zestawy parametrów](#Adding-Parameter-Sets-to-a-Cmdlet)

- [Deklarowanie klasy polecenia Cmdlet](#Declaring-the-Cmdlet-Class)

- [Deklarowanie parametrów polecenia Cmdlet](#Declaring-the-Parameters-of-the-Cmdlet)

- [Zastępowanie metody przetwarzania danych wejściowych](#Overriding-an-Input-Processing-Method)

- [Przykładowy kod](#Declaring-the-Parameters-of-the-Cmdlet)

- [Definiowanie typów obiektów i formatowanie](#Defining-Object-Types-and-Formatting)

- [Tworzenie polecenia cmdlet](#Building-the-Cmdlet)

- [Testowanie polecenia cmdlet](#Testing-the-Cmdlet)

## <a name="things-to-know-about-parameter-sets"></a>Warto poznać zestawy parametrów

Program Windows PowerShell określa parametr ustawiona jako grupa parametry, które działają razem. Za pomocą grupowania parametrów polecenia cmdlet, można utworzyć pojedynczego polecenia cmdlet, które można modyfikować jej funkcje, oparte na użytkownik Określa, jakie grupy parametrów.

Na przykład polecenia cmdlet, które używa dwóch zestawów parametrów, aby zdefiniować różne funkcje `Get-EventLog` polecenia cmdlet, które są dostarczane przez środowisko Windows PowerShell. To polecenie cmdlet zwraca różne informacje, gdy użytkownik określi `List` lub `LogName` parametru. Jeśli `LogName` parametr jest określony, polecenie cmdlet zwraca informacje o zdarzeniach w danym dziennika zdarzeń. Jeśli `List` parametr jest określony, polecenie cmdlet zwraca informacje o dzienniku plików samodzielnie (nie informacje o zdarzeniu zawierają). W tym przypadku `List` i `LogName` parametry zidentyfikować dwa zestawy oddzielny parametr.

Dwie ważne czynności należy pamiętać o zestawów parametrów jest środowisko uruchomieniowe programu Windows PowerShell używa tylko jeden zestaw parametrów dla określonego składnika, i że każdy zestaw parametrów muszą mieć co najmniej jeden parametr jest unikatowa dla tego zestawu parametrów.

Aby zilustrować ostatni punkt, to polecenie cmdlet Stop-Proc używa trzech zestawów parametrów: `ProcessName`, `ProcessId`, i `InputObject`. Każda z tych zestawów parametrów ma jeden parametr, który nie znajduje się w innych zestawów parametrów. Zestawy parametrów można udostępnić innych parametrów, ale polecenie cmdlet używa unikatowe parametry `ProcessName`, `ProcessId`, i `InputObject` do identyfikowania który zestaw parametrów, które należy używać w czasie wykonywania programu Windows PowerShell.

## <a name="declaring-the-cmdlet-class"></a>Deklarowanie klasy polecenia Cmdlet

Pierwszym krokiem w procesie tworzenia polecenia cmdlet jest zawsze nazewnictwa polecenia cmdlet i deklarowanie klasy .NET, która implementuje polecenia cmdlet. Dla tego polecenia cmdlet zlecenie cyklu życia "Stop" jest stosowana, ponieważ polecenie cmdlet zatrzymuje procesów systemowych. Nazwa rzeczownik "Proc" jest używana, ponieważ polecenie cmdlet działa na procesach. W poniższej deklaracji należy pamiętać, że nazwa polecenia cmdlet czasownik i rzeczownik są odzwierciedlane na nazwę klasy polecenia cmdlet.

> [!NOTE]
> Aby uzyskać więcej informacji o nazwach zlecenie zatwierdzonych polecenia cmdlet, zobacz [nazwy zlecenie poleceń Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Poniższy kod jest w definicji klasy dla tego polecenia cmdlet Stop-Proc.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        DefaultParameterSetName = "ProcessId",
        SupportsShouldProcess = true)]
public class StopProcCommand : PSCmdlet
```

```vb
<Cmdlet(VerbsLifecycle.Stop, "Proc", DefaultParameterSetName:="ProcessId", _
SupportsShouldProcess:=True)> _
Public Class StopProcCommand
    Inherits PSCmdlet
```

## <a name="declaring-the-parameters-of-the-cmdlet"></a>Deklarowanie parametrów polecenia Cmdlet

To polecenie cmdlet definiuje trzy parametry wymagane jako dane wejściowe do polecenia cmdlet (tych parametrów również definiować zestawy parametrów), jak również `Force` parametr, który zarządza, działanie polecenia cmdlet i `PassThru` parametr, który określa, czy wysyłane polecenia cmdlet Obiekt danych wyjściowych przez potok. Domyślnie to polecenie cmdlet nie przekazuje obiekt, za pośrednictwem potoku. Aby uzyskać więcej informacji na temat tych ostatnich dwóch parametrów zobacz [Tworzenie polecenia Cmdlet, który modyfikuje System](./creating-a-cmdlet-that-modifies-the-system.md).

### <a name="declaring-the-name-parameter"></a>Deklarowanie parametru Name

Tego parametru wejściowego pozwala użytkownikowi na określenie nazwy procesów, aby zostać zatrzymane. Należy pamiętać, że `ParameterSetName` atrybutu słowa kluczowego [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) Określa atrybut `ProcessName` zestaw parametrów dla tego parametru.

[!code-csharp[StopProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

```vb
<Parameter(Position:=0, ParameterSetName:="ProcessName", _
Mandatory:=True, _
ValueFromPipeline:=True, ValueFromPipelineByPropertyName:=True, _
HelpMessage:="The name of one or more processes to stop. " & _
    "Wildcards are permitted."), [Alias]("ProcessName")> _
Public Property Name() As String()
    Get
        Return processNames
    End Get
    Set(ByVal value As String())
        processNames = value
    End Set
End Property

Private processNames() As String
```

Należy zauważyć, że alias "ProcessName" znajduje się do tego parametru.

### <a name="declaring-the-id-parameter"></a>Deklarowanie parametru Id

Tego parametru wejściowego zezwala użytkownikowi na określenie identyfikatorów procesów, aby zostać zatrzymane. Należy pamiętać, że `ParameterSetName` atrybutu słowa kluczowego [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) Określa atrybut `ProcessId` zestaw parametrów.

```csharp
[Parameter(
           ParameterSetName = "ProcessId",
           Mandatory = true,
           ValueFromPipelineByPropertyName = true,
           ValueFromPipeline = true
)]
[Alias("ProcessId")]
public int[] Id
{
  get { return processIds; }
  set { processIds = value; }
}
private int[] processIds;
```

```vb
<Parameter(ParameterSetName:="ProcessId", _
Mandatory:=True, _
ValueFromPipelineByPropertyName:=True, _
ValueFromPipeline:=True), [Alias]("ProcessId")> _
Public Property Id() As Integer()
    Get
        Return processIds
    End Get
    Set(ByVal value As Integer())
        processIds = value
    End Set
End Property
Private processIds() As Integer
```

Należy zauważyć, że alias "ProcessId" znajduje się do tego parametru.

### <a name="declaring-the-inputobject-parameter"></a>Deklarowanie parametru InputObject

Tego parametru wejściowego zezwala użytkownikowi na określenie obiektu wejściowego, który zawiera informacje o procesach, aby zostać zatrzymane. Należy pamiętać, że `ParameterSetName` atrybutu słowa kluczowego [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) Określa atrybut `InputObject` zestaw parametrów dla tego parametru.

```csharp
[Parameter(
           ParameterSetName = "InputObject",
           Mandatory = true,
           ValueFromPipeline = true)]
public Process[] InputObject
{
  get { return inputObject; }
  set { inputObject = value; }
}
private Process[] inputObject;
```

```vb
<Parameter(ParameterSetName:="InputObject", _
Mandatory:=True, ValueFromPipeline:=True)> _
Public Property InputObject() As Process()
    Get
        Return myInputObject
    End Get
    Set(ByVal value As Process())
        myInputObject = value
    End Set
End Property
Private myInputObject() As Process
```

Należy zauważyć, że ten parametr nie ma aliasu.

### <a name="declaring-parameters-in-multiple-parameter-sets"></a>Deklarowanie parametrów w wiele zestawów parametrów

Mimo że musi być unikatowy parametr dla każdego zestawu parametrów, parametry mogą należeć do więcej niż jeden zestaw parametrów. W takich przypadkach należy podać parametr współużytkowany [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) deklaracji atrybutu dla każdego zestawu do którego parametr należy. Jeśli parametr wszystkie zestawy parametrów, możesz tylko trzeba zadeklarować atrybut parameter raz i nie trzeba określić nazwę zestawu parametru.

## <a name="overriding-an-input-processing-method"></a>Zastępowanie metody przetwarzania danych wejściowych

Każdego polecenia cmdlet jest przesłonięcie metody przetwarzania danych wejściowych, w większości przypadków będzie to [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody. W tym poleceniu cmdlet [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metoda zostanie przesłonięta, tak aby polecenie cmdlet może przetwarzać dowolną liczbę procesów. Zawiera on instrukcji Select, która wywołuje inną metodę, na podstawie której zestaw parametrów użytkownika została określona.

```csharp
protected override void ProcessRecord()
{
  switch (ParameterSetName)
  {
    case "ProcessName":
         ProcessByName();
         break;

    case "ProcessId":
         ProcessById();
         break;

    case "InputObject":
         foreach (Process process in inputObject)
         {
           SafeStopProcess(process);
         }
         break;

    default:
         throw new ArgumentException("Bad ParameterSet Name");
  } // switch (ParameterSetName...
} // ProcessRecord
```

```vb
Protected Overrides Sub ProcessRecord()
    Select Case ParameterSetName
        Case "ProcessName"
            ProcessByName()

        Case "ProcessId"
            ProcessById()

        Case "InputObject"
            Dim process As Process
            For Each process In myInputObject
                SafeStopProcess(process)
            Next process

        Case Else
            Throw New ArgumentException("Bad ParameterSet Name")
    End Select

End Sub 'ProcessRecord ' ProcessRecord
```

Metody pomocnika wywołane przez instrukcję Select nie zawiera opisu, ale możesz zobaczyć ich implementacji w cały przykładowy kod w następnej sekcji.

## <a name="code-sample"></a>Przykładowy kod

Aby uzyskać pełne C# przykładowego kodu, zobacz [przykładowe StopProcessSample04](./stopprocesssample04-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definiowanie typów obiektów i formatowanie

Program Windows PowerShell przekazuje informacje między poleceniami cmdlet, używając obiektów platformy .NET. W związku z tym polecenie cmdlet może się okazać zdefiniowanie swój własny typ, lub polecenie cmdlet może być konieczne rozszerzenie istniejącego typu dostarczane przez inne polecenie cmdlet. Aby uzyskać więcej informacji na temat definiowania nowych typów lub rozszerzanie istniejących typów, zobacz [rozszerzanie typów obiektów i formatowanie](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Tworzenie polecenia cmdlet

Po zaimplementowaniu polecenia cmdlet, należy zarejestrować go za pomocą programu Windows PowerShell za pomocą przystawki programu Windows PowerShell. Aby uzyskać więcej informacji na temat rejestrowania poleceń cmdlet, zobacz [sposób zarejestrować poleceń cmdlet, dostawców i hostowania aplikacji](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testowanie polecenia cmdlet

Gdy Twoje polecenie cmdlet został zarejestrowany za pomocą programu Windows PowerShell, należy go przetestować, uruchamiając go w wierszu polecenia. Poniżej przedstawiono niektóre testy, które pokazują sposób, w jaki `ProcessId` i `InputObject` parametry mogą służyć do testowania ich zestawów parametrów, aby zatrzymać proces.

- Za pomocą programu Windows PowerShell pracę, należy uruchomić polecenie cmdlet Stop-Proc z `ProcessId` zestaw parametrów, aby zatrzymać proces, na podstawie jego identyfikatora. W tym przypadku jest przy użyciu polecenia cmdlet `ProcessId` zestaw parametrów, aby zatrzymać proces.

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Za pomocą programu Windows PowerShell pracę, należy uruchomić polecenie cmdlet Stop-Proc z `InputObject` zestaw parametrów, aby zatrzymać procesy w obiekcie Notatnik pobierane przez `Get-Process` polecenia.

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Zobacz też

[Tworzenie polecenia Cmdlet, który modyfikuje systemu](./creating-a-cmdlet-that-modifies-the-system.md)

[Jak utworzyć polecenia Cmdlet programu Windows PowerShell](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Formatowanie i rozszerzanie typy obiektów](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Jak zarejestrować poleceń cmdlet, dostawców i aplikacji hosta](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)
