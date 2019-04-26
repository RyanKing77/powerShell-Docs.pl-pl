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
ms.openlocfilehash: bbe9f0213754d1cc47e0fd9a7a898bde916c0636
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068443"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a>Tworzenie polecenia cmdlet, które modyfikuje system

Czasami polecenia cmdlet, należy zmodyfikować stan działania systemu, a nie tylko stan środowiska uruchomieniowego programu Windows PowerShell. W takich przypadkach polecenia cmdlet powinien pozwalać użytkownikowi szansę upewnić się, czy należy wprowadzić zmiany.

Umożliwiających potwierdzenie polecenia cmdlet, należy wykonać dwie czynności.

- Zadeklaruj, że polecenie cmdlet obsługuje potwierdzenia po określeniu [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) atrybutu, ustawiając dla słowa kluczowego SupportsShouldProcess `true`.

- Wywołaj [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) podczas wykonywania polecenia cmdlet (jak pokazano w poniższym przykładzie).

Dzięki obsłudze potwierdzenie, udostępnia polecenia cmdlet `Confirm` i `WhatIf` parametry, które są dostarczane przez środowisko Windows PowerShell, a także spełnia wskazówki dotyczące programowania dla poleceń cmdlet (Aby uzyskać więcej informacji na temat wytycznych programowania polecenia cmdlet, zobacz [ Wskazówki dotyczące programowania polecenia cmdlet](./cmdlet-development-guidelines.md).).

## <a name="changing-the-system"></a>Zmiana systemu

Czynność "Zmiana systemu" odnosi się do dowolnego polecenia cmdlet, które potencjalnie zmieni się stan systemu poza programu Windows PowerShell. Na przykład zatrzymywanie procesu, włączenie lub wyłączenie konta użytkownika lub dodawanie wierszy do tabeli bazy danych są wszystkie zmiany do systemu, które powinny zostać potwierdzone. Z kolei odczytywanie danych lub nawiązywać połączenia z przejściowych operacji nie zmieniaj system i zazwyczaj nie wymaga potwierdzenia. Potwierdzenie nie jest również wymagany dla akcji, których wynikiem jest ograniczona do wewnątrz środowiska uruchomieniowego programu Windows PowerShell, takie jak `set-variable`. Polecenia cmdlet, który może być lub może nie mieć trwałe zmiany powinny deklarować `SupportsShouldProcess` i wywołać [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) tylko wtedy, gdy są one przeprowadzasz trwałych zmian.

> [!NOTE]
> Potwierdzenie ShouldProcess dotyczy tylko polecenia cmdlet. Jeśli polecenie albo skrypt modyfikuje stan działania systemu poprzez bezpośrednie wywoływanie właściwości lub metody .NET lub przez wywołującego aplikacje spoza środowiska Windows PowerShell, ta forma potwierdzenia nie będą dostępne.

## <a name="the-stopproc-cmdlet"></a>Polecenia cmdlet StopProc

W tym temacie opisano polecenia cmdlet Stop-Proc, który podejmuje próby zatrzymania procesów, które są pobierane za pomocą polecenia cmdlet Get-Proc (opisanego w [tworzenia Your pierwsze polecenie Cmdlet](./creating-a-cmdlet-without-parameters.md)).

Tematy w tej sekcji są następujące:

- [Definiowanie polecenia cmdlet](#Defining-the-Cmdlet)

- [Definiowanie parametrów modyfikacji systemu](#Defining-Parameters-for-System-Modification)

- [Zastępowanie metody przetwarzania danych wejściowych](#Overriding-an-Input-Processing-Method)

- [Wywołanie metody ShouldProcess](#Calling-the-ShouldProcess-Method)

- [Wywołanie metody ShouldContinue](#Calling-the-ShouldContinue-Method)

- [Zatrzymywanie przetwarzania danych wejściowych](#Stopping-Input-Processing)

- [Przykładowy kod](#Code-Sample)

- [Definiowanie typów obiektów i formatowanie](#Defining-Object-Types-and-Formatting)

- [Tworzenie polecenia cmdlet](#Building-the-Cmdlet)

- [Testowanie polecenia cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>Definiowanie polecenia cmdlet

Pierwszym krokiem w procesie tworzenia polecenia cmdlet jest zawsze nazewnictwa polecenia cmdlet i deklarowanie klasy .NET, która implementuje polecenia cmdlet. Ponieważ piszesz polecenia cmdlet, aby zmienić system powinien zostać nazwany odpowiednio. To polecenie cmdlet zatrzymuje procesów systemowych, więc nazwę zlecenie wybrane w tym miejscu jest "Zatrzymaj" zdefiniowany przez [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) klasy z rzeczownikiem "Proc", aby wskazać, że polecenia cmdlet zatrzymuje procesy. Aby uzyskać więcej informacji na temat polecenia cmdlet zatwierdzonych czasowników, zobacz [nazwy zlecenie poleceń Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Poniżej znajduje się w definicji klasy dla tego polecenia cmdlet Stop-Proc.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

Należy pamiętać, w [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) deklaracji, `SupportsShouldProcess` — słowo kluczowe atrybutu jest równa `true` umożliwiające polecenia cmdlet do wykonywania wywołań do [ System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) i [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue). Bez tego zestawu — słowo kluczowe `Confirm` i `WhatIf` parametry nie będą dostępne dla użytkownika.

### <a name="extremely-destructive-actions"></a>Bardzo destrukcyjne działania

Niektóre operacje są bardzo destrukcyjne, takie jak ponowne formatowanie partycji active dysku twardego. W takich przypadkach należy ustawić polecenia cmdlet `ConfirmImpact`  =  `ConfirmImpact.High` podczas deklarowania [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) atrybutu. To ustawienie wymusza polecenia cmdlet na potwierdzenie żądania przez użytkownika, nawet wtedy, gdy użytkownik nie określił `Confirm` parametru. Jednak deweloperów polecenia cmdlet należy unikać nadużywanie `ConfirmImpact` dla operacji, które są po prostu potencjalnie szkodliwych, np. usunięcie konta użytkownika. Należy pamiętać, że jeśli `ConfirmImpact` ustawiono [System.Management.Automation.Confirmimpact.High](/dotnet/api/System.Management.Automation.ConfirmImpact.High).

Podobnie niektóre operacje są najprawdopodobniej nie występują destrukcyjne, mimo że teoretycznie mogą modyfikować stan działania systemu poza programu Windows PowerShell. Takie polecenia cmdlet można ustawić `ConfirmImpact` do [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0). Spowoduje to obejście żądania potwierdzenia, gdzie użytkownik został wyświetlony monit o potwierdzenie operacji tylko średni wpływ i o dużym znaczeniu.

## <a name="defining-parameters-for-system-modification"></a>Definiowanie parametrów modyfikacji systemu

W tej sekcji opisano sposób definiowania parametry polecenia cmdlet, łącznie z tymi, które są niezbędne do modyfikacji systemu pomocy technicznej. Zobacz [dodając parametry te dane wejściowe wiersza polecenia procesu](./adding-parameters-that-process-command-line-input.md) Jeśli potrzebujesz ogólnych informacji na temat definiowania parametrów.

Polecenie cmdlet Stop-Proc definiuje trzy parametry: `Name`, `Force`, i `PassThru`.

`Name` Parametr odnosi się do `Name` własności obiektu wejściowego procesu. Należy pamiętać, że `Name` parametru, w tym przykładzie jest obowiązkowe, ponieważ polecenie cmdlet zakończy się niepowodzeniem, jeśli nie ma proces o określonej nazwie, aby zatrzymać.

`Force` Parametr umożliwia użytkownikowi przesłanianie wywołania [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue). W rzeczywistości każdego polecenia cmdlet wywołująca [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) powinny mieć `Force` parametru, aby podczas `Force` jest określony, polecenie cmdlet pomija wywołanie [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) i kontynuuje operację. Należy pamiętać, że nie dotyczy to wywołania [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).

`PassThru` Parametr umożliwia użytkownikowi wskazują, czy polecenie cmdlet przekazuje obiekt danych wyjściowych, za pośrednictwem potoku, w tym przypadku po zatrzymaniu procesu. Należy pamiętać, że ten parametr jest powiązany z polecenia cmdlet sam zamiast do właściwości obiektu danych wejściowych.

Poniżej przedstawiono deklaracji parametrów dla polecenia cmdlet Stop-Proc.

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

## <a name="overriding-an-input-processing-method"></a>Zastępowanie metody przetwarzania danych wejściowych

Polecenie cmdlet jest przesłonięcie metody przetwarzania danych wejściowych. Poniższy kod ilustruje [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) zastąpienie używane w poleceniu cmdlet Stop-Proc próbki. Dla każdego żądanego nazwę procesu, ta metoda zapewnia, że proces nie jest specjalny proces, próbuje zatrzymać proces i wysyła dane wyjściowe obiektu, jeśli `PassThru` określono parametr.

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

## <a name="calling-the-shouldprocess-method"></a>Wywołanie metody ShouldProcess

Dane wejściowe przetwarzania metody Twojego polecenia cmdlet powinny wywoływać [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metodę, aby potwierdzić wykonanie operacji przed dokonaniem zmiany (na przykład usuwania plików) do stanu uruchomienia systemu. Umożliwia podanie poprawnego zachowania w zakresie "WhatIf" i "Potwierdź" w powłoce środowiska uruchomieniowego programu Windows PowerShell.

> [!NOTE]
> Jeśli polecenia cmdlet stwierdza, że obsługuje ona powinien przetworzyć i nie dokona [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) wywołać, użytkownik może modyfikować system nieoczekiwanie.

Wywołanie [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) wysyła nazwę zasobu był zmieniany na użytkownika, ze środowiskiem uruchomieniowym programu Windows PowerShell, biorąc pod uwagę wszystkie ustawienia wiersza polecenia lub zmienne preferencji określenie, co powinno być wyświetlane użytkownikowi.

W poniższym przykładzie pokazano wywołanie metody [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) z zastępowania metody [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody w przykładzie Polecenie cmdlet Stop-Proc.

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a>Wywołanie metody ShouldContinue

Wywołanie [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metoda wysyła dodatkowej wiadomości do użytkownika. To wywołanie jest przeprowadzany po wywołaniu [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) zwraca `true` i, jeśli `Force` parametr nie został ustawiony na `true`. Użytkownik może następnie udostępniać opinii powiedzieć, czy operacja powinna być kontynuowana. Wywołania polecenia cmdlet [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) jako dodatkowe sprawdzenie modyfikacje potencjalnie niebezpiecznych systemu lub gdy chcesz zapewnić tak na wszystkie, a nie na wszystkie opcje dla użytkownika.

W poniższym przykładzie pokazano wywołanie metody [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) z zastępowania metody [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody w przykładzie Polecenie cmdlet Stop-Proc.

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

## <a name="stopping-input-processing"></a>Zatrzymywanie przetwarzania danych wejściowych

Dane wejściowe przetwarzania metody polecenia cmdlet, które sprawia, że modyfikacje systemu należy podać sposób zatrzymania przetwarzania danych wejściowych. W przypadku tego polecenia cmdlet Stop-Proc, Wykonano wywołanie z [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody [System.Diagnostics.Process.Kill*](/dotnet/api/System.Diagnostics.Process.Kill) metody. Ponieważ `PassThru` parametr ma wartość `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) wywołuje również [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) do wysłania obiektu procesu do potoku.

## <a name="code-sample"></a>Przykładowy kod

Aby uzyskać pełne C# przykładowego kodu, zobacz [przykładowe StopProcessSample01](./stopprocesssample01-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definiowanie typów obiektów i formatowanie

Program Windows PowerShell przekazuje informacje między poleceniami cmdlet, używając obiektów platformy .net. W związku z tym polecenie cmdlet może być konieczne zdefiniowanie swój własny typ, lub polecenie cmdlet może być konieczne rozszerzyć istniejący typ dostarczane przez inne polecenie cmdlet. Aby uzyskać więcej informacji na temat definiowania nowych typów lub rozszerzanie istniejących typów, zobacz [rozszerzanie typów obiektów i formatowanie](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Tworzenie polecenia cmdlet

Po zaimplementowaniu polecenia cmdlet, musi być zarejestrowana przy użyciu programu Windows PowerShell za pomocą przystawki programu Windows PowerShell. Aby uzyskać więcej informacji na temat rejestrowania poleceń cmdlet, zobacz [sposób zarejestrować poleceń cmdlet, dostawców i hostowania aplikacji](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testowanie polecenia cmdlet

Po zarejestrowaniu Twojego polecenia cmdlet przy użyciu programu Windows PowerShell można ją przetestować, uruchamiając go w wierszu polecenia. Poniżej przedstawiono kilka testów, które testowe polecenie cmdlet Stop-Proc. Aby uzyskać więcej informacji o korzystaniu z poleceń cmdlet w wierszu polecenia, zobacz [wprowadzenie do programu Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Uruchom program Windows PowerShell i użyj polecenia cmdlet Stop-Proc, aby zatrzymać przetwarzanie, jak pokazano poniżej. Ponieważ polecenie cmdlet Określa `Name` parametr jako wymagane, zapytania polecenia cmdlet dla parametru.

    ```powershell
    PS> stop-proc
    ```

Zostanie wyświetlone następujące dane wyjściowe.

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- Teraz użyjemy polecenia cmdlet można zatrzymać procesu o nazwie "NOTATNIK". Polecenie cmdlet wyświetli monit o potwierdzenie akcji.

    ```powershell
    PS> stop-proc -Name notepad
    ```

Zostanie wyświetlone następujące dane wyjściowe.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Użyj Stop-Proc, jak pokazano, aby zatrzymać krytyczny proces o nazwie "Logowania do systemu Windows". Zostanie wyświetlony monit i ostrzeżenie o wykonanie tej akcji, ponieważ spowoduje to ponowne uruchomienie systemu operacyjnego.

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

Zostanie wyświetlone następujące dane wyjściowe.

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- Teraz Wypróbujmy można zatrzymać procesu WINLOGON bez otrzymania ostrzeżenia. Należy pamiętać, że ten wpis polecenie używa `Force` parametr do zastąpienia ostrzeżenia.

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

Zostanie wyświetlone następujące dane wyjściowe.

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Zobacz też

[Dodając parametry, które przetwarzają dane wejściowe wiersza polecenia](./adding-parameters-that-process-command-line-input.md)

[Formatowanie i rozszerzanie typy obiektów](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Jak zarejestrować poleceń cmdlet, dostawców i aplikacji hosta](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)

[Przykłady polecenia cmdlet](./cmdlet-samples.md)