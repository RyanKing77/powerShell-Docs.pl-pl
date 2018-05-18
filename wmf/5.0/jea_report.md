---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 7982acc111e95b4167f948314f176d53f39d3620
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="reporting-on-jea"></a><span data-ttu-id="7a93e-102">Raporty dotyczące usługi JEA</span><span class="sxs-lookup"><span data-stu-id="7a93e-102">Reporting on JEA</span></span>
<span data-ttu-id="7a93e-103">Aby zgłosić stanu konfiguracji JEA, można użyć:</span><span class="sxs-lookup"><span data-stu-id="7a93e-103">In order to report on the state of your JEA configuration, you can use:</span></span>
1.  <span data-ttu-id="7a93e-104">**Get-PSSessionConfiguration** zwraca listę wszystkich zarejestrowanych punktów końcowych na danym komputerze.</span><span class="sxs-lookup"><span data-stu-id="7a93e-104">**Get-PSSessionConfiguration** to return a list of all registered endpoints on a given machine.</span></span>
2.  <span data-ttu-id="7a93e-105">**Get-PSSessionCapability** raport ma dotyczyć możliwości danego użytkownika ma w określonym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="7a93e-105">**Get-PSSessionCapability** to report on the capabilities any given user has on a specific endpoint.</span></span>

<span data-ttu-id="7a93e-106">Oto przykład **Get-PSSessionCapability**:</span><span class="sxs-lookup"><span data-stu-id="7a93e-106">Here’s an example of **Get-PSSessionCapability**:</span></span>
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

<span data-ttu-id="7a93e-107">Raport ma dotyczyć _akcje_ trwało użytkowników podczas sesji JEA, możesz:</span><span class="sxs-lookup"><span data-stu-id="7a93e-107">To report on the _actions_ users took during a JEA session, you can:</span></span>
1. <span data-ttu-id="7a93e-108">Włącz zapisy "over ramię" dla tego punktu końcowego JEA i poszukaj katalogu wykaz pełny dziennik czynności wykonywanych przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="7a93e-108">Enable the "over-the-shoulder" transcripts for that JEA endpoint and consult the transcript directory for a full log of each user's actions</span></span>
2. <span data-ttu-id="7a93e-109">Włączanie logowania modułu programu PowerShell i sprawdź dzienniki zdarzeń programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7a93e-109">Turn on PowerShell module logging and inspect the PowerShell event logs.</span></span>
