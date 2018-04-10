---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasób WindowsFeatureSet DSC
ms.openlocfilehash: a6fecba0397b88ce39f6f1a1be6cc366c8a983a6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-windowsfeatureset-resource"></a>Zasób WindowsFeatureSet DSC

> Dotyczy: Środowiska Windows PowerShell 5.0

**WindowsFeatureSet** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm, aby upewnić się, że role i funkcje zostały dodane lub usunięte w docelowym węźle.
Ten zasób jest [złożonego zasobów](authoringResourceComposite.md) , który odwołuje się [zasobów WindowsFeature](windowsfeatureResource.md) dla każdej funkcji określone w `Name` właściwości.

Jeśli chcesz skonfigurować wiele funkcji systemu Windows na tym samym stanie, należy użyć tego zasobu.

## <a name="syntax"></a>Składnia

```
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [bool] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a>Właściwości

|  Właściwość  |  Opis   |
|---|---|
| Nazwa| Nazwy ról lub funkcji, które chcesz zapewnić zostały dodane lub usunięte. To jest taka sama jak **nazwa** właściwość [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) polecenia cmdlet, a nie nazwę wyświetlaną ról lub funkcji.|
| Poświadczenie| Poświadczenia używane do dodawania lub usuwania ról lub funkcji.|
| Upewnij się| Wskazuje, czy role i funkcje zostaną dodane. Aby upewnić się, że role i funkcje są dodane, ustaw tę właściwość na "Brak", aby upewnić się, że role i funkcje zostały usunięte, ustaw właściwość na "Brak".|
| IncludeAllSubFeature| Ta właściwość jest ustawiana **$true** uwzględnienie wszystkich wymaganych podfunkcje z funkcji z **nazwa** właściwości.|
| Ścieżka dziennika| Ścieżka do pliku dziennika miejscu dostawcy zasobów do operacji logowania.|
| dependsOn| Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.|
| Źródło| Określa lokalizację pliku źródłowego do użycia na potrzeby instalacji, jeśli to konieczne.|

## <a name="example"></a>Przykład

Następująca konfiguracja zapewnia, że **serwera sieci Web** (IIS) i **serwera SMTP** funkcji wraz z wszystkimi podfunkcjami, są zainstalowane.

```powershell
configuration FeatureSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        WindowsFeatureSet WindowsFeatureSetExample
        {
            Name                    = @("SMTP-Server", "Web-Server")
            Ensure                  = 'Present'
            IncludeAllSubFeature    = $true
        }
    }
}
```