---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
ms.openlocfilehash: 32f8e20889ddc526def4b925e8d0761a2e851e19
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="unified-and-consistent-state-and-status-representation"></a>Ujednolicone i spójny stan i stan reprezentacja

Szereg ulepszeń zostały wprowadzone w tej wersji dla wbudowanych LCM stan i stan usługi Konfiguracja DSC automatyzacji. Obejmują one ujednoliconego i spójny stan i stan oświadczenia, właściwości datetime można zarządzać stan obiektów zwróconych przez polecenie cmdlet Get-DscConfigurationStatus i rozszerzone właściwości szczegółów stanu LCM zwrócony przez Get DscLocalConfigurationManager polecenia cmdlet.

Reprezentacja LCM stan i stan operacji DSC są poprawione i ujednolicone zgodnie z następującymi zasadami:
1.  Notprocessed zasobów nie będzie mieć wpływu LCM stan i stan usługi Konfiguracja DSC.
2.  Zatrzymaj LCM dalsze przetwarzanie zasobów po napotkaniu z zasobem, który żąda ponownego uruchomienia.
3.  Zasób, który żąda ponownego uruchomienia nie jest w żądanym stanie do momentu ponownego uruchomienia wystąpi.
4.  Po napotkaniu zasobu, który zakończy się niepowodzeniem, LCM śledzi dalsze przetwarzanie zasobów tak długo, jak nie są one zależne od awarii jednego.
5.  Ogólne informacje o stanie zwracanych przez polecenie cmdlet Get-DscConfigurationStatus jest superklasą zbiór stanu wszystkich zasobów.
6.  Stan PendingReboot jest nadzbiorem PendingConfiguration stanu.

W poniższej tabeli pokazano wynikowe stan i stan powiązane właściwości w obszarze kilka typowych scenariuszy.

| **Scenariusz**                    | **LCMState\***       | **Stan** | **Wymagane ponowne uruchomienie komputera**  | **ResourcesInDesiredState**  | **ResourcesNotInDesiredState** |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| S**^**                          | W stanie bezczynności                 | Success    | $false        | S                            | $null                          |
| F**^**                          | PendingConfiguration | Niepowodzenie    | $false        | $null                        | F                              |
| S, F                             | PendingConfiguration | Niepowodzenie    | $false        | S                            | F                              |
| F-S                             | PendingConfiguration | Niepowodzenie    | $false        | S                            | F                              |
| S<sub>1</sub>, F, S<sub>2</sub> | PendingConfiguration | Niepowodzenie    | $false        | S<sub>1</sub>, S<sub>2</sub> | F                              |
| F<sub>1</sub>, S, F<sub>2</sub> | PendingConfiguration | Niepowodzenie    | $false        | S                            | F<sub>1</sub>, F<sub>2</sub>   |
| S, r                            | PendingReboot        | Success    | $true         | S                            | r                              |
| F, r                            | PendingReboot        | Niepowodzenie    | $true         | $null                        | F, r                           |
| r, S                            | PendingReboot        | Success    | $true         | $null                        | r                              |
| r, F                            | PendingReboot        | Success    | $true         | $null                        | r                              |

^ S<sub>i</sub>: szeregu zasobów, które zostały zastosowane F<sub>i</sub>: szeregu zasobów, które są stosowane niepomyślnie r: A zasobem, który wymaga ponownego uruchomienia\*

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```
## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a>Rozszerzenie w poleceniu cmdlet Get-DscConfigurationStatus

Polecenie cmdlet Get-DscConfigurationStatus w tej wersji wprowadzono kilka ulepszeń. Wcześniej właściwość data_rozpoczęcia obiektów zwróconych przez polecenie cmdlet jest typu String. Teraz jest typu Data/Godzina, dzięki czemu złożonych, wybierając i filtrowanie łatwiej na podstawie wewnętrznych właściwości obiektu Datetime.
```powershell
(Get-DscConfigurationStatus).StartDate | fl \*
DateTime : Friday, November 13, 2015 1:39:44 PM
Date : 11/13/2015 12:00:00 AM
Day : 13
DayOfWeek : Friday
DayOfYear : 317
Hour : 13
Kind : Local
Millisecond : 886
Minute : 39
Month : 11
Second : 44
Ticks : 635830187848860000
TimeOfDay : 13:39:44.8860000
Year : 2015
```

Poniżej przedstawiono przykład zwraca wszystkie rekordy operacji DSC się stało z tego samego dnia, tygodnia, w obecnie.
```powershell
(Get-DscConfigurationStatus –All) | where { $\_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

Rejestruje operacje, które nie należy wprowadzać zmian w konfiguracji węzła (tj. tylko operacje odczytu) są eliminowane. W związku z tym Test-DscConfiguration operacji Get-DscConfiguration są już zafałszowane za w zwróciło obiektów z polecenia cmdlet Get-DscConfigurationStatus.
Rekordy operacji określania ustawień konfiguracji metadanych jest dodawana do powrotu polecenia cmdlet Get-DscConfigurationStatus.

Poniżej przedstawiono przykładowy wynik zwracany z Get-DscConfigurationStatus — wszystkie polecenia cmdlet.
```powershell
All configuration operations:

Status StartDate Type RebootRequested
------ --------- ---- ---------------
Success 11/13/2015 11:38:16 AM Consistency False
Success 11/13/2015 11:23:16 AM Reboot False
Success 11/13/2015 11:21:43 AM Reboot True
Success 11/13/2015 11:20:44 AM Initial True
Success 11/13/2015 11:20:44 AM LocalConfigurationManager False
```

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a>Rozszerzenie w poleceniu cmdlet Get-DscLocalConfigurationManager
Nowe pole LCMStateDetail jest dodawany do obiektu zwróconego z polecenia cmdlet Get-DscLocalConfigurationManager. To pole jest wypełniane podczas LCMState jest "Zajęty". Mogą być pobierane przez następujące polecenie cmdlet:
```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

Poniżej przedstawiono przykładowe dane wyjściowe ciągłego monitorowania w konfiguracji, która wymaga ponownego uruchomienia w węźle zdalnym.
```powershell
Start a configuration that requires two reboots

Monitor LCM State:
LCM State: Busy, LCM is applying a new configuration.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: Idle,
LCM State: Busy, LCM is performing a consistency check.
LCM State: Idle,
```

