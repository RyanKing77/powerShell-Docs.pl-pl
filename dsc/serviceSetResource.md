---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasób ServiceSet DSC
ms.openlocfilehash: 1f879d2eafeb11e69968252a11f0c550c9b103f3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-serviceset-resource"></a>Zasób ServiceSet DSC

> Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0


**ServiceSet** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm zarządzania usługami w docelowym węźle. Ten zasób jest [złożonego zasobów](authoringResourceComposite.md) wywołującym [usługi zasobów](serviceResource.md) dla każdej usługi określone w `Name` właściwości.

Jeśli chcesz skonfigurować liczbę usług do tego samego stanu, należy użyć tego zasobu.

## <a name="syntax"></a>Składnia

```
Service [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a>Właściwości

|  Właściwość  |  Opis   |
|---|---|
| Nazwa| Wskazuje nazwy usługi. Należy pamiętać, że czasami to różni się od nazwy wyświetlane. Można uzyskać listę usług i ich bieżącego stanu z [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) polecenia cmdlet.|
| StartupType| Wskazuje typ uruchomienia usługi. Wartości, które są dozwolone dla tej właściwości to: **automatyczne**, **wyłączone**, i **ręczne**|
| BuiltInAccount| Wskazuje, że konto logowania dla usługi. Wartości, które są dozwolone dla tej właściwości to: **Usługa lokalna**, **LocalSystem**, i **NetworkService**.|
| Stan| Wskazuje stan chcesz zapewnić usługę: **zatrzymane** lub **systemem**.|
| Upewnij się| Wskazuje, czy istnieją usługi w systemie. Ta właściwość jest ustawiana **nieobecne** aby upewnić się, że nie istnieją usługi. Ustawieniem dla niego **obecny** (wartość domyślna) zapewnia, że istnieją usługi docelowej.|
| Poświadczenie| Określa poświadczenia dla konta, na którym będzie uruchamiana zasobów usługi. Ta właściwość i **BuiltinAccount** właściwości nie mogą być używane razem.|
| dependsOn| Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest *ResourceName* i jej typ jest *ResourceType*, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.|



## <a name="example"></a>Przykład

Następującej konfiguracji uruchamiania usługi "Windows Audio" i "Usług pulpitu zdalnego".

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```