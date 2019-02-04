---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Używanie polecenia Import-DSCResource
ms.openlocfilehash: 6bc3c1aa1d34a05e3188666da825322235c0672e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686614"
---
# <a name="using-import-dscresource"></a>Używanie polecenia Import-DSCResource

`Import-DScResource` jest dynamiczne słowo kluczowe, które można używać tylko wewnątrz bloku skryptu konfiguracji. `Import-DSCResource` — Słowo kluczowe, aby zaimportować wszystkie zasoby potrzebne w danej konfiguracji. Zasobów w ramach `$phsome` są importowane automatycznie, ale nadal jest uważany za najlepszym rozwiązaniem, aby jawnie importujesz wszelkie zasoby używane w Twojej [konfiguracji](Configurations.md).

Składnia `Import-DSCResource` znajdują się poniżej.

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>]
```

|Parametr  |Opis  |
|---------|---------|
|`-Name`|Nazwy zasobów DSC, należy zaimportować. Jeśli nazwa modułu jest określony, polecenie wyszukuje te zasoby DSC, w tym module; w przeciwnym razie polecenie przeszukuje zasoby DSC w wszystkich ścieżek zasobów DSC. Symbole wieloznaczne są obsługiwane.|
|`-ModuleName`|Nazwy modułu kontenera lub specyfikacje modułu.  Jeśli określisz zasoby do zaimportowania z modułu, polecenie podejmie próbę importowanie tylko tych zasobów. Jeśli określisz tylko moduł, polecenie importuje wszystkie zasoby DSC w module.|

Można używać symboli wieloznacznych, za pomocą `-Name` parametru w przypadku korzystania z `Import-DSCResource`.

```powershell
Import-DscResource -Name * -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a>Przykład: Użyj Import-DSCResource w ramach konfiguracji

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName MS_DSC1 -name Service, File, Registry

    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    Import-DSCResource -Name File, TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
...
```

> [!NOTE]
> Określanie wielu wartości dla nazwy zasobów i moduły w tym samym poleceniu nie są obsługiwane. Może mieć niedeterministyczne zachowanie dotyczące zasobu, który można załadować z modułu, którego, w przypadku, gdy ten sam zasób istnieje wiele modułów. Poniższego polecenia spowoduje błąd podczas kompilacji.
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

Warto wziąć pod uwagę podczas korzystania z parametr Name:

- Jest to operacja intensywnie korzystających z zasobów, w zależności od liczby modułów zainstalowanych na komputerze.
- Będzie on ładować się pierwszy zasób znaleziono o podanej nazwie. W przypadku, gdy istnieje więcej niż jeden zasób o takiej samej nazwie, zainstalowane, można załadować niewłaściwych zasobów.

Użycie zalecane jest, aby określić `–ModuleName` z `-Name` parametru, zgodnie z poniższym opisem.

Użycie tych ma następujące zalety:

- Zmniejsza to negatywny wpływ na wydajność, ograniczając zakres wyszukiwania dla określonego zasobu.
- Jawnie definiuje moduł definiowania zasobu, zapewnienie, że właściwy zasób jest ładowany.

> [!NOTE]
> W programie PowerShell 5.0 zasoby DSC może mieć wiele wersji i wersje, które można zainstalować na komputerze side-by-side. To jest implementowany przez korzystanie z kilku wersji moduł zasobów, które są zawarte w tym samym folderze modułu.
> Aby uzyskać więcej informacji, zobacz [korzystanie z zasobów z wieloma wersjami](sxsresource.md).

## <a name="intellisense-with-import-dscresource"></a>Funkcja IntelliSense z Import-DSCResource

Podczas tworzenia konfiguracji DSC w środowisku ISE, program PowerShell udostępnia IntelliSence dla zasobów i właściwości zasobów. Definicje zasobów w ramach `$pshome` ścieżka modułu są ładowane automatycznie. Podczas importowania zasobów przy użyciu `Import-DSCResource` — słowo kluczowe, definicje określonego zasobu zostaną dodane, a funkcja Intellisense jest rozwinięta i obejmuje schemat importowanych zasobów.

![Funkcja Intellisense zasobów](/media/resource-intellisense.png)

> [!NOTE]
> Począwszy od programu PowerShell w wersji 5.0, dodano uzupełnianie po naciśnięciu tabulatora ISE dla zasobów DSC oraz ich właściwości. Aby uzyskać więcej informacji, zobacz [zasobów](../resources/resources.md).

Podczas kompilowania konfiguracji, programu PowerShell używa definicji zasobów zaimportowanych do sprawdzania poprawności wszystkich bloków zasobów w konfiguracji.
Każdy blok zasobu jest weryfikowana, za pomocą definicji schematu do zasobu, dla następujących reguł.

- Używane są tylko właściwości zdefiniowane w schemacie.
- Typy danych dla każdej właściwości są poprawne.
- Określono właściwości kluczy.
- Nie właściwości tylko do odczytu jest używany.
- Sprawdzanie poprawności na podstawie wartości mapowania typów.

Rozważmy następującą konfigurację:

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

Kompilowanie tej konfiguracji będzie skutkowało błędem.

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

Funkcja IntelliSense i schematu sprawdzania poprawności pozwalają przechwytywać więcej błędów podczas analizy i kompilacja, unikając kompilacji w czasie wykonywania.

> [!NOTE]
> Każdy zasób DSC może mieć nazwę, a **FriendlyName** definiowana przez schemat zasobu. Poniżej przedstawiono dwa pierwsze wiersze "MSFT_ServiceResource.shema.mof".
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> Korzystając z tego zasobu w konfiguracji, można określić **MSFT_ServiceResource** lub **usługi**.

## <a name="powershell-v4-and-v5-differences"></a>Różnice w wersji 4 i 5 programu PowerShell

Istnieje wiele różnice, które zobaczysz podczas tworzenia konfiguracji w programie PowerShell 4.0 vs. Program PowerShell 5.0 lub nowszy. W tej sekcji zostanie podkreślić różnice zostanie wyświetlony odpowiedni do tego artykułu.

### <a name="multiple-resource-versions"></a>Wiele wersji zasobu

Zainstalowanie i używanie wielu wersji obok siebie zasobów nie jest obsługiwana w programie PowerShell 4.0. Jeśli zauważysz problemów dotyczących importowania zasobów do konfiguracji, upewnij się, mieć tylko jedną wersję zasobu zainstalowane.

Na ilustracji poniżej dwie wersje **xPSDesiredStateConfiguration** moduł są zainstalowane.

![Wiele wersji zasobu, stała](/media/multiple-resource-versions-broken.md)

Skopiuj zawartość tej wersji żądany moduł najwyższego poziomu katalog modułu.

![Wiele wersji zasobu, stała](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a>Lokalizacja zasobu

Podczas tworzenia i kompilowanie konfiguracji, Twoje zasoby mogą być przechowywane w dowolnym katalogu określonego przez użytkownika [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path). W programie PowerShell 4.0 LCM wymaga wszystkie moduły zasobów DSC mają być przechowywane w obszarze "Program Files\WindowsPowerShell\Modules" lub `$pshome\Modules`. Począwszy od programu PowerShell w wersji 5.0, wymóg ten został usunięty i modułów zasoby mogą być przechowywane w dowolnym katalogu określonego przez `PSModulePath`.

## <a name="see-also"></a>Zobacz też

- [Zasoby](../resources/resources.md)
