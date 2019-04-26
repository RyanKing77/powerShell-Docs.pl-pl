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
ms.openlocfilehash: fb113086ce89e4becff9bcaf3232905fde2bf610
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068814"
---
# <a name="adding-parameters-that-process-command-line-input"></a><span data-ttu-id="30ecb-102">Dodawanie parametrów, które przetwarzają dane wejściowe wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="30ecb-102">Adding Parameters That Process Command-Line Input</span></span>

<span data-ttu-id="30ecb-103">Jedno źródło danych wejściowych dla polecenia cmdlet jest wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="30ecb-103">One source of input for a cmdlet is the command line.</span></span> <span data-ttu-id="30ecb-104">W tym temacie opisano sposób dodawania parametrów do **Get-Proc** polecenia cmdlet (opisanego w [tworzenia Your pierwsze polecenie Cmdlet](./creating-a-cmdlet-without-parameters.md)) tak, aby polecenie cmdlet może przetwarzać dane wejściowe z komputera lokalnego, w oparciu o jawne obiekty są przekazywane do polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="30ecb-104">This topic describes how to add a parameter to the **Get-Proc** cmdlet (which is described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process input from the local computer based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="30ecb-105">**Get-Proc** polecenia cmdlet opisane tutaj pobiera procesów na podstawie ich nazw, a następnie wyświetla informacje dotyczące procesów w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="30ecb-105">The **Get-Proc** cmdlet described here retrieves processes based on their names, and then displays information about the processes at a command prompt.</span></span>

<span data-ttu-id="30ecb-106">Poniższe sekcje są przedstawione w tym temacie:</span><span class="sxs-lookup"><span data-stu-id="30ecb-106">The following sections are in this topic:</span></span>

- [<span data-ttu-id="30ecb-107">Definiowanie klasy polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="30ecb-107">Defining the Cmdlet Class</span></span>](#Defining-the-Cmdlet-Class)

- [<span data-ttu-id="30ecb-108">Deklarowanie parametrów</span><span class="sxs-lookup"><span data-stu-id="30ecb-108">Declaring Parameters</span></span>](#Declaring-Parameters)

- [<span data-ttu-id="30ecb-109">Obsługa Walidacja parametru</span><span class="sxs-lookup"><span data-stu-id="30ecb-109">Supporting Parameter Validation</span></span>](#Supporting-Parameter-Validation)

- [<span data-ttu-id="30ecb-110">Zastępowanie metody przetwarzania danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="30ecb-110">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="30ecb-111">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="30ecb-111">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="30ecb-112">Definiowanie typów obiektów i formatowanie</span><span class="sxs-lookup"><span data-stu-id="30ecb-112">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="30ecb-113">Tworzenie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="30ecb-113">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="30ecb-114">Testowanie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="30ecb-114">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="30ecb-115">Definiowanie klasy polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="30ecb-115">Defining the Cmdlet Class</span></span>

<span data-ttu-id="30ecb-116">Pierwszym krokiem w procesie tworzenia polecenia cmdlet jest polecenie cmdlet nazewnictwa i deklarację klasy .NET Framework, która implementuje polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="30ecb-116">The first step in cmdlet creation is cmdlet naming and the declaration of the .NET Framework class that implements the cmdlet.</span></span> <span data-ttu-id="30ecb-117">To polecenie cmdlet pobiera informacje o procesu, więc nazwa zlecenie wybrane w tym miejscu jest "Get".</span><span class="sxs-lookup"><span data-stu-id="30ecb-117">This cmdlet retrieves process information, so the verb name chosen here is "Get."</span></span> <span data-ttu-id="30ecb-118">(Prawie dowolny rodzaj polecenia cmdlet, który jest zdolny do pobierania informacji o może przetwarzać dane wejściowe wiersza polecenia). Aby uzyskać więcej informacji na temat polecenia cmdlet zatwierdzonych czasowników, zobacz [nazwy zlecenie poleceń Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="30ecb-118">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="30ecb-119">Poniżej przedstawiono deklarację klasy dla **Get-Proc** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="30ecb-119">Here's the class declaration for the **Get-Proc** cmdlet.</span></span> <span data-ttu-id="30ecb-120">Szczegółowe informacje o tej definicji znajdują się w [tworzenia Your pierwsze polecenie Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="30ecb-120">Details about this definition are provided in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a><span data-ttu-id="30ecb-121">Deklarowanie parametrów</span><span class="sxs-lookup"><span data-stu-id="30ecb-121">Declaring Parameters</span></span>

<span data-ttu-id="30ecb-122">Parametr polecenia cmdlet umożliwia użytkownikowi podanie danych wejściowych do polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="30ecb-122">A cmdlet parameter enables the user to provide input to the cmdlet.</span></span> <span data-ttu-id="30ecb-123">W poniższym przykładzie **Get-Proc** i `Get-Member` są nazwami potokowe poleceń cmdlet i `MemberType` jest parametrem `Get-Member` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="30ecb-123">In the following example, **Get-Proc** and `Get-Member` are the names of pipelined cmdlets, and `MemberType` is a parameter for the `Get-Member` cmdlet.</span></span> <span data-ttu-id="30ecb-124">Parametr ma argument "property".</span><span class="sxs-lookup"><span data-stu-id="30ecb-124">The parameter has the argument "property."</span></span>

<span data-ttu-id="30ecb-125">**PS > get-proc; `get-member` membertype — właściwość**</span><span class="sxs-lookup"><span data-stu-id="30ecb-125">**PS> get-proc ; `get-member` -membertype property**</span></span>

<span data-ttu-id="30ecb-126">Aby zadeklarować parametry polecenia cmdlet, należy najpierw zdefiniować właściwości, które reprezentują parametry.</span><span class="sxs-lookup"><span data-stu-id="30ecb-126">To declare parameters for a cmdlet, you must first define the properties that represent the parameters.</span></span> <span data-ttu-id="30ecb-127">W **Get-Proc** jest jedynym parametrem polecenia cmdlet `Name`, która w tym przypadku reprezentuje nazwę obiektu procesu .NET Framework do pobrania.</span><span class="sxs-lookup"><span data-stu-id="30ecb-127">In the **Get-Proc** cmdlet, the only parameter is `Name`, which in this case represents the name of the .NET Framework process object to retrieve.</span></span> <span data-ttu-id="30ecb-128">W związku z tym klasa polecenia cmdlet definiuje właściwość typu String, aby zaakceptować tablicę nazw.</span><span class="sxs-lookup"><span data-stu-id="30ecb-128">Therefore, the cmdlet class defines a property of type string to accept an array of names.</span></span>

<span data-ttu-id="30ecb-129">Poniżej przedstawiono deklaracji parametru pod kątem `Name` parametru **Get-Proc** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="30ecb-129">Here's the parameter declaration for the `Name` parameter of the **Get-Proc** cmdlet.</span></span>

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

<span data-ttu-id="30ecb-130">Aby poinformować środowiska uruchomieniowego programu Windows PowerShell, które ta właściwość jest `Name` parametru [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) definicji właściwości jest dodawany atrybut.</span><span class="sxs-lookup"><span data-stu-id="30ecb-130">To inform the Windows PowerShell runtime that this property is the `Name` parameter, a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute is added to the property definition.</span></span> <span data-ttu-id="30ecb-131">Podstawowa składnia do deklarowania ten atrybut jest `[Parameter()]`.</span><span class="sxs-lookup"><span data-stu-id="30ecb-131">The basic syntax for declaring this attribute is `[Parameter()]`.</span></span>

> [!NOTE]
> <span data-ttu-id="30ecb-132">Parametr musi być jawnie oznaczone jako publiczne.</span><span class="sxs-lookup"><span data-stu-id="30ecb-132">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="30ecb-133">Parametry, które nie są oznaczane jako publicznego domyślnego wewnętrznego i nie można odnaleźć środowiska uruchomieniowego programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="30ecb-133">Parameters that are not marked as public default to internal and are not found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="30ecb-134">To polecenie cmdlet używa tablicę ciągów dla `Name` parametru.</span><span class="sxs-lookup"><span data-stu-id="30ecb-134">This cmdlet uses an array of strings for the `Name` parameter.</span></span> <span data-ttu-id="30ecb-135">Jeśli to możliwe Twojego polecenia cmdlet powinny również zdefiniować parametr jako tablicę, ponieważ umożliwia to polecenie cmdlet, aby zaakceptować więcej niż jeden element.</span><span class="sxs-lookup"><span data-stu-id="30ecb-135">If possible, your cmdlet should also define a parameter as an array, because this allows the cmdlet to accept more than one item.</span></span>

#### <a name="things-to-remember-about-parameter-definitions"></a><span data-ttu-id="30ecb-136">Warto zapamiętać o definicjami parametrów</span><span class="sxs-lookup"><span data-stu-id="30ecb-136">Things to Remember About Parameter Definitions</span></span>

- <span data-ttu-id="30ecb-137">Wstępnie zdefiniowane programu Windows PowerShell parametru nazwy i typy danych powinny zostać ponownie użyte możliwie najlepiej upewnić się, że Twojego polecenia cmdlet jest zgodna z poleceń cmdlet programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="30ecb-137">Predefined Windows PowerShell parameter names and data types should be reused as much as possible to ensure that your cmdlet is compatible with Windows PowerShell cmdlets.</span></span> <span data-ttu-id="30ecb-138">Na przykład, jeśli wszystkie polecenia cmdlet używane jest wstępnie zdefiniowane `Id` Nazwa parametru do identyfikacji zasobu, użytkownik będzie łatwo zrozumieć znaczenie parametru, niezależnie od tego, jakie polecenia cmdlet używają.</span><span class="sxs-lookup"><span data-stu-id="30ecb-138">For example, if all cmdlets use the predefined `Id` parameter name to identify a resource, user will easily understand the meaning of the parameter, regardless of what cmdlet they are using.</span></span> <span data-ttu-id="30ecb-139">Po prostu nazwy parametrów, wykonaj te same zasady, które są używane dla nazwy zmiennych w środowisku uruchomieniowym języka (wspólnego CLR).</span><span class="sxs-lookup"><span data-stu-id="30ecb-139">Basically, parameter names follow the same rules as those used for variable names in the common language runtime (CLR).</span></span> <span data-ttu-id="30ecb-140">Aby uzyskać więcej informacji o nazwach parametrów, zobacz [nazwy parametrów polecenia Cmdlet](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span><span class="sxs-lookup"><span data-stu-id="30ecb-140">For more information about parameter naming, see [Cmdlet Parameter Names](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span></span>

- <span data-ttu-id="30ecb-141">Program Windows PowerShell rezerwuje kilka nazw parametrów, aby zapewnić spójne środowisko użytkownika.</span><span class="sxs-lookup"><span data-stu-id="30ecb-141">Windows PowerShell reserves a few parameter names to provide a consistent user experience.</span></span> <span data-ttu-id="30ecb-142">Nie używaj tych nazw parametrów: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, i `OutBuffer`.</span><span class="sxs-lookup"><span data-stu-id="30ecb-142">Do not use these parameter names: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, and `OutBuffer`.</span></span> <span data-ttu-id="30ecb-143">Ponadto następujące aliasy dla tych nazw parametrów są zarezerwowane: `vb`, `db`, `ea`, `ev`, `ov`, i `ob`.</span><span class="sxs-lookup"><span data-stu-id="30ecb-143">Additionally, the following aliases for these parameter names are reserved: `vb`, `db`, `ea`, `ev`, `ov`, and `ob`.</span></span>

- <span data-ttu-id="30ecb-144">`Name` jest to nazwa proste i typowych parametrów, zalecane w przypadku poleceń cmdlet.</span><span class="sxs-lookup"><span data-stu-id="30ecb-144">`Name` is a simple and common parameter name, recommended for use in your cmdlets.</span></span> <span data-ttu-id="30ecb-145">Zaleca się wybrać nazwę parametru następująco niż złożone, unikatowe dla określonego polecenia cmdlet i trudne do zapamiętania nazwę.</span><span class="sxs-lookup"><span data-stu-id="30ecb-145">It is better to choose a parameter name like this than a complex name that is unique to a specific cmdlet and hard to remember.</span></span>

- <span data-ttu-id="30ecb-146">Parametry są bez uwzględniania wielkości liter w programie Windows PowerShell, mimo że domyślnie powłoki zachowuje wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="30ecb-146">Parameters are case-insensitive in Windows PowerShell, although by default the shell preserves case.</span></span> <span data-ttu-id="30ecb-147">Uwzględnianie wielkości liter argumentów, zależy od działania polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="30ecb-147">Case-sensitivity of the arguments depends on the operation of the cmdlet.</span></span> <span data-ttu-id="30ecb-148">Argumenty są przekazywane do parametru, jak określono w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="30ecb-148">Arguments are passed to a parameter as specified at the command line.</span></span>

- <span data-ttu-id="30ecb-149">Przykłady innych deklaracji parametrów, zobacz [parametry polecenia Cmdlet](./cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="30ecb-149">For examples of other parameter declarations, see [Cmdlet Parameters](./cmdlet-parameters.md).</span></span>

## <a name="declaring-parameters-as-positional-or-named"></a><span data-ttu-id="30ecb-150">Deklarowanie parametry pozycyjne lub nazwane</span><span class="sxs-lookup"><span data-stu-id="30ecb-150">Declaring Parameters as Positional or Named</span></span>

<span data-ttu-id="30ecb-151">Polecenia cmdlet należy ustawić każdy parametr jako parametr pozycyjne i nazwane.</span><span class="sxs-lookup"><span data-stu-id="30ecb-151">A cmdlet must set each parameter as either a positional or named parameter.</span></span> <span data-ttu-id="30ecb-152">Oba rodzaje parametrów akceptuje pojedynczy argumentów, wiele argumentów rozdzielonych przecinkami, a ustawienia Boolean.</span><span class="sxs-lookup"><span data-stu-id="30ecb-152">Both kinds of parameters accept single arguments, multiple arguments separated by commas, and Boolean settings.</span></span> <span data-ttu-id="30ecb-153">Parametr logiczny, nazywany również *Przełącz*, obsługuje tylko logiczną ustawienia.</span><span class="sxs-lookup"><span data-stu-id="30ecb-153">A Boolean parameter, also called a *switch*, handles only Boolean settings.</span></span> <span data-ttu-id="30ecb-154">Przełącznik służy do wykrycia obecności parametru.</span><span class="sxs-lookup"><span data-stu-id="30ecb-154">The switch is used to determine the presence of the parameter.</span></span> <span data-ttu-id="30ecb-155">Zalecaną wartością domyślną jest `false`.</span><span class="sxs-lookup"><span data-stu-id="30ecb-155">The recommended default is `false`.</span></span>

<span data-ttu-id="30ecb-156">Przykład **Get-Proc** definiuje polecenie cmdlet `Name` parametru jako parametr pozycyjne od pozycji 0.</span><span class="sxs-lookup"><span data-stu-id="30ecb-156">The sample **Get-Proc** cmdlet defines the `Name` parameter as a positional parameter with position 0.</span></span> <span data-ttu-id="30ecb-157">Oznacza to, że pierwszy argument, który użytkownik wprowadza w wierszu polecenia jest automatycznie wstawiany dla tego parametru.</span><span class="sxs-lookup"><span data-stu-id="30ecb-157">This means that the first argument the user enters on the command line is automatically inserted for this parameter.</span></span> <span data-ttu-id="30ecb-158">Jeśli chcesz zdefiniować nazwany parametr, dla którego użytkownik musi określić nazwę parametru w wierszu polecenia należy pozostawić `Position` — słowo kluczowe z deklaracji atrybutu.</span><span class="sxs-lookup"><span data-stu-id="30ecb-158">If you want to define a named parameter, for which the user must specify the parameter name from the command line, leave the `Position` keyword out of the attribute declaration.</span></span>

> [!NOTE]
> <span data-ttu-id="30ecb-159">Chyba, że parametry muszą nosić, zaleca się wykonanie najczęściej używane parametry pozycyjne tak, aby użytkownicy nie będą musieli wpisać nazwę parametru.</span><span class="sxs-lookup"><span data-stu-id="30ecb-159">Unless parameters must be named, we recommend that you make the most-used parameters positional so that users will not have to type the parameter name.</span></span>

## <a name="declaring-parameters-as-mandatory-or-optional"></a><span data-ttu-id="30ecb-160">Deklarowanie parametrów jako wymagany lub opcjonalny</span><span class="sxs-lookup"><span data-stu-id="30ecb-160">Declaring Parameters as Mandatory or Optional</span></span>

<span data-ttu-id="30ecb-161">Polecenia cmdlet, należy ustawić każdy parametr jako opcjonalny lub to parametr obowiązkowy.</span><span class="sxs-lookup"><span data-stu-id="30ecb-161">A cmdlet must set each parameter as either an optional or a mandatory parameter.</span></span> <span data-ttu-id="30ecb-162">W przykładzie **Get-Proc** polecenia cmdlet, `Name` parametr jest definiowany jako opcjonalną, ponieważ `Mandatory` — słowo kluczowe nie jest ustawiona w deklaracji atrybutu.</span><span class="sxs-lookup"><span data-stu-id="30ecb-162">In the sample **Get-Proc** cmdlet, the `Name` parameter is defined as optional because the `Mandatory` keyword is not set in the attribute declaration.</span></span>

## <a name="supporting-parameter-validation"></a><span data-ttu-id="30ecb-163">Obsługa Walidacja parametru</span><span class="sxs-lookup"><span data-stu-id="30ecb-163">Supporting Parameter Validation</span></span>

<span data-ttu-id="30ecb-164">Przykład **Get-Proc** polecenie cmdlet dodaje atrybut walidacji danych wejściowych [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), `Name` parametru, aby włączyć weryfikację, dane wejściowe nie jest ani `null` ani pusta.</span><span class="sxs-lookup"><span data-stu-id="30ecb-164">The sample **Get-Proc** cmdlet adds an input validation attribute, [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), to the `Name` parameter to enable validation that the input is neither `null` nor empty.</span></span> <span data-ttu-id="30ecb-165">Ten atrybut jest jednym z kilku atrybutów sprawdzania poprawności, udostępniane przez środowisko Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="30ecb-165">This attribute is one of several validation attributes provided by Windows PowerShell.</span></span> <span data-ttu-id="30ecb-166">Aby zapoznać się z przykładami innych atrybutów sprawdzania poprawności, zobacz [sprawdzanie poprawności wprowadzania parametrów](./validating-parameter-input.md).</span><span class="sxs-lookup"><span data-stu-id="30ecb-166">For examples of other validation attributes, see [Validating Parameter Input](./validating-parameter-input.md).</span></span>

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="30ecb-167">Zastępowanie metody przetwarzania danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="30ecb-167">Overriding an Input Processing Method</span></span>

<span data-ttu-id="30ecb-168">W przypadku Twojego polecenia cmdlet do obsługi danych wejściowych wiersza polecenia, musi ono przesłonić odpowiedniej metody przetwarzania danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="30ecb-168">If your cmdlet is to handle command-line input, it must override the appropriate input processing methods.</span></span> <span data-ttu-id="30ecb-169">Metody podstawowe przetwarzania danych wejściowych wprowadzonych w temacie [tworzenia Your pierwsze polecenie Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="30ecb-169">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="30ecb-170">**Get-Proc** polecenie cmdlet zastępuje [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody, aby obsłużyć `Name` parametr danych wejściowych dostarczonych przez użytkownika lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="30ecb-170">The **Get-Proc** cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="30ecb-171">Jeśli nazwa nie zostanie podany, ta metoda pobiera procesów dla każdej nazwy żądanej procesu lub wszystkich procesów.</span><span class="sxs-lookup"><span data-stu-id="30ecb-171">This method gets the processes for each requested process name, or all for processes if no name is provided.</span></span> <span data-ttu-id="30ecb-172">Należy zauważyć, że w [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), wywołanie [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) znajdują się dane wyjściowe mechanizm umożliwiający wysyłanie danych wyjściowych obiektów do potoku.</span><span class="sxs-lookup"><span data-stu-id="30ecb-172">Notice that in [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="30ecb-173">Drugi parametr to wywołanie `enumerateCollection`, jest równa `true` poinformować wyliczyć tablicy danych wyjściowych obiektów procesów i zapisać jeden proces naraz w wierszu polecenia środowiska uruchomieniowego programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="30ecb-173">The second parameter of this call, `enumerateCollection`, is set to `true` to inform the Windows PowerShell runtime to enumerate the output array of process objects and write one process at a time to the command line.</span></span>

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

## <a name="code-sample"></a><span data-ttu-id="30ecb-174">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="30ecb-174">Code Sample</span></span>

<span data-ttu-id="30ecb-175">Aby uzyskać pełne C# przykładowego kodu, zobacz [przykładowe GetProcessSample02](./getprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="30ecb-175">For the complete C# sample code, see [GetProcessSample02 Sample](./getprocesssample02-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="30ecb-176">Definiowanie typów obiektów i formatowanie</span><span class="sxs-lookup"><span data-stu-id="30ecb-176">Defining Object Types and Formatting</span></span>

<span data-ttu-id="30ecb-177">Program Windows PowerShell przekazuje informacje między poleceniami cmdlet przy użyciu obiektów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="30ecb-177">Windows PowerShell passes information between cmdlets by using .NET Framework objects.</span></span> <span data-ttu-id="30ecb-178">W związku z tym polecenie cmdlet może się okazać zdefiniowanie swój własny typ, lub polecenie cmdlet może być konieczne rozszerzenie istniejącego typu dostarczane przez inne polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="30ecb-178">Consequently, a cmdlet might need to define its own type, or a cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="30ecb-179">Aby uzyskać więcej informacji na temat definiowania nowych typów lub rozszerzanie istniejących typów, zobacz [rozszerzanie typów obiektów i formatowanie](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="30ecb-179">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="30ecb-180">Tworzenie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="30ecb-180">Building the Cmdlet</span></span>

<span data-ttu-id="30ecb-181">Po zaimplementowaniu polecenia cmdlet należy zarejestrować go za pomocą programu Windows PowerShell, za pomocą przystawki programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="30ecb-181">After you implement a cmdlet, you must register it with Windows PowerShell by using a Windows PowerShell snap-in.</span></span> <span data-ttu-id="30ecb-182">Aby uzyskać więcej informacji na temat rejestrowania poleceń cmdlet, zobacz [sposób zarejestrować poleceń cmdlet, dostawców i hostowania aplikacji](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="30ecb-182">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="30ecb-183">Testowanie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="30ecb-183">Testing the Cmdlet</span></span>

<span data-ttu-id="30ecb-184">Gdy Twojego polecenia cmdlet zostanie zarejestrowane przy użyciu programu Windows PowerShell, można ją przetestować, uruchamiając go w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="30ecb-184">When your cmdlet is registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="30ecb-185">Poniżej przedstawiono dwa sposoby, aby przetestować kod, aby uzyskać przykładowe polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="30ecb-185">Here are two ways to test the code for the sample cmdlet.</span></span> <span data-ttu-id="30ecb-186">Aby uzyskać więcej informacji o korzystaniu z poleceń cmdlet w wierszu polecenia, zobacz [wprowadzenie do programu Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="30ecb-186">For more information about using cmdlets from the command line, see [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="30ecb-187">W wierszu polecenia programu Windows PowerShell Użyj następującego polecenia, aby wyświetlić listę proces programu Internet Explorer, który nosi nazwę "IEXPLORE."</span><span class="sxs-lookup"><span data-stu-id="30ecb-187">At the Windows PowerShell prompt, use the following command to list the Internet Explorer process, which is named "IEXPLORE."</span></span>

    ```powershell
    PS> get-proc -name iexplore
    ```

<span data-ttu-id="30ecb-188">Zostanie wyświetlone następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="30ecb-188">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- <span data-ttu-id="30ecb-189">Aby wyświetlić listę procesów programu Internet Explorer, Outlook i Notatnik, o nazwie "IEXPLORE", "OUTLOOK" i "NOTATNIK", użyj następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="30ecb-189">To list the Internet Explorer, Outlook, and Notepad processes named "IEXPLORE," "OUTLOOK," and "NOTEPAD," use the following command.</span></span> <span data-ttu-id="30ecb-190">W przypadku wielu procesów, są wyświetlane wszystkie z nich.</span><span class="sxs-lookup"><span data-stu-id="30ecb-190">If there are multiple processes, all of them are displayed.</span></span>

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

<span data-ttu-id="30ecb-191">Zostanie wyświetlone następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="30ecb-191">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a><span data-ttu-id="30ecb-192">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="30ecb-192">See Also</span></span>

[<span data-ttu-id="30ecb-193">Dodając parametry, z których potok przetwarzania danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="30ecb-193">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="30ecb-194">Tworzenie swojej pierwszej polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="30ecb-194">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="30ecb-195">Formatowanie i rozszerzanie typy obiektów</span><span class="sxs-lookup"><span data-stu-id="30ecb-195">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="30ecb-196">Jak zarejestrować poleceń cmdlet, dostawców i aplikacji hosta</span><span class="sxs-lookup"><span data-stu-id="30ecb-196">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="30ecb-197">Dokumentacja programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="30ecb-197">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="30ecb-198">Przykłady polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="30ecb-198">Cmdlet Samples</span></span>](./cmdlet-samples.md)
