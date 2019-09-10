---
title: Instalowanie programu PowerShell Core w systemie Linux
description: Informacje na temat instalowania programu PowerShell Core w różnych dystrybucjach systemu Linux
ms.date: 07/19/2019
ms.openlocfilehash: 7d7c9a9f915f0a6e735a7baec1ec56e9c205a155
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848184"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="bda01-103">Instalowanie programu PowerShell Core w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="bda01-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="bda01-104">Obsługuje [Ubuntu 16,04][u16], [Ubuntu 18,04][u1804], [Ubuntu 18,10][u1810], [Ubuntu 19,04][u1904], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42,3][opensuse], [openSUSE przestępny 15][opensuse], [Fedora 27 ][fedora], [Fedora 28][fedora]i [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="bda01-104">Supports [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Ubuntu 19.04][u1904], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="bda01-105">W przypadku dystrybucji systemu Linux, które nie są oficjalnie obsługiwane, można spróbować zainstalować program PowerShell przy użyciu [pakietu przyciągania programu PowerShell][snap].</span><span class="sxs-lookup"><span data-stu-id="bda01-105">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="bda01-106">Możesz również spróbować wdrożyć pliki binarne programu PowerShell bezpośrednio przy użyciu [ `tar.gz` archiwum][tar]systemu Linux, ale konieczne jest skonfigurowanie wymaganych zależności w oparciu o system operacyjny w osobnych krokach.</span><span class="sxs-lookup"><span data-stu-id="bda01-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="bda01-107">Wszystkie pakiety są dostępne na naszej stronie [wydań][] usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="bda01-107">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="bda01-108">Po zainstalowaniu pakietu Uruchom `pwsh` polecenie z terminalu.</span><span class="sxs-lookup"><span data-stu-id="bda01-108">After the package is installed, run `pwsh` from a terminal.</span></span>

[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[u1904]: #ubuntu-1904
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="bda01-109">Instalowanie wersji zapoznawczej</span><span class="sxs-lookup"><span data-stu-id="bda01-109">Installing Preview Releases</span></span>

<span data-ttu-id="bda01-110">W przypadku instalowania programu PowerShell Core w wersji zapoznawczej dla systemu Linux za pośrednictwem repozytorium pakietów `powershell` nazwa `powershell-preview`pakietu zmieni się z na.</span><span class="sxs-lookup"><span data-stu-id="bda01-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="bda01-111">Instalowanie za pomocą bezpośredniego pobierania nie zmienia się, a nie z nazwą pliku.</span><span class="sxs-lookup"><span data-stu-id="bda01-111">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="bda01-112">Poniższa tabela zawiera polecenia służące do instalowania stabilnych i wersji zapoznawczych pakietów przy użyciu różnych menedżerów pakietów:</span><span class="sxs-lookup"><span data-stu-id="bda01-112">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="bda01-113">Dystrybucje</span><span class="sxs-lookup"><span data-stu-id="bda01-113">Distribution(s)</span></span>|<span data-ttu-id="bda01-114">Stabilne polecenie</span><span class="sxs-lookup"><span data-stu-id="bda01-114">Stable Command</span></span> | <span data-ttu-id="bda01-115">Podgląd — polecenie</span><span class="sxs-lookup"><span data-stu-id="bda01-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="bda01-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="bda01-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="bda01-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="bda01-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="bda01-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="bda01-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1604"></a><span data-ttu-id="bda01-119">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="bda01-119">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="bda01-120">Instalacja za pośrednictwem repozytorium pakietów — Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="bda01-120">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="bda01-121">Program PowerShell Core dla systemu Linux jest publikowany w repozytoriach pakietów w celu ułatwienia instalacji i aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="bda01-121">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="bda01-122">Preferowana metoda jest następująca:</span><span class="sxs-lookup"><span data-stu-id="bda01-122">The preferred method is as follows:</span></span>

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

<span data-ttu-id="bda01-123">Jako administratora Zarejestruj repozytorium Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bda01-123">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="bda01-124">Po zarejestrowaniu można zaktualizować program PowerShell `sudo apt-get upgrade powershell`za pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="bda01-124">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="bda01-125">Instalacja za pośrednictwem bezpośredniego pobierania — Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="bda01-125">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="bda01-126">Pobierz pakiet `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` Debian ze strony [wydań][] na maszynę Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="bda01-126">Download the Debian package `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="bda01-127">Następnie w terminalu wykonaj następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="bda01-127">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="bda01-128">`dpkg -i` Polecenie kończy się niepowodzeniem z zależnościami niewypełnienia.</span><span class="sxs-lookup"><span data-stu-id="bda01-128">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="bda01-129">Następne polecenie, rozwiązuje `apt-get install -f` te problemy, a następnie kończy konfigurowanie pakietu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bda01-129">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="bda01-130">Dezinstalacja — Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="bda01-130">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="bda01-131">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="bda01-131">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="bda01-132">Instalacja za pośrednictwem repozytorium pakietów — Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="bda01-132">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="bda01-133">Program PowerShell Core dla systemu Linux jest publikowany w repozytoriach pakietów w celu ułatwienia instalacji i aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="bda01-133">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="bda01-134">Preferowana metoda jest następująca:</span><span class="sxs-lookup"><span data-stu-id="bda01-134">The preferred method is as follows:</span></span>

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

<span data-ttu-id="bda01-135">Jako administratora Zarejestruj repozytorium Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bda01-135">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="bda01-136">Po zarejestrowaniu można zaktualizować program PowerShell `sudo apt-get upgrade powershell`za pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="bda01-136">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="bda01-137">Instalacja za pośrednictwem bezpośredniego pobierania — Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="bda01-137">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="bda01-138">Pobierz pakiet `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` Debian ze strony [wydań][] na maszynę Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="bda01-138">Download the Debian package `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="bda01-139">Następnie w terminalu wykonaj następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="bda01-139">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="bda01-140">`dpkg -i` Polecenie kończy się niepowodzeniem z zależnościami niewypełnienia.</span><span class="sxs-lookup"><span data-stu-id="bda01-140">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="bda01-141">Następne polecenie, rozwiązuje `apt-get install -f` te problemy, a następnie kończy konfigurowanie pakietu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bda01-141">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="bda01-142">Dezinstalacja — Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="bda01-142">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="bda01-143">Ubuntu 18,10</span><span class="sxs-lookup"><span data-stu-id="bda01-143">Ubuntu 18.10</span></span>

<span data-ttu-id="bda01-144">Instalacja jest obsługiwana za `snapd`pośrednictwem.</span><span class="sxs-lookup"><span data-stu-id="bda01-144">Installation is supported via `snapd`.</span></span> <span data-ttu-id="bda01-145">Aby uzyskać instrukcje, zobacz [przyciąganie pakietu][snap].</span><span class="sxs-lookup"><span data-stu-id="bda01-145">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="bda01-146">Ubuntu 18,10 to [wersja przejściowa](https://www.ubuntu.com/about/release-cycle) obsługiwana przez [społeczność](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="bda01-146">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1904"></a><span data-ttu-id="bda01-147">Ubuntu 19,04</span><span class="sxs-lookup"><span data-stu-id="bda01-147">Ubuntu 19.04</span></span>

<span data-ttu-id="bda01-148">Instalacja jest obsługiwana za `snapd`pośrednictwem.</span><span class="sxs-lookup"><span data-stu-id="bda01-148">Installation is supported via `snapd`.</span></span> <span data-ttu-id="bda01-149">Aby uzyskać instrukcje, zobacz [przyciąganie pakietu][snap].</span><span class="sxs-lookup"><span data-stu-id="bda01-149">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="bda01-150">Ubuntu 19,04 to [wersja przejściowa](https://www.ubuntu.com/about/release-cycle) obsługiwana przez [społeczność](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="bda01-150">Ubuntu 19.04 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="debian-8"></a><span data-ttu-id="bda01-151">Debian 8</span><span class="sxs-lookup"><span data-stu-id="bda01-151">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="bda01-152">Instalacja za pośrednictwem repozytorium pakietów — Debian 8</span><span class="sxs-lookup"><span data-stu-id="bda01-152">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="bda01-153">Program PowerShell Core dla systemu Linux jest publikowany w repozytoriach pakietów w celu ułatwienia instalacji i aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="bda01-153">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="bda01-154">Preferowana metoda jest następująca:</span><span class="sxs-lookup"><span data-stu-id="bda01-154">The preferred method is as follows:</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install -y curl apt-transport-https

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

<span data-ttu-id="bda01-155">Jako administratora Zarejestruj repozytorium Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bda01-155">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="bda01-156">Po zarejestrowaniu można zaktualizować program PowerShell `sudo apt-get upgrade powershell`za pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="bda01-156">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="bda01-157">Debian 9</span><span class="sxs-lookup"><span data-stu-id="bda01-157">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="bda01-158">Instalacja za pośrednictwem repozytorium pakietów — Debian 9</span><span class="sxs-lookup"><span data-stu-id="bda01-158">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="bda01-159">Program PowerShell Core dla systemu Linux jest publikowany w repozytoriach pakietów w celu ułatwienia instalacji i aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="bda01-159">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="bda01-160">Preferowana metoda jest następująca:</span><span class="sxs-lookup"><span data-stu-id="bda01-160">The preferred method is as follows:</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install -y curl gnupg apt-transport-https

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

<span data-ttu-id="bda01-161">Jako administratora Zarejestruj repozytorium Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bda01-161">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="bda01-162">Po zarejestrowaniu można zaktualizować program PowerShell `sudo apt-get upgrade powershell`za pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="bda01-162">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="bda01-163">Instalacja za pośrednictwem bezpośredniego pobierania — Debian 9</span><span class="sxs-lookup"><span data-stu-id="bda01-163">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="bda01-164">Pobierz pakiet `powershell_6.2.0-1.debian.9_amd64.deb` Debian ze strony [wydań][] na maszynę debian.</span><span class="sxs-lookup"><span data-stu-id="bda01-164">Download the Debian package `powershell_6.2.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="bda01-165">Następnie w terminalu wykonaj następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="bda01-165">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="bda01-166">Dezinstalacja — Debian 9</span><span class="sxs-lookup"><span data-stu-id="bda01-166">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="bda01-167">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="bda01-167">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="bda01-168">Ten pakiet działa w Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="bda01-168">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="bda01-169">Instalacja za pośrednictwem repozytorium pakietów (preferowany) — CentOS 7</span><span class="sxs-lookup"><span data-stu-id="bda01-169">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="bda01-170">Program PowerShell Core dla systemu Linux jest publikowany w oficjalnych repozytoriach firmy Microsoft w celu ułatwienia instalacji i aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="bda01-170">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="bda01-171">Jako administratora Zarejestruj repozytorium Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bda01-171">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="bda01-172">Po zarejestrowaniu można zaktualizować program PowerShell `sudo yum update powershell`za pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="bda01-172">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="bda01-173">Instalacja za pośrednictwem bezpośredniego pobierania — CentOS 7</span><span class="sxs-lookup"><span data-stu-id="bda01-173">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="bda01-174">Korzystając z programu [CentOS 7][], Pobierz pakiet `powershell-6.2.0-1.rhel.7.x86_64.rpm` RPM ze strony [wydań][] na maszynę CentOS.</span><span class="sxs-lookup"><span data-stu-id="bda01-174">Using [CentOS 7][], download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="bda01-175">Następnie w terminalu wykonaj następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="bda01-175">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="bda01-176">Możesz zainstalować KCO bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="bda01-176">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="bda01-177">Dezinstalacja — CentOS 7</span><span class="sxs-lookup"><span data-stu-id="bda01-177">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="bda01-179">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="bda01-179">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="bda01-180">Instalacja za pośrednictwem repozytorium pakietów (preferowany) — Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="bda01-180">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="bda01-181">Program PowerShell Core dla systemu Linux jest publikowany w oficjalnych repozytoriach firmy Microsoft w celu ułatwienia instalacji i aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="bda01-181">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="bda01-182">Jako administratora Zarejestruj repozytorium Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bda01-182">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="bda01-183">Po zarejestrowaniu można zaktualizować program PowerShell `sudo yum update powershell`za pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="bda01-183">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="bda01-184">Instalacja za pośrednictwem bezpośredniego pobierania — Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="bda01-184">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="bda01-185">Pobierz pakiet `powershell-6.2.0-1.rhel.7.x86_64.rpm` RPM ze strony [wydań][] na maszynę Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="bda01-185">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="bda01-186">Następnie w terminalu wykonaj następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="bda01-186">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="bda01-187">Możesz zainstalować KCO bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="bda01-187">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="bda01-188">Dezinstalacja-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="bda01-188">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="bda01-189">openSUSE</span><span class="sxs-lookup"><span data-stu-id="bda01-189">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="bda01-190">Instalacja — openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="bda01-190">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="bda01-191">Instalacja — openSUSE przestępny 15</span><span class="sxs-lookup"><span data-stu-id="bda01-191">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="bda01-192">Dezinstalacja-openSUSE 42,3, openSUSE przestępny 15</span><span class="sxs-lookup"><span data-stu-id="bda01-192">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="bda01-193">Fedora</span><span class="sxs-lookup"><span data-stu-id="bda01-193">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="bda01-194">Fedora 28 jest obsługiwana tylko w programie PowerShell Core 6,1 i nowszym.</span><span class="sxs-lookup"><span data-stu-id="bda01-194">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="bda01-195">Instalacja za pośrednictwem repozytorium pakietów (preferowany) — Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="bda01-195">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="bda01-196">Program PowerShell Core dla systemu Linux jest publikowany w oficjalnych repozytoriach firmy Microsoft w celu ułatwienia instalacji i aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="bda01-196">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="bda01-197">Instalacja za pośrednictwem bezpośredniego pobierania — Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="bda01-197">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="bda01-198">Pobierz pakiet `powershell-6.2.0-1.rhel.7.x86_64.rpm` RPM ze strony [wydań][] na maszynę Fedora.</span><span class="sxs-lookup"><span data-stu-id="bda01-198">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="bda01-199">Następnie w terminalu wykonaj następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="bda01-199">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="bda01-200">Możesz zainstalować KCO bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="bda01-200">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="bda01-201">Dezinstalacja — Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="bda01-201">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="bda01-202">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="bda01-202">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="bda01-203">Obsługa archów jest eksperymentalna.</span><span class="sxs-lookup"><span data-stu-id="bda01-203">Arch support is experimental.</span></span>

<span data-ttu-id="bda01-204">Program PowerShell jest dostępny w repozytorium użytkowników w systemie [Łuk z systemem Linux][] (AUR).</span><span class="sxs-lookup"><span data-stu-id="bda01-204">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="bda01-205">Można go skompilować z [najnowszą wersją otagowaną][arch-release]</span><span class="sxs-lookup"><span data-stu-id="bda01-205">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="bda01-206">Można go skompilować z [ostatniego zatwierdzenia do głównego][arch-git]</span><span class="sxs-lookup"><span data-stu-id="bda01-206">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="bda01-207">Można go zainstalować przy użyciu [najnowszej wersji pliku binarnego][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="bda01-207">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="bda01-208">Pakiety w AUR są utrzymywane przez społeczność. nie ma oficjalnego wsparcia.</span><span class="sxs-lookup"><span data-stu-id="bda01-208">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="bda01-209">Aby uzyskać więcej informacji na temat instalowania pakietów z programu AUR, zobacz witrynę [typu wiki systemu Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) lub społeczność [pliku dockerfile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="bda01-209">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Łuk z systemem Linux]: https://www.archlinux.org/download/
[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="bda01-211">Pakiet przyciągania</span><span class="sxs-lookup"><span data-stu-id="bda01-211">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="bda01-212">Pobieranie przyciągania</span><span class="sxs-lookup"><span data-stu-id="bda01-212">Getting snapd</span></span>

<span data-ttu-id="bda01-213">`snapd`jest wymagany do uruchomienia przyciągania.</span><span class="sxs-lookup"><span data-stu-id="bda01-213">`snapd` is required to run snaps.</span></span> <span data-ttu-id="bda01-214">Skorzystaj z [tych instrukcji](https://docs.snapcraft.io/core/install) , aby upewnić `snapd` się, że zainstalowano program.</span><span class="sxs-lookup"><span data-stu-id="bda01-214">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="bda01-215">Instalacja za pomocą przystawki</span><span class="sxs-lookup"><span data-stu-id="bda01-215">Installation via Snap</span></span>

<span data-ttu-id="bda01-216">Program PowerShell Core dla systemu Linux jest publikowany w [magazynie Snap](https://snapcraft.io/store) w celu ułatwienia instalacji i aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="bda01-216">PowerShell Core for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="bda01-217">Preferowana metoda jest następująca:</span><span class="sxs-lookup"><span data-stu-id="bda01-217">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="bda01-218">Aby zainstalować wersję zapoznawczą, należy użyć następującej metody:</span><span class="sxs-lookup"><span data-stu-id="bda01-218">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="bda01-219">Po zakończeniu instalacji przyciąganie zostanie automatycznie uaktualnione.</span><span class="sxs-lookup"><span data-stu-id="bda01-219">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="bda01-220">Możesz wyzwolić uaktualnienie przy użyciu `sudo snap refresh powershell` lub `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="bda01-220">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="bda01-221">Dezinstalacji</span><span class="sxs-lookup"><span data-stu-id="bda01-221">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="bda01-222">lub</span><span class="sxs-lookup"><span data-stu-id="bda01-222">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="bda01-223">Kali</span><span class="sxs-lookup"><span data-stu-id="bda01-223">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="bda01-224">Instalacja — Kali</span><span class="sxs-lookup"><span data-stu-id="bda01-224">Installation - Kali</span></span>

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

### <a name="uninstallation---kali"></a><span data-ttu-id="bda01-225">Dezinstalacja — Kali</span><span class="sxs-lookup"><span data-stu-id="bda01-225">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="bda01-226">Raspbian</span><span class="sxs-lookup"><span data-stu-id="bda01-226">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="bda01-227">Obsługa raspbian jest eksperymentalna.</span><span class="sxs-lookup"><span data-stu-id="bda01-227">Raspbian support is experimental.</span></span>

<span data-ttu-id="bda01-228">Obecnie program PowerShell jest obsługiwany tylko w rozciągnięciu raspbian.</span><span class="sxs-lookup"><span data-stu-id="bda01-228">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="bda01-229">CoreCLR i PowerShell Core działają tylko na urządzeniach z procesorami pi 2 i pi 3 jako innych urządzeń, takich jak [pi zero](https://github.com/dotnet/coreclr/issues/10605), ale mają nieobsługiwany procesor.</span><span class="sxs-lookup"><span data-stu-id="bda01-229">CoreCLR and PowerShell Core will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="bda01-230">Pobierz [rozciąganie raspbian](https://www.raspberrypi.org/downloads/raspbian/) i postępuj zgodnie z [instrukcjami instalacji](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) , aby uzyskać je do liczby pi.</span><span class="sxs-lookup"><span data-stu-id="bda01-230">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="bda01-231">Instalacja — raspbian</span><span class="sxs-lookup"><span data-stu-id="bda01-231">Installation - Raspbian</span></span>

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

<span data-ttu-id="bda01-232">Opcjonalnie można utworzyć link symboliczny, aby uruchomić program PowerShell bez określania ścieżki do `pwsh` pliku binarnego.</span><span class="sxs-lookup"><span data-stu-id="bda01-232">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="bda01-233">Dezinstalacja — raspbian</span><span class="sxs-lookup"><span data-stu-id="bda01-233">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="bda01-234">Archiwa binarne</span><span class="sxs-lookup"><span data-stu-id="bda01-234">Binary Archives</span></span>

<span data-ttu-id="bda01-235">Archiwa `tar.gz` binarne programu PowerShell są udostępniane dla platform systemu Linux w celu włączenia zaawansowanych scenariuszy wdrażania.</span><span class="sxs-lookup"><span data-stu-id="bda01-235">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="bda01-236">Zależności</span><span class="sxs-lookup"><span data-stu-id="bda01-236">Dependencies</span></span>

<span data-ttu-id="bda01-237">Program PowerShell kompiluje przenośne pliki binarne dla wszystkich dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="bda01-237">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="bda01-238">Jednak środowisko uruchomieniowe programu .NET Core wymaga różnych zależności od różnych dystrybucji, a program PowerShell jest zbyt mało.</span><span class="sxs-lookup"><span data-stu-id="bda01-238">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="bda01-239">Na poniższym wykresie przedstawiono zależności programu .NET Core 2,0, które są oficjalnie obsługiwane przez różne dystrybucje systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="bda01-239">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="bda01-240">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="bda01-240">OS</span></span>                 | <span data-ttu-id="bda01-241">Zależności</span><span class="sxs-lookup"><span data-stu-id="bda01-241">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="bda01-242">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="bda01-242">Ubuntu 16.04</span></span>       | <span data-ttu-id="bda01-243">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="bda01-243">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="bda01-244">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="bda01-244">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="bda01-245">Ubuntu 17,10</span><span class="sxs-lookup"><span data-stu-id="bda01-245">Ubuntu 17.10</span></span>       | <span data-ttu-id="bda01-246">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="bda01-246">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="bda01-247">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="bda01-247">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="bda01-248">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="bda01-248">Ubuntu 18.04</span></span>       | <span data-ttu-id="bda01-249">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="bda01-249">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="bda01-250">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="bda01-250">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="bda01-251">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="bda01-251">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="bda01-252">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="bda01-252">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="bda01-253">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="bda01-253">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="bda01-254">Debian 9 (Rozciągnij)</span><span class="sxs-lookup"><span data-stu-id="bda01-254">Debian 9 (Stretch)</span></span> | <span data-ttu-id="bda01-255">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="bda01-255">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="bda01-256">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="bda01-256">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="bda01-257">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="bda01-257">CentOS 7</span></span> <br> <span data-ttu-id="bda01-258">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="bda01-258">Oracle Linux 7</span></span> <br> <span data-ttu-id="bda01-259">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="bda01-259">RHEL 7</span></span> | <span data-ttu-id="bda01-260">libunwind, libcurl, OpenSSL-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="bda01-260">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="bda01-261">openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="bda01-261">openSUSE 42.3</span></span> | <span data-ttu-id="bda01-262">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="bda01-262">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="bda01-263">openSUSE przestępny 15</span><span class="sxs-lookup"><span data-stu-id="bda01-263">openSUSE Leap 15</span></span> | <span data-ttu-id="bda01-264">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="bda01-264">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="bda01-265">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="bda01-265">Fedora 27</span></span> <br> <span data-ttu-id="bda01-266">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="bda01-266">Fedora 28</span></span> | <span data-ttu-id="bda01-267">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="bda01-267">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="bda01-268">W celu wdrożenia plików binarnych programu PowerShell na dystrybucji systemu Linux, które nie są oficjalnie obsługiwane, należy zainstalować wymagane zależności w docelowym systemie operacyjnym w oddzielnych krokach.</span><span class="sxs-lookup"><span data-stu-id="bda01-268">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="bda01-269">Na przykład nasza firma [Amazon Linux pliku dockerfile][amazon-dockerfile] najpierw instaluje zależności, a następnie wyodrębnia archiwum systemu `tar.gz` Linux.</span><span class="sxs-lookup"><span data-stu-id="bda01-269">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="bda01-270">Instalacja — archiwa binarne</span><span class="sxs-lookup"><span data-stu-id="bda01-270">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="bda01-271">Linux</span><span class="sxs-lookup"><span data-stu-id="bda01-271">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="bda01-272">Odinstalowywanie archiwów binarnych</span><span class="sxs-lookup"><span data-stu-id="bda01-272">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="bda01-273">Ścieżki</span><span class="sxs-lookup"><span data-stu-id="bda01-273">Paths</span></span>

* <span data-ttu-id="bda01-274">`$PSHOME`była`/opt/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="bda01-274">`$PSHOME` is `/opt/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="bda01-275">Zostaną odczytane profile użytkowników`~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="bda01-275">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="bda01-276">Domyślne profile zostaną odczytane`$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="bda01-276">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="bda01-277">Moduły użytkownika zostaną odczytane`~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="bda01-277">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="bda01-278">Zostaną odczytane moduły udostępnione`/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="bda01-278">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="bda01-279">Domyślne moduły zostaną odczytane`$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="bda01-279">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="bda01-280">Historia PSReadline zostanie zarejestrowana w`~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="bda01-280">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="bda01-281">Profile respektują konfigurację dla każdego hosta programu PowerShell, dlatego w tych samych lokalizacjach istnieją `Microsoft.PowerShell_profile.ps1` domyślne profile specyficzne dla hosta.</span><span class="sxs-lookup"><span data-stu-id="bda01-281">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="bda01-282">Program PowerShell przestrzega [specyfikacji xdg Base Directory][xdg-bds] w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="bda01-282">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[wydań]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
