---
ms.date: 12/12/2018
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Używanie polecenia Import-DSCResource
ms.openlocfilehash: f22c741969b1429074e7307a00a5c014cf563089
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2019
ms.locfileid: "56265505"
---
# <a name="using-import-dscresource"></a>Używanie polecenia Import-DSCResource

`Import-DScResource` jest słowem kluczowym dynamiczna, której można używać tylko wewnątrz bloku skryptu konfiguracji. `Import-DSCResource` — Słowo kluczowe, aby zaimportować wszystkie zasoby potrzebne w danej konfiguracji. Zasobów w ramach `$phsome` są importowane automatycznie, ale nadal jest uznawane za najlepszym rozwiązaniem jest jawnie zaimportować wszystkie zasoby używane w sieci [konfiguracji](Configurations.md).

Składnia `Import-DSCResource` są wyświetlane poniżej.  Podczas określania modułów według nazwy, jest wymagane do wyświetlenia każdego w nowym wierszu.

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|Parametr  |Opis  |
|---------|---------|
|`-Name`|Nazwy zasobów DSC należy zaimportować. Nazwa modułu jest określony, polecenie wyszukuje tych zasobów DSC modułu; w przeciwnym razie polecenie przeszukuje zasobów DSC wszystkie ścieżki zasobu usługi Konfiguracja DSC. Symbole wieloznaczne są obsługiwane.|
|`-ModuleName`|Nazwa modułu lub specyfikacji modułu.  Jeśli określisz zasoby do zaimportowania z modułu polecenia spróbuj zaimportować tylko tych zasobów. Jeśli określisz tylko moduł polecenie importuje wszystkie zasoby DSC w module.|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a>Przykład: Użyj DSCResource importu w konfiguracji

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
> Określanie wielu wartości dla nazw zasobów i modułów w tym samym poleceniu nie są obsługiwane. Może mieć deterministyczna zachowanie o zasobie, które można załadować z modułu, którego w przypadku, gdy ten sam zasób istnieje w wielu modułów. Poniżej polecenia spowoduje błąd podczas kompilacji.
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

Kwestie do rozważenia przy użyciu parametru Nazwa:

- Jest operacją intensywnie w zależności od liczby modułów zainstalowanych na komputerze.
- Go zostanie załadowany pierwszy zasób znaleziono o podanej nazwie. W przypadku, jeśli istnieje więcej niż jeden zasób o tej samej nazwie zainstalowana, można załadować niewłaściwego zasobu.

Użycie zalecane jest określenie `–ModuleName` z `-Name` parametru, zgodnie z poniższym opisem.

To użycie ma następujące zalety:

- Zmniejsza wpływ na wydajność dzięki ograniczeniu liczby zakres wyszukiwania dla określonego zasobu.
- Definiuje jawnie modułu definiowania zasobów, zapewnienie, że właściwy zasób został załadowany.

> [!NOTE]
> W programie PowerShell 5.0 DSC zasobów może mieć wiele wersji, a wersji można zainstalować na komputerze side-by-side. Ten sposób jest implementowany przez korzystanie z kilku wersji moduł zasobów, które są zawarte w tym samym folderze modułu.
> Aby uzyskać więcej informacji, zobacz [przy użyciu zasobów z wieloma wersjami](sxsresource.md).

## <a name="intellisense-with-import-dscresource"></a>IntelliSense z DSCResource importu

Podczas tworzenia konfiguracji DSC w ISE programu PowerShell zawiera IntelliSence zasobów i właściwości zasobów. Definicje zasobów w obszarze `$pshome` ścieżka modułu są ładowane automatycznie. Podczas importowania zasobów przy użyciu `Import-DSCResource` — słowo kluczowe, definicje określonego zasobu zostaną dodane i Intellisense jest rozszerzona w celu uwzględnienia schematu importowanego zasobu.

![Intellisense zasobów](/media/resource-intellisense.png)

> [!NOTE]
> Począwszy od programu PowerShell w wersji 5.0, dodano uzupełniania po naciśnięciu tabulatora ISE DSC zasobów i ich właściwości. Aby uzyskać więcej informacji, zobacz [zasobów](../resources/resources.md).

Podczas kompilowania konfiguracji, programu PowerShell używa definicji importowanego zasobu do sprawdzania poprawności wszystkich bloków zasobów w konfiguracji.
Każdy blok zasobów jest weryfikowane, za pomocą definicji schematu do zasobu, dla następujących reguł.

- Używane są tylko właściwości zdefiniowane w schemacie.
- Typy danych dla każdej właściwości są prawidłowe.
- Właściwości klucze są określone.
- Nie właściwości tylko do odczytu jest używany.
- Sprawdzanie poprawności na wartość mapowania typów.

Należy wziąć pod uwagę następującą konfigurację:

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

Kompilowanie tej konfiguracji powoduje błąd.

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

Funkcja IntelliSense i schemat sprawdzania poprawności umożliwiają efektywnej więcej błędów w czasie analizy i kompilacji, unikając komplikacji w czasie wykonywania.

> [!NOTE]
> Każdy zasób DSC może mieć nazwę, a **FriendlyName** zdefiniowane przez schemat zasobu. Poniżej przedstawiono dwa pierwsze wiersze "MSFT_ServiceResource.shema.mof".
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> Korzystając z tego zasobu w konfiguracji, można określić **MSFT_ServiceResource** lub **usługi**.

## <a name="powershell-v4-and-v5-differences"></a>Różnice w wersji 4 i v5 programu PowerShell

Różnią się wiele widocznej podczas tworzenia konfiguracji w programie vs PowerShell 4.0. PowerShell 5.0 i nowszych. W tej sekcji zostały wyróżnione różnice zostanie wyświetlony związane z tym artykułem.

### <a name="multiple-resource-versions"></a>Wiele wersji zasobów

Zainstalowanie i używanie wielu wersji obok siebie zasobów nie jest obsługiwana w programie PowerShell w wersji 4.0. Jeśli zauważysz problemy importowania zasobów do konfiguracji użytkownika, upewnij się, mieć tylko jedną wersję zasobu zainstalowane.

Na ilustracji poniżej dwie wersje **xPSDesiredStateConfiguration** moduł jest zainstalowany.

![Wiele wersji zasobów stałej](/media/multiple-resource-versions-broken.md)

Skopiuj zawartość tej wersji żądany moduł na najwyższym poziomie katalog modułu.

![Wiele wersji zasobów stałej](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a>Lokalizacja zasobu

Podczas tworzenia i kompilowanie konfiguracje, zasoby mogą być przechowywane w dowolnym katalogu określonego przez użytkownika [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path). W programie PowerShell w wersji 4.0 LCM wymaga wszystkie moduły zasobów DSC mają być przechowywane w obszarze "Program Files\WindowsPowerShell\Modules" lub `$pshome\Modules`. Począwszy od programu PowerShell w wersji 5.0, to wymaganie został usunięty, i modułów zasoby mogą być przechowywane w dowolnym katalogu określonego przez `PSModulePath`.

## <a name="see-also"></a>Zobacz też

- [Zasoby](../resources/resources.md)
