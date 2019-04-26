---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób Windowsprocess DSC
ms.openlocfilehash: cee93ab283ded407d6e032161125aa6d6ac98827
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076773"
---
# <a name="dsc-windowsprocess-resource"></a>Zasób Windowsprocess DSC

_Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0_

**WindowsProcess** zasobów w Windows PowerShell Desired State Configuration (DSC) udostępnia mechanizm do konfigurowania procesów na węzeł docelowy.

## <a name="syntax"></a>Składnia

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ DependsOn = [string[]] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
}
```

## <a name="properties"></a>Właściwości

| Właściwość | Opis |
| --- | --- |
| Argumenty| Wskazuje ciąg argumenty do przekazania do procesu jako-to. Jeśli musisz przekazać argumenty kilka umieściliśmy je w tym ciągu.|
| Ścieżka| Ścieżka do pliku wykonywalnego procesu. Jeśli nazwa pliku wykonywalnego (nie w pełni kwalifikowana ścieżka), zasobu DSC wyszuka środowiska **ścieżki** zmiennej (`$env:Path`) można znaleźć pliku wykonywalnego. Jeśli wartość tej właściwości jest w pełni kwalifikowaną ścieżkę, DSC nie będzie używać **ścieżki** zmiennej środowiskowej, aby znaleźć plik i zgłosi błąd, jeśli ścieżka nie istnieje. Ścieżki względne są niedozwolone.|
| Poświadczenie| Określa poświadczenia do uruchamiania procesu.|
| Upewnij się| Wskazuje, czy Proces istnieje. Ustaw tę właściwość "Present", aby upewnić się, że istnieje proces. W przeciwnym wypadku ustaw ją na "Brak". Wartość domyślna to "Istnieje".|
| dependsOn | Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest **ResourceName** a jej typ jest **ResourceType**, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"` .|
| StandardErrorPath| Określa ścieżkę katalogu do zapisu błędu standardowego. Wszystkie istniejące pliki zostaną zastąpione.|
| StandardInputPath| Wskazuje standardowy lokalizację danych wejściowych.|
| StandardOutputPath| Wskazuje lokalizację do zapisania wyjścia standardowego. Wszystkie istniejące pliki zostaną zastąpione.|
| WorkingDirectory| Wskazuje lokalizację, która będzie służyć jako bieżący katalog roboczy dla procesu.|