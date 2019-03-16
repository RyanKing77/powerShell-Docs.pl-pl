---
title: Dodawanie aliasy, rozszerzenia symboli wieloznacznych i pomocy do parametrów polecenia Cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: db664e589f625855b5a33a02c522d6b238ad2810
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054883"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a>Dodawanie aliasów, rozszerzenia symboli wieloznacznych i pomocy do parametrów polecenia cmdlet

W tej sekcji opisano sposób dodawania aliasów i rozwijanie symbolu wieloznacznego i pomocy wiadomości do parametrów polecenia cmdlet Stop-Proc (opisanego w [Tworzenie polecenia Cmdlet, który modyfikuje System](./creating-a-cmdlet-that-modifies-the-system.md)).

To polecenie cmdlet Stop-Proc podejmuje próby zatrzymania procesów, które są pobierane za pomocą polecenia cmdlet Get-Proc (opisanego w [tworzenia Your pierwsze polecenie Cmdlet](./creating-a-cmdlet-without-parameters.md)).

Tematy w tej sekcji są następujące:

- [Definiowanie polecenia cmdlet](#Defining-the-Cmdlet)

- [Definiowanie parametrów modyfikacji systemu](#Defining-Parameters-for-System-Modification)

- [Definiowanie aliasu parametru](#Defining-a-Parameter-Alias)

- [Tworzenie pomocy dotyczącej parametrów](#Creating-Help-for-Parameters)

- [Zastępowanie metody przetwarzania danych wejściowych](#Overriding-an-Input-Processing-Method)

- [Obsługa rozszerzenia symboli wieloznacznych](#Supporting-Wildcard-Expansion)

- [Przykładowy kod](#Defining-a-Parameter-Alias)

- [Definiowanie typów obiektów i formatowanie](#Define-Object-Types-and-Formatting)

- [Tworzenie polecenia cmdlet](#Building-the-Cmdlet)

- [Testowanie polecenia cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>Definiowanie polecenia cmdlet

Pierwszym krokiem w procesie tworzenia polecenia cmdlet jest zawsze nazewnictwa polecenia cmdlet i deklarowanie klasy .NET, która implementuje polecenia cmdlet. Ponieważ piszesz polecenia cmdlet, aby zmienić system powinien zostać nazwany odpowiednio. Ponieważ to polecenie cmdlet zatrzymuje procesów systemowych, używa ona czasownik "Stop" zdefiniowany przez [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) klasy z rzeczownikiem "Proc", aby wskazać proces. Aby uzyskać więcej informacji na temat polecenia cmdlet zatwierdzonych czasowników, zobacz [nazwy zlecenie poleceń Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Poniższy kod jest w definicji klasy dla tego polecenia cmdlet Stop-Proc.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Definiowanie parametrów modyfikacji systemu

Twoje polecenie cmdlet musi definiować parametry tej modyfikacji systemu pomocy technicznej i opinie użytkowników. Polecenia cmdlet należy zdefiniować `Name` parametru lub równoważnej, aby polecenie cmdlet będzie można zmodyfikować system jakieś identyfikatora. Ponadto, polecenie cmdlet należy zdefiniować `Force` i `PassThru` parametrów. Aby uzyskać więcej informacji na temat tych parametrów, zobacz [Tworzenie polecenia Cmdlet, który modyfikuje System](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="defining-a-parameter-alias"></a>Definiowanie aliasu parametru

Alias parametru może być alternatywną nazwę lub dobrze zdefiniowanych 1 literę lub litery 2 krótkiej nazwy parametru polecenia cmdlet. W obu przypadkach celem aliasy użycia jest uproszczenie wpisu użytkownika z wiersza polecenia. Windows PowerShell obsługuje aliasów parametrów za pomocą [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) atrybut, który używa składni deklaracji [Alias()].

W poniższym kodzie pokazano, jak aliasu jest dodawany do `Name` parametru.

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
[Alias("ProcessName")]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

Oprócz używania [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) atrybutu, programu Windows PowerShell środowisko uruchomieniowe wykonuje dopasowanie części nazwy, nawet, jeśli nie określono żadnych aliasów. Na przykład Twoje polecenie cmdlet ma `FileName` parametr a to znaczy jedynym parametrem, który rozpoczyna się od `F`, użytkownik może wprowadzić `Filename`, `Filenam`, `File`, `Fi`, lub `F` i nadal rozpoznaje wpis `FileName` parametru.

## <a name="creating-help-for-parameters"></a>Tworzenie pomocy dotyczącej parametrów

Program Windows PowerShell umożliwia tworzenie pomocy dla parametrów polecenia cmdlet. W tym przypadku każdego parametru używany do modyfikacji i użytkownika informacje zwrotne z systemu. Dla każdego parametru do obsługi pomocy można ustawić `HelpMessage` atrybutu — słowo kluczowe w [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) deklaracji atrybutu. This — słowo kluczowe definiuje tekst do wyświetlenia dla użytkownika, aby uzyskać pomoc przy użyciu parametru. Można również ustawić `HelpMessageBaseName` — słowo kluczowe, aby zidentyfikować podstawowej nazwy zasobu dla wiadomości. Jeśli ustawisz to słowo kluczowe, należy także ustawić `HelpMessageResourceId` — słowo kluczowe, aby określić identyfikator zasobu.

Poniższy kod z tego polecenia cmdlet Stop-Proc definiuje `HelpMessage` atrybutu słowo kluczowe `Name` parametru.

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
```

## <a name="overriding-an-input-processing-method"></a>Zastępowanie metody przetwarzania danych wejściowych

Twojego polecenia cmdlet jest przesłonięcie metody przetwarzania danych wejściowych, w większości przypadków będzie to [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). Podczas modyfikowania systemu, polecenia cmdlet powinny wywoływać [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) i [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metody, aby umożliwić użytkownikowi Aby przekazać opinię, zanim zostanie zmienione. Aby uzyskać więcej informacji o tych metodach, zobacz [Tworzenie polecenia Cmdlet, który modyfikuje System](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="supporting-wildcard-expansion"></a>Obsługa rozszerzenia symboli wieloznacznych

Aby umożliwić zaznaczanie wielu obiektów, można użyć Twojego polecenia cmdlet [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) i [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) klasy zapewniające Obsługa rozszerzenia symboli wieloznacznych dla parametrów wejściowych. Przykłady wzorców symboli wieloznacznych lsa * \*txt i [a-c]\*. Gdy wzorzec zawiera znak, który ma zostać użyty dosłownie, użyj znaków cudzysłowu Wstecz (') jako znak ucieczki.

Symbol wieloznaczny rozszerzenia nazwy pliku i ścieżka są przykłady typowych scenariuszy, w których polecenia cmdlet mogą być Zezwalaj na obsługę ścieżki w danych wejściowych, gdy wymagany jest wybór wielu obiektów. Często zdarza się w systemie plików, w których użytkownik chce, aby wyświetlić wszystkie pliki znajdujące się w bieżącym folderze.

Tylko rzadko należy implementacji dopasowania wzorca dostosowane symboli wieloznacznych. W tym przypadku Twojego polecenia cmdlet powinien obsługiwać pełną 1003.2 POSIX, 3.13 specyfikacji dla rozszerzenia symboli wieloznacznych lub następujące podzbioru uproszczone:

- **Znak zapytania (?).** Dopasowuje dowolny znak w określonej lokalizacji.

- **Gwiazdka (\*).** Dopasowuje zero lub więcej znaków, zaczynając od określonej lokalizacji.

- **Otwierającego nawiasu ([]).** Wprowadza wzorzec wyrażenie w nawiasie kwadratowym, który może zawierać znaków lub zakres znaków. Jeśli zakres jest wymagany, łącznika (-) jest używany do wskazania zakresu.

- **Zamknij nawiasu (]).** Kończy się wzorzec wyrażenie w nawiasie kwadratowym.

- **Oferta wstecz znaku ucieczki (').** Wskazuje, że następny znak należy podjąć dosłownie. Należy pamiętać, że podczas określania znaku cudzysłowu Wstecz, z poziomu wiersza polecenia (w przeciwieństwie do określenia programowo), znaku ucieczki wstecz oferty należy określić dwa razy.

> [!NOTE]
> Aby uzyskać więcej informacji na temat wzorców symboli wieloznacznych, zobacz [obsługi symboli wieloznacznych w parametrach polecenia Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).

Poniższy kod pokazuje, jak ustawić opcje symboli wieloznacznych i zdefiniuj wzór symboli wieloznacznych, używany do rozpoznawania `Name` parametrów dla tego polecenia cmdlet.

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

Poniższy kod przedstawia sposób testowania, czy nazwa procesu jest zgodny ze wzorcem zdefiniowanych symboli wieloznacznych. Zwróć uwagę, że w tym przypadku jeśli nazwa procesu nie jest zgodna z wzorcem, polecenia cmdlet w dalszym ciągu na Pobierz dalej nazwę procesu.

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a>Przykładowy kod

Aby uzyskać pełne C# przykładowego kodu, zobacz [przykładowe StopProcessSample03](./stopprocesssample03-sample.md).

## <a name="define-object-types-and-formatting"></a>Zdefiniuj typy obiektów i formatowanie

Program Windows PowerShell przekazuje informacje między poleceniami cmdlet, używając obiektów platformy .net. W związku z tym polecenie cmdlet może być konieczne zdefiniowanie swój własny typ, lub polecenie cmdlet może być konieczne rozszerzyć istniejący typ dostarczane przez inne polecenie cmdlet. Aby uzyskać więcej informacji na temat definiowania nowych typów lub rozszerzanie istniejących typów, zobacz [rozszerzanie typów obiektów i formatowanie](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Tworzenie polecenia cmdlet

Po zaimplementowaniu polecenia cmdlet, musi być zarejestrowana przy użyciu programu Windows PowerShell za pomocą przystawki programu Windows PowerShell. Aby uzyskać więcej informacji na temat rejestrowania poleceń cmdlet, zobacz [sposób zarejestrować poleceń cmdlet, dostawców i hostowania aplikacji](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testowanie polecenia cmdlet

Po zarejestrowaniu Twojego polecenia cmdlet przy użyciu programu Windows PowerShell można ją przetestować, uruchamiając go w wierszu polecenia. Teraz przetestuj przykładowe polecenie cmdlet Stop-Proc. Aby uzyskać więcej informacji o korzystaniu z poleceń cmdlet w wierszu polecenia, zobacz [wprowadzenie do programu Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Uruchom program Windows PowerShell i użyj Stop-Proc, aby zatrzymać proces przy użyciu ProcessName alias `Name` parametru.

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

Zostanie wyświetlone następujące dane wyjściowe.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- W wierszu polecenia, należy wprowadzić poniższy wpis. Parametr Name jest obowiązkowy, zostanie wyświetlony monit o jej. Wprowadzanie "!" wyświetlenie tekstu pomocy skojarzonych z parametrem.

    ```powershell
    PS> stop-proc
    ```

Zostanie wyświetlone następujące dane wyjściowe.

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- Teraz wprowadź następujący wpis, aby zatrzymać wszystkie procesy, które pasuje do wzorca symbol wieloznaczny "* Uwaga\*". Zostanie wyświetlony monit przed zatrzymaniem każdy proces, który pasuje do wzorca.

    ```powershell
    PS> stop-proc -Name *note*
    ```

Zostanie wyświetlone następujące dane wyjściowe.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

Zostanie wyświetlone następujące dane wyjściowe.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

Zostanie wyświetlone następujące dane wyjściowe.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Zobacz też

[Tworzenie polecenia Cmdlet, który modyfikuje systemu](./creating-a-cmdlet-that-modifies-the-system.md)

[Jak utworzyć polecenia Cmdlet programu Windows PowerShell](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Formatowanie i rozszerzanie typy obiektów](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Jak zarejestrować poleceń cmdlet, dostawców i aplikacji hosta](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Obsługa symboli wieloznacznych w parametry polecenia Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)
