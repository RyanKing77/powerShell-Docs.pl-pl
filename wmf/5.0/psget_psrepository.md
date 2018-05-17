---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9a9bdac652512640209c20e3deb20d7abc0142c6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="register-a-powershell-repository"></a>Rejestrowanie repozytorium programu PowerShell
Można skonfigurować PowerShellGet działać względem wewnętrznego repozytoriów. Można to zrobić za pomocą następującymi dodatkami:
- Register-PSRepository: Rejestruje repozytorium dla bieżącego użytkownika.
- Wyrejestruj PSRepository: Usuwa zarejestrowanych repozytorium dla bieżącego użytkownika.
- Set-PSRepository: Ustaw wartość dla zarejestrowanego repozytorium.
- Get-PSRepository: Pobierz repozytoria wszystkich zarejestrowanych dla bieżącego użytkownika.

Po zarejestrowaniu repozytorium, można użyć modułu Znajdź i zainstaluj moduł do pracy z nim.

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
