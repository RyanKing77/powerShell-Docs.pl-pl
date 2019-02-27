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
ms.openlocfilehash: ffc08d2713c4bfc0938b2e07146102af8b5467d2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846802"
---
# <a name="adding-user-messages-to-your-cmdlet"></a><span data-ttu-id="e559a-102">Dodawanie wiadomości użytkownika do polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="e559a-102">Adding User Messages to Your Cmdlet</span></span>

<span data-ttu-id="e559a-103">Polecenia cmdlet można napisać kilka rodzajów wiadomości, które mogą być wyświetlane użytkownikowi w czasie wykonywania programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e559a-103">Cmdlets can write several kinds of messages that can be displayed to the user by the Windows PowerShell runtime.</span></span> <span data-ttu-id="e559a-104">Te komunikaty zawierają następujące typy:</span><span class="sxs-lookup"><span data-stu-id="e559a-104">These messages include the following types:</span></span>

- <span data-ttu-id="e559a-105">Pełne komunikaty, które zawierają ogólne informacje o użytkowniku.</span><span class="sxs-lookup"><span data-stu-id="e559a-105">Verbose messages that contain general user information.</span></span>

- <span data-ttu-id="e559a-106">Debugowanie komunikatów, które zawierają informacje dotyczące rozwiązywania problemów.</span><span class="sxs-lookup"><span data-stu-id="e559a-106">Debug messages that contain troubleshooting information.</span></span>

- <span data-ttu-id="e559a-107">Komunikaty ostrzegawcze, które zawierają powiadomienie, że polecenie cmdlet ma wykonywać operacji, która może mieć nieoczekiwane wyniki.</span><span class="sxs-lookup"><span data-stu-id="e559a-107">Warning messages that contain a notification that the cmdlet is about to perform an operation that can have unexpected results.</span></span>

- <span data-ttu-id="e559a-108">Raport postęp polecenia cmdlet działać, komunikaty, które zawierają informacje o ile zostało zakończone, podczas wykonywania operacji, która zajmuje dużo czasu.</span><span class="sxs-lookup"><span data-stu-id="e559a-108">Progress report messages that contain information about how much work the cmdlet has completed when performing an operation that takes a long time.</span></span>

<span data-ttu-id="e559a-109">Nie ma ograniczeń liczby wiadomości, które może zapisać Twojego polecenia cmdlet lub typ wiadomości, które zapisuje Twojego polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e559a-109">There are no limits to the number of messages that your cmdlet can write or the type of messages that your cmdlet writes.</span></span> <span data-ttu-id="e559a-110">Każdy komunikat jest zapisywany, wprowadzając wywołania określone dane wejściowe przetwarzania metody Twojego polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e559a-110">Each message is written by making a specific call from within the input processing method of your cmdlet.</span></span>

## <a name="the-stopproc-cmdlet"></a><span data-ttu-id="e559a-111">Polecenia cmdlet StopProc</span><span class="sxs-lookup"><span data-stu-id="e559a-111">The StopProc Cmdlet</span></span>

<span data-ttu-id="e559a-112">Tematy w tej sekcji są następujące:</span><span class="sxs-lookup"><span data-stu-id="e559a-112">Topics in this section include the following:</span></span>

- [<span data-ttu-id="e559a-113">Definiowanie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="e559a-113">Defining the Cmdlet</span></span>](#Defining-the-Cmdlet)

- [<span data-ttu-id="e559a-114">Definiowanie parametrów modyfikacji systemu</span><span class="sxs-lookup"><span data-stu-id="e559a-114">Defining Parameters for System Modification</span></span>](#Defining-Parameters-for-System-Modification)

- [<span data-ttu-id="e559a-115">Zastępowanie metody przetwarzania danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="e559a-115">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="e559a-116">Zapisywanie komunikat trybu informacji pełnej</span><span class="sxs-lookup"><span data-stu-id="e559a-116">Writing a Verbose Message</span></span>](#Writing-a-Verbose-Message)

- [<span data-ttu-id="e559a-117">Zapisywanie komunikatów debugowania</span><span class="sxs-lookup"><span data-stu-id="e559a-117">Writing a Debug Message</span></span>](#Writing-a-Debug-Message)

- [<span data-ttu-id="e559a-118">Zapisywanie komunikatu ostrzegawczego</span><span class="sxs-lookup"><span data-stu-id="e559a-118">Writing a Warning Message</span></span>](#Writing-a-Warning-Message)

- [<span data-ttu-id="e559a-119">Zapisywanie komunikatu o postępie</span><span class="sxs-lookup"><span data-stu-id="e559a-119">Writing a Progress Message</span></span>](#Writing-a-Progress-Message)

- [<span data-ttu-id="e559a-120">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="e559a-120">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="e559a-121">Zdefiniuj typy obiektów i formatowanie</span><span class="sxs-lookup"><span data-stu-id="e559a-121">Define Object Types and Formatting</span></span>](#Define-Object-Types-and-Formatting)

- [<span data-ttu-id="e559a-122">Tworzenie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="e559a-122">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="e559a-123">Testowanie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="e559a-123">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a><span data-ttu-id="e559a-124">Definiowanie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="e559a-124">Defining the Cmdlet</span></span>

<span data-ttu-id="e559a-125">Pierwszym krokiem w procesie tworzenia polecenia cmdlet jest zawsze nazewnictwa polecenia cmdlet i deklarowanie klasy .NET, która implementuje polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e559a-125">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="e559a-126">Dowolny rodzaj polecenia cmdlet można napisać powiadomienia użytkownika z metody; przetwarzania danych wejściowych tak ogólnie rzecz biorąc, możesz nazwać tego polecenia cmdlet przy użyciu dowolnej zlecenie, która wskazuje, jakie modyfikacje system wykonuje polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e559a-126">Any sort of cmdlet can write user notifications from its input processing methods; so, in general, you can name this cmdlet using any verb that indicates what system modifications the cmdlet performs.</span></span> <span data-ttu-id="e559a-127">Aby uzyskać więcej informacji na temat polecenia cmdlet zatwierdzonych czasowników, zobacz [nazwy zlecenie poleceń Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="e559a-127">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="e559a-128">Polecenia cmdlet Stop-Proc jest przeznaczony do modyfikacji systemu; w związku z tym [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) deklaracja klasy .NET musi zawierać `SupportsShouldProcess` atrybutu — słowo kluczowe i można ustawić `true`.</span><span class="sxs-lookup"><span data-stu-id="e559a-128">The Stop-Proc cmdlet is designed to modify the system; therefore, the [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration for the .NET class must include the `SupportsShouldProcess` attribute keyword and be set to `true`.</span></span>

<span data-ttu-id="e559a-129">Poniższy kod jest definicji dla tej klasy polecenia cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="e559a-129">The following code is the definition for this Stop-Proc cmdlet class.</span></span> <span data-ttu-id="e559a-130">Aby uzyskać więcej informacji na temat tej definicji, zobacz [Tworzenie polecenia Cmdlet, który modyfikuje System](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="e559a-130">For more information about this definition, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="e559a-131">Definiowanie parametrów modyfikacji systemu</span><span class="sxs-lookup"><span data-stu-id="e559a-131">Defining Parameters for System Modification</span></span>

<span data-ttu-id="e559a-132">Polecenie cmdlet Stop-Proc definiuje trzy parametry: `Name`, `Force`, i `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="e559a-132">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span> <span data-ttu-id="e559a-133">Aby uzyskać więcej informacji na temat definiowania tych parametrów, zobacz [Tworzenie polecenia Cmdlet, który modyfikuje System](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="e559a-133">For more information about defining these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

<span data-ttu-id="e559a-134">Poniżej przedstawiono deklaracji parametrów dla polecenia cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="e559a-134">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="e559a-135">Zastępowanie metody przetwarzania danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="e559a-135">Overriding an Input Processing Method</span></span>

<span data-ttu-id="e559a-136">Twojego polecenia cmdlet jest przesłonięcie metody przetwarzania danych wejściowych, w większości przypadków będzie [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="e559a-136">Your cmdlet must override an input processing method, most often it will be [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="e559a-137">To polecenie cmdlet Stop-Proc zastępuje [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) przetwarzania metody wejściowej.</span><span class="sxs-lookup"><span data-stu-id="e559a-137">This Stop-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) input processing method.</span></span> <span data-ttu-id="e559a-138">W tej implementacji polecenia cmdlet Stop-Proc wywołań do zapisania pełne komunikaty wyjściowe komunikaty debugowania i komunikaty ostrzegawcze.</span><span class="sxs-lookup"><span data-stu-id="e559a-138">In this implementation of the Stop-Proc cmdlet, calls are made to write verbose messages, debug messages, and warning messages.</span></span>

> [!NOTE]
> <span data-ttu-id="e559a-139">Aby uzyskać więcej informacji na temat jak ta metoda wywołuje [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) i [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metod, zobacz [Tworzenie polecenia Cmdlet, który modyfikuje System](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="e559a-139">For more information about how this method calls the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="writing-a-verbose-message"></a><span data-ttu-id="e559a-140">Zapisywanie komunikat trybu informacji pełnej</span><span class="sxs-lookup"><span data-stu-id="e559a-140">Writing a Verbose Message</span></span>

<span data-ttu-id="e559a-141">[System.Management.Automation.Cmdlet.Writeverbose\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) metoda służy do zapisywania ogólne informacje na poziomie użytkownika, która nie ma wpływu na określone warunki błędów.</span><span class="sxs-lookup"><span data-stu-id="e559a-141">The [System.Management.Automation.Cmdlet.Writeverbose\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method is used to write general user-level information that is unrelated to specific error conditions.</span></span> <span data-ttu-id="e559a-142">Administrator systemu może następnie używać tych informacji, aby kontynuować przetwarzania innych poleceń.</span><span class="sxs-lookup"><span data-stu-id="e559a-142">The system administrator can then use that information to continue processing other commands.</span></span> <span data-ttu-id="e559a-143">Ponadto powinien być zlokalizowany wszelkie informacje napisane przy użyciu tej metody, stosownie do potrzeb.</span><span class="sxs-lookup"><span data-stu-id="e559a-143">In addition, any information written using this method should be localized as needed.</span></span>

<span data-ttu-id="e559a-144">Poniższy kod z tego polecenia cmdlet Stop-Proc przedstawia dwa wywołania [System.Management.Automation.Cmdlet.Writeverbose\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) metody z zastępowania metody [System.Management.Automation.Cmdlet.Processrecord\* ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody.</span><span class="sxs-lookup"><span data-stu-id="e559a-144">The following code from this Stop-Proc cmdlet shows two calls to the [System.Management.Automation.Cmdlet.Writeverbose\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method from the override of the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a><span data-ttu-id="e559a-145">Zapisywanie komunikatów debugowania</span><span class="sxs-lookup"><span data-stu-id="e559a-145">Writing a Debug Message</span></span>

<span data-ttu-id="e559a-146">[System.Management.Automation.Cmdlet.Writedebug\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) metoda służy do zapisywania komunikatów debugowania, które mogą służyć do rozwiązywania problemów z polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e559a-146">The [System.Management.Automation.Cmdlet.Writedebug\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method is used to write debug messages that can be used to troubleshoot the operation of the cmdlet.</span></span> <span data-ttu-id="e559a-147">Wykonano wywołanie z metody przetwarzania danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="e559a-147">The call is made from an input processing method.</span></span>

> [!NOTE]
> <span data-ttu-id="e559a-148">Definiuje również środowiska Windows PowerShell `Debug` parametr, który przedstawia zarówno pełne i informacje o debugowaniu.</span><span class="sxs-lookup"><span data-stu-id="e559a-148">Windows PowerShell also defines a `Debug` parameter that presents both verbose and debug information.</span></span> <span data-ttu-id="e559a-149">Jeśli Twoje polecenie cmdlet obsługuje ten parametr, nie trzeba wywoływać [System.Management.Automation.Cmdlet.Writedebug\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) w ten sam kod, który wywołuje [System.Management.Automation.Cmdlet.Writeverbose\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span><span class="sxs-lookup"><span data-stu-id="e559a-149">If your cmdlet supports this parameter, it does not need to call [System.Management.Automation.Cmdlet.Writedebug\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) in the same code that calls [System.Management.Automation.Cmdlet.Writeverbose\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span></span>

<span data-ttu-id="e559a-150">Następujące dwie sekcje kodu z przykładowe polecenie cmdlet Stop-Proc Pokaż wywołania [System.Management.Automation.Cmdlet.Writedebug\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) metody z zastępowania metody [ System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody.</span><span class="sxs-lookup"><span data-stu-id="e559a-150">The following two sections of code from the sample Stop-Proc cmdlet show calls to the [System.Management.Automation.Cmdlet.Writedebug\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method from the override of the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="e559a-151">Ten komunikat debugowania są zapisywane bezpośrednio przed [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="e559a-151">This debug message is written immediately before [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) is called.</span></span>

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

<span data-ttu-id="e559a-152">Ten komunikat debugowania są zapisywane bezpośrednio przed [System.Management.Automation.Cmdlet.Writeobject\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="e559a-152">This debug message is written immediately before [System.Management.Automation.Cmdlet.Writeobject\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) is called.</span></span>

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

<span data-ttu-id="e559a-153">Windows PowerShell automatycznie kieruje dowolnego [System.Management.Automation.Cmdlet.Writedebug\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) wywołania śledzenia infrastruktury i polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e559a-153">Windows PowerShell automatically routes any [System.Management.Automation.Cmdlet.Writedebug\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) calls to the tracing infrastructure and cmdlets.</span></span> <span data-ttu-id="e559a-154">Dzięki temu wywołania metody do śledzenia do hostowania aplikacji, plik lub debugera bez konieczności ponownego wykonać pracę dodatkowe rozwoju w ramach polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e559a-154">This allows the method calls to be traced to the hosting application, a file, or a debugger without your having to do any extra development work within the cmdlet.</span></span> <span data-ttu-id="e559a-155">Następujący wpis wiersza polecenia implementuje operacji śledzenia.</span><span class="sxs-lookup"><span data-stu-id="e559a-155">The following command-line entry implements a tracing operation.</span></span>

<span data-ttu-id="e559a-156">**PS > wyrażenie śledzenia stop-proc — plik proc.log — polecenia stop-proc Notatnik**</span><span class="sxs-lookup"><span data-stu-id="e559a-156">**PS> trace-expression stop-proc -file proc.log -command stop-proc notepad**</span></span>

## <a name="writing-a-warning-message"></a><span data-ttu-id="e559a-157">Zapisywanie komunikatu ostrzegawczego</span><span class="sxs-lookup"><span data-stu-id="e559a-157">Writing a Warning Message</span></span>

<span data-ttu-id="e559a-158">[System.Management.Automation.Cmdlet.Writewarning\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) metoda służy do zapisywania ostrzeżenia, gdy polecenie cmdlet ma wykonać operacji, która może mieć nieoczekiwany wynik, na przykład zastąpienia pliku tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="e559a-158">The [System.Management.Automation.Cmdlet.Writewarning\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method is used to write a warning when the cmdlet is about to perform an operation that might have an unexpected result, for example, overwriting a read-only file.</span></span>

<span data-ttu-id="e559a-159">Poniższy kod z polecenia cmdlet Stop-Proc przykładowy pokazuje wywołanie [System.Management.Automation.Cmdlet.Writewarning\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) metody z zastępowania metody [ System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody.</span><span class="sxs-lookup"><span data-stu-id="e559a-159">The following code from the sample Stop-Proc cmdlet shows the call to the [System.Management.Automation.Cmdlet.Writewarning\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method from the override of the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a><span data-ttu-id="e559a-160">Zapisywanie komunikatu o postępie</span><span class="sxs-lookup"><span data-stu-id="e559a-160">Writing a Progress Message</span></span>

<span data-ttu-id="e559a-161">[System.Management.Automation.Cmdlet.Writeprogress\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) używany do zapisywania wiadomości dotyczące postępu podczas operacji polecenia cmdlet zająć dużo czasu wykonania.</span><span class="sxs-lookup"><span data-stu-id="e559a-161">The [System.Management.Automation.Cmdlet.Writeprogress\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) is used to write progress messages when cmdlet operations take an extended amount of time to complete.</span></span> <span data-ttu-id="e559a-162">Wywołanie [System.Management.Automation.Cmdlet.Writeprogress\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) przekazuje [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) obiekt, który jest wysyłany do hostowania aplikacji w celu renderowania dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e559a-162">A call to [System.Management.Automation.Cmdlet.Writeprogress\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passes a [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) object that is sent to the hosting application for rendering to the user.</span></span>

> [!NOTE]
> <span data-ttu-id="e559a-163">To polecenie cmdlet Stop-Proc nie zawiera wywołanie [System.Management.Automation.Cmdlet.Writeprogress\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) metody.</span><span class="sxs-lookup"><span data-stu-id="e559a-163">This Stop-Proc cmdlet does not include a call to the [System.Management.Automation.Cmdlet.Writeprogress\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span></span>

<span data-ttu-id="e559a-164">Poniższy kod jest przykładem komunikat o postępie napisane przez polecenia cmdlet, które próbuje skopiować element.</span><span class="sxs-lookup"><span data-stu-id="e559a-164">The following code is an example of a progress message written by a cmdlet that is attempting to copy an item.</span></span>

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a><span data-ttu-id="e559a-165">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="e559a-165">Code Sample</span></span>

<span data-ttu-id="e559a-166">Aby uzyskać pełne C# przykładowego kodu, zobacz [przykładowe StopProcessSample02](./stopprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="e559a-166">For the complete C# sample code, see [StopProcessSample02 Sample](./stopprocesssample02-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="e559a-167">Zdefiniuj typy obiektów i formatowanie</span><span class="sxs-lookup"><span data-stu-id="e559a-167">Define Object Types and Formatting</span></span>

<span data-ttu-id="e559a-168">Program Windows PowerShell przekazuje informacje między poleceniami cmdlet, używając obiektów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="e559a-168">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="e559a-169">W związku z tym polecenie cmdlet może się okazać zdefiniowanie swój własny typ, lub polecenie cmdlet może być konieczne rozszerzenie istniejącego typu dostarczane przez inne polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e559a-169">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="e559a-170">Aby uzyskać więcej informacji na temat definiowania nowych typów lub rozszerzanie istniejących typów, zobacz [rozszerzanie typów obiektów i formatowanie](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="e559a-170">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="e559a-171">Tworzenie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="e559a-171">Building the Cmdlet</span></span>

<span data-ttu-id="e559a-172">Po zaimplementowaniu polecenia cmdlet, musi być zarejestrowana przy użyciu programu Windows PowerShell za pomocą przystawki programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e559a-172">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="e559a-173">Aby uzyskać więcej informacji na temat rejestrowania poleceń cmdlet, zobacz [sposób zarejestrować poleceń cmdlet, dostawców i hostowania aplikacji](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="e559a-173">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="e559a-174">Testowanie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="e559a-174">Testing the Cmdlet</span></span>

<span data-ttu-id="e559a-175">Po zarejestrowaniu Twojego polecenia cmdlet przy użyciu programu Windows PowerShell można ją przetestować, uruchamiając go w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="e559a-175">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="e559a-176">Teraz przetestuj przykładowe polecenie cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="e559a-176">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="e559a-177">Aby uzyskać więcej informacji o korzystaniu z poleceń cmdlet w wierszu polecenia, zobacz [wprowadzenie do programu Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="e559a-177">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="e559a-178">Następujący wpis wiersza polecenia używa Stop-Proc, aby zatrzymać proces o nazwie "NOTATNIK", zapewniają pełne powiadomienia i drukowanie informacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="e559a-178">The following command-line entry uses Stop-Proc to stop the process named "NOTEPAD", provide verbose notifications, and print debug information.</span></span>

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

<span data-ttu-id="e559a-179">Zostanie wyświetlone następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="e559a-179">The following output appears.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e559a-180">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e559a-180">See Also</span></span>

[<span data-ttu-id="e559a-181">Tworzenie polecenia Cmdlet, który modyfikuje systemu</span><span class="sxs-lookup"><span data-stu-id="e559a-181">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="e559a-182">Jak utworzyć polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e559a-182">How to Create a Windows PowerShell Cmdlet</span></span>](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="e559a-183">Formatowanie i rozszerzanie typy obiektów</span><span class="sxs-lookup"><span data-stu-id="e559a-183">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="e559a-184">Jak zarejestrować poleceń cmdlet, dostawców i aplikacji hosta</span><span class="sxs-lookup"><span data-stu-id="e559a-184">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="e559a-185">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e559a-185">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
