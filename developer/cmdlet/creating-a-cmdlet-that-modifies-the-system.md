---
title: Tworzenie polecenia Cmdlet, który modyfikuje systemu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- should process [PowerShell Programmer's Guide]
- should continue [PowerShell Programmer's Guide]
- user feedback [PowerShell Programmer's Guide]
- confirm impact [PowerShell Programmer's Guide]
ms.assetid: 59be4120-1700-4d92-a308-ef4a32ccf11a
caps.latest.revision: 8
ms.openlocfilehash: a4fa9ce52855928679a2425f24f2e49a68030c63
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854915"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a><span data-ttu-id="8119f-102">Tworzenie polecenia cmdlet, które modyfikuje system</span><span class="sxs-lookup"><span data-stu-id="8119f-102">Creating a Cmdlet that Modifies the System</span></span>

<span data-ttu-id="8119f-103">Czasami polecenia cmdlet, należy zmodyfikować stan działania systemu, a nie tylko stan środowiska uruchomieniowego programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8119f-103">Sometimes a cmdlet must modify the running state of the system, not just the state of the Windows PowerShell runtime.</span></span> <span data-ttu-id="8119f-104">W takich przypadkach polecenia cmdlet powinien pozwalać użytkownikowi szansę upewnić się, czy należy wprowadzić zmiany.</span><span class="sxs-lookup"><span data-stu-id="8119f-104">In these cases, the cmdlet should allow the user a chance to confirm whether or not to make the change.</span></span>

<span data-ttu-id="8119f-105">Umożliwiających potwierdzenie polecenia cmdlet, należy wykonać dwie czynności.</span><span class="sxs-lookup"><span data-stu-id="8119f-105">To support confirmation a cmdlet must do two things.</span></span>

- <span data-ttu-id="8119f-106">Zadeklaruj, że polecenie cmdlet obsługuje potwierdzenia po określeniu [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) atrybutu, ustawiając dla słowa kluczowego SupportsShouldProcess `true`.</span><span class="sxs-lookup"><span data-stu-id="8119f-106">Declare that the cmdlet supports confirmation when you specify the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute by setting the SupportsShouldProcess keyword to `true`.</span></span>

- <span data-ttu-id="8119f-107">Wywołaj [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) podczas wykonywania polecenia cmdlet (jak pokazano w poniższym przykładzie).</span><span class="sxs-lookup"><span data-stu-id="8119f-107">Call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) during the execution of the cmdlet (as shown in the following example).</span></span>

<span data-ttu-id="8119f-108">Dzięki obsłudze potwierdzenie, udostępnia polecenia cmdlet `Confirm` i `WhatIf` parametry, które są dostarczane przez środowisko Windows PowerShell, a także spełnia wskazówki dotyczące programowania dla poleceń cmdlet (Aby uzyskać więcej informacji na temat wytycznych programowania polecenia cmdlet, zobacz [ Wskazówki dotyczące programowania polecenia cmdlet](./cmdlet-development-guidelines.md).).</span><span class="sxs-lookup"><span data-stu-id="8119f-108">By supporting confirmation, a cmdlet exposes the `Confirm` and `WhatIf` parameters that are provided by Windows PowerShell, and also meets the development guidelines for cmdlets (For more information about cmdlet development guidelines, see [Cmdlet Development Guidelines](./cmdlet-development-guidelines.md).).</span></span>

## <a name="changing-the-system"></a><span data-ttu-id="8119f-109">Zmiana systemu</span><span class="sxs-lookup"><span data-stu-id="8119f-109">Changing the System</span></span>

<span data-ttu-id="8119f-110">Czynność "Zmiana systemu" odnosi się do dowolnego polecenia cmdlet, które potencjalnie zmieni się stan systemu poza programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8119f-110">The act of "changing the system" refers to any cmdlet that potentially changes the state of the system outside Windows PowerShell.</span></span> <span data-ttu-id="8119f-111">Na przykład zatrzymywanie procesu, włączenie lub wyłączenie konta użytkownika lub dodawanie wierszy do tabeli bazy danych są wszystkie zmiany do systemu, które powinny zostać potwierdzone.</span><span class="sxs-lookup"><span data-stu-id="8119f-111">For example, stopping a process, enabling or disabling a user account, or adding a row to a database table are all changes to the system that should be confirmed.</span></span> <span data-ttu-id="8119f-112">Z kolei odczytywanie danych lub nawiązywać połączenia z przejściowych operacji nie zmieniaj system i zazwyczaj nie wymaga potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="8119f-112">In contrast, operations that read data or establish transient connections do not change the system and generally do not require confirmation.</span></span> <span data-ttu-id="8119f-113">Potwierdzenie nie jest również wymagany dla akcji, których wynikiem jest ograniczona do wewnątrz środowiska uruchomieniowego programu Windows PowerShell, takie jak `set-variable`.</span><span class="sxs-lookup"><span data-stu-id="8119f-113">Confirmation is also not needed for actions whose effect is limited to inside the Windows PowerShell runtime, such as `set-variable`.</span></span> <span data-ttu-id="8119f-114">Polecenia cmdlet, który może być lub może nie mieć trwałe zmiany powinny deklarować `SupportsShouldProcess` i wywołać [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) tylko wtedy, gdy są one przeprowadzasz trwałych zmian.</span><span class="sxs-lookup"><span data-stu-id="8119f-114">Cmdlets that might or might not make a persistent change should declare `SupportsShouldProcess` and call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) only if they are about to make a persistent change.</span></span>

> [!NOTE]
> <span data-ttu-id="8119f-115">Potwierdzenie ShouldProcess dotyczy tylko polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8119f-115">ShouldProcess confirmation applies only to cmdlets.</span></span> <span data-ttu-id="8119f-116">Jeśli polecenie albo skrypt modyfikuje stan działania systemu poprzez bezpośrednie wywoływanie właściwości lub metody .NET lub przez wywołującego aplikacje spoza środowiska Windows PowerShell, ta forma potwierdzenia nie będą dostępne.</span><span class="sxs-lookup"><span data-stu-id="8119f-116">If a command or script modifies the running state of a system by directly calling .NET methods or properties, or by calling applications outside of Windows PowerShell, this form of confirmation will not be available.</span></span>

## <a name="the-stopproc-cmdlet"></a><span data-ttu-id="8119f-117">Polecenia cmdlet StopProc</span><span class="sxs-lookup"><span data-stu-id="8119f-117">The StopProc Cmdlet</span></span>

<span data-ttu-id="8119f-118">W tym temacie opisano polecenia cmdlet Stop-Proc, który podejmuje próby zatrzymania procesów, które są pobierane za pomocą polecenia cmdlet Get-Proc (opisanego w [tworzenia Your pierwsze polecenie Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="8119f-118">This topic describes a Stop-Proc cmdlet that attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="8119f-119">Definiowanie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="8119f-119">Defining the Cmdlet</span></span>

<span data-ttu-id="8119f-120">Pierwszym krokiem w procesie tworzenia polecenia cmdlet jest zawsze nazewnictwa polecenia cmdlet i deklarowanie klasy .NET, która implementuje polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8119f-120">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="8119f-121">Ponieważ piszesz polecenia cmdlet, aby zmienić system powinien zostać nazwany odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="8119f-121">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="8119f-122">To polecenie cmdlet zatrzymuje procesów systemowych, więc nazwę zlecenie wybrane w tym miejscu jest "Zatrzymaj" zdefiniowany przez [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) klasy z rzeczownikiem "Proc", aby wskazać, że polecenia cmdlet zatrzymuje procesy.</span><span class="sxs-lookup"><span data-stu-id="8119f-122">This cmdlet stops system processes, so the verb name chosen here is "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate that the cmdlet stops processes.</span></span> <span data-ttu-id="8119f-123">Aby uzyskać więcej informacji na temat polecenia cmdlet zatwierdzonych czasowników, zobacz [nazwy zlecenie poleceń Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="8119f-123">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="8119f-124">Poniżej znajduje się w definicji klasy dla tego polecenia cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="8119f-124">The following is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

<span data-ttu-id="8119f-125">Należy pamiętać, w [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) deklaracji, `SupportsShouldProcess` — słowo kluczowe atrybutu jest równa `true` umożliwiające polecenia cmdlet do wykonywania wywołań do [ System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) i [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span><span class="sxs-lookup"><span data-stu-id="8119f-125">Be aware that in the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration, the `SupportsShouldProcess` attribute keyword is set to `true` to enable the cmdlet to make calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="8119f-126">Bez tego zestawu — słowo kluczowe `Confirm` i `WhatIf` parametry nie będą dostępne dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8119f-126">Without this keyword set, the `Confirm` and `WhatIf` parameters will not be available to the user.</span></span>

### <a name="extremely-destructive-actions"></a><span data-ttu-id="8119f-127">Bardzo destrukcyjne działania</span><span class="sxs-lookup"><span data-stu-id="8119f-127">Extremely Destructive Actions</span></span>

<span data-ttu-id="8119f-128">Niektóre operacje są bardzo destrukcyjne, takie jak ponowne formatowanie partycji active dysku twardego.</span><span class="sxs-lookup"><span data-stu-id="8119f-128">Some operations are extremely destructive, such as reformatting an active hard disk partition.</span></span> <span data-ttu-id="8119f-129">W takich przypadkach należy ustawić polecenia cmdlet `ConfirmImpact`  =  `ConfirmImpact.High` podczas deklarowania [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) atrybutu.</span><span class="sxs-lookup"><span data-stu-id="8119f-129">In these cases, the cmdlet should set `ConfirmImpact` = `ConfirmImpact.High` when declaring the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute.</span></span> <span data-ttu-id="8119f-130">To ustawienie wymusza polecenia cmdlet na potwierdzenie żądania przez użytkownika, nawet wtedy, gdy użytkownik nie określił `Confirm` parametru.</span><span class="sxs-lookup"><span data-stu-id="8119f-130">This setting forces the cmdlet to request user confirmation even when the user has not specified the `Confirm` parameter.</span></span> <span data-ttu-id="8119f-131">Jednak deweloperów polecenia cmdlet należy unikać nadużywanie `ConfirmImpact` dla operacji, które są po prostu potencjalnie szkodliwych, np. usunięcie konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8119f-131">However, cmdlet developers should avoid overusing `ConfirmImpact` for operations that are just potentially destructive, such as deleting a user account.</span></span> <span data-ttu-id="8119f-132">Należy pamiętać, że jeśli `ConfirmImpact` ustawiono [System.Management.Automation.Confirmimpact.High](/dotnet/api/System.Management.Automation.ConfirmImpact.High).</span><span class="sxs-lookup"><span data-stu-id="8119f-132">Remember that if `ConfirmImpact` is set to [System.Management.Automation.Confirmimpact.High](/dotnet/api/System.Management.Automation.ConfirmImpact.High).</span></span>

<span data-ttu-id="8119f-133">Podobnie niektóre operacje są najprawdopodobniej nie występują destrukcyjne, mimo że teoretycznie mogą modyfikować stan działania systemu poza programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8119f-133">Similarly, some operations are unlikely to be destructive, although they do in theory modify the running state of a system outside Windows PowerShell.</span></span> <span data-ttu-id="8119f-134">Takie polecenia cmdlet można ustawić `ConfirmImpact` do [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span><span class="sxs-lookup"><span data-stu-id="8119f-134">Such cmdlets can set `ConfirmImpact` to [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span></span> <span data-ttu-id="8119f-135">Spowoduje to obejście żądania potwierdzenia, gdzie użytkownik został wyświetlony monit o potwierdzenie operacji tylko średni wpływ i o dużym znaczeniu.</span><span class="sxs-lookup"><span data-stu-id="8119f-135">This will bypass confirmation requests where the user has asked to confirm only medium-impact and high-impact operations.</span></span>

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="8119f-136">Definiowanie parametrów modyfikacji systemu</span><span class="sxs-lookup"><span data-stu-id="8119f-136">Defining Parameters for System Modification</span></span>

<span data-ttu-id="8119f-137">W tej sekcji opisano sposób definiowania parametry polecenia cmdlet, łącznie z tymi, które są niezbędne do modyfikacji systemu pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="8119f-137">This section describes how to define the cmdlet parameters, including those that are needed to support system modification.</span></span> <span data-ttu-id="8119f-138">Zobacz [dodając parametry te dane wejściowe wiersza polecenia procesu](./adding-parameters-that-process-command-line-input.md) Jeśli potrzebujesz ogólnych informacji na temat definiowania parametrów.</span><span class="sxs-lookup"><span data-stu-id="8119f-138">See [Adding Parameters that Process CommandLine Input](./adding-parameters-that-process-command-line-input.md) if you need general information about defining parameters.</span></span>

<span data-ttu-id="8119f-139">Polecenie cmdlet Stop-Proc definiuje trzy parametry: `Name`, `Force`, i `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="8119f-139">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span>

<span data-ttu-id="8119f-140">`Name` Parametr odnosi się do `Name` własności obiektu wejściowego procesu.</span><span class="sxs-lookup"><span data-stu-id="8119f-140">The `Name` parameter corresponds to the `Name` property of the process input object.</span></span> <span data-ttu-id="8119f-141">Należy pamiętać, że `Name` parametru, w tym przykładzie jest obowiązkowe, ponieważ polecenie cmdlet zakończy się niepowodzeniem, jeśli nie ma proces o określonej nazwie, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="8119f-141">Be aware that the `Name` parameter in this sample is mandatory, as the cmdlet will fail if it does not have a named process to stop.</span></span>

<span data-ttu-id="8119f-142">`Force` Parametr umożliwia użytkownikowi przesłanianie wywołania [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span><span class="sxs-lookup"><span data-stu-id="8119f-142">The `Force` parameter allows the user to override calls to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="8119f-143">W rzeczywistości każdego polecenia cmdlet wywołująca [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) powinny mieć `Force` parametru, aby podczas `Force` jest określony, polecenie cmdlet pomija wywołanie [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) i kontynuuje operację.</span><span class="sxs-lookup"><span data-stu-id="8119f-143">In fact, any cmdlet that calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) should have a `Force` parameter so that when `Force` is specified, the cmdlet skips the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) and proceeds with the operation.</span></span> <span data-ttu-id="8119f-144">Należy pamiętać, że nie dotyczy to wywołania [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span><span class="sxs-lookup"><span data-stu-id="8119f-144">Be aware that this does not affect calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span></span>

<span data-ttu-id="8119f-145">`PassThru` Parametr umożliwia użytkownikowi wskazują, czy polecenie cmdlet przekazuje obiekt danych wyjściowych, za pośrednictwem potoku, w tym przypadku po zatrzymaniu procesu.</span><span class="sxs-lookup"><span data-stu-id="8119f-145">The `PassThru` parameter allows the user to indicate whether the cmdlet passes an output object through the pipeline, in this case, after a process is stopped.</span></span> <span data-ttu-id="8119f-146">Należy pamiętać, że ten parametr jest powiązany z polecenia cmdlet sam zamiast do właściwości obiektu danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="8119f-146">Be aware that this parameter is tied to the cmdlet itself instead of to a property of the input object.</span></span>

<span data-ttu-id="8119f-147">Poniżej przedstawiono deklaracji parametrów dla polecenia cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="8119f-147">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="8119f-148">Zastępowanie metody przetwarzania danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="8119f-148">Overriding an Input Processing Method</span></span>

<span data-ttu-id="8119f-149">Polecenie cmdlet jest przesłonięcie metody przetwarzania danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="8119f-149">The cmdlet must override an input processing method.</span></span> <span data-ttu-id="8119f-150">Poniższy kod ilustruje [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) zastąpienie używane w poleceniu cmdlet Stop-Proc próbki.</span><span class="sxs-lookup"><span data-stu-id="8119f-150">The following code illustrates the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override used in the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="8119f-151">Dla każdego żądanego nazwę procesu, ta metoda zapewnia, że proces nie jest specjalny proces, próbuje zatrzymać proces i wysyła dane wyjściowe obiektu, jeśli `PassThru` określono parametr.</span><span class="sxs-lookup"><span data-stu-id="8119f-151">For each requested process name, this method ensures that the process is not a special process, tries to stop the process, and then sends an output object if the `PassThru` parameter is specified.</span></span>

```csharp
protected override void ProcessRecord()
{
  foreach (string name in processNames)
  {
    // For every process name passed to the cmdlet, get the associated
    // process(es). For failures, write a non-terminating error
    Process[] processes;

    try
    {
      processes = Process.GetProcessesByName(name);
    }
    catch (InvalidOperationException ioe)
    {
      WriteError(new ErrorRecord(ioe,"Unable to access the target process by name",
                 ErrorCategory.InvalidOperation, name));
      continue;
    }

    // Try to stop the process(es) that have been retrieved for a name
    foreach (Process process in processes)
    {
      string processName;

      try
      {
        processName = process.ProcessName;
      }

      catch (Win32Exception e)
        {
          WriteError(new ErrorRecord(e, "ProcessNameNotFound",
                     ErrorCategory.ReadError, process));
          continue;
        }

        // Call Should Process to confirm the operation first.
        // This is always false if WhatIf is set.
        if (!ShouldProcess(string.Format("{0} ({1})", processName,
                           process.Id)))
        {
          continue;
        }
        // Call ShouldContinue to make sure the user really does want
        // to stop a critical process that could possibly stop the computer.
        bool criticalProcess =
             criticalProcessNames.Contains(processName.ToLower());

        if (criticalProcess &&!force)
        {
          string message = String.Format
                ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                processName);

          // It is possible that ProcessRecord is called multiple times
          // when the Name parameter receives objects as input from the
          // pipeline. So to retain YesToAll and NoToAll input that the
          // user may enter across multiple calls to ProcessRecord, this
          // information is stored as private members of the cmdlet.
          if (!ShouldContinue(message, "Warning!",
                              ref yesToAll,
                              ref noToAll))
          {
            continue;
          }
        } // if (criticalProcess...
        // Stop the named process.
        try
        {
          process.Kill();
        }
        catch (Exception e)
        {
          if ((e is Win32Exception) || (e is SystemException) ||
              (e is InvalidOperationException))
          {
            // This process could not be stopped so write
            // a non-terminating error.
            string message = String.Format("{0} {1} {2}",
                             "Could not stop process \"", processName,
                             "\".");
            WriteError(new ErrorRecord(e, message,
                       ErrorCategory.CloseError, process));
                       continue;
          } // if ((e is...
          else throw;
        } // catch

        // If the PassThru parameter argument is
        // True, pass the terminated process on.
        if (passThru)
        {
          WriteObject(process);
        }
    } // foreach (Process...
  } // foreach (string...
} // ProcessRecord
```

## <a name="calling-the-shouldprocess-method"></a><span data-ttu-id="8119f-152">Wywołanie metody ShouldProcess</span><span class="sxs-lookup"><span data-stu-id="8119f-152">Calling the ShouldProcess Method</span></span>

<span data-ttu-id="8119f-153">Dane wejściowe przetwarzania metody Twojego polecenia cmdlet powinny wywoływać [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metodę, aby potwierdzić wykonanie operacji przed dokonaniem zmiany (na przykład usuwania plików) do stanu uruchomienia systemu.</span><span class="sxs-lookup"><span data-stu-id="8119f-153">The input processing method of your cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to confirm execution of an operation before a change (for example, deleting files) is made to the running state of the system.</span></span> <span data-ttu-id="8119f-154">Umożliwia podanie poprawnego zachowania w zakresie "WhatIf" i "Potwierdź" w powłoce środowiska uruchomieniowego programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8119f-154">This allows the Windows PowerShell runtime to supply the correct "WhatIf" and "Confirm" behavior within the shell.</span></span>

> [!NOTE]
> <span data-ttu-id="8119f-155">Jeśli polecenia cmdlet stwierdza, że obsługuje ona powinien przetworzyć i nie dokona [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) wywołać, użytkownik może modyfikować system nieoczekiwanie.</span><span class="sxs-lookup"><span data-stu-id="8119f-155">If a cmdlet states that it supports should process and fails to make the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call, the user might modify the system unexpectedly.</span></span>

<span data-ttu-id="8119f-156">Wywołanie [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) wysyła nazwę zasobu był zmieniany na użytkownika, ze środowiskiem uruchomieniowym programu Windows PowerShell, biorąc pod uwagę wszystkie ustawienia wiersza polecenia lub zmienne preferencji określenie, co powinno być wyświetlane użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="8119f-156">The call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command-line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="8119f-157">W poniższym przykładzie pokazano wywołanie metody [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) z zastępowania metody [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody w przykładzie Polecenie cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="8119f-157">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a><span data-ttu-id="8119f-158">Wywołanie metody ShouldContinue</span><span class="sxs-lookup"><span data-stu-id="8119f-158">Calling the ShouldContinue Method</span></span>

<span data-ttu-id="8119f-159">Wywołanie [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metoda wysyła dodatkowej wiadomości do użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8119f-159">The call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method sends a secondary message to the user.</span></span> <span data-ttu-id="8119f-160">To wywołanie jest przeprowadzany po wywołaniu [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) zwraca `true` i, jeśli `Force` parametr nie został ustawiony na `true`.</span><span class="sxs-lookup"><span data-stu-id="8119f-160">This call is made after the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) returns `true` and if the `Force` parameter was not set to `true`.</span></span> <span data-ttu-id="8119f-161">Użytkownik może następnie udostępniać opinii powiedzieć, czy operacja powinna być kontynuowana.</span><span class="sxs-lookup"><span data-stu-id="8119f-161">The user can then provide feedback to say whether the operation should be continued.</span></span> <span data-ttu-id="8119f-162">Wywołania polecenia cmdlet [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) jako dodatkowe sprawdzenie modyfikacje potencjalnie niebezpiecznych systemu lub gdy chcesz zapewnić tak na wszystkie, a nie na wszystkie opcje dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8119f-162">Your cmdlet calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) as an additional check for potentially dangerous system modifications or when you want to provide yes-to-all and no-to-all options to the user.</span></span>

<span data-ttu-id="8119f-163">W poniższym przykładzie pokazano wywołanie metody [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) z zastępowania metody [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody w przykładzie Polecenie cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="8119f-163">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (criticalProcess &&!force)
{
  string message = String.Format
        ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
        processName);

  // It is possible that ProcessRecord is called multiple times
  // when the Name parameter receives objects as input from the
  // pipeline. So to retain YesToAll and NoToAll input that the
  // user may enter across multiple calls to ProcessRecord, this
  // information is stored as private members of the cmdlet.
  if (!ShouldContinue(message, "Warning!",
                      ref yesToAll,
                      ref noToAll))
  {
    continue;
  }
} // if (criticalProcess...
```

## <a name="stopping-input-processing"></a><span data-ttu-id="8119f-164">Zatrzymywanie przetwarzania danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="8119f-164">Stopping Input Processing</span></span>

<span data-ttu-id="8119f-165">Dane wejściowe przetwarzania metody polecenia cmdlet, które sprawia, że modyfikacje systemu należy podać sposób zatrzymania przetwarzania danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="8119f-165">The input processing method of a cmdlet that makes system modifications must provide a way of stopping the processing of input.</span></span> <span data-ttu-id="8119f-166">W przypadku tego polecenia cmdlet Stop-Proc, Wykonano wywołanie z [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) metody.</span><span class="sxs-lookup"><span data-stu-id="8119f-166">In the case of this Stop-Proc cmdlet, a call is made from the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to the [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) method.</span></span> <span data-ttu-id="8119f-167">Ponieważ `PassThru` parametr ma wartość `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) wywołuje również [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) do wysłania obiektu procesu do potoku.</span><span class="sxs-lookup"><span data-stu-id="8119f-167">Because the `PassThru` parameter is set to `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) also calls [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) to send the process object to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="8119f-168">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="8119f-168">Code Sample</span></span>

<span data-ttu-id="8119f-169">Aby uzyskać pełne C# przykładowego kodu, zobacz [przykładowe StopProcessSample01](./stopprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="8119f-169">For the complete C# sample code, see [StopProcessSample01 Sample](./stopprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="8119f-170">Definiowanie typów obiektów i formatowanie</span><span class="sxs-lookup"><span data-stu-id="8119f-170">Defining Object Types and Formatting</span></span>

<span data-ttu-id="8119f-171">Program Windows PowerShell przekazuje informacje między poleceniami cmdlet, używając obiektów platformy .net.</span><span class="sxs-lookup"><span data-stu-id="8119f-171">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="8119f-172">W związku z tym polecenie cmdlet może być konieczne zdefiniowanie swój własny typ, lub polecenie cmdlet może być konieczne rozszerzyć istniejący typ dostarczane przez inne polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8119f-172">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="8119f-173">Aby uzyskać więcej informacji na temat definiowania nowych typów lub rozszerzanie istniejących typów, zobacz [rozszerzanie typów obiektów i formatowanie](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="8119f-173">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="8119f-174">Tworzenie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="8119f-174">Building the Cmdlet</span></span>

<span data-ttu-id="8119f-175">Po zaimplementowaniu polecenia cmdlet, musi być zarejestrowana przy użyciu programu Windows PowerShell za pomocą przystawki programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8119f-175">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="8119f-176">Aby uzyskać więcej informacji na temat rejestrowania poleceń cmdlet, zobacz [sposób zarejestrować poleceń cmdlet, dostawców i hostowania aplikacji](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="8119f-176">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="8119f-177">Testowanie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="8119f-177">Testing the Cmdlet</span></span>

<span data-ttu-id="8119f-178">Po zarejestrowaniu Twojego polecenia cmdlet przy użyciu programu Windows PowerShell można ją przetestować, uruchamiając go w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="8119f-178">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="8119f-179">Poniżej przedstawiono kilka testów, które testowe polecenie cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="8119f-179">Here are several tests that test the Stop-Proc cmdlet.</span></span> <span data-ttu-id="8119f-180">Aby uzyskać więcej informacji o korzystaniu z poleceń cmdlet w wierszu polecenia, zobacz [wprowadzenie do programu Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="8119f-180">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="8119f-181">Uruchom program Windows PowerShell i użyj polecenia cmdlet Stop-Proc, aby zatrzymać przetwarzanie, jak pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="8119f-181">Start Windows PowerShell and use the Stop-Proc cmdlet to stop processing as shown below.</span></span> <span data-ttu-id="8119f-182">Ponieważ polecenie cmdlet Określa `Name` parametr jako wymagane, zapytania polecenia cmdlet dla parametru.</span><span class="sxs-lookup"><span data-stu-id="8119f-182">Because the cmdlet specifies the `Name` parameter as mandatory, the cmdlet queries for the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="8119f-183">Zostanie wyświetlone następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="8119f-183">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- <span data-ttu-id="8119f-184">Teraz użyjemy polecenia cmdlet można zatrzymać procesu o nazwie "NOTATNIK".</span><span class="sxs-lookup"><span data-stu-id="8119f-184">Now let's use the cmdlet to stop the process named "NOTEPAD".</span></span> <span data-ttu-id="8119f-185">Polecenie cmdlet wyświetli monit o potwierdzenie akcji.</span><span class="sxs-lookup"><span data-stu-id="8119f-185">The cmdlet asks you to confirm the action.</span></span>

    ```powershell
    PS> stop-proc -Name notepad
    ```

<span data-ttu-id="8119f-186">Zostanie wyświetlone następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="8119f-186">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="8119f-187">Użyj Stop-Proc, jak pokazano, aby zatrzymać krytyczny proces o nazwie "Logowania do systemu Windows".</span><span class="sxs-lookup"><span data-stu-id="8119f-187">Use Stop-Proc as shown to stop the critical process named "WINLOGON".</span></span> <span data-ttu-id="8119f-188">Zostanie wyświetlony monit i ostrzeżenie o wykonanie tej akcji, ponieważ spowoduje to ponowne uruchomienie systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="8119f-188">You are prompted and warned about performing this action because it will cause the operating system to reboot.</span></span>

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

<span data-ttu-id="8119f-189">Zostanie wyświetlone następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="8119f-189">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- <span data-ttu-id="8119f-190">Teraz Wypróbujmy można zatrzymać procesu WINLOGON bez otrzymania ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="8119f-190">Let's now try to stop the WINLOGON process without receiving a warning.</span></span> <span data-ttu-id="8119f-191">Należy pamiętać, że ten wpis polecenie używa `Force` parametr do zastąpienia ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="8119f-191">Be aware that this command entry uses the `Force` parameter to override the warning.</span></span>

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

<span data-ttu-id="8119f-192">Zostanie wyświetlone następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="8119f-192">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="8119f-193">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8119f-193">See Also</span></span>

[<span data-ttu-id="8119f-194">Dodając parametry, które przetwarzają dane wejściowe wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="8119f-194">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="8119f-195">Formatowanie i rozszerzanie typy obiektów</span><span class="sxs-lookup"><span data-stu-id="8119f-195">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="8119f-196">Jak zarejestrować poleceń cmdlet, dostawców i aplikacji hosta</span><span class="sxs-lookup"><span data-stu-id="8119f-196">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="8119f-197">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8119f-197">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="8119f-198">Przykłady polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="8119f-198">Cmdlet Samples</span></span>](./cmdlet-samples.md)