# <a name="installing-powershell-core-on-windows"></a>Instalowanie programu PowerShell Core w systemie Windows

## <a name="msi"></a>MSI

Do zainstalowania programu PowerShell na klientach z systemem Windows lub Windows Server (działa w systemie Windows 7 z dodatkiem SP1, Server 2008 R2 lub nowszy), Pobierz pakiet MSI z naszej usługi GitHub [zwalnia][] strony.

Plik MSI wygląda tak- `PowerShell-6.0.0.<buildversion>.<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

Po pobraniu, kliknij dwukrotnie Instalatora, a następnie postępuj zgodnie z monitami.

Brak skrót umieszczone w Menu Start, podczas instalacji.

* Domyślnie pakiet jest zainstalowany na `$env:ProgramFiles\PowerShell\`
* Można uruchomić programu PowerShell za pomocą Start Menu lub `$env:ProgramFiles\PowerShell\pwsh.exe`

### <a name="prerequisites"></a>Wymagania wstępne

Aby włączyć obsługę zdalną środowiska PowerShell przez WSMan, muszą zostać spełnione następujące wymagania wstępne:

* Zainstaluj [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) w wersjach systemu Windows przed systemem Windows 10.
  Jest ona dostępna za pośrednictwem bezpośredniego pobierania lub usługi Windows Update.
  Poprawiono pełni (w tym opcjonalnych pakietów), obsługiwane systemy mają już to zainstalowane.
* Zainstaluj zestaw Windows Management Framework (WMF) [4.0](https://www.microsoft.com/download/details.aspx?id=40855) lub nowszą ([5.1](https://www.microsoft.com/download/details.aspx?id=54616)) w systemie Windows 7 i Windows Server 2008 R2.

## <a name="zip"></a>ZIP

Binarny archiwum ZIP programu PowerShell umożliwiające zaawansowanych scenariuszach wdrożenia.
Należy zauważyć, że podczas korzystania z archiwum ZIP, nie będzie otrzymywał sprawdzania wymagań wstępnych, tak jak pakiet MSI.
Dlatego w celu komunikacji zdalnej za pośrednictwem usługi WSMan działają prawidłowo w wersjach systemu Windows przed systemem Windows 10, trzeba upewnij się, że [wymagania wstępne](#prerequisites) są spełnione.

## <a name="deploying-on-nano-server"></a>Wdrażanie na serwerze Nano

W poniższych instrukcjach przyjęto, że wersja programu PowerShell jest już uruchomiona w obrazie Nano Server i że ma zostać wygenerowane przez [Nano Server Image Builder](https://technet.microsoft.com/windows-server-docs/get-started/deploy-nano-server).
Nano Server jest "bezobsługowe" systemu operacyjnego i wdrożenia plików binarnych programu PowerShell Core może się zdarzyć na dwa sposoby:

1. W trybie offline — zainstalować dysk VHD Nano Server i rozpakuj zawartość pliku zip do wybranej lokalizacji w zainstalowanym obrazie.
1. Tryb online — transferu pliku zip w sesji programu PowerShell i Rozpakuj go w wybranej lokalizacji.

W obu przypadkach należy wersji systemu Windows 10 x64 Zip pakietu i będzie musiał uruchomić polecenia w ramach wystąpienia programu PowerShell "Administrator".

### <a name="offline-deployment-of-powershell-core"></a>W trybie offline wdrażania podstawowych programu PowerShell

1. Rozpakuj pakiet do katalogu w zainstalowanym obrazie Nano Server za pomocą narzędzia Twoje ulubione zip.
1. Odinstaluj obraz i uruchom go.
1. Połącz się z wystąpieniem skrzynki odbiorczej, programu Windows PowerShell.
1. Postępuj zgodnie z instrukcjami, aby utworzyć punktu końcowego usług zdalnych za pomocą [innej techniki wystąpienia](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

### <a name="online-deployment-of-powershell-core"></a>Wdrożenie online PowerShell Core

Następujące kroki przeprowadzi Cię przez wdrożenia programu PowerShell Core uruchomione wystąpienie Nano Server i konfiguracji punktu końcowego zdalnego.

* Połącz z wystąpieniem skrzynki odbiorczej programu Windows PowerShell

```powershell
$session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
```

* Skopiuj plik do wystąpienia Nano Server

```powershell
Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
```

* Wprowadź sesji

```powershell
Enter-PSSession $session
```

* Wyodrębnij plik Zip

```powershell
# Insert the appropriate version.
Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
```

* Oparta na usłudze WSMan komunikacji zdalnej, wykonaj instrukcje tworzenia punktu końcowego usług zdalnych za pomocą [innej techniki wystąpienia](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

## <a name="instructions-to-create-a-remoting-endpoint"></a>Instrukcje dotyczące tworzenia punktu końcowego usługi zdalne

PowerShell Core obsługuje protokół komunikacji zdalnej programu PowerShell (PSRP) za pośrednictwem protokołów SSH, jak i WSMan. Aby uzyskać więcej informacji, zobacz:

* [SSH komunikację zdalną środowiska PowerShell główną][ssh-remoting]
* [Usługi zdalne WSMan główną programu PowerShell][wsman-remoting]

## <a name="artifact-installation-instructions"></a>Instrukcje dotyczące instalacji artefaktów

Firma Microsoft publikowania archiwum środowisko CoreCLR bitów w każdej kompilacji CI z [AppVeyor][].

## <a name="coreclr-artifacts"></a>Środowisko CoreCLR artefaktów

* Pobierz pakiet zip z **artefakty** kartę określonej kompilacji.
* Plik zip Odblokuj: kliknij prawym przyciskiem myszy w Eksploratorze plików -> Właściwości -> Zastosuj "Odblokuj" -> pole wyboru
* Wyodrębnij plik zip do `bin` katalogu
* `./bin/pwsh.exe`

<!-- [download-center]: TODO -->
[zwalnia]: https://github.com/PowerShell/PowerShell/releases
[signing]: ../../tools/Sign-Package.ps1
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell