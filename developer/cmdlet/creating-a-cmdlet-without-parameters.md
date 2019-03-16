---
title: Tworzenie polecenia Cmdlet bez parametrów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmers Guide], creating
- cmdlets [PowerShell Programmers Guide], basic cmdlet
ms.assetid: 54236ef3-82db-45f8-9114-1ecb7ff65d3e
caps.latest.revision: 8
ms.openlocfilehash: c380b28570c955de6f41152fd617f5c1b0f9e4bd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054700"
---
# <a name="creating-a-cmdlet-without-parameters"></a><span data-ttu-id="c0ec9-102">Tworzenie polecenia cmdlet bez parametrów</span><span class="sxs-lookup"><span data-stu-id="c0ec9-102">Creating a Cmdlet without Parameters</span></span>

<span data-ttu-id="c0ec9-103">Ta sekcja zawiera opis sposobu tworzenia polecenia cmdlet, które pobiera informacje z komputera lokalnego bez użycia parametrów, a następnie zapisuje informacje do potoku.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-103">This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span> <span data-ttu-id="c0ec9-104">Polecenia cmdlet opisane w tym miejscu to polecenie cmdlet Get-Proc, pobiera informacje o procesach komputera lokalnego, a następnie wyświetli te informacje w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-104">The cmdlet described here is a Get-Proc cmdlet that retrieves information about the processes of the local computer, and then displays that information at the command line.</span></span>

<span data-ttu-id="c0ec9-105">Tematy w tej sekcji są następujące:</span><span class="sxs-lookup"><span data-stu-id="c0ec9-105">Topics in this section include the following:</span></span>

- [<span data-ttu-id="c0ec9-106">Polecenia cmdlet nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="c0ec9-106">Naming the Cmdlet</span></span>](#Naming-the-Cmdlet)

- [<span data-ttu-id="c0ec9-107">Definiowanie klasy polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c0ec9-107">Defining the Cmdlet Class</span></span>](#Defining-the-Cmdlet-Class)

- [<span data-ttu-id="c0ec9-108">Zastępowanie metody przetwarzania danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="c0ec9-108">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="c0ec9-109">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="c0ec9-109">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="c0ec9-110">Definiowanie typów obiektów i formatowanie</span><span class="sxs-lookup"><span data-stu-id="c0ec9-110">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="c0ec9-111">Tworzenie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="c0ec9-111">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="c0ec9-112">Testowanie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="c0ec9-112">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

> [!NOTE]
> <span data-ttu-id="c0ec9-113">Należy pamiętać, że podczas pisania poleceń cmdlet, zestawy odwołań Windows PowerShell® domyślnie pobierane są na dysku (w C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0). Nie są zainstalowane w globalnej pamięci podręcznej zestawów (GAC).</span><span class="sxs-lookup"><span data-stu-id="c0ec9-113">Be aware that when writing cmdlets, the Windows PowerShell® reference assemblies are downloaded onto disk (by default at C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).They are not installed in the Global Assembly Cache (GAC).</span></span>

## <a name="naming-the-cmdlet"></a><span data-ttu-id="c0ec9-114">Polecenia cmdlet nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="c0ec9-114">Naming the Cmdlet</span></span>

<span data-ttu-id="c0ec9-115">Nazwa polecenia cmdlet składa się z zlecenia, który wskazuje, że przez polecenie cmdlet akcję i rzeczownik, który wskazuje elementy, które działają polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-115">A cmdlet name consists of a verb that indicates the action the cmdlet takes and a noun that indicates the items that the cmdlet acts upon.</span></span> <span data-ttu-id="c0ec9-116">Ponieważ to polecenie cmdlet Get-Proc przykład umożliwia pobranie obiektów procesu, używa ona czasownik "Pobierz", zdefiniowane przez [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) wyliczenie i rzeczownik "Proc", aby wskazać, że polecenie cmdlet działa w elementach procesu.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-116">Because this sample Get-Proc cmdlet retrieves process objects, it uses the verb "Get", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeration, and the noun "Proc" to indicate that the cmdlet works on process items.</span></span>

<span data-ttu-id="c0ec9-117">Podczas określania nazwy poleceń cmdlet, nie używaj żadnego z następujących znaków: #, () {} [] & - / \ $;: "" <> &#124; ?</span><span class="sxs-lookup"><span data-stu-id="c0ec9-117">When naming cmdlets, do not use any of the following characters: # , () {} [] & - /\ $ ; : " '<> &#124; ?</span></span> <span data-ttu-id="c0ec9-118">@ \` .</span><span class="sxs-lookup"><span data-stu-id="c0ec9-118">@ \` .</span></span>

### <a name="choosing-a-noun"></a><span data-ttu-id="c0ec9-119">Wybieranie rzeczownik</span><span class="sxs-lookup"><span data-stu-id="c0ec9-119">Choosing a Noun</span></span>

<span data-ttu-id="c0ec9-120">Należy wybrać rzeczownik, który jest specyficzny.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-120">You should choose a noun that is specific.</span></span> <span data-ttu-id="c0ec9-121">Najlepiej użyć pojedynczej rzeczownik, prefiks z wersją skróconą nazwę produktu.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-121">It is best to use a singular noun prefixed with a shortened version of the product name.</span></span> <span data-ttu-id="c0ec9-122">Przykładowa nazwa polecenia cmdlet tego typu jest "`Get-SQLServer`".</span><span class="sxs-lookup"><span data-stu-id="c0ec9-122">An example cmdlet name of this type is "`Get-SQLServer`".</span></span>

### <a name="choosing-a-verb"></a><span data-ttu-id="c0ec9-123">Wybieranie zlecenia</span><span class="sxs-lookup"><span data-stu-id="c0ec9-123">Choosing a Verb</span></span>

<span data-ttu-id="c0ec9-124">Należy użyć zlecenia z zestawu nazwy zlecenie zatwierdzonych poleceń cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-124">You should use a verb from the set of approved cmdlet verb names.</span></span> <span data-ttu-id="c0ec9-125">Aby uzyskać więcej informacji na temat zatwierdzone czasowniki zobacz [nazwy zlecenie poleceń Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="c0ec9-125">For more information about the approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="c0ec9-126">Definiowanie klasy polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c0ec9-126">Defining the Cmdlet Class</span></span>

<span data-ttu-id="c0ec9-127">Po wybraniu opcji Nazwa polecenia cmdlet, należy zdefiniować klasa platformy .NET w celu wykonania polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-127">Once you have chosen a cmdlet name, define a .NET class to implement the cmdlet.</span></span> <span data-ttu-id="c0ec9-128">Poniżej przedstawiono w definicji klasy dla tego polecenia cmdlet Get-Proc próbki:</span><span class="sxs-lookup"><span data-stu-id="c0ec9-128">Here is the class definition for this sample Get-Proc cmdlet:</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

<span data-ttu-id="c0ec9-129">Należy zauważyć, że przed definicją klasy [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) atrybutu przy użyciu składni `[Cmdlet(verb, noun, ...)]`, jest używany do identyfikowania tej klasy jako polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-129">Notice that previous to the class definition, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute, with the syntax `[Cmdlet(verb, noun, ...)]`, is used to identify this class as a cmdlet.</span></span> <span data-ttu-id="c0ec9-130">Jest to jedyny atrybut wymagane dla wszystkich poleceń cmdlet i pozwala wywoływać je poprawnie środowiska uruchomieniowego programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-130">This is the only required attribute for all cmdlets, and it allows the Windows PowerShell runtime to call them correctly.</span></span> <span data-ttu-id="c0ec9-131">Można ustawić atrybutu słów kluczowych, aby dodatkowo zadeklarować klasy, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-131">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="c0ec9-132">Należy pamiętać, że deklaracji atrybutu dla klasy GetProcCommand nasze przykładowe deklaruje tylko nazwy polecenia cmdlet Get-Proc rzeczownika i zlecenie.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-132">Be aware that the attribute declaration for our sample GetProcCommand class declares only the noun and verb names for the Get-Proc cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="c0ec9-133">Dla wszystkich klas atrybutów programu Windows PowerShell słowa kluczowe, które można ustawić odnoszą się do właściwości klasy atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-133">For all Windows PowerShell attribute classes, the keywords that you can set correspond to properties of the attribute class.</span></span>

<span data-ttu-id="c0ec9-134">Podczas określania nazwy klasy polecenia cmdlet, jest dobrym rozwiązaniem, aby odzwierciedlić nazwę polecenia cmdlet w nazwie klasy.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-134">When naming the class of the cmdlet, it is a good practice to reflect the cmdlet name in the class name.</span></span> <span data-ttu-id="c0ec9-135">W tym celu należy użyć formy "VerbNounCommand" i zastąp "Czasownik" i "Rzeczownik" czasownik i rzeczownik nazwa polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-135">To do this, use the form "VerbNounCommand" and replace "Verb" and "Noun" with the verb and noun used in the cmdlet name.</span></span> <span data-ttu-id="c0ec9-136">Jak pokazano w poprzednim definicji klasy, przykładowe polecenie cmdlet Get-Proc definiuje klasę o nazwie GetProcCommand, która jest pochodną [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-136">As is shown in the previous class definition, the sample Get-Proc cmdlet defines a class called GetProcCommand, which derives from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) base class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c0ec9-137">Jeśli chcesz zdefiniować polecenia cmdlet, który uzyskuje dostęp do środowiska wykonawczego programu Windows PowerShell bezpośrednio klasy .NET powinien pochodzić od [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-137">If you want to define a cmdlet that accesses the Windows PowerShell runtime directly, your .NET class should derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span> <span data-ttu-id="c0ec9-138">Aby uzyskać więcej informacji na temat tej klasy, zobacz [tworzenia tego definiuje zestawy parametrów polecenia Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="c0ec9-138">For more information about this class, see [Creating a Cmdlet that Defines Parameter Sets](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

> [!NOTE]
> <span data-ttu-id="c0ec9-139">Klasy związane z poleceniem cmdlet musi być jawnie oznaczone jako publiczne.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-139">The class for a cmdlet must be explicitly marked as public.</span></span> <span data-ttu-id="c0ec9-140">Klasy, które nie zostały oznaczone jako publiczne będą domyślnie wewnętrznego i nie zostanie znaleziony w czasie wykonywania programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-140">Classes that are not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="c0ec9-141">Używa programu Windows PowerShell [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) przestrzeń nazw dla swojej klasy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-141">Windows PowerShell uses the [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) namespace for its cmdlet classes.</span></span> <span data-ttu-id="c0ec9-142">Zalecane jest umieszczenie Twoich zajęciach polecenia cmdlet w przestrzeni nazw poleceń przestrzeni nazw interfejsu API, na przykład xxx.PS.Commands.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-142">It is recommended to place your cmdlet classes in a Commands namespace of your API namespace, for example, xxx.PS.Commands.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="c0ec9-143">Zastępowanie metody przetwarzania danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="c0ec9-143">Overriding an Input Processing Method</span></span>

<span data-ttu-id="c0ec9-144">[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klasa udostępnia trzy metody głównej przetwarzania danych wejściowych, co najmniej jeden z nich muszą przesłaniać Twojego polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-144">The [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class provides three main input processing methods, at least one of which your cmdlet must override.</span></span> <span data-ttu-id="c0ec9-145">Aby uzyskać więcej informacji o przetwarzaniu rekordy w programie Windows PowerShell, zobacz [sposób działania programu Windows PowerShell](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).</span><span class="sxs-lookup"><span data-stu-id="c0ec9-145">For more information about how Windows PowerShell processes records, see [How Windows PowerShell Works](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).</span></span>

<span data-ttu-id="c0ec9-146">Dla wszystkich typów danych wejściowych, środowisko wykonawcze programu Windows PowerShell wywołuje [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) umożliwiające przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-146">For all types of input, the Windows PowerShell runtime calls [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) to enable processing.</span></span> <span data-ttu-id="c0ec9-147">Jeśli Twojego polecenia cmdlet należy wykonać niektóre wstępne przetwarzanie lub Instalator, go to zrobić przez zastąpienie tej metody.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-147">If your cmdlet must perform some preprocessing or setup, it can do this by overriding this method.</span></span>

> [!NOTE]
> <span data-ttu-id="c0ec9-148">Do opisania zestawem wartości parametrów, które podano podczas wywoływania polecenia cmdlet, programu Windows PowerShell używa termin "record".</span><span class="sxs-lookup"><span data-stu-id="c0ec9-148">Windows PowerShell uses the term "record" to describe the set of parameter values supplied when a cmdlet is called.</span></span>

<span data-ttu-id="c0ec9-149">Jeśli Twojego polecenia cmdlet akceptuje dane wejściowe w potoku, musi ono przesłonić [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metodę i opcjonalnie [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)metody.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-149">If your cmdlet accepts pipeline input, it must override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, and optionally the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="c0ec9-150">Na przykład polecenia cmdlet mogą zastąpić obie metody, jeśli zbiera wszystkie dane wejściowe, używając [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) , a następnie dane wejściowe jako całości, a nie jeden element w czasie, jako `Sort-Object` wykonuje polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-150">For example, a cmdlet might override both methods if it gathers all input using [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) and then operates on the input as a whole rather than one element at a time, as the `Sort-Object` cmdlet does.</span></span>

<span data-ttu-id="c0ec9-151">Jeśli Twojego polecenia cmdlet nie przyjmuje dane wejściowe w potoku, należy zastąpić [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metody.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-151">If your cmdlet does not take pipeline input, it should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="c0ec9-152">Należy pamiętać, że ta metoda jest często używana zamiast [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) gdy polecenie cmdlet nie może działać na jeden element w czasie, tak jak w przypadku sortowania polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-152">Be aware that this method is frequently used in place of [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) when the cmdlet cannot operate on one element at a time, as is the case for a sorting cmdlet.</span></span>

<span data-ttu-id="c0ec9-153">Ponieważ to przykładowe polecenie cmdlet Get-Proc musi otrzymać bit wejście potokowe, zastępuje ona [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody i używa domyślnej implementacji dla [ System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) i [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span><span class="sxs-lookup"><span data-stu-id="c0ec9-153">Because this sample Get-Proc cmdlet must receive pipeline input, it overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method and uses the default implementations for [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) and [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span></span> <span data-ttu-id="c0ec9-154">[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) zastąpienie pobiera procesy i zapisuje je w wiersza polecenia przy użyciu [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) metody.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-154">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override retrieves processes and writes them to the command line using the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Get the current processes
  Process[] processes = Process.GetProcesses();

  // Write the processes to the pipeline making them available
  // to the next cmdlet. The second parameter of this call tells
  // PowerShell to enumerate the array, and send one process at a
  // time to the pipeline.
  WriteObject(processes, true);
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ Get the current processes.
    Dim processes As Process()
    processes = Process.GetProcesses()

    '/ Write the processes to the pipeline making them available
    '/ to the next cmdlet. The second parameter of this call tells
    '/ PowerShell to enumerate the array, and send one process at a
    '/ time to the pipeline.
    WriteObject(processes, True)

End Sub 'ProcessRecord
```

#### <a name="things-to-remember-about-input-processing"></a><span data-ttu-id="c0ec9-155">Warto zapamiętać informacje o przetwarzaniu danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="c0ec9-155">Things to Remember About Input Processing</span></span>

- <span data-ttu-id="c0ec9-156">Domyślne źródło danych wejściowych jest obiektem jawne (na przykład, ciąg), dostarczone przez użytkownika w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-156">The default source for input is an explicit object (for example, a string) provided by the user on the command line.</span></span> <span data-ttu-id="c0ec9-157">Aby uzyskać więcej informacji, zobacz [polecenia Cmdlet, aby dane wejściowe wiersza polecenia procesu tworzenia](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="c0ec9-157">For more information, see [Creating a Cmdlet to Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

- <span data-ttu-id="c0ec9-158">Metoda przetwarzania danych wejściowych może również odbierać dane wejściowe z danych wyjściowych obiektu nadrzędnego polecenia cmdlet do potoku.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-158">An input processing method can also receive input from the output object of an upstream cmdlet on the pipeline.</span></span> <span data-ttu-id="c0ec9-159">Aby uzyskać więcej informacji, zobacz [tworzenia polecenia Cmdlet, aby proces wejście potokowe](./adding-parameters-that-process-pipeline-input.md).</span><span class="sxs-lookup"><span data-stu-id="c0ec9-159">For more information, see [Creating a Cmdlet to Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="c0ec9-160">Należy pamiętać, że Twojego polecenia cmdlet mogą odbierać dane wejściowe z kombinacji wiersza polecenia i potoku źródła.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-160">Be aware that your cmdlet can receive input from a combination of command-line and pipeline sources.</span></span>

- <span data-ttu-id="c0ec9-161">Polecenia cmdlet podrzędne mogą nie zwracać przez długi czas lub wcale.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-161">The downstream cmdlet might not return for a long time, or not at all.</span></span> <span data-ttu-id="c0ec9-162">Z tego powodu, dane wejściowe przetwarzania metody w Twojego polecenia cmdlet powinno zawierać nie blokad podczas wywołania [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), szczególnie blokad, dla których zakres wykracza poza wystąpieniem polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-162">For that reason, the input processing method in your cmdlet should not hold locks during calls to [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especially locks for which the scope extends beyond the cmdlet instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c0ec9-163">Polecenia cmdlet nigdy nie powinien wywoływać [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) lub równoważnym.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-163">Cmdlets should never call [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) or its equivalent.</span></span>

- <span data-ttu-id="c0ec9-164">Środowiska może mieć obiektu zmienne, aby wyczyścić po zakończeniu przetwarzania (na przykład, jeśli zostanie on otwarty dojście do pliku w [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metody i przechowuje dojście Otwórz do użytku przez [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span><span class="sxs-lookup"><span data-stu-id="c0ec9-164">Your cmdlet might have object variables to clean up when it is finished processing (for example, if it opens a file handle in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span></span> <span data-ttu-id="c0ec9-165">Należy pamiętać, że środowisko wykonawcze programu Windows PowerShell nie zawsze wywołuje [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metody, która powinna wykonać oczyszczania obiektu.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-165">It is important to remember that the Windows PowerShell runtime does not always call the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method, which should perform object cleanup.</span></span>

<span data-ttu-id="c0ec9-166">Na przykład [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) nie może być wywoływana, jeśli polecenia cmdlet zostanie anulowane w środku lub gdy kończącym błędu w jakichkolwiek pracach związanych z polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-166">For example, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) might not be called if the cmdlet is canceled midway or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="c0ec9-167">W związku z tym, polecenia cmdlet, które wymaga czyszczenia obiektu powinny implementować pełne [System.IDisposable](/dotnet/api/System.IDisposable) wzorca, w tym finalizator, dzięki czemu środowisko uruchomieniowe może wywołać zarówno [ System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) i [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) po zakończeniu przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-167">Therefore, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including the finalizer, so that the runtime can call both [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) at the end of processing.</span></span>

## <a name="code-sample"></a><span data-ttu-id="c0ec9-168">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="c0ec9-168">Code Sample</span></span>

<span data-ttu-id="c0ec9-169">Aby uzyskać pełne C# przykładowego kodu, zobacz [przykładowe GetProcessSample01](./getprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="c0ec9-169">For the complete C# sample code, see [GetProcessSample01 Sample](./getprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="c0ec9-170">Definiowanie typów obiektów i formatowanie</span><span class="sxs-lookup"><span data-stu-id="c0ec9-170">Defining Object Types and Formatting</span></span>

<span data-ttu-id="c0ec9-171">Program Windows PowerShell przekazuje informacje między poleceniami cmdlet, używając obiektów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-171">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="c0ec9-172">W związku z tym polecenie cmdlet może się okazać zdefiniowanie swój własny typ, lub polecenie cmdlet może być konieczne rozszerzenie istniejącego typu dostarczane przez inne polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-172">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="c0ec9-173">Aby uzyskać więcej informacji na temat definiowania nowych typów lub rozszerzanie istniejących typów, zobacz [rozszerzanie typów obiektów i formatowanie](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="c0ec9-173">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="c0ec9-174">Tworzenie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="c0ec9-174">Building the Cmdlet</span></span>

<span data-ttu-id="c0ec9-175">Po zaimplementowaniu polecenia cmdlet, należy zarejestrować go za pomocą programu Windows PowerShell za pomocą przystawki programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-175">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="c0ec9-176">Aby uzyskać więcej informacji na temat rejestrowania poleceń cmdlet, zobacz [sposób zarejestrować poleceń cmdlet, dostawców i hostowania aplikacji](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="c0ec9-176">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="c0ec9-177">Testowanie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="c0ec9-177">Testing the Cmdlet</span></span>

<span data-ttu-id="c0ec9-178">Po zarejestrowaniu Twojego polecenia cmdlet przy użyciu programu Windows PowerShell można ją przetestować, uruchamiając go w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-178">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="c0ec9-179">Kod nasze przykładowe polecenie cmdlet Get-Proc jest mały, ale nadal używa środowiska uruchomieniowego programu Windows PowerShell i istniejący obiekt .NET, która jest wystarczająco dużo, aby była przydatna.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-179">The code for our sample Get-Proc cmdlet is small, but it still uses the Windows PowerShell runtime and an existing .NET object, which is enough to make it useful.</span></span> <span data-ttu-id="c0ec9-180">Możemy go przetestować, aby lepiej zrozumieć, co zrobić, Get-Proc i jak można używać jej dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-180">Let's test it to better understand what Get-Proc can do and how its output can be used.</span></span> <span data-ttu-id="c0ec9-181">Aby uzyskać więcej informacji o korzystaniu z poleceń cmdlet w wierszu polecenia, zobacz [wprowadzenie do programu Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="c0ec9-181">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

1. <span data-ttu-id="c0ec9-182">Uruchom program Windows PowerShell, a następnie pobrać bieżących procesów uruchomionych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-182">Start Windows PowerShell, and get the current processes running on the computer.</span></span>

    ```powershell
    get-proc
    ```

    <span data-ttu-id="c0ec9-183">Zostanie wyświetlone następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-183">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. <span data-ttu-id="c0ec9-184">Przypisz zmienną do wyników polecenia cmdlet do manipulacji łatwiejsze.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-184">Assign a variable to the cmdlet results for easier manipulation.</span></span>

    ```powershell
    $p=get-proc
    ```

3. <span data-ttu-id="c0ec9-185">Pobierz liczbę procesów.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-185">Get the number of processes.</span></span>

    ```powershell
    $p.length
    ```

    <span data-ttu-id="c0ec9-186">Zostanie wyświetlone następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-186">The following output appears.</span></span>

    ```output
    63
    ```

4. <span data-ttu-id="c0ec9-187">Pobieranie określonego procesu.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-187">Retrieve a specific process.</span></span>

    ```powershell
    $p[6]
    ```

    <span data-ttu-id="c0ec9-188">Zostanie wyświetlone następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-188">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. <span data-ttu-id="c0ec9-189">Uzyskaj czas rozpoczęcia tego procesu.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-189">Get the start time of this process.</span></span>

    ```powershell
    $p[6].starttime
    ```

    <span data-ttu-id="c0ec9-190">Zostanie wyświetlone następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-190">The following output appears.</span></span>

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. <span data-ttu-id="c0ec9-191">Uzyskaj procesy, dla których jest większy niż 500 licznika dojść i sortować wyniki.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-191">Get the processes for which the handle count is greater than 500, and sort the result.</span></span>

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    <span data-ttu-id="c0ec9-192">Zostanie wyświetlone następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-192">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. <span data-ttu-id="c0ec9-193">Użyj `Get-Member` polecenia cmdlet, aby wyświetlić listę właściwości dostępnych dla każdego procesu.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-193">Use the `Get-Member` cmdlet to list the properties available for each process.</span></span>

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    <span data-ttu-id="c0ec9-194">Zostanie wyświetlone następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="c0ec9-194">The following output appears.</span></span>

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a><span data-ttu-id="c0ec9-195">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c0ec9-195">See Also</span></span>

[<span data-ttu-id="c0ec9-196">Tworzenie polecenia Cmdlet do przetwarzania danych wejściowych wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="c0ec9-196">Creating a Cmdlet to Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="c0ec9-197">Polecenia Cmdlet do przetwarzania danych wejściowych potoku tworzenia</span><span class="sxs-lookup"><span data-stu-id="c0ec9-197">Creating a Cmdlet to Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="c0ec9-198">Jak utworzyć polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c0ec9-198">How to Create a Windows PowerShell Cmdlet</span></span>](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="c0ec9-199">Formatowanie i rozszerzanie typy obiektów</span><span class="sxs-lookup"><span data-stu-id="c0ec9-199">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="c0ec9-200">Jak działa program Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c0ec9-200">How Windows PowerShell Works</span></span>](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[<span data-ttu-id="c0ec9-201">Jak zarejestrować poleceń cmdlet, dostawców i aplikacji hosta</span><span class="sxs-lookup"><span data-stu-id="c0ec9-201">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="c0ec9-202">Dokumentacja programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c0ec9-202">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="c0ec9-203">Przykłady polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="c0ec9-203">Cmdlet Samples</span></span>](./cmdlet-samples.md)