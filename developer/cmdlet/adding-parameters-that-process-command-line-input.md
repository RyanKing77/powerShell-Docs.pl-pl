---
title: Dodając parametry, które przetwarzają dane wejściowe wiersza polecenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], parameters
- Get-Proc cmdlet [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], command line input
- command line input [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], creating
ms.assetid: da0b32f8-7b51-440e-a061-3177b5759e0e
caps.latest.revision: 9
ms.openlocfilehash: c9ad84c5bcb6826fcf51db9a1f1a578a65a1f275
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854951"
---
# <a name="adding-parameters-that-process-command-line-input"></a>Dodawanie parametrów, które przetwarzają dane wejściowe wiersza polecenia

Jedno źródło danych wejściowych dla polecenia cmdlet jest wiersza polecenia. W tym temacie opisano sposób dodawania parametrów do **Get-Proc** polecenia cmdlet (opisanego w [tworzenia Your pierwsze polecenie Cmdlet](./creating-a-cmdlet-without-parameters.md)) tak, aby polecenie cmdlet może przetwarzać dane wejściowe z komputera lokalnego, w oparciu o jawne obiekty są przekazywane do polecenia cmdlet. **Get-Proc** polecenia cmdlet opisane tutaj pobiera procesów na podstawie ich nazw, a następnie wyświetla informacje dotyczące procesów w wierszu polecenia.

## <a name="defining-the-cmdlet-class"></a>Definiowanie klasy polecenia Cmdlet

Pierwszym krokiem w procesie tworzenia polecenia cmdlet jest polecenie cmdlet nazewnictwa i deklarację klasy .NET Framework, która implementuje polecenia cmdlet. To polecenie cmdlet pobiera informacje o procesu, więc nazwa zlecenie wybrane w tym miejscu jest "Get". (Prawie dowolny rodzaj polecenia cmdlet, który jest zdolny do pobierania informacji o może przetwarzać dane wejściowe wiersza polecenia). Aby uzyskać więcej informacji na temat polecenia cmdlet zatwierdzonych czasowników, zobacz [nazwy zlecenie poleceń Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Poniżej przedstawiono deklarację klasy dla **Get-Proc** polecenia cmdlet. Szczegółowe informacje o tej definicji znajdują się w [tworzenia Your pierwsze polecenie Cmdlet](./creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a>Deklarowanie parametrów

Parametr polecenia cmdlet umożliwia użytkownikowi podanie danych wejściowych do polecenia cmdlet. W poniższym przykładzie **Get-Proc** i `Get-Member` są nazwami potokowe poleceń cmdlet i `MemberType` jest parametrem `Get-Member` polecenia cmdlet. Parametr ma argument "property".

**PS > get-proc; `get-member` membertype — właściwość**

Aby zadeklarować parametry polecenia cmdlet, należy najpierw zdefiniować właściwości, które reprezentują parametry. W **Get-Proc** jest jedynym parametrem polecenia cmdlet `Name`, która w tym przypadku reprezentuje nazwę obiektu procesu .NET Framework do pobrania. W związku z tym klasa polecenia cmdlet definiuje właściwość typu String, aby zaakceptować tablicę nazw.

Poniżej przedstawiono deklaracji parametru pod kątem `Name` parametru **Get-Proc** polecenia cmdlet.

```csharp
/// <summary>
/// Specify the cmdlet Name parameter.
/// </summary>
  [Parameter(Position = 0)]
  [ValidateNotNullOrEmpty]
  public string[] Name
  {
    get { return processNames; }
    set { processNames = value; }
  }
  private string[] processNames;

  #endregion Parameters
```

```vb
<Parameter(Position:=0), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

Aby poinformować środowiska uruchomieniowego programu Windows PowerShell, które ta właściwość jest `Name` parametru [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) definicji właściwości jest dodawany atrybut. Podstawowa składnia do deklarowania ten atrybut jest `[Parameter()]`.

> [!NOTE]
> Parametr musi być jawnie oznaczone jako publiczne. Parametry, które nie są oznaczane jako publicznego domyślnego wewnętrznego i nie można odnaleźć środowiska uruchomieniowego programu Windows PowerShell.

To polecenie cmdlet używa tablicę ciągów dla `Name` parametru. Jeśli to możliwe Twojego polecenia cmdlet powinny również zdefiniować parametr jako tablicę, ponieważ umożliwia to polecenie cmdlet, aby zaakceptować więcej niż jeden element.

#### <a name="things-to-remember-about-parameter-definitions"></a>Warto zapamiętać o definicjami parametrów

- Wstępnie zdefiniowane programu Windows PowerShell parametru nazwy i typy danych powinny zostać ponownie użyte możliwie najlepiej upewnić się, że Twojego polecenia cmdlet jest zgodna z poleceń cmdlet programu Windows PowerShell. Na przykład, jeśli wszystkie polecenia cmdlet używane jest wstępnie zdefiniowane `Id` Nazwa parametru do identyfikacji zasobu, użytkownik będzie łatwo zrozumieć znaczenie parametru, niezależnie od tego, jakie polecenia cmdlet używają. Po prostu nazwy parametrów, wykonaj te same zasady, które są używane dla nazwy zmiennych w środowisku uruchomieniowym języka (wspólnego CLR). Aby uzyskać więcej informacji o nazwach parametrów, zobacz [nazwy parametrów polecenia Cmdlet](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).

- Program Windows PowerShell rezerwuje kilka nazw parametrów, aby zapewnić spójne środowisko użytkownika. Nie używaj tych nazw parametrów: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, i `OutBuffer`. Ponadto następujące aliasy dla tych nazw parametrów są zarezerwowane: `vb`, `db`, `ea`, `ev`, `ov`, i `ob`.

- `Name` jest to nazwa proste i typowych parametrów, zalecane w przypadku poleceń cmdlet. Zaleca się wybrać nazwę parametru następująco niż złożone, unikatowe dla określonego polecenia cmdlet i trudne do zapamiętania nazwę.

- Parametry są bez uwzględniania wielkości liter w programie Windows PowerShell, mimo że domyślnie powłoki zachowuje wielkość liter. Uwzględnianie wielkości liter argumentów, zależy od działania polecenia cmdlet. Argumenty są przekazywane do parametru, jak określono w wierszu polecenia.

- Przykłady innych deklaracji parametrów, zobacz [parametry polecenia Cmdlet](./cmdlet-parameters.md).

## <a name="declaring-parameters-as-positional-or-named"></a>Deklarowanie parametry pozycyjne lub nazwane

Polecenia cmdlet należy ustawić każdy parametr jako parametr pozycyjne i nazwane. Oba rodzaje parametrów akceptuje pojedynczy argumentów, wiele argumentów rozdzielonych przecinkami, a ustawienia Boolean. Parametr logiczny, nazywany również *Przełącz*, obsługuje tylko logiczną ustawienia. Przełącznik służy do wykrycia obecności parametru. Zalecaną wartością domyślną jest `false`.

Przykład **Get-Proc** definiuje polecenie cmdlet `Name` parametru jako parametr pozycyjne od pozycji 0. Oznacza to, że pierwszy argument, który użytkownik wprowadza w wierszu polecenia jest automatycznie wstawiany dla tego parametru. Jeśli chcesz zdefiniować nazwany parametr, dla którego użytkownik musi określić nazwę parametru w wierszu polecenia należy pozostawić `Position` — słowo kluczowe z deklaracji atrybutu.

> [!NOTE]
> Chyba, że parametry muszą nosić, zaleca się wykonanie najczęściej używane parametry pozycyjne tak, aby użytkownicy nie będą musieli wpisać nazwę parametru.

## <a name="declaring-parameters-as-mandatory-or-optional"></a>Deklarowanie parametrów jako wymagany lub opcjonalny

Polecenia cmdlet, należy ustawić każdy parametr jako opcjonalny lub to parametr obowiązkowy. W przykładzie **Get-Proc** polecenia cmdlet, `Name` parametr jest definiowany jako opcjonalną, ponieważ `Mandatory` — słowo kluczowe nie jest ustawiona w deklaracji atrybutu.

## <a name="supporting-parameter-validation"></a>Obsługa Walidacja parametru

Przykład **Get-Proc** polecenie cmdlet dodaje atrybut walidacji danych wejściowych [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), `Name` parametru, aby włączyć weryfikację, dane wejściowe nie jest ani `null` ani pusta. Ten atrybut jest jednym z kilku atrybutów sprawdzania poprawności, udostępniane przez środowisko Windows PowerShell. Aby zapoznać się z przykładami innych atrybutów sprawdzania poprawności, zobacz [sprawdzanie poprawności wprowadzania parametrów](./validating-parameter-input.md).

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a>Zastępowanie metody przetwarzania danych wejściowych

W przypadku Twojego polecenia cmdlet do obsługi danych wejściowych wiersza polecenia, musi ono przesłonić odpowiedniej metody przetwarzania danych wejściowych. Metody podstawowe przetwarzania danych wejściowych wprowadzonych w temacie [tworzenia Your pierwsze polecenie Cmdlet](./creating-a-cmdlet-without-parameters.md).

**Get-Proc** polecenie cmdlet zastępuje [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody, aby obsłużyć `Name` parametr danych wejściowych dostarczonych przez użytkownika lub skryptu. Jeśli nazwa nie zostanie podany, ta metoda pobiera procesów dla każdej nazwy żądanej procesu lub wszystkich procesów. Należy zauważyć, że w [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), wywołanie [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) znajdują się dane wyjściowe mechanizm umożliwiający wysyłanie danych wyjściowych obiektów do potoku. Drugi parametr to wywołanie `enumerateCollection`, jest równa `true` poinformować wyliczyć tablicy danych wyjściowych obiektów procesów i zapisać jeden proces naraz w wierszu polecenia środowiska uruchomieniowego programu Windows PowerShell.

```csharp
protected override void ProcessRecord()
{
  // If no process names are passed to the cmdlet, get all processes.
  if (processNames == null)
  {
    // Write the processes to the pipeline making them available
    // to the next cmdlet. The second argument of this call tells
    // PowerShell to enumerate the array, and send one process at a
    // time to the pipeline.
    WriteObject(Process.GetProcesses(), true);
  }
  else
  {
    // If process names are passed to the cmdlet, get and write
    // the associated processes.
    foreach (string name in processNames)
    {
      WriteObject(Process.GetProcessesByName(name), true);
    }
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        Dim processes As Process()
        processes = Process.GetProcesses()
    End If

    '/ If process names are specified, write the processes to the
    '/ pipeline to display them or make them available to the next cmdlet.

    For Each name As String In processNames
        '/ The second parameter of this call tells PowerShell to enumerate the
        '/ array, and send one process at a time to the pipeline.
        WriteObject(Process.GetProcessesByName(name), True)
    Next

End Sub 'ProcessRecord
```

## <a name="code-sample"></a>Przykładowy kod

Aby uzyskać pełne C# przykładowego kodu, zobacz [przykładowe GetProcessSample02](./getprocesssample02-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definiowanie typów obiektów i formatowanie

Program Windows PowerShell przekazuje informacje między poleceniami cmdlet przy użyciu obiektów .NET Framework. W związku z tym polecenie cmdlet może się okazać zdefiniowanie swój własny typ, lub polecenie cmdlet może być konieczne rozszerzenie istniejącego typu dostarczane przez inne polecenie cmdlet. Aby uzyskać więcej informacji na temat definiowania nowych typów lub rozszerzanie istniejących typów, zobacz [rozszerzanie typów obiektów i formatowanie](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Tworzenie polecenia cmdlet

Po zaimplementowaniu polecenia cmdlet należy zarejestrować go za pomocą programu Windows PowerShell, za pomocą przystawki programu Windows PowerShell. Aby uzyskać więcej informacji na temat rejestrowania poleceń cmdlet, zobacz [sposób zarejestrować poleceń cmdlet, dostawców i hostowania aplikacji](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testowanie polecenia cmdlet

Gdy Twojego polecenia cmdlet zostanie zarejestrowane przy użyciu programu Windows PowerShell, można ją przetestować, uruchamiając go w wierszu polecenia. Poniżej przedstawiono dwa sposoby, aby przetestować kod, aby uzyskać przykładowe polecenie cmdlet. Aby uzyskać więcej informacji o korzystaniu z poleceń cmdlet w wierszu polecenia, zobacz [wprowadzenie do programu Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- W wierszu polecenia programu Windows PowerShell Użyj następującego polecenia, aby wyświetlić listę proces programu Internet Explorer, który nosi nazwę "IEXPLORE."

    ```powershell
    PS> get-proc -name iexplore
    ```

Zostanie wyświetlone następujące dane wyjściowe.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- Aby wyświetlić listę procesów programu Internet Explorer, Outlook i Notatnik, o nazwie "IEXPLORE", "OUTLOOK" i "NOTATNIK", użyj następującego polecenia. W przypadku wielu procesów, są wyświetlane wszystkie z nich.

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

Zostanie wyświetlone następujące dane wyjściowe.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a>Zobacz też

[Dodając parametry, z których potok przetwarzania danych wejściowych](./adding-parameters-that-process-pipeline-input.md)

[Tworzenie swojej pierwszej polecenia Cmdlet](./creating-a-cmdlet-without-parameters.md)

[Formatowanie i rozszerzanie typy obiektów](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Jak zarejestrować poleceń cmdlet, dostawców i aplikacji hosta](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Dokumentacja programu Windows PowerShell](../windows-powershell-reference.md)

[Przykłady polecenia cmdlet](./cmdlet-samples.md)
