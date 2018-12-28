---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Konfiguracje DSC
ms.openlocfilehash: 6af27f442de3080facd65892c713c989d0e388c5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404969"
---
# <a name="dsc-configurations"></a>Konfiguracje DSC

> Dotyczy: Program Windows PowerShell 4.0, Windows PowerShell 5.0

Konfiguracje DSC są skrypty programu PowerShell, definiujące specjalny rodzaj funkcji.
Aby zdefiniować konfigurację, należy użyć programu PowerShell — słowo kluczowe **konfiguracji**.

```powershell
Configuration MyDscConfiguration {
    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = 'Present'
            Name = 'RSAT'
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}
MyDscConfiguration
```

Zapisz skrypt jako `.ps1` pliku.

## <a name="configuration-syntax"></a>Składnia konfiguracji

Skrypt konfiguracji składa się z następujących elementów:

- **Konfiguracji** bloku. Jest to blok skryptu najbardziej zewnętrznej. Można zdefiniować przy użyciu **konfiguracji** — słowo kluczowe i podając nazwę. W takim przypadku nazwa konfiguracji jest "MyDscConfiguration".
- Co najmniej jeden **węzła** bloków. Te definiują węzłów (maszyn wirtualnych lub komputerach), które konfigurujesz. W powyższej konfiguracji, ma jedną **węzła** bloku, który jest przeznaczony dla komputera o nazwie "TEST-PC1". Blok węzła może akceptować wiele nazw komputerów.
- Jeden lub więcej bloków zasobów. Jest to, gdzie konfiguracja ustawia właściwości zasobów, które go służy do konfigurowania. W tym przypadku istnieją dwa bloki zasobów, z których każde wywołanie zasobu "WindowsFeature".

W ramach **konfiguracji** bloku, można zrobić wszystko, co zwykle można w funkcji programu PowerShell. Na przykład w poprzednim przykładzie, jeśli nie chcesz ciężko code nazwę komputera docelowego w konfiguracji, można dodać parametr dla nazwy węzła:

W tym przykładzie Określ nazwę węzła przez przekazanie jej jako **ComputerName** parametru podczas kompilowania konfiguracji. Nazwa, wartość domyślna to "localhost".

```powershell
Configuration MyDscConfiguration
{
    param
    (
        [string[]]$ComputerName='localhost'
    )

    Node $ComputerName
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

**Węzła** bloku mogą również akceptować wiele nazw komputerów. W powyższym przykładzie, można użyć `-ComputerName` parametr lub — dostęp próbny rozdzielonych przecinkami listę komputerów, bezpośrednio do **węzła** bloku.

```powershell
MyDscConfiguration -ComputerName "localhost", "Server01"
```

Podczas określania listy komputerów do **węzła** bloku, z w ramach konfiguracji, należy użyć tablicy notacji.

```powershell
Configuration MyDscConfiguration
{
    Node @('localhost', 'Server01')
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

## <a name="compiling-the-configuration"></a>Kompilowanie konfiguracji

Przed może przyjąć konfiguracji, należy skompilować go na dokument MOF.
Możesz to zrobić, wywołując konfiguracji, takie jak wywoływałby funkcję programu PowerShell.
Ostatni wiersz przykład zawierający tylko nazwę konfiguracji, wywołuje konfiguracji.

> [!NOTE]
> Aby wywołać konfigurację, funkcja musi być w zakresie globalnym (podobnie jak w przypadku innych funkcji programu PowerShell).
> Ułatwia to możliwe albo przez "Funkcja dot-sourcing" skryptu, lub przez uruchomienie skryptu konfiguracji przy użyciu klawisza F5 lub klikając **uruchamianie skryptu** przycisku w środowisku ISE.
> Do źródła skryptu, kropka, uruchom polecenie `. .\myConfig.ps1` gdzie `myConfig.ps1` to nazwa pliku skryptu, który zawiera konfigurację.

Gdy wywołujesz konfiguracji, go:

- Usuwa wszystkie zmienne
- Tworzy folder w bieżącym katalogu o nazwie identycznej z nazwą konfiguracji.
- Tworzy plik o nazwie _NodeName_MOF w nowy katalog, gdzie _NodeName_ jest nazwa konfiguracji węzła docelowego.
  Jeśli istnieje więcej niż jeden węzeł, zostanie utworzony plik MOF dla każdego węzła.

> [!NOTE]
> Plik MOF zawiera wszystkie informacje o konfiguracji dla węzła docelowego. W związku z tym należy Przechowuj w bezpiecznym miejscu.
> Aby uzyskać więcej informacji, zobacz [Zabezpieczanie pliku MOF](../pull-server/secureMOF.md).

Kompilowanie to pierwsza Konfiguracja powyżej skutkuje następującą strukturę folderów:

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 localhost.mof
```

Jeśli konfiguracja przyjmuje parametr, jak w drugim przykładzie, który ma zostać dostarczona w czasie kompilacji. Poniżej przedstawiono, jak będzie wyglądać:

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration -ComputerName 'MyTestNode'
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```

## <a name="using-new-resources-in-your-configuration"></a>Za pomocą nowych zasobów w konfiguracji

Po przeprowadzeniu poprzednich przykładach, można zauważyć, że zostały ostrzegani, które były używane zasób bez jawnie jego importowania.
Już dziś DSC jest dostarczany z 12 zasobów jako część modułu PSDesiredStateConfiguration.

Polecenia cmdlet [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), może służyć do określenia, jakie zasoby są zainstalowane w systemie i dostępne do użycia przez LCM.
Gdy te moduły zostały umieszczone w `$env:PSModulePath` i prawidłowo rozpoznawane przez [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), są nadal muszą być ładowane w konfiguracji.

**Import-DscResource** jest dynamiczne słowo kluczowe, które mogą być rozpoznawane tylko w ramach **konfiguracji** bloku, nie jest poleceniem cmdlet.
**Import-DscResource** obsługuje dwa parametry:

- **ModuleName** jest to zalecany sposób korzystania z **Import-DscResource**. Przyjmuje nazwę modułu, która zawiera zasoby do zaimportowania (a także ciąg na tablicę nazwy modułów).
- **Nazwa** to nazwa zasobu do zaimportowania. Nie jest to przyjazna nazwa jako "Name" zwróciło [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), ale nazwa klasy używane podczas definiowania schematu zasobów (zwracane jako **ResourceType** przez [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).

Aby uzyskać więcej informacji na temat korzystania z `Import-DSCResource`, zobacz [Import-DSCResource przy użyciu](import-dscresource.md)

## <a name="powershell-v4-and-v5-differences"></a>Różnice w wersji 4 i 5 programu PowerShell

Istnieją różnice w których zasoby DSC muszą znajdować się w programie PowerShell 4.0. Aby uzyskać więcej informacji, zobacz [lokalizacja zasobu](import-dscresource.md#resource-location).

## <a name="see-also"></a>Zobacz też

- [Program Windows PowerShell Desired State Configuration — omówienie](../overview/overview.md)
- [Zasoby DSC](../resources/resources.md)
- [Konfigurowanie programu Local Configuration Manager](../managing-nodes/metaConfig.md)
