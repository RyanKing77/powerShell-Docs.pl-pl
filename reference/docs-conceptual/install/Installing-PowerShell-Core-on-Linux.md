---
title: Instalowanie programu PowerShell Core w systemie Linux
description: Informacje na temat instalowania programu PowerShell Core w różnych dystrybucjach systemu Linux
ms.date: 07/19/2019
ms.openlocfilehash: 929b153ef784f3203cd31a0e2fc52e744a07532f
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2019
ms.locfileid: "68372198"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="dae25-103">Instalowanie programu PowerShell Core w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="dae25-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="dae25-104">Obsługuje [Ubuntu 16,04][u16], [Ubuntu 18,04][u1804], [Ubuntu 18,10][u1810], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42,3][opensuse], [openSUSE przestępny 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], i [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="dae25-104">Supports [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="dae25-105">W przypadku dystrybucji systemu Linux, które nie są oficjalnie obsługiwane, można spróbować zainstalować program PowerShell przy użyciu [pakietu przyciągania programu PowerShell][snap].</span><span class="sxs-lookup"><span data-stu-id="dae25-105">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="dae25-106">Możesz również spróbować wdrożyć pliki binarne programu PowerShell bezpośrednio przy użyciu [ `tar.gz` archiwum][tar]systemu Linux, ale konieczne jest skonfigurowanie wymaganych zależności w oparciu o system operacyjny w osobnych krokach.</span><span class="sxs-lookup"><span data-stu-id="dae25-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="dae25-107">Wszystkie pakiety są dostępne na naszej stronie [wydań][] usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="dae25-107">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="dae25-108">Po zainstalowaniu pakietu Uruchom `pwsh` polecenie z terminalu.</span><span class="sxs-lookup"><span data-stu-id="dae25-108">After the package is installed, run `pwsh` from a terminal.</span></span>

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

## <a name="installing-preview-releases"></a><span data-ttu-id="dae25-109">Instalowanie wersji zapoznawczej</span><span class="sxs-lookup"><span data-stu-id="dae25-109">Installing Preview Releases</span></span>

<span data-ttu-id="dae25-110">W przypadku instalowania programu PowerShell Core w wersji zapoznawczej dla systemu Linux za pośrednictwem repozytorium pakietów `powershell` nazwa `powershell-preview`pakietu zmieni się z na.</span><span class="sxs-lookup"><span data-stu-id="dae25-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="dae25-111">Instalowanie za pomocą bezpośredniego pobierania nie zmienia się, a nie z nazwą pliku.</span><span class="sxs-lookup"><span data-stu-id="dae25-111">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="dae25-112">Poniższa tabela zawiera polecenia służące do instalowania stabilnych i wersji zapoznawczych pakietów przy użyciu różnych menedżerów pakietów:</span><span class="sxs-lookup"><span data-stu-id="dae25-112">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="dae25-113">Dystrybucje</span><span class="sxs-lookup"><span data-stu-id="dae25-113">Distribution(s)</span></span>|<span data-ttu-id="dae25-114">Stabilne polecenie</span><span class="sxs-lookup"><span data-stu-id="dae25-114">Stable Command</span></span> | <span data-ttu-id="dae25-115">Podgląd — polecenie</span><span class="sxs-lookup"><span data-stu-id="dae25-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="dae25-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="dae25-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="dae25-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="dae25-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="dae25-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="dae25-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1604"></a><span data-ttu-id="dae25-119">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="dae25-119">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="dae25-120">Instalacja za pośrednictwem repozytorium pakietów — Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="dae25-120">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="dae25-121">Program PowerShell Core dla systemu Linux jest publikowany w repozytoriach pakietów w celu ułatwienia instalacji i aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="dae25-121">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="dae25-122">Preferowana metoda jest następująca:</span><span class="sxs-lookup"><span data-stu-id="dae25-122">The preferred method is as follows:</span></span>

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

<span data-ttu-id="dae25-123">Jako administratora Zarejestruj repozytorium Microsoft.</span><span class="sxs-lookup"><span data-stu-id="dae25-123">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="dae25-124">Po zarejestrowaniu można zaktualizować program PowerShell `sudo apt-get upgrade powershell`za pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="dae25-124">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="dae25-125">Instalacja za pośrednictwem bezpośredniego pobierania — Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="dae25-125">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="dae25-126">Pobierz pakiet `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` Debian ze strony [wydań][] na maszynę Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="dae25-126">Download the Debian package `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="dae25-127">Następnie w terminalu wykonaj następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="dae25-127">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="dae25-128">`dpkg -i` Polecenie kończy się niepowodzeniem z zależnościami niewypełnienia.</span><span class="sxs-lookup"><span data-stu-id="dae25-128">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="dae25-129">Następne polecenie, rozwiązuje `apt-get install -f` te problemy, a następnie kończy konfigurowanie pakietu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dae25-129">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="dae25-130">Dezinstalacja — Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="dae25-130">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="dae25-131">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="dae25-131">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="dae25-132">Instalacja za pośrednictwem repozytorium pakietów — Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="dae25-132">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="dae25-133">Program PowerShell Core dla systemu Linux jest publikowany w repozytoriach pakietów w celu ułatwienia instalacji i aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="dae25-133">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="dae25-134">Preferowana metoda jest następująca:</span><span class="sxs-lookup"><span data-stu-id="dae25-134">The preferred method is as follows:</span></span>

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

<span data-ttu-id="dae25-135">Jako administratora Zarejestruj repozytorium Microsoft.</span><span class="sxs-lookup"><span data-stu-id="dae25-135">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="dae25-136">Po zarejestrowaniu można zaktualizować program PowerShell `sudo apt-get upgrade powershell`za pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="dae25-136">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="dae25-137">Instalacja za pośrednictwem bezpośredniego pobierania — Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="dae25-137">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="dae25-138">Pobierz pakiet `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` Debian ze strony [wydań][] na maszynę Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="dae25-138">Download the Debian package `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="dae25-139">Następnie w terminalu wykonaj następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="dae25-139">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="dae25-140">`dpkg -i` Polecenie kończy się niepowodzeniem z zależnościami niewypełnienia.</span><span class="sxs-lookup"><span data-stu-id="dae25-140">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="dae25-141">Następne polecenie, rozwiązuje `apt-get install -f` te problemy, a następnie kończy konfigurowanie pakietu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dae25-141">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="dae25-142">Dezinstalacja — Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="dae25-142">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="dae25-143">Ubuntu 18,10</span><span class="sxs-lookup"><span data-stu-id="dae25-143">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="dae25-144">Jako 18,10 jest [wydaniem tymczasowym](https://www.ubuntu.com/about/release-cycle), jest to jedyna [obsługiwana społeczność](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="dae25-144">As 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle), it is only [community supported](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span></span>

<span data-ttu-id="dae25-145">Instalowanie na 18,10 jest obsługiwane za `snapd`pośrednictwem.</span><span class="sxs-lookup"><span data-stu-id="dae25-145">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="dae25-146">Aby uzyskać pełne instrukcje, zobacz [pakiet Snap][snap] .</span><span class="sxs-lookup"><span data-stu-id="dae25-146">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="dae25-147">Debian 8</span><span class="sxs-lookup"><span data-stu-id="dae25-147">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="dae25-148">Instalacja za pośrednictwem repozytorium pakietów — Debian 8</span><span class="sxs-lookup"><span data-stu-id="dae25-148">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="dae25-149">Program PowerShell Core dla systemu Linux jest publikowany w repozytoriach pakietów w celu ułatwienia instalacji i aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="dae25-149">PowerShell Core, for Linux, is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="dae25-150">Preferowana metoda jest następująca:</span><span class="sxs-lookup"><span data-stu-id="dae25-150">The preferred method is as follows:</span></span>

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

<span data-ttu-id="dae25-151">Jako administratora Zarejestruj repozytorium Microsoft.</span><span class="sxs-lookup"><span data-stu-id="dae25-151">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="dae25-152">Po zarejestrowaniu można zaktualizować program PowerShell `sudo apt-get upgrade powershell`za pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="dae25-152">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="dae25-153">Debian 9</span><span class="sxs-lookup"><span data-stu-id="dae25-153">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="dae25-154">Instalacja za pośrednictwem repozytorium pakietów — Debian 9</span><span class="sxs-lookup"><span data-stu-id="dae25-154">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="dae25-155">Program PowerShell Core dla systemu Linux jest publikowany w repozytoriach pakietów w celu ułatwienia instalacji i aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="dae25-155">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="dae25-156">Preferowana metoda jest następująca:</span><span class="sxs-lookup"><span data-stu-id="dae25-156">The preferred method is as follows:</span></span>

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

<span data-ttu-id="dae25-157">Jako administratora Zarejestruj repozytorium Microsoft.</span><span class="sxs-lookup"><span data-stu-id="dae25-157">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="dae25-158">Po zarejestrowaniu można zaktualizować program PowerShell `sudo apt-get upgrade powershell`za pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="dae25-158">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="dae25-159">Instalacja za pośrednictwem bezpośredniego pobierania — Debian 9</span><span class="sxs-lookup"><span data-stu-id="dae25-159">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="dae25-160">Pobierz pakiet `powershell_6.2.0-1.debian.9_amd64.deb` Debian ze strony [wydań][] na maszynę debian.</span><span class="sxs-lookup"><span data-stu-id="dae25-160">Download the Debian package `powershell_6.2.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="dae25-161">Następnie w terminalu wykonaj następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="dae25-161">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="dae25-162">Dezinstalacja — Debian 9</span><span class="sxs-lookup"><span data-stu-id="dae25-162">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="dae25-163">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="dae25-163">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="dae25-164">Ten pakiet działa w Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="dae25-164">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="dae25-165">Instalacja za pośrednictwem repozytorium pakietów (preferowany) — CentOS 7</span><span class="sxs-lookup"><span data-stu-id="dae25-165">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="dae25-166">Program PowerShell Core dla systemu Linux jest publikowany w oficjalnych repozytoriach firmy Microsoft w celu ułatwienia instalacji i aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="dae25-166">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="dae25-167">Jako administratora Zarejestruj repozytorium Microsoft.</span><span class="sxs-lookup"><span data-stu-id="dae25-167">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="dae25-168">Po zarejestrowaniu można zaktualizować program PowerShell `sudo yum update powershell`za pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="dae25-168">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="dae25-169">Instalacja za pośrednictwem bezpośredniego pobierania — CentOS 7</span><span class="sxs-lookup"><span data-stu-id="dae25-169">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="dae25-170">Korzystając z programu [CentOS 7][], Pobierz pakiet `powershell-6.2.0-1.rhel.7.x86_64.rpm` RPM ze strony [wydań][] na maszynę CentOS.</span><span class="sxs-lookup"><span data-stu-id="dae25-170">Using [CentOS 7][], download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="dae25-171">Następnie w terminalu wykonaj następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="dae25-171">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="dae25-172">Możesz zainstalować KCO bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="dae25-172">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="dae25-173">Dezinstalacja — CentOS 7</span><span class="sxs-lookup"><span data-stu-id="dae25-173">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="dae25-175">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="dae25-175">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="dae25-176">Instalacja za pośrednictwem repozytorium pakietów (preferowany) — Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="dae25-176">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="dae25-177">Program PowerShell Core dla systemu Linux jest publikowany w oficjalnych repozytoriach firmy Microsoft w celu ułatwienia instalacji i aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="dae25-177">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="dae25-178">Jako administratora Zarejestruj repozytorium Microsoft.</span><span class="sxs-lookup"><span data-stu-id="dae25-178">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="dae25-179">Po zarejestrowaniu można zaktualizować program PowerShell `sudo yum update powershell`za pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="dae25-179">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="dae25-180">Instalacja za pośrednictwem bezpośredniego pobierania — Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="dae25-180">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="dae25-181">Pobierz pakiet `powershell-6.2.0-1.rhel.7.x86_64.rpm` RPM ze strony [wydań][] na maszynę Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="dae25-181">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="dae25-182">Następnie w terminalu wykonaj następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="dae25-182">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="dae25-183">Możesz zainstalować KCO bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="dae25-183">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="dae25-184">Dezinstalacja-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="dae25-184">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="dae25-185">openSUSE</span><span class="sxs-lookup"><span data-stu-id="dae25-185">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="dae25-186">Instalacja — openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="dae25-186">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="dae25-187">Instalacja — openSUSE przestępny 15</span><span class="sxs-lookup"><span data-stu-id="dae25-187">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="dae25-188">Dezinstalacja-openSUSE 42,3, openSUSE przestępny 15</span><span class="sxs-lookup"><span data-stu-id="dae25-188">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="dae25-189">Fedora</span><span class="sxs-lookup"><span data-stu-id="dae25-189">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="dae25-190">Fedora 28 jest obsługiwana tylko w programie PowerShell Core 6,1 i nowszym.</span><span class="sxs-lookup"><span data-stu-id="dae25-190">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="dae25-191">Instalacja za pośrednictwem repozytorium pakietów (preferowany) — Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="dae25-191">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="dae25-192">Program PowerShell Core dla systemu Linux jest publikowany w oficjalnych repozytoriach firmy Microsoft w celu ułatwienia instalacji i aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="dae25-192">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="dae25-193">Instalacja za pośrednictwem bezpośredniego pobierania — Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="dae25-193">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="dae25-194">Pobierz pakiet `powershell-6.2.0-1.rhel.7.x86_64.rpm` RPM ze strony [wydań][] na maszynę Fedora.</span><span class="sxs-lookup"><span data-stu-id="dae25-194">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="dae25-195">Następnie w terminalu wykonaj następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="dae25-195">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="dae25-196">Możesz zainstalować KCO bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="dae25-196">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="dae25-197">Dezinstalacja — Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="dae25-197">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="dae25-198">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="dae25-198">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="dae25-199">Obsługa archów jest eksperymentalna.</span><span class="sxs-lookup"><span data-stu-id="dae25-199">Arch support is experimental.</span></span>

<span data-ttu-id="dae25-200">Program PowerShell jest dostępny w repozytorium użytkowników w systemie [Łuk z systemem Linux][] (AUR).</span><span class="sxs-lookup"><span data-stu-id="dae25-200">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="dae25-201">Można go skompilować z [najnowszą wersją otagowaną][arch-release]</span><span class="sxs-lookup"><span data-stu-id="dae25-201">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="dae25-202">Można go skompilować z [ostatniego zatwierdzenia do głównego][arch-git]</span><span class="sxs-lookup"><span data-stu-id="dae25-202">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="dae25-203">Można go zainstalować przy użyciu [najnowszej wersji pliku binarnego][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="dae25-203">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="dae25-204">Pakiety w AUR są utrzymywane przez społeczność. nie ma oficjalnego wsparcia.</span><span class="sxs-lookup"><span data-stu-id="dae25-204">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="dae25-205">Aby uzyskać więcej informacji na temat instalowania pakietów z programu AUR, zobacz witrynę [typu wiki systemu Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) lub społeczność [pliku dockerfile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="dae25-205">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Łuk z systemem Linux]: https://www.archlinux.org/download/
[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="dae25-207">Pakiet przyciągania</span><span class="sxs-lookup"><span data-stu-id="dae25-207">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="dae25-208">Pobieranie przyciągania</span><span class="sxs-lookup"><span data-stu-id="dae25-208">Getting snapd</span></span>

<span data-ttu-id="dae25-209">`snapd`jest wymagany do uruchomienia przyciągania.</span><span class="sxs-lookup"><span data-stu-id="dae25-209">`snapd` is required to run snaps.</span></span> <span data-ttu-id="dae25-210">Skorzystaj z [tych instrukcji](https://docs.snapcraft.io/core/install) , aby upewnić `snapd` się, że zainstalowano program.</span><span class="sxs-lookup"><span data-stu-id="dae25-210">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="dae25-211">Instalacja za pomocą przystawki</span><span class="sxs-lookup"><span data-stu-id="dae25-211">Installation via Snap</span></span>

<span data-ttu-id="dae25-212">Program PowerShell Core dla systemu Linux jest publikowany w [magazynie Snap](https://snapcraft.io/store) w celu ułatwienia instalacji i aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="dae25-212">PowerShell Core for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="dae25-213">Preferowana metoda jest następująca:</span><span class="sxs-lookup"><span data-stu-id="dae25-213">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="dae25-214">Aby zainstalować wersję zapoznawczą, należy użyć następującej metody:</span><span class="sxs-lookup"><span data-stu-id="dae25-214">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="dae25-215">Po zakończeniu instalacji przyciąganie zostanie automatycznie uaktualnione.</span><span class="sxs-lookup"><span data-stu-id="dae25-215">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="dae25-216">Możesz wyzwolić uaktualnienie przy użyciu `sudo snap refresh powershell` lub `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="dae25-216">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="dae25-217">Dezinstalacji</span><span class="sxs-lookup"><span data-stu-id="dae25-217">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="dae25-218">lub</span><span class="sxs-lookup"><span data-stu-id="dae25-218">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="dae25-219">Kali</span><span class="sxs-lookup"><span data-stu-id="dae25-219">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="dae25-220">Instalacja — Kali</span><span class="sxs-lookup"><span data-stu-id="dae25-220">Installation - Kali</span></span>

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

### <a name="uninstallation---kali"></a><span data-ttu-id="dae25-221">Dezinstalacja — Kali</span><span class="sxs-lookup"><span data-stu-id="dae25-221">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="dae25-222">Raspbian</span><span class="sxs-lookup"><span data-stu-id="dae25-222">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="dae25-223">Obsługa raspbian jest eksperymentalna.</span><span class="sxs-lookup"><span data-stu-id="dae25-223">Raspbian support is experimental.</span></span>

<span data-ttu-id="dae25-224">Obecnie program PowerShell jest obsługiwany tylko w rozciągnięciu raspbian.</span><span class="sxs-lookup"><span data-stu-id="dae25-224">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="dae25-225">CoreCLR i PowerShell Core działają tylko na urządzeniach z procesorami pi 2 i pi 3 jako innych urządzeń, takich jak [pi zero](https://github.com/dotnet/coreclr/issues/10605), ale mają nieobsługiwany procesor.</span><span class="sxs-lookup"><span data-stu-id="dae25-225">CoreCLR and PowerShell Core will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="dae25-226">Pobierz [rozciąganie raspbian](https://www.raspberrypi.org/downloads/raspbian/) i postępuj zgodnie z [instrukcjami instalacji](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) , aby uzyskać je do liczby pi.</span><span class="sxs-lookup"><span data-stu-id="dae25-226">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="dae25-227">Instalacja — raspbian</span><span class="sxs-lookup"><span data-stu-id="dae25-227">Installation - Raspbian</span></span>

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

<span data-ttu-id="dae25-228">Opcjonalnie można utworzyć link symboliczny, aby uruchomić program PowerShell bez określania ścieżki do `pwsh` pliku binarnego.</span><span class="sxs-lookup"><span data-stu-id="dae25-228">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="dae25-229">Dezinstalacja — raspbian</span><span class="sxs-lookup"><span data-stu-id="dae25-229">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="dae25-230">Archiwa binarne</span><span class="sxs-lookup"><span data-stu-id="dae25-230">Binary Archives</span></span>

<span data-ttu-id="dae25-231">Archiwa `tar.gz` binarne programu PowerShell są udostępniane dla platform systemu Linux w celu włączenia zaawansowanych scenariuszy wdrażania.</span><span class="sxs-lookup"><span data-stu-id="dae25-231">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="dae25-232">Zależności</span><span class="sxs-lookup"><span data-stu-id="dae25-232">Dependencies</span></span>

<span data-ttu-id="dae25-233">Program PowerShell kompiluje przenośne pliki binarne dla wszystkich dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="dae25-233">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="dae25-234">Jednak środowisko uruchomieniowe programu .NET Core wymaga różnych zależności od różnych dystrybucji, a program PowerShell jest zbyt mało.</span><span class="sxs-lookup"><span data-stu-id="dae25-234">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="dae25-235">Na poniższym wykresie przedstawiono zależności programu .NET Core 2,0, które są oficjalnie obsługiwane przez różne dystrybucje systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="dae25-235">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="dae25-236">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="dae25-236">OS</span></span>                 | <span data-ttu-id="dae25-237">Zależności</span><span class="sxs-lookup"><span data-stu-id="dae25-237">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="dae25-238">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="dae25-238">Ubuntu 16.04</span></span>       | <span data-ttu-id="dae25-239">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="dae25-239">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="dae25-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="dae25-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="dae25-241">Ubuntu 17,10</span><span class="sxs-lookup"><span data-stu-id="dae25-241">Ubuntu 17.10</span></span>       | <span data-ttu-id="dae25-242">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="dae25-242">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="dae25-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="dae25-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="dae25-244">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="dae25-244">Ubuntu 18.04</span></span>       | <span data-ttu-id="dae25-245">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="dae25-245">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="dae25-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="dae25-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="dae25-247">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="dae25-247">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="dae25-248">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="dae25-248">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="dae25-249">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="dae25-249">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="dae25-250">Debian 9 (Rozciągnij)</span><span class="sxs-lookup"><span data-stu-id="dae25-250">Debian 9 (Stretch)</span></span> | <span data-ttu-id="dae25-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="dae25-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="dae25-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="dae25-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="dae25-253">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="dae25-253">CentOS 7</span></span> <br> <span data-ttu-id="dae25-254">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="dae25-254">Oracle Linux 7</span></span> <br> <span data-ttu-id="dae25-255">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="dae25-255">RHEL 7</span></span> | <span data-ttu-id="dae25-256">libunwind, libcurl, OpenSSL-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="dae25-256">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="dae25-257">openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="dae25-257">openSUSE 42.3</span></span> | <span data-ttu-id="dae25-258">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="dae25-258">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="dae25-259">openSUSE przestępny 15</span><span class="sxs-lookup"><span data-stu-id="dae25-259">openSUSE Leap 15</span></span> | <span data-ttu-id="dae25-260">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="dae25-260">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="dae25-261">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="dae25-261">Fedora 27</span></span> <br> <span data-ttu-id="dae25-262">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="dae25-262">Fedora 28</span></span> | <span data-ttu-id="dae25-263">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="dae25-263">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="dae25-264">W celu wdrożenia plików binarnych programu PowerShell na dystrybucji systemu Linux, które nie są oficjalnie obsługiwane, należy zainstalować wymagane zależności w docelowym systemie operacyjnym w oddzielnych krokach.</span><span class="sxs-lookup"><span data-stu-id="dae25-264">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="dae25-265">Na przykład nasza firma [Amazon Linux pliku dockerfile][amazon-dockerfile] najpierw instaluje zależności, a następnie wyodrębnia archiwum systemu `tar.gz` Linux.</span><span class="sxs-lookup"><span data-stu-id="dae25-265">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="dae25-266">Instalacja — archiwa binarne</span><span class="sxs-lookup"><span data-stu-id="dae25-266">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="dae25-267">Linux</span><span class="sxs-lookup"><span data-stu-id="dae25-267">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="dae25-268">Odinstalowywanie archiwów binarnych</span><span class="sxs-lookup"><span data-stu-id="dae25-268">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="dae25-269">Ścieżki</span><span class="sxs-lookup"><span data-stu-id="dae25-269">Paths</span></span>

* <span data-ttu-id="dae25-270">`$PSHOME`była`/opt/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="dae25-270">`$PSHOME` is `/opt/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="dae25-271">Zostaną odczytane profile użytkowników`~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="dae25-271">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="dae25-272">Domyślne profile zostaną odczytane`$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="dae25-272">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="dae25-273">Moduły użytkownika zostaną odczytane`~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="dae25-273">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="dae25-274">Zostaną odczytane moduły udostępnione`/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="dae25-274">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="dae25-275">Domyślne moduły zostaną odczytane`$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="dae25-275">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="dae25-276">Historia PSReadline zostanie zarejestrowana w`~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="dae25-276">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="dae25-277">Profile respektują konfigurację dla każdego hosta programu PowerShell, dlatego w tych samych lokalizacjach istnieją `Microsoft.PowerShell_profile.ps1` domyślne profile specyficzne dla hosta.</span><span class="sxs-lookup"><span data-stu-id="dae25-277">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="dae25-278">Program PowerShell przestrzega [specyfikacji xdg Base Directory][xdg-bds] w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="dae25-278">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[wydań]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
