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
ms.openlocfilehash: 3741982f81efa04d8fe7ab448fba5f2fdf4b0c01
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068868"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a><span data-ttu-id="a24d7-102">Dodawanie raportowania błędów niepowodujących zakończenia działania do polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="a24d7-102">Adding Non-Terminating Error Reporting to Your Cmdlet</span></span>

<span data-ttu-id="a24d7-103">Polecenia cmdlet mogą raportować błędy niekończące, wywołując [System.Management.Automation.Cmdlet.WriteError][] metody i nadal będzie mogła działać na bieżący obiekt danych wejściowych lub dalsze przychodzące potoku obiektów.</span><span class="sxs-lookup"><span data-stu-id="a24d7-103">Cmdlets can report nonterminating errors by calling the [System.Management.Automation.Cmdlet.WriteError][] method and still continue to operate on the current input object or on further incoming pipeline objects.</span></span>
<span data-ttu-id="a24d7-104">W tej sekcji opisano sposób tworzenia polecenia cmdlet, który zgłasza błędy niekończące z jego metody przetwarzania danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="a24d7-104">This section explains how to create a cmdlet that reports nonterminating errors from its input processing methods.</span></span>

<span data-ttu-id="a24d7-105">Błędy niekończące (a także błędy kończący), należy przekazać polecenie cmdlet [System.Management.Automation.ErrorRecord][] obiektu zidentyfikować błąd.</span><span class="sxs-lookup"><span data-stu-id="a24d7-105">For nonterminating errors (as well as terminating errors), the cmdlet must pass an [System.Management.Automation.ErrorRecord][] object identifying the error.</span></span>
<span data-ttu-id="a24d7-106">Każdy rekord błędu jest identyfikowany przez unikatowego ciągu o nazwie "Identyfikator błędu".</span><span class="sxs-lookup"><span data-stu-id="a24d7-106">Each error record is identified by a unique string called the "error identifier".</span></span>
<span data-ttu-id="a24d7-107">Oprócz identyfikatora kategorii każdego błędu jest określona przez stałe zdefiniowane przez [System.Management.Automation.ErrorCategory][] wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="a24d7-107">In addition to the identifier, the category of each error is specified by constants defined by a [System.Management.Automation.ErrorCategory][] enumeration.</span></span>
<span data-ttu-id="a24d7-108">Użytkownik może wyświetlić błędy na podstawie ich kategorii, ustawiając `$ErrorView` zmienną "CategoryView".</span><span class="sxs-lookup"><span data-stu-id="a24d7-108">The user can view errors based on their category by setting the `$ErrorView` variable to "CategoryView".</span></span>

<span data-ttu-id="a24d7-109">Aby uzyskać więcej informacji na temat rekordów błędów, zobacz [rekordów błędów programu Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="a24d7-109">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="a24d7-110">Definiowanie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="a24d7-110">Defining the Cmdlet</span></span>

<span data-ttu-id="a24d7-111">Pierwszym krokiem w procesie tworzenia polecenia cmdlet jest zawsze nazewnictwa polecenia cmdlet i deklarowanie klasy .NET, która implementuje polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a24d7-111">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span>
<span data-ttu-id="a24d7-112">To polecenie cmdlet pobiera informacje o procesu, więc nazwę zlecenie wybrane w tym miejscu to "Get".</span><span class="sxs-lookup"><span data-stu-id="a24d7-112">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span>
<span data-ttu-id="a24d7-113">(Prawie dowolny rodzaj polecenia cmdlet, który jest zdolny do pobierania informacji o może przetwarzać dane wejściowe wiersza polecenia). Aby uzyskać więcej informacji na temat polecenia cmdlet zatwierdzonych czasowników, zobacz [nazwy zlecenie poleceń Cmdlet](approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="a24d7-113">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="a24d7-114">Poniżej przedstawiono definicję dla tego polecenia cmdlet Get-Proc.</span><span class="sxs-lookup"><span data-stu-id="a24d7-114">The following is the definition for this Get-Proc cmdlet.</span></span>
<span data-ttu-id="a24d7-115">Szczegóły tej definicji są podane w [tworzenia Your pierwsze polecenie Cmdlet](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="a24d7-115">Details of this definition are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a><span data-ttu-id="a24d7-116">Definiowanie parametrów</span><span class="sxs-lookup"><span data-stu-id="a24d7-116">Defining Parameters</span></span>

<span data-ttu-id="a24d7-117">W razie potrzeby Twojego polecenia cmdlet należy zdefiniować parametry w celu przetwarzania danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="a24d7-117">If necessary, your cmdlet must define parameters for processing input.</span></span>
<span data-ttu-id="a24d7-118">To polecenie cmdlet Get-Proc definiuje **nazwa** parametru, zgodnie z opisem w [dodając parametry te dane wejściowe wiersza polecenia procesu](adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="a24d7-118">This Get-Proc cmdlet defines a **Name** parameter as described in [Adding Parameters that Process Command-Line Input](adding-parameters-that-process-command-line-input.md).</span></span>

<span data-ttu-id="a24d7-119">Poniżej przedstawiono deklaracji parametru pod kątem **nazwa** parametrów to polecenie cmdlet Get-Proc.</span><span class="sxs-lookup"><span data-stu-id="a24d7-119">Here is the parameter declaration for the **Name** parameter of this Get-Proc cmdlet.</span></span>

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

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="a24d7-120">Zastępowanie metody przetwarzania danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="a24d7-120">Overriding Input Processing Methods</span></span>

<span data-ttu-id="a24d7-121">Wszystkie polecenia cmdlet muszą przesłaniać co najmniej jedną z metod dostarczonych przez przetwarzanie danych wejściowych [System.Management.Automation.Cmdlet][] klasy.</span><span class="sxs-lookup"><span data-stu-id="a24d7-121">All cmdlets must override at least one of the input processing methods provided by the [System.Management.Automation.Cmdlet][] class.</span></span>
<span data-ttu-id="a24d7-122">Te metody są omówione w [tworzenia Your pierwsze polecenie Cmdlet](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="a24d7-122">These methods are discussed in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="a24d7-123">Twojego polecenia cmdlet powinny obsługiwać każdego wybranego rekordu jako niezależne, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="a24d7-123">Your cmdlet should handle each record as independently as possible.</span></span>

<span data-ttu-id="a24d7-124">To polecenie cmdlet Get-Proc zastępuje [System.Management.Automation.Cmdlet.ProcessRecord][] metody, aby obsłużyć **nazwa** parametr dla danych wejściowych dostarczonych przez użytkownika lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="a24d7-124">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord][] method to handle the **Name** parameter for input provided by the user or a script.</span></span>
<span data-ttu-id="a24d7-125">Ta metoda zostanie wyświetlony procesy dla każdej nazwy żądanej procesu lub wszystkich procesów, jeśli podano żadnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="a24d7-125">This method will get the processes for each requested process name or all processes if no name is provided.</span></span>
<span data-ttu-id="a24d7-126">Szczegóły to zastąpienie są podane w [tworzenia Your pierwsze polecenie Cmdlet](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="a24d7-126">Details of this override are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

### <a name="things-to-remember-when-reporting-errors"></a><span data-ttu-id="a24d7-127">Warto zapamiętać, gdy raportowanie błędów</span><span class="sxs-lookup"><span data-stu-id="a24d7-127">Things to Remember When Reporting Errors</span></span>

<span data-ttu-id="a24d7-128">[System.Management.Automation.ErrorRecord][] obiektu, że polecenia cmdlet przekazuje podczas pisania błąd wymaga wyjątek podstawą.</span><span class="sxs-lookup"><span data-stu-id="a24d7-128">The [System.Management.Automation.ErrorRecord][] object that the cmdlet passes when writing an error requires an exception at its core.</span></span>
<span data-ttu-id="a24d7-129">Podczas określania wyjątek do użycia, postępuj zgodnie z wytycznymi dla platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="a24d7-129">Follow the .NET guidelines when determining the exception to use.</span></span>
<span data-ttu-id="a24d7-130">Zasadniczo Jeśli błąd semantycznie jest taka sama jak istniejące wyjątek, polecenia cmdlet należy użyć lub pochodzić od tego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="a24d7-130">Basically, if the error is semantically the same as an existing exception, the cmdlet should use or derive from that exception.</span></span>
<span data-ttu-id="a24d7-131">W przeciwnym razie powinien pochodzić, nowy wyjątek lub hierarchia wyjątków bezpośrednio z [System.Exception][] klasy.</span><span class="sxs-lookup"><span data-stu-id="a24d7-131">Otherwise, it should derive a new exception or exception hierarchy directly from the [System.Exception][] class.</span></span>

<span data-ttu-id="a24d7-132">Podczas tworzenia identyfikatorów błędu (dostępne za pośrednictwem właściwości FullyQualifiedErrorId klasy rekord błędu) pamiętać o następujących.</span><span class="sxs-lookup"><span data-stu-id="a24d7-132">When creating error identifiers (accessed through the FullyQualifiedErrorId property of the ErrorRecord class) keep the following in mind.</span></span>

- <span data-ttu-id="a24d7-133">Ciągi użycia, które są przeznaczone do celów diagnostycznych, aby podczas sprawdzania w pełni kwalifikowanego identyfikatora można określić, jaki dokładnie błąd i w przypadku, gdy błąd pochodzi z.</span><span class="sxs-lookup"><span data-stu-id="a24d7-133">Use strings that are targeted for diagnostic purposes so that when inspecting the fully qualified identifier you can determine what the error is and where the error came from.</span></span>

- <span data-ttu-id="a24d7-134">Identyfikator formy błąd w pełni kwalifikowana może wyglądać następująco.</span><span class="sxs-lookup"><span data-stu-id="a24d7-134">A well formed fully qualified error identifier might be as follows.</span></span>

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

<span data-ttu-id="a24d7-135">Należy zauważyć, że w poprzednim przykładzie identyfikator błędu (pierwszy token) wskazuje na to, co to jest błąd i pozostałej części wskazuje, skąd pochodzą błędu.</span><span class="sxs-lookup"><span data-stu-id="a24d7-135">Notice that in the previous example, the error identifier (the first token) designates what the error is and the remaining part indicates where the error came from.</span></span>

- <span data-ttu-id="a24d7-136">W przypadku bardziej złożonych scenariuszy Identyfikator błędu może być token oddzielone kropką, który może zostać przeanalizowany w zakresie kontroli.</span><span class="sxs-lookup"><span data-stu-id="a24d7-136">For more complex scenarios, the error identifier can be a dot separated token that can be parsed on inspection.</span></span>
  <span data-ttu-id="a24d7-137">Dzięki temu za gałęzi na części identyfikator błędu, a także kategoria błędu identyfikator i błędów.</span><span class="sxs-lookup"><span data-stu-id="a24d7-137">This allows you too branch on the parts of the error identifier as well as the error identifier and error category.</span></span>

<span data-ttu-id="a24d7-138">Polecenia cmdlet należy przypisać różne ścieżki identyfikatorów wystąpienia określonego błędu.</span><span class="sxs-lookup"><span data-stu-id="a24d7-138">The cmdlet should assign specific error identifiers to different code paths.</span></span>
<span data-ttu-id="a24d7-139">Pamiętać następujące informacje do przypisywania identyfikatorów, błąd:</span><span class="sxs-lookup"><span data-stu-id="a24d7-139">Keep the following information in mind for assignment of error identifiers:</span></span>

- <span data-ttu-id="a24d7-140">Identyfikator błędu należy pozostaje niezmienna przez cały cykl jej polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a24d7-140">An error identifier should remain constant throughout the cmdlet life cycle.</span></span>
  <span data-ttu-id="a24d7-141">Nie należy zmieniać semantyki odpowiadającym błędzie między wersjami polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a24d7-141">Do not change the semantics of an error identifier between cmdlet versions.</span></span>

- <span data-ttu-id="a24d7-142">Tekst na użytek odpowiadający lapidarnie błąd raportowany Identyfikator błędu.</span><span class="sxs-lookup"><span data-stu-id="a24d7-142">Use text for an error identifier that tersely corresponds to the error being reported.</span></span>
  <span data-ttu-id="a24d7-143">Nie należy używać biały znak lub znaki interpunkcyjne.</span><span class="sxs-lookup"><span data-stu-id="a24d7-143">Do not use white space or punctuation.</span></span>

- <span data-ttu-id="a24d7-144">Mieć Twojego polecenia cmdlet wygenerować tylko identyfikatory błędów, które są do odtworzenia.</span><span class="sxs-lookup"><span data-stu-id="a24d7-144">Have your cmdlet generate only error identifiers that are reproducible.</span></span>
  <span data-ttu-id="a24d7-145">Na przykład nie powinna ona generować identyfikator, który zawiera identyfikator procesu.</span><span class="sxs-lookup"><span data-stu-id="a24d7-145">For example, it should not generate an identifier that includes a process identifier.</span></span>
  <span data-ttu-id="a24d7-146">Błąd identyfikatory są przydatne do użytkownika, tylko wtedy, gdy odnoszą się do identyfikatorów, które są widoczne dla innych użytkowników, w której występuje ten sam problem.</span><span class="sxs-lookup"><span data-stu-id="a24d7-146">Error identifiers are useful to a user only when they correspond to identifiers that are seen by other users experiencing the same problem.</span></span>

<span data-ttu-id="a24d7-147">Nieobsługiwane wyjątki nie są objęte programu PowerShell w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="a24d7-147">Unhandled exceptions are not caught by PowerShell in the following conditions:</span></span>

- <span data-ttu-id="a24d7-148">Jeśli polecenie cmdlet tworzy nowy wątek i kod działający w tym wątku zawiera nieobsługiwany wyjątek, programu PowerShell nie będzie przechwytywać błąd i zakończy proces.</span><span class="sxs-lookup"><span data-stu-id="a24d7-148">If a cmdlet creates a new thread and code running in that thread throws an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>

- <span data-ttu-id="a24d7-149">Jeśli obiekt ma kod w metody Dispose lub destruktor, który powoduje, że nieobsługiwany wyjątek, programu PowerShell nie będzie przechwytywać błąd i zakończy proces.</span><span class="sxs-lookup"><span data-stu-id="a24d7-149">If an object has code in its destructor or Dispose methods that causes an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>

## <a name="reporting-nonterminating-errors"></a><span data-ttu-id="a24d7-150">Błędy niekończące raportowania</span><span class="sxs-lookup"><span data-stu-id="a24d7-150">Reporting Nonterminating Errors</span></span>

<span data-ttu-id="a24d7-151">Jeden z metody przetwarzania danych wejściowych zgłosić błąd niekończące do strumienia wyjściowego przy użyciu [System.Management.Automation.Cmdlet.WriteError][] metody.</span><span class="sxs-lookup"><span data-stu-id="a24d7-151">Any one of the input processing methods can report a nonterminating error to the output stream using the [System.Management.Automation.Cmdlet.WriteError][] method.</span></span>

<span data-ttu-id="a24d7-152">Poniżej przedstawiono przykładowy kod z tego polecenia cmdlet Get-Proc, który ilustruje wywołanie [System.Management.Automation.Cmdlet.WriteError][] z w ramach zastępowania metody [System.Management.Automation.Cmdlet.ProcessRecord][] metody.</span><span class="sxs-lookup"><span data-stu-id="a24d7-152">Here is a code example from this Get-Proc cmdlet that illustrates the call to [System.Management.Automation.Cmdlet.WriteError][] from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord][] method.</span></span>
<span data-ttu-id="a24d7-153">W tym przypadku jest nawiązywane połączenie, jeśli polecenie cmdlet nie można odnaleźć procesu dla identyfikatora określonego procesu.</span><span class="sxs-lookup"><span data-stu-id="a24d7-153">In this case, the call is made if the cmdlet cannot find a process for a specified process identifier.</span></span>

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

### <a name="things-to-remember-about-writing-nonterminating-errors"></a><span data-ttu-id="a24d7-154">Warto zapamiętać o pisaniu błędy niekończące</span><span class="sxs-lookup"><span data-stu-id="a24d7-154">Things to Remember About Writing Nonterminating Errors</span></span>

<span data-ttu-id="a24d7-155">Błąd niekończące polecenia cmdlet należy wygenerować identyfikatora wystąpienia określonego błędu dla każdego określonego obiektu wejściowego.</span><span class="sxs-lookup"><span data-stu-id="a24d7-155">For a nonterminating error, the cmdlet must generate a specific error identifier for each specific input object.</span></span>

<span data-ttu-id="a24d7-156">Polecenia cmdlet często musi zmodyfikować produkowane przez niekończące Błąd akcji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a24d7-156">A cmdlet frequently needs to modify the PowerShell action produced by a nonterminating error.</span></span>
<span data-ttu-id="a24d7-157">Jego można to zrobić, definiując `ErrorAction` i `ErrorVariable` parametrów.</span><span class="sxs-lookup"><span data-stu-id="a24d7-157">It can do this by defining the `ErrorAction` and `ErrorVariable` parameters.</span></span>
<span data-ttu-id="a24d7-158">Jeśli definiowanie `ErrorAction` parametru polecenia cmdlet przedstawia opcje użytkownika [System.Management.Automation.ActionPreference][], można również bezpośrednio wpływają na akcję, ustawiając `$ErrorActionPreference` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="a24d7-158">If defining the `ErrorAction` parameter, the cmdlet presents the user options [System.Management.Automation.ActionPreference][], you can also directly influence the action by setting the `$ErrorActionPreference` variable.</span></span>

<span data-ttu-id="a24d7-159">Polecenia cmdlet można zapisać błędy niekończące do zmiennej za pomocą `ErrorVariable` parametr, który nie ma wpływu ustawienia `ErrorAction`.</span><span class="sxs-lookup"><span data-stu-id="a24d7-159">The cmdlet can save nonterminating errors to a variable using the `ErrorVariable` parameter, which is not affected by the setting of `ErrorAction`.</span></span>
<span data-ttu-id="a24d7-160">Błędy można dołączyć do istniejącej zmiennej błąd, dodając znak plus (+) na początku nazwy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="a24d7-160">Failures can be appended to an existing error variable by adding a plus sign (+) to the front of the variable name.</span></span>

## <a name="code-sample"></a><span data-ttu-id="a24d7-161">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="a24d7-161">Code Sample</span></span>

<span data-ttu-id="a24d7-162">Aby uzyskać pełne C# przykładowego kodu, zobacz [przykładowe GetProcessSample04](./getprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="a24d7-162">For the complete C# sample code, see [GetProcessSample04 Sample](./getprocesssample04-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="a24d7-163">Zdefiniuj typy obiektów i formatowanie</span><span class="sxs-lookup"><span data-stu-id="a24d7-163">Define Object Types and Formatting</span></span>

<span data-ttu-id="a24d7-164">Program PowerShell przekazuje informacje między poleceniami cmdlet, używając obiektów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="a24d7-164">PowerShell passes information between cmdlets using .NET objects.</span></span>
<span data-ttu-id="a24d7-165">W związku z tym polecenie cmdlet może się okazać zdefiniowanie swój własny typ, lub polecenie cmdlet może być konieczne rozszerzenie istniejącego typu dostarczane przez inne polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a24d7-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span>
<span data-ttu-id="a24d7-166">Aby uzyskać więcej informacji na temat definiowania nowych typów lub rozszerzanie istniejących typów, zobacz [rozszerzanie typów obiektów i formatowanie](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="a24d7-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="a24d7-167">Tworzenie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="a24d7-167">Building the Cmdlet</span></span>

<span data-ttu-id="a24d7-168">Po zaimplementowaniu polecenia cmdlet, należy zarejestrować go za pomocą programu Windows PowerShell za pomocą przystawki programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a24d7-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span>
<span data-ttu-id="a24d7-169">Aby uzyskać więcej informacji na temat rejestrowania poleceń cmdlet, zobacz [sposób zarejestrować poleceń cmdlet, dostawców i hostowania aplikacji](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="a24d7-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="a24d7-170">Testowanie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="a24d7-170">Testing the Cmdlet</span></span>

<span data-ttu-id="a24d7-171">Po zarejestrowaniu Twojego polecenia cmdlet przy użyciu programu PowerShell można ją przetestować, uruchamiając go w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="a24d7-171">When your cmdlet has been registered with PowerShell, you can test it by running it on the command line.</span></span>
<span data-ttu-id="a24d7-172">Teraz przetestuj przykładowe polecenie cmdlet Get-Proc aby zobaczyć, czy zgłasza błąd:</span><span class="sxs-lookup"><span data-stu-id="a24d7-172">Let's test the sample Get-Proc cmdlet to see whether it reports an error:</span></span>

- <span data-ttu-id="a24d7-173">Uruchom program PowerShell i użyj polecenia cmdlet Get-Proc można pobrać procesów o nazwie "TEST".</span><span class="sxs-lookup"><span data-stu-id="a24d7-173">Start PowerShell, and use the Get-Proc cmdlet to retrieve the processes named "TEST".</span></span>

    ```powershell
    PS> get-proc -name test
    ```

<span data-ttu-id="a24d7-174">Zostanie wyświetlone następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="a24d7-174">The following output appears.</span></span>

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a><span data-ttu-id="a24d7-175">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a24d7-175">See Also</span></span>

[<span data-ttu-id="a24d7-176">Dodając parametry, z których potok przetwarzania danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="a24d7-176">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="a24d7-177">Dodając parametry, które przetwarzają dane wejściowe wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="a24d7-177">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="a24d7-178">Tworzenie swojej pierwszej polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a24d7-178">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="a24d7-179">Formatowanie i rozszerzanie typy obiektów</span><span class="sxs-lookup"><span data-stu-id="a24d7-179">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="a24d7-180">Jak zarejestrować poleceń cmdlet, dostawców i aplikacji hosta</span><span class="sxs-lookup"><span data-stu-id="a24d7-180">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="a24d7-181">Dokumentacja programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a24d7-181">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="a24d7-182">Przykłady polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="a24d7-182">Cmdlet Samples</span></span>](./cmdlet-samples.md)

[System.Exception]: /dotnet/api/System.Exception
[System.Management.Automation.ActionPreference]: /dotnet/api/System.Management.Automation.ActionPreference
[System.Management.Automation.Cmdlet.ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System.Management.Automation.Cmdlet.WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System.Management.Automation.Cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System.Management.Automation.ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System.Management.Automation.ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
