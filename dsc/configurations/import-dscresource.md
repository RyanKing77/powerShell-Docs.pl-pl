---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguracja, instalacja
title: Używanie polecenia Import-DSCResource
ms.openlocfilehash: e1c2c06d756a70c2de516f330e3123235ce740ba
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215409"
---
# <a name="using-import-dscresource"></a>Używanie polecenia Import-DSCResource

`Import-DScResource`jest dynamicznym słowem kluczowym, którego można używać tylko wewnątrz bloku skryptu konfiguracji. `Import-DSCResource` Słowo kluczowe służące do importowania wszelkich zasobów wymaganych w konfiguracji. Zasoby w `$pshome` obszarze są importowane automatycznie, ale nadal jest uważane za najlepsze rozwiązanie do jawnego importowania wszystkich zasobów używanych w [konfiguracji](Configurations.md).

Składnia dla `Import-DSCResource` jest pokazana poniżej.  W przypadku określania modułów według nazwy jest wymagane, aby wyświetlić każdą z nich w nowym wierszu.

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|Parametr  |Opis  |
|---------|---------|
|`-Name`|Nazwy zasobów DSC, które należy zaimportować. Jeśli nazwa modułu jest określona, polecenie wyszukuje te zasoby DSC w ramach tego modułu; w przeciwnym razie polecenie przeszukuje zasoby DSC we wszystkich ścieżkach zasobów DSC. Symbole wieloznaczne są obsługiwane.|
|`-ModuleName`|Nazwa modułu lub Specyfikacja modułu.  W przypadku określenia zasobów do zaimportowania z modułu polecenie spowoduje próbę zaimportowania tylko tych zasobów. Jeśli określisz tylko moduł, polecenie importuje wszystkie zasoby DSC w module.|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a>Przykład: Używanie elementu import-DSCResource w konfiguracji

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration -Name Service, File, Registry
    
    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    # As a best practice, list each requirement on a different line if possible.  This makes reviewing
    # multiple changes in source control a bit easier.
    Import-DSCResource -Name File
    Import-DSCResource -Name TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    # When specifying the modulename parameter, it is a requirement to list each on a new line.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
    Import-DSCResource -ModuleName ComputerManagementDsc
...
```

> [!NOTE]
> Określanie wielu wartości nazw zasobów i nazw modułów w tym samym poleceniu nie jest obsługiwane. Może mieć niedeterministyczne zachowanie dotyczące tego, który zasób jest ładowany, z którego modułu w przypadku tego samego zasobu istnieje w wielu modułach. Poniższe polecenie spowoduje błąd podczas kompilacji.
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

Kwestie, które należy wziąć pod uwagę w przypadku używania tylko parametru name:

- Jest to operacja intensywnie korzystająca z zasobów w zależności od liczby modułów zainstalowanych na komputerze.
- Zostanie załadowany pierwszy znaleziony zasób o podaną nazwę. W przypadku, gdy zainstalowano więcej niż jeden zasób o tej samej nazwie, może załadować niewłaściwy zasób.

Zalecanym użyciem jest określenie `–ModuleName` `-Name` parametru z parametrem, zgodnie z poniższym opisem.

To użycie ma następujące zalety:

- Zmniejsza to wpływ na wydajność, ograniczając zakres wyszukiwania dla określonego zasobu.
- Jawnie definiuje moduł definiujący zasób, upewniając się, że jest ładowany prawidłowy zasób.

> [!NOTE]
> W programie PowerShell 5,0 zasoby DSC mogą mieć wiele wersji, a wersje można instalować na komputerze obok siebie. Jest to implementowane przez posiadanie wielu wersji modułu zasobów, które znajdują się w tym samym folderze modułu.
> Aby uzyskać więcej informacji, zobacz [Korzystanie z zasobów z wieloma wersjami](sxsresource.md).

## <a name="intellisense-with-import-dscresource"></a>Technologia IntelliSense z usługą import-DSCResource

Podczas tworzenia konfiguracji DSC w programie ISE program PowerShell udostępnia IntelliSence dla zasobów i właściwości zasobów. Definicje zasobów w `$pshome` ścieżce modułu są ładowane automatycznie. Po zaimportowaniu zasobów przy `Import-DSCResource` użyciu słowa kluczowego określone definicje zasobów są dodawane, a funkcja IntelliSense jest rozwinięta, aby uwzględnić schemat zaimportowanego zasobu.

![Technologia IntelliSense zasobów](../media/resource-intellisense.png)

> [!NOTE]
> Począwszy od programu PowerShell 5,0, uzupełnianie kart zostało dodane do ISE dla zasobów DSC i ich właściwości. Aby uzyskać więcej informacji, zobacz [zasoby](../resources/resources.md).

Podczas kompilowania konfiguracji program PowerShell używa zaimportowanych definicji zasobów do walidacji wszystkich bloków zasobów w konfiguracji.
Każdy blok zasobów jest sprawdzany przy użyciu definicji schematu zasobu dla następujących reguł.

- Używane są tylko właściwości zdefiniowane w schemacie.
- Typy danych dla każdej właściwości są poprawne.
- Określono właściwości kluczy.
- Nie jest używana właściwość tylko do odczytu.
- Sprawdzanie poprawności typów map wartości.

Weź pod uwagę następującą konfigurację:

```powershell
Configuration SchemaValidationInCorrectEnumValue
{
    # It is best practice to explicitly import all resources used in your Configuration.
    # This includes resources that are imported automatically, like WindowsFeature.
    Import-DSCResource -Name WindowsFeature
    Node localhost
    {
        WindowsFeature ROLE1
        {
            Name = “Telnet-Client”
            Ensure = “Invalid”
        }
    }
}
```

Skompilowanie tej konfiguracji spowoduje wystąpienie błędu.

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

Funkcja IntelliSense i sprawdzanie poprawności schematu umożliwiają przechwytywanie większej liczby błędów podczas analizowania i kompilowania, unikając komplikacji w czasie wykonywania.

> [!NOTE]
> Każdy zasób DSC może mieć nazwę i **FriendlyName** zdefiniowane przez schemat zasobu. Poniżej znajdują się pierwsze dwa wiersze pliku "MSFT_ServiceResource. Shema. MOF".
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> W przypadku korzystania z tego zasobu w konfiguracji można określić **MSFT_ServiceResource** lub **usługę**.

## <a name="powershell-v4-and-v5-differences"></a>Różnice w programie PowerShell w wersji 4 i 5

Istnieje wiele różnic, które są widoczne podczas tworzenia konfiguracji w programie PowerShell 4,0 a Program PowerShell 5,0 i nowsze. W tej sekcji zostaną wyróżnione różnice, które są odpowiednie dla tego artykułu.

### <a name="multiple-resource-versions"></a>Wiele wersji zasobów

Instalowanie i używanie wielu wersji zasobów obok siebie nie jest obsługiwane w programie PowerShell 4,0. Jeśli zauważysz problemy z importowaniem zasobów do konfiguracji, upewnij się, że zainstalowano tylko jedną wersję zasobu.

Na poniższym obrazie zainstalowano dwie wersje modułu **xPSDesiredStateConfiguration** .

![Rozwiązano wiele wersji zasobów](../media/multiple-resource-versions-broken.png)

Skopiuj zawartość żądanej wersji modułu do najwyższego poziomu katalogu modułów.

![Rozwiązano wiele wersji zasobów](../media/multiple-resource-versions-fixed.png)

### <a name="resource-location"></a>Lokalizacja zasobu

Podczas tworzenia i kompilowania konfiguracji zasoby mogą być przechowywane w dowolnym katalogu określonym przez [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path). W programie PowerShell 4,0 LCM wymaga, aby wszystkie moduły zasobów DSC były przechowywane w obszarze "program Files\WindowsPowerShell\Modules" `$pshome\Modules`lub. Począwszy od programu PowerShell 5,0, to wymaganie zostało usunięte, a moduły zasobów mogą być przechowywane w dowolnym katalogu `PSModulePath`określonym przez.

## <a name="see-also"></a>Zobacz też

- [Zasoby](../resources/resources.md)
