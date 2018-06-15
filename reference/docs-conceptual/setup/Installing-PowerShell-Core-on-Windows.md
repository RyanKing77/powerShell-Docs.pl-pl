# <a name="installing-powershell-core-on-windows"></a>Instalowanie programu PowerShell Core w systemie Windows

## <a name="msi"></a>MSI

Do zainstalowania programu PowerShell na klientach z systemem Windows lub Windows Server (działa w systemie Windows 7 z dodatkiem SP1, Server 2008 R2 lub nowszy), Pobierz pakiet MSI z naszą stronę [] GitHub [wersjach].

Plik MSI wygląda tak- `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

Po pobraniu, kliknij dwukrotnie Instalatora, a następnie postępuj zgodnie z monitami.

Brak skrót umieszczone w Menu Start, podczas instalacji.

- Domyślnie pakiet jest zainstalowany na `$env:ProgramFiles\PowerShell\<version>`
- Można uruchomić programu PowerShell za pomocą Start Menu lub `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`

### <a name="prerequisites"></a>Wymagania wstępne

Aby włączyć obsługę zdalną środowiska PowerShell przez WSMan, muszą zostać spełnione następujące wymagania wstępne:

- Zainstaluj [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) w wersjach systemu Windows przed systemem Windows 10.
  Jest ona dostępna za pośrednictwem bezpośredniego pobierania lub usługi Windows Update.
  Poprawiono pełni (w tym opcjonalnych pakietów), obsługiwane systemy mają już to zainstalowane.
- W systemie Windows 7 i Windows Server 2008 R2, należy zainstalować Windows Management Framework (WMF) 4.0 lub nowszej.

## <a name="zip"></a>ZIP

Binarny archiwum ZIP programu PowerShell umożliwiające zaawansowanych scenariuszach wdrożenia.
Należy zauważyć, że podczas korzystania z archiwum ZIP, nie będzie otrzymywał sprawdzania wymagań wstępnych, tak jak pakiet MSI.
Dlatego w celu komunikacji zdalnej za pośrednictwem usługi WSMan działają prawidłowo w wersjach systemu Windows przed systemem Windows 10, trzeba upewnij się, że [wymagania wstępne](#prerequisites) są spełnione.

## <a name="deploying-on-windows-iot"></a>Wdrażanie na IoT z systemem Windows

IoT z systemem Windows jest dostarczany już z programu Windows PowerShell, który zostanie wykorzystany do wdrożenia programu PowerShell Core 6.

1. Utwórz `PSSession` do urządzenia docelowego

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. Skopiuj pakiet ZIP na urządzeniu

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-6.0.2-win-arm32.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. Nawiąż połączenie z urządzeniem, a następnie rozwiń węzeł archiwum

   ```powershell
   Enter-PSSession $s
   cd u:\users\administrator\downloads
   Expand-Archive .\PowerShell-6.0.2-win-arm32.zip
   ```

4. Konfiguracja usług zdalnych do programu PowerShell Core 6

   ```powershell
   cd .\PowerShell-6.0.2-win-arm32
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. Połącz do punktu końcowego programu PowerShell Core 6 na urządzeniu

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.6.0.2
   ```

## <a name="deploying-on-nano-server"></a>Wdrażanie na serwerze Nano

W poniższych instrukcjach przyjęto, że wersja programu PowerShell jest już uruchomiona w obrazie Nano Server i że ma zostać wygenerowane przez [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).
Nano Server jest "bezobsługowe" systemu operacyjnego. Podstawowe pliki binarne można wdrożyć, przy użyciu dwóch różnych metod.

1. W trybie offline — zainstalować dysk VHD Nano Server i rozpakuj zawartość pliku zip do wybranej lokalizacji w zainstalowanym obrazie.
2. Tryb online — transferu pliku zip w sesji programu PowerShell i Rozpakuj go w wybranej lokalizacji.

W obu przypadkach należy wersji systemu Windows 10 x64 ZIP pakietu i będzie musiał uruchomić polecenia w ramach wystąpienia programu PowerShell "Administrator".

### <a name="offline-deployment-of-powershell-core"></a>W trybie offline wdrażania podstawowych programu PowerShell

1. Rozpakuj pakiet do katalogu w zainstalowanym obrazie Nano Server za pomocą narzędzia Twoje ulubione zip.
2. Odinstaluj obraz i uruchom go.
3. Połącz się z wystąpieniem skrzynki odbiorczej, programu Windows PowerShell.
4. Postępuj zgodnie z instrukcjami, aby utworzyć punktu końcowego usług zdalnych za pomocą ["innej techniki wystąpienia"](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

### <a name="online-deployment-of-powershell-core"></a>Wdrożenie online PowerShell Core

Poniższe kroki przedstawiono środowiska PowerShell Core uruchomione wystąpienie Nano Server i konfiguracji punktu końcowego zdalnego.

- Połącz z wystąpieniem skrzynki odbiorczej programu Windows PowerShell

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- Skopiuj plik do wystąpienia Nano Server

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- Wprowadź sesji

  ```powershell
  Enter-PSSession $session
  ```

- Wyodrębnij plik ZIP

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- Oparta na usłudze WSMan komunikacji zdalnej, wykonaj instrukcje tworzenia punktu końcowego usług zdalnych za pomocą ["innej techniki wystąpienia"](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

## <a name="instructions-to-create-a-remoting-endpoint"></a>Instrukcje dotyczące tworzenia punktu końcowego usługi zdalne

PowerShell Core obsługuje protokół komunikacji zdalnej programu PowerShell (PSRP) za pośrednictwem protokołów SSH, jak i WSMan.
Aby uzyskać więcej informacji, zobacz:

- [SSH komunikację zdalną środowiska PowerShell główną] [ssh-Komunikacja zdalna]
- [WSMan komunikację zdalną środowiska PowerShell główną] [Komunikacja zdalna wsman]

## <a name="artifact-installation-instructions"></a>Instrukcje dotyczące instalacji artefaktów

Firma Microsoft publikuje archiwum środowisko CoreCLR bitów w każdej kompilacji CI o [] [AppVeyor].

Aby zainstalować podstawowe programu PowerShell z artefaktu środowisko CoreCLR:

1. Pobierz pakiet ZIP z **artefakty** kartę określonej kompilacji.
2. Plik ZIP Odblokuj: kliknij prawym przyciskiem myszy w Eksploratorze plików -> Właściwości -> Zastosuj "Odblokuj" -> pole wyboru
3. Wyodrębnij plik zip do `bin` katalogu
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO --> [zwalnia]: https://github.com/PowerShell/PowerShell/releases [ssh-Komunikacja zdalna]:... /Core-PowerShell/SSH-Remoting-in-PowerShell-Core.MD [wsman Komunikacja zdalna]:... /Core-PowerShell/wsman-Remoting-in-PowerShell-Core.MD [AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell