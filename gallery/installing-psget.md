---
ms.date: 06/12/2017
contributor: manikb
keywords: Galeria, programu powershell, polecenia cmdlet, psget
title: Instalowanie menedżera pakietów PowerShellGet
ms.openlocfilehash: 35be7d02ea856ea39218f05d32b43c60fa1bd53e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219355"
---
# <a name="installing-powershellget"></a><span data-ttu-id="2e246-103">Instalowanie menedżera pakietów PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="2e246-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="2e246-104">W polu modułu w następujących wersjach jest PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="2e246-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="2e246-105">[Windows 10](https://www.microsoft.com/windows/get-windows-10) lub nowsza</span><span class="sxs-lookup"><span data-stu-id="2e246-105">[Windows 10](https://www.microsoft.com/windows/get-windows-10) or newer</span></span>
- <span data-ttu-id="2e246-106">[Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/windows-server-2016) lub nowsza</span><span class="sxs-lookup"><span data-stu-id="2e246-106">[Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/windows-server-2016) or newer</span></span>
- <span data-ttu-id="2e246-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) lub nowsza</span><span class="sxs-lookup"><span data-stu-id="2e246-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="2e246-108">6 programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="2e246-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a><span data-ttu-id="2e246-109">Pobieranie modułu PowerShellGet dla środowiska PowerShell w wersji 3.0 i 4.0</span><span class="sxs-lookup"><span data-stu-id="2e246-109">Get PowerShellGet module for PowerShell versions 3.0 and 4.0</span></span>

- [<span data-ttu-id="2e246-110">PackageManagement MSI</span><span class="sxs-lookup"><span data-stu-id="2e246-110">PackageManagement MSI</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="2e246-111">Pobierz najnowszą wersję z galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="2e246-111">Get the latest version from PowerShell Gallery</span></span>

- <span data-ttu-id="2e246-112">Przed zaktualizowaniem PowerShellGet, zawsze należy zainstalować najnowszą wersję dostawcy Nuget.</span><span class="sxs-lookup"><span data-stu-id="2e246-112">Before updating PowerShellGet, you should always install the latest Nuget provider.</span></span> <span data-ttu-id="2e246-113">Aby to zrobić, uruchom następujące polecenie w sesji programu PowerShell z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="2e246-113">To do that, run the following in an elevated PowerShell session.</span></span>

```powershell
Install-PackageProvider Nuget –Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="2e246-114">Dla systemów z programu PowerShell w wersji 5.0 (lub nowsza) można zainstalować najnowsze PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="2e246-114">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

- <span data-ttu-id="2e246-115">Aby to zrobić w systemie Windows 10, Windows Server 2016, każdy system WMF 5.0 lub 5.1 zainstalowany lub każdy system 6 programu PowerShell, uruchom następujące polecenia z sesji programu PowerShell z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="2e246-115">To do this on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

```powershell
Install-Module –Name PowerShellGet –Force
Exit
```

- <span data-ttu-id="2e246-116">Użyj modułu aktualizacji, aby uzyskać nowsze wersje.</span><span class="sxs-lookup"><span data-stu-id="2e246-116">Use Update-Module to get newer versions.</span></span>

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpgomicrosoftcomfwlinklinkid746217clcid0x409"></a><span data-ttu-id="2e246-117">Dla systemami PowerShell 3 lub 4 programu PowerShell, który został zainstalowany [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="2e246-117">For systems running PowerShell 3 or PowerShell 4, that have installed the [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)</span></span>

- <span data-ttu-id="2e246-118">Użyj poniżej polecenia cmdlet PowerShellGet z sesji programu PowerShell z podwyższonym poziomem uprawnień, aby zapisać modułów do katalogu lokalnego</span><span class="sxs-lookup"><span data-stu-id="2e246-118">Use below PowerShellGet cmdlet from an elevated PowerShell session to save the modules to a local directory</span></span>

```powershell
Save-Module PowerShellGet -Path C:\LocalFolder
Exit
```

- <span data-ttu-id="2e246-119">Upewnij się, że PowerShellGet i PackageManagment moduły nie załadowano żadnych innych procesów.</span><span class="sxs-lookup"><span data-stu-id="2e246-119">Ensure that PowerShellGet and PackageManagment modules are not loaded in any other processes.</span></span>
- <span data-ttu-id="2e246-120">Usuń zawartość `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` i `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` folderów.</span><span class="sxs-lookup"><span data-stu-id="2e246-120">Delete contents of `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and  `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` folders.</span></span>
- <span data-ttu-id="2e246-121">Ponownie otwórz konsolę PS z podwyższonym poziomem uprawnień, a następnie uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="2e246-121">Re-open the PS Console with elevated permissions then run the following commands.</span></span>

```powershell
Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
```