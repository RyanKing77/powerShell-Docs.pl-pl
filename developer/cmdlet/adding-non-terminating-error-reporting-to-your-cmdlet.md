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
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a>Dodawanie raportowania błędów niepowodujących zakończenia działania do polecenia cmdlet

Polecenia cmdlet mogą raportować błędy niekończące, wywołując [System.Management.Automation.Cmdlet.WriteError][] metody i nadal będzie mogła działać na bieżący obiekt danych wejściowych lub dalsze przychodzące potoku obiektów.
W tej sekcji opisano sposób tworzenia polecenia cmdlet, który zgłasza błędy niekończące z jego metody przetwarzania danych wejściowych.

Błędy niekończące (a także błędy kończący), należy przekazać polecenie cmdlet [System.Management.Automation.ErrorRecord][] obiektu zidentyfikować błąd.
Każdy rekord błędu jest identyfikowany przez unikatowego ciągu o nazwie "Identyfikator błędu".
Oprócz identyfikatora kategorii każdego błędu jest określona przez stałe zdefiniowane przez [System.Management.Automation.ErrorCategory][] wyliczenia.
Użytkownik może wyświetlić błędy na podstawie ich kategorii, ustawiając `$ErrorView` zmienną "CategoryView".

Aby uzyskać więcej informacji na temat rekordów błędów, zobacz [rekordów błędów programu Windows PowerShell](./windows-powershell-error-records.md).

## <a name="defining-the-cmdlet"></a>Definiowanie polecenia cmdlet

Pierwszym krokiem w procesie tworzenia polecenia cmdlet jest zawsze nazewnictwa polecenia cmdlet i deklarowanie klasy .NET, która implementuje polecenia cmdlet.
To polecenie cmdlet pobiera informacje o procesu, więc nazwę zlecenie wybrane w tym miejscu to "Get".
(Prawie dowolny rodzaj polecenia cmdlet, który jest zdolny do pobierania informacji o może przetwarzać dane wejściowe wiersza polecenia). Aby uzyskać więcej informacji na temat polecenia cmdlet zatwierdzonych czasowników, zobacz [nazwy zlecenie poleceń Cmdlet](approved-verbs-for-windows-powershell-commands.md).

Poniżej przedstawiono definicję dla tego polecenia cmdlet Get-Proc.
Szczegóły tej definicji są podane w [tworzenia Your pierwsze polecenie Cmdlet](creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a>Definiowanie parametrów

W razie potrzeby Twojego polecenia cmdlet należy zdefiniować parametry w celu przetwarzania danych wejściowych.
To polecenie cmdlet Get-Proc definiuje **nazwa** parametru, zgodnie z opisem w [dodając parametry te dane wejściowe wiersza polecenia procesu](adding-parameters-that-process-command-line-input.md).

Poniżej przedstawiono deklaracji parametru pod kątem **nazwa** parametrów to polecenie cmdlet Get-Proc.

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

## <a name="overriding-input-processing-methods"></a>Zastępowanie metody przetwarzania danych wejściowych

Wszystkie polecenia cmdlet muszą przesłaniać co najmniej jedną z metod dostarczonych przez przetwarzanie danych wejściowych [System.Management.Automation.Cmdlet][] klasy.
Te metody są omówione w [tworzenia Your pierwsze polecenie Cmdlet](creating-a-cmdlet-without-parameters.md).

> [!NOTE]
> Twojego polecenia cmdlet powinny obsługiwać każdego wybranego rekordu jako niezależne, jak to możliwe.

To polecenie cmdlet Get-Proc zastępuje [System.Management.Automation.Cmdlet.ProcessRecord][] metody, aby obsłużyć **nazwa** parametr dla danych wejściowych dostarczonych przez użytkownika lub skryptu.
Ta metoda zostanie wyświetlony procesy dla każdej nazwy żądanej procesu lub wszystkich procesów, jeśli podano żadnej nazwy.
Szczegóły to zastąpienie są podane w [tworzenia Your pierwsze polecenie Cmdlet](creating-a-cmdlet-without-parameters.md).

### <a name="things-to-remember-when-reporting-errors"></a>Warto zapamiętać, gdy raportowanie błędów

[System.Management.Automation.ErrorRecord][] obiektu, że polecenia cmdlet przekazuje podczas pisania błąd wymaga wyjątek podstawą.
Podczas określania wyjątek do użycia, postępuj zgodnie z wytycznymi dla platformy .NET.
Zasadniczo Jeśli błąd semantycznie jest taka sama jak istniejące wyjątek, polecenia cmdlet należy użyć lub pochodzić od tego wyjątku.
W przeciwnym razie powinien pochodzić, nowy wyjątek lub hierarchia wyjątków bezpośrednio z [System.Exception][] klasy.

Podczas tworzenia identyfikatorów błędu (dostępne za pośrednictwem właściwości FullyQualifiedErrorId klasy rekord błędu) pamiętać o następujących.

- Ciągi użycia, które są przeznaczone do celów diagnostycznych, aby podczas sprawdzania w pełni kwalifikowanego identyfikatora można określić, jaki dokładnie błąd i w przypadku, gdy błąd pochodzi z.

- Identyfikator formy błąd w pełni kwalifikowana może wyglądać następująco.

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

Należy zauważyć, że w poprzednim przykładzie identyfikator błędu (pierwszy token) wskazuje na to, co to jest błąd i pozostałej części wskazuje, skąd pochodzą błędu.

- W przypadku bardziej złożonych scenariuszy Identyfikator błędu może być token oddzielone kropką, który może zostać przeanalizowany w zakresie kontroli.
  Dzięki temu za gałęzi na części identyfikator błędu, a także kategoria błędu identyfikator i błędów.

Polecenia cmdlet należy przypisać różne ścieżki identyfikatorów wystąpienia określonego błędu.
Pamiętać następujące informacje do przypisywania identyfikatorów, błąd:

- Identyfikator błędu należy pozostaje niezmienna przez cały cykl jej polecenia cmdlet.
  Nie należy zmieniać semantyki odpowiadającym błędzie między wersjami polecenia cmdlet.

- Tekst na użytek odpowiadający lapidarnie błąd raportowany Identyfikator błędu.
  Nie należy używać biały znak lub znaki interpunkcyjne.

- Mieć Twojego polecenia cmdlet wygenerować tylko identyfikatory błędów, które są do odtworzenia.
  Na przykład nie powinna ona generować identyfikator, który zawiera identyfikator procesu.
  Błąd identyfikatory są przydatne do użytkownika, tylko wtedy, gdy odnoszą się do identyfikatorów, które są widoczne dla innych użytkowników, w której występuje ten sam problem.

Nieobsługiwane wyjątki nie są objęte programu PowerShell w następujących warunkach:

- Jeśli polecenie cmdlet tworzy nowy wątek i kod działający w tym wątku zawiera nieobsługiwany wyjątek, programu PowerShell nie będzie przechwytywać błąd i zakończy proces.

- Jeśli obiekt ma kod w metody Dispose lub destruktor, który powoduje, że nieobsługiwany wyjątek, programu PowerShell nie będzie przechwytywać błąd i zakończy proces.

## <a name="reporting-nonterminating-errors"></a>Błędy niekończące raportowania

Jeden z metody przetwarzania danych wejściowych zgłosić błąd niekończące do strumienia wyjściowego przy użyciu [System.Management.Automation.Cmdlet.WriteError][] metody.

Poniżej przedstawiono przykładowy kod z tego polecenia cmdlet Get-Proc, który ilustruje wywołanie [System.Management.Automation.Cmdlet.WriteError][] z w ramach zastępowania metody [System.Management.Automation.Cmdlet.ProcessRecord][] metody.
W tym przypadku jest nawiązywane połączenie, jeśli polecenie cmdlet nie można odnaleźć procesu dla identyfikatora określonego procesu.

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

### <a name="things-to-remember-about-writing-nonterminating-errors"></a>Warto zapamiętać o pisaniu błędy niekończące

Błąd niekończące polecenia cmdlet należy wygenerować identyfikatora wystąpienia określonego błędu dla każdego określonego obiektu wejściowego.

Polecenia cmdlet często musi zmodyfikować produkowane przez niekończące Błąd akcji programu PowerShell.
Jego można to zrobić, definiując `ErrorAction` i `ErrorVariable` parametrów.
Jeśli definiowanie `ErrorAction` parametru polecenia cmdlet przedstawia opcje użytkownika [System.Management.Automation.ActionPreference][], można również bezpośrednio wpływają na akcję, ustawiając `$ErrorActionPreference` zmiennej.

Polecenia cmdlet można zapisać błędy niekończące do zmiennej za pomocą `ErrorVariable` parametr, który nie ma wpływu ustawienia `ErrorAction`.
Błędy można dołączyć do istniejącej zmiennej błąd, dodając znak plus (+) na początku nazwy zmiennej.

## <a name="code-sample"></a>Przykładowy kod

Aby uzyskać pełne C# przykładowego kodu, zobacz [przykładowe GetProcessSample04](./getprocesssample04-sample.md).

## <a name="define-object-types-and-formatting"></a>Zdefiniuj typy obiektów i formatowanie

Program PowerShell przekazuje informacje między poleceniami cmdlet, używając obiektów platformy .NET.
W związku z tym polecenie cmdlet może się okazać zdefiniowanie swój własny typ, lub polecenie cmdlet może być konieczne rozszerzenie istniejącego typu dostarczane przez inne polecenie cmdlet.
Aby uzyskać więcej informacji na temat definiowania nowych typów lub rozszerzanie istniejących typów, zobacz [rozszerzanie typów obiektów i formatowanie](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Tworzenie polecenia cmdlet

Po zaimplementowaniu polecenia cmdlet, należy zarejestrować go za pomocą programu Windows PowerShell za pomocą przystawki programu Windows PowerShell.
Aby uzyskać więcej informacji na temat rejestrowania poleceń cmdlet, zobacz [sposób zarejestrować poleceń cmdlet, dostawców i hostowania aplikacji](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testowanie polecenia cmdlet

Po zarejestrowaniu Twojego polecenia cmdlet przy użyciu programu PowerShell można ją przetestować, uruchamiając go w wierszu polecenia.
Teraz przetestuj przykładowe polecenie cmdlet Get-Proc aby zobaczyć, czy zgłasza błąd:

- Uruchom program PowerShell i użyj polecenia cmdlet Get-Proc można pobrać procesów o nazwie "TEST".

    ```powershell
    PS> get-proc -name test
    ```

Zostanie wyświetlone następujące dane wyjściowe.

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a>Zobacz też

[Dodając parametry, z których potok przetwarzania danych wejściowych](./adding-parameters-that-process-pipeline-input.md)

[Dodając parametry, które przetwarzają dane wejściowe wiersza polecenia](./adding-parameters-that-process-command-line-input.md)

[Tworzenie swojej pierwszej polecenia Cmdlet](./creating-a-cmdlet-without-parameters.md)

[Formatowanie i rozszerzanie typy obiektów](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Jak zarejestrować poleceń cmdlet, dostawców i aplikacji hosta](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Dokumentacja programu Windows PowerShell](../windows-powershell-reference.md)

[Przykłady polecenia cmdlet](./cmdlet-samples.md)

[System.Exception]: /dotnet/api/System.Exception
[System.Management.Automation.ActionPreference]: /dotnet/api/System.Management.Automation.ActionPreference
[System.Management.Automation.Cmdlet.ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System.Management.Automation.Cmdlet.WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System.Management.Automation.Cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System.Management.Automation.ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System.Management.Automation.ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
