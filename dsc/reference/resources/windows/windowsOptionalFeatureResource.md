---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób WindowsOptionalFeature DSC
ms.openlocfilehash: 390caefd2ad190afc651b22ed1beb5cf1d604527
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685445"
---
# <a name="dsc-windowsoptionalfeature-resource"></a>Zasób WindowsOptionalFeature DSC

> Dotyczy: Windows PowerShell 5.0

**WindowsOptionalFeature** zasób w Windows PowerShell Desired State Configuration (DSC) zapewnia mechanizm, aby upewnić się, że funkcje opcjonalne są włączone na węźle docelowym.

## <a name="syntax"></a>Składnia

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a>Właściwości

|  Właściwość  |  Opis   |
|---|---|
| Nazwa| Wskazuje nazwę funkcji, którą chcesz, aby upewnić się, jest włączone lub wyłączone.|
| Upewnij się| Określa, czy ta funkcja jest włączona. Aby upewnić się, że ta funkcja jest włączona, ustaw tę właściwość na "Włącz", aby upewnić się, że funkcja jest wyłączona, ustaw właściwość na "Wyłącz".|
| Źródło| Nie zaimplementowano.|
| NoWindowsUpdateCheck| Określa, czy narzędzia DISM skontaktuje się z usługą Windows Update (WU) podczas szukania plików źródłowych włączyć funkcję. Jeśli $true, narzędzia DISM nie skontaktować się z usługi WU.|
| RemoveFilesOnDisable| Ustaw **$true** Aby usunąć wszystkie pliki skojarzone z funkcją, gdy jest on wyłączony (to znaczy, gdy **upewnij się, że** jest ustawiona na "Brak").|
| PoziomRejestrowania| Maksymalny poziom informacji wyjściowych wyświetlanych w dziennikach. Dozwolone wartości to: "ErrorsOnly" (tylko błędy są rejestrowane), "ErrorsAndWarning" (błędy i ostrzeżenia są rejestrowane), a "ErrorsAndWarningAndInformation" (błędy, ostrzeżenia i informacje o debugowaniu są rejestrowane).|
| Ścieżka dziennika| Ścieżka do pliku dziennika, w której chcesz dostawcy zasobów do dziennika operacji.|
| DependsOn| Określa, czy konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest __ResourceName__ a jej typ jest __ResourceType__, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.|