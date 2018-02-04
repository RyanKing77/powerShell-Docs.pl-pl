# <a name="installing-powershell-core-on-macos-and-linux"></a>Instalowanie programu PowerShell Core w systemach macOS i Linux

Obsługuje [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04] [ u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25 ] [ fed25], [Fedora 26][fed26], [Arch Linux][arch]i [macOS 10.12][mac].

Dla dystrybucje systemu Linux, które nie są obsługiwane oficjalnie, można spróbować użyć [PowerShell AppImage][lai]. Można też spróbować wdrożenia plików binarnych programu PowerShell bezpośrednio przy użyciu systemu Linux [ `tar.gz` archiwum][tar], ale należy skonfigurować wymagane zależności, oparte na system operacyjny w oddzielne kroki.

Wszystkie pakiety są dostępne w naszej witrynie GitHub [zwalnia][] strony. Po zainstalowaniu pakietu `pwsh` z terminalu.

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1704
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fed25]: #fedora-25
[fed26]: #fedora-26
[arch]: #arch-linux
[lai]: #linux-appimage
[mac]: #macos-1012
[tar]: #binary-archives

## <a name="ubuntu-1404"></a>Ubuntu 14.04

### <a name="installation-via-package-repository---ubuntu-1404"></a>Instalacja za pośrednictwem repozytorium pakietów - Ubuntu 14.04

Podstawowe programu PowerShell dla systemu Linux jest publikowany dla repozytoriów pakietu do łatwej instalacji (i aktualizacji). Jest to preferowana metoda.

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/14.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Po zarejestrowaniu repozytorium Microsoft raz jako administratora, od, wystarczy użyć `sudo apt-get upgrade powershell` go zaktualizować.

### <a name="installation-via-direct-download---ubuntu-1404"></a>Instalacja za pośrednictwem bezpośredniego pobierania - Ubuntu 14.04

Pobierz pakiet Debian `powershell_6.0.0-1.ubuntu.14.04_amd64.deb` z [zwalnia][] strony na maszynie Ubuntu.

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.14.04_amd64.deb
```

W terminalu następnie wykonaj następujące czynności:

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> Należy pamiętać, że `dpkg -i` zakończy się niepowodzeniem z zależności unmet; następne polecenie `apt-get install -f` rozpoznaje je, a następnie kończy Konfigurowanie pakietu programu PowerShell.

### <a name="uninstallation---ubuntu-1404"></a>Dezinstalacja - Ubuntu 14.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a>Ubuntu 16.04

### <a name="installation-via-package-repository---ubuntu-1604"></a>Instalacja za pośrednictwem repozytorium pakietów - Ubuntu 16.04

Podstawowe programu PowerShell dla systemu Linux jest publikowany dla repozytoriów pakietu do łatwej instalacji (i aktualizacji).
Jest to preferowana metoda.

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Po zarejestrowaniu repozytorium Microsoft raz jako administratora, od, wystarczy użyć `sudo apt-get upgrade powershell` go zaktualizować.

### <a name="installation-via-direct-download---ubuntu-1604"></a>Instalacja za pośrednictwem bezpośredniego pobierania - Ubuntu 16.04

Pobierz pakiet Debian `powershell_6.0.0-1.ubuntu.16.04_amd64.deb` z [zwalnia][] strony na maszynie Ubuntu:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
```

W terminalu następnie wykonaj następujące czynności:

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> Należy pamiętać, że `dpkg -i` zakończy się niepowodzeniem z zależności unmet; następne polecenie `apt-get install -f` rozpoznaje je, a następnie kończy Konfigurowanie pakietu programu PowerShell.

### <a name="uninstallation---ubuntu-1604"></a>Dezinstalacja - Ubuntu 16.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a>Ubuntu 17.04

### <a name="installation-via-package-repository---ubuntu-1704"></a>Instalacja za pośrednictwem repozytorium pakietów - Ubuntu 17.04

Podstawowe programu PowerShell dla systemu Linux jest publikowany dla repozytoriów pakietu do łatwej instalacji (i aktualizacji).
Jest to preferowana metoda.

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/17.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Po zarejestrowaniu repozytorium Microsoft raz jako administratora, od, wystarczy użyć `sudo apt-get upgrade powershell` go zaktualizować.

### <a name="installation-via-direct-download---ubuntu-1704"></a>Instalacja za pośrednictwem bezpośredniego pobierania - Ubuntu 17.04

Pobierz pakiet Debian `powershell_6.0.0-1.ubuntu.17.04_amd64.deb` z [zwalnia][] strony na maszynie Ubuntu:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.17.04_amd64.deb
```

W terminalu następnie wykonaj następujące czynności:

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> Należy pamiętać, że `dpkg -i` zakończy się niepowodzeniem z zależności unmet; następne polecenie `apt-get install -f` rozpoznaje je, a następnie kończy Konfigurowanie pakietu programu PowerShell.

### <a name="uninstallation---ubuntu-1704"></a>Dezinstalacja - Ubuntu 17.04

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a>Debian 8

### <a name="installation-via-package-repository---debian-8"></a>Instalacja za pośrednictwem repozytorium pakietów - Debian 8

Podstawowe programu PowerShell dla systemu Linux jest publikowany dla repozytoriów pakietu do łatwej instalacji (i aktualizacji).
Jest to preferowana metoda.

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Po zarejestrowaniu repozytorium Microsoft raz jako administratora, od, wystarczy użyć `sudo apt-get upgrade powershell` go zaktualizować.

### <a name="installation-via-direct-download---debian-8"></a>Instalacja za pośrednictwem bezpośredniego pobierania - Debian 8

Pobierz pakiet Debian `powershell_6.0.0-1.debian.8_amd64.deb` z [zwalnia][] strony na maszynie Debian:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.8_amd64.deb
```

W terminalu następnie wykonaj następujące czynności:

```sh
sudo dpkg -i powershell_6.0.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> Należy pamiętać, że `dpkg -i` zakończy się niepowodzeniem z zależności unmet; następne polecenie `apt-get install -f` rozpoznaje je, a następnie kończy Konfigurowanie pakietu programu PowerShell.

### <a name="uninstallation---debian-8"></a>Dezinstalacja - Debian 8

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a>Debian 9

### <a name="installation-via-package-repository---debian-9"></a>Instalacja za pośrednictwem repozytorium pakietów - Debian 9

Podstawowe programu PowerShell dla systemu Linux jest publikowany dla repozytoriów pakietu do łatwej instalacji (i aktualizacji).
Jest to preferowana metoda.

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl gnupg apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Po zarejestrowaniu repozytorium Microsoft raz jako administratora, od, wystarczy użyć `sudo apt-get upgrade powershell` go zaktualizować.

### <a name="installation-via-direct-download---debian-9"></a>Instalacja za pośrednictwem bezpośredniego pobierania - Debian 9

Pobierz pakiet Debian `powershell_6.0.0-1.debian.9_amd64.deb` z [zwalnia][] strony na maszynie Debian:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

W terminalu następnie wykonaj następujące czynności:

```sh
sudo dpkg -i powershell_6.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

> Należy pamiętać, że `dpkg -i` zakończy się niepowodzeniem z zależności unmet; następne polecenie `apt-get install -f` rozpoznaje je, a następnie kończy Konfigurowanie pakietu programu PowerShell.

### <a name="uninstallation---debian-9"></a>Dezinstalacja - Debian 9

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a>CentOS 7

> Ten pakiet jest również działa na Oracle Linux 7.

### <a name="installation-via-package-repository-preferred---centos-7"></a>Instalacja za pośrednictwem repozytorium pakietów (preferowane) - CentOS 7

Podstawowe programu PowerShell dla systemu Linux jest publikowany oficjalnego repozytoria Microsoft easy instalacji (i aktualizacji).

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Po zarejestrowaniu repozytorium Microsoft raz jako administratora, wystarczy użyć `sudo yum update powershell` aktualizacji programu PowerShell.

### <a name="installation-via-direct-download---centos-7"></a>Instalacja za pośrednictwem bezpośredniego pobierania - CentOS 7

Przy użyciu [CentOS 7][], Pobierz pakiet RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` z [zwalnia][] strony na maszynie CentOS:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

W terminalu następnie wykonaj następujące czynności:

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Można także zainstalować RPM bez pośredniego kroku pobierania go:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a>Dezinstalacja - CentOS 7

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a>Instalacja za pośrednictwem repozytorium pakietów (preferowane) - Red Hat Enterprise Linux (RHEL) 7

Podstawowe programu PowerShell dla systemu Linux jest publikowany oficjalnego repozytoria Microsoft easy instalacji (i aktualizacji).

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Po zarejestrowaniu repozytorium Microsoft raz jako administratora, wystarczy użyć `sudo yum update powershell` aktualizacji programu PowerShell.

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a>Instalacja za pośrednictwem bezpośredniego pobierania - Red Hat Enterprise Linux (RHEL) 7

Pobierz pakiet RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` z [zwalnia][] strony na maszynie Red Hat Enterprise Linux:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

W terminalu następnie wykonaj następujące czynności:

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Można także zainstalować RPM bez pośredniego kroku pobierania go:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>Dezinstalacja - Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a>OpenSUSE 42.2

> **Uwaga:** podczas instalowania programu PowerShell Core, OpenSUSE może zgłosić, nic nie zapewnia `libcurl`.
`libcurl`powinno być już zainstalowane w obsługiwanych wersjach OpenSUSE.
Uruchom `zypper search libcurl` o potwierdzenie.
Błąd przedstawi 2 rozwiązania. Wybierz pozycję "Rozwiązania 2", aby kontynuować instalację programu PowerShell Core.

### <a name="installation-via-package-repository-preferred---opensuse-422"></a>Instalacja za pośrednictwem repozytorium pakietów (preferowane) - OpenSUSE 42.2

Podstawowe programu PowerShell dla systemu Linux jest publikowany oficjalnego repozytoria Microsoft easy instalacji (i aktualizacji).

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Product feed
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/zypp/repos.d/microsoft.repo

# Update the list of products
sudo zypper update

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-422"></a>Instalacja za pośrednictwem bezpośredniego pobierania - OpenSUSE 42.2

Pobierz pakiet RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` z [zwalnia][] strony na maszynie OpenSUSE:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Można także zainstalować RPM bez pośredniego kroku pobierania go:

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a>Dezinstalacja - OpenSUSE 42.2

```sh
sudo zypper remove powershell
```

## <a name="fedora-25"></a>Fedora 25

### <a name="installation-via-package-repository-preferred---fedora-25"></a>Instalacja za pośrednictwem repozytorium pakietów (preferowane) - Fedora 25

Podstawowe programu PowerShell dla systemu Linux jest publikowany oficjalnego repozytoria Microsoft easy instalacji (i aktualizacji).

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-25"></a>Instalacja za pośrednictwem bezpośredniego pobierania - Fedora 25

Pobierz pakiet RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` z [zwalnia][] strony na maszynie Fedora:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

W terminalu następnie wykonaj następujące czynności:

```sh
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Można także zainstalować RPM bez pośredniego kroku pobierania go:

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a>Dezinstalacja - Fedora 25

```sh
sudo dnf remove powershell
```

## <a name="fedora-26"></a>Fedora 26

### <a name="installation-via-package-repository-preferred---fedora-26"></a>Instalacja za pośrednictwem repozytorium pakietów (preferowane) - Fedora 26

Podstawowe programu PowerShell dla systemu Linux jest publikowany oficjalnego repozytoria Microsoft easy instalacji (i aktualizacji).

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install a system component
sudo dnf install compat-openssl10

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-26"></a>Instalacja za pośrednictwem bezpośredniego pobierania - 26 Fedora

Pobierz pakiet RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` z [zwalnia][] strony na maszynie Fedora:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

W terminalu następnie wykonaj następujące czynności:

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Można także zainstalować RPM bez pośredniego kroku pobierania go:

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a>Dezinstalacja - 26 Fedora

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Arch Linux

Środowisko PowerShell jest dostępny z [Arch Linux][] użytkownika repozytorium (AUR).

* Może być kompilowana przy użyciu [najnowszej oznakowane zlecenia][arch-release]
* Mogą być kompilowane z [najnowszym zatwierdzeniu do wzorca][arch-git]
* Można zainstalować, za pomocą [najnowszej wersji pliku binarnego][arch-bin]

Pakiety w AUR Wspólnotę utrzymane — nie jest oficjalną obsługiwane.

Aby uzyskać więcej informacji na temat instalowania pakietów z AUR, zobacz [wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) lub społeczności [plik DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a>AppImage systemu Linux

Przy użyciu najnowszych dystrybucji systemu Linux, Pobierz AppImage `powershell-6.0.0-x86_64.AppImage` z [zwalnia][] strony na komputerze systemu Linux.

W terminalu następnie wykonaj następujące czynności:

```bash
chmod a+x powershell-6.0.0-x86_64.AppImage
./powershell-6.0.0-x86_64.AppImage
```

[AppImage][] umożliwia uruchamianie programu PowerShell bez jej instalowania. Jest przenośnych aplikacji, która zawiera w jednym pakiecie spójnego środowiska PowerShell i jego zależności (w tym oprogramowanie .NET Core zależności systemu). Ten pakiet działa niezależnie od dystrybucji systemu Linux użytkownika, a jest jedną wartość binarną.

[appimage]: http://appimage.org/

## <a name="macos-1012"></a>macOS 10.12

### <a name="installation-via-homebrew-preferred---macos-1012"></a>Instalacja za pomocą oprogramowania Homebrew (preferowane) - macOS 10.12

[Homebrew] [ brew] jest brak Menedżer pakietów dla macOS. Jeśli `brew` nie znaleziono polecenia, należy zainstalować następujące Homebrew [zgodnie z instrukcjami][brew].

Po zainstalowaniu oprogramowania Homebrew Instalowanie programu PowerShell jest bardzo proste. Najpierw zainstaluj [pojemnika transportowego Homebrew][cask], więc można zainstalować więcej pakietów:

```sh
brew tap caskroom/cask
```

Teraz można zainstalować programu PowerShell:

```sh
brew cask install powershell
```

Po udostępnieniu nowej wersji programu PowerShell, po prostu zaktualizuj wzory dla oprogramowania Homebrew i uaktualnienia programu PowerShell:

```sh
brew update
brew cask reinstall powershell
```

> Uwaga: z powodu [ten problem w pojemnika transportowego](https://github.com/caskroom/homebrew-cask/issues/29301), musisz obecnie wykonać reinstall do uaktualnienia.

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download---macos-1012"></a>Instalacja za pośrednictwem bezpośredniego pobieranie - macOS 10.12

Przy użyciu macOS 10.12, Pobierz pakiet PKG `powershell-6.0.0-osx.10.12-x64.pkg` z [zwalnia][] strony na maszynie macOS.

Kliknij dwukrotnie plik i postępuj zgodnie z monitami albo zainstalować go z terminala:

```sh
sudo installer -pkg powershell-6.0.0-osx.10.12-x64.pkg -target /
```

### <a name="uninstallation---macos-1012"></a>Dezinstalacja - macOS 10.12

Po zainstalowaniu programu PowerShell z oprogramowania Homebrew dezinstalacji jest łatwe:

```sh
brew cask uninstall powershell
```

Po zainstalowaniu programu PowerShell za pomocą bezpośredniego pobierania programu PowerShell musi zostać usunięte ręcznie:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Aby odinstalować dodatkowe ścieżki programu PowerShell (np. Ścieżka profilu użytkownika) można znaleźć pod adresem [ścieżki] [ paths] sekcji poniżej w tym dokumencie i usunąć żądaną ścieżki na `sudo rm`. (Uwaga: nie jest to konieczne, jeśli podczas instalacji oprogramowania Homebrew.)

[paths]:#paths

## <a name="kali"></a>Kali

### <a name="installation"></a>Instalacja

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Download & Install PowerShell
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a>Uruchom program PowerShell w najnowszej Kali (Kali przewijane GNU/Linux) bez instalowania go

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.0-x86_64.AppImage

# Start PowerShell
./powershell-6.0.0-x86_64.AppImage
```

### <a name="uninstallation---kali"></a>Dezinstalacja - Kali

```sh
sudo dpkg -r powershell-6.0.0-x86_64.AppImage
```

## <a name="raspbian"></a>Raspbian

Obecnie programu PowerShell jest obsługiwana tylko na Raspbian Stretch.

### <a name="installation"></a>Instalacja

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

### <a name="uninstallation---raspbian"></a>Dezinstalacja - Raspbian

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a>Archiwa binarne

Dane binarne środowiska PowerShell `tar.gz` archiwa są udostępniane dla macOS i platformy Linux, aby włączyć zaawansowanych scenariuszach wdrożenia.

### <a name="dependencies"></a>Zależności

Dla systemu Linux programu PowerShell kompilacje przenośne pliki binarne dla wszystkich dystrybucje systemu Linux.
Jednak różnych zależności na różne dystrybucje wymaga środowiska uruchomieniowego .NET Core i dlatego programu PowerShell jest taka sama.

W poniższej tabeli przedstawiono zależności .NET Core 2.0 na różnych dystrybucje systemu Linux, które oficjalnie są obsługiwane.

| System operacyjny                 | Zależności |
| ------------------ | ------------ |
| Ubuntu 14.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Ubuntu 16.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55 |
| Ubuntu 17.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57 |
| Debian 8 (Joasia)  | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Debian 9 (Stretch) | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 <br> OpenSUSE 42.2 <br> Fedora 25 | libunwind, libcurl, openssl-libs, libicu |
| Fedora 26          | libunwind, libcurl, openssl-libs, libicu, compat-openssl10 |

W celu wdrożenia plików binarnych programu PowerShell na dystrybucje systemu Linux, które nie są obsługiwane oficjalnie, musisz zainstalować zależności niezbędne dla docelowego systemu operacyjnego w oddzielne kroki. Na przykład naszych [plik dockerfile Amazon Linux] [ amazon-dockerfile] najpierw instaluje zależności, a następnie wyodrębnia systemu Linux `tar.gz` archiwum.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a>Instalacja — archiwa binarne

#### <a name="linux"></a>Linux

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.0/pwsh /usr/bin/pwsh
```

#### <a name="macos"></a>macOS

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.0/pwsh /usr/local/bin/pwsh
```

### <a name="uninstallation---binary-archives"></a>Dezinstalacja - archiwa binarne

#### <a name="linux"></a>Linux

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

#### <a name="macos"></a>macOS

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

## <a name="paths"></a>Ścieżki

* `$PSHOME`jest`/opt/microsoft/powershell/6.0.0/`
* Profile użytkowników będą odczytywane z`~/.config/powershell/profile.ps1`
* Domyślne profile będą odczytywane z`$PSHOME/profile.ps1`
* Moduły użytkownika będą odczytywane z`~/.local/share/powershell/Modules`
* Udostępniony moduły będą odczytywane z`/usr/local/share/powershell/Modules`
* Domyślne moduły będą odczytywane z`$PSHOME/Modules`
* Historia PSReadline zostanie zarejestrowana w celu`~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Profile przestrzegać konfiguracji na hosta w programie PowerShell, więc domyślne profile specyficzne dla hosta istnieje w `Microsoft.PowerShell_profile.ps1` w tej samej lokalizacji.

W systemie Linux i macOS [specyfikacji katalogu Base XDG] [ xdg-bds] jest przestrzegana.

Należy pamiętać, że ponieważ macOS jest typem pochodnym BSD, zamiast `/opt`, prefiks używany jest `/usr/local`. W związku z tym `$PSHOME` jest `/usr/local/microsoft/powershell/6.0.0/`, i Utwórz Link symboliczny znajduje się w `/usr/local/bin/pwsh`.

[zwalnia]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
