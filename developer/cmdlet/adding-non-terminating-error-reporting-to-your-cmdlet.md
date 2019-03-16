---
title: Dodawanie raportów o błędach do Twojego polecenia Cmdlet do niepowodujące | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: e0550dacc33f45f45ba105ca5cb4d2e5b5d675fb
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056060"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a><span data-ttu-id="6edb4-102">Dodawanie raportowania błędów niepowodujących zakończenia działania do polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="6edb4-102">Adding Non-Terminating Error Reporting to Your Cmdlet</span></span>

<span data-ttu-id="6edb4-103">Polecenia cmdlet mogą raportować błędy niekończące, wywołując [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metody i nadal będzie mogła działać na bieżący obiekt danych wejściowych lub dalsze przychodzące potoku obiektów.</span><span class="sxs-lookup"><span data-stu-id="6edb4-103">Cmdlets can report nonterminating errors by calling the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method and still continue to operate on the current input object or on further incoming pipeline objects.</span></span> <span data-ttu-id="6edb4-104">W tej sekcji opisano sposób tworzenia polecenia cmdlet, który zgłasza błędy niekończące z jego metody przetwarzania danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="6edb4-104">This section explains how to create a cmdlet that reports nonterminating errors from its input processing methods.</span></span>

<span data-ttu-id="6edb4-105">Błędy niekończące (a także błędy kończący), należy przekazać polecenie cmdlet [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) obiektu zidentyfikować błąd.</span><span class="sxs-lookup"><span data-stu-id="6edb4-105">For nonterminating errors (as well as terminating errors), the cmdlet must pass an [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) object identifying the error.</span></span> <span data-ttu-id="6edb4-106">Każdy rekord błędu jest identyfikowane za pomocą unikatowego ciągu o nazwie "Identyfikator błędu."</span><span class="sxs-lookup"><span data-stu-id="6edb4-106">Each error record is identified by a unique string called the "error identifier."</span></span> <span data-ttu-id="6edb4-107">Oprócz identyfikatora kategorii każdego błędu jest określona przez stałe zdefiniowane przez [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="6edb4-107">In addition to the identifier, the category of each error is specified by constants defined by a [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumeration.</span></span> <span data-ttu-id="6edb4-108">Użytkownik może wyświetlić błędy na podstawie ich kategorii, ustawiając `$ErrorView` zmienną "CategoryView".</span><span class="sxs-lookup"><span data-stu-id="6edb4-108">The user can view errors based on their category by setting the `$ErrorView` variable to "CategoryView".</span></span>

<span data-ttu-id="6edb4-109">Aby uzyskać więcej informacji na temat rekordów błędów, zobacz [rekordów błędów programu Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="6edb4-109">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="6edb4-110">Tematy w tej sekcji są następujące:</span><span class="sxs-lookup"><span data-stu-id="6edb4-110">Topics in this section include the following:</span></span>

- [<span data-ttu-id="6edb4-111">Definiowanie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="6edb4-111">Defining the Cmdlet</span></span>](#Defining-the-Cmdlet)

- [<span data-ttu-id="6edb4-112">Definiowanie parametrów</span><span class="sxs-lookup"><span data-stu-id="6edb4-112">Defining Parameters</span></span>](#Defining-Parameters)

- [<span data-ttu-id="6edb4-113">Zastępowanie metody przetwarzania danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="6edb4-113">Overriding Input Processing Methods</span></span>](#Overriding-Input-Processing-Methods)

- [<span data-ttu-id="6edb4-114">Błędy niekończące raportowania</span><span class="sxs-lookup"><span data-stu-id="6edb4-114">Reporting Nonterminating Errors</span></span>](#Reporting-Nonterminating-Errors)

- [<span data-ttu-id="6edb4-115">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="6edb4-115">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="6edb4-116">Definiowanie typów obiektów i formatowanie</span><span class="sxs-lookup"><span data-stu-id="6edb4-116">Defining Object Types and Formatting</span></span>](#Define-Object-Types-and-Formatting)

- [<span data-ttu-id="6edb4-117">Tworzenie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="6edb4-117">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="6edb4-118">Testowanie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="6edb4-118">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a><span data-ttu-id="6edb4-119">Definiowanie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="6edb4-119">Defining the Cmdlet</span></span>

<span data-ttu-id="6edb4-120">Pierwszym krokiem w procesie tworzenia polecenia cmdlet jest zawsze nazewnictwa polecenia cmdlet i deklarowanie klasy .NET, która implementuje polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6edb4-120">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="6edb4-121">To polecenie cmdlet pobiera informacje o procesu, więc nazwę zlecenie wybrane w tym miejscu to "Get".</span><span class="sxs-lookup"><span data-stu-id="6edb4-121">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="6edb4-122">(Prawie dowolny rodzaj polecenia cmdlet, który jest zdolny do pobierania informacji o może przetwarzać dane wejściowe wiersza polecenia). Aby uzyskać więcej informacji na temat polecenia cmdlet zatwierdzonych czasowników, zobacz [nazwy zlecenie poleceń Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="6edb4-122">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="6edb4-123">Poniżej przedstawiono definicję dla tego polecenia cmdlet Get-Proc.</span><span class="sxs-lookup"><span data-stu-id="6edb4-123">The following is the definition for this Get-Proc cmdlet.</span></span> <span data-ttu-id="6edb4-124">Szczegóły tej definicji są podane w [tworzenia Your pierwsze polecenie Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="6edb4-124">Details of this definition are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a><span data-ttu-id="6edb4-125">Definiowanie parametrów</span><span class="sxs-lookup"><span data-stu-id="6edb4-125">Defining Parameters</span></span>

<span data-ttu-id="6edb4-126">W razie potrzeby Twojego polecenia cmdlet należy zdefiniować parametry w celu przetwarzania danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="6edb4-126">If necessary, your cmdlet must define parameters for processing input.</span></span> <span data-ttu-id="6edb4-127">To polecenie cmdlet Get-Proc definiuje `Name` parametru, zgodnie z opisem w [dodając parametry te dane wejściowe wiersza polecenia procesu](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="6edb4-127">This Get-Proc cmdlet defines a `Name` parameter as described in [Adding Parameters that Process Command-Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

<span data-ttu-id="6edb4-128">Poniżej przedstawiono deklaracji parametru pod kątem `Name` parametrów to polecenie cmdlet Get-Proc.</span><span class="sxs-lookup"><span data-stu-id="6edb4-128">Here is the parameter declaration for the `Name` parameter of this Get-Proc cmdlet.</span></span>

```csharp
[Parameter(
           Position = 0,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
[ValidateNotNullOrEmpty]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

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

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="6edb4-129">Zastępowanie metody przetwarzania danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="6edb4-129">Overriding Input Processing Methods</span></span>

<span data-ttu-id="6edb4-130">Wszystkie polecenia cmdlet muszą przesłaniać co najmniej jedną z metod dostarczonych przez przetwarzanie danych wejściowych [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klasy.</span><span class="sxs-lookup"><span data-stu-id="6edb4-130">All cmdlets must override at least one of the input processing methods provided by the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="6edb4-131">Te metody są omówione w [tworzenia Your pierwsze polecenie Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="6edb4-131">These methods are discussed in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="6edb4-132">Twojego polecenia cmdlet powinny obsługiwać każdego wybranego rekordu jako niezależne, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="6edb4-132">Your cmdlet should handle each record as independently as possible.</span></span>

<span data-ttu-id="6edb4-133">To polecenie cmdlet Get-Proc zastępuje [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody, aby obsłużyć `Name` parametr dla danych wejściowych dostarczonych przez użytkownika lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="6edb4-133">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter for input provided by the user or a script.</span></span> <span data-ttu-id="6edb4-134">Ta metoda zostanie wyświetlony procesy dla każdej nazwy żądanej procesu lub wszystkich procesów, jeśli podano żadnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="6edb4-134">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="6edb4-135">Szczegóły to zastąpienie są podane w [tworzenia Your pierwsze polecenie Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="6edb4-135">Details of this override are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

#### <a name="things-to-remember-when-reporting-errors"></a><span data-ttu-id="6edb4-136">Warto zapamiętać, gdy raportowanie błędów</span><span class="sxs-lookup"><span data-stu-id="6edb4-136">Things to Remember When Reporting Errors</span></span>

<span data-ttu-id="6edb4-137">[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) obiektu, że polecenia cmdlet przekazuje podczas pisania błąd wymaga wyjątek podstawą.</span><span class="sxs-lookup"><span data-stu-id="6edb4-137">The [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) object that the cmdlet passes when writing an error requires an exception at its core.</span></span> <span data-ttu-id="6edb4-138">Podczas określania wyjątek do użycia, postępuj zgodnie z wytycznymi dla platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="6edb4-138">Follow the .NET guidelines when determining the exception to use.</span></span> <span data-ttu-id="6edb4-139">Zasadniczo Jeśli błąd semantycznie jest taka sama jak istniejące wyjątek, polecenia cmdlet należy użyć lub pochodzić od tego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="6edb4-139">Basically, if the error is semantically the same as an existing exception, the cmdlet should use or derive from that exception.</span></span> <span data-ttu-id="6edb4-140">W przeciwnym razie powinien pochodzić, nowy wyjątek lub hierarchia wyjątków bezpośrednio z [System.Exception](/dotnet/api/System.Exception) klasy.</span><span class="sxs-lookup"><span data-stu-id="6edb4-140">Otherwise, it should derive a new exception or exception hierarchy directly from the [System.Exception](/dotnet/api/System.Exception) class.</span></span>

<span data-ttu-id="6edb4-141">Podczas tworzenia identyfikatorów błędu (dostępne za pośrednictwem właściwości FullyQualifiedErrorId klasy rekord błędu) pamiętać o następujących.</span><span class="sxs-lookup"><span data-stu-id="6edb4-141">When creating error identifiers (accessed through the FullyQualifiedErrorId property of the ErrorRecord class) keep the following in mind.</span></span>

- <span data-ttu-id="6edb4-142">Ciągi użycia, które są przeznaczone do celów diagnostycznych, aby podczas sprawdzania w pełni kwalifikowanego identyfikatora można określić, jaki dokładnie błąd i w przypadku, gdy błąd pochodzi z.</span><span class="sxs-lookup"><span data-stu-id="6edb4-142">Use strings that are targeted for diagnostic purposes so that when inspecting the fully qualified identifier you can determine what the error is and where the error came from.</span></span>

- <span data-ttu-id="6edb4-143">Identyfikator formy błąd w pełni kwalifikowana może wyglądać następująco.</span><span class="sxs-lookup"><span data-stu-id="6edb4-143">A well formed fully qualified error identifier might be as follows.</span></span>

`CommandNotFoundException,Micrososft.PowerShell.Commands.GetCommanddCommand.`

<span data-ttu-id="6edb4-144">Należy zauważyć, że w poprzednim przykładzie identyfikator błędu (pierwszy token) wskazuje na to, co to jest błąd i pozostałej części wskazuje, skąd pochodzą błędu.</span><span class="sxs-lookup"><span data-stu-id="6edb4-144">Notice that in the previous example, the error identifier (the first token) designates what the error is and the remaining part indicates where the error came from.</span></span>

- <span data-ttu-id="6edb4-145">W przypadku bardziej złożonych scenariuszy Identyfikator błędu może być token oddzielone kropką, który może zostać przeanalizowany w zakresie kontroli.</span><span class="sxs-lookup"><span data-stu-id="6edb4-145">For more complex scenarios, the error identifier can be a dot separated token that can be parsed on inspection.</span></span> <span data-ttu-id="6edb4-146">Dzięki temu za gałęzi na części identyfikator błędu, a także kategoria błędu identyfikator i błędów.</span><span class="sxs-lookup"><span data-stu-id="6edb4-146">This allows you too branch on the parts of the error identifier as well as the error identifier and error category.</span></span>

<span data-ttu-id="6edb4-147">Polecenia cmdlet należy przypisać różne ścieżki identyfikatorów wystąpienia określonego błędu.</span><span class="sxs-lookup"><span data-stu-id="6edb4-147">The cmdlet should assign specific error identifiers to different code paths.</span></span> <span data-ttu-id="6edb4-148">Pamiętać następujące informacje do przypisywania identyfikatorów, błąd:</span><span class="sxs-lookup"><span data-stu-id="6edb4-148">Keep the following information in mind for assignment of error identifiers:</span></span>

- <span data-ttu-id="6edb4-149">Identyfikator błędu należy pozostaje niezmienna przez cały cykl jej polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6edb4-149">An error identifier should remain constant throughout the cmdlet life cycle.</span></span> <span data-ttu-id="6edb4-150">Nie należy zmieniać semantyki odpowiadającym błędzie między wersjami polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6edb4-150">Do not change the semantics of an error identifier between cmdlet versions.</span></span>

- <span data-ttu-id="6edb4-151">Tekst na użytek odpowiadający lapidarnie błąd raportowany Identyfikator błędu.</span><span class="sxs-lookup"><span data-stu-id="6edb4-151">Use text for an error identifier that tersely corresponds to the error being reported.</span></span> <span data-ttu-id="6edb4-152">Nie należy używać biały znak lub znaki interpunkcyjne.</span><span class="sxs-lookup"><span data-stu-id="6edb4-152">Do not use white space or punctuation.</span></span>

- <span data-ttu-id="6edb4-153">Mieć Twojego polecenia cmdlet wygenerować tylko identyfikatory błędów, które są do odtworzenia.</span><span class="sxs-lookup"><span data-stu-id="6edb4-153">Have your cmdlet generate only error identifiers that are reproducible.</span></span> <span data-ttu-id="6edb4-154">Na przykład nie powinna ona generować identyfikator, który zawiera identyfikator procesu.</span><span class="sxs-lookup"><span data-stu-id="6edb4-154">For example, it should not generate an identifier that includes a process identifier.</span></span> <span data-ttu-id="6edb4-155">Błąd identyfikatory są przydatne do użytkownika, tylko wtedy, gdy odnoszą się do identyfikatorów, które są widoczne dla innych użytkowników, w której występuje ten sam problem.</span><span class="sxs-lookup"><span data-stu-id="6edb4-155">Error identifiers are useful to a user only when they correspond to identifiers that are seen by other users experiencing the same problem.</span></span>

<span data-ttu-id="6edb4-156">Nieobsługiwane wyjątki nie są objęte programu Windows PowerShell w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="6edb4-156">Unhandled exceptions are not caught by Windows PowerShell in the following conditions:</span></span>

- <span data-ttu-id="6edb4-157">Jeśli polecenie cmdlet tworzy nowy wątek i kod działający w tym wątku zawiera nieobsługiwany wyjątek, programu Windows PowerShell nie będzie przechwytywać błąd i zakończy proces.</span><span class="sxs-lookup"><span data-stu-id="6edb4-157">If a cmdlet creates a new thread and code running in that thread throws an unhandled exception, Windows PowerShell will not catch the error and will terminate the process.</span></span>

- <span data-ttu-id="6edb4-158">Jeśli obiekt ma kod w metody Dispose lub destruktor, który powoduje, że nieobsługiwany wyjątek, programu Windows PowerShell nie będzie przechwytywać błąd i zakończy proces.</span><span class="sxs-lookup"><span data-stu-id="6edb4-158">If an object has code in its destructor or Dispose methods that causes an unhandled exception, Windows PowerShell will not catch the error and will terminate the process.</span></span>

## <a name="reporting-nonterminating-errors"></a><span data-ttu-id="6edb4-159">Błędy niekończące raportowania</span><span class="sxs-lookup"><span data-stu-id="6edb4-159">Reporting Nonterminating Errors</span></span>

<span data-ttu-id="6edb4-160">Jeden z metody przetwarzania danych wejściowych zgłosić błąd niekończące do strumienia wyjściowego przy użyciu [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metody.</span><span class="sxs-lookup"><span data-stu-id="6edb4-160">Any one of the input processing methods can report a nonterminating error to the output stream using the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span> <span data-ttu-id="6edb4-161">Poniżej przedstawiono przykładowy kod z tego polecenia cmdlet Get-Proc, który ilustruje wywołanie [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) z w ramach zastępowania metody [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody.</span><span class="sxs-lookup"><span data-stu-id="6edb4-161">Here is a code example from this Get-Proc cmdlet that illustrates the call to [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="6edb4-162">W tym przypadku jest nawiązywane połączenie, jeśli polecenie cmdlet nie można odnaleźć procesu dla identyfikatora określonego procesu.</span><span class="sxs-lookup"><span data-stu-id="6edb4-162">In this case, the call is made if the cmdlet cannot find a process for a specified process identifier.</span></span>

```csharp
protected override void ProcessRecord()
{
  // If no name parameter passed to cmdlet, get all processes.
  if (processNames == null)
  {
    WriteObject(Process.GetProcesses(), true);
  }
    else
    {
      // If a name parameter is passed to cmdlet, get and write
      // the associated processes.
      // Write a nonterminating error for failure to retrieve
      // a process.
      foreach (string name in processNames)
      {
        Process[] processes;

        try
        {
          processes = Process.GetProcessesByName(name);
        }
        catch (InvalidOperationException ex)
        {
          WriteError(new ErrorRecord(
                     ex,
                     "NameNotFound",
                     ErrorCategory.InvalidOperation,
                     name));
          continue;
        }

        WriteObject(processes, true);
      } // foreach (...
    } // else
  }
```

#### <a name="things-to-remember-about-writing-nonterminating-errors"></a><span data-ttu-id="6edb4-163">Warto zapamiętać o pisaniu błędy niekończące</span><span class="sxs-lookup"><span data-stu-id="6edb4-163">Things to Remember About Writing Nonterminating Errors</span></span>

<span data-ttu-id="6edb4-164">Błąd niekończące polecenia cmdlet należy wygenerować identyfikatora wystąpienia określonego błędu dla każdego określonego obiektu wejściowego.</span><span class="sxs-lookup"><span data-stu-id="6edb4-164">For a nonterminating error, the cmdlet must generate a specific error identifier for each specific input object.</span></span>

<span data-ttu-id="6edb4-165">Polecenia cmdlet często musi zmodyfikować akcji programu Windows PowerShell, generowane przez niekończące błędu.</span><span class="sxs-lookup"><span data-stu-id="6edb4-165">A cmdlet frequently needs to modify the Windows PowerShell action produced by a nonterminating error.</span></span> <span data-ttu-id="6edb4-166">Jego można to zrobić, definiując `ErrorAction` i `ErrorVariable` parametrów.</span><span class="sxs-lookup"><span data-stu-id="6edb4-166">It can do this by defining the `ErrorAction` and `ErrorVariable` parameters.</span></span> <span data-ttu-id="6edb4-167">Jeśli definiowanie `ErrorAction` parametru polecenia cmdlet przedstawia opcje użytkownika [System.Management.Automation.Actionpreference](/dotnet/api/system.management.automation.actionpreference), można również bezpośrednio wpływają na akcję, ustawiając `$ErrorActionPreference` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="6edb4-167">If defining the `ErrorAction` parameter, the cmdlet presents the user options [System.Management.Automation.Actionpreference](/dotnet/api/system.management.automation.actionpreference), you can also directly influence the action by setting the `$ErrorActionPreference` variable.</span></span>

<span data-ttu-id="6edb4-168">Polecenia cmdlet można zapisać błędy niekończące do zmiennej za pomocą `ErrorVariable` parametr, który nie ma wpływu ustawienia `ErrorAction`.</span><span class="sxs-lookup"><span data-stu-id="6edb4-168">The cmdlet can save nonterminating errors to a variable using the `ErrorVariable` parameter, which is not affected by the setting of `ErrorAction`.</span></span> <span data-ttu-id="6edb4-169">Błędy można dołączyć do istniejącej zmiennej błąd, dodając znak plus (+) na początku nazwy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="6edb4-169">Failures can be appended to an existing error variable by adding a plus sign (+) to the front of the variable name.</span></span>

## <a name="code-sample"></a><span data-ttu-id="6edb4-170">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="6edb4-170">Code Sample</span></span>

<span data-ttu-id="6edb4-171">Aby uzyskać pełne C# przykładowego kodu, zobacz [przykładowe GetProcessSample04](./getprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="6edb4-171">For the complete C# sample code, see [GetProcessSample04 Sample](./getprocesssample04-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="6edb4-172">Zdefiniuj typy obiektów i formatowanie</span><span class="sxs-lookup"><span data-stu-id="6edb4-172">Define Object Types and Formatting</span></span>

<span data-ttu-id="6edb4-173">Program Windows PowerShell przekazuje informacje między poleceniami cmdlet, używając obiektów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="6edb4-173">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="6edb4-174">W związku z tym polecenie cmdlet może się okazać zdefiniowanie swój własny typ, lub polecenie cmdlet może być konieczne rozszerzenie istniejącego typu dostarczane przez inne polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6edb4-174">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="6edb4-175">Aby uzyskać więcej informacji na temat definiowania nowych typów lub rozszerzanie istniejących typów, zobacz [rozszerzanie typów obiektów i formatowanie](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="6edb4-175">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="6edb4-176">Tworzenie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="6edb4-176">Building the Cmdlet</span></span>

<span data-ttu-id="6edb4-177">Po zaimplementowaniu polecenia cmdlet, należy zarejestrować go za pomocą programu Windows PowerShell za pomocą przystawki programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6edb4-177">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="6edb4-178">Aby uzyskać więcej informacji na temat rejestrowania poleceń cmdlet, zobacz [sposób zarejestrować poleceń cmdlet, dostawców i hostowania aplikacji](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="6edb4-178">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="6edb4-179">Testowanie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="6edb4-179">Testing the Cmdlet</span></span>

<span data-ttu-id="6edb4-180">Po zarejestrowaniu Twojego polecenia cmdlet przy użyciu programu Windows PowerShell można ją przetestować, uruchamiając go w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="6edb4-180">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="6edb4-181">Teraz przetestuj przykładowe polecenie cmdlet Get-Proc aby zobaczyć, czy zgłasza błąd:</span><span class="sxs-lookup"><span data-stu-id="6edb4-181">Let's test the sample Get-Proc cmdlet to see whether it reports an error:</span></span>

- <span data-ttu-id="6edb4-182">Uruchom program Windows PowerShell i użyj polecenia cmdlet Get-Proc można pobrać procesów o nazwie "TEST".</span><span class="sxs-lookup"><span data-stu-id="6edb4-182">Start Windows PowerShell, and use the Get-Proc cmdlet to retrieve the processes named "TEST".</span></span>

    ```powershell
    PS> get-proc -name test
    ```

<span data-ttu-id="6edb4-183">Zostanie wyświetlone następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="6edb4-183">The following output appears.</span></span>

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a><span data-ttu-id="6edb4-184">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6edb4-184">See Also</span></span>

[<span data-ttu-id="6edb4-185">Dodając parametry, z których potok przetwarzania danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="6edb4-185">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="6edb4-186">Dodając parametry, które przetwarzają dane wejściowe wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="6edb4-186">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="6edb4-187">Tworzenie swojej pierwszej polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6edb4-187">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="6edb4-188">Formatowanie i rozszerzanie typy obiektów</span><span class="sxs-lookup"><span data-stu-id="6edb4-188">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="6edb4-189">Jak zarejestrować poleceń cmdlet, dostawców i aplikacji hosta</span><span class="sxs-lookup"><span data-stu-id="6edb4-189">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="6edb4-190">Dokumentacja programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6edb4-190">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="6edb4-191">Przykłady polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="6edb4-191">Cmdlet Samples</span></span>](./cmdlet-samples.md)
