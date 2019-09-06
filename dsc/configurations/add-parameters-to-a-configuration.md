---
ms.date: 12/12/2018
keywords: DSC, PowerShell, zasób, Galeria, konfiguracja
title: Dodawanie parametrów do konfiguracji
ms.openlocfilehash: 72e6c15593d11ed39d7fe8ea79f794089f410cf8
ms.sourcegitcommit: d1ba596f9e0d4df9565601a70687a126d535c917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2019
ms.locfileid: "70386315"
---
# <a name="add-parameters-to-a-configuration"></a>Dodawanie parametrów do konfiguracji

Podobnie jak w przypadku funkcji, [konfiguracje](configurations.md) mogą być sparametryzowane, aby umożliwić większą konfigurację dynamiczną na podstawie danych wejściowych użytkownika. Kroki są podobne do tych opisanych w [funkcjach z parametrami](/powershell/module/microsoft.powershell.core/about/about_functions).

Ten przykład rozpoczyna się od podstawowej konfiguracji, która konfiguruje "bufor" usługi jako "uruchomiona".

```powershell
Configuration TestConfig
{
    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}
```

## <a name="built-in-configuration-parameters"></a>Wbudowane parametry konfiguracji

W przeciwieństwie do funkcji chociaż atrybut [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) nie dodaje żadnych funkcji. Oprócz [typowych parametrów](/powershell/module/microsoft.powershell.core/about/about_commonparameters)konfiguracje mogą również używać następujących wbudowanych parametrów, bez konieczności definiowania ich.

|Parametr  |Opis  |
|---------|---------|
|`-InstanceName`|Używane do definiowania [konfiguracji złożonych](compositeconfigs.md)|
|`-DependsOn`|Używane do definiowania [konfiguracji złożonych](compositeconfigs.md)|
|`-PSDSCRunAsCredential`|Używane do definiowania [konfiguracji złożonych](compositeconfigs.md)|
|`-ConfigurationData`|Służy do przekazywania [danych konfiguracji](configData.md) strukturalnej do użycia w konfiguracji.|
|`-OutputPath`|Służy do określania miejsca, w\<którym\>zostanie skompilowany plik "ComputerName. MOF"|

## <a name="adding-your-own-parameters-to-configurations"></a>Dodawanie własnych parametrów do konfiguracji

Oprócz wbudowanych parametrów można także dodać własne parametry do konfiguracji. Blok parametrów przechodzi bezpośrednio wewnątrz deklaracji konfiguracji, podobnie jak funkcja. Blok parametrów konfiguracyjnych powinien znajdować się poza deklaracjami **węzłów** i przekraczać wszystkie instrukcje *importu* . Dodając parametry, można sprawić, aby konfiguracje były bardziej niezawodne i dynamiczne.

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a>Dodaj parametr ComputerName

Pierwszy parametr, który można dodać, to `-Computername` parametr, dzięki czemu można dynamicznie kompilować plik ". MOF" dla każdego `-Computername` przekazanego do konfiguracji. Podobnie jak funkcje, można również zdefiniować wartość domyślną, na wypadek, gdy użytkownik nie przekaże wartości dla`-ComputerName`

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

W ramach konfiguracji można określić `-ComputerName` parametr podczas definiowania bloku węzła.

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a>Wywoływanie konfiguracji za pomocą parametrów

Po dodaniu parametrów do konfiguracji można użyć ich w taki sam sposób, jak w przypadku polecenia cmdlet.

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a>Kompilowanie wielu plików MOF

Blok węzła może również akceptować rozdzieloną przecinkami listę nazw komputerów i generować pliki "MOF" dla każdego z nich. Poniższy przykład umożliwia wygenerowanie plików "MOF" dla wszystkich komputerów przewidzianych do `-ComputerName` parametru.

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}

TestConfig -ComputerName "server01", "server02", "server03"
```

## <a name="advanced-parameters-in-configurations"></a>Zaawansowane parametry w konfiguracjach

Oprócz `-ComputerName` parametru można dodać parametry dla nazwy usługi i stanu. Poniższy przykład dodaje blok parametrów z `-ServiceName` parametrem i używa go do dynamicznego definiowania bloku zasobów **usługi** . Dodaje `-State` również parametr do dynamicznego definiowania **stanu** w bloku zasobów **usługi** .

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ServiceName,

        [String]
        $State,

        [String]
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

> [!NOTE]
> W większej liczbie scenariuszy advacned może być bardziej zrozumiałe przeniesienie danych dynamicznych do [danych konfiguracji](configData.md)strukturalnej.

Przykładowa konfiguracja ma teraz wartość dynamiczną `$ServiceName`, ale jeśli nie zostanie określona, kompilacja powoduje wystąpienie błędu. Możesz dodać wartość domyślną, jak w tym przykładzie.

```powershell
[String]
$ServiceName="Spooler"
```

W tym wystąpieniu sprawiasz, że po prostu wymusisz, że użytkownik może określić wartość `$ServiceName` parametru. Ten `parameter` atrybut umożliwia dodanie dalszej obsługi weryfikacji i potoku do parametrów konfiguracji.

Przed dowolnymi deklaracjami parametrów `parameter` Dodaj blok atrybutu jak w poniższym przykładzie.

```powershell
[parameter()]
[String]
$ServiceName
```

Można określić argumenty dla każdego `parameter` atrybutu, aby kontrolować aspekty zdefiniowanego parametru. Poniższy przykład wykonuje `$ServiceName` parametr **obowiązkowy** .

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

Dla parametru, chcemy uniemożliwić użytkownikowi Określanie wartości spoza wstępnie zdefiniowanego zestawu (na przykład uruchomionego, zatrzymanego), `ValidationSet*`aby użytkownik mógł określić wartości spoza wstępnie zdefiniowanego zestawu (na przykład uruchomione, `$State` Zatrzymane). Poniższy przykład dodaje `ValidationSet` atrybut `$State` do parametru. Ponieważ nie chcemy, aby `$State` parametr był **obowiązkowy**, należy dodać do niego wartość domyślną.

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> Nie trzeba określać `parameter` atrybutu przy `validation` użyciu atrybutu.

Więcej informacji na temat `parameter` atrybutów i poprawności można znaleźć w [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters).

## <a name="fully-parameterized-configuration"></a>Pełna konfiguracja sparametryzowanej

Mamy teraz konfigurację sparametryzowanej, która wymusza użytkownikowi określenie `-InstanceName`, `-ServiceName`i sprawdza poprawność `-State` parametru.

```powershell
Configuration TestConfig
{
    param
    (
        [parameter(Mandatory)]
        [String]
        $ServiceName,

        [ValidateSet("Running","Stopped")]
        [String]
        $State="Running",

        [String]
        $ComputerName="localhost",
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

## <a name="see-also"></a>Zobacz też

- [Pomoc dotycząca zapisu konfiguracji DSC](configHelp.md)
- [Konfiguracje dynamiczne](flow-control-in-configurations.md)
- [Używanie danych konfiguracji w konfiguracjach](configData.md)
- [Oddziel dane dotyczące konfiguracji i środowiska](separatingEnvData.md)
