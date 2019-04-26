---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Korzystanie z danych konfiguracji
ms.openlocfilehash: f2d25b9ced805fb4c91378ebfe840104eb6ce52a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080224"
---
# <a name="using-configuration-data-in-dsc"></a>Korzystanie z danych konfiguracji w DSC

> Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0

Za pomocą wbudowanych DSC **ConfigurationData** parametru, można zdefiniować dane, które mogą być używane w konfiguracji.
Dzięki temu można utworzyć jednej konfiguracji, który może służyć do wielu węzłów lub w różnych środowiskach.
Na przykład jeśli tworzysz aplikację, można użyć jednej konfiguracji dla środowisk środowisk deweloperskich i produkcyjnych i użyj dane konfiguracyjne, aby określić dane dla każdego środowiska.

W tym temacie opisano strukturę **ConfigurationData** hashtable.
Przykłady sposobu używania danych konfiguracji, zobacz [oddzielanie danych konfiguracji i środowiska](separatingEnvData.md).

## <a name="the-configurationdata-common-parameter"></a>Typowy parametr danych konfiguracji

Konfiguracja DSC przyjmuje typowego parametru **ConfigurationData**, należy określić podczas kompilacji konfiguracji.
Aby dowiedzieć się, jak kompilowanie konfiguracji, zobacz [konfiguracje DSC](configurations.md).

**ConfigurationData** parametr ma tablicę skrótów, którą musi mieć co najmniej jeden klucz o nazwie **AllNodes**.
Może też mieć co najmniej jeden klucz.

> [!NOTE]
> Przykłady w tym temacie, użyj jednego dodatkowego klucza (innych niż nazwany **AllNodes** klucza) o nazwie `NonNodeData`, ale może zawierać dowolną liczbę dodatkowych kluczy i nazwij je, co tylko chcesz.

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

Wartość **AllNodes** klucza jest tablicą. Każdy element tej tablicy jest również tabelę mieszania, który musi mieć co najmniej jeden klucz o nazwie **NodeName**:

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

Inne klucze można dodać do każdej tabeli wyznaczania wartości skrótu:

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

Aby zastosować właściwości dla wszystkich węzłów, można utworzyć członkiem **AllNodes** tablica, która ma **NodeName** z `*`.
Na przykład, aby nadać każdy węzeł `LogPath` właściwości, można to zrobić:

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

To jest odpowiednikiem dodawania właściwości o nazwie `LogPath` o wartości `"C:\Logs"` do każdego z innych bloków (`VM-1`, `VM-2`, i `VM-3`).

## <a name="defining-the-configurationdata-hashtable"></a>Definiowanie hashtable danych konfiguracji

Można zdefiniować **ConfigurationData** jako zmienną, w tym samym pliku skryptu konfiguracji (jak w naszych poprzednich przykładach) lub w osobnym `.psd1` pliku.
Aby zdefiniować **ConfigurationData** w `.psd1` plików, utworzyć plik, który zawiera tylko tablicy skrótów, który reprezentuje dane konfiguracji.

Na przykład można utworzyć pliku o nazwie `MyData.psd1` z następującą zawartością:

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

Aby skompilować konfigurację, dla którego zdefiniowano dane konfiguracji, przekazać dane konfiguracji jako wartość **ConfigurationData** parametru.

Spowoduje to utworzenie pliku MOF dla każdej pozycji w **AllNodes** tablicy.
Każdy plik MOF będzie miała z `NodeName` właściwość odpowiadający mu wpis w tablicy.

Na przykład, jeśli zdefiniujesz dane konfiguracji, podobnie jak w `MyData.psd1` pliku powyżej kompilacji konfiguracji będzie utworzenie ich obu `VM-1.mof` i `VM-2.mof` plików.

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a>Kompilowanie konfiguracji z danymi konfiguracji przy użyciu zmiennej

Na korzystanie z danych konfiguracji, który jest zdefiniowany jako zmienną, w tym samym `.ps1` pliku konfiguracji, przekazać nazwę zmiennej jako wartości **ConfigurationData** parametru podczas kompilowania konfiguracji:

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a>Kompilowanie konfiguracji w danych konfiguracji, używając pliku danych

Aby korzystać z danych konfiguracji, która jest zdefiniowana w pliku psd1, przekazujesz ścieżkę i nazwę tego pliku jako wartość **ConfigurationData** parametru podczas kompilowania konfiguracji:

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a>Za pomocą zmiennych danych konfiguracji w konfiguracji

DSC udostępnia następujące zmienne specjalne, których można użyć w skrypcie konfiguracji:

- **$AllNodes** odwołuje się do całej kolekcji węzłów zdefiniowane w **ConfigurationData**. Można filtrować **AllNodes** kolekcji przy użyciu **. WHERE()** i **. Metody ForEach()**.
- **ConfigurationData** odwołuje się do tabeli całego wyznaczania wartości skrótu, który jest przekazywany jako parametr podczas kompilowania konfiguracji.
- **MyTypeName** zawiera [konfiguracji](configurations.md) zmienna zostanie użyta w nazwie. Na przykład w konfiguracji `MyDscConfiguration`, `$MyTypeName` będzie mieć wartość `MyDscConfiguration`.
- **Węzeł** odwołuje się do określonego wpisu w **AllNodes** kolekcji po jest filtrowany za pomocą **. WHERE()** lub **. Metody ForEach()**.
  - Możesz dowiedzieć się więcej o tych metodach w [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)

## <a name="using-non-node-data"></a>Korzystanie z danych niż węzła

Jak widzieliśmy w poprzednich przykładach **ConfigurationData** hashtable może mieć co najmniej jeden klucz oprócz wymaganych **AllNodes** klucza.
W przykładach w tym temacie, firma Microsoft ma używany tylko jeden dodatkowy węzeł o nazwie go `NonNodeData`.
Można jednak zdefiniować dowolną liczbę dodatkowych kluczy i nazwy dowolnych znaków.

Na przykład przy użyciu danych węzeł-zobacz [oddzielanie danych konfiguracji i środowiska](separatingEnvData.md).

## <a name="see-also"></a>Zobacz też

- [Opcje poświadczeń w danych konfiguracji](configDataCredentials.md)
- [Konfiguracje DSC](configurations.md)