---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób Processset DSC
ms.openlocfilehash: 91a2d5b562864addcb8e11062916d291448bbf57
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688840"
---
# <a name="dsc-windowsprocess-resource"></a>Zasób Windowsprocess DSC

_Dotyczy: Windows PowerShell 5.0_

**ProcessSet** zasobów w Windows PowerShell Desired State Configuration (DSC) udostępnia mechanizm do konfigurowania procesów na węzeł docelowy. Ten zasób jest [złożonego zasobów](../../../resources/authoringResourceComposite.md) wywołująca [zasób windowsprocess](windowsProcessResource.md) dla każdej grupy określony w `GroupName` parametru.

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

| Właściwość | Opis |
| --- | --- |
| Argumenty| Ciąg, który zawiera argumenty do przekazania do procesu jako-to. Jeśli musisz przekazać argumenty kilka umieściliśmy je w tym ciągu.|
| Ścieżka| Ścieżki do plików wykonywalnych procesu. Jeśli są one nazwy plików wykonywalnych (nie w pełni kwalifikowanej ścieżki), umożliwia wyszukiwanie zasobów DSC środowiska **ścieżki** zmiennej (`$env:Path`) aby znaleźć pliki. Jeśli wartości tej właściwości to w pełni kwalifikowanej ścieżki, DSC nie będzie używać **ścieżki** zmiennej środowiskowej, aby znaleźć pliki i zgłosi błąd, jeśli ścieżki nie istnieje. Ścieżki względne są niedozwolone.|
| Poświadczenie| Określa poświadczenia do uruchamiania procesu.|
| Upewnij się| Określa, czy istnieje procesów. Ustaw tę właściwość "Present", aby upewnić się, że istnieje proces. W przeciwnym wypadku ustaw ją na "Brak". Wartość domyślna to "Istnieje".|
| StandardErrorPath| Ścieżka, do którego procesy standardowy błąd zapisu. Wszystkie istniejące pliki zostaną zastąpione.|
| StandardInputPath| Strumień, z którego proces odbiera standardowe dane wejściowe.|
| StandardOutputPath| Ścieżka pliku, w której procesy zapisuje standardowe dane wyjściowe. Wszystkie istniejące pliki zostaną zastąpione.|
| WorkingDirectory| Lokalizacja używana jako bieżący katalog roboczy dla procesów.|
| DependsOn | Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest **ResourceName** a jej typ jest **_ResourceType**, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"` .|
