---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 5ac9566979e1b761249f5cc7c62ed44047a2b9f6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058016"
---
# <a name="register-a-powershell-repository"></a><span data-ttu-id="290c7-102">Rejestrowanie repozytorium programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="290c7-102">Register a PowerShell Repository</span></span>
<span data-ttu-id="290c7-103">Można skonfigurować modułu PowerShellGet działać względem wewnętrznego repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="290c7-103">You can configure PowerShellGet to operate against internal repositories.</span></span> <span data-ttu-id="290c7-104">Można to zrobić, korzystając z następującymi dodatkami:</span><span class="sxs-lookup"><span data-stu-id="290c7-104">This is done by using the following additions:</span></span>
- <span data-ttu-id="290c7-105">Register-PSRepository: Rejestruje repozytorium dla bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="290c7-105">Register-PSRepository: Registers a repository for the current user.</span></span>
- <span data-ttu-id="290c7-106">Wyrejestruj PSRepository: Usuwa zarejestrowanego repozytorium dla bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="290c7-106">Unregister-PSRepository: Removes a registered repository for the current user.</span></span>
- <span data-ttu-id="290c7-107">Set-PSRepository: Ustaw wartość dla zarejestrowanego repozytorium.</span><span class="sxs-lookup"><span data-stu-id="290c7-107">Set-PSRepository: Set values for a registered repository.</span></span>
- <span data-ttu-id="290c7-108">Get-PSRepository: Pobierz wszystkie zarejestrowane repozytoria dla bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="290c7-108">Get-PSRepository: Get all registered repositories for the current user.</span></span>

<span data-ttu-id="290c7-109">Po zarejestrowaniu repozytorium, można użyć Find-Module i Install-Module z nią pracować.</span><span class="sxs-lookup"><span data-stu-id="290c7-109">After a repository is registered, you can use Find-Module and Install-Module to work with it.</span></span>

```powershell
\#Register a default repository
Register-PSRepository –Name DemoRepo –SourceLocation “https://www.myget.org/F/powershellgetdemo/api/v2” –PublishLocation “<https://www.myget.org/F/powershellgetdemo/api/v2>/package” –InstallationPolicy –Trusted

\#Get all of the registered repositories
Get-PSRepository
Name SourceLocation
---- --------------
PSGallery https://msconfiggallery.cloudapp...
DemoRepo https://www.myget.org/F/powershe...

\#Search only the new repository for modules
Find-Module -Repository DemoRepo
Repository Version Name
---------- ------- ----
DemoRepo 1.0.1 xActiveDirectory
DemoRepo 1.1.1 SomeModule

\#By default, PowerShellGet operates against all registered repositories when none is specified. In this example, the “SomeModule” module is installed from the DemoRepo.
Install-Module SomeModule

\#Removing a repository
Unregister-PSRepository DemoRepo
```
