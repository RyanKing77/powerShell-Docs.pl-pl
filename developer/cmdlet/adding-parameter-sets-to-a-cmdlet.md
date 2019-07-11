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
ms.openlocfilehash: d330b9be1da9fbb36be324e68fd6cf2d874fc06b
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733812"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a><span data-ttu-id="ce7c8-102">Dodawanie zestawu parametrów do polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="ce7c8-102">Adding Parameter Sets to a Cmdlet</span></span>

## <a name="things-to-know-about-parameter-sets"></a><span data-ttu-id="ce7c8-103">Warto poznać zestawy parametrów</span><span class="sxs-lookup"><span data-stu-id="ce7c8-103">Things to Know About Parameter Sets</span></span>

<span data-ttu-id="ce7c8-104">Program Windows PowerShell określa parametr ustawiona jako grupa parametry, które działają razem.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-104">Windows PowerShell defines a parameter set as a group of parameters that operate together.</span></span> <span data-ttu-id="ce7c8-105">Za pomocą grupowania parametrów polecenia cmdlet, można utworzyć pojedynczego polecenia cmdlet, które można modyfikować jej funkcje, oparte na użytkownik Określa, jakie grupy parametrów.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-105">By grouping the parameters of a cmdlet, you can create a single cmdlet that can change its functionality based on what group of parameters the user specifies.</span></span>

<span data-ttu-id="ce7c8-106">Na przykład polecenia cmdlet, które używa dwóch zestawów parametrów, aby zdefiniować różne funkcje `Get-EventLog` polecenia cmdlet, które są dostarczane przez środowisko Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-106">An example of a cmdlet that uses two parameter sets to define different functionalities is the `Get-EventLog` cmdlet that is provided by Windows PowerShell.</span></span> <span data-ttu-id="ce7c8-107">To polecenie cmdlet zwraca różne informacje, gdy użytkownik określi `List` lub `LogName` parametru.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-107">This cmdlet returns different information when the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="ce7c8-108">Jeśli `LogName` parametr jest określony, polecenie cmdlet zwraca informacje o zdarzeniach w danym dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-108">If the `LogName` parameter is specified, the cmdlet returns information about the events in a given event log.</span></span> <span data-ttu-id="ce7c8-109">Jeśli `List` parametr jest określony, polecenie cmdlet zwraca informacje o dzienniku plików samodzielnie (nie informacje o zdarzeniu zawierają).</span><span class="sxs-lookup"><span data-stu-id="ce7c8-109">If the `List` parameter is specified, the cmdlet returns information about the log files themselves (not the event information they contain).</span></span> <span data-ttu-id="ce7c8-110">W tym przypadku `List` i `LogName` parametry zidentyfikować dwa zestawy oddzielny parametr.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-110">In this case, the `List` and `LogName` parameters identify two separate parameter sets.</span></span>

<span data-ttu-id="ce7c8-111">Dwie ważne czynności należy pamiętać o zestawów parametrów jest środowisko uruchomieniowe programu Windows PowerShell używa tylko jeden zestaw parametrów dla określonego składnika, i że każdy zestaw parametrów muszą mieć co najmniej jeden parametr jest unikatowa dla tego zestawu parametrów.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-111">Two important things to remember about parameter sets is that the Windows PowerShell runtime uses only one parameter set for a particular input, and that each parameter set must have at least one parameter that is unique for that parameter set.</span></span>

<span data-ttu-id="ce7c8-112">Aby zilustrować ostatni punkt, to polecenie cmdlet Stop-Proc używa trzech zestawów parametrów: `ProcessName`, `ProcessId`, i `InputObject`.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-112">To illustrate that last point, this Stop-Proc cmdlet uses three parameter sets: `ProcessName`, `ProcessId`, and `InputObject`.</span></span> <span data-ttu-id="ce7c8-113">Każda z tych zestawów parametrów ma jeden parametr, który nie znajduje się w innych zestawów parametrów.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-113">Each of these parameter sets has one parameter that is not in the other parameter sets.</span></span> <span data-ttu-id="ce7c8-114">Zestawy parametrów można udostępnić innych parametrów, ale polecenie cmdlet używa unikatowe parametry `ProcessName`, `ProcessId`, i `InputObject` do identyfikowania który zestaw parametrów, które należy używać w czasie wykonywania programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-114">The parameter sets could share other parameters, but the cmdlet uses the unique parameters `ProcessName`, `ProcessId`, and `InputObject` to identify which set of parameters that the Windows PowerShell runtime should use.</span></span>

## <a name="declaring-the-cmdlet-class"></a><span data-ttu-id="ce7c8-115">Deklarowanie klasy polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ce7c8-115">Declaring the Cmdlet Class</span></span>

<span data-ttu-id="ce7c8-116">Pierwszym krokiem w procesie tworzenia polecenia cmdlet jest zawsze nazewnictwa polecenia cmdlet i deklarowanie klasy .NET, która implementuje polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-116">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="ce7c8-117">Dla tego polecenia cmdlet zlecenie cyklu życia "Stop" jest stosowana, ponieważ polecenie cmdlet zatrzymuje procesów systemowych.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-117">For this cmdlet, the life-cycle verb "Stop" is used because the cmdlet stops system processes.</span></span> <span data-ttu-id="ce7c8-118">Nazwa rzeczownik "Proc" jest używana, ponieważ polecenie cmdlet działa na procesach.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-118">The noun name "Proc" is used because the cmdlet works on processes.</span></span> <span data-ttu-id="ce7c8-119">W poniższej deklaracji należy pamiętać, że nazwa polecenia cmdlet czasownik i rzeczownik są odzwierciedlane na nazwę klasy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-119">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span>

> [!NOTE]
> <span data-ttu-id="ce7c8-120">Aby uzyskać więcej informacji o nazwach zlecenie zatwierdzonych polecenia cmdlet, zobacz [nazwy zlecenie poleceń Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="ce7c8-120">For more information about approved cmdlet verb names, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="ce7c8-121">Poniższy kod jest w definicji klasy dla tego polecenia cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-121">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

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

## <a name="declaring-the-parameters-of-the-cmdlet"></a><span data-ttu-id="ce7c8-122">Deklarowanie parametrów polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ce7c8-122">Declaring the Parameters of the Cmdlet</span></span>

<span data-ttu-id="ce7c8-123">To polecenie cmdlet definiuje trzy parametry wymagane jako dane wejściowe do polecenia cmdlet (tych parametrów również definiować zestawy parametrów), jak również `Force` parametr, który zarządza, działanie polecenia cmdlet i `PassThru` parametr, który określa, czy wysyłane polecenia cmdlet Obiekt danych wyjściowych przez potok.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-123">This cmdlet defines three parameters needed as input to the cmdlet (these parameters also define the parameter sets), as well as a `Force` parameter that manages what the cmdlet does and a `PassThru` parameter that determines whether the cmdlet sends an output object through the pipeline.</span></span> <span data-ttu-id="ce7c8-124">Domyślnie to polecenie cmdlet nie przekazuje obiekt, za pośrednictwem potoku.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-124">By default, this cmdlet does not pass an object through the pipeline.</span></span> <span data-ttu-id="ce7c8-125">Aby uzyskać więcej informacji na temat tych ostatnich dwóch parametrów zobacz [Tworzenie polecenia Cmdlet, który modyfikuje System](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="ce7c8-125">For more information about these last two parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

### <a name="declaring-the-name-parameter"></a><span data-ttu-id="ce7c8-126">Deklarowanie parametru Name</span><span class="sxs-lookup"><span data-stu-id="ce7c8-126">Declaring the Name Parameter</span></span>

<span data-ttu-id="ce7c8-127">Tego parametru wejściowego pozwala użytkownikowi na określenie nazwy procesów, aby zostać zatrzymane.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-127">This input parameter allows the user to specify the names of the processes to be stopped.</span></span> <span data-ttu-id="ce7c8-128">Należy pamiętać, że `ParameterSetName` atrybutu słowa kluczowego [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) Określa atrybut `ProcessName` zestaw parametrów dla tego parametru.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-128">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessName` parameter set for this parameter.</span></span>

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

<span data-ttu-id="ce7c8-129">Należy zauważyć, że alias "ProcessName" znajduje się do tego parametru.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-129">Note also that the alias "ProcessName" is given to this parameter.</span></span>

### <a name="declaring-the-id-parameter"></a><span data-ttu-id="ce7c8-130">Deklarowanie parametru Id</span><span class="sxs-lookup"><span data-stu-id="ce7c8-130">Declaring the Id Parameter</span></span>

<span data-ttu-id="ce7c8-131">Tego parametru wejściowego zezwala użytkownikowi na określenie identyfikatorów procesów, aby zostać zatrzymane.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-131">This input parameter allows the user to specify the identifiers of the processes to be stopped.</span></span> <span data-ttu-id="ce7c8-132">Należy pamiętać, że `ParameterSetName` atrybutu słowa kluczowego [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) Określa atrybut `ProcessId` zestaw parametrów.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-132">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessId` parameter set.</span></span>

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

<span data-ttu-id="ce7c8-133">Należy zauważyć, że alias "ProcessId" znajduje się do tego parametru.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-133">Note also that the alias "ProcessId" is given to this parameter.</span></span>

### <a name="declaring-the-inputobject-parameter"></a><span data-ttu-id="ce7c8-134">Deklarowanie parametru InputObject</span><span class="sxs-lookup"><span data-stu-id="ce7c8-134">Declaring the InputObject Parameter</span></span>

<span data-ttu-id="ce7c8-135">Tego parametru wejściowego zezwala użytkownikowi na określenie obiektu wejściowego, który zawiera informacje o procesach, aby zostać zatrzymane.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-135">This input parameter allows the user to specify an input object that contains information about the processes to be stopped.</span></span> <span data-ttu-id="ce7c8-136">Należy pamiętać, że `ParameterSetName` atrybutu słowa kluczowego [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) Określa atrybut `InputObject` zestaw parametrów dla tego parametru.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-136">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `InputObject` parameter set for this parameter.</span></span>

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

<span data-ttu-id="ce7c8-137">Należy zauważyć, że ten parametr nie ma aliasu.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-137">Note also that this parameter has no alias.</span></span>

### <a name="declaring-parameters-in-multiple-parameter-sets"></a><span data-ttu-id="ce7c8-138">Deklarowanie parametrów w wiele zestawów parametrów</span><span class="sxs-lookup"><span data-stu-id="ce7c8-138">Declaring Parameters in Multiple Parameter Sets</span></span>

<span data-ttu-id="ce7c8-139">Mimo że musi być unikatowy parametr dla każdego zestawu parametrów, parametry mogą należeć do więcej niż jeden zestaw parametrów.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-139">Although there must be a unique parameter for each parameter set, parameters can belong to more than one parameter set.</span></span> <span data-ttu-id="ce7c8-140">W takich przypadkach należy podać parametr współużytkowany [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) deklaracji atrybutu dla każdego zestawu do którego parametr należy.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-140">In these cases, give the shared parameter a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration for each set to which that the parameter belongs.</span></span> <span data-ttu-id="ce7c8-141">Jeśli parametr wszystkie zestawy parametrów, możesz tylko trzeba zadeklarować atrybut parameter raz i nie trzeba określić nazwę zestawu parametru.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-141">If a parameter is in all parameter sets, you only have to declare the parameter attribute once and do not need to specify the parameter set name.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="ce7c8-142">Zastępowanie metody przetwarzania danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="ce7c8-142">Overriding an Input Processing Method</span></span>

<span data-ttu-id="ce7c8-143">Każdego polecenia cmdlet jest przesłonięcie metody przetwarzania danych wejściowych, w większości przypadków będzie to [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-143">Every cmdlet must override an input processing method, most often this will be the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="ce7c8-144">W tym poleceniu cmdlet [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metoda zostanie przesłonięta, tak aby polecenie cmdlet może przetwarzać dowolną liczbę procesów.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-144">In this cmdlet, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden so that the cmdlet can process any number of processes.</span></span> <span data-ttu-id="ce7c8-145">Zawiera on instrukcji Select, która wywołuje inną metodę, na podstawie której zestaw parametrów użytkownika została określona.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-145">It contains a Select statement that calls a different method based on which parameter set the user has specified.</span></span>

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

<span data-ttu-id="ce7c8-146">Metody pomocnika wywołane przez instrukcję Select nie zawiera opisu, ale możesz zobaczyć ich implementacji w cały przykładowy kod w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-146">The Helper methods called by the Select statement are not described here, but you can see their implementation in the complete code sample in the next section.</span></span>

## <a name="code-sample"></a><span data-ttu-id="ce7c8-147">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="ce7c8-147">Code Sample</span></span>

<span data-ttu-id="ce7c8-148">Aby uzyskać pełne C# przykładowego kodu, zobacz [przykładowe StopProcessSample04](./stopprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="ce7c8-148">For the complete C# sample code, see [StopProcessSample04 Sample](./stopprocesssample04-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="ce7c8-149">Definiowanie typów obiektów i formatowanie</span><span class="sxs-lookup"><span data-stu-id="ce7c8-149">Defining Object Types and Formatting</span></span>

<span data-ttu-id="ce7c8-150">Program Windows PowerShell przekazuje informacje między poleceniami cmdlet, używając obiektów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-150">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="ce7c8-151">W związku z tym polecenie cmdlet może się okazać zdefiniowanie swój własny typ, lub polecenie cmdlet może być konieczne rozszerzenie istniejącego typu dostarczane przez inne polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-151">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="ce7c8-152">Aby uzyskać więcej informacji na temat definiowania nowych typów lub rozszerzanie istniejących typów, zobacz [rozszerzanie typów obiektów i formatowanie](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="ce7c8-152">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="ce7c8-153">Tworzenie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="ce7c8-153">Building the Cmdlet</span></span>

<span data-ttu-id="ce7c8-154">Po zaimplementowaniu polecenia cmdlet, należy zarejestrować go za pomocą programu Windows PowerShell za pomocą przystawki programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-154">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="ce7c8-155">Aby uzyskać więcej informacji na temat rejestrowania poleceń cmdlet, zobacz [sposób zarejestrować poleceń cmdlet, dostawców i hostowania aplikacji](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="ce7c8-155">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="ce7c8-156">Testowanie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="ce7c8-156">Testing the Cmdlet</span></span>

<span data-ttu-id="ce7c8-157">Gdy Twoje polecenie cmdlet został zarejestrowany za pomocą programu Windows PowerShell, należy go przetestować, uruchamiając go w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-157">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="ce7c8-158">Poniżej przedstawiono niektóre testy, które pokazują sposób, w jaki `ProcessId` i `InputObject` parametry mogą służyć do testowania ich zestawów parametrów, aby zatrzymać proces.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-158">Here are some tests that show how the `ProcessId` and `InputObject` parameters can be used to test their parameter sets to stop a process.</span></span>

- <span data-ttu-id="ce7c8-159">Za pomocą programu Windows PowerShell pracę, należy uruchomić polecenie cmdlet Stop-Proc z `ProcessId` zestaw parametrów, aby zatrzymać proces, na podstawie jego identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-159">With Windows PowerShell started, run the Stop-Proc cmdlet with the `ProcessId` parameter set to stop a process based on its identifier.</span></span> <span data-ttu-id="ce7c8-160">W tym przypadku jest przy użyciu polecenia cmdlet `ProcessId` zestaw parametrów, aby zatrzymać proces.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-160">In this case, the cmdlet is using the `ProcessId` parameter set to stop the process.</span></span>

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="ce7c8-161">Za pomocą programu Windows PowerShell pracę, należy uruchomić polecenie cmdlet Stop-Proc z `InputObject` zestaw parametrów, aby zatrzymać procesy w obiekcie Notatnik pobierane przez `Get-Process` polecenia.</span><span class="sxs-lookup"><span data-stu-id="ce7c8-161">With Windows PowerShell started, run the Stop-Proc cmdlet with the `InputObject` parameter set to stop processes on the Notepad object retrieved by the `Get-Process` command.</span></span>

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="ce7c8-162">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce7c8-162">See Also</span></span>

[<span data-ttu-id="ce7c8-163">Tworzenie polecenia Cmdlet, który modyfikuje systemu</span><span class="sxs-lookup"><span data-stu-id="ce7c8-163">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="ce7c8-164">Jak utworzyć polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ce7c8-164">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="ce7c8-165">[Formatowanie i rozszerzanie typy obiektów](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="ce7c8-165">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="ce7c8-166">[Jak zarejestrować poleceń cmdlet, dostawców i aplikacji hosta](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="ce7c8-166">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="ce7c8-167">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ce7c8-167">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
