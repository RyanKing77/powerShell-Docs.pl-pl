---
ms.date: 12/12/2018
keywords: DSC, powershell, zasób, galerii, Instalator
title: Dodawanie parametrów do konfiguracji
ms.openlocfilehash: 15213404f0cdd6416baf1f83af91b8f5279cc97f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080260"
---
# <a name="add-parameters-to-a-configuration"></a>Dodawanie parametrów do konfiguracji

Funkcje, takie jak [konfiguracje](configurations.md) mogą być parametryzowane, aby umożliwić bardziej dynamiczne konfiguracje oparte na danych wejściowych użytkownika. Kroki są podobne do tych opisanych w [funkcje z parametrami](/powershell/module/microsoft.powershell.core/about/about_functions).

W tym przykładzie rozpoczyna się od podstawowej konfiguracji, który konfiguruje usługę "Buforu", "Działa".

```powershell
Configuration TestConfig
{
    # It is best practice to implicitly import any required resources or modules.
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

W przeciwieństwie do funkcji, [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) atrybut dodaje żadnych funkcji. Oprócz [wspólne parametry](/powershell/module/microsoft.powershell.core/about/about_commonparameters), konfiguracje można również użyć następujące wbudowane parametrów, bez konieczności ich.

|Parametr  |Opis  |
|---------|---------|
|`-InstanceName`|Używanego przy definiowaniu [złożonej konfiguracji](compositeconfigs.md)|
|`-DependsOn`|Używanego przy definiowaniu [złożonej konfiguracji](compositeconfigs.md)|
|`-PSDSCRunAsCredential`|Używanego przy definiowaniu [złożonej konfiguracji](compositeconfigs.md)|
|`-ConfigurationData`|Służy do przekazywania w strukturze [dane konfiguracyjne](configData.md) do użytku w konfiguracji.|
|`-OutputPath`|Pozwala określić, gdzie Twoje "\<computername\>MOF" zostanie skompilowany plik|

## <a name="adding-your-own-parameters-to-configurations"></a>Dodawanie własnych parametrów konfiguracji

Oprócz wbudowanych parametrów można również dodać własne parametry do konfiguracji. Blok parametrów przechodzi bezpośrednio wewnątrz deklaracji konfiguracji, podobnie jak funkcja. Blok parametrów konfiguracji powinien znajdować się poza dowolne **węzła** deklaracji i nowszych dowolne *zaimportować* instrukcji. Dodając parametry, można tworzyć konfiguracje bardziej niezawodnych i dynamicznych.

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a>Dodaj parametr nazwa_komputera

Pierwszy parametr, można dodać jest `-Computername` parametru, więc możesz dynamicznie skompilować pliku "MOF" dla każdego `-Computername` przekazać do konfiguracji. Takie jak Functions można również zdefiniować wartość domyślna w przypadku, gdy użytkownik nie przekaże wartości `-ComputerName`

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

W ramach konfiguracji, możesz określić swoje `-ComputerName` parametru podczas definiowania bloku z węzła.

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a>Wywoływanie konfigurację z parametrami

Po dodaniu parametry konfiguracji, można je tak, jak za pomocą polecenia cmdlet.

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a>Kompilowanie wielu plików MOF

Blok węzła także zaakceptować wartość rozdzielaną przecinkami listę nazw komputerów i będzie generować pliki "MOF" dla każdego. Można uruchomić poniższy przykład, aby wygenerować pliki "MOF" dla wszystkich komputerów, przekazywane do `-ComputerName` parametru.

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
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

## <a name="advanced-parameters-in-configurations"></a>Zaawansowane parametry w konfiguracji

Oprócz `-ComputerName` parametru, możemy dodać parametry dla nazwy usługi i stanu. Poniższy przykład umożliwia dodanie bloku parametrów, za pomocą `-ServiceName` parametru i używa go w celu dynamicznego definiowania **usługi** bloku zasobów. Dodaje także `-State` parametr w celu dynamicznego definiowania **stanu** w **usługi** bloku zasobów.

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

    # It is best practice to implicitly import any required resources or modules.
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
> W dalszych scenariuszach advacned, może być bardziej zrozumiałe, aby przenieść dane dynamiczne do ze strukturą [dane konfiguracyjne](configData.md).

Przykład konfiguracji teraz przyjmuje dynamiczny `$ServiceName`, ale jeśli nie jest określony, kompilacja będzie skutkowało błędem. Można dodać wartość domyślną, np. w tym przykładzie.

```powershell
[String]
$ServiceName="Spooler"
```

W tym wystąpieniu, więcej sensu można po prostu zmusza użytkownika do określenia wartości `$ServiceName` parametru. `parameter` Atrybut można dodawać dodatkowe sprawdzanie poprawności i potoku obsługi parametrów konfiguracji użytkownika.

Nad dowolnym deklaracji parametru Dodaj `parameter` bloku attribute, tak jak w poniższym przykładzie.

```powershell
[parameter()]
[String]
$ServiceName
```

Można określić argumenty do każdego `parameter` atrybutu do sterowania aspektami zdefiniowany parametr. Poniższy przykład wykonuje `$ServiceName` **obowiązkowe** parametru.

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

Dla `$State` parametru, prosimy o poświęcenie zapobiec określania wartości poza zestaw wstępnie zdefiniowanych przez użytkownika (takie jak uruchamianie, zatrzymane) `ValidationSet*`atrybut może uniemożliwić użytkownikowi korzystanie ze określania wartości poza zestaw wstępnie zdefiniowanych (na przykład działanie Zatrzymana). W poniższym przykładzie dodano `ValidationSet` atrybutu `$State` parametru. Ponieważ nie chcemy mieć `$State` parametru **obowiązkowe**, musimy dodać wartość domyślną dla niego.

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> Nie należy określić `parameter` atrybutu przy użyciu `validation` atrybutu.

Przeczytaj więcej o `parameter` i sprawdzanie poprawności atrybutów w [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).

## <a name="fully-parameterized-configuration"></a>W pełni sparametryzowane konfiguracji

W efekcie powstał sparametryzowane konfigurację, która wymusza użytkownikowi na określenie `-InstanceName`, `-ServiceName`i sprawdza poprawność `-State` parametru.

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

    # It is best practice to implicitly import any required resources or modules.
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

- [Zapis pomocy dotyczących konfiguracji DSC](configHelp.md)
- [Dynamiczne konfiguracje](flow-control-in-configurations.md)
- [Korzystanie z danych konfiguracji w konfiguracji](configData.md)
- [Osobne dane konfiguracji i środowiska](separatingEnvData.md)
