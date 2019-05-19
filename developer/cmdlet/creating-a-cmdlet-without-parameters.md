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
ms.openlocfilehash: 7f10acf59dedbb4af17bc5250e8624282ba22656
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854963"
---
# <a name="creating-a-cmdlet-without-parameters"></a>Tworzenie polecenia cmdlet bez parametrów

Ta sekcja zawiera opis sposobu tworzenia polecenia cmdlet, które pobiera informacje z komputera lokalnego bez użycia parametrów, a następnie zapisuje informacje do potoku. Polecenia cmdlet opisane w tym miejscu to polecenie cmdlet Get-Proc, pobiera informacje o procesach komputera lokalnego, a następnie wyświetli te informacje w wierszu polecenia.

> [!NOTE]
> Należy pamiętać, że podczas pisania poleceń cmdlet, zestawy odwołań Windows PowerShell® domyślnie pobierane są na dysku (w C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0). Nie są zainstalowane w globalnej pamięci podręcznej zestawów (GAC).

## <a name="naming-the-cmdlet"></a>Polecenia cmdlet nazewnictwa

Nazwa polecenia cmdlet składa się z zlecenia, który wskazuje, że przez polecenie cmdlet akcję i rzeczownik, który wskazuje elementy, które działają polecenia cmdlet. Ponieważ to polecenie cmdlet Get-Proc przykład umożliwia pobranie obiektów procesu, używa ona czasownik "Pobierz", zdefiniowane przez [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) wyliczenie i rzeczownik "Proc", aby wskazać, że polecenie cmdlet działa w elementach procesu.

Podczas określania nazwy poleceń cmdlet, nie używaj żadnego z następujących znaków: #, () {} [] & - / \ $;: "" <> &#124; ? @ ` .

### <a name="choosing-a-noun"></a>Wybieranie rzeczownik

Należy wybrać rzeczownik, który jest specyficzny. Najlepiej użyć pojedynczej rzeczownik, prefiks z wersją skróconą nazwę produktu. Przykładowa nazwa polecenia cmdlet tego typu jest "`Get-SQLServer`".

### <a name="choosing-a-verb"></a>Wybieranie zlecenia

Należy użyć zlecenia z zestawu nazwy zlecenie zatwierdzonych poleceń cmdlet. Aby uzyskać więcej informacji na temat zatwierdzone czasowniki zobacz [nazwy zlecenie poleceń Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

## <a name="defining-the-cmdlet-class"></a>Definiowanie klasy polecenia Cmdlet

Po wybraniu opcji Nazwa polecenia cmdlet, należy zdefiniować klasa platformy .NET w celu wykonania polecenia cmdlet. Poniżej przedstawiono w definicji klasy dla tego polecenia cmdlet Get-Proc próbki:

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

Należy zauważyć, że przed definicją klasy [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) atrybutu przy użyciu składni `[Cmdlet(verb, noun, ...)]`, jest używany do identyfikowania tej klasy jako polecenia cmdlet. Jest to jedyny atrybut wymagane dla wszystkich poleceń cmdlet i pozwala wywoływać je poprawnie środowiska uruchomieniowego programu Windows PowerShell. Można ustawić atrybutu słów kluczowych, aby dodatkowo zadeklarować klasy, jeśli to konieczne. Należy pamiętać, że deklaracji atrybutu dla klasy GetProcCommand nasze przykładowe deklaruje tylko nazwy polecenia cmdlet Get-Proc rzeczownika i zlecenie.

> [!NOTE]
> Dla wszystkich klas atrybutów programu Windows PowerShell słowa kluczowe, które można ustawić odnoszą się do właściwości klasy atrybutu.

Podczas określania nazwy klasy polecenia cmdlet, jest dobrym rozwiązaniem, aby odzwierciedlić nazwę polecenia cmdlet w nazwie klasy. W tym celu należy użyć formy "VerbNounCommand" i zastąp "Czasownik" i "Rzeczownik" czasownik i rzeczownik nazwa polecenia cmdlet. Jak pokazano w poprzednim definicji klasy, przykładowe polecenie cmdlet Get-Proc definiuje klasę o nazwie GetProcCommand, która jest pochodną [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klasy bazowej.

> [!IMPORTANT]
> Jeśli chcesz zdefiniować polecenia cmdlet, który uzyskuje dostęp do środowiska wykonawczego programu Windows PowerShell bezpośrednio klasy .NET powinien pochodzić od [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) klasy bazowej. Aby uzyskać więcej informacji na temat tej klasy, zobacz [tworzenia tego definiuje zestawy parametrów polecenia Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).

> [!NOTE]
> Klasy związane z poleceniem cmdlet musi być jawnie oznaczone jako publiczne. Klasy, które nie zostały oznaczone jako publiczne będą domyślnie wewnętrznego i nie zostanie znaleziony w czasie wykonywania programu Windows PowerShell.

Używa programu Windows PowerShell [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) przestrzeń nazw dla swojej klasy polecenia cmdlet. Zalecane jest umieszczenie Twoich zajęciach polecenia cmdlet w przestrzeni nazw poleceń przestrzeni nazw interfejsu API, na przykład xxx.PS.Commands.

## <a name="overriding-an-input-processing-method"></a>Zastępowanie metody przetwarzania danych wejściowych

[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klasa udostępnia trzy metody głównej przetwarzania danych wejściowych, co najmniej jeden z nich muszą przesłaniać Twojego polecenia cmdlet. Aby uzyskać więcej informacji o przetwarzaniu rekordy w programie Windows PowerShell, zobacz [sposób działania programu Windows PowerShell](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

Dla wszystkich typów danych wejściowych, środowisko wykonawcze programu Windows PowerShell wywołuje [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) umożliwiające przetwarzania. Jeśli Twojego polecenia cmdlet należy wykonać niektóre wstępne przetwarzanie lub Instalator, go to zrobić przez zastąpienie tej metody.

> [!NOTE]
> Do opisania zestawem wartości parametrów, które podano podczas wywoływania polecenia cmdlet, programu Windows PowerShell używa termin "record".

Jeśli Twojego polecenia cmdlet akceptuje dane wejściowe w potoku, musi ono przesłonić [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metodę i opcjonalnie [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)metody. Na przykład polecenia cmdlet mogą zastąpić obie metody, jeśli zbiera wszystkie dane wejściowe, używając [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) , a następnie dane wejściowe jako całości, a nie jeden element w czasie, jako `Sort-Object` wykonuje polecenie cmdlet.

Jeśli Twojego polecenia cmdlet nie przyjmuje dane wejściowe w potoku, należy zastąpić [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metody. Należy pamiętać, że ta metoda jest często używana zamiast [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) gdy polecenie cmdlet nie może działać na jeden element w czasie, tak jak w przypadku sortowania polecenia cmdlet.

Ponieważ to przykładowe polecenie cmdlet Get-Proc musi otrzymać bit wejście potokowe, zastępuje ona [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody i używa domyślnej implementacji dla [ System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) i [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing). [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) zastąpienie pobiera procesy i zapisuje je w wiersza polecenia przy użyciu [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) metody.

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

#### <a name="things-to-remember-about-input-processing"></a>Warto zapamiętać informacje o przetwarzaniu danych wejściowych

- Domyślne źródło danych wejściowych jest obiektem jawne (na przykład, ciąg), dostarczone przez użytkownika w wierszu polecenia. Aby uzyskać więcej informacji, zobacz [polecenia Cmdlet, aby dane wejściowe wiersza polecenia procesu tworzenia](./adding-parameters-that-process-command-line-input.md).

- Metoda przetwarzania danych wejściowych może również odbierać dane wejściowe z danych wyjściowych obiektu nadrzędnego polecenia cmdlet do potoku. Aby uzyskać więcej informacji, zobacz [tworzenia polecenia Cmdlet, aby proces wejście potokowe](./adding-parameters-that-process-pipeline-input.md). Należy pamiętać, że Twojego polecenia cmdlet mogą odbierać dane wejściowe z kombinacji wiersza polecenia i potoku źródła.

- Polecenia cmdlet podrzędne mogą nie zwracać przez długi czas lub wcale. Z tego powodu, dane wejściowe przetwarzania metody w Twojego polecenia cmdlet powinno zawierać nie blokad podczas wywołania [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), szczególnie blokad, dla których zakres wykracza poza wystąpieniem polecenia cmdlet.

> [!IMPORTANT]
> Polecenia cmdlet nigdy nie powinien wywoływać [System.Console.Writeline*](/dotnet/api/System.Console.WriteLine) lub równoważnym.

- Środowiska może mieć obiektu zmienne, aby wyczyścić po zakończeniu przetwarzania (na przykład, jeśli zostanie on otwarty dojście do pliku w [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metody i przechowuje dojście Otwórz do użytku przez [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)). Należy pamiętać, że środowisko wykonawcze programu Windows PowerShell nie zawsze wywołuje [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metody, która powinna wykonać oczyszczania obiektu.

Na przykład [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) nie może być wywoływana, jeśli polecenia cmdlet zostanie anulowane w środku lub gdy kończącym błędu w jakichkolwiek pracach związanych z polecenia cmdlet. W związku z tym, polecenia cmdlet, które wymaga czyszczenia obiektu powinny implementować pełne [System.IDisposable](/dotnet/api/System.IDisposable) wzorca, w tym finalizator, dzięki czemu środowisko uruchomieniowe może wywołać zarówno [ System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) i [System.IDisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) po zakończeniu przetwarzania.

## <a name="code-sample"></a>Przykładowy kod

Aby uzyskać pełne C# przykładowego kodu, zobacz [przykładowe GetProcessSample01](./getprocesssample01-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definiowanie typów obiektów i formatowanie

Program Windows PowerShell przekazuje informacje między poleceniami cmdlet, używając obiektów platformy .NET. W związku z tym polecenie cmdlet może się okazać zdefiniowanie swój własny typ, lub polecenie cmdlet może być konieczne rozszerzenie istniejącego typu dostarczane przez inne polecenie cmdlet. Aby uzyskać więcej informacji na temat definiowania nowych typów lub rozszerzanie istniejących typów, zobacz [rozszerzanie typów obiektów i formatowanie](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Tworzenie polecenia cmdlet

Po zaimplementowaniu polecenia cmdlet, należy zarejestrować go za pomocą programu Windows PowerShell za pomocą przystawki programu Windows PowerShell. Aby uzyskać więcej informacji na temat rejestrowania poleceń cmdlet, zobacz [sposób zarejestrować poleceń cmdlet, dostawców i hostowania aplikacji](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testowanie polecenia cmdlet

Po zarejestrowaniu Twojego polecenia cmdlet przy użyciu programu Windows PowerShell można ją przetestować, uruchamiając go w wierszu polecenia. Kod nasze przykładowe polecenie cmdlet Get-Proc jest mały, ale nadal używa środowiska uruchomieniowego programu Windows PowerShell i istniejący obiekt .NET, która jest wystarczająco dużo, aby była przydatna. Możemy go przetestować, aby lepiej zrozumieć, co zrobić, Get-Proc i jak można używać jej dane wyjściowe. Aby uzyskać więcej informacji o korzystaniu z poleceń cmdlet w wierszu polecenia, zobacz [wprowadzenie do programu Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

1. Uruchom program Windows PowerShell, a następnie pobrać bieżących procesów uruchomionych na komputerze.

    ```powershell
    get-proc
    ```

    Zostanie wyświetlone następujące dane wyjściowe.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. Przypisz zmienną do wyników polecenia cmdlet do manipulacji łatwiejsze.

    ```powershell
    $p=get-proc
    ```

3. Pobierz liczbę procesów.

    ```powershell
    $p.length
    ```

    Zostanie wyświetlone następujące dane wyjściowe.

    ```output
    63
    ```

4. Pobieranie określonego procesu.

    ```powershell
    $p[6]
    ```

    Zostanie wyświetlone następujące dane wyjściowe.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. Uzyskaj czas rozpoczęcia tego procesu.

    ```powershell
    $p[6].starttime
    ```

    Zostanie wyświetlone następujące dane wyjściowe.

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. Uzyskaj procesy, dla których jest większy niż 500 licznika dojść i sortować wyniki.

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    Zostanie wyświetlone następujące dane wyjściowe.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. Użyj `Get-Member` polecenia cmdlet, aby wyświetlić listę właściwości dostępnych dla każdego procesu.

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    Zostanie wyświetlone następujące dane wyjściowe.

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a>Zobacz też

[Tworzenie polecenia Cmdlet do przetwarzania danych wejściowych wiersza polecenia](./adding-parameters-that-process-command-line-input.md)

[Polecenia Cmdlet do przetwarzania danych wejściowych potoku tworzenia](./adding-parameters-that-process-pipeline-input.md)

[Jak utworzyć polecenia Cmdlet programu Windows PowerShell](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Formatowanie i rozszerzanie typy obiektów](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Jak działa program Windows PowerShell](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Jak zarejestrować poleceń cmdlet, dostawców i aplikacji hosta](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Dokumentacja programu Windows PowerShell](../windows-powershell-reference.md)

[Przykłady polecenia cmdlet](./cmdlet-samples.md)