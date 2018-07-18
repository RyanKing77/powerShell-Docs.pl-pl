---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób Processset DSC
ms.openlocfilehash: d18d2c96239abd83cea735e0fbce198d0456cea6
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093994"
---
# <a name="dsc-windowsprocess-resource"></a>Zasób Windowsprocess DSC

> Dotyczy: Windows PowerShell 5.0

**ProcessSet** zasobów w Windows PowerShell Desired State Configuration (DSC) udostępnia mechanizm do konfigurowania procesów na węzeł docelowy. Ten zasób jest [złożonego zasobów](authoringResourceComposite.md) wywołująca [zasób windowsprocess](windowsProcessResource.md) dla każdej grupy określony w `GroupName` parametru.

## <a name="syntax"></a>Składnia

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Właściwości

|  Właściwość  |  Opis   |
|---|---|
| Argumenty| Ciąg, który zawiera argumenty do przekazania do procesu jako-to. Jeśli musisz przekazać argumenty kilka umieściliśmy je w tym ciągu.|
| Ścieżka| Ścieżki do plików wykonywalnych procesu. Jeśli są one nazwy plików wykonywalnych (nie w pełni kwalifikowanej ścieżki), umożliwia wyszukiwanie zasobów DSC środowiska **ścieżki** zmiennej (`$env:Path`) aby znaleźć pliki. Jeśli wartości tej właściwości to w pełni kwalifikowanej ścieżki, DSC nie będzie używać **ścieżki** zmiennej środowiskowej, aby znaleźć pliki i zgłosi błąd, jeśli ścieżki nie istnieje. Ścieżki względne są niedozwolone.|
| Poświadczenie| Określa poświadczenia do uruchamiania procesu.|
| Upewnij się| Określa, czy istnieje procesów. Ustaw tę właściwość "Present", aby upewnić się, że istnieje proces. W przeciwnym wypadku ustaw ją na "Brak". Wartość domyślna to "Istnieje".|
| StandardErrorPath| Ścieżka, do którego procesy standardowy błąd zapisu. Wszystkie istniejące pliki zostaną zastąpione.|
| StandardInputPath| Strumień, z którego proces odbiera standardowe dane wejściowe.|
| StandardOutputPath| Ścieżka pliku, w której procesy zapisuje standardowe dane wyjściowe. Wszystkie istniejące pliki zostaną zastąpione.|
| WorkingDirectory| Lokalizacja używana jako bieżący katalog roboczy dla procesów.|
| DependsOn | Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest **ResourceName** a jej typ jest **_ResourceType**, składnia przy użyciu tej właściwości jest "DependsOn"[= ResourceName ResourceType]"".|