---
title: Dodając parametry, które przetwarzają dane wejściowe w potoku | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], pipeline input
- parameters [PowerShell Programmer's Guide], pipeline input
ms.assetid: 09bf70a9-7c76-4ffe-b3f0-a1d5f10a0931
caps.latest.revision: 8
ms.openlocfilehash: bd52dc8aee7975d0899083a5c2f595b17690dc33
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054768"
---
# <a name="adding-parameters-that-process-pipeline-input"></a>Dodawanie parametrów, które przetwarzają dane wejściowe potoku

Jedno źródło danych wejściowych dla polecenia cmdlet jest obiekt w potoku, który pochodzi z nadrzędnego polecenia cmdlet. W tej sekcji opisano sposób dodać parametr do polecenia cmdlet Get-Proc (opisanego w [tworzenia Your pierwsze polecenie Cmdlet](./creating-a-cmdlet-without-parameters.md)) tak, aby polecenie cmdlet może przetwarzać obiektów z potoku.

To polecenie cmdlet Get-Proc używa `Name` parametr, który akceptuje dane wejściowe z obiektu potok pobiera informacje o procesach z komputera lokalnego, w oparciu o podanej nazwy i następnie wyświetla informacje dotyczące procesów w wierszu polecenia.

Tematy w tej sekcji są następujące:

- [Definiowanie klasy polecenia Cmdlet](#Defining-the-Cmdlet-Class)

- [Definiowanie danych wejściowych z potoku](#Defining-Input-from-the-Pipeline)

- [Zastępowanie metody przetwarzania danych wejściowych](#Overriding-an-Input-Processing-Method)

- [Przykładowy kod](#Code-Sample)

- [Definiowanie typów obiektów i formatowanie](#Defining-Object-Types-and-Formatting)

- [Tworzenie polecenia cmdlet](#Building-the-Cmdlet)

- [Testowanie polecenia cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a>Definiowanie klasy polecenia Cmdlet

Pierwszym krokiem w procesie tworzenia polecenia cmdlet jest zawsze nazewnictwa polecenia cmdlet i deklarowanie klasy .NET, która implementuje polecenia cmdlet. To polecenie cmdlet pobiera informacje o procesu, więc nazwę zlecenie wybrane w tym miejscu to "Get". (Prawie dowolny rodzaj polecenia cmdlet, który jest zdolny do pobierania informacji o może przetwarzać dane wejściowe wiersza polecenia). Aby uzyskać więcej informacji na temat polecenia cmdlet zatwierdzonych czasowników, zobacz [nazwy zlecenie poleceń Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Poniżej przedstawiono definicję dla tego polecenia cmdlet Get-Proc. Szczegóły tej definicji są podane w [tworzenia Your pierwsze polecenie Cmdlet](./creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a>Definiowanie danych wejściowych z potoku

W tej sekcji opisano sposób definiowania danych wejściowych z potoku do polecenia cmdlet. To polecenie cmdlet Get-Proc definiuje właściwość, która reprezentuje `Name` parametru, zgodnie z opisem w [dodając parametry te dane wejściowe wiersza polecenia procesu](./adding-parameters-that-process-command-line-input.md). (Zobacz tego tematu ogólne informacje o deklarowanie parametrów).

Jednak gdy polecenie cmdlet wymaga do przetwarzania danych wejściowych potoku, musi mieć parametry powiązany z wartości wejściowe przez środowisko uruchomieniowe programu Windows PowerShell. Aby to zrobić, należy dodać `ValueFromPipeline` — słowo kluczowe lub dodać `ValueFromPipelineByProperty` słowa kluczowego [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) deklaracji atrybutu. Określ `ValueFromPipeline` — słowo kluczowe, jeśli polecenie cmdlet uzyskuje dostęp do kompletnego obiektu wejściowego. Określ `ValueFromPipelineByProperty` Jeśli polecenia cmdlet uzyskuje dostęp do właściwości obiektu.

Poniżej przedstawiono deklaracji parametru pod kątem `Name` parametrów to polecenie cmdlet Get-Proc, który akceptuje dane wejściowe w potoku.

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L35-L44 "GetProcessSample03.cs")]

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

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#GetProc03VBNameParameter](Msh_samplesgetproc03#GetProc03VBNameParameter)]  -->

Poprzednie zestawy deklaracji `ValueFromPipeline` słowa kluczowego `true` tak, aby środowisko uruchomieniowe programu Windows PowerShell będzie powiązać parametr przychodzącego obiektu Jeśli obiekt jest taki sam typ co parametr lub może być przekształcone do tego samego typu. `ValueFromPipelineByPropertyName` — Słowo kluczowe jest również ustawiona na `true` tak, aby środowisko uruchomieniowe programu Windows PowerShell będzie sprawdzać przychodzącego obiektu dla `Name` właściwości. Jeśli obiekt przychodzące ma taką właściwość, środowisko uruchomieniowe powiąże `Name` parametr `Name` przychodzącego obiektu.

> [!NOTE]
> Ustawienie `ValueFromPipeline` atrybutu — słowo kluczowe parametru mają pierwszeństwo przed ustawieniem dla `ValueFromPipelineByPropertyName` — słowo kluczowe.

## <a name="overriding-an-input-processing-method"></a>Zastępowanie metody przetwarzania danych wejściowych

W przypadku Twojego polecenia cmdlet do obsługi danych wejściowych potoku, trzeba zastąpić odpowiedniej metody przetwarzania danych wejściowych. Metody podstawowe przetwarzania danych wejściowych wprowadzonych w temacie [tworzenia Your pierwsze polecenie Cmdlet](./creating-a-cmdlet-without-parameters.md).

To polecenie cmdlet Get-Proc zastępuje [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metody, aby obsłużyć `Name` parametr danych wejściowych dostarczonych przez użytkownika lub skryptu. Ta metoda zostanie wyświetlony procesy dla każdej nazwy żądanej procesu lub wszystkich procesów, jeśli podano żadnej nazwy. Należy zauważyć, że w ramach [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), wywołanie [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) znajdują się dane wyjściowe mechanizm umożliwiający wysyłanie danych wyjściowych obiektów do potoku. Drugi parametr to wywołanie `enumerateCollection`, jest równa `true` stwierdzić, środowisko wykonawcze programu Windows PowerShell do wyliczania tablicy obiektów procesów i zapisać jeden proces naraz w wierszu polecenia.

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
    } // End foreach (string name...).
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()
    Dim processes As Process()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        processes = Process.GetProcesses()
    Else

        '/ If process names are specified, write the processes to the
        '/ pipeline to display them or make them available to the next cmdlet.
        For Each name As String In processNames
            '/ The second parameter of this call tells PowerShell to enumerate the
            '/ array, and send one process at a time to the pipeline.
            WriteObject(Process.GetProcessesByName(name), True)
        Next
    End If

End Sub 'ProcessRecord
```

## <a name="code-sample"></a>Przykładowy kod

Aby uzyskać pełne C# przykładowego kodu, zobacz [przykładowe GetProcessSample03](./getprocesssample03-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definiowanie typów obiektów i formatowanie

Program Windows PowerShell przekazuje informacje między poleceniami cmdlet, używając obiektów platformy .net. W związku z tym polecenie cmdlet może być konieczne zdefiniowanie swój własny typ, lub polecenie cmdlet może być konieczne rozszerzyć istniejący typ dostarczane przez inne polecenie cmdlet. Aby uzyskać więcej informacji na temat definiowania nowych typów lub rozszerzanie istniejących typów, zobacz [rozszerzanie typów obiektów i formatowanie](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Tworzenie polecenia cmdlet

Po zaimplementowaniu polecenie cmdlet musi być zarejestrowana przy użyciu programu Windows PowerShell za pomocą przystawki programu Windows PowerShell. Aby uzyskać więcej informacji na temat rejestrowania poleceń cmdlet, zobacz [sposób zarejestrować poleceń cmdlet, dostawców i hostowania aplikacji](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testowanie polecenia cmdlet

Gdy Twoje polecenie cmdlet został zarejestrowany za pomocą programu Windows PowerShell, należy go przetestować, uruchamiając go w wierszu polecenia. Na przykład przetestować kod, aby uzyskać przykładowe polecenie cmdlet. Aby uzyskać więcej informacji o korzystaniu z poleceń cmdlet w wierszu polecenia, zobacz [wprowadzenie do programu Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- W wierszu polecenia programu Windows PowerShell wpisz następujące polecenia, aby pobrać nazw procesów przy użyciu potoku.

    ```powershell
    PS> type ProcessNames | get-proc
    ```

Zostanie wyświetlone następujące dane wyjściowe.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----   ----- -----   ------    --  -----------
        809      21  40856    4448    147    9.50  2288  iexplore
        737      21  26036   16348    144   22.03  3860  iexplore
         39       2   1024     388     30    0.08  3396  notepad
       3927      62  71836   26984    467  195.19  1848  OUTLOOK
    ```

- Wprowadź następujące wiersze, które można pobrać obiektów procesów, które mają `Name` właściwości od procesów o nazwie "IEXPLORE". W tym przykładzie użyto `Get-Process` polecenia cmdlet (udostępnione przez środowisko Windows PowerShell) jako nadrzędnego polecenie, aby pobrać procesów "IEXPLORE".

    ```powershell
    PS> get-process iexplore | get-proc
    ```

Zostanie wyświetlone następujące dane wyjściowe.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----      ----- -----   ------     -- -----------
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
    ```

## <a name="see-also"></a>Zobacz też

[Dodając parametry, które przetwarzają dane wejściowe wiersza polecenia](./adding-parameters-that-process-command-line-input.md)

[Tworzenie swojej pierwszej polecenia Cmdlet](./creating-a-cmdlet-without-parameters.md)

[Formatowanie i rozszerzanie typy obiektów](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Jak zarejestrować poleceń cmdlet, dostawców i aplikacji hosta](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Dokumentacja programu Windows PowerShell](../windows-powershell-reference.md)

[Przykłady polecenia cmdlet](./cmdlet-samples.md)
