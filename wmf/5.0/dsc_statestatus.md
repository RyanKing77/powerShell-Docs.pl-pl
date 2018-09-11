---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: ff2c2bd7369893d72db001ecabf63991ded0bfd5
ms.sourcegitcommit: ac20e0faaa37142e9c6e4507a21df2f4a3fdbece
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44339875"
---
# <a name="unified-and-consistent-state-and-status-representation"></a>Ujednolicony i spójny stan oraz reprezentacja stanu

Szereg ulepszeń zostały wprowadzone w tym wydaniu automatyzacji stanu LCM i stan DSC. Obejmują one ujednolicony i spójny stan i stan reprezentacje datetime w zarządzaniu własności stan obiektów zwróconych przez `Get-DscConfigurationStatus` LCM rozszerzone i polecenia cmdlet stanu szczegóły właściwości zwróconej przez `Get-DscLocalConfigurationManager` polecenia cmdlet.

Reprezentacja stanu LCM i stan operacji dla DSC są poprawiony i ujednolicone zgodnie z następującymi zasadami:

1. Notprocessed zasobów nie ma wpływu na stanu LCM i stan DSC.
2. LCM zatrzymać dalsze zasoby przetwarzanie po napotkaniu zasobem, który żąda ponownego uruchomienia.
3. Zasób, który żąda ponownego rozruchu nie jest w żądanym stanie do momentu ponownego uruchomienia rzeczywiście się dzieje.
4. Po napotkaniu zasobem, który zakończy się niepowodzeniem, LCM utrzymuje dalsze przetwarzanie zasobów tak długo, jak nie są zależne od awarii jednej.
5. Ogólny stan zwrócony przez `Get-DscConfigurationStatus` polecenie cmdlet jest zbiór super stanu wszystkich zasobów.
6. Stan PendingReboot jest nadzbiorem PendingConfiguration stanu.

W poniższej tabeli przedstawiono wynikowe stanu i statusu powiązane właściwości pod kilka typowych scenariuszy.

| Scenariusz                        | LCMState             | Stan     | Wymagane ponowne uruchomienie komputera | ResourcesInDesiredState   | ResourcesNotInDesiredState |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| S<sub>i</sub>                   | W stanie bezczynności                 | Success    | $false        | S                            | $null                          |
| F<sub>i</sub>                   | PendingConfiguration | Niepowodzenie    | $false        | $null                        | F                              |
| S, F                             | PendingConfiguration | Niepowodzenie    | $false        | S                            | F                              |
| F, S                             | PendingConfiguration | Niepowodzenie    | $false        | S                            | F                              |
| S<sub>1</sub>, F, S<sub>2</sub> | PendingConfiguration | Niepowodzenie    | $false        | S<sub>1</sub>, S<sub>2</sub> | F                              |
| F<sub>1</sub>, S, F<sub>2</sub> | PendingConfiguration | Niepowodzenie    | $false        | S                            | F<sub>1</sub>, F<sub>2</sub>   |
| S, r                            | PendingReboot        | Success    | $true         | S                            | r                              |
| F, r                            | PendingReboot        | Niepowodzenie    | $true         | $null                        | F, r                           |
| r, S                            | PendingReboot        | Success    | $true         | $null                        | r                              |
| r, F                            | PendingReboot        | Success    | $true         | $null                        | r                              |

- S<sub>i</sub>: szeregu zasobów, które zostały zastosowane pomyślnie
- F<sub>i</sub>: szeregu zasobów, które stosowane niepomyślnie
- r: z zasobem, który wymaga ponownego uruchomienia

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a>Rozszerzenie w poleceniu cmdlet Get-DscConfigurationStatus

Wprowadzono kilka ulepszeń `Get-DscConfigurationStatus` polecenia cmdlet w tej wersji. Wcześniej StartDate własności obiektów zwróconych przez polecenie cmdlet jest typu String. Teraz jest typu Data/Godzina, co umożliwia złożonych, wybieranie i filtrowanie, łatwiej na podstawie wewnętrzne właściwości obiektu daty/godziny.

```powershell
(Get-DscConfigurationStatus).StartDate | Format-List *

DateTime    : Friday, November 13, 2015 1:39:44 PM
Date        : 11/13/2015 12:00:00 AM
Day         : 13
DayOfWeek   : Friday
DayOfYear   : 317
Hour        : 13
Kind        : Local
Millisecond : 886
Minute      : 39
Month       : 11
Second      : 44
Ticks       : 635830187848860000
TimeOfDay   : 13:39:44.8860000
Year        : 2015
```

Poniższy przykład zwraca wszystkie rekordy operacji DSC, które miały miejsce tego samego dnia, tygodnia jako bieżący dzień.

```powershell
(Get-DscConfigurationStatus –All) | Where-Object { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

Rejestruje operacje, które należy wprowadzać zmian w konfiguracji węzła (tj. tylko operacji odczytu) są eliminowane. W związku z tym `Test-DscConfiguration`, `Get-DscConfiguration` operacje są już zafałszowane za w zwracanych obiektów z `Get-DscConfigurationStatus` polecenia cmdlet. Rekordy operacja ustawienie konfiguracji metadanych jest dodawana do powrotu `Get-DscConfigurationStatus` polecenia cmdlet.

Poniżej znajduje się przykład wyniku zwracanego z `Get-DscConfigurationStatus –All` polecenia cmdlet.

```output
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

Nowe pole LCMStateDetail zostanie dodany do obiektu zwróconego z `Get-DscLocalConfigurationManager` polecenia cmdlet. To pole jest wypełniane podczas LCMState jest "Zajęty". Mogą być pobierane przez następujące polecenie cmdlet:

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

Poniżej przedstawiono przykładowe dane wyjściowe ciągłego monitorowania w konfiguracji, która wymaga ponownego uruchomienia w węźle zdalnym.

```output
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
