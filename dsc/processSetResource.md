---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasób ProcessSet DSC
ms.openlocfilehash: 412cf1076996126f0d9b7a9a8ebbc9bdb7ecf377
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-windowsprocess-resource"></a>Zasób WindowsProcess DSC

> Dotyczy: Środowiska Windows PowerShell 5.0

**ProcessSet** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm konfigurowania procesów w docelowym węźle. Ten zasób jest [złożonego zasobów](authoringResourceComposite.md) , który odwołuje się [zasobów WindowsProcess](windowsProcessResource.md) dla każdej grupy określonej w `GroupName` parametru.

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
| Argumenty| Ciąg, który zawiera argumenty do przekazania do procesu jako — jest. Aby przekazać argumenty kilka należy umieścić je w tym ciągu.|
| Ścieżka| Ścieżki do plików wykonywalnych procesu. Jeśli są one nazwy plików wykonywalnych (nie w pełni kwalifikowanej ścieżki), zasobu DSC przeszuka środowiska **ścieżki** zmiennej (`$env:Path`) można znaleźć plików. Jeśli wartości tej właściwości są w pełni kwalifikowanymi ścieżkami, nie będzie używać DSC **ścieżki** zmiennej środowiskowej można znaleźć plików i zgłosi błąd, jeśli ścieżki nie istnieje. Ścieżki względne nie są dozwolone.|
| Poświadczenie| Wskazuje poświadczeń dla uruchamiania procesu.|
| Upewnij się| Określa, czy istnieje procesów. Ustaw tę właściwość na "Brak", aby upewnić się, czy Proces istnieje. W przeciwnym wypadku ustaw ją na "Brak". Wartość domyślna to "Brak".|
| StandardErrorPath| Ścieżka, do którego standardowy błąd zapisu procesów. Wszystkie istniejące pliki zostaną zastąpione.|
| StandardInputPath| Strumień, z którego proces odbiera standardowe dane wejściowe.|
| StandardOutputPath| Ścieżka pliku, do którego procesy zapisu wyjścia standardowego. Wszystkie istniejące pliki zostaną zastąpione.|
| WorkingDirectory| Lokalizacja używana jako bieżący katalog roboczy dla procesów.|
| dependsOn | Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest **ResourceName** i jej typ jest **_ResourceType**, składnia za pomocą tej właściwości to "DependsOn ="[ResourceName ResourceType]"".|