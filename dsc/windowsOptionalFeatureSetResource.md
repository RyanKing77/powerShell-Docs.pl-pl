---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasób WindowsOptionalFeatureSet DSC
ms.openlocfilehash: 3329e0d0f1988a2ee20eb848da943ff1b22bd4df
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a>Zasób WindowsOptionalFeatureSet DSC

> Dotyczy: Środowiska Windows PowerShell 5.0

**WindowsOptionalFeatureSet** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm, aby upewnić się, że funkcje opcjonalne są włączone w docelowym węźle.
Ten zasób jest [złożonego zasobów](authoringResourceComposite.md) , który odwołuje się [zasobów WindowsOptionalFeature](windowsOptionalFeatureResource.md) dla każdej funkcji określone w `Name` właściwości.

Jeśli chcesz skonfigurować liczbę opcjonalne funkcje systemu Windows na tym samym stanie, należy użyć tego zasobu.

## <a name="syntax"></a>Składnia

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a>Właściwości

|  Właściwość  |  Opis   |
|---|---|
| Nazwa| Wskazuje nazwę funkcji, które chcesz zapewnić są włączone lub wyłączone.|
| Upewnij się| Określa, czy są włączone funkcje. Aby upewnić się, że funkcje są włączone, ustaw tę właściwość, aby "Włącz", aby upewnić się, że te funkcje są wyłączone, ustaw dla właściwości "Wyłącz".|
| Źródło| Nie jest zaimplementowana.|
| NoWindowsUpdateCheck| Określa, czy narzędzia DISM kontaktuje Windows Update (WU) podczas wyszukiwania plików źródłowych do włączania funkcji. Jeśli $true, narzędzia DISM skontaktować się z usługi WU.|
| RemoveFilesOnDisable| Ustaw **$true** Aby usunąć wszystkie pliki skojarzone z funkcjami, gdy są one wyłączone (oznacza to, gdy **upewnij się, że** jest ustawiona na "Brak").|
| PoziomRejestrowania| Maksymalny poziom informacji wyjściowych wyświetlanych w dziennikach. Dopuszczalne wartości to: "ErrorsOnly" (tylko błędy są rejestrowane), "ErrorsAndWarning" (błędy i ostrzeżenia są rejestrowane), a "ErrorsAndWarningAndInformation" (błędy, ostrzeżenia i informacje o debugowaniu są rejestrowane).|
| Ścieżka dziennika| Ścieżka do pliku dziennika miejscu dostawcy zasobów do operacji logowania.|
| dependsOn| Określa, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.|