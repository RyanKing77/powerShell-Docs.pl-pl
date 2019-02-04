---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: cd3338ae305896e282056a871974e5f899ef6ff5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686243"
---
# <a name="reporting-on-jea"></a>Raporty dotyczące usługi JEA

W celu raportowania stanu konfiguracji JEA, można użyć:

1. **Get-PSSessionConfiguration** aby powrócić do listy wszystkich zarejestrowanych punkty końcowe na danym komputerze.
2. **Get-PSSessionCapability** Aby sporządzić raport na temat możliwości danego użytkownika ma w określonym punkcie końcowym.

Oto przykład **Get PSSessionCapability**:

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

Aby sporządzić raport na temat _akcje_ użytkowników trwało podczas sesji JEA, możesz:

1. Włącz zapisów "over ramię" dla tego punktu końcowego JEA i poszukaj katalogu transkrypcji pełny dziennik akcji każdego użytkownika
2. Włączanie logowania modułu programu PowerShell i sprawdź dzienniki zdarzeń programu PowerShell.