---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób usługi DSC
ms.openlocfilehash: 09571bd0eaa428e7d0bb7a533d6ad1c0c936e2cf
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048377"
---
# <a name="dsc-service-resource"></a>Zasób usługi DSC

> Dotyczy: Program Windows PowerShell 4.0, Windows PowerShell 5.0


**Usługi** zasób w Windows PowerShell Desired State Configuration (DSC) zapewnia mechanizm zarządzania usługami na węzeł docelowy.

## <a name="syntax"></a>Składnia

```
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Path = [string] ]
}
```

## <a name="properties"></a>Właściwości

|  Właściwość  |  Opis   |
|---|---|
| Nazwa| Wskazuje nazwę usługi. Należy pamiętać, że czasami jest inna niż nazwa wyświetlana. Możesz uzyskać listę usług i ich bieżący stan za pomocą polecenia cmdlet Get-Service.|
| BuiltInAccount| Wskazuje, że konto logowania do użycia dla usługi. Wartości, które są dozwolone dla tej właściwości to: **Usługa lokalna**, **LocalSystem**, i **NetworkService**.|
| Poświadczenie| Określa poświadczenia dla konta, które będzie działać usługa. Ta właściwość i __BuiltinAccount__ właściwości nie mogą być używane razem.|
| DependsOn| Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest __ResourceName__ a jej typ jest __ResourceType__, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.|
| StartupType| Wskazuje typ uruchomienia usługi. Wartości, które są dozwolone dla tej właściwości to: **Automatyczne**, **wyłączone**, i **ręczne**|
| Stan| Wskazuje stan, który chcesz zapewnić usługę.|
| Opis | Określa opis usługi docelowej.|
| DisplayName | Określa nazwę wyświetlaną usługi docelowej.|
| Upewnij się | Wskazuje, czy Usługa docelowa istnieje w systemie. Ustaw tę właściwość na **nieobecne** aby upewnić się, że Usługa docelowa nie istnieje. Ustawienie **obecne** (wartość domyślna) gwarantuje, czy istnieje usługa docelowa.|
| Ścieżka | Określa ścieżkę do pliku binarnego dla nowej usługi.|

## <a name="example"></a>Przykład

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```