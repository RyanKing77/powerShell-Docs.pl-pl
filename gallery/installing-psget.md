---
ms.date: 06/12/2017
contributor: manikb
keywords: Galeria, programu powershell, polecenie cmdlet, psget
title: Instalowanie menedżera pakietów PowerShellGet
ms.openlocfilehash: 23a53a9117c9f6a7ad157b635cd7ff4b3b3444c5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075277"
---
# <a name="installing-powershellget"></a>Instalowanie menedżera pakietów PowerShellGet

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>Moduł PowerShellGet jest moduł skrzynkach odbiorczych w następujących wersjach

- [Windows 10](https://www.microsoft.com/windows) lub nowszej
- [System Windows Server 2016](/windows-server/windows-server) lub nowszej
- [Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) lub nowszej
- [PowerShell 6](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a>Uzyskiwanie modułu PowerShellGet w przypadku programu PowerShell w wersji 3.0 i 4.0

- [Funkcja PackageManagement MSI](https://www.microsoft.com/download/details.aspx?id=51451)

## <a name="get-the-latest-version-from-powershell-gallery"></a>Pobierz najnowszą wersję z galerii programu PowerShell

- Przed zaktualizowaniem modułu PowerShellGet, należy zawsze instalować najnowszego dostawcę Nuget. Aby to zrobić, uruchom następujące polecenie w sesji programu PowerShell z podwyższonym poziomem uprawnień.

  ```powershell
  Install-PackageProvider Nuget –Force
  Exit
  ```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>Dla systemów z programu PowerShell w wersji 5.0 (lub nowsza) można zainstalować najnowszy moduł PowerShellGet

- Aby to zrobić w systemie Windows 10, Windows Server 2016, każdy system WMF 5.0 lub 5.1 zainstalowane lub dowolnego systemu przy użyciu programu PowerShell 6 Uruchom następujące polecenia w sesji programu PowerShell z podwyższonym poziomem uprawnień.

  ```powershell
  Install-Module –Name PowerShellGet –Force
  Exit
  ```

- Użyj `Update-Module` można pobrać nowsze wersje.

  ```powershell
  Update-Module -Name PowerShellGet
  Exit
  ```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpswwwmicrosoftcomdownloaddetailsaspxid51451"></a>Dla komputerów z systemami program PowerShell 3 lub 4 programu PowerShell, który został zainstalowany [MSI funkcji PackageManagement](https://www.microsoft.com/download/details.aspx?id=51451)

- Użyć poniższego polecenia cmdlet PowerShellGet sesję programu PowerShell z podwyższonym poziomem uprawnień do zapisania modułów do katalogu lokalnego

  ```powershell
  Save-Module PowerShellGet -Path C:\LocalFolder
  Exit
  ```

- Upewnij się, moduły PackageManagement modułu PowerShellGet oraz spełnione nie są ładowane w żadnych innych procesów.
- Usuń zawartość `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` i `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` folderów.
- Ponownie otwórz konsolę PS z podwyższonym poziomem uprawnień, a następnie uruchom następujące polecenia.

  ```powershell
  Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
  Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
  ```
