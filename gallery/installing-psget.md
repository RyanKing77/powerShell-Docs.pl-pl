---
ms.date: 06/12/2017
contributor: manikb
keywords: Galeria, programu powershell, polecenie cmdlet, psget
title: Instalowanie menedżera pakietów PowerShellGet
ms.openlocfilehash: c385f7fbf6b688a11face9c3ebf4e6475a7b4c33
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893964"
---
# <a name="installing-powershellget"></a><span data-ttu-id="c3d46-103">Instalowanie menedżera pakietów PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="c3d46-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="c3d46-104">Moduł PowerShellGet jest moduł skrzynkach odbiorczych w następujących wersjach</span><span class="sxs-lookup"><span data-stu-id="c3d46-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="c3d46-105">[Windows 10](https://www.microsoft.com/en-us/windows) lub nowszej</span><span class="sxs-lookup"><span data-stu-id="c3d46-105">[Windows 10](https://www.microsoft.com/en-us/windows) or newer</span></span>
- <span data-ttu-id="c3d46-106">[System Windows Server 2016](/windows-server/windows-server) lub nowszej</span><span class="sxs-lookup"><span data-stu-id="c3d46-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="c3d46-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) lub nowszej</span><span class="sxs-lookup"><span data-stu-id="c3d46-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="c3d46-108">Program PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="c3d46-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a><span data-ttu-id="c3d46-109">Uzyskiwanie modułu PowerShellGet w przypadku programu PowerShell w wersji 3.0 i 4.0</span><span class="sxs-lookup"><span data-stu-id="c3d46-109">Get PowerShellGet module for PowerShell versions 3.0 and 4.0</span></span>

- [<span data-ttu-id="c3d46-110">Funkcja PackageManagement MSI</span><span class="sxs-lookup"><span data-stu-id="c3d46-110">PackageManagement MSI</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=51451)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="c3d46-111">Pobierz najnowszą wersję z galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="c3d46-111">Get the latest version from PowerShell Gallery</span></span>

- <span data-ttu-id="c3d46-112">Przed zaktualizowaniem modułu PowerShellGet, należy zawsze instalować najnowszego dostawcę Nuget.</span><span class="sxs-lookup"><span data-stu-id="c3d46-112">Before updating PowerShellGet, you should always install the latest Nuget provider.</span></span> <span data-ttu-id="c3d46-113">Aby to zrobić, uruchom następujące polecenie w sesji programu PowerShell z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="c3d46-113">To do that, run the following in an elevated PowerShell session.</span></span>

  ```powershell
  Install-PackageProvider Nuget –Force
  Exit
  ```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="c3d46-114">Dla systemów z programu PowerShell w wersji 5.0 (lub nowsza) można zainstalować najnowszy moduł PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="c3d46-114">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

- <span data-ttu-id="c3d46-115">Aby to zrobić w systemie Windows 10, Windows Server 2016, każdy system WMF 5.0 lub 5.1 zainstalowane lub dowolnego systemu przy użyciu programu PowerShell 6 Uruchom następujące polecenia w sesji programu PowerShell z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="c3d46-115">To do this on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

  ```powershell
  Install-Module –Name PowerShellGet –Force
  Exit
  ```

- <span data-ttu-id="c3d46-116">Użyj `Update-Module` można pobrać nowsze wersje.</span><span class="sxs-lookup"><span data-stu-id="c3d46-116">Use `Update-Module` to get newer versions.</span></span>

  ```powershell
  Update-Module -Name PowerShellGet
  Exit
  ```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpswwwmicrosoftcomen-usdownloaddetailsaspxid51451"></a><span data-ttu-id="c3d46-117">Dla komputerów z systemami program PowerShell 3 lub 4 programu PowerShell, który został zainstalowany [MSI funkcji PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=51451)</span><span class="sxs-lookup"><span data-stu-id="c3d46-117">For systems running PowerShell 3 or PowerShell 4, that have installed the [PackageManagement MSI](https://www.microsoft.com/en-us/download/details.aspx?id=51451)</span></span>

- <span data-ttu-id="c3d46-118">Użyć poniższego polecenia cmdlet PowerShellGet sesję programu PowerShell z podwyższonym poziomem uprawnień do zapisania modułów do katalogu lokalnego</span><span class="sxs-lookup"><span data-stu-id="c3d46-118">Use below PowerShellGet cmdlet from an elevated PowerShell session to save the modules to a local directory</span></span>

  ```powershell
  Save-Module PowerShellGet -Path C:\LocalFolder
  Exit
  ```

- <span data-ttu-id="c3d46-119">Upewnij się, modułu PowerShellGet oraz spełnione PackageManagment modułów nie są ładowane w żadnych innych procesów.</span><span class="sxs-lookup"><span data-stu-id="c3d46-119">Ensure that PowerShellGet and PackageManagment modules are not loaded in any other processes.</span></span>
- <span data-ttu-id="c3d46-120">Usuń zawartość `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` i `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` folderów.</span><span class="sxs-lookup"><span data-stu-id="c3d46-120">Delete contents of `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and  `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` folders.</span></span>
- <span data-ttu-id="c3d46-121">Ponownie otwórz konsolę PS z podwyższonym poziomem uprawnień, a następnie uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="c3d46-121">Re-open the PS Console with elevated permissions then run the following commands.</span></span>

  ```powershell
  Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
  Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
  ```