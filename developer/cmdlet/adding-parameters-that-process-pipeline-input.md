---
title: Dodając parametry, które przetwarzają dane wejściowe w potoku | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], pipeline input
- parameters [PowerShell Programmer's Guide], pipeline input
ms.assetid: 09bf70a9-7c76-4ffe-b3f0-a1d5f10a0931
caps.latest.revision: 8
ms.openlocfilehash: bd52dc8aee7975d0899083a5c2f595b17690dc33
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068763"
---
# <a name="adding-parameters-that-process-pipeline-input"></a><span data-ttu-id="e5d14-102">Dodawanie parametrów, które przetwarzają dane wejściowe potoku</span><span class="sxs-lookup"><span data-stu-id="e5d14-102">Adding Parameters that Process Pipeline Input</span></span>

<span data-ttu-id="e5d14-103">Jedno źródło danych wejściowych dla polecenia cmdlet jest obiekt w potoku, który pochodzi z nadrzędnego polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e5d14-103">One source of input for a cmdlet is an object on the pipeline that originates from an upstream cmdlet.</span></span> <span data-ttu-id="e5d14-104">W tej sekcji opisano sposób dodać parametr do polecenia cmdlet Get-Proc (opisanego w [tworzenia Your pierwsze polecenie Cmdlet](./creating-a-cmdlet-without-parameters.md)) tak, aby polecenie cmdlet może przetwarzać obiektów z potoku.</span><span class="sxs-lookup"><span data-stu-id="e5d14-104">This section describes how to add a parameter to the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process pipeline objects.</span></span>

<span data-ttu-id="e5d14-105">To polecenie cmdlet Get-Proc używa `Name` parametr, który akceptuje dane wejściowe z obiektu potok pobiera informacje o procesach z komputera lokalnego, w oparciu o podanej nazwy i następnie wyświetla informacje dotyczące procesów w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="e5d14-105">This Get-Proc cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

<span data-ttu-id="e5d14-106">Tematy w tej sekcji są następujące:</span><span class="sxs-lookup"><span data-stu-id="e5d14-106">Topics in this section include the following:</span></span>

- [<span data-ttu-id="e5d14-107">Definiowanie klasy polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e5d14-107">Defining the Cmdlet Class</span></span>](#Defining-the-Cmdlet-Class)

- [<span data-ttu-id="e5d14-108">Definiowanie danych wejściowych z potoku</span><span class="sxs-lookup"><span data-stu-id="e5d14-108">Defining Input from the Pipeline</span></span>](#Defining-Input-from-the-Pipeline)

- [<span data-ttu-id="e5d14-109">Zastępowanie metody przetwarzania danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="e5d14-109">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="e5d14-110">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="e5d14-110">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="e5d14-111">Definiowanie typów obiektów i formatowanie</span><span class="sxs-lookup"><span data-stu-id="e5d14-111">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="e5d14-112">Tworzenie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="e5d14-112">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="e5d14-113">Testowanie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="e5d14-113">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="e5d14-114">Definiowanie klasy polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e5d14-114">Defining the Cmdlet Class</span></span>

<span data-ttu-id="e5d14-115">Pierwszym krokiem w procesie tworzenia polecenia cmdlet jest zawsze nazewnictwa polecenia cmdlet i deklarowanie klasy .NET, która implementuje polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e5d14-115">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="e5d14-116">To polecenie cmdlet pobiera informacje o procesu, więc nazwę zlecenie wybrane w tym miejscu to "Get".</span><span class="sxs-lookup"><span data-stu-id="e5d14-116">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="e5d14-117">(Prawie dowolny rodzaj polecenia cmdlet, który jest zdolny do pobierania informacji o może przetwarzać dane wejściowe wiersza polecenia). Aby uzyskać więcej informacji na temat polecenia cmdlet zatwierdzonych czasowników, zobacz [nazwy zlecenie poleceń Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="e5d14-117">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="e5d14-118">Poniżej przedstawiono definicję dla tego polecenia cmdlet Get-Proc.</span><span class="sxs-lookup"><span data-stu-id="e5d14-118">The following is the definition for this Get-Proc cmdlet.</span></span> <span data-ttu-id="e5d14-119">Szczegóły tej definicji są podane w [tworzenia Your pierwsze polecenie Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e5d14-119">Details of this definition are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a><span data-ttu-id="e5d14-120">Definiowanie danych wejściowych z potoku</span><span class="sxs-lookup"><span data-stu-id="e5d14-120">Defining Input from the Pipeline</span></span>

<span data-ttu-id="e5d14-121">W tej sekcji opisano sposób definiowania danych wejściowych z potoku do polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e5d14-121">This section describes how to define input from the pipeline for a cmdlet.</span></span> <span data-ttu-id="e5d14-122">To polecenie cmdlet Get-Proc definiuje właściwość, która reprezentuje `Name` parametru, zgodnie z opisem w [dodając parametry te dane wejściowe wiersza polecenia procesu](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="e5d14-122">This Get-Proc cmdlet defines a property that represents the `Name` parameter as described in [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span> <span data-ttu-id="e5d14-123">(Zobacz tego tematu ogólne informacje o deklarowanie parametrów).</span><span class="sxs-lookup"><span data-stu-id="e5d14-123">(See that topic for general information about declaring parameters.)</span></span>

<span data-ttu-id="e5d14-124">Jednak gdy polecenie cmdlet wymaga do przetwarzania danych wejściowych potoku, musi mieć parametry powiązany z wartości wejściowe przez środowisko uruchomieniowe programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e5d14-124">However, when a cmdlet needs to process pipeline input, it must have its parameters bound to input values by the Windows PowerShell runtime.</span></span> <span data-ttu-id="e5d14-125">Aby to zrobić, należy dodać `ValueFromPipeline` — słowo kluczowe lub dodać `ValueFromPipelineByProperty` słowa kluczowego [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) deklaracji atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e5d14-125">To do this, you must add the `ValueFromPipeline` keyword or add the `ValueFromPipelineByProperty` keyword to the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="e5d14-126">Określ `ValueFromPipeline` — słowo kluczowe, jeśli polecenie cmdlet uzyskuje dostęp do kompletnego obiektu wejściowego.</span><span class="sxs-lookup"><span data-stu-id="e5d14-126">Specify the `ValueFromPipeline` keyword if the cmdlet accesses the complete input object.</span></span> <span data-ttu-id="e5d14-127">Określ `ValueFromPipelineByProperty` Jeśli polecenia cmdlet uzyskuje dostęp do właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="e5d14-127">Specify the `ValueFromPipelineByProperty` if the cmdlet accesses only a property of the object.</span></span>

<span data-ttu-id="e5d14-128">Poniżej przedstawiono deklaracji parametru pod kątem `Name` parametrów to polecenie cmdlet Get-Proc, który akceptuje dane wejściowe w potoku.</span><span class="sxs-lookup"><span data-stu-id="e5d14-128">Here is the parameter declaration for the `Name` parameter of this Get-Proc cmdlet that accepts pipeline input.</span></span>

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L35-L44 "GetProcessSample03.cs")]

```vb
<Parameter(Position:=0, ValueFromPipeline:=True, _
ValueFromPipelineByPropertyName:=True), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#GetProc03VBNameParameter](Msh_samplesgetproc03#GetProc03VBNameParameter)]  -->

<span data-ttu-id="e5d14-129">Poprzednie zestawy deklaracji `ValueFromPipeline` słowa kluczowego `true` tak, aby środowisko uruchomieniowe programu Windows PowerShell będzie powiązać parametr przychodzącego obiektu Jeśli obiekt jest taki sam typ co parametr lub może być przekształcone do tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="e5d14-129">The previous declaration sets the `ValueFromPipeline` keyword to `true` so that the Windows PowerShell runtime will bind the parameter to the incoming object if the object is the same type as the parameter, or if it can be coerced to the same type.</span></span> <span data-ttu-id="e5d14-130">`ValueFromPipelineByPropertyName` — Słowo kluczowe jest również ustawiona na `true` tak, aby środowisko uruchomieniowe programu Windows PowerShell będzie sprawdzać przychodzącego obiektu dla `Name` właściwości.</span><span class="sxs-lookup"><span data-stu-id="e5d14-130">The `ValueFromPipelineByPropertyName` keyword is also set to `true` so that the Windows PowerShell runtime will check the incoming object for a `Name` property.</span></span> <span data-ttu-id="e5d14-131">Jeśli obiekt przychodzące ma taką właściwość, środowisko uruchomieniowe powiąże `Name` parametr `Name` przychodzącego obiektu.</span><span class="sxs-lookup"><span data-stu-id="e5d14-131">If the incoming object has such a property, the runtime will bind the `Name` parameter to the `Name` property of the incoming object.</span></span>

> [!NOTE]
> <span data-ttu-id="e5d14-132">Ustawienie `ValueFromPipeline` atrybutu — słowo kluczowe parametru mają pierwszeństwo przed ustawieniem dla `ValueFromPipelineByPropertyName` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="e5d14-132">The setting of the `ValueFromPipeline` attribute keyword for a parameter takes precedence over the setting for the `ValueFromPipelineByPropertyName` keyword.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="e5d14-133">Zastępowanie metody przetwarzania danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="e5d14-133">Overriding an Input Processing Method</span></span>

<span data-ttu-id="e5d14-134">W przypadku Twojego polecenia cmdlet do obsługi danych wejściowych potoku, trzeba zastąpić odpowiedniej metody przetwarzania danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="e5d14-134">If your cmdlet is to handle pipeline input, it needs to override the appropriate input processing methods.</span></span> <span data-ttu-id="e5d14-135">Metody podstawowe przetwarzania danych wejściowych wprowadzonych w temacie [tworzenia Your pierwsze polecenie Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e5d14-135">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="e5d14-136">To polecenie cmdlet Get-Proc zastępuje [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody, aby obsłużyć `Name` parametr danych wejściowych dostarczonych przez użytkownika lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="e5d14-136">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="e5d14-137">Ta metoda zostanie wyświetlony procesy dla każdej nazwy żądanej procesu lub wszystkich procesów, jeśli podano żadnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="e5d14-137">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="e5d14-138">Należy zauważyć, że w ramach [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), wywołanie [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) znajdują się dane wyjściowe mechanizm umożliwiający wysyłanie danych wyjściowych obiektów do potoku.</span><span class="sxs-lookup"><span data-stu-id="e5d14-138">Notice that within [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="e5d14-139">Drugi parametr to wywołanie `enumerateCollection`, jest równa `true` stwierdzić, środowisko wykonawcze programu Windows PowerShell do wyliczania tablicy obiektów procesów i zapisać jeden proces naraz w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="e5d14-139">The second parameter of this call, `enumerateCollection`, is set to `true` to tell the Windows PowerShell runtime to enumerate the array of process objects, and write one process at a time to the command line.</span></span>

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
    } // End foreach (string name...).
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()
    Dim processes As Process()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        processes = Process.GetProcesses()
    Else

        '/ If process names are specified, write the processes to the
        '/ pipeline to display them or make them available to the next cmdlet.
        For Each name As String In processNames
            '/ The second parameter of this call tells PowerShell to enumerate the
            '/ array, and send one process at a time to the pipeline.
            WriteObject(Process.GetProcessesByName(name), True)
        Next
    End If

End Sub 'ProcessRecord
```

## <a name="code-sample"></a><span data-ttu-id="e5d14-140">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="e5d14-140">Code Sample</span></span>

<span data-ttu-id="e5d14-141">Aby uzyskać pełne C# przykładowego kodu, zobacz [przykładowe GetProcessSample03](./getprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="e5d14-141">For the complete C# sample code, see [GetProcessSample03 Sample](./getprocesssample03-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="e5d14-142">Definiowanie typów obiektów i formatowanie</span><span class="sxs-lookup"><span data-stu-id="e5d14-142">Defining Object Types and Formatting</span></span>

<span data-ttu-id="e5d14-143">Program Windows PowerShell przekazuje informacje między poleceniami cmdlet, używając obiektów platformy .net.</span><span class="sxs-lookup"><span data-stu-id="e5d14-143">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="e5d14-144">W związku z tym polecenie cmdlet może być konieczne zdefiniowanie swój własny typ, lub polecenie cmdlet może być konieczne rozszerzyć istniejący typ dostarczane przez inne polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e5d14-144">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="e5d14-145">Aby uzyskać więcej informacji na temat definiowania nowych typów lub rozszerzanie istniejących typów, zobacz [rozszerzanie typów obiektów i formatowanie](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="e5d14-145">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="e5d14-146">Tworzenie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="e5d14-146">Building the Cmdlet</span></span>

<span data-ttu-id="e5d14-147">Po zaimplementowaniu polecenie cmdlet musi być zarejestrowana przy użyciu programu Windows PowerShell za pomocą przystawki programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e5d14-147">After implementing a cmdlet it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="e5d14-148">Aby uzyskać więcej informacji na temat rejestrowania poleceń cmdlet, zobacz [sposób zarejestrować poleceń cmdlet, dostawców i hostowania aplikacji](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="e5d14-148">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="e5d14-149">Testowanie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="e5d14-149">Testing the Cmdlet</span></span>

<span data-ttu-id="e5d14-150">Gdy Twoje polecenie cmdlet został zarejestrowany za pomocą programu Windows PowerShell, należy go przetestować, uruchamiając go w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="e5d14-150">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="e5d14-151">Na przykład przetestować kod, aby uzyskać przykładowe polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e5d14-151">For example, test the code for the sample cmdlet.</span></span> <span data-ttu-id="e5d14-152">Aby uzyskać więcej informacji o korzystaniu z poleceń cmdlet w wierszu polecenia, zobacz [wprowadzenie do programu Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="e5d14-152">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="e5d14-153">W wierszu polecenia programu Windows PowerShell wpisz następujące polecenia, aby pobrać nazw procesów przy użyciu potoku.</span><span class="sxs-lookup"><span data-stu-id="e5d14-153">At the Windows PowerShell prompt, enter the following commands to retrieve the process names through the pipeline.</span></span>

    ```powershell
    PS> type ProcessNames | get-proc
    ```

<span data-ttu-id="e5d14-154">Zostanie wyświetlone następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="e5d14-154">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----   ----- -----   ------    --  -----------
        809      21  40856    4448    147    9.50  2288  iexplore
        737      21  26036   16348    144   22.03  3860  iexplore
         39       2   1024     388     30    0.08  3396  notepad
       3927      62  71836   26984    467  195.19  1848  OUTLOOK
    ```

- <span data-ttu-id="e5d14-155">Wprowadź następujące wiersze, które można pobrać obiektów procesów, które mają `Name` właściwości od procesów o nazwie "IEXPLORE".</span><span class="sxs-lookup"><span data-stu-id="e5d14-155">Enter the following lines to get the process objects that have a `Name` property from the processes called "IEXPLORE".</span></span> <span data-ttu-id="e5d14-156">W tym przykładzie użyto `Get-Process` polecenia cmdlet (udostępnione przez środowisko Windows PowerShell) jako nadrzędnego polecenie, aby pobrać procesów "IEXPLORE".</span><span class="sxs-lookup"><span data-stu-id="e5d14-156">This example uses the `Get-Process` cmdlet (provided by Windows PowerShell) as an upstream command to retrieve the "IEXPLORE" processes.</span></span>

    ```powershell
    PS> get-process iexplore | get-proc
    ```

<span data-ttu-id="e5d14-157">Zostanie wyświetlone następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="e5d14-157">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----      ----- -----   ------     -- -----------
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
    ```

## <a name="see-also"></a><span data-ttu-id="e5d14-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e5d14-158">See Also</span></span>

[<span data-ttu-id="e5d14-159">Dodając parametry, które przetwarzają dane wejściowe wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="e5d14-159">Adding Parameters that Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="e5d14-160">Tworzenie swojej pierwszej polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e5d14-160">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="e5d14-161">Formatowanie i rozszerzanie typy obiektów</span><span class="sxs-lookup"><span data-stu-id="e5d14-161">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="e5d14-162">Jak zarejestrować poleceń cmdlet, dostawców i aplikacji hosta</span><span class="sxs-lookup"><span data-stu-id="e5d14-162">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="e5d14-163">Dokumentacja programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e5d14-163">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="e5d14-164">Przykłady polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="e5d14-164">Cmdlet Samples</span></span>](./cmdlet-samples.md)
