---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Konfiguracje DSC
ms.openlocfilehash: 171068acb51f44e31c81e63f6640222ef71bee38
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093698"
---
# <a name="dsc-configurations"></a>Konfiguracje DSC

> Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0

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

Zapisz skrypt jako plik .ps1.

## <a name="configuration-syntax"></a>Składnia konfiguracji

Skrypt konfiguracji składa się z następujących elementów:

- **Konfiguracji** bloku. Jest to blok skryptu najbardziej zewnętrznej. Można zdefiniować przy użyciu **konfiguracji** — słowo kluczowe i podając nazwę. W takim przypadku nazwa konfiguracji jest "MyDscConfiguration".
- Co najmniej jeden **węzła** bloków. Te definiują węzłów (maszyn wirtualnych lub komputerach), które konfigurujesz. W powyższej konfiguracji, ma jedną **węzła** bloku, który jest przeznaczony dla komputera o nazwie "TEST-PC1".
- Jeden lub więcej bloków zasobów. Jest to, gdzie konfiguracja ustawia właściwości zasobów, które go służy do konfigurowania. W tym przypadku istnieją dwa bloki zasobów, z których każde wywołanie zasobu "WindowsFeature".

W ramach **konfiguracji** bloku, można zrobić wszystko, co zwykle można w funkcji programu PowerShell. Na przykład w poprzednim przykładzie, jeśli nie chcesz ciężko code nazwę komputera docelowego w konfiguracji, można dodać parametr dla nazwy węzła:

```powershell
Configuration MyDscConfiguration {
    param(
        [string[]]$ComputerName='localhost'
    )
    Node $ComputerName {
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
MyDscConfiguration -ComputerName $ComputerName
```

W tym przykładzie Określ nazwę węzła przez przekazanie jej jako **ComputerName** parametru podczas kompilowania konfiguracji. Nazwa, wartość domyślna to "localhost".

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
  W przypadku węzłów więcej niż jeden plik MOF będzie można utworzyć dla każdego węzła.

> [!NOTE]
> Plik MOF zawiera wszystkie informacje o konfiguracji dla węzła docelowego. W związku z tym należy Przechowuj w bezpiecznym miejscu.
> Aby uzyskać więcej informacji, zobacz [Zabezpieczanie pliku MOF](secureMOF.md).

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

## <a name="using-dependson"></a>Za pomocą DependsOn

Jest przydatne — słowo kluczowe DSC **DependsOn**. Zazwyczaj (chociaż niekoniecznie), DSC, ma zastosowanie zasobów w kolejności, w jakiej występują w ramach konfiguracji.
Jednak **DependsOn** Określa, która zasoby zależne inne zasoby, a LCM gwarantuje, że są stosowane w odpowiedniej kolejności, niezależnie od kolejności, w zasobach, które są zdefiniowane wystąpień.
Na przykład konfiguracji może określić, że wystąpienie **użytkownika** zasobów zależy od istnienia **grupy** wystąpienie:

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = 'Present'
            GroupName = 'TestGroup'
        }

        User UserExample {
            Ensure = 'Present'
            UserName = 'TestUser'
            FullName = 'TestUser'
            DependsOn = '[Group]GroupExample'
        }
    }
}
```

## <a name="using-new-resources-in-your-configuration"></a>Za pomocą nowych zasobów w konfiguracji

Po przeprowadzeniu poprzednich przykładach, można zauważyć, że zostały ostrzegani, które były używane zasób bez jawnie jego importowania.
Już dziś DSC jest dostarczany z 12 zasobów jako część modułu PSDesiredStateConfiguration.
Inne zasoby zewnętrznych modułów muszą być umieszczone w `$env:PSModulePath` uznawane przez LCM.
Nowe polecenie cmdlet [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), może służyć do określenia, jakie zasoby są zainstalowane w systemie i dostępne do użycia przez LCM.
Gdy te moduły zostały umieszczone w `$env:PSModulePath` i prawidłowo rozpoznawane przez [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), są nadal muszą być ładowane w konfiguracji.
**Import-DscResource** jest dynamiczne słowo kluczowe, które mogą być rozpoznawane tylko w ramach **konfiguracji** bloku (czyli nie jest poleceniem cmdlet).
**Import-DscResource** obsługuje dwa parametry:

- **ModuleName** jest to zalecany sposób korzystania z **Import-DscResource**. Przyjmuje nazwę modułu, która zawiera zasoby do zaimportowania (a także ciąg na tablicę nazwy modułów).
- **Nazwa** to nazwa zasobu do zaimportowania. Nie jest to przyjazna nazwa jako "Name" zwróciło [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), ale nazwa klasy używane podczas definiowania schematu zasobów (zwracane jako **ResourceType** przez [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx)).

## <a name="see-also"></a>Zobacz też

- [Program Windows PowerShell Desired State Configuration — omówienie](overview.md)
- [Zasoby DSC](resources.md)
- [Konfigurowanie programu Local Configuration Manager](metaConfig.md)