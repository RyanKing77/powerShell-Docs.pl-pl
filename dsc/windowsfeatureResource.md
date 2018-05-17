---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasób WindowsFeature DSC
ms.openlocfilehash: ece77043d3a4131150b934a19ee8b92dd75c48f0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-windowsfeature-resource"></a>Zasób WindowsFeature DSC

> Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0

**WindowsFeature** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm, aby upewnić się, że role i funkcje zostały dodane lub usunięte w docelowym węźle.

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
| Nazwa| Wskazuje nazwę roli lub funkcji, które chcesz zapewnić zostanie dodany lub usunięty. Jest taka sama jak __nazwa__ właściwość z [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) polecenia cmdlet, a nie nazwę wyświetlaną roli lub funkcji.|
| Poświadczenie| Określa poświadczenia używane do dodawania lub usuwania roli lub funkcji.|
| Upewnij się| Wskazuje, jeśli jest dodawany roli lub funkcji. Aby upewnić się, że roli lub funkcji jest dodany, ustaw tę właściwość na "Brak", aby upewnić się, że zostanie usunięty rolę lub funkcję, ustaw właściwość na "Brak".|
| IncludeAllSubFeature| Ta właściwość jest ustawiana __$true__ do zapewnienia stan wszystkich wymaganych podfunkcje ze stanem funkcji z __nazwa__ właściwości.|
| Ścieżka dziennika| Określa ścieżkę do pliku dziennika miejscu dostawcy zasobów do operacji logowania.|
| dependsOn| Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.|
| Źródło| Określa lokalizację pliku źródłowego do użycia na potrzeby instalacji, jeśli to konieczne.|

## <a name="example"></a>Przykład
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```