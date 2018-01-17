---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Przy użyciu danych konfiguracji"
ms.openlocfilehash: b56a3f970b0b5121585dc4ed2f32da3243b980bd
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="using-configuration-data-in-dsc"></a>Przy użyciu danych konfiguracji w konfiguracji DSC

>Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0

Za pomocą wbudowanych DSC **ConfigurationData** parametru, można zdefiniować dane, które mogą być używane w konfiguracji. Dzięki temu można utworzyć pojedynczą konfiguracją, która może służyć do wielu węzłów lub dla różnych środowisk. Na przykład jeśli tworzysz aplikację, można korzystać z jednej konfiguracji dla środowisk zarówno projektowania i produkcji i korzystać z danych konfiguracji do określania danych dla każdego środowiska.

W tym temacie opisano strukturę **ConfigurationData** hashtable. Przykłady sposobu używania danych konfiguracji, zobacz [oddzielanie danych konfiguracji i środowiska](separatingEnvData.md).

## <a name="the-configurationdata-common-parameter"></a>Typowy parametr ConfigurationData

Typowy Parametr przyjmuje konfiguracji DSC **ConfigurationData**, określ, kiedy kompilacja konfiguracji. Informacje o konfiguracjach kompilacji, zobacz [konfiguracji DSC](configurations.md).

**ConfigurationData** parametr jest hasthtable, który musi mieć co najmniej jeden klucz o nazwie **AllNodes**. Może również mieć co najmniej jeden klucz.

>**Uwaga:** przykłady w tym temacie, użyj jednego klucza dodatkowe (innych niż nazwany **AllNodes** klucza) o nazwie `NonNodeData`, jednak zawierać dowolną liczbę dodatkowych kluczy i nazwy dowolne.

```powershell
$MyData = 
@{
    AllNodes = @()
    NonNodeData = ""   
}
```

Wartość **AllNodes** klucza jest tablicą. Każdy element tej tablicy jest również tablicy skrótów, który musi mieć co najmniej jeden klucz o nazwie **NodeName**:

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName = "VM-1"
        },

 
        @{
            NodeName = "VM-2"
        },

 
        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""   
}
```

Kluczy można dodać do każdej tabeli skrótów:

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },

 
        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },

 
        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""   
}
```

Aby zastosować właściwości dla wszystkich węzłów, można utworzyć członkiem **AllNodes** tablica, która ma **NodeName** z `*`. Na przykład, w celu każdego węzła `LogPath` właściwości, można to zrobić:

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName     = "*"
            LogPath      = "C:\Logs"
        },

 
        @{
            NodeName     = "VM-1"
            Role         = "WebServer"
            SiteContents = "C:\Site1"
            SiteName     = "Website1"
        },

 
        @{
            NodeName     = "VM-2"
            Role         = "SQLServer"
        },

 
        @{
            NodeName     = "VM-3"
            Role         = "WebServer"
            SiteContents = "C:\Site2"
            SiteName     = "Website3"
        }
    );
}
```

Jest to równoważne dodawania właściwości o nazwie `LogPath` o wartości `"C:\Logs"` do każdego z innych bloków (`VM-1`, `VM-2`, i `VM-3`).

## <a name="defining-the-configurationdata-hashtable"></a>Definiowanie ConfigurationData hashtable

Można zdefiniować **ConfigurationData** jako zmiennej w ramach tego samego pliku skryptu jako konfiguracji (jak w naszych przykładach poprzedniej) lub w oddzielnej `.psd1` pliku. Aby zdefiniować **ConfigurationData** w `.psd1` pliku, Utwórz plik, który zawiera tylko hashtable, który reprezentuje dane konfiguracji.

Na przykład można utworzyć pliku o nazwie `MyData.psd1` z następującą zawartość:

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        },

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

## <a name="compiling-a-configuration-with-configuration-data"></a>Kompilowanie konfiguracji z danymi konfiguracji

Aby skompilować konfiguracji, dla którego zdefiniowano dane konfiguracji, przekazać dane konfiguracji jako wartość **ConfigurationData** parametru.

Spowoduje to utworzenie pliku MOF dla każdej pozycji w **AllNodes** tablicy.
Każdy plik MOF będą miały nazwę nadaną przez `NodeName` właściwości odpowiadający mu wpis w tablicy.

Na przykład, jeśli należy zdefiniować dane konfiguracji, jak w `MyData.psd1` pliku powyżej, kompilowanie konfiguracji spowoduje utworzenie zarówno `VM-1.mof` i `VM-2.mof` plików.

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a>Kompilowanie konfiguracji z danymi konfiguracji przy użyciu zmiennej

Aby użyć danych konfiguracji, który jest zdefiniowany jako zmienną, w tym samym `.ps1` pliku jako Konfiguracja, przekaż nazwę zmiennej jako wartości **ConfigurationData** parametr podczas kompilowania konfiguracji:

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a>Kompilowanie konfiguracji z danymi konfiguracji przy użyciu pliku danych

Aby korzystać z danych konfiguracji, która jest zdefiniowana w pliku psd1, przekazujesz ścieżkę i nazwę tego pliku jako wartość **ConfigurationData** parametr podczas kompilowania konfiguracji:

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a>Używanie zmiennych ConfigurationData w konfiguracji

DSC udostępnia trzy zmienne specjalne, których można użyć w skrypcie konfiguracji: **$AllNodes**, **$Node**, i **$ConfigurationData**.

- **$AllNodes** odwołuje się do całego kolekcja węzłów zdefiniowane w **ConfigurationData**. Można filtrować **AllNodes** kolekcji przy użyciu **. WHERE()** i **. ForEach()**.
- **Węzeł** odwołuje się do określonego wpisu w **AllNodes** kolekcji po jest filtrowana za pomocą **. WHERE()** lub **. ForEach()**.
- **ConfigurationData** odwołuje się do tabeli całego wyznaczania wartości skrótu, która jest przekazywana jako parametr podczas kompilowania konfiguracji.

## <a name="using-non-node-data"></a>Przy użyciu danych z systemem innym niż węzeł

Jak przedstawiono w poprzednich przykładach, możemy **ConfigurationData** hashtable może mieć co najmniej jeden klucz oprócz wymaganych **AllNodes** klucza.
W przykładach w niniejszym temacie, firma Microsoft ma używany tylko jeden dodatkowy węzeł o nazwie go `NonNodeData`. Można jednak określić dowolną liczbę dodatkowych kluczy i nazwy dowolnych znaków.

Na przykład przy użyciu danych z systemem innym niż węzeł, zobacz [oddzielanie danych konfiguracji i środowiska](separatingEnvData.md).

## <a name="see-also"></a>Zobacz też
- [Opcje poświadczeń w danych konfiguracji](configDataCredentials.md)
- [Konfiguracji DSC](configurations.md)

