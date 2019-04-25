---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: cd3338ae305896e282056a871974e5f899ef6ff5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085264"
---
# <a name="reporting-on-jea"></a><span data-ttu-id="2c755-102">Raporty dotyczące usługi JEA</span><span class="sxs-lookup"><span data-stu-id="2c755-102">Reporting on JEA</span></span>

<span data-ttu-id="2c755-103">W celu raportowania stanu konfiguracji JEA, można użyć:</span><span class="sxs-lookup"><span data-stu-id="2c755-103">In order to report on the state of your JEA configuration, you can use:</span></span>

1. <span data-ttu-id="2c755-104">**Get-PSSessionConfiguration** aby powrócić do listy wszystkich zarejestrowanych punkty końcowe na danym komputerze.</span><span class="sxs-lookup"><span data-stu-id="2c755-104">**Get-PSSessionConfiguration** to return a list of all registered endpoints on a given machine.</span></span>
2. <span data-ttu-id="2c755-105">**Get-PSSessionCapability** Aby sporządzić raport na temat możliwości danego użytkownika ma w określonym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="2c755-105">**Get-PSSessionCapability** to report on the capabilities any given user has on a specific endpoint.</span></span>

<span data-ttu-id="2c755-106">Oto przykład **Get PSSessionCapability**:</span><span class="sxs-lookup"><span data-stu-id="2c755-106">Here's an example of **Get-PSSessionCapability**:</span></span>

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

<span data-ttu-id="2c755-107">Aby sporządzić raport na temat _akcje_ użytkowników trwało podczas sesji JEA, możesz:</span><span class="sxs-lookup"><span data-stu-id="2c755-107">To report on the _actions_ users took during a JEA session, you can:</span></span>

1. <span data-ttu-id="2c755-108">Włącz zapisów "over ramię" dla tego punktu końcowego JEA i poszukaj katalogu transkrypcji pełny dziennik akcji każdego użytkownika</span><span class="sxs-lookup"><span data-stu-id="2c755-108">Enable the "over-the-shoulder" transcripts for that JEA endpoint and consult the transcript directory for a full log of each user's actions</span></span>
2. <span data-ttu-id="2c755-109">Włączanie logowania modułu programu PowerShell i sprawdź dzienniki zdarzeń programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2c755-109">Turn on PowerShell module logging and inspect the PowerShell event logs.</span></span>