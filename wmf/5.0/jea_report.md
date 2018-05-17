---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 7982acc111e95b4167f948314f176d53f39d3620
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="reporting-on-jea"></a>Raporty dotyczące usługi JEA
Aby zgłosić stanu konfiguracji JEA, można użyć:
1.  **Get-PSSessionConfiguration** zwraca listę wszystkich zarejestrowanych punktów końcowych na danym komputerze.
2.  **Get-PSSessionCapability** raport ma dotyczyć możliwości danego użytkownika ma w określonym punkcie końcowym.

Oto przykład **Get-PSSessionCapability**:
```powershell
Get-PSSessionCapability -ConfigurationName Maintenance -Username "CONTOSO\JohnDoe"

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           clear -> Clear-Host
Alias           cls -> Clear-Host
Alias           exsn -> Exit-PSSession
Alias           gcm -> Get-Command
Alias           measure -> Measure-Object
Alias           select -> Select-Object
Function        Clear-Host
Function        Exit-PSSession
Function        Get-Command
Function        Get-FormatData
Function        Get-Help
Function        Get-UserInfo
Function        Measure-Object
Function        Out-Default
Function        Select-Object
Cmdlet          Restart-Service                                    3.0.0.0 Microsof...


```

Raport ma dotyczyć _akcje_ trwało użytkowników podczas sesji JEA, możesz:
1. Włącz zapisy "over ramię" dla tego punktu końcowego JEA i poszukaj katalogu wykaz pełny dziennik czynności wykonywanych przez użytkownika
2. Włączanie logowania modułu programu PowerShell i sprawdź dzienniki zdarzeń programu PowerShell.
