# <a name="installing-powershell-core-on-linux"></a>Instalowanie programu PowerShell Core w systemie Linux

Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].

Dla dystrybucje systemu Linux, które nie są obsługiwane oficjalnie, można spróbować użyć [PowerShell AppImage][lai].
Można też spróbować wdrożenia plików binarnych programu PowerShell bezpośrednio przy użyciu systemu Linux [ `tar.gz` archiwum][tar], ale należy skonfigurować wymagane zależności, oparte na system operacyjny w oddzielne kroki.

Wszystkie pakiety są dostępne w naszej witrynie GitHub [zwalnia][] strony.
Po zainstalowaniu pakietu `pwsh` z terminalu.

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1710
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fedora]: #fedora
[arch]: #arch-linux
[lai]: #linux-appimage
[tar]: #binary-archives

## <a name="ubuntu-1404"></a>Ubuntu 14.04

### <a name="installation-via-package-repository---ubuntu-1404"></a>Instalacja za pośrednictwem repozytorium pakietów - Ubuntu 14.04

Podstawowe programu PowerShell dla systemu Linux jest publikowany dla repozytoriów pakietu do łatwej instalacji (i aktualizacji).
Jest to preferowana metoda.

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

Jako administratora Zarejestruj repozytorium firmy Microsoft.
Następnie należy po prostu użyć `sudo apt-get upgrade powershell` aktualizacji instalacji.

### <a name="installation-via-direct-download---ubuntu-1404"></a>Instalacja za pośrednictwem bezpośredniego pobierania - Ubuntu 14.04

Pobierz pakiet Debian `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` z [zwalnia][] strony na maszynie Ubuntu.

W terminalu następnie wykonaj następujące czynności:

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
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
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/16.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Po zarejestrowaniu repozytorium Microsoft raz jako administratora, od, wystarczy użyć `sudo apt-get upgrade powershell` go zaktualizować.

### <a name="installation-via-direct-download---ubuntu-1604"></a>Instalacja za pośrednictwem bezpośredniego pobierania - Ubuntu 16.04

Pobierz pakiet Debian `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` z [zwalnia][] strony na maszynie Ubuntu.

W terminalu następnie wykonaj następujące czynności:

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> Należy pamiętać, że `dpkg -i` zakończy się niepowodzeniem z zależności unmet; następne polecenie `apt-get install -f` rozpoznaje je, a następnie kończy Konfigurowanie pakietu programu PowerShell.

### <a name="uninstallation---ubuntu-1604"></a>Dezinstalacja - Ubuntu 16.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1710"></a>Ubuntu 17.10

> Uwaga: Po dodano obsługę Ubuntu 18.04 `6.1.0-preview.2`

### <a name="installation-via-package-repository---ubuntu-1710"></a>Instalacja za pośrednictwem repozytorium pakietów - Ubuntu 17.10

Podstawowe programu PowerShell dla systemu Linux jest publikowany dla repozytoriów pakietu do łatwej instalacji (i aktualizacji).
Jest to preferowana metoda.

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/17.10/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Po zarejestrowaniu repozytorium Microsoft raz jako administratora, od, wystarczy użyć `sudo apt-get upgrade powershell` go zaktualizować.

### <a name="installation-via-direct-download---ubuntu-1710"></a>Instalacja za pośrednictwem bezpośredniego pobierania - Ubuntu 17.10

Pobierz pakiet Debian `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` z [zwalnia][] strony na maszynie Ubuntu.

W terminalu następnie wykonaj następujące czynności:

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.10_amd64.deb
sudo apt-get install -f
```

> Należy pamiętać, że `dpkg -i` zakończy się niepowodzeniem z zależności unmet; następne polecenie `apt-get install -f` rozpoznaje je, a następnie kończy Konfigurowanie pakietu programu PowerShell.

### <a name="uninstallation---ubuntu-1710"></a>Dezinstalacja - Ubuntu 17.10

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a>Ubuntu 18.04

> Uwaga: Po dodano obsługę Ubuntu 18.04 `6.1.0-preview.2`

### <a name="installation-via-package-repository---ubuntu-1804"></a>Instalacja za pośrednictwem repozytorium pakietów - Ubuntu 18.04

Podstawowe programu PowerShell dla systemu Linux jest publikowany dla repozytoriów pakietu do łatwej instalacji (i aktualizacji).
Jest to preferowana metoda.

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Po zarejestrowaniu repozytorium Microsoft raz jako administratora, od, wystarczy użyć `sudo apt-get upgrade powershell` go zaktualizować.

### <a name="installation-via-direct-download---ubuntu-1804"></a>Instalacja za pośrednictwem bezpośredniego pobierania - Ubuntu 18.04

Pobierz pakiet Debian `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` z [zwalnia][] strony na maszynie Ubuntu.

W terminalu następnie wykonaj następujące czynności:

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> Należy pamiętać, że `dpkg -i` zakończy się niepowodzeniem z zależności unmet; następne polecenie `apt-get install -f` rozpoznaje je, a następnie kończy Konfigurowanie pakietu programu PowerShell.

### <a name="uninstallation---ubuntu-1710"></a>Dezinstalacja - Ubuntu 17.10

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

Pobierz pakiet Debian `powershell_6.0.2-1.debian.8_amd64.deb` z [zwalnia][] strony na Debian maszyny.

W terminalu następnie wykonaj następujące czynności:

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> Należy pamiętać, że `dpkg -i` zakończy się niepowodzeniem z unmet zależności.
> Następne polecenie `apt-get install -f` rozpoznaje je, a następnie kończy Konfigurowanie pakietu programu PowerShell.

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

Pobierz pakiet Debian `powershell_6.0.2-1.debian.9_amd64.deb` z [zwalnia][] strony na Debian maszyny.

W terminalu następnie wykonaj następujące czynności:

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> Należy pamiętać, że `dpkg -i` zakończy się niepowodzeniem z unmet zależności.
> Następne polecenie `apt-get install -f` rozpoznaje je, a następnie kończy Konfigurowanie pakietu programu PowerShell.

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

Przy użyciu [CentOS 7][], Pobierz pakiet RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` z [zwalnia][] strony na maszynie CentOS.

W terminalu następnie wykonaj następujące czynności:

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

Można także zainstalować RPM bez pośredniego kroku pobierania go:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
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

Pobierz pakiet RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` z [zwalnia][] strony na maszynie Red Hat Enterprise Linux.

W terminalu następnie wykonaj następujące czynności:

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

Można także zainstalować RPM bez pośredniego kroku pobierania go:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>Dezinstalacja - Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a>OpenSUSE 42.2

> [!NOTE]
> Podczas instalacji podstawowej programu PowerShell `zypper` może Zgłoś następujący błąd:
>
> ```Output
> Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
>  Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
>  Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
> ```
>
> W takim przypadku sprawdź, czy zgodna `libcurl` biblioteki występuje przez sprawdzenie, czy następujące polecenie pokazuje `libcurl4` pakietu jako zainstalowane:
>
> ```sh
> zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
> ```
>
> Następnie wybierz pozycję `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` rozwiązania podczas instalowania pakietu programu PowerShell.

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

Pobierz pakiet RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` z [zwalnia][] strony na maszynie OpenSUSE.

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

Można także zainstalować RPM bez pośredniego kroku pobierania go:

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a>Dezinstalacja - OpenSUSE 42.2

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a>Fedora

> Należy pamiętać, Fedora 28 jest obsługiwana tylko w programie PowerShell Core 6.1 i nowszych.

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a>Instalacja za pośrednictwem repozytorium pakietów (preferowane) - Fedora 27 Fedora 28

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a>Instalacja za pośrednictwem bezpośredniego pobierania - Fedora 27, Fedora 28

Pobierz pakiet RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` z [zwalnia][] strony na maszynie Fedora.

W terminalu następnie wykonaj następujące czynności:

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

Można także zainstalować RPM bez pośredniego kroku pobierania go:

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a>Dezinstalacja - Fedora 27 Fedora 28

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Arch Linux

Środowisko PowerShell jest dostępny z [Arch systemu Linux][] użytkownika repozytorium (AUR).

* Może być kompilowana przy użyciu [najnowszej oznakowane zlecenia][arch-release]
* Mogą być kompilowane z [najnowszym zatwierdzeniu do wzorca][arch-git]
* Można zainstalować, za pomocą [najnowszej wersji pliku binarnego][arch-bin]

Pakiety w AUR Wspólnotę utrzymane — nie jest oficjalną obsługiwane.

Aby uzyskać więcej informacji na temat instalowania pakietów z AUR, zobacz [wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) lub społeczności [plik DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).

[Arch systemu Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a>AppImage systemu Linux

Przy użyciu najnowszych dystrybucji systemu Linux, Pobierz AppImage `powershell-6.0.1-x86_64.AppImage` z [zwalnia][] strony na komputerze systemu Linux.

W terminalu następnie wykonaj następujące czynności:

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

[AppImage][] umożliwia uruchamianie programu PowerShell bez jej instalowania.
Jest przenośnych aplikacji, która zawiera w jednym pakiecie spójnego środowiska PowerShell i jego zależności (w tym oprogramowanie .NET Core zależności systemu).
Ten pakiet jest jedną wartość binarną, która działa niezależnie od dystrybucji systemu Linux przez użytkownika.

[appimage]: http://appimage.org/

## <a name="kali"></a>Kali

### <a name="installation"></a>Instalacja

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Install PowerShell
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a>Uruchom program PowerShell w najnowszej Kali (Kali przewijane GNU/Linux) bez instalowania go

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a>Dezinstalacja - Kali

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a>Raspbian

Obecnie programu PowerShell jest obsługiwana tylko na Raspbian Stretch.

Również środowisko CoreCLR (i w związku z tym podstawowe programu PowerShell) będą działać tylko na urządzeniach Pi 2 i Pi 3 jako inne urządzenia, tak samo, jak [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), nieobsługiwany procesor.

Pobierz [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) i postępuj zgodnie z [instrukcje dotyczące instalacji](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) uzyskać na Twoje Pi.

### <a name="installation"></a>Instalacja

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.2-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

Opcjonalnie można utworzyć łącza symbolicznego, aby można było uruchomić program PowerShell bez określenia ścieżki do "pwsh" binarne

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a>Dezinstalacja - Raspbian

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a>Archiwa binarne

Dane binarne środowiska PowerShell `tar.gz` archiwa są udostępniane dla platform Linux umożliwić wdrożenie zaawansowanych scenariuszy.

### <a name="dependencies"></a>Zależności

PowerShell kompilacje przenośne pliki binarne dla wszystkich dystrybucje systemu Linux.
Jednak różnych zależności na różne dystrybucje wymaga środowiska uruchomieniowego .NET Core i dlatego programu PowerShell jest taka sama.

W poniższej tabeli przedstawiono zależności .NET Core 2.0 oficjalnie obsługiwanych w różnych dystrybucje systemu Linux.

| System operacyjny                 | Zależności |
| ------------------ | ------------ |
| Ubuntu 14.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Ubuntu 16.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55 |
| Ubuntu 17.10       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57 |
| Ubuntu 18.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60 |
| Debian 8 (Joasia)  | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Debian 9 (Stretch) | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 <br> OpenSUSE 42.2 | libunwind, libcurl, biblioteki openssl, libicu |
| Fedora 27 <br> Fedora 28 | libunwind, libcurl, openssl-libs, libicu, compat-openssl10 |

Aby wdrożyć pliki binarne programu PowerShell na dystrybucje systemu Linux, które nie są obsługiwane oficjalnie, należy zainstalować zależności niezbędne dla docelowego systemu operacyjnego w oddzielne kroki.
Na przykład naszych [plik dockerfile Amazon Linux] [ amazon-dockerfile] najpierw instaluje zależności, a następnie wyodrębnia systemu Linux `tar.gz` archiwum.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a>Instalacja — archiwa binarne

#### <a name="linux"></a>Linux

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.2/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a>Odinstalowanie archiwa binarne

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a>Ścieżki

* `$PSHOME` jest `/opt/microsoft/powershell/6.0.2/`
* Profile użytkowników będą odczytywane z `~/.config/powershell/profile.ps1`
* Domyślne profile będą odczytywane z `$PSHOME/profile.ps1`
* Moduły użytkownika będą odczytywane z `~/.local/share/powershell/Modules`
* Udostępniony moduły będą odczytywane z `/usr/local/share/powershell/Modules`
* Domyślne moduły będą odczytywane z `$PSHOME/Modules`
* Historia PSReadline zostanie zarejestrowana w celu `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Profile przestrzegać konfiguracji na hosta w programie PowerShell, więc domyślne profile specyficzne dla hosta istnieje w `Microsoft.PowerShell_profile.ps1` w tej samej lokalizacji.

PowerShell szanuje [specyfikacji katalogu Base XDG] [ xdg-bds] w systemie Linux.

[zwalnia]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
