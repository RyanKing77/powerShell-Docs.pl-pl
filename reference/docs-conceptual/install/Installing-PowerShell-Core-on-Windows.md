---
title: Instalowanie programu PowerShell Core w systemie Windows
description: Informacje o instalowaniu programu PowerShell Core w Windows
ms.date: 08/06/2018
ms.openlocfilehash: 910ee5a653fc1703bfddaf6367225f3b654d600f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058033"
---
# <a name="installing-powershell-core-on-windows"></a>Instalowanie programu PowerShell Core w systemie Windows

Istnieje wiele sposobów, aby zainstalować program PowerShell Core w Windows.

## <a name="prerequisites"></a>Wymagania wstępne

Aby włączyć komunikację zdalną programu PowerShell za pośrednictwem usługi WS-Management, muszą zostać spełnione następujące wymagania wstępne:

- Zainstaluj [uniwersalnego środowiska uruchomieniowego c.](https://www.microsoft.com/download/details.aspx?id=50410) na Windows wersjach wcześniejszych niż Windows 10. Jest ona dostępna za pośrednictwem bezpośredniego pobierania lub Windows Update. W pełni zastosować poprawki względem jakiegokolwiek (w tym opcjonalnych pakietów), obsługiwane systemy mają już to zainstalowane.
- Windows Management Framework (WMF) 4.0 lub nowszym należy zainstalować na Windows 7 i Windows Server 2008 R2.

## <a name="a-idmsi-installing-the-msi-package"></a><a id="msi" />Instalowanie pakietu MSI

Aby zainstalować program PowerShell w klienta Windows lub Windows Server (działa w systemie Windows 7 z dodatkiem SP1, Server 2008 R2 i nowszych), Pobierz pakiet MSI z naszej stronie [] GitHub [wersjach]. Przewiń w dół do **zasoby** części wersji, którą chcesz zainstalować. Sekcja zasoby mogą być zwinięte, konieczne może być kliknij, aby ją rozwinąć.

Plik MSI wyglądają następująco — `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

Po pobraniu, kliknij dwukrotnie Instalatora, a następnie postępuj zgodnie z monitami.

Instalator tworzy skrót, w Windows Start Menu.

- Domyślnie pakiet jest zainstalowany na `$env:ProgramFiles\PowerShell\<version>`
- Można uruchomić programu PowerShell przy użyciu Start Menu lub `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`

### <a name="administrative-install-from-the-command-line"></a>Administracyjne instalacji z wiersza polecenia

Pakiety MSI można zainstalować z poziomu wiersza polecenia. Dzięki temu administratorzy mogą wdrażać pakiety bez interakcji z użytkownikiem. Pakiet MSI środowiska PowerShell obejmuje następujące właściwości, aby określić opcje instalacji:

- **ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** — ta właściwość określa opcję dodawania **Otwórz program PowerShell** element do menu kontekstowego w Eksploratorze Windows.
- **ENABLE_PSREMOTING** — ta właściwość określa opcja włączania komunikacji zdalnej programu PowerShell podczas instalacji.
- **REGISTER_MANIFEST** — ta właściwość określa opcję rejestrowania manifestu rejestrowania zdarzeń Windows.

Poniższy przykład pokazuje, jak do przeprowadzenia instalacji dyskretnej programu PowerShell Core ze wszystkimi opcjami instalacji włączone.

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

Aby uzyskać pełną listę opcji wiersza polecenia msiexec.exe zobacz [opcje wiersza polecenia](/windows/desktop/Msi/command-line-options).

## <a name="a-idzip-installing-the-zip-package"></a><a id="zip" />Instalowanie pakietu ZIP

Binarny archiwa ZIP programu PowerShell są podane w celu włączenia zaawansowanych scenariuszach wdrożenia. Należy zauważyć, że korzystając z archiwum ZIP, nie będą otrzymywać sprawdzania wymagań wstępnych, tak jak pakietu MSI. Dla niego komunikacji zdalnej za pośrednictwem usługi WS-Management, aby zapewnić prawidłowe działanie, upewnij się, że zostały spełnione [wymagania wstępne](#prerequisites).

## <a name="deploying-on-windows-iot"></a>Wdrażanie na Windows IoT

Zawiera już Windows IoT za pomocą programu Windows PowerShell, które firma Microsoft będzie używany do wdrażania programu PowerShell Core 6.

1. Utwórz `PSSession` urządzenie docelowe

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. Skopiuj pakiet ZIP do urządzenia

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. Łączenie z urządzeniem, a następnie rozwiń archiwum

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. Konfigurowanie komunikacji zdalnej programu PowerShell Core 6

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. Łączenie do endpoint programu PowerShell Core 6 na urządzeniu

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a>Wdrażanie na serwerze Nano Server

W poniższych instrukcjach przyjęto, że wersja programu PowerShell jest już uruchomiona na obrazie Nano Server i czy ma zostać wygenerowane przez [Kreator obrazów serwera Nano](/windows-server/get-started/deploy-nano-server).
Serwer nano Server jest "bezobsługowe" systemu operacyjnego. Podstawowe pliki binarne można wdrożyć przy użyciu dwóch różnych metod.

1. W trybie offline — zainstalować dysk VHD serwera Nano i rozpakuj zawartość pliku zip do wybranej lokalizacji w zainstalowanym obrazie.
2. Tryb online — przenoszenie pliku zip przez sesję programu PowerShell i Rozpakuj go w wybranej lokalizacji.

W obu przypadkach należy wersji systemu Windows 10 x64 ZIP pakietu i będzie konieczne uruchomienie poleceń w ramach wystąpienia programu PowerShell "Administrator".

### <a name="offline-deployment-of-powershell-core"></a>Wdrożenie programu PowerShell Core w trybie offline

1. Aby rozpakować pakiet do katalogu w zainstalowanym obrazie systemu Nano Server przy użyciu usługi narzędzia zip ulubionych.
2. Odinstaluj obraz i jego rozruch.
3. Połącz z wystąpieniem skrzynki odbiorczej programu Windows PowerShell.
4. Postępuj zgodnie z instrukcjami, aby utworzyć punkt końcowy komunikacji zdalnej za pomocą ["inna technika wystąpienia"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

### <a name="online-deployment-of-powershell-core"></a>Online wdrożenia programu PowerShell Core

Poniższe kroki prowadzą przez wdrożenia programu PowerShell Core do uruchomionego wystąpienia systemu Nano Server i konfiguracji jego zdalnego punktu końcowego.

- Połącz się z wystąpieniem skrzynki odbiorczej programu Windows PowerShell

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- Skopiuj plik do wystąpienia systemu Nano Server

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- Wprowadź sesję

  ```powershell
  Enter-PSSession $session
  ```

- Wyodrębnij plik ZIP

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- Chcąc oparta na usłudze WSMan komunikacji zdalnej, postępuj zgodnie z instrukcjami, aby utworzyć punkt końcowy komunikacji zdalnej przy użyciu ["inna technika wystąpienia"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

## <a name="how-to-create-a-remoting-endpoint"></a>Jak utworzyć punkt końcowy komunikacji zdalnej

Program PowerShell Core obsługuje protokół komunikacji zdalnej programu PowerShell (PSRP) za pośrednictwem protokołu SSH i WSMan. Aby uzyskać więcej informacji, zobacz:

- [SSH komunikacji zdalnej w programie PowerShell Core] [ssh-Komunikacja zdalna]
- [Komunikacja zdalna usługi WS-Management w programie PowerShell Core] [Komunikacja zdalna usługi WS-Management]

<!-- [download-center]: TODO -->
[zwalnia]: https://github.com/PowerShell/PowerShell/releases [ssh-Komunikacja zdalna]:... [Komunikacja zdalna usługi WS-Management] /Core-PowerShell/SSH-Remoting-in-PowerShell-Core.md:... /Core-PowerShell/wsman-Remoting-in-PowerShell-Core.MD [AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
