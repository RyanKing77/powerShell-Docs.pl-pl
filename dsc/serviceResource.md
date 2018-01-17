---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Zasoby usługi Konfiguracja DSC"
ms.openlocfilehash: a549530edc19496a68c036fecbd18b0072cc6d74
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-service-resource"></a>Zasoby usługi Konfiguracja DSC

> Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0


**Usługi** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm zarządzania usługami w docelowym węźle.

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
| Nazwa| Wskazuje nazwę usługi. Należy pamiętać, że czasami jest inna niż nazwa wyświetlana. Aby uzyskać listę usług i ich bieżącego stanu za pomocą polecenia cmdlet Get-Service.| 
| BuiltInAccount| Wskazuje, że konto logowania do użycia dla usługi. Wartości, które są dozwolone dla tej właściwości to: **Usługa lokalna**, **LocalSystem**, i **NetworkService**.| 
| Poświadczenie| Określa poświadczenia dla konta, na którym będzie uruchamiana usługa. Ta właściwość i __BuiltinAccount__ właściwości nie mogą być używane razem.| 
| dependsOn| Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.| 
| StartupType| Wskazuje typ uruchomienia usługi. Wartości, które są dozwolone dla tej właściwości to: **automatyczne**, **wyłączone**, i **ręczne**| 
| Stan| Wskazuje stan, który chcesz zapewnić usługę.| 
| Opis | Wskazuje opis usługi docelowej.| 
| DisplayName | Wskazuje nazwę wyświetlaną usługi docelowej.| 
| Upewnij się | Wskazuje, czy Usługa docelowa istnieje w systemie. Ta właściwość jest ustawiana **nieobecne** aby upewnić się, że Usługa docelowa nie istnieje. Ustawieniem dla niego **obecny** (wartość domyślna) zapewnia, że istnieje usługi docelowej.|
| Ścieżka | Określa ścieżkę do pliku binarnego nowej usługi.| 

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

