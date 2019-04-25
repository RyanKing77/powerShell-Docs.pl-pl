---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Instrukcje warunkowe i pętle w konfiguracjach
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080139"
---
# <a name="conditional-statements-and-loops-in-configurations"></a>Instrukcje warunkowe i pętle w konfiguracjach

Możesz wprowadzić swoje [konfiguracje](configurations.md) bardziej dynamiczne, przy użyciu słów kluczowych sterowanie przepływem programu PowerShell. W tym artykule opisano, jak można użyć instrukcje warunkowe i pętle się bardziej dynamiczne konfiguracje. Połączenie warunkowe i pętle z [parametry](add-parameters-to-a-configuration.md) i [dane konfiguracyjne](configData.md) umożliwia większą elastyczność i kontrolę podczas kompilowania konfiguracji.

Podobnie jak funkcja lub blok skryptu można użyć dowolnego języka programu PowerShell w ramach konfiguracji. Instrukcji, których można używać tylko zostaną ocenione, gdy wywołujesz konfigurację tak, aby skompilować pliku "MOF". Poniższe przykłady pokazują prostych scenariuszy do zademonstrowania koncepcji. Instrukcje warunkowe są pętli częściej są używane z parametrami i dane konfiguracji.

W tym prostym przykładzie **usługi** bloku zasobów pobiera bieżący stan usługi w czasie kompilacji, aby wygenerować plik "MOF", który przechowuje swojego bieżącego stanu.

> [!NOTE]
> Przy użyciu dynamicznych bloków zasobów będzie wywłaszczenia skuteczności Intellisense. Analizator składni programu PowerShell nie można określić, jeśli określone wartości są akceptowane, dopóki jest kompilowana konfiguracja.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Service Spooler
        {
            Name = "Spooler"
            State = $(Get-Service -Name 'spooler').Status
            StartType = $(Get-Service -Name 'spooler').StartType
        }
    }
}
```

Ponadto można utworzyć **usługi** blokowania zasobów dla każdej usługi na bieżącym komputerze przy użyciu `foreach` pętli.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Foreach ($service in $(Get-Service))
        {
            Service $service.Name
            {
                Name = $service.Name
                State = $service.Status
                StartType = $service.StartType
            }
        }
    }
}
```

Można również tylko utworzyć konfiguracje dla maszyn, które są w trybie online, za pomocą prostego `if` instrukcji.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    Foreach ($computer in @('Server01', 'Server02', 'Server03'))
    {
        if (Test-Connection -ComputerName $computer)
        {
            Node $computer
            {
                Service "Spooler"
                {
                    Name = "Spooler"
                    State = "Started"
                }
            }
        }
    }
}
```

> [!NOTE]
> Zasób dynamiczny bloków w powyższych odwołań przykłady bieżącej maszyny. W tym wystąpieniu, które będą maszyny tworzenia konfiguracji na nie element docelowy węzła.

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a>Podsumowanie

Podsumowując można użyć dowolnego języka programu PowerShell w ramach konfiguracji.

Obejmuje to np.:

- Niestandardowe obiekty
- Tabele
- Manipulowanie ciągami
- Komunikacja zdalna
- Usługa WMI i CIM
- Obiekty ActiveDirectory
- i więcej...

Każdy kod programu PowerShell, zdefiniowane w konfiguracji będą oceniane czasu kompilacji, ale możesz również umieścić kod w skrypcie zawierający konfigurację. Każdy kod poza blokiem konfiguracji zostaną wykonane podczas importowania konfiguracji.

## <a name="see-also"></a>Zobacz też

- [Dodaj parametry konfiguracji](add-parameters-to-a-configuration.md)
- [Oddzielenie danych konfiguracji z konfiguracji](configData.md)
