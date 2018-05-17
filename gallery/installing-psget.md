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
---
# <a name="installing-powershellget"></a>Instalowanie menedżera pakietów PowerShellGet

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>W polu modułu w następujących wersjach jest PowerShellGet

- [Windows 10](https://www.microsoft.com/windows/get-windows-10) lub nowsza
- [Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/windows-server-2016) lub nowsza
- [Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) lub nowsza
- [6 programu PowerShell](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a>Pobieranie modułu PowerShellGet dla środowiska PowerShell w wersji 3.0 i 4.0

- [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

## <a name="get-the-latest-version-from-powershell-gallery"></a>Pobierz najnowszą wersję z galerii programu PowerShell

- Przed zaktualizowaniem PowerShellGet, zawsze należy zainstalować najnowszą wersję dostawcy Nuget. Aby to zrobić, uruchom następujące polecenie w sesji programu PowerShell z podwyższonym poziomem uprawnień.

```powershell
Install-PackageProvider Nuget –Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>Dla systemów z programu PowerShell w wersji 5.0 (lub nowsza) można zainstalować najnowsze PowerShellGet

- Aby to zrobić w systemie Windows 10, Windows Server 2016, każdy system WMF 5.0 lub 5.1 zainstalowany lub każdy system 6 programu PowerShell, uruchom następujące polecenia z sesji programu PowerShell z podwyższonym poziomem uprawnień.

```powershell
Install-Module –Name PowerShellGet –Force
Exit
```

- Użyj modułu aktualizacji, aby uzyskać nowsze wersje.

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpgomicrosoftcomfwlinklinkid746217clcid0x409"></a>Dla systemami PowerShell 3 lub 4 programu PowerShell, który został zainstalowany [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

- Użyj poniżej polecenia cmdlet PowerShellGet z sesji programu PowerShell z podwyższonym poziomem uprawnień, aby zapisać modułów do katalogu lokalnego

```powershell
Save-Module PowerShellGet -Path C:\LocalFolder
Exit
```

- Upewnij się, że PowerShellGet i PackageManagment moduły nie załadowano żadnych innych procesów.
- Usuń zawartość `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` i `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` folderów.
- Ponownie otwórz konsolę PS z podwyższonym poziomem uprawnień, a następnie uruchom następujące polecenia.

```powershell
Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
```