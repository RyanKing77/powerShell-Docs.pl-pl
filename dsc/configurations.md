---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Konfiguracji DSC
ms.openlocfilehash: d98bf0e85c12103d9b1eeded155bab1af364bd4c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188449"
---
# <a name="dsc-configurations"></a>Konfiguracji DSC

>Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0

Konfiguracji DSC są skrypty programu PowerShell, które definiują specjalny typ funkcji.
Aby zdefiniować konfigurację, użyj programu PowerShell — słowo kluczowe **konfiguracji**.

```powershell
Configuration MyDscConfiguration {

    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
MyDscConfiguration

```

Zapisz skrypt jako plik .ps1.

## <a name="configuration-syntax"></a>Składnia konfiguracji

Skrypt konfiguracji składa się z następujących elementów:

- **Konfiguracji** bloku. To jest blok skryptu najbardziej zewnętrznego. Należy zdefiniować za pomocą **konfiguracji** — słowo kluczowe i podanie nazwy. W takim przypadku nazwa konfiguracji jest "MyDscConfiguration".
- Co najmniej jeden **węzła** bloków. Zdefiniuj te węzły (komputerach lub maszynach wirtualnych), które są konfigurowane. W powyższej konfiguracji istnieje **węzła** bloku przeznaczonego komputerze o nazwie "TEST-PC1".
- Co najmniej jeden zasób bloków. Jest to, gdzie konfiguracji ustawia właściwości zasobów, które jest jej konfigurowanie. W takim przypadku są dwa bloki zasobów, z których każde wywołanie zasobu "WindowsFeature".

W ramach **konfiguracji** bloku, można wykonywać wszystkie zwykle można w funkcji programu PowerShell. Na przykład w poprzednim przykładzie, jeśli nie chcesz twardego kodu nazwę komputera docelowego w konfiguracji, możesz można dodać parametr nazwy węzła:

```powershell
Configuration MyDscConfiguration {

    param(
        [string[]]$ComputerName="localhost"
    )
    Node $ComputerName {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
MyDscConfiguration -ComputerName $ComputerName

```

W tym przykładzie, określ nazwę węzła przekazując go jako **ComputerName** parametr podczas kompilowania konfiguracji. Wartość Nazwa domyślna to "localhost".

## <a name="compiling-the-configuration"></a>Kompilowanie konfiguracji

Zanim użytkownik wprowadza konfigurację, należy go skompilować do dokumentu MOF.
W tym celu wywoływania konfiguracji, takich jak spowodowałoby wywołanie funkcji programu PowerShell.
Ostatni wiersz przykład zawierający tylko nazwę konfiguracji, wywołuje konfiguracji.

>**Uwaga:** do wywołania konfiguracji, funkcja musi być w zakresie globalnym (podobnie jak w przypadku innych funkcji programu PowerShell).
>Ułatwia to wystąpić albo przez "dot-sourcing" skryptu, lub przez uruchomienie skryptu konfiguracji za pomocą F5 lub klikając **Uruchom skrypt** przycisk w ISE.
>Aby kropka źródła skryptu, uruchom polecenie `. .\myConfig.ps1` gdzie `myConfig.ps1` to nazwa pliku skryptu, który zawiera konfigurację.

Podczas wywoływania konfiguracji, go:

- Usuwa wszystkie zmienne
- Tworzy folder w bieżącym katalogu o nazwie identycznej z nazwą konfiguracji.
- Tworzy plik o nazwie _NodeName_MOF w nowy katalog, gdy _NodeName_ jest nazwa konfiguracji węzła docelowego.
    Jeśli istnieje więcej niż jeden węzeł, pliku MOF zostaną utworzone dla każdego węzła.

>**Uwaga**: plik MOF zawiera wszystkie informacje o konfiguracji dla węzła docelowego. W związku z tym ważne jest podlegać ochronie.
>Aby uzyskać więcej informacji, zobacz [Zabezpieczanie pliku MOF](secureMOF.md).

Kompilowanie pierwszy konfiguracji powyżej powoduje następującą strukturę folderów:

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

Jeśli konfiguracja przyjmuje parametr, jak pokazano w przykładzie drugiej, który ma zostać podany w czasie kompilacji. Oto, którego wygląd:

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

## <a name="using-dependson"></a>Przy użyciu DependsOn

Jest przydatne słowa kluczowego DSC **DependsOn**. Zwykle (chociaż niekoniecznie), DSC stosuje zasobów w kolejności ich występowania w konfiguracji.
Jednak **DependsOn** określa zasoby zależne inne zasoby, a LCM gwarantuje, że są stosowane w odpowiedniej kolejności, niezależnie od kolejności w zasobie, które są zdefiniowane wystąpień.
Na przykład konfiguracji może określić, że wystąpienie **użytkownika** istnienie zależy od zasobu **grupy** wystąpienie:

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = "Present"
            GroupName = "TestGroup"
        }

        User UserExample {
            Ensure = "Present"
            UserName = "TestUser"
            FullName = "TestUser"
            DependsOn = "[Group]GroupExample"
        }
    }
}

```

## <a name="using-new-resources-in-your-configuration"></a>Przy użyciu nowych zasobów w konfiguracji

W przypadku uruchomienia poprzednich przykładach, można zauważyć, że zostały ostrzeżenie, że zostały przy użyciu zasobu nie jest jawnie importowany.
Obecnie DSC jest dostarczany z 12 zasobów w ramach modułu PSDesiredStateConfiguration.
Inne zasoby w modułach zewnętrznych muszą znajdować się w `$env:PSModulePath` uznawane za LCM.
Nowe polecenie cmdlet [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), może służyć do określenia, jakie zasoby są zainstalowane w systemie i dostępne do użycia przez LCM.
Gdy te moduły zostały umieszczone w `$env:PSModulePath` i są prawidłowo rozpoznawane przez [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), nadal muszą być ładowane w ramach konfiguracji.
**Import-DscResource** jest dynamiczne słowo kluczowe rozpoznawany tylko w ramach **konfiguracji** bloku (tj. go nie jest poleceniem cmdlet).
**Import-DscResource** obsługuje dwa parametry:
- **Nazwa modułu** jest zalecanym sposobem przy użyciu **DscResource importu**. Przyjmuje nazwę modułu, który zawiera zasoby do zaimportowania (a także tablicy ciągów nazw modułu).
- **Nazwa** jest nazwa zasobu do zaimportowania. Nie jest to przyjazna nazwa zwracane w postaci "Name" przez [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), ale nazwa klasy używane podczas definiowania schematu zasobów (zwracane jako **ResourceType** przez [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx)).

## <a name="see-also"></a>Zobacz też
* [Omówienie stanu konfiguracji żądanego programu Windows PowerShell](overview.md)
* [Zasoby usługi Konfiguracja DSC](resources.md)
* [Konfigurowanie lokalny program Configuration Manager](metaConfig.md)
