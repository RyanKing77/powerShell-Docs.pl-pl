---
title: Dodawanie użytkownika wiadomości do Twojego polecenia Cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WriteWarning
- notifications, writing
- progress notification
- WriteVerbose
- Stop-Proc
- WriteProgress
- WriteDebug
- notifications, debug
- ProgressRecord
- samples, Stop-Proc cmdlet
- notifications, progress
- notifications, warning
- WriteObject
- WriteError
- verbose notification
- ProcessRecord
- notifications, verbose
- debug notification
- cmdlet, writing notifications
- warning
- code sample, user notifications
- user notifications
ms.assetid: 14c13acb-f0b7-4613-bc7d-c361d14da1a2
caps.latest.revision: 8
ms.openlocfilehash: 138c6a43937e72fffaa2a09243e500e9822e6111
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854939"
---
# <a name="adding-user-messages-to-your-cmdlet"></a><span data-ttu-id="7ee10-102">Dodawanie wiadomości użytkownika do polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="7ee10-102">Adding User Messages to Your Cmdlet</span></span>

<span data-ttu-id="7ee10-103">Polecenia cmdlet można napisać kilka rodzajów wiadomości, które mogą być wyświetlane użytkownikowi w czasie wykonywania programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7ee10-103">Cmdlets can write several kinds of messages that can be displayed to the user by the Windows PowerShell runtime.</span></span> <span data-ttu-id="7ee10-104">Te komunikaty zawierają następujące typy:</span><span class="sxs-lookup"><span data-stu-id="7ee10-104">These messages include the following types:</span></span>

- <span data-ttu-id="7ee10-105">Pełne komunikaty, które zawierają ogólne informacje o użytkowniku.</span><span class="sxs-lookup"><span data-stu-id="7ee10-105">Verbose messages that contain general user information.</span></span>

- <span data-ttu-id="7ee10-106">Debugowanie komunikatów, które zawierają informacje dotyczące rozwiązywania problemów.</span><span class="sxs-lookup"><span data-stu-id="7ee10-106">Debug messages that contain troubleshooting information.</span></span>

- <span data-ttu-id="7ee10-107">Komunikaty ostrzegawcze, które zawierają powiadomienie, że polecenie cmdlet ma wykonywać operacji, która może mieć nieoczekiwane wyniki.</span><span class="sxs-lookup"><span data-stu-id="7ee10-107">Warning messages that contain a notification that the cmdlet is about to perform an operation that can have unexpected results.</span></span>

- <span data-ttu-id="7ee10-108">Raport postęp polecenia cmdlet działać, komunikaty, które zawierają informacje o ile zostało zakończone, podczas wykonywania operacji, która zajmuje dużo czasu.</span><span class="sxs-lookup"><span data-stu-id="7ee10-108">Progress report messages that contain information about how much work the cmdlet has completed when performing an operation that takes a long time.</span></span>

<span data-ttu-id="7ee10-109">Nie ma ograniczeń liczby wiadomości, które może zapisać Twojego polecenia cmdlet lub typ wiadomości, które zapisuje Twojego polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7ee10-109">There are no limits to the number of messages that your cmdlet can write or the type of messages that your cmdlet writes.</span></span> <span data-ttu-id="7ee10-110">Każdy komunikat jest zapisywany, wprowadzając wywołania określone dane wejściowe przetwarzania metody Twojego polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7ee10-110">Each message is written by making a specific call from within the input processing method of your cmdlet.</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="7ee10-111">Definiowanie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="7ee10-111">Defining the Cmdlet</span></span>

<span data-ttu-id="7ee10-112">Pierwszym krokiem w procesie tworzenia polecenia cmdlet jest zawsze nazewnictwa polecenia cmdlet i deklarowanie klasy .NET, która implementuje polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7ee10-112">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="7ee10-113">Dowolny rodzaj polecenia cmdlet można napisać powiadomienia użytkownika z metody; przetwarzania danych wejściowych tak ogólnie rzecz biorąc, możesz nazwać tego polecenia cmdlet przy użyciu dowolnej zlecenie, która wskazuje, jakie modyfikacje system wykonuje polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7ee10-113">Any sort of cmdlet can write user notifications from its input processing methods; so, in general, you can name this cmdlet using any verb that indicates what system modifications the cmdlet performs.</span></span> <span data-ttu-id="7ee10-114">Aby uzyskać więcej informacji na temat polecenia cmdlet zatwierdzonych czasowników, zobacz [nazwy zlecenie poleceń Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="7ee10-114">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="7ee10-115">Polecenia cmdlet Stop-Proc jest przeznaczony do modyfikacji systemu; w związku z tym [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) deklaracja klasy .NET musi zawierać `SupportsShouldProcess` atrybutu — słowo kluczowe i można ustawić `true`.</span><span class="sxs-lookup"><span data-stu-id="7ee10-115">The Stop-Proc cmdlet is designed to modify the system; therefore, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration for the .NET class must include the `SupportsShouldProcess` attribute keyword and be set to `true`.</span></span>

<span data-ttu-id="7ee10-116">Poniższy kod jest definicji dla tej klasy polecenia cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="7ee10-116">The following code is the definition for this Stop-Proc cmdlet class.</span></span> <span data-ttu-id="7ee10-117">Aby uzyskać więcej informacji na temat tej definicji, zobacz [Tworzenie polecenia Cmdlet, który modyfikuje System](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="7ee10-117">For more information about this definition, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="7ee10-118">Definiowanie parametrów modyfikacji systemu</span><span class="sxs-lookup"><span data-stu-id="7ee10-118">Defining Parameters for System Modification</span></span>

<span data-ttu-id="7ee10-119">Polecenie cmdlet Stop-Proc definiuje trzy parametry: `Name`, `Force`, i `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="7ee10-119">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span> <span data-ttu-id="7ee10-120">Aby uzyskać więcej informacji na temat definiowania tych parametrów, zobacz [Tworzenie polecenia Cmdlet, który modyfikuje System](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="7ee10-120">For more information about defining these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

<span data-ttu-id="7ee10-121">Poniżej przedstawiono deklaracji parametrów dla polecenia cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="7ee10-121">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

```csharp
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;

/// <summary>
/// Specify the Force parameter that allows the user to override
/// the ShouldContinue call to force the stop operation. This
/// parameter should always be used with caution.
/// </summary>
[Parameter]
public SwitchParameter Force
{
  get { return force; }
  set { force = value; }
}
private bool force;

/// <summary>
/// Specify the PassThru parameter that allows the user to specify
/// that the cmdlet should pass the process object down the pipeline
/// after the process has been stopped.
/// </summary>
[Parameter]
public SwitchParameter PassThru
{
  get { return passThru; }
  set { passThru = value; }
}
private bool passThru;
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="7ee10-122">Zastępowanie metody przetwarzania danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="7ee10-122">Overriding an Input Processing Method</span></span>

<span data-ttu-id="7ee10-123">Twojego polecenia cmdlet jest przesłonięcie metody przetwarzania danych wejściowych, w większości przypadków będzie [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="7ee10-123">Your cmdlet must override an input processing method, most often it will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="7ee10-124">To polecenie cmdlet Stop-Proc zastępuje [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) przetwarzania metody wejściowej.</span><span class="sxs-lookup"><span data-stu-id="7ee10-124">This Stop-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) input processing method.</span></span> <span data-ttu-id="7ee10-125">W tej implementacji polecenia cmdlet Stop-Proc wywołań do zapisania pełne komunikaty wyjściowe komunikaty debugowania i komunikaty ostrzegawcze.</span><span class="sxs-lookup"><span data-stu-id="7ee10-125">In this implementation of the Stop-Proc cmdlet, calls are made to write verbose messages, debug messages, and warning messages.</span></span>

> [!NOTE]
> <span data-ttu-id="7ee10-126">Aby uzyskać więcej informacji na temat jak ta metoda wywołuje [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) i [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metod, zobacz [Tworzenie polecenia Cmdlet, który modyfikuje System](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="7ee10-126">For more information about how this method calls the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="writing-a-verbose-message"></a><span data-ttu-id="7ee10-127">Zapisywanie komunikat trybu informacji pełnej</span><span class="sxs-lookup"><span data-stu-id="7ee10-127">Writing a Verbose Message</span></span>

<span data-ttu-id="7ee10-128">[System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) metoda służy do zapisywania ogólne informacje na poziomie użytkownika, która nie ma wpływu na określone warunki błędów.</span><span class="sxs-lookup"><span data-stu-id="7ee10-128">The [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method is used to write general user-level information that is unrelated to specific error conditions.</span></span> <span data-ttu-id="7ee10-129">Administrator systemu może następnie używać tych informacji, aby kontynuować przetwarzania innych poleceń.</span><span class="sxs-lookup"><span data-stu-id="7ee10-129">The system administrator can then use that information to continue processing other commands.</span></span> <span data-ttu-id="7ee10-130">Ponadto powinien być zlokalizowany wszelkie informacje napisane przy użyciu tej metody, stosownie do potrzeb.</span><span class="sxs-lookup"><span data-stu-id="7ee10-130">In addition, any information written using this method should be localized as needed.</span></span>

<span data-ttu-id="7ee10-131">Poniższy kod z tego polecenia cmdlet Stop-Proc przedstawia dwa wywołania [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) metody z zastępowania metody [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody.</span><span class="sxs-lookup"><span data-stu-id="7ee10-131">The following code from this Stop-Proc cmdlet shows two calls to the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a><span data-ttu-id="7ee10-132">Zapisywanie komunikatów debugowania</span><span class="sxs-lookup"><span data-stu-id="7ee10-132">Writing a Debug Message</span></span>

<span data-ttu-id="7ee10-133">[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) metoda służy do zapisywania komunikatów debugowania, które mogą służyć do rozwiązywania problemów z polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7ee10-133">The [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method is used to write debug messages that can be used to troubleshoot the operation of the cmdlet.</span></span> <span data-ttu-id="7ee10-134">Wykonano wywołanie z metody przetwarzania danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="7ee10-134">The call is made from an input processing method.</span></span>

> [!NOTE]
> <span data-ttu-id="7ee10-135">Definiuje również środowiska Windows PowerShell `Debug` parametr, który przedstawia zarówno pełne i informacje o debugowaniu.</span><span class="sxs-lookup"><span data-stu-id="7ee10-135">Windows PowerShell also defines a `Debug` parameter that presents both verbose and debug information.</span></span> <span data-ttu-id="7ee10-136">Jeśli Twoje polecenie cmdlet obsługuje ten parametr, nie trzeba wywoływać [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) w ten sam kod, który wywołuje [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) .</span><span class="sxs-lookup"><span data-stu-id="7ee10-136">If your cmdlet supports this parameter, it does not need to call [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) in the same code that calls [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span></span>

<span data-ttu-id="7ee10-137">Następujące dwie sekcje kodu z przykładowe polecenie cmdlet Stop-Proc Pokaż wywołania [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) metody z zastępowania metody [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody.</span><span class="sxs-lookup"><span data-stu-id="7ee10-137">The following two sections of code from the sample Stop-Proc cmdlet show calls to the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="7ee10-138">Ten komunikat debugowania są zapisywane bezpośrednio przed [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="7ee10-138">This debug message is written immediately before [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) is called.</span></span>

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

<span data-ttu-id="7ee10-139">Ten komunikat debugowania są zapisywane bezpośrednio przed [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="7ee10-139">This debug message is written immediately before [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) is called.</span></span>

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

<span data-ttu-id="7ee10-140">Windows PowerShell automatycznie kieruje dowolnego [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) wywołania śledzenia infrastruktury i polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7ee10-140">Windows PowerShell automatically routes any [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) calls to the tracing infrastructure and cmdlets.</span></span> <span data-ttu-id="7ee10-141">Dzięki temu wywołania metody do śledzenia do hostowania aplikacji, plik lub debugera bez konieczności ponownego wykonać pracę dodatkowe rozwoju w ramach polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7ee10-141">This allows the method calls to be traced to the hosting application, a file, or a debugger without your having to do any extra development work within the cmdlet.</span></span> <span data-ttu-id="7ee10-142">Następujący wpis wiersza polecenia implementuje operacji śledzenia.</span><span class="sxs-lookup"><span data-stu-id="7ee10-142">The following command-line entry implements a tracing operation.</span></span>

<span data-ttu-id="7ee10-143">**PS > wyrażenie śledzenia stop-proc — plik proc.log — polecenia stop-proc Notatnik**</span><span class="sxs-lookup"><span data-stu-id="7ee10-143">**PS> trace-expression stop-proc -file proc.log -command stop-proc notepad**</span></span>

## <a name="writing-a-warning-message"></a><span data-ttu-id="7ee10-144">Zapisywanie komunikatu ostrzegawczego</span><span class="sxs-lookup"><span data-stu-id="7ee10-144">Writing a Warning Message</span></span>

<span data-ttu-id="7ee10-145">[System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) metoda służy do zapisywania ostrzeżenia, gdy polecenie cmdlet ma wykonać operacji, która może mieć nieoczekiwany wynik, na przykład zastąpienia pliku tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="7ee10-145">The [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method is used to write a warning when the cmdlet is about to perform an operation that might have an unexpected result, for example, overwriting a read-only file.</span></span>

<span data-ttu-id="7ee10-146">Poniższy kod z polecenia cmdlet Stop-Proc przykładowy pokazuje wywołanie [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) metody z zastępowania metody [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody.</span><span class="sxs-lookup"><span data-stu-id="7ee10-146">The following code from the sample Stop-Proc cmdlet shows the call to the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a><span data-ttu-id="7ee10-147">Zapisywanie komunikatu o postępie</span><span class="sxs-lookup"><span data-stu-id="7ee10-147">Writing a Progress Message</span></span>

<span data-ttu-id="7ee10-148">[System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) używany do zapisywania wiadomości dotyczące postępu podczas operacji polecenia cmdlet zająć dużo czasu wykonania.</span><span class="sxs-lookup"><span data-stu-id="7ee10-148">The [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) is used to write progress messages when cmdlet operations take an extended amount of time to complete.</span></span> <span data-ttu-id="7ee10-149">Wywołanie [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) przekazuje [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) obiekt, który jest wysyłany do hostowania aplikacji w celu renderowania dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7ee10-149">A call to [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passes a [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) object that is sent to the hosting application for rendering to the user.</span></span>

> [!NOTE]
> <span data-ttu-id="7ee10-150">To polecenie cmdlet Stop-Proc nie zawiera wywołanie [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) metody.</span><span class="sxs-lookup"><span data-stu-id="7ee10-150">This Stop-Proc cmdlet does not include a call to the [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span></span>

<span data-ttu-id="7ee10-151">Poniższy kod jest przykładem komunikat o postępie napisane przez polecenia cmdlet, które próbuje skopiować element.</span><span class="sxs-lookup"><span data-stu-id="7ee10-151">The following code is an example of a progress message written by a cmdlet that is attempting to copy an item.</span></span>

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a><span data-ttu-id="7ee10-152">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="7ee10-152">Code Sample</span></span>

<span data-ttu-id="7ee10-153">Aby uzyskać pełne C# przykładowego kodu, zobacz [przykładowe StopProcessSample02](./stopprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="7ee10-153">For the complete C# sample code, see [StopProcessSample02 Sample](./stopprocesssample02-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="7ee10-154">Zdefiniuj typy obiektów i formatowanie</span><span class="sxs-lookup"><span data-stu-id="7ee10-154">Define Object Types and Formatting</span></span>

<span data-ttu-id="7ee10-155">Program Windows PowerShell przekazuje informacje między poleceniami cmdlet, używając obiektów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="7ee10-155">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="7ee10-156">W związku z tym polecenie cmdlet może się okazać zdefiniowanie swój własny typ, lub polecenie cmdlet może być konieczne rozszerzenie istniejącego typu dostarczane przez inne polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7ee10-156">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="7ee10-157">Aby uzyskać więcej informacji na temat definiowania nowych typów lub rozszerzanie istniejących typów, zobacz [rozszerzanie typów obiektów i formatowanie](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="7ee10-157">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="7ee10-158">Tworzenie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="7ee10-158">Building the Cmdlet</span></span>

<span data-ttu-id="7ee10-159">Po zaimplementowaniu polecenia cmdlet, musi być zarejestrowana przy użyciu programu Windows PowerShell za pomocą przystawki programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7ee10-159">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="7ee10-160">Aby uzyskać więcej informacji na temat rejestrowania poleceń cmdlet, zobacz [sposób zarejestrować poleceń cmdlet, dostawców i hostowania aplikacji](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="7ee10-160">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="7ee10-161">Testowanie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="7ee10-161">Testing the Cmdlet</span></span>

<span data-ttu-id="7ee10-162">Po zarejestrowaniu Twojego polecenia cmdlet przy użyciu programu Windows PowerShell można ją przetestować, uruchamiając go w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="7ee10-162">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="7ee10-163">Teraz przetestuj przykładowe polecenie cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="7ee10-163">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="7ee10-164">Aby uzyskać więcej informacji o korzystaniu z poleceń cmdlet w wierszu polecenia, zobacz [wprowadzenie do programu Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="7ee10-164">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="7ee10-165">Następujący wpis wiersza polecenia używa Stop-Proc, aby zatrzymać proces o nazwie "NOTATNIK", zapewniają pełne powiadomienia i drukowanie informacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="7ee10-165">The following command-line entry uses Stop-Proc to stop the process named "NOTEPAD", provide verbose notifications, and print debug information.</span></span>

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

<span data-ttu-id="7ee10-166">Zostanie wyświetlone następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="7ee10-166">The following output appears.</span></span>

    ```
    VERBOSE: Attempting to stop process " notepad ".
    DEBUG: Acquired name for pid 5584 : "notepad"

    Confirm
    Continue with this operation?
    [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): Y

    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (5584)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    VERBOSE: Stopped process "notepad", pid 5584.
    ```

## <a name="see-also"></a><span data-ttu-id="7ee10-167">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7ee10-167">See Also</span></span>

[<span data-ttu-id="7ee10-168">Tworzenie polecenia Cmdlet, który modyfikuje systemu</span><span class="sxs-lookup"><span data-stu-id="7ee10-168">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="7ee10-169">Jak utworzyć polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7ee10-169">How to Create a Windows PowerShell Cmdlet</span></span>](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="7ee10-170">Formatowanie i rozszerzanie typy obiektów</span><span class="sxs-lookup"><span data-stu-id="7ee10-170">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="7ee10-171">Jak zarejestrować poleceń cmdlet, dostawców i aplikacji hosta</span><span class="sxs-lookup"><span data-stu-id="7ee10-171">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="7ee10-172">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7ee10-172">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
