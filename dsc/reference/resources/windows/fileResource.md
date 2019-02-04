---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób DSC plików
ms.openlocfilehash: b5bc2c305b8cfccbd044274811df631264a24279
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688427"
---
# <a name="dsc-file-resource"></a>Zasób DSC plików

> Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0

Zasób pliku w Windows PowerShell Desired State Configuration (DSC) zapewnia mechanizm zarządzania plikami i folderami w docelowym węźle. **Ścieżka_docelowa** i **Ścieżka_źródłowa** muszą być dostępne w docelowym węźle.

## <a name="syntax"></a>Składnia

```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
}
```

## <a name="properties"></a>Właściwości

|Właściwość       |Opis                                                                   |Wymagana|Wartość domyślna|
|---------------|------------------------------------------------------------------------------|--------|-------|
|DestinationPath|Lokalizacja, w węźle docelowym, aby mieć pewność, jest `Present` lub `Absent`.|Tak|Nie|
|Atrybuty     |Żądany stan atrybutów dla pliku docelowego lub katalogu. Prawidłowe wartości to **archiwum**, **ukryty**, **tylko do odczytu**, i **systemu**.|Nie|Brak|
|Suma kontrolna      |Typ sumy kontrolnej używany do określenia, czy dwa pliki są takie same. Prawidłowe wartości to: SHA-1, SHA-256, SHA-512, createdDate, Data modyfikacji.|Nie|Tylko nazwę pliku lub katalogu jest porównywany.|
|Zawartość       |Prawidłowa tylko w przypadku korzystania z `File` typu. Wskazuje zawartość, aby upewnij się, że są `Present` lub `Absent` z pliku docelowego. |Nie|Brak|
|Poświadczenie     |Poświadczenia, które są wymagane do dostępu do zasobów, takich jak pliki źródłowe.|Nie|Konto komputera węzła docelowego. (*patrz Uwaga*)|
|Upewnij się         |Żądany stan docelowego pliku lub katalogu. |Nie|**Obecna**|
|Force          |Zastępuje operacji dostępu, które mogłyby spowodować błąd (np. zastąpienie pliku lub usunięcie katalogu, który nie jest pusty).|Nie|`$false`|
|Recurse        |Prawidłowa tylko w przypadku korzystania z `Directory` typu. Wykonuje rekursywnego operacji stan do wszystkich podkatalogów.|Nie|`$false`|
|DependsOn      |Ustawia zależność określonych zasobów. Ten zasób będzie wykonywane tylko wtedy po pomyślnym wykonaniu wszystkich zasobów zależnych. Można określić zasoby zależne, używając składni `"[ResourceType]ResourceName"`. See [about_DependsOn](../../../configurations/resource-depends-on.md)|Nie|Brak|
|SourcePath     |Ścieżka, z którego można skopiować zasobu pliku lub folderu.|Nie|Brak|
|Typ           |Typ zasobu jest skonfigurowany. Prawidłowe wartości to `Directory` i `File`.|Nie|`File`|
|MatchSource    |Określa, jeśli zasób powinien monitorować nowe pliki dodane do katalogu źródłowego po kopii początkowej. Wartość `$true` wskazuje, że po kopii początkowej, wszystkie nowe pliki źródłowe zostaną skopiowane do lokalizacji docelowej. Jeśli ustawiono `$False`, zasób buforuje zawartość katalogu źródłowego i ignoruje wszelkie pliki dodane po kopii początkowej.|Nie|`$false`|

> [!WARNING]
> Jeśli nie określisz wartości `Credential` lub `PSRunAsCredential` (PS V.5), zasób będzie używał konta komputera węzła docelowego w dostęp do `SourcePath`.  Gdy `SourcePath` jest udziału UNC, może to spowodować błąd "Odmowa dostępu". Upewnij się, Twoje uprawnienia są odpowiednio ustawiane lub użyj `Credential` lub `PSRunAsCredential` właściwości, aby określić konto, które mają być używane.

## <a name="present-vs-absent"></a>Przedstawia programu vs. Nieobecny

Każdy zasób DSC wykonuje różne operacje, w oparciu o wartość określona dla `Ensure` właściwości. Wartości, które określisz dla powyższych właściwości określa operacji stanu wykonywane.

### <a name="existence"></a>Istnienie

Kiedy należy określić tylko `DestinationPath`, zasób zapewnia, że ścieżka istnieje (`Present`) lub nie istnieje (`Absent`).

### <a name="copy-operations"></a>Operacje kopiowania

Po określeniu `SourcePath` i `DestinationPath` z `Type` wartość **katalogu**, katalog zasobów kopii źródłowej w ścieżce docelowej. Właściwości `Recurse`, `Force`, i `MatchSource` Zmień typ operacji kopiowania wykonywania, podczas gdy `Credential` Określa konto, które umożliwia uzyskanie dostępu do katalogu źródłowego.

### <a name="limitations"></a>Ograniczenia

Jeśli określona wartość `ReadOnly` dla `Attributes` właściwości wraz z `DestinationPath`, `Ensure = "Present"` utworzyłoby podanej ścieżki, podczas gdy `Contents` ustawiał zawartość pliku.  `Absent` Będzie ignorować stan operacji `Attributes` właściwość całkowicie i Usuń każdy plik w określonej ścieżce.

## <a name="example"></a>Przykład

Poniższy przykład kopiuje katalog i jego podkatalogach z serwera ściągania z węzłem docelowym przy użyciu pliku zasobu. Jeśli operacja się powiedzie, zasób dziennika zapisuje komunikat z potwierdzeniem w dzienniku zdarzeń.

Katalog źródłowy jest ścieżką UNC (`\\PullServer\DemoSource`) udostępnionych z serwera ściągania. `Recurse` Właściwości gwarantuje, że wszystkie podkatalogi są również kopiowane.

> [!IMPORTANT]
> LCM w docelowym węźle wykonuje w kontekście lokalnego konta systemowego, domyślnie. Aby udzielić dostępu do **Ścieżka_źródłowa**, nadać kontu komputera węzła docelowego odpowiednie uprawnienia. **Poświadczeń** i **PSDSCRunAsCredential** (v5) zarówno zmienić używa kontekstu LCM, aby uzyskać dostęp do **Ścieżka_źródłowa**. Nadal musisz udzielić dostępu do konta, które będą używane do dostępu **Ścieżka_źródłowa**.

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present" # Ensure the directory is Present on the target node.
            Type = "Directory" # The default is File.
            Recurse = $true # Recursively copy all subdirectories.
            SourcePath = "\\PullServer\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # Depends on successful execution of the File resource.
        }
    }
}
```

Więcej używania na **poświadczenia** Zobacz DSC [Uruchom jako użytkownik](../../../configurations/runAsUser.md) lub [poświadczenia dostępu do danych konfiguracji](../../../configurations/configDataCredentials.md).
