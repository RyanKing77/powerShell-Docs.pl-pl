---
title: Dodając parametry, które przetwarzają dane wejściowe wiersza polecenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], parameters
- Get-Proc cmdlet [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], command line input
- command line input [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], creating
ms.assetid: da0b32f8-7b51-440e-a061-3177b5759e0e
caps.latest.revision: 9
ms.openlocfilehash: c9ad84c5bcb6826fcf51db9a1f1a578a65a1f275
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854951"
---
# <a name="adding-parameters-that-process-command-line-input"></a><span data-ttu-id="95163-102">Dodawanie parametrów, które przetwarzają dane wejściowe wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="95163-102">Adding Parameters That Process Command-Line Input</span></span>

<span data-ttu-id="95163-103">Jedno źródło danych wejściowych dla polecenia cmdlet jest wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="95163-103">One source of input for a cmdlet is the command line.</span></span> <span data-ttu-id="95163-104">W tym temacie opisano sposób dodawania parametrów do **Get-Proc** polecenia cmdlet (opisanego w [tworzenia Your pierwsze polecenie Cmdlet](./creating-a-cmdlet-without-parameters.md)) tak, aby polecenie cmdlet może przetwarzać dane wejściowe z komputera lokalnego, w oparciu o jawne obiekty są przekazywane do polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="95163-104">This topic describes how to add a parameter to the **Get-Proc** cmdlet (which is described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process input from the local computer based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="95163-105">**Get-Proc** polecenia cmdlet opisane tutaj pobiera procesów na podstawie ich nazw, a następnie wyświetla informacje dotyczące procesów w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="95163-105">The **Get-Proc** cmdlet described here retrieves processes based on their names, and then displays information about the processes at a command prompt.</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="95163-106">Definiowanie klasy polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="95163-106">Defining the Cmdlet Class</span></span>

<span data-ttu-id="95163-107">Pierwszym krokiem w procesie tworzenia polecenia cmdlet jest polecenie cmdlet nazewnictwa i deklarację klasy .NET Framework, która implementuje polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="95163-107">The first step in cmdlet creation is cmdlet naming and the declaration of the .NET Framework class that implements the cmdlet.</span></span> <span data-ttu-id="95163-108">To polecenie cmdlet pobiera informacje o procesu, więc nazwa zlecenie wybrane w tym miejscu jest "Get".</span><span class="sxs-lookup"><span data-stu-id="95163-108">This cmdlet retrieves process information, so the verb name chosen here is "Get."</span></span> <span data-ttu-id="95163-109">(Prawie dowolny rodzaj polecenia cmdlet, który jest zdolny do pobierania informacji o może przetwarzać dane wejściowe wiersza polecenia). Aby uzyskać więcej informacji na temat polecenia cmdlet zatwierdzonych czasowników, zobacz [nazwy zlecenie poleceń Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="95163-109">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="95163-110">Poniżej przedstawiono deklarację klasy dla **Get-Proc** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="95163-110">Here's the class declaration for the **Get-Proc** cmdlet.</span></span> <span data-ttu-id="95163-111">Szczegółowe informacje o tej definicji znajdują się w [tworzenia Your pierwsze polecenie Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="95163-111">Details about this definition are provided in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a><span data-ttu-id="95163-112">Deklarowanie parametrów</span><span class="sxs-lookup"><span data-stu-id="95163-112">Declaring Parameters</span></span>

<span data-ttu-id="95163-113">Parametr polecenia cmdlet umożliwia użytkownikowi podanie danych wejściowych do polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="95163-113">A cmdlet parameter enables the user to provide input to the cmdlet.</span></span> <span data-ttu-id="95163-114">W poniższym przykładzie **Get-Proc** i `Get-Member` są nazwami potokowe poleceń cmdlet i `MemberType` jest parametrem `Get-Member` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="95163-114">In the following example, **Get-Proc** and `Get-Member` are the names of pipelined cmdlets, and `MemberType` is a parameter for the `Get-Member` cmdlet.</span></span> <span data-ttu-id="95163-115">Parametr ma argument "property".</span><span class="sxs-lookup"><span data-stu-id="95163-115">The parameter has the argument "property."</span></span>

<span data-ttu-id="95163-116">**PS > get-proc; `get-member` membertype — właściwość**</span><span class="sxs-lookup"><span data-stu-id="95163-116">**PS> get-proc ; `get-member` -membertype property**</span></span>

<span data-ttu-id="95163-117">Aby zadeklarować parametry polecenia cmdlet, należy najpierw zdefiniować właściwości, które reprezentują parametry.</span><span class="sxs-lookup"><span data-stu-id="95163-117">To declare parameters for a cmdlet, you must first define the properties that represent the parameters.</span></span> <span data-ttu-id="95163-118">W **Get-Proc** jest jedynym parametrem polecenia cmdlet `Name`, która w tym przypadku reprezentuje nazwę obiektu procesu .NET Framework do pobrania.</span><span class="sxs-lookup"><span data-stu-id="95163-118">In the **Get-Proc** cmdlet, the only parameter is `Name`, which in this case represents the name of the .NET Framework process object to retrieve.</span></span> <span data-ttu-id="95163-119">W związku z tym klasa polecenia cmdlet definiuje właściwość typu String, aby zaakceptować tablicę nazw.</span><span class="sxs-lookup"><span data-stu-id="95163-119">Therefore, the cmdlet class defines a property of type string to accept an array of names.</span></span>

<span data-ttu-id="95163-120">Poniżej przedstawiono deklaracji parametru pod kątem `Name` parametru **Get-Proc** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="95163-120">Here's the parameter declaration for the `Name` parameter of the **Get-Proc** cmdlet.</span></span>

```csharp
/// <summary>
/// Specify the cmdlet Name parameter.
/// </summary>
  [Parameter(Position = 0)]
  [ValidateNotNullOrEmpty]
  public string[] Name
  {
    get { return processNames; }
    set { processNames = value; }
  }
  private string[] processNames;

  #endregion Parameters
```

```vb
<Parameter(Position:=0), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

<span data-ttu-id="95163-121">Aby poinformować środowiska uruchomieniowego programu Windows PowerShell, które ta właściwość jest `Name` parametru [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) definicji właściwości jest dodawany atrybut.</span><span class="sxs-lookup"><span data-stu-id="95163-121">To inform the Windows PowerShell runtime that this property is the `Name` parameter, a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute is added to the property definition.</span></span> <span data-ttu-id="95163-122">Podstawowa składnia do deklarowania ten atrybut jest `[Parameter()]`.</span><span class="sxs-lookup"><span data-stu-id="95163-122">The basic syntax for declaring this attribute is `[Parameter()]`.</span></span>

> [!NOTE]
> <span data-ttu-id="95163-123">Parametr musi być jawnie oznaczone jako publiczne.</span><span class="sxs-lookup"><span data-stu-id="95163-123">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="95163-124">Parametry, które nie są oznaczane jako publicznego domyślnego wewnętrznego i nie można odnaleźć środowiska uruchomieniowego programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="95163-124">Parameters that are not marked as public default to internal and are not found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="95163-125">To polecenie cmdlet używa tablicę ciągów dla `Name` parametru.</span><span class="sxs-lookup"><span data-stu-id="95163-125">This cmdlet uses an array of strings for the `Name` parameter.</span></span> <span data-ttu-id="95163-126">Jeśli to możliwe Twojego polecenia cmdlet powinny również zdefiniować parametr jako tablicę, ponieważ umożliwia to polecenie cmdlet, aby zaakceptować więcej niż jeden element.</span><span class="sxs-lookup"><span data-stu-id="95163-126">If possible, your cmdlet should also define a parameter as an array, because this allows the cmdlet to accept more than one item.</span></span>

#### <a name="things-to-remember-about-parameter-definitions"></a><span data-ttu-id="95163-127">Warto zapamiętać o definicjami parametrów</span><span class="sxs-lookup"><span data-stu-id="95163-127">Things to Remember About Parameter Definitions</span></span>

- <span data-ttu-id="95163-128">Wstępnie zdefiniowane programu Windows PowerShell parametru nazwy i typy danych powinny zostać ponownie użyte możliwie najlepiej upewnić się, że Twojego polecenia cmdlet jest zgodna z poleceń cmdlet programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="95163-128">Predefined Windows PowerShell parameter names and data types should be reused as much as possible to ensure that your cmdlet is compatible with Windows PowerShell cmdlets.</span></span> <span data-ttu-id="95163-129">Na przykład, jeśli wszystkie polecenia cmdlet używane jest wstępnie zdefiniowane `Id` Nazwa parametru do identyfikacji zasobu, użytkownik będzie łatwo zrozumieć znaczenie parametru, niezależnie od tego, jakie polecenia cmdlet używają.</span><span class="sxs-lookup"><span data-stu-id="95163-129">For example, if all cmdlets use the predefined `Id` parameter name to identify a resource, user will easily understand the meaning of the parameter, regardless of what cmdlet they are using.</span></span> <span data-ttu-id="95163-130">Po prostu nazwy parametrów, wykonaj te same zasady, które są używane dla nazwy zmiennych w środowisku uruchomieniowym języka (wspólnego CLR).</span><span class="sxs-lookup"><span data-stu-id="95163-130">Basically, parameter names follow the same rules as those used for variable names in the common language runtime (CLR).</span></span> <span data-ttu-id="95163-131">Aby uzyskać więcej informacji o nazwach parametrów, zobacz [nazwy parametrów polecenia Cmdlet](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span><span class="sxs-lookup"><span data-stu-id="95163-131">For more information about parameter naming, see [Cmdlet Parameter Names](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span></span>

- <span data-ttu-id="95163-132">Program Windows PowerShell rezerwuje kilka nazw parametrów, aby zapewnić spójne środowisko użytkownika.</span><span class="sxs-lookup"><span data-stu-id="95163-132">Windows PowerShell reserves a few parameter names to provide a consistent user experience.</span></span> <span data-ttu-id="95163-133">Nie używaj tych nazw parametrów: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, i `OutBuffer`.</span><span class="sxs-lookup"><span data-stu-id="95163-133">Do not use these parameter names: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, and `OutBuffer`.</span></span> <span data-ttu-id="95163-134">Ponadto następujące aliasy dla tych nazw parametrów są zarezerwowane: `vb`, `db`, `ea`, `ev`, `ov`, i `ob`.</span><span class="sxs-lookup"><span data-stu-id="95163-134">Additionally, the following aliases for these parameter names are reserved: `vb`, `db`, `ea`, `ev`, `ov`, and `ob`.</span></span>

- <span data-ttu-id="95163-135">`Name` jest to nazwa proste i typowych parametrów, zalecane w przypadku poleceń cmdlet.</span><span class="sxs-lookup"><span data-stu-id="95163-135">`Name` is a simple and common parameter name, recommended for use in your cmdlets.</span></span> <span data-ttu-id="95163-136">Zaleca się wybrać nazwę parametru następująco niż złożone, unikatowe dla określonego polecenia cmdlet i trudne do zapamiętania nazwę.</span><span class="sxs-lookup"><span data-stu-id="95163-136">It is better to choose a parameter name like this than a complex name that is unique to a specific cmdlet and hard to remember.</span></span>

- <span data-ttu-id="95163-137">Parametry są bez uwzględniania wielkości liter w programie Windows PowerShell, mimo że domyślnie powłoki zachowuje wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="95163-137">Parameters are case-insensitive in Windows PowerShell, although by default the shell preserves case.</span></span> <span data-ttu-id="95163-138">Uwzględnianie wielkości liter argumentów, zależy od działania polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="95163-138">Case-sensitivity of the arguments depends on the operation of the cmdlet.</span></span> <span data-ttu-id="95163-139">Argumenty są przekazywane do parametru, jak określono w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="95163-139">Arguments are passed to a parameter as specified at the command line.</span></span>

- <span data-ttu-id="95163-140">Przykłady innych deklaracji parametrów, zobacz [parametry polecenia Cmdlet](./cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="95163-140">For examples of other parameter declarations, see [Cmdlet Parameters](./cmdlet-parameters.md).</span></span>

## <a name="declaring-parameters-as-positional-or-named"></a><span data-ttu-id="95163-141">Deklarowanie parametry pozycyjne lub nazwane</span><span class="sxs-lookup"><span data-stu-id="95163-141">Declaring Parameters as Positional or Named</span></span>

<span data-ttu-id="95163-142">Polecenia cmdlet należy ustawić każdy parametr jako parametr pozycyjne i nazwane.</span><span class="sxs-lookup"><span data-stu-id="95163-142">A cmdlet must set each parameter as either a positional or named parameter.</span></span> <span data-ttu-id="95163-143">Oba rodzaje parametrów akceptuje pojedynczy argumentów, wiele argumentów rozdzielonych przecinkami, a ustawienia Boolean.</span><span class="sxs-lookup"><span data-stu-id="95163-143">Both kinds of parameters accept single arguments, multiple arguments separated by commas, and Boolean settings.</span></span> <span data-ttu-id="95163-144">Parametr logiczny, nazywany również *Przełącz*, obsługuje tylko logiczną ustawienia.</span><span class="sxs-lookup"><span data-stu-id="95163-144">A Boolean parameter, also called a *switch*, handles only Boolean settings.</span></span> <span data-ttu-id="95163-145">Przełącznik służy do wykrycia obecności parametru.</span><span class="sxs-lookup"><span data-stu-id="95163-145">The switch is used to determine the presence of the parameter.</span></span> <span data-ttu-id="95163-146">Zalecaną wartością domyślną jest `false`.</span><span class="sxs-lookup"><span data-stu-id="95163-146">The recommended default is `false`.</span></span>

<span data-ttu-id="95163-147">Przykład **Get-Proc** definiuje polecenie cmdlet `Name` parametru jako parametr pozycyjne od pozycji 0.</span><span class="sxs-lookup"><span data-stu-id="95163-147">The sample **Get-Proc** cmdlet defines the `Name` parameter as a positional parameter with position 0.</span></span> <span data-ttu-id="95163-148">Oznacza to, że pierwszy argument, który użytkownik wprowadza w wierszu polecenia jest automatycznie wstawiany dla tego parametru.</span><span class="sxs-lookup"><span data-stu-id="95163-148">This means that the first argument the user enters on the command line is automatically inserted for this parameter.</span></span> <span data-ttu-id="95163-149">Jeśli chcesz zdefiniować nazwany parametr, dla którego użytkownik musi określić nazwę parametru w wierszu polecenia należy pozostawić `Position` — słowo kluczowe z deklaracji atrybutu.</span><span class="sxs-lookup"><span data-stu-id="95163-149">If you want to define a named parameter, for which the user must specify the parameter name from the command line, leave the `Position` keyword out of the attribute declaration.</span></span>

> [!NOTE]
> <span data-ttu-id="95163-150">Chyba, że parametry muszą nosić, zaleca się wykonanie najczęściej używane parametry pozycyjne tak, aby użytkownicy nie będą musieli wpisać nazwę parametru.</span><span class="sxs-lookup"><span data-stu-id="95163-150">Unless parameters must be named, we recommend that you make the most-used parameters positional so that users will not have to type the parameter name.</span></span>

## <a name="declaring-parameters-as-mandatory-or-optional"></a><span data-ttu-id="95163-151">Deklarowanie parametrów jako wymagany lub opcjonalny</span><span class="sxs-lookup"><span data-stu-id="95163-151">Declaring Parameters as Mandatory or Optional</span></span>

<span data-ttu-id="95163-152">Polecenia cmdlet, należy ustawić każdy parametr jako opcjonalny lub to parametr obowiązkowy.</span><span class="sxs-lookup"><span data-stu-id="95163-152">A cmdlet must set each parameter as either an optional or a mandatory parameter.</span></span> <span data-ttu-id="95163-153">W przykładzie **Get-Proc** polecenia cmdlet, `Name` parametr jest definiowany jako opcjonalną, ponieważ `Mandatory` — słowo kluczowe nie jest ustawiona w deklaracji atrybutu.</span><span class="sxs-lookup"><span data-stu-id="95163-153">In the sample **Get-Proc** cmdlet, the `Name` parameter is defined as optional because the `Mandatory` keyword is not set in the attribute declaration.</span></span>

## <a name="supporting-parameter-validation"></a><span data-ttu-id="95163-154">Obsługa Walidacja parametru</span><span class="sxs-lookup"><span data-stu-id="95163-154">Supporting Parameter Validation</span></span>

<span data-ttu-id="95163-155">Przykład **Get-Proc** polecenie cmdlet dodaje atrybut walidacji danych wejściowych [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), `Name` parametru, aby włączyć weryfikację, dane wejściowe nie jest ani `null` ani pusta.</span><span class="sxs-lookup"><span data-stu-id="95163-155">The sample **Get-Proc** cmdlet adds an input validation attribute, [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), to the `Name` parameter to enable validation that the input is neither `null` nor empty.</span></span> <span data-ttu-id="95163-156">Ten atrybut jest jednym z kilku atrybutów sprawdzania poprawności, udostępniane przez środowisko Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="95163-156">This attribute is one of several validation attributes provided by Windows PowerShell.</span></span> <span data-ttu-id="95163-157">Aby zapoznać się z przykładami innych atrybutów sprawdzania poprawności, zobacz [sprawdzanie poprawności wprowadzania parametrów](./validating-parameter-input.md).</span><span class="sxs-lookup"><span data-stu-id="95163-157">For examples of other validation attributes, see [Validating Parameter Input](./validating-parameter-input.md).</span></span>

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="95163-158">Zastępowanie metody przetwarzania danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="95163-158">Overriding an Input Processing Method</span></span>

<span data-ttu-id="95163-159">W przypadku Twojego polecenia cmdlet do obsługi danych wejściowych wiersza polecenia, musi ono przesłonić odpowiedniej metody przetwarzania danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="95163-159">If your cmdlet is to handle command-line input, it must override the appropriate input processing methods.</span></span> <span data-ttu-id="95163-160">Metody podstawowe przetwarzania danych wejściowych wprowadzonych w temacie [tworzenia Your pierwsze polecenie Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="95163-160">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="95163-161">**Get-Proc** polecenie cmdlet zastępuje [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody, aby obsłużyć `Name` parametr danych wejściowych dostarczonych przez użytkownika lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="95163-161">The **Get-Proc** cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="95163-162">Jeśli nazwa nie zostanie podany, ta metoda pobiera procesów dla każdej nazwy żądanej procesu lub wszystkich procesów.</span><span class="sxs-lookup"><span data-stu-id="95163-162">This method gets the processes for each requested process name, or all for processes if no name is provided.</span></span> <span data-ttu-id="95163-163">Należy zauważyć, że w [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), wywołanie [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) znajdują się dane wyjściowe mechanizm umożliwiający wysyłanie danych wyjściowych obiektów do potoku.</span><span class="sxs-lookup"><span data-stu-id="95163-163">Notice that in [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="95163-164">Drugi parametr to wywołanie `enumerateCollection`, jest równa `true` poinformować wyliczyć tablicy danych wyjściowych obiektów procesów i zapisać jeden proces naraz w wierszu polecenia środowiska uruchomieniowego programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="95163-164">The second parameter of this call, `enumerateCollection`, is set to `true` to inform the Windows PowerShell runtime to enumerate the output array of process objects and write one process at a time to the command line.</span></span>

```csharp
protected override void ProcessRecord()
{
  // If no process names are passed to the cmdlet, get all processes.
  if (processNames == null)
  {
    // Write the processes to the pipeline making them available
    // to the next cmdlet. The second argument of this call tells
    // PowerShell to enumerate the array, and send one process at a
    // time to the pipeline.
    WriteObject(Process.GetProcesses(), true);
  }
  else
  {
    // If process names are passed to the cmdlet, get and write
    // the associated processes.
    foreach (string name in processNames)
    {
      WriteObject(Process.GetProcessesByName(name), true);
    }
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        Dim processes As Process()
        processes = Process.GetProcesses()
    End If

    '/ If process names are specified, write the processes to the
    '/ pipeline to display them or make them available to the next cmdlet.

    For Each name As String In processNames
        '/ The second parameter of this call tells PowerShell to enumerate the
        '/ array, and send one process at a time to the pipeline.
        WriteObject(Process.GetProcessesByName(name), True)
    Next

End Sub 'ProcessRecord
```

## <a name="code-sample"></a><span data-ttu-id="95163-165">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="95163-165">Code Sample</span></span>

<span data-ttu-id="95163-166">Aby uzyskać pełne C# przykładowego kodu, zobacz [przykładowe GetProcessSample02](./getprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="95163-166">For the complete C# sample code, see [GetProcessSample02 Sample](./getprocesssample02-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="95163-167">Definiowanie typów obiektów i formatowanie</span><span class="sxs-lookup"><span data-stu-id="95163-167">Defining Object Types and Formatting</span></span>

<span data-ttu-id="95163-168">Program Windows PowerShell przekazuje informacje między poleceniami cmdlet przy użyciu obiektów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="95163-168">Windows PowerShell passes information between cmdlets by using .NET Framework objects.</span></span> <span data-ttu-id="95163-169">W związku z tym polecenie cmdlet może się okazać zdefiniowanie swój własny typ, lub polecenie cmdlet może być konieczne rozszerzenie istniejącego typu dostarczane przez inne polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="95163-169">Consequently, a cmdlet might need to define its own type, or a cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="95163-170">Aby uzyskać więcej informacji na temat definiowania nowych typów lub rozszerzanie istniejących typów, zobacz [rozszerzanie typów obiektów i formatowanie](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="95163-170">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="95163-171">Tworzenie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="95163-171">Building the Cmdlet</span></span>

<span data-ttu-id="95163-172">Po zaimplementowaniu polecenia cmdlet należy zarejestrować go za pomocą programu Windows PowerShell, za pomocą przystawki programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="95163-172">After you implement a cmdlet, you must register it with Windows PowerShell by using a Windows PowerShell snap-in.</span></span> <span data-ttu-id="95163-173">Aby uzyskać więcej informacji na temat rejestrowania poleceń cmdlet, zobacz [sposób zarejestrować poleceń cmdlet, dostawców i hostowania aplikacji](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="95163-173">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="95163-174">Testowanie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="95163-174">Testing the Cmdlet</span></span>

<span data-ttu-id="95163-175">Gdy Twojego polecenia cmdlet zostanie zarejestrowane przy użyciu programu Windows PowerShell, można ją przetestować, uruchamiając go w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="95163-175">When your cmdlet is registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="95163-176">Poniżej przedstawiono dwa sposoby, aby przetestować kod, aby uzyskać przykładowe polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="95163-176">Here are two ways to test the code for the sample cmdlet.</span></span> <span data-ttu-id="95163-177">Aby uzyskać więcej informacji o korzystaniu z poleceń cmdlet w wierszu polecenia, zobacz [wprowadzenie do programu Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="95163-177">For more information about using cmdlets from the command line, see [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="95163-178">W wierszu polecenia programu Windows PowerShell Użyj następującego polecenia, aby wyświetlić listę proces programu Internet Explorer, który nosi nazwę "IEXPLORE."</span><span class="sxs-lookup"><span data-stu-id="95163-178">At the Windows PowerShell prompt, use the following command to list the Internet Explorer process, which is named "IEXPLORE."</span></span>

    ```powershell
    PS> get-proc -name iexplore
    ```

<span data-ttu-id="95163-179">Zostanie wyświetlone następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="95163-179">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- <span data-ttu-id="95163-180">Aby wyświetlić listę procesów programu Internet Explorer, Outlook i Notatnik, o nazwie "IEXPLORE", "OUTLOOK" i "NOTATNIK", użyj następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="95163-180">To list the Internet Explorer, Outlook, and Notepad processes named "IEXPLORE," "OUTLOOK," and "NOTEPAD," use the following command.</span></span> <span data-ttu-id="95163-181">W przypadku wielu procesów, są wyświetlane wszystkie z nich.</span><span class="sxs-lookup"><span data-stu-id="95163-181">If there are multiple processes, all of them are displayed.</span></span>

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

<span data-ttu-id="95163-182">Zostanie wyświetlone następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="95163-182">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a><span data-ttu-id="95163-183">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95163-183">See Also</span></span>

[<span data-ttu-id="95163-184">Dodając parametry, z których potok przetwarzania danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="95163-184">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="95163-185">Tworzenie swojej pierwszej polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="95163-185">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="95163-186">Formatowanie i rozszerzanie typy obiektów</span><span class="sxs-lookup"><span data-stu-id="95163-186">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="95163-187">Jak zarejestrować poleceń cmdlet, dostawców i aplikacji hosta</span><span class="sxs-lookup"><span data-stu-id="95163-187">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="95163-188">Dokumentacja programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="95163-188">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="95163-189">Przykłady polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="95163-189">Cmdlet Samples</span></span>](./cmdlet-samples.md)
