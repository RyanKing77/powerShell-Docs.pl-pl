---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 2fb2e4b0c40322b5ec78fabede22a7e3ecbbd2aa
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093766"
---
# <a name="reporting-on-jea"></a>Raporty dotyczące usługi JEA

W celu raportowania stanu konfiguracji JEA, można użyć:

1. **Get-PSSessionConfiguration** aby powrócić do listy wszystkich zarejestrowanych punkty końcowe na danym komputerze.
1. **Get-PSSessionCapability** Aby sporządzić raport na temat możliwości danego użytkownika ma w określonym punkcie końcowym.

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
