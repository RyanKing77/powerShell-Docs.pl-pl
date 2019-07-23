---
title: Instalowanie programu PowerShell Core w systemie Linux
description: Informacje na temat instalowania programu PowerShell Core w różnych dystrybucjach systemu Linux
ms.date: 07/19/2019
ms.openlocfilehash: 929b153ef784f3203cd31a0e2fc52e744a07532f
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372198"
---
# <a name="installing-powershell-core-on-linux"></a>Instalowanie programu PowerShell Core w systemie Linux

Obsługuje [Ubuntu 16,04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18,10][u1810], [Debian 9][deb9],
 [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][RHEL7], [openSUSE 42,3][opensuse], [openSUSE przestępny 15][opensuse] , [Fedora 27][fedora], [Fedora 28][Fedora]i [Arch Linux][arch].

W przypadku dystrybucji systemu Linux, które nie są oficjalnie obsługiwane, można spróbować zainstalować program PowerShell przy użyciu [pakietu przyciągania programu PowerShell][snap]. Możesz również spróbować wdrożyć pliki binarne programu PowerShell bezpośrednio przy użyciu [ `tar.gz` archiwum][tar]systemu Linux, ale konieczne jest skonfigurowanie wymaganych zależności w oparciu o system operacyjny w osobnych krokach.

Wszystkie pakiety są dostępne na naszej stronie [wydań][] usługi GitHub. Po zainstalowaniu pakietu Uruchom `pwsh` polecenie z terminalu.

[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a>Instalowanie wersji zapoznawczej

W przypadku instalowania programu PowerShell Core w wersji zapoznawczej dla systemu Linux za pośrednictwem repozytorium pakietów `powershell` nazwa `powershell-preview`pakietu zmieni się z na.

Instalowanie za pomocą bezpośredniego pobierania nie zmienia się, a nie z nazwą pliku.

Poniższa tabela zawiera polecenia służące do instalowania stabilnych i wersji zapoznawczych pakietów przy użyciu różnych menedżerów pakietów:

|Dystrybucje|Stabilne polecenie | Podgląd — polecenie |
|---------------|---------------|-----------------|
| Ubuntu, Debian |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| CentOS, RedHat |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| Fedora   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1604"></a>Ubuntu 16.04

### <a name="installation-via-package-repository---ubuntu-1604"></a>Instalacja za pośrednictwem repozytorium pakietów — Ubuntu 16,04

Program PowerShell Core dla systemu Linux jest publikowany w repozytoriach pakietów w celu ułatwienia instalacji i aktualizacji.

Preferowana metoda jest następująca:

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

Jako administratora Zarejestruj repozytorium Microsoft. Po zarejestrowaniu można zaktualizować program PowerShell `sudo apt-get upgrade powershell`za pomocą polecenia.

### <a name="installation-via-direct-download---ubuntu-1604"></a>Instalacja za pośrednictwem bezpośredniego pobierania — Ubuntu 16,04

Pobierz pakiet `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` Debian ze strony [wydań][] na maszynę Ubuntu.

Następnie w terminalu wykonaj następujące polecenia:

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i` Polecenie kończy się niepowodzeniem z zależnościami niewypełnienia. Następne polecenie, rozwiązuje `apt-get install -f` te problemy, a następnie kończy konfigurowanie pakietu programu PowerShell.

### <a name="uninstallation---ubuntu-1604"></a>Dezinstalacja — Ubuntu 16,04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a>Ubuntu 18.04

### <a name="installation-via-package-repository---ubuntu-1804"></a>Instalacja za pośrednictwem repozytorium pakietów — Ubuntu 18,04

Program PowerShell Core dla systemu Linux jest publikowany w repozytoriach pakietów w celu ułatwienia instalacji i aktualizacji.

Preferowana metoda jest następująca:

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Enable the "universe" repositories
sudo add-apt-repository universe

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Jako administratora Zarejestruj repozytorium Microsoft. Po zarejestrowaniu można zaktualizować program PowerShell `sudo apt-get upgrade powershell`za pomocą polecenia.

### <a name="installation-via-direct-download---ubuntu-1804"></a>Instalacja za pośrednictwem bezpośredniego pobierania — Ubuntu 18,04

Pobierz pakiet `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` Debian ze strony [wydań][] na maszynę Ubuntu.

Następnie w terminalu wykonaj następujące polecenia:

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> `dpkg -i` Polecenie kończy się niepowodzeniem z zależnościami niewypełnienia. Następne polecenie, rozwiązuje `apt-get install -f` te problemy, a następnie kończy konfigurowanie pakietu programu PowerShell.

### <a name="uninstallation---ubuntu-1804"></a>Dezinstalacja — Ubuntu 18,04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a>Ubuntu 18,10

> [!NOTE]
> Jako 18,10 jest [wydaniem tymczasowym](https://www.ubuntu.com/about/release-cycle), jest to jedyna [obsługiwana społeczność](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).

Instalowanie na 18,10 jest obsługiwane za `snapd`pośrednictwem. Aby uzyskać pełne instrukcje, zobacz [pakiet Snap][snap] .

## <a name="debian-8"></a>Debian 8

### <a name="installation-via-package-repository---debian-8"></a>Instalacja za pośrednictwem repozytorium pakietów — Debian 8

Program PowerShell Core dla systemu Linux jest publikowany w repozytoriach pakietów w celu ułatwienia instalacji i aktualizacji.

Preferowana metoda jest następująca:

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

Jako administratora Zarejestruj repozytorium Microsoft. Po zarejestrowaniu można zaktualizować program PowerShell `sudo apt-get upgrade powershell`za pomocą polecenia.

## <a name="debian-9"></a>Debian 9

### <a name="installation-via-package-repository---debian-9"></a>Instalacja za pośrednictwem repozytorium pakietów — Debian 9

Program PowerShell Core dla systemu Linux jest publikowany w repozytoriach pakietów w celu ułatwienia instalacji i aktualizacji.

Preferowana metoda jest następująca:

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

Jako administratora Zarejestruj repozytorium Microsoft. Po zarejestrowaniu można zaktualizować program PowerShell `sudo apt-get upgrade powershell`za pomocą polecenia.

### <a name="installation-via-direct-download---debian-9"></a>Instalacja za pośrednictwem bezpośredniego pobierania — Debian 9

Pobierz pakiet `powershell_6.2.0-1.debian.9_amd64.deb` Debian ze strony [wydań][] na maszynę debian.

Następnie w terminalu wykonaj następujące polecenia:

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a>Dezinstalacja — Debian 9

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a>CentOS 7

> [!NOTE]
> Ten pakiet działa w Oracle Linux 7.

### <a name="installation-via-package-repository-preferred---centos-7"></a>Instalacja za pośrednictwem repozytorium pakietów (preferowany) — CentOS 7

Program PowerShell Core dla systemu Linux jest publikowany w oficjalnych repozytoriach firmy Microsoft w celu ułatwienia instalacji i aktualizacji.

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Jako administratora Zarejestruj repozytorium Microsoft. Po zarejestrowaniu można zaktualizować program PowerShell `sudo yum update powershell`za pomocą polecenia.

### <a name="installation-via-direct-download---centos-7"></a>Instalacja za pośrednictwem bezpośredniego pobierania — CentOS 7

Korzystając z programu [CentOS 7][], Pobierz pakiet `powershell-6.2.0-1.rhel.7.x86_64.rpm` RPM ze strony [wydań][] na maszynę CentOS.

Następnie w terminalu wykonaj następujące polecenia:

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

Możesz zainstalować KCO bez pośredniego kroku pobierania go:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a>Dezinstalacja — CentOS 7

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a>Instalacja za pośrednictwem repozytorium pakietów (preferowany) — Red Hat Enterprise Linux (RHEL) 7

Program PowerShell Core dla systemu Linux jest publikowany w oficjalnych repozytoriach firmy Microsoft w celu ułatwienia instalacji i aktualizacji.

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Jako administratora Zarejestruj repozytorium Microsoft. Po zarejestrowaniu można zaktualizować program PowerShell `sudo yum update powershell`za pomocą polecenia.

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a>Instalacja za pośrednictwem bezpośredniego pobierania — Red Hat Enterprise Linux (RHEL) 7

Pobierz pakiet `powershell-6.2.0-1.rhel.7.x86_64.rpm` RPM ze strony [wydań][] na maszynę Red Hat Enterprise Linux.

Następnie w terminalu wykonaj następujące polecenia:

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

Możesz zainstalować KCO bez pośredniego kroku pobierania go:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>Dezinstalacja-Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a>openSUSE

### <a name="installation---opensuse-423"></a>Instalacja — openSUSE 42,3

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a>Instalacja — openSUSE przestępny 15

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a>Dezinstalacja-openSUSE 42,3, openSUSE przestępny 15

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a>Fedora

> [!NOTE]
> Fedora 28 jest obsługiwana tylko w programie PowerShell Core 6,1 i nowszym.

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a>Instalacja za pośrednictwem repozytorium pakietów (preferowany) — Fedora 27, Fedora 28

Program PowerShell Core dla systemu Linux jest publikowany w oficjalnych repozytoriach firmy Microsoft w celu ułatwienia instalacji i aktualizacji.

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a>Instalacja za pośrednictwem bezpośredniego pobierania — Fedora 27, Fedora 28

Pobierz pakiet `powershell-6.2.0-1.rhel.7.x86_64.rpm` RPM ze strony [wydań][] na maszynę Fedora.

Następnie w terminalu wykonaj następujące polecenia:

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

Możesz zainstalować KCO bez pośredniego kroku pobierania go:

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a>Dezinstalacja — Fedora 27, Fedora 28

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Arch Linux

> [!NOTE]
> Obsługa archów jest eksperymentalna.

Program PowerShell jest dostępny w repozytorium użytkowników w systemie [Łuk z systemem Linux][] (AUR).

* Można go skompilować z [najnowszą wersją otagowaną][arch-release]
* Można go skompilować z [ostatniego zatwierdzenia do głównego][arch-git]
* Można go zainstalować przy użyciu [najnowszej wersji pliku binarnego][arch-bin]

Pakiety w AUR są utrzymywane przez społeczność. nie ma oficjalnego wsparcia.

Aby uzyskać więcej informacji na temat instalowania pakietów z programu AUR, zobacz witrynę [typu wiki systemu Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) lub społeczność [pliku dockerfile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).

[Łuk z systemem Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a>Pakiet przyciągania

### <a name="getting-snapd"></a>Pobieranie przyciągania

`snapd`jest wymagany do uruchomienia przyciągania. Skorzystaj z [tych instrukcji](https://docs.snapcraft.io/core/install) , aby upewnić `snapd` się, że zainstalowano program.

### <a name="installation-via-snap"></a>Instalacja za pomocą przystawki

Program PowerShell Core dla systemu Linux jest publikowany w [magazynie Snap](https://snapcraft.io/store) w celu ułatwienia instalacji i aktualizacji.

Preferowana metoda jest następująca:

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

Aby zainstalować wersję zapoznawczą, należy użyć następującej metody:

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

Po zakończeniu instalacji przyciąganie zostanie automatycznie uaktualnione. Możesz wyzwolić uaktualnienie przy użyciu `sudo snap refresh powershell` lub `sudo snap refresh powershell-preview`.

### <a name="uninstallation"></a>Dezinstalacji

```sh
sudo snap remove powershell
```

lub

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a>Kali

### <a name="installation---kali"></a>Instalacja — Kali

```sh
# Download & Install prerequisites
wget http://ftp.us.debian.org/debian/pool/main/i/icu/libicu57_57.1-6+deb9u2_amd64.deb
dpkg -i libicu57_57.1-6+deb9u2_amd64.deb
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

### <a name="uninstallation---kali"></a>Dezinstalacja — Kali

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a>Raspbian

> [!NOTE]
> Obsługa raspbian jest eksperymentalna.

Obecnie program PowerShell jest obsługiwany tylko w rozciągnięciu raspbian.

CoreCLR i PowerShell Core działają tylko na urządzeniach z procesorami pi 2 i pi 3 jako innych urządzeń, takich jak [pi zero](https://github.com/dotnet/coreclr/issues/10605), ale mają nieobsługiwany procesor.

Pobierz [rozciąganie raspbian](https://www.raspberrypi.org/downloads/raspbian/) i postępuj zgodnie z [instrukcjami instalacji](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) , aby uzyskać je do liczby pi.

### <a name="installation---raspbian"></a>Instalacja — raspbian

```sh
###################################
# Prerequisites

# Update package lists
sudo apt-get update

# Install libunwind8 and libssl1.0
# Regex is used to ensure that we do not install libssl1.0-dev, as it is a variant that is not required
sudo apt-get install '^libssl1.0.[0-9]$' libunwind8 -y

###################################
# Download and extract PowerShell

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.2.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

Opcjonalnie można utworzyć link symboliczny, aby uruchomić program PowerShell bez określania ścieżki do `pwsh` pliku binarnego.

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a>Dezinstalacja — raspbian

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a>Archiwa binarne

Archiwa `tar.gz` binarne programu PowerShell są udostępniane dla platform systemu Linux w celu włączenia zaawansowanych scenariuszy wdrażania.

### <a name="dependencies"></a>Zależności

Program PowerShell kompiluje przenośne pliki binarne dla wszystkich dystrybucji systemu Linux. Jednak środowisko uruchomieniowe programu .NET Core wymaga różnych zależności od różnych dystrybucji, a program PowerShell jest zbyt mało.

Na poniższym wykresie przedstawiono zależności programu .NET Core 2,0, które są oficjalnie obsługiwane przez różne dystrybucje systemu Linux.

| System operacyjny                 | Zależności |
| ------------------ | ------------ |
| Ubuntu 16.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55 |
| Ubuntu 17,10       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57 |
| Ubuntu 18.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu60 |
| Debian 8 (Jessie)  | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Debian 9 (Rozciągnij) | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 | libunwind, libcurl, OpenSSL-libs, libicu |
| openSUSE 42,3 | libcurl4, libopenssl1_0_0, libicu52_1 |
| openSUSE przestępny 15 | libcurl4, libopenssl1_0_0, libicu60_2 |
| Fedora 27 <br> Fedora 28 | libunwind, libcurl, openssl-libs, libicu, compat-openssl10 |

W celu wdrożenia plików binarnych programu PowerShell na dystrybucji systemu Linux, które nie są oficjalnie obsługiwane, należy zainstalować wymagane zależności w docelowym systemie operacyjnym w oddzielnych krokach. Na przykład nasza firma [Amazon Linux pliku dockerfile][amazon-dockerfile] najpierw instaluje zależności, a następnie wyodrębnia archiwum systemu `tar.gz` Linux.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a>Instalacja — archiwa binarne

#### <a name="linux"></a>Linux

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a>Odinstalowywanie archiwów binarnych

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a>Ścieżki

* `$PSHOME`była`/opt/microsoft/powershell/6.2.0/`
* Zostaną odczytane profile użytkowników`~/.config/powershell/profile.ps1`
* Domyślne profile zostaną odczytane`$PSHOME/profile.ps1`
* Moduły użytkownika zostaną odczytane`~/.local/share/powershell/Modules`
* Zostaną odczytane moduły udostępnione`/usr/local/share/powershell/Modules`
* Domyślne moduły zostaną odczytane`$PSHOME/Modules`
* Historia PSReadline zostanie zarejestrowana w`~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Profile respektują konfigurację dla każdego hosta programu PowerShell, dlatego w tych samych lokalizacjach istnieją `Microsoft.PowerShell_profile.ps1` domyślne profile specyficzne dla hosta.

Program PowerShell przestrzega [specyfikacji xdg Base Directory][xdg-bds] w systemie Linux.

[wydań]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
