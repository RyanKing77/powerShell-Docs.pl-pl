---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasób WindowsOptionalFeature DSC
ms.openlocfilehash: 1866bc9cd2194a62de23eaabee8a9c5049a84946
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-windowsoptionalfeature-resource"></a>Zasób WindowsOptionalFeature DSC

> Dotyczy: Środowiska Windows PowerShell 5.0

**WindowsOptionalFeature** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm, aby upewnić się, że funkcje opcjonalne są włączone w docelowym węźle.

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
| Nazwa| Wskazuje nazwę funkcji, który chcesz zapewnić jest włączone lub wyłączone.|
| Upewnij się| Określa, czy ta funkcja jest włączona. Aby upewnić się, że funkcja jest włączona, ustaw tę właściwość, aby "Włącz", aby upewnić się, że funkcja jest wyłączona, ustaw dla właściwości "Wyłącz".|
| Źródło| Nie jest zaimplementowana.|
| NoWindowsUpdateCheck| Określa, czy narzędzia DISM kontaktuje Windows Update (WU) podczas wyszukiwania plików źródłowych włączyć funkcję. Jeśli $true, narzędzia DISM skontaktować się z usługi WU.|
| RemoveFilesOnDisable| Ustaw **$true** Aby usunąć wszystkie pliki skojarzone z funkcją wyłączonego (oznacza to, gdy **upewnij się, że** jest ustawiona na "Brak").|
| PoziomRejestrowania| Maksymalny poziom informacji wyjściowych wyświetlanych w dziennikach. Dopuszczalne wartości to: "ErrorsOnly" (tylko błędy są rejestrowane), "ErrorsAndWarning" (błędy i ostrzeżenia są rejestrowane), a "ErrorsAndWarningAndInformation" (błędy, ostrzeżenia i informacje o debugowaniu są rejestrowane).|
| Ścieżka dziennika| Ścieżka do pliku dziennika miejscu dostawcy zasobów do operacji logowania.|
| dependsOn| Określa, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.|