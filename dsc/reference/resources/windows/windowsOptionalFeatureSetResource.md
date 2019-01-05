---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób Windowsoptionalfeatureset DSC
ms.openlocfilehash: c27d026e01bbb443a82112e37f1d199fb3482e49
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048413"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a>Zasób Windowsoptionalfeatureset DSC

> Dotyczy: Windows PowerShell 5.0

**WindowsOptionalFeatureSet** zasób w Windows PowerShell Desired State Configuration (DSC) zapewnia mechanizm, aby upewnić się, że funkcje opcjonalne są włączone na węźle docelowym.
Ten zasób jest [złożonego zasobów](../../../resources/authoringResourceComposite.md) wywołująca [zasób WindowsOptionalFeature](windowsOptionalFeatureResource.md) dla każdej funkcji, określone w `Name` właściwości.

Korzystając z tego zasobu, jeśli chcesz skonfigurować liczbę Windows opcjonalnych funkcji do takiego samego stanu.

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
| Nazwa| Wskazuje nazwę funkcji, które chcesz, aby upewnić się, są włączone lub wyłączone.|
| Upewnij się| Określa, czy włączono wybór funkcji. Aby upewnić się, że funkcje te są włączone, ustaw tę właściwość na "Włącz", aby upewnić się, że funkcje są wyłączone, ustaw właściwość na "Wyłącz".|
| Źródło| Nie zaimplementowano.|
| NoWindowsUpdateCheck| Określa, czy narzędzia DISM skontaktuje się z usługą Windows Update (WU) podczas szukania plików źródłowych w celu włączenia funkcji. Jeśli $true, narzędzia DISM nie skontaktować się z usługi WU.|
| RemoveFilesOnDisable| Ustaw **$true** Aby usunąć wszystkie pliki skojarzone z funkcjami, gdy są one wyłączone (to znaczy, gdy **upewnij się, że** jest ustawiona na "Nieobecny").|
| PoziomRejestrowania| Maksymalny poziom informacji wyjściowych wyświetlanych w dziennikach. Dozwolone wartości to: "ErrorsOnly" (tylko błędy są rejestrowane), "ErrorsAndWarning" (błędy i ostrzeżenia są rejestrowane), a "ErrorsAndWarningAndInformation" (błędy, ostrzeżenia i informacje o debugowaniu są rejestrowane).|
| Ścieżka dziennika| Ścieżka do pliku dziennika, w której chcesz dostawcy zasobów do dziennika operacji.|
| DependsOn| Określa, czy konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest __ResourceName__ a jej typ jest __ResourceType__, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.|
