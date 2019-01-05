---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: DSC dla systemu Linux zasób nxEnvironment
ms.openlocfilehash: 763ec560faa6adaf42aef3c21c9045be95f780bc
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048593"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a>DSC dla systemu Linux zasób nxEnvironment

**NxEnvironment** zasób w programie PowerShell Desired State Configuration (DSC) zapewnia mechanizm zarządzania systemowe zmienne środowiskowe w węźle systemu Linux.

## <a name="syntax"></a>Składnia

```
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Path = <bool> }
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Właściwości

|  Właściwość |  Opis |
|---|---|
| Nazwa| Wskazuje nazwę zmiennej środowiskowej, dla którego chcesz zapewnić określonego stanu.|
| Wartość| Wartość do przypisania do zmiennej środowiskowej.|
| Upewnij się| Określa, czy należy sprawdzić, czy zmienna istnieje. Ustaw tę właściwość "Present", aby upewnić się, że istnieje zmienna. Ustaw ją na "Brak", aby upewnić się, że nie istnieje zmienna. Wartość domyślna to "Istnieje".|
| Ścieżka| Definiuje zmienną środowiskową, która jest konfigurowana. Ustaw tę właściwość na **$true** , gdy zmienna **ścieżki** zmiennej; w przeciwnym razie ustaw ją na **$false**. Wartość domyślna to **$false**. Jeśli zmienna konfigurowany jest **ścieżki** podana wartość zmiennej, za pośrednictwem **wartość** właściwości, które zostaną dołączone do istniejącej wartości.|
| DependsOn | Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli **identyfikator** zasobu jest najpierw blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** a jej typ jest **ResourceType**, składnia za pomocą tego Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="additional-information"></a>Dodatkowe informacje

* Jeśli **ścieżki** jest nieobecny lub równa **$false**, zmienne środowiskowe są zarządzane w `/etc/environment`. Programy i skrypty może wymagać konfiguracji źródłowej `/etc/environment` plik, aby uzyskać dostęp do zmiennych w środowisku zarządzanym.
* Jeśli **ścieżki** ustawiono **$true**, zmienna środowiskowa odbywa się w pliku `/etc/profile.d/DSCenvironment.sh`. Ten plik zostanie utworzony, jeśli nie istnieje. Jeśli **upewnij się, że** jest ustawiona na "Brak" i **ścieżki** ustawiono **$true**, zmienna środowiskowa tylko zostaną usunięte z `/etc/profile.d/DSCenvironment.sh` , a nie z innych plików.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać **nxEnvironment** zasób, aby upewnić się, że **TestEnvironmentVariable** jest obecny i ma wartość "Test-Value". Jeśli **TestEnvironmentVariable** jest nieobecna, zostanie on utworzony.

```
Import-DSCResource -Module nx


nxEnvironment EnvironmentExample
{
    Ensure = “Present”
    Name = “TestEnvironmentVariable”
    Value = “TestValue”
}
```