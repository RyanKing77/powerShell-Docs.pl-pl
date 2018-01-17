---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "DSC dla systemu Linux nxEnvironment zasobów"
ms.openlocfilehash: 61e0c7e77e486cea878351f1929d73f1f80710d8
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-for-linux-nxenvironment-resource"></a>DSC dla systemu Linux nxEnvironment zasobów

**NxEnvironment** zasób w PowerShell żądanego stanu konfiguracji (DSC) zapewnia mechanizm do zarządzania systemowe zmienne środowiskowe w węźle systemu Linux.

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
| Nazwa| Wskazuje nazwę zmiennej środowiskowej, dla którego chcesz zapewnić z określonym stanem.| 
| Wartość| Wartość do przypisania do zmiennej środowiskowej.| 
| Upewnij się| Określa, czy sprawdzić, czy istnieje zmienna. Ustaw tę właściwość na "Brak", aby upewnić się, że istnieje zmienna. Ustaw ją na "Brak", aby upewnić się, że zmienna nie istnieje. Wartość domyślna to "Brak".| 
| Ścieżka| Definiuje zmienną środowiskową, który jest konfigurowany. Ta właściwość jest ustawiana **$true** Jeśli zmienna jest **ścieżki** zmiennej; w przeciwnym razie ustaw ją na **$false**. Wartość domyślna to **$false**. Jeśli zmienna konfigurowany jest **ścieżki** wartość zmiennej, realizowane za pośrednictwem **wartość** właściwości, które zostaną dołączone do istniejącej wartości.| 
| dependsOn | Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli **identyfikator** zasobu jest pierwszy blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** i jej typ jest **ResourceType**, za pomocą tej składni Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.| 

## <a name="additional-information"></a>Dodatkowe informacje

* Jeśli **ścieżki** jest nieobecny lub ustawić **$false**, zmienne środowiskowe są zarządzane w `/etc/environment`. Programy i skrypty może być wymagana konfiguracja źródła `/etc/environment` pliku do uzyskania dostępu do zmiennych środowiskowych zarządzanych.
* Jeśli **ścieżki** ustawiono **$true**, zmienna środowiskowa odbywa się w pliku `/etc/profile.d/DSCenvironment.sh`. Ten plik zostanie utworzona, jeśli nie istnieje. Jeśli **upewnij się, że** jest ustawiona na "Brak" i **ścieżki** ustawiono **$true**, zmienna środowiskowa zostanie tylko usunięte z `/etc/profile.d/DSCenvironment.sh` , a nie z innych plików.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia użycie **nxEnvironment** zasobów, aby upewnić się, że **TestEnvironmentVariable** jest obecny i ma wartość "Test-Value". Jeśli **TestEnvironmentVariable** jest nieobecna, zostanie on utworzony.

```
Import-DSCResource -Module nx 


nxEnvironment EnvironmentExample
{
    Ensure = “Present”
    Name = “TestEnvironmentVariable”
    Value = “TestValue”
}
```


