---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Zasób WindowsProcess DSC"
ms.openlocfilehash: c34d3cb1d4d9b899b45fba7b4b148a7c977f5365
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-windowsprocess-resource"></a>Zasób WindowsProcess DSC

> Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0

**WindowsProcess** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm konfigurowania procesów w docelowym węźle.

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
|  Właściwość  |  Opis   | 
|---|---| 
| Argumenty| Wskazuje ciąg argumenty do przekazania do procesu jako — jest. Aby przekazać argumenty kilka należy umieścić je w tym ciągu.| 
| Ścieżka| Ścieżka do pliku wykonywalnego procesu. Jeśli nazwa pliku wykonywalnego (nie pełni kwalifikowana ścieżka), zasobu DSC przeszuka środowiska **ścieżki** zmiennej (`$env:Path`) można znaleźć pliku wykonywalnego. Jeśli wartość tej właściwości jest w pełni kwalifikowana, nie będzie używać DSC **ścieżki** zmiennej środowiskowej, aby znaleźć plik i zgłosi błąd, jeśli ścieżka nie istnieje. Ścieżki względne nie są dozwolone.| 
| Poświadczenie| Wskazuje poświadczeń dla uruchamiania procesu.| 
| Upewnij się| Wskazuje, czy Proces istnieje. Ustaw tę właściwość na "Brak", aby upewnić się, czy Proces istnieje. W przeciwnym wypadku ustaw ją na "Brak". Wartość domyślna to "Brak".| 
| dependsOn | Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości to "DependsOn ="[ResourceName ResourceType]"".| 
| StandardErrorPath| Określa ścieżkę katalogu do zapisania standardowy błąd. Wszystkie istniejące pliki zostaną zastąpione.| 
| StandardInputPath| Określa lokalizację standardowe wejściowego.| 
| StandardOutputPath| Wskazuje lokalizację do zapisania wyjścia standardowego. Wszystkie istniejące pliki zostaną zastąpione.| 
| WorkingDirectory| Określa lokalizację, która będzie służyć jako bieżący katalog roboczy dla procesu.| 

