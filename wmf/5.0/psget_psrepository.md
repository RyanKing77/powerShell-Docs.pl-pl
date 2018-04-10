---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 269f4112704067f291728e4c1d745d68ec6ccd6f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="register-a-powershell-repository"></a><span data-ttu-id="c46c9-102">Rejestrowanie repozytorium programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="c46c9-102">Register a PowerShell Repository</span></span>
<span data-ttu-id="c46c9-103">Można skonfigurować PowerShellGet działać względem wewnętrznego repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="c46c9-103">You can configure PowerShellGet to operate against internal repositories.</span></span> <span data-ttu-id="c46c9-104">Można to zrobić za pomocą następującymi dodatkami:</span><span class="sxs-lookup"><span data-stu-id="c46c9-104">This is done by using the following additions:</span></span>
- <span data-ttu-id="c46c9-105">Register-PSRepository: Rejestruje repozytorium dla bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c46c9-105">Register-PSRepository: Registers a repository for the current user.</span></span>
- <span data-ttu-id="c46c9-106">Wyrejestruj PSRepository: Usuwa zarejestrowanych repozytorium dla bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c46c9-106">Unregister-PSRepository: Removes a registered repository for the current user.</span></span>
- <span data-ttu-id="c46c9-107">Set-PSRepository: Ustaw wartość dla zarejestrowanego repozytorium.</span><span class="sxs-lookup"><span data-stu-id="c46c9-107">Set-PSRepository: Set values for a registered repository.</span></span>
- <span data-ttu-id="c46c9-108">Get-PSRepository: Pobierz repozytoria wszystkich zarejestrowanych dla bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c46c9-108">Get-PSRepository: Get all registered repositories for the current user.</span></span>

<span data-ttu-id="c46c9-109">Po zarejestrowaniu repozytorium, można użyć modułu Znajdź i zainstaluj moduł do pracy z nim.</span><span class="sxs-lookup"><span data-stu-id="c46c9-109">After a repository is registered, you can use Find-Module and Install-Module to work with it.</span></span>

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