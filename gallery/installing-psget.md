---
ms.date: 06/12/2017
contributor: manikb
keywords: Galeria, PowerShell, cmdlet, psget
title: Instalowanie menedżera pakietów PowerShellGet
ms.openlocfilehash: 2d3ba8c4d4d4c7ee023c7e6a948a29d8f47ea242
ms.sourcegitcommit: 8d47eb41445ffaf10fcd68874e397c9a1703d898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/29/2019
ms.locfileid: "68601414"
---
# <a name="installing-powershellget"></a><span data-ttu-id="bd01e-103">Instalowanie menedżera pakietów PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="bd01e-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="bd01e-104">PowerShellGet to moduł wbudowany w następujących wersjach</span><span class="sxs-lookup"><span data-stu-id="bd01e-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="bd01e-105">[System Windows 10](https://www.microsoft.com/windows) lub nowszy</span><span class="sxs-lookup"><span data-stu-id="bd01e-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="bd01e-106">[System Windows Server 2016](/windows-server/windows-server) lub nowszy</span><span class="sxs-lookup"><span data-stu-id="bd01e-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="bd01e-107">[Windows Management Framework (WMF) 5,0](https://www.microsoft.com/download/details.aspx?id=50395) lub nowszy</span><span class="sxs-lookup"><span data-stu-id="bd01e-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="bd01e-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="bd01e-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a><span data-ttu-id="bd01e-109">Pobierz moduł PowerShellGet dla programu PowerShell w wersji 3,0 i 4,0</span><span class="sxs-lookup"><span data-stu-id="bd01e-109">Get PowerShellGet module for PowerShell versions 3.0 and 4.0</span></span>

- [<span data-ttu-id="bd01e-110">PackageManagement MSI</span><span class="sxs-lookup"><span data-stu-id="bd01e-110">PackageManagement MSI</span></span>](https://www.microsoft.com/download/details.aspx?id=51451)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="bd01e-111">Pobierz najnowszą wersję z Galeria programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="bd01e-111">Get the latest version from PowerShell Gallery</span></span>

- <span data-ttu-id="bd01e-112">Przed aktualizacją PowerShellGet należy zawsze zainstalować najnowszego dostawcę NuGet.</span><span class="sxs-lookup"><span data-stu-id="bd01e-112">Before updating PowerShellGet, you should always install the latest Nuget provider.</span></span> <span data-ttu-id="bd01e-113">Aby to zrobić, uruchom następujące polecenie w sesji programu PowerShell z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="bd01e-113">To do that, run the following in an elevated PowerShell session.</span></span>

  ```powershell
  Install-PackageProvider Nuget -Force
  Exit
  ```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="bd01e-114">W przypadku systemów z programem PowerShell 5,0 (lub nowszym) można zainstalować najnowszą PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="bd01e-114">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

- <span data-ttu-id="bd01e-115">W tym celu w systemie Windows 10, Windows Server 2016, dowolnym systemie, w którym zainstalowano program WMF 5,0 lub 5,1, lub dowolnego systemu z programem PowerShell 6 Uruchom następujące polecenia w sesji programu PowerShell z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="bd01e-115">To do this on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

  ```powershell
  Install-Module -Name PowerShellGet -Force
  Exit
  ```

- <span data-ttu-id="bd01e-116">Użyj `Update-Module` , aby uzyskać nowsze wersje.</span><span class="sxs-lookup"><span data-stu-id="bd01e-116">Use `Update-Module` to get newer versions.</span></span>

  ```powershell
  Update-Module -Name PowerShellGet
  Exit
  ```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpswwwmicrosoftcomdownloaddetailsaspxid51451"></a><span data-ttu-id="bd01e-117">W przypadku systemów z uruchomionym programem PowerShell 3 lub PowerShell 4, który zainstalował plik [MSI PackageManagement](https://www.microsoft.com/download/details.aspx?id=51451)</span><span class="sxs-lookup"><span data-stu-id="bd01e-117">For systems running PowerShell 3 or PowerShell 4, that have installed the [PackageManagement MSI](https://www.microsoft.com/download/details.aspx?id=51451)</span></span>

- <span data-ttu-id="bd01e-118">Użyj poniższego polecenia cmdlet PowerShellGet z sesji programu PowerShell z podwyższonym poziomem uprawnień, aby zapisać moduły w katalogu lokalnym</span><span class="sxs-lookup"><span data-stu-id="bd01e-118">Use below PowerShellGet cmdlet from an elevated PowerShell session to save the modules to a local directory</span></span>

  ```powershell
  Save-Module PowerShellGet -Path C:\LocalFolder
  Exit
  ```

- <span data-ttu-id="bd01e-119">Upewnij się, że moduły PowerShellGet i PackageManagement nie są załadowane w żadnym innym procesie.</span><span class="sxs-lookup"><span data-stu-id="bd01e-119">Ensure that PowerShellGet and PackageManagement modules are not loaded in any other processes.</span></span>
- <span data-ttu-id="bd01e-120">Usuń zawartość `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` i `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` foldery.</span><span class="sxs-lookup"><span data-stu-id="bd01e-120">Delete contents of `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and  `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` folders.</span></span>
- <span data-ttu-id="bd01e-121">Ponownie otwórz konsolę PS z podwyższonym poziomem uprawnień, a następnie uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="bd01e-121">Re-open the PS Console with elevated permissions then run the following commands.</span></span>

  ```powershell
  Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
  Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
  ```
