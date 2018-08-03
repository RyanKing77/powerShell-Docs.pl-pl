# <a name="installing-powershell-core-on-windows"></a>Instalowanie programu PowerShell Core w systemie Windows

## <a name="msi"></a>TOŻSAMOŚCI USŁUGI ZARZĄDZANEJ

Aby zainstalować program PowerShell w klienta Windows lub Windows Server (działa w systemie Windows 7 z dodatkiem SP1, Server 2008 R2 i nowszych), Pobierz pakiet MSI w usłudze GitHub [zwalnia][] strony.

Plik MSI wyglądają następująco — `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

Po pobraniu, kliknij dwukrotnie Instalatora, a następnie postępuj zgodnie z monitami.

Brak skrótu umieszczone w trakcie instalacji, w Menu Start.

- Domyślnie pakiet jest zainstalowany na `$env:ProgramFiles\PowerShell\<version>`
- Można uruchomić programu PowerShell przy użyciu Start Menu lub `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`

### <a name="prerequisites"></a>Wymagania wstępne

Aby włączyć komunikację zdalną programu PowerShell za pośrednictwem usługi WS-Management, muszą zostać spełnione następujące wymagania wstępne:

- Zainstaluj [uniwersalnego środowiska uruchomieniowego c.](https://www.microsoft.com/download/details.aspx?id=50410) na Windows wersjach wcześniejszych niż Windows 10.
  Jest ona dostępna za pośrednictwem bezpośredniego pobierania lub Windows Update.
  W pełni zastosować poprawki względem jakiegokolwiek (w tym opcjonalnych pakietów), obsługiwane systemy mają już to zainstalowane.
- Windows Management Framework (WMF) 4.0 lub nowszym należy zainstalować na Windows 7 i Windows Server 2008 R2.

## <a name="zip"></a>ZIP

Binarny archiwa ZIP programu PowerShell są podane w celu włączenia zaawansowanych scenariuszach wdrożenia.
Należy zauważyć, że korzystając z archiwum ZIP, nie będą otrzymywać sprawdzania wymagań wstępnych, tak jak pakietu MSI.
Aby dla niego komunikacji zdalnej za pośrednictwem usługi WS-Management działało poprawnie, w wersjach Windows przed systemem Windows 10, należy się upewnić, [wymagania wstępne](#prerequisites) są spełnione.

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
   Copy-Item .\PowerShell-6.0.2-win-arm32.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. Łączenie z urządzeniem, a następnie rozwiń archiwum

   ```powershell
   Enter-PSSession $s
   cd u:\users\administrator\downloads
   Expand-Archive .\PowerShell-6.0.2-win-arm32.zip
   ```

4. Konfigurowanie komunikacji zdalnej programu PowerShell Core 6

   ```powershell
   cd .\PowerShell-6.0.2-win-arm32
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. Łączenie do endpoint programu PowerShell Core 6 na urządzeniu

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.6.0.2
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
4. Postępuj zgodnie z instrukcjami, aby utworzyć punkt końcowy komunikacji zdalnej za pomocą ["inna technika wystąpienia"](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

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

- Chcąc oparta na usłudze WSMan komunikacji zdalnej, postępuj zgodnie z instrukcjami, aby utworzyć punkt końcowy komunikacji zdalnej przy użyciu ["inna technika wystąpienia"](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

## <a name="instructions-to-create-a-remoting-endpoint"></a>Instrukcje, aby utworzyć punkt końcowy komunikacji zdalnej

Program PowerShell Core obsługuje protokół komunikacji zdalnej programu PowerShell (PSRP) za pośrednictwem protokołu SSH i WSMan.
Aby uzyskać więcej informacji, zobacz:

- [SSH komunikacji zdalnej w programie PowerShell Core][ssh-remoting]
- [Komunikacja zdalna usługi WS-Management, w programie PowerShell Core][wsman-remoting]

## <a name="artifact-installation-instructions"></a>Instrukcje dotyczące instalacji artefaktu

Publikujemy archiwum z bitami CoreCLR przy każdej kompilacji ciągłej integracji przy użyciu [AppVeyor][].

Aby zainstalować program PowerShell Core z artefaktów CoreCLR:

1. Pobierz pakiet pliku ZIP z **artefaktów** kartę konkretnej kompilacji.
2. Odblokuj plik ZIP: kliknij prawym przyciskiem myszy w Eksploratorze plików -> Właściwości -> wyboru Zastosuj "Odblokuj" box ->
3. Wyodrębnij plik zip do `bin` katalogu
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO -->

[zwalnia]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
