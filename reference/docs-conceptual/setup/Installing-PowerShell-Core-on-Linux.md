---
title: Instalowanie programu PowerShell Core w systemie Linux
description: Informacje o instalowaniu programu PowerShell Core w różnych dystrybucjach systemu Linux
ms.date: 08/06/2018
ms.openlocfilehash: d60e1d5a89b6907b67c19b8cfcde969be156bd60
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851293"
---
# <a name="installing-powershell-core-on-linux"></a>Instalowanie programu PowerShell Core w systemie Linux

Obsługuje [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10] [ u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27 ] [ fedora], [Fedora 28][fedora], i [Arch Linux][arch].

Dystrybucje systemu Linux, które nie są oficjalnie obsługiwane, spróbuj użyć [pakiet przyciąganie PowerShell][snap].
Możesz też spróbować wdrażania plików binarnych programu PowerShell bezpośrednio przy użyciu systemu Linux [ `tar.gz` archiwum][tar], ale należy skonfigurować niezbędne zależności, w oparciu o system operacyjny w oddzielne kroki.

Wszystkie pakiety są dostępne w usłudze GitHub [zwalnia][] strony.
Po zainstalowaniu pakietu Uruchom `pwsh` z poziomu terminalu.

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u18]: #ubuntu-1810
[u18]: #ubuntu-1804
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-423
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a>Instalowanie wersji zapoznawczych

Podczas instalowania wersji programu PowerShell Core w wersji zapoznawczej dla systemu Linux przy użyciu repozytorium pakietów, nazwy pakietu zmieni się z `powershell` do `powershell-preview`.

Instalowanie przy użyciu bezpośredniego pobierania nie ulega zmianie, inna niż nazwa pliku.

W tym miejscu znajduje się tabela polecenia, aby zainstalować pakiety w wersji zapoznawczej i stabilny, przy użyciu różnych menedżerów pakietów:

|Distribution(s)|Polecenie stabilne | Polecenia w wersji zapoznawczej |
|---------------|---------------|-----------------|
| Ubuntu, Debian |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| CentOS, RedHat |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| OpenSUSE |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| Fedora   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a>Ubuntu 14.04

### <a name="installation-via-package-repository---ubuntu-1404"></a>Instalację przy użyciu repozytorium pakietów — Ubuntu 14.04

Program PowerShell Core dla systemu Linux jest publikowany repozytoriów pakietów do łatwej instalacji (i aktualizacji).
Jest to preferowana metoda.

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/14.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Jako administratora należy zarejestrować się w repozytorium firmy Microsoft.
Od tego momentu, po prostu musisz użyć `sudo apt-get upgrade powershell` do aktualizacji instalacji.

### <a name="installation-via-direct-download---ubuntu-1404"></a>Instalację za pomocą bezpośredniego pobierania — Ubuntu 14.04

Pobierz pakiet Debian `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`
z [zwalnia][] strony na komputerze Ubuntu.

Następnie wykonaj następujące czynności w terminalu:

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i` Polecenia nie powiodło się niewypełnienia zależności.
> Następne polecenie `apt-get install -f` rozwiązuje te problemy, a następnie kończy Konfigurowanie pakietami programu PowerShell.

### <a name="uninstallation---ubuntu-1404"></a>Dezinstalacja — Ubuntu 14.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a>Ubuntu 16.04

### <a name="installation-via-package-repository---ubuntu-1604"></a>Instalację przy użyciu repozytorium pakietów — Ubuntu 16.04

Program PowerShell Core dla systemu Linux jest publikowany repozytoriów pakietów do łatwej instalacji (i aktualizacji).
Jest to preferowana metoda.

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Po zarejestrowaniu programu Microsoft repository raz jako administratora, od tego momentu, po prostu musisz użyć `sudo apt-get upgrade powershell` ją zaktualizować.

### <a name="installation-via-direct-download---ubuntu-1604"></a>Instalację za pomocą bezpośredniego pobierania — Ubuntu 16.04

Pobierz pakiet Debian `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`
z [zwalnia][] strony na komputerze Ubuntu.

Następnie wykonaj następujące czynności w terminalu:

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i` Polecenia nie powiodło się niewypełnienia zależności.
> Następne polecenie `apt-get install -f` rozwiązuje te problemy, a następnie kończy Konfigurowanie pakietami programu PowerShell.

### <a name="uninstallation---ubuntu-1604"></a>Dezinstalacja — Ubuntu 16.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a>Ubuntu 18.04

> [!NOTE]
> Dodano obsługę systemu Ubuntu 18.04 po `6.1.0-preview.2`

### <a name="installation-via-package-repository---ubuntu-1804"></a>Instalację przy użyciu repozytorium pakietów — Ubuntu 18.04

Program PowerShell Core dla systemu Linux jest publikowany repozytoriów pakietów do łatwej instalacji (i aktualizacji).
Jest to preferowana metoda.

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Po zarejestrowaniu programu Microsoft repository raz jako administratora, od tego momentu, po prostu musisz użyć `sudo apt-get upgrade powershell` ją zaktualizować.

### <a name="installation-via-direct-download---ubuntu-1804"></a>Instalację za pomocą bezpośredniego pobierania — Ubuntu 18.04

Pobierz pakiet Debian `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`
z [zwalnia][] strony na komputerze Ubuntu.

Następnie wykonaj następujące czynności w terminalu:

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i` Polecenia nie powiodło się niewypełnienia zależności.
> Następne polecenie `apt-get install -f` rozwiązuje te problemy, a następnie kończy Konfigurowanie pakietami programu PowerShell.

### <a name="uninstallation---ubuntu-1804"></a>Dezinstalacja — Ubuntu 18.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a>Ubuntu 18.10

> [!NOTE]
> Dodano obsługę systemu Ubuntu 18.10 po `6.1.0-preview.3`.
> Podobnie jak 18.10 dzienną kompilacją, jest tylko społeczności obsługiwane.

Instalowanie na 18.10 jest świadczona za pośrednictwem `snapd`. Zobacz [przyciąganie pakietu] [ snap] pełne instrukcje;

## <a name="debian-8"></a>Debian 8

### <a name="installation-via-package-repository---debian-8"></a>Instalację przy użyciu repozytorium pakietów — Debian 8

Program PowerShell Core dla systemu Linux jest publikowany repozytoriów pakietów do łatwej instalacji (i aktualizacji).
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

Po zarejestrowaniu programu Microsoft repository raz jako administratora, od tego momentu, po prostu musisz użyć `sudo apt-get upgrade powershell` ją zaktualizować.

### <a name="installation-via-direct-download---debian-8"></a>Instalację za pomocą bezpośredniego pobierania — Debian 8

Pobierz pakiet Debian `powershell_6.1.0-1.debian.8_amd64.deb`
z [zwalnia][] strony na komputerze Debian.

Następnie wykonaj następujące czynności w terminalu:

```sh
sudo dpkg -i powershell_6.1.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i` Polecenia nie powiodło się niewypełnienia zależności.
> Następne polecenie `apt-get install -f` rozwiązuje te problemy, a następnie kończy Konfigurowanie pakietami programu PowerShell.

### <a name="uninstallation---debian-8"></a>Dezinstalacja — Debian 8

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a>Debian 9

### <a name="installation-via-package-repository---debian-9"></a>Instalację przy użyciu repozytorium pakietów - Debian 9

Program PowerShell Core dla systemu Linux jest publikowany repozytoriów pakietów do łatwej instalacji (i aktualizacji).
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

Po zarejestrowaniu programu Microsoft repository raz jako administratora, od tego momentu, po prostu musisz użyć `sudo apt-get upgrade powershell` ją zaktualizować.

### <a name="installation-via-direct-download---debian-9"></a>Instalację za pomocą bezpośredniego pobierania - Debian 9

Pobierz pakiet Debian `powershell_6.1.0-1.debian.9_amd64.deb`
z [zwalnia][] strony na komputerze Debian.

Następnie wykonaj następujące czynności w terminalu:

```sh
sudo dpkg -i powershell_6.1.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a>Dezinstalacja — Debian 9

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a>CentOS 7

> [!NOTE]
> Ten pakiet działa także w systemie Oracle Linux 7.

### <a name="installation-via-package-repository-preferred---centos-7"></a>Instalację przy użyciu repozytorium pakietów (preferowany) - CentOS 7

Program PowerShell Core dla systemu Linux jest publikowany oficjalnych repozytoriów firmy Microsoft do łatwej instalacji (i aktualizacji).

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Po zarejestrowaniu programu Microsoft repository raz jako administratora, po prostu musisz użyć `sudo yum update powershell` do zaktualizowania programu PowerShell.

### <a name="installation-via-direct-download---centos-7"></a>Instalację za pomocą bezpośredniego pobierania - CentOS 7

Za pomocą [CentOS 7][], Pobierz pakiet obr. / min `powershell-6.1.0-1.rhel.7.x86_64.rpm`
z [zwalnia][] strony na komputerze CentOS.

Następnie wykonaj następujące czynności w terminalu:

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

Można także zainstalować obr. / min bez pośredniego kroku pobierania go:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a>Dezinstalacja - CentOS 7

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a>Instalację przy użyciu repozytorium pakietów (preferowany) - Red Hat Enterprise Linux (RHEL) 7

Program PowerShell Core dla systemu Linux jest publikowany oficjalnych repozytoriów firmy Microsoft do łatwej instalacji (i aktualizacji).

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Po zarejestrowaniu programu Microsoft repository raz jako administratora, po prostu musisz użyć `sudo yum update powershell` do zaktualizowania programu PowerShell.

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a>Instalację za pomocą bezpośredniego pobierania - Red Hat Enterprise Linux (RHEL) 7

Pobierz pakiet obr. / min `powershell-6.1.0-1.rhel.7.x86_64.rpm`
z [zwalnia][] strony na komputerze Red Hat Enterprise Linux.

Następnie wykonaj następujące czynności w terminalu:

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

Można także zainstalować obr. / min bez pośredniego kroku pobierania go:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>Dezinstalacja - Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse-423"></a>OpenSUSE 42.3

Podczas instalowania programu PowerShell Core `zypper` może Zgłoś następujący błąd:

```Output
Problem: nothing provides libcurl needed by powershell-6.1.0-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.1.0-1.rhel.7.x86_64
 Solution 2: break powershell-6.1.0-1.rhel.7.x86_64 by ignoring some of its dependencies
```

W takim przypadku upewnij się, że zgodne `libcurl` biblioteka jest obecny, sprawdzając, czy następujące polecenie pokazuje `libcurl4` pakietu jako zainstalowane:

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

Następnie wybierz `break powershell-6.1.0-1.rhel.7.x86_64 by ignoring some of its dependencies` rozwiązania podczas instalowania pakietu programu PowerShell.

### <a name="installation-via-package-repository-preferred---opensuse-423"></a>Instalację przy użyciu repozytorium pakietów (preferowany) - OpenSUSE 42.3

Program PowerShell Core dla systemu Linux jest publikowany oficjalnych repozytoriów firmy Microsoft do łatwej instalacji (i aktualizacji).

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Repository
zypper ar https://packages.microsoft.com/rhel/7/prod/

# Update the list of products
sudo zypper update

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-423"></a>Instalację za pomocą bezpośredniego pobierania - OpenSUSE 42.3

Pobierz pakiet RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm` z [zwalnia][] strony na komputerze OpenSUSE.

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

Można także zainstalować obr. / min bez pośredniego kroku pobierania go:

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-423"></a>Dezinstalacja - OpenSUSE 42.3

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a>Fedora

> [!NOTE]
> Fedora 28 jest obsługiwane tylko w sytuacji, w programie PowerShell Core 6.1 lub nowszej.

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a>Instalację przy użyciu repozytorium pakietów (preferowany) - Fedora 27, Fedora 28

Program PowerShell Core dla systemu Linux jest publikowany oficjalnych repozytoriów firmy Microsoft do łatwej instalacji (i aktualizacji).

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a>Instalację za pomocą bezpośredniego pobierania - Fedora 27, Fedora 28

Pobierz pakiet obr. / min `powershell-6.1.0-1.rhel.7.x86_64.rpm`
z [zwalnia][] strony na komputerze Fedora.

Następnie wykonaj następujące czynności w terminalu:

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

Można także zainstalować obr. / min bez pośredniego kroku pobierania go:

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a>Dezinstalacja - Fedora 27, Fedora 28

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Arch Linux

> [!NOTE]
> Obsługa architektury jest eksperymentalne.

Program PowerShell jest dostępny z [Arch systemu Linux][] użytkownika repozytorium (AUR).

* Może być skompilowana przy użyciu [najnowsze tagiem wydania][arch-release]
* Może być kompilowane z [najnowsze zatwierdzenie do wzorca][arch-git]
* Można zainstalować, za pomocą [najnowszej wersji pliku binarnego][arch-bin]

Pakiety w AUR są utrzymywane społeczności — Brak obsługi oficjalnych.

Aby uzyskać więcej informacji na temat instalowania pakietów z AUR, zobacz [wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) lub społeczności [pliku DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).

[Arch systemu Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a>Przyciągaj pakietu

### <a name="getting-snapd"></a>Wprowadzenie snapd

`snapd` jest wymagany do uruchomienia przyciąganie.
Użyj [w instrukcjach](https://docs.snapcraft.io/core/install) aby upewnić się, że masz `snapd` zainstalowane.

### <a name="installation-via-snap"></a>Instalację za pomocą przystawki

Program PowerShell Core dla systemu Linux, są publikowane w [magazynu przystawki](https://snapcraft.io/store) łatwej instalacji (i aktualizacji).
Jest to preferowana metoda.

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

Po zainstalowaniu przystawki zostanie automatycznie uaktualniona, ale możesz wyzwolić uaktualnienia przy użyciu `sudo snap refresh powershell-preview`.

### <a name="uninstallation"></a>Dezinstalacja

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a>Kali

### <a name="installation"></a>Instalacja

```sh
# Download & Install prerequisites
wget http://ftp.us.debian.org/debian/pool/main/i/icu/libicu57_57.1-9_amd64.deb
dpkg -i libicu57_57.1-9_amd64.deb
apt-get update && apt-get install -y curl gnupg apt-transport-https

# Add Microsoft public repository key to APT
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -

# Add Microsoft package repository to the source list
echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" | tee /etc/apt/sources.list.d/powershell.list

# Install PowerShell package
apt-get update && apt-get install -y powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a>Dezinstalacja - Kali

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a>Raspbian

> [!NOTE]
> Obsługa Raspbian jest eksperymentalne.

Program PowerShell jest obecnie obsługiwane tylko w Raspbian Stretch.

Również CoreCLR (i w związku z tym program PowerShell Core) będą działać tylko na urządzeniach Pi 2 i Pi 3 jako inne urządzenia, takie jak [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), ma nieobsługiwany procesor.

Pobierz [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) i postępuj zgodnie z [instrukcje dotyczące instalacji](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) uruchomienie go na swoje Pi.

### <a name="installation"></a>Instalacja

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.1.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

Opcjonalnie można utworzyć łącza symbolicznego, aby można było uruchomić środowisko PowerShell bez określenia ścieżki do "pwsh" binarny

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

## <a name="binary-archives"></a>Binarny archiwa

Plik binarny programu PowerShell `tar.gz` archiwa są dostarczane dla platform Linux umożliwić zaawansowanych scenariuszach wdrożenia.

### <a name="dependencies"></a>Zależności

PowerShell tworzy przenośne pliki binarne dla wszystkich dystrybucjach systemu Linux.
Środowisko uruchomieniowe programu .NET Core wymaga różnych składników zależnych w różnych dystrybucjach — a więc programu PowerShell działa tak samo.

Poniższej tabeli przedstawiono zależności platformy .NET Core 2.0, które są oficjalnie obsługiwane przez różne dystrybucje systemu Linux.

| System operacyjny                 | Zależności |
| ------------------ | ------------ |
| Ubuntu 14.04       | libc6, liblttng libgssapi-krb5-2, libgcc1,-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Ubuntu 16.04       | libc6, liblttng libgssapi-krb5-2, libgcc1,-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55 |
| Ubuntu 17.10       | libc6, liblttng libgssapi-krb5-2, libgcc1,-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57 |
| Ubuntu 18.04       | libc6, liblttng libgssapi-krb5-2, libgcc1,-ust0, libstdc ++ 6 <br> libcurl3 libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60 |
| Debian 8 (Jessie)  | libc6, liblttng libgssapi-krb5-2, libgcc1,-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Debian 9 (Stretch) | libc6, liblttng libgssapi-krb5-2, libgcc1,-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 <br> OpenSUSE OpenSUSE 42.3 | libunwind, libcurl, biblioteki openssl, libicu |
| Fedora 27 <br> Fedora 28 | libunwind, libcurl, openssl-libs, libicu, compat-openssl10 |

Aby wdrożyć pliki binarne programu PowerShell, w dystrybucjach systemu Linux, które nie są oficjalnie obsługiwane, należy zainstalować wymagane zależności dla docelowego systemu operacyjnego w oddzielne kroki.
Na przykład naszym [dockerfile Amazon Linux] [ amazon-dockerfile] najpierw zainstalowanie zależności, a następnie wyodrębnia systemu Linux `tar.gz` archiwum.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a>Instalacja — archiwum binarne

#### <a name="linux"></a>Linux

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a>Odinstalowywanie archiwum binarne

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a>Ścieżki

* `$PSHOME` jest `/opt/microsoft/powershell/6.1.0/`
* Profile użytkowników będą odczytywane z `~/.config/powershell/profile.ps1`
* Domyślne profile będą odczytywane z `$PSHOME/profile.ps1`
* Moduły użytkownika zostanie odczytany z `~/.local/share/powershell/Modules`
* Udostępnione moduły będą odczytywane z `/usr/local/share/powershell/Modules`
* Domyślne moduły będą odczytywane z `$PSHOME/Modules`
* Historia PSReadline zostanie zarejestrowana w celu `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Profile przestrzegają konfiguracji dla hosta programu PowerShell, więc domyślne profile specyficzne dla hosta istnieje w `Microsoft.PowerShell_profile.ps1` w tej samej lokalizacji.

Stosuje się do programu PowerShell [specyfikację katalogu Base XDG] [ xdg-bds] w systemie Linux.

[zwalnia]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
