---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób Windowsfeatureset DSC
ms.openlocfilehash: 8a64168d9ad0d6a6c40eb0398cc734fa93a247dc
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726789"
---
# <a name="dsc-windowsfeatureset-resource"></a>Zasób Windowsfeatureset DSC

> Dotyczy: Windows PowerShell 5.0

**WindowsFeatureSet** zasób w Windows PowerShell Desired State Configuration (DSC) zapewnia mechanizm, aby upewnić się, że role i funkcje są dodawane lub usuwane w węźle docelowym.
Ten zasób jest [złożonego zasobów](../../../resources/authoringResourceComposite.md) wywołująca [zasób WindowsFeature](windowsfeatureResource.md) dla każdej funkcji, określone w `Name` właściwości.

Korzystając z tego zasobu, gdy użytkownik chce skonfigurować pewną liczbę funkcji Windows na tym samym stanie.

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

|  Właściwość  |  Description   |
|---|---|
| Nazwa| Nazwy ról lub funkcji, które chcesz, aby upewnić się, są dodawane lub usuwane. To jest taka sama jak **nazwa** właściwość [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature?view=winserver2012r2-ps) polecenia cmdlet, a nie nazwę wyświetlaną ról lub funkcji.|
| Poświadczenie| Poświadczenia używane do dodawania lub usuwania ról lub funkcji.|
| Upewnij się| Wskazuje, czy dodać ról lub funkcji. Aby upewnić się, że ról lub funkcji dodano, ustaw tę właściwość na "Obecny", aby upewnić się, czy role i funkcje zostały usunięte, należy ustawić właściwość na "Brak".|
| IncludeAllSubFeature| Ustaw tę właściwość na **$true** obejmujący wszystkie wymagane podfunkcje przy użyciu funkcji, należy określić przy użyciu **nazwa** właściwości.|
| Ścieżka dziennika| Ścieżka do pliku dziennika, w której chcesz dostawcy zasobów do dziennika operacji.|
| dependsOn| Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest __ResourceName__ a jej typ jest __ResourceType__, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.|
| Source| Wskazuje lokalizację pliku źródłowego na potrzeby instalacji, jeśli to konieczne.|

## <a name="example"></a>Przykład

Następująca konfiguracja zapewnia, że **serwera sieci Web** (IIS) i **serwera SMTP** funkcji wraz z wszystkimi podfunkcjami każdego, są zainstalowane.

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
