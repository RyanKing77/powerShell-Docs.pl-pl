---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób WindowsFeature DSC
ms.openlocfilehash: 7a57f4b2797ab3bb202aea8b2543d1e3f14074e9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685970"
---
# <a name="dsc-windowsfeature-resource"></a>Zasób WindowsFeature DSC

> Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0

**WindowsFeature** zasób w Windows PowerShell Desired State Configuration (DSC) zapewnia mechanizm, aby upewnić się, że role i funkcje są dodawane lub usuwane w węźle docelowym.

## <a name="syntax"></a>Składnia

```
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Source = [string] ]
}
```

## <a name="properties"></a>Właściwości

|  Właściwość  |  Opis   |
|---|---|
| Nazwa| Wskazuje nazwę rolę lub funkcję, która chce mieć pewność, jest dodane lub usunięte. To jest taka sama jak __nazwa__ właściwości z [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) polecenia cmdlet, a nie nazwę wyświetlaną roli lub funkcji.|
| Poświadczenie| Określa poświadczenia do użycia w celu dodania lub usunięcia roli lub funkcji.|
| Upewnij się| Wskazuje, jeśli jest dodawany roli lub funkcji. Aby upewnij się, że rola lub funkcja dodano, ustaw tę właściwość na "Obecny", aby upewnić się, że została usunięta rolę lub funkcję, należy ustawić właściwość na "Brak".|
| IncludeAllSubFeature| Ustaw tę właściwość na __$true__ do zapewnienia stan podfunkcje wszystkie wymagane ze stanem tej funkcji należy określić przy użyciu __nazwa__ właściwości.|
| Ścieżka dziennika| Określa ścieżkę do pliku dziennika, w której chcesz dostawcy zasobów do dziennika operacji.|
| DependsOn| Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest __ResourceName__ a jej typ jest __ResourceType__, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.|
| Źródło| Wskazuje lokalizację pliku źródłowego na potrzeby instalacji, jeśli to konieczne.|

## <a name="example"></a>Przykład
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```