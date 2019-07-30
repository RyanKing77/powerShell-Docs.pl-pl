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
# <a name="installing-powershellget"></a>Instalowanie menedżera pakietów PowerShellGet

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>PowerShellGet to moduł wbudowany w następujących wersjach

- [System Windows 10](https://www.microsoft.com/windows) lub nowszy
- [System Windows Server 2016](/windows-server/windows-server) lub nowszy
- [Windows Management Framework (WMF) 5,0](https://www.microsoft.com/download/details.aspx?id=50395) lub nowszy
- [PowerShell 6](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a>Pobierz moduł PowerShellGet dla programu PowerShell w wersji 3,0 i 4,0

- [PackageManagement MSI](https://www.microsoft.com/download/details.aspx?id=51451)

## <a name="get-the-latest-version-from-powershell-gallery"></a>Pobierz najnowszą wersję z Galeria programu PowerShell

- Przed aktualizacją PowerShellGet należy zawsze zainstalować najnowszego dostawcę NuGet. Aby to zrobić, uruchom następujące polecenie w sesji programu PowerShell z podwyższonym poziomem uprawnień.

  ```powershell
  Install-PackageProvider Nuget -Force
  Exit
  ```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>W przypadku systemów z programem PowerShell 5,0 (lub nowszym) można zainstalować najnowszą PowerShellGet

- W tym celu w systemie Windows 10, Windows Server 2016, dowolnym systemie, w którym zainstalowano program WMF 5,0 lub 5,1, lub dowolnego systemu z programem PowerShell 6 Uruchom następujące polecenia w sesji programu PowerShell z podwyższonym poziomem uprawnień.

  ```powershell
  Install-Module -Name PowerShellGet -Force
  Exit
  ```

- Użyj `Update-Module` , aby uzyskać nowsze wersje.

  ```powershell
  Update-Module -Name PowerShellGet
  Exit
  ```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpswwwmicrosoftcomdownloaddetailsaspxid51451"></a>W przypadku systemów z uruchomionym programem PowerShell 3 lub PowerShell 4, który zainstalował plik [MSI PackageManagement](https://www.microsoft.com/download/details.aspx?id=51451)

- Użyj poniższego polecenia cmdlet PowerShellGet z sesji programu PowerShell z podwyższonym poziomem uprawnień, aby zapisać moduły w katalogu lokalnym

  ```powershell
  Save-Module PowerShellGet -Path C:\LocalFolder
  Exit
  ```

- Upewnij się, że moduły PowerShellGet i PackageManagement nie są załadowane w żadnym innym procesie.
- Usuń zawartość `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` i `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` foldery.
- Ponownie otwórz konsolę PS z podwyższonym poziomem uprawnień, a następnie uruchom następujące polecenia.

  ```powershell
  Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
  Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
  ```
