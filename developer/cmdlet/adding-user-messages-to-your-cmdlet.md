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
ms.openlocfilehash: 5b3a5f5d5d02c7d5a3c1d622ec1a3740739c694f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055040"
---
# <a name="adding-user-messages-to-your-cmdlet"></a>Dodawanie wiadomości użytkownika do polecenia cmdlet

Polecenia cmdlet można napisać kilka rodzajów wiadomości, które mogą być wyświetlane użytkownikowi w czasie wykonywania programu Windows PowerShell. Te komunikaty zawierają następujące typy:

- Pełne komunikaty, które zawierają ogólne informacje o użytkowniku.

- Debugowanie komunikatów, które zawierają informacje dotyczące rozwiązywania problemów.

- Komunikaty ostrzegawcze, które zawierają powiadomienie, że polecenie cmdlet ma wykonywać operacji, która może mieć nieoczekiwane wyniki.

- Raport postęp polecenia cmdlet działać, komunikaty, które zawierają informacje o ile zostało zakończone, podczas wykonywania operacji, która zajmuje dużo czasu.

Nie ma ograniczeń liczby wiadomości, które może zapisać Twojego polecenia cmdlet lub typ wiadomości, które zapisuje Twojego polecenia cmdlet. Każdy komunikat jest zapisywany, wprowadzając wywołania określone dane wejściowe przetwarzania metody Twojego polecenia cmdlet.

## <a name="the-stopproc-cmdlet"></a>Polecenia cmdlet StopProc

Tematy w tej sekcji są następujące:

- [Definiowanie polecenia cmdlet](#Defining-the-Cmdlet)

- [Definiowanie parametrów modyfikacji systemu](#Defining-Parameters-for-System-Modification)

- [Zastępowanie metody przetwarzania danych wejściowych](#Overriding-an-Input-Processing-Method)

- [Zapisywanie komunikat trybu informacji pełnej](#Writing-a-Verbose-Message)

- [Zapisywanie komunikatów debugowania](#Writing-a-Debug-Message)

- [Zapisywanie komunikatu ostrzegawczego](#Writing-a-Warning-Message)

- [Zapisywanie komunikatu o postępie](#Writing-a-Progress-Message)

- [Przykładowy kod](#Code-Sample)

- [Zdefiniuj typy obiektów i formatowanie](#Define-Object-Types-and-Formatting)

- [Tworzenie polecenia cmdlet](#Building-the-Cmdlet)

- [Testowanie polecenia cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>Definiowanie polecenia cmdlet

Pierwszym krokiem w procesie tworzenia polecenia cmdlet jest zawsze nazewnictwa polecenia cmdlet i deklarowanie klasy .NET, która implementuje polecenia cmdlet. Dowolny rodzaj polecenia cmdlet można napisać powiadomienia użytkownika z metody; przetwarzania danych wejściowych tak ogólnie rzecz biorąc, możesz nazwać tego polecenia cmdlet przy użyciu dowolnej zlecenie, która wskazuje, jakie modyfikacje system wykonuje polecenie cmdlet. Aby uzyskać więcej informacji na temat polecenia cmdlet zatwierdzonych czasowników, zobacz [nazwy zlecenie poleceń Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Polecenia cmdlet Stop-Proc jest przeznaczony do modyfikacji systemu; w związku z tym [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) deklaracja klasy .NET musi zawierać `SupportsShouldProcess` atrybutu — słowo kluczowe i można ustawić `true`.

Poniższy kod jest definicji dla tej klasy polecenia cmdlet Stop-Proc. Aby uzyskać więcej informacji na temat tej definicji, zobacz [Tworzenie polecenia Cmdlet, który modyfikuje System](./creating-a-cmdlet-that-modifies-the-system.md).

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Definiowanie parametrów modyfikacji systemu

Polecenie cmdlet Stop-Proc definiuje trzy parametry: `Name`, `Force`, i `PassThru`. Aby uzyskać więcej informacji na temat definiowania tych parametrów, zobacz [Tworzenie polecenia Cmdlet, który modyfikuje System](./creating-a-cmdlet-that-modifies-the-system.md).

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

Twojego polecenia cmdlet jest przesłonięcie metody przetwarzania danych wejściowych, w większości przypadków będzie [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). To polecenie cmdlet Stop-Proc zastępuje [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) przetwarzania metody wejściowej. W tej implementacji polecenia cmdlet Stop-Proc wywołań do zapisania pełne komunikaty wyjściowe komunikaty debugowania i komunikaty ostrzegawcze.

> [!NOTE]
> Aby uzyskać więcej informacji na temat jak ta metoda wywołuje [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) i [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metod, zobacz [Tworzenie polecenia Cmdlet, który modyfikuje System](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="writing-a-verbose-message"></a>Zapisywanie komunikat trybu informacji pełnej

[System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) metoda służy do zapisywania ogólne informacje na poziomie użytkownika, która nie ma wpływu na określone warunki błędów. Administrator systemu może następnie używać tych informacji, aby kontynuować przetwarzania innych poleceń. Ponadto powinien być zlokalizowany wszelkie informacje napisane przy użyciu tej metody, stosownie do potrzeb.

Poniższy kod z tego polecenia cmdlet Stop-Proc przedstawia dwa wywołania [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) metody z zastępowania metody [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody.

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a>Zapisywanie komunikatów debugowania

[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) metoda służy do zapisywania komunikatów debugowania, które mogą służyć do rozwiązywania problemów z polecenia cmdlet. Wykonano wywołanie z metody przetwarzania danych wejściowych.

> [!NOTE]
> Definiuje również środowiska Windows PowerShell `Debug` parametr, który przedstawia zarówno pełne i informacje o debugowaniu. Jeśli Twoje polecenie cmdlet obsługuje ten parametr, nie trzeba wywoływać [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) w ten sam kod, który wywołuje [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) .

Następujące dwie sekcje kodu z przykładowe polecenie cmdlet Stop-Proc Pokaż wywołania [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) metody z zastępowania metody [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody.

Ten komunikat debugowania są zapisywane bezpośrednio przed [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) jest wywoływana.

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

Ten komunikat debugowania są zapisywane bezpośrednio przed [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) jest wywoływana.

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

Windows PowerShell automatycznie kieruje dowolnego [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) wywołania śledzenia infrastruktury i polecenia cmdlet. Dzięki temu wywołania metody do śledzenia do hostowania aplikacji, plik lub debugera bez konieczności ponownego wykonać pracę dodatkowe rozwoju w ramach polecenia cmdlet. Następujący wpis wiersza polecenia implementuje operacji śledzenia.

**PS > wyrażenie śledzenia stop-proc — plik proc.log — polecenia stop-proc Notatnik**

## <a name="writing-a-warning-message"></a>Zapisywanie komunikatu ostrzegawczego

[System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) metoda służy do zapisywania ostrzeżenia, gdy polecenie cmdlet ma wykonać operacji, która może mieć nieoczekiwany wynik, na przykład zastąpienia pliku tylko do odczytu.

Poniższy kod z polecenia cmdlet Stop-Proc przykładowy pokazuje wywołanie [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) metody z zastępowania metody [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody.

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a>Zapisywanie komunikatu o postępie

[System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) używany do zapisywania wiadomości dotyczące postępu podczas operacji polecenia cmdlet zająć dużo czasu wykonania. Wywołanie [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) przekazuje [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) obiekt, który jest wysyłany do hostowania aplikacji w celu renderowania dla użytkownika.

> [!NOTE]
> To polecenie cmdlet Stop-Proc nie zawiera wywołanie [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) metody.

Poniższy kod jest przykładem komunikat o postępie napisane przez polecenia cmdlet, które próbuje skopiować element.

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a>Przykładowy kod

Aby uzyskać pełne C# przykładowego kodu, zobacz [przykładowe StopProcessSample02](./stopprocesssample02-sample.md).

## <a name="define-object-types-and-formatting"></a>Zdefiniuj typy obiektów i formatowanie

Program Windows PowerShell przekazuje informacje między poleceniami cmdlet, używając obiektów platformy .NET. W związku z tym polecenie cmdlet może się okazać zdefiniowanie swój własny typ, lub polecenie cmdlet może być konieczne rozszerzenie istniejącego typu dostarczane przez inne polecenie cmdlet. Aby uzyskać więcej informacji na temat definiowania nowych typów lub rozszerzanie istniejących typów, zobacz [rozszerzanie typów obiektów i formatowanie](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Tworzenie polecenia cmdlet

Po zaimplementowaniu polecenia cmdlet, musi być zarejestrowana przy użyciu programu Windows PowerShell za pomocą przystawki programu Windows PowerShell. Aby uzyskać więcej informacji na temat rejestrowania poleceń cmdlet, zobacz [sposób zarejestrować poleceń cmdlet, dostawców i hostowania aplikacji](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testowanie polecenia cmdlet

Po zarejestrowaniu Twojego polecenia cmdlet przy użyciu programu Windows PowerShell można ją przetestować, uruchamiając go w wierszu polecenia. Teraz przetestuj przykładowe polecenie cmdlet Stop-Proc. Aby uzyskać więcej informacji o korzystaniu z poleceń cmdlet w wierszu polecenia, zobacz [wprowadzenie do programu Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Następujący wpis wiersza polecenia używa Stop-Proc, aby zatrzymać proces o nazwie "NOTATNIK", zapewniają pełne powiadomienia i drukowanie informacji debugowania.

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

Zostanie wyświetlone następujące dane wyjściowe.

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

## <a name="see-also"></a>Zobacz też

[Tworzenie polecenia Cmdlet, który modyfikuje systemu](./creating-a-cmdlet-that-modifies-the-system.md)

[Jak utworzyć polecenia Cmdlet programu Windows PowerShell](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Formatowanie i rozszerzanie typy obiektów](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Jak zarejestrować poleceń cmdlet, dostawców i aplikacji hosta](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)
