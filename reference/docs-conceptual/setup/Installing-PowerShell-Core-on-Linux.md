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
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="7cd0b-103">Instalowanie programu PowerShell Core w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="7cd0b-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="7cd0b-104">Obsługuje [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10] [ u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27 ] [ fedora], [Fedora 28][fedora], i [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="7cd0b-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10][u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="7cd0b-105">Dystrybucje systemu Linux, które nie są oficjalnie obsługiwane, spróbuj użyć [pakiet przyciąganie PowerShell][snap].</span><span class="sxs-lookup"><span data-stu-id="7cd0b-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="7cd0b-106">Możesz też spróbować wdrażania plików binarnych programu PowerShell bezpośrednio przy użyciu systemu Linux [ `tar.gz` archiwum][tar], ale należy skonfigurować niezbędne zależności, w oparciu o system operacyjny w oddzielne kroki.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="7cd0b-107">Wszystkie pakiety są dostępne w usłudze GitHub [zwalnia][] strony.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="7cd0b-108">Po zainstalowaniu pakietu Uruchom `pwsh` z poziomu terminalu.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

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

## <a name="installing-preview-releases"></a><span data-ttu-id="7cd0b-109">Instalowanie wersji zapoznawczych</span><span class="sxs-lookup"><span data-stu-id="7cd0b-109">Installing Preview Releases</span></span>

<span data-ttu-id="7cd0b-110">Podczas instalowania wersji programu PowerShell Core w wersji zapoznawczej dla systemu Linux przy użyciu repozytorium pakietów, nazwy pakietu zmieni się z `powershell` do `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="7cd0b-111">Instalowanie przy użyciu bezpośredniego pobierania nie ulega zmianie, inna niż nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="7cd0b-112">W tym miejscu znajduje się tabela polecenia, aby zainstalować pakiety w wersji zapoznawczej i stabilny, przy użyciu różnych menedżerów pakietów:</span><span class="sxs-lookup"><span data-stu-id="7cd0b-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="7cd0b-113">Distribution(s)</span><span class="sxs-lookup"><span data-stu-id="7cd0b-113">Distribution(s)</span></span>|<span data-ttu-id="7cd0b-114">Polecenie stabilne</span><span class="sxs-lookup"><span data-stu-id="7cd0b-114">Stable Command</span></span> | <span data-ttu-id="7cd0b-115">Polecenia w wersji zapoznawczej</span><span class="sxs-lookup"><span data-stu-id="7cd0b-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="7cd0b-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="7cd0b-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="7cd0b-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="7cd0b-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="7cd0b-118">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="7cd0b-118">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="7cd0b-119">Fedora</span><span class="sxs-lookup"><span data-stu-id="7cd0b-119">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="7cd0b-120">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="7cd0b-120">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="7cd0b-121">Instalację przy użyciu repozytorium pakietów — Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="7cd0b-121">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="7cd0b-122">Program PowerShell Core dla systemu Linux jest publikowany repozytoriów pakietów do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="7cd0b-122">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="7cd0b-123">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-123">This is the preferred method.</span></span>

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

<span data-ttu-id="7cd0b-124">Jako administratora należy zarejestrować się w repozytorium firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-124">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="7cd0b-125">Od tego momentu, po prostu musisz użyć `sudo apt-get upgrade powershell` do aktualizacji instalacji.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-125">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="7cd0b-126">Instalację za pomocą bezpośredniego pobierania — Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="7cd0b-126">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="7cd0b-127">Pobierz pakiet Debian `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="7cd0b-127">Download the Debian package `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span></span>
<span data-ttu-id="7cd0b-128">z [zwalnia][] strony na komputerze Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-128">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="7cd0b-129">Następnie wykonaj następujące czynności w terminalu:</span><span class="sxs-lookup"><span data-stu-id="7cd0b-129">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="7cd0b-130">`dpkg -i` Polecenia nie powiodło się niewypełnienia zależności.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-130">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="7cd0b-131">Następne polecenie `apt-get install -f` rozwiązuje te problemy, a następnie kończy Konfigurowanie pakietami programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-131">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="7cd0b-132">Dezinstalacja — Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="7cd0b-132">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="7cd0b-133">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="7cd0b-133">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="7cd0b-134">Instalację przy użyciu repozytorium pakietów — Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="7cd0b-134">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="7cd0b-135">Program PowerShell Core dla systemu Linux jest publikowany repozytoriów pakietów do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="7cd0b-135">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="7cd0b-136">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-136">This is the preferred method.</span></span>

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

<span data-ttu-id="7cd0b-137">Po zarejestrowaniu programu Microsoft repository raz jako administratora, od tego momentu, po prostu musisz użyć `sudo apt-get upgrade powershell` ją zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-137">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="7cd0b-138">Instalację za pomocą bezpośredniego pobierania — Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="7cd0b-138">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="7cd0b-139">Pobierz pakiet Debian `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="7cd0b-139">Download the Debian package `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span></span>
<span data-ttu-id="7cd0b-140">z [zwalnia][] strony na komputerze Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-140">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="7cd0b-141">Następnie wykonaj następujące czynności w terminalu:</span><span class="sxs-lookup"><span data-stu-id="7cd0b-141">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="7cd0b-142">`dpkg -i` Polecenia nie powiodło się niewypełnienia zależności.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-142">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="7cd0b-143">Następne polecenie `apt-get install -f` rozwiązuje te problemy, a następnie kończy Konfigurowanie pakietami programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-143">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="7cd0b-144">Dezinstalacja — Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="7cd0b-144">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="7cd0b-145">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="7cd0b-145">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="7cd0b-146">Dodano obsługę systemu Ubuntu 18.04 po `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="7cd0b-146">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="7cd0b-147">Instalację przy użyciu repozytorium pakietów — Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="7cd0b-147">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="7cd0b-148">Program PowerShell Core dla systemu Linux jest publikowany repozytoriów pakietów do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="7cd0b-148">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="7cd0b-149">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-149">This is the preferred method.</span></span>

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

<span data-ttu-id="7cd0b-150">Po zarejestrowaniu programu Microsoft repository raz jako administratora, od tego momentu, po prostu musisz użyć `sudo apt-get upgrade powershell` ją zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-150">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="7cd0b-151">Instalację za pomocą bezpośredniego pobierania — Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="7cd0b-151">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="7cd0b-152">Pobierz pakiet Debian `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="7cd0b-152">Download the Debian package `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span></span>
<span data-ttu-id="7cd0b-153">z [zwalnia][] strony na komputerze Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-153">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="7cd0b-154">Następnie wykonaj następujące czynności w terminalu:</span><span class="sxs-lookup"><span data-stu-id="7cd0b-154">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="7cd0b-155">`dpkg -i` Polecenia nie powiodło się niewypełnienia zależności.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-155">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="7cd0b-156">Następne polecenie `apt-get install -f` rozwiązuje te problemy, a następnie kończy Konfigurowanie pakietami programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-156">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="7cd0b-157">Dezinstalacja — Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="7cd0b-157">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="7cd0b-158">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="7cd0b-158">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="7cd0b-159">Dodano obsługę systemu Ubuntu 18.10 po `6.1.0-preview.3`.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-159">Support for Ubuntu 18.10 was added after `6.1.0-preview.3`.</span></span>
> <span data-ttu-id="7cd0b-160">Podobnie jak 18.10 dzienną kompilacją, jest tylko społeczności obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-160">As 18.10 is a daily build, it is only community supported.</span></span>

<span data-ttu-id="7cd0b-161">Instalowanie na 18.10 jest świadczona za pośrednictwem `snapd`.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-161">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="7cd0b-162">Zobacz [przyciąganie pakietu] [ snap] pełne instrukcje;</span><span class="sxs-lookup"><span data-stu-id="7cd0b-162">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="7cd0b-163">Debian 8</span><span class="sxs-lookup"><span data-stu-id="7cd0b-163">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="7cd0b-164">Instalację przy użyciu repozytorium pakietów — Debian 8</span><span class="sxs-lookup"><span data-stu-id="7cd0b-164">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="7cd0b-165">Program PowerShell Core dla systemu Linux jest publikowany repozytoriów pakietów do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="7cd0b-165">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="7cd0b-166">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-166">This is the preferred method.</span></span>

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

<span data-ttu-id="7cd0b-167">Po zarejestrowaniu programu Microsoft repository raz jako administratora, od tego momentu, po prostu musisz użyć `sudo apt-get upgrade powershell` ją zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-167">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="7cd0b-168">Instalację za pomocą bezpośredniego pobierania — Debian 8</span><span class="sxs-lookup"><span data-stu-id="7cd0b-168">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="7cd0b-169">Pobierz pakiet Debian `powershell_6.1.0-1.debian.8_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="7cd0b-169">Download the Debian package `powershell_6.1.0-1.debian.8_amd64.deb`</span></span>
<span data-ttu-id="7cd0b-170">z [zwalnia][] strony na komputerze Debian.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-170">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="7cd0b-171">Następnie wykonaj następujące czynności w terminalu:</span><span class="sxs-lookup"><span data-stu-id="7cd0b-171">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="7cd0b-172">`dpkg -i` Polecenia nie powiodło się niewypełnienia zależności.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-172">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="7cd0b-173">Następne polecenie `apt-get install -f` rozwiązuje te problemy, a następnie kończy Konfigurowanie pakietami programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-173">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="7cd0b-174">Dezinstalacja — Debian 8</span><span class="sxs-lookup"><span data-stu-id="7cd0b-174">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="7cd0b-175">Debian 9</span><span class="sxs-lookup"><span data-stu-id="7cd0b-175">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="7cd0b-176">Instalację przy użyciu repozytorium pakietów - Debian 9</span><span class="sxs-lookup"><span data-stu-id="7cd0b-176">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="7cd0b-177">Program PowerShell Core dla systemu Linux jest publikowany repozytoriów pakietów do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="7cd0b-177">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="7cd0b-178">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-178">This is the preferred method.</span></span>

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

<span data-ttu-id="7cd0b-179">Po zarejestrowaniu programu Microsoft repository raz jako administratora, od tego momentu, po prostu musisz użyć `sudo apt-get upgrade powershell` ją zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-179">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="7cd0b-180">Instalację za pomocą bezpośredniego pobierania - Debian 9</span><span class="sxs-lookup"><span data-stu-id="7cd0b-180">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="7cd0b-181">Pobierz pakiet Debian `powershell_6.1.0-1.debian.9_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="7cd0b-181">Download the Debian package `powershell_6.1.0-1.debian.9_amd64.deb`</span></span>
<span data-ttu-id="7cd0b-182">z [zwalnia][] strony na komputerze Debian.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-182">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="7cd0b-183">Następnie wykonaj następujące czynności w terminalu:</span><span class="sxs-lookup"><span data-stu-id="7cd0b-183">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="7cd0b-184">Dezinstalacja — Debian 9</span><span class="sxs-lookup"><span data-stu-id="7cd0b-184">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="7cd0b-185">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7cd0b-185">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="7cd0b-186">Ten pakiet działa także w systemie Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-186">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="7cd0b-187">Instalację przy użyciu repozytorium pakietów (preferowany) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7cd0b-187">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="7cd0b-188">Program PowerShell Core dla systemu Linux jest publikowany oficjalnych repozytoriów firmy Microsoft do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="7cd0b-188">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="7cd0b-189">Po zarejestrowaniu programu Microsoft repository raz jako administratora, po prostu musisz użyć `sudo yum update powershell` do zaktualizowania programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-189">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="7cd0b-190">Instalację za pomocą bezpośredniego pobierania - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7cd0b-190">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="7cd0b-191">Za pomocą [CentOS 7][], Pobierz pakiet obr. / min `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="7cd0b-191">Using [CentOS 7][], download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="7cd0b-192">z [zwalnia][] strony na komputerze CentOS.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-192">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="7cd0b-193">Następnie wykonaj następujące czynności w terminalu:</span><span class="sxs-lookup"><span data-stu-id="7cd0b-193">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="7cd0b-194">Można także zainstalować obr. / min bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="7cd0b-194">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="7cd0b-195">Dezinstalacja - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7cd0b-195">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="7cd0b-197">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="7cd0b-197">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="7cd0b-198">Instalację przy użyciu repozytorium pakietów (preferowany) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="7cd0b-198">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="7cd0b-199">Program PowerShell Core dla systemu Linux jest publikowany oficjalnych repozytoriów firmy Microsoft do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="7cd0b-199">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="7cd0b-200">Po zarejestrowaniu programu Microsoft repository raz jako administratora, po prostu musisz użyć `sudo yum update powershell` do zaktualizowania programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-200">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="7cd0b-201">Instalację za pomocą bezpośredniego pobierania - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="7cd0b-201">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="7cd0b-202">Pobierz pakiet obr. / min `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="7cd0b-202">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="7cd0b-203">z [zwalnia][] strony na komputerze Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-203">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="7cd0b-204">Następnie wykonaj następujące czynności w terminalu:</span><span class="sxs-lookup"><span data-stu-id="7cd0b-204">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="7cd0b-205">Można także zainstalować obr. / min bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="7cd0b-205">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="7cd0b-206">Dezinstalacja - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="7cd0b-206">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-423"></a><span data-ttu-id="7cd0b-207">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="7cd0b-207">OpenSUSE 42.3</span></span>

<span data-ttu-id="7cd0b-208">Podczas instalowania programu PowerShell Core `zypper` może Zgłoś następujący błąd:</span><span class="sxs-lookup"><span data-stu-id="7cd0b-208">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.1.0-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.1.0-1.rhel.7.x86_64
 Solution 2: break powershell-6.1.0-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="7cd0b-209">W takim przypadku upewnij się, że zgodne `libcurl` biblioteka jest obecny, sprawdzając, czy następujące polecenie pokazuje `libcurl4` pakietu jako zainstalowane:</span><span class="sxs-lookup"><span data-stu-id="7cd0b-209">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="7cd0b-210">Następnie wybierz `break powershell-6.1.0-1.rhel.7.x86_64 by ignoring some of its dependencies` rozwiązania podczas instalowania pakietu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-210">Then choose the `break powershell-6.1.0-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-423"></a><span data-ttu-id="7cd0b-211">Instalację przy użyciu repozytorium pakietów (preferowany) - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="7cd0b-211">Installation via Package Repository (preferred) - OpenSUSE 42.3</span></span>

<span data-ttu-id="7cd0b-212">Program PowerShell Core dla systemu Linux jest publikowany oficjalnych repozytoriów firmy Microsoft do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="7cd0b-212">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-423"></a><span data-ttu-id="7cd0b-213">Instalację za pomocą bezpośredniego pobierania - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="7cd0b-213">Installation via Direct Download - OpenSUSE 42.3</span></span>

<span data-ttu-id="7cd0b-214">Pobierz pakiet RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm` z [zwalnia][] strony na komputerze OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-214">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="7cd0b-215">Można także zainstalować obr. / min bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="7cd0b-215">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-423"></a><span data-ttu-id="7cd0b-216">Dezinstalacja - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="7cd0b-216">Uninstallation - OpenSUSE 42.3</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="7cd0b-217">Fedora</span><span class="sxs-lookup"><span data-stu-id="7cd0b-217">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="7cd0b-218">Fedora 28 jest obsługiwane tylko w sytuacji, w programie PowerShell Core 6.1 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-218">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="7cd0b-219">Instalację przy użyciu repozytorium pakietów (preferowany) - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="7cd0b-219">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="7cd0b-220">Program PowerShell Core dla systemu Linux jest publikowany oficjalnych repozytoriów firmy Microsoft do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="7cd0b-220">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="7cd0b-221">Instalację za pomocą bezpośredniego pobierania - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="7cd0b-221">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="7cd0b-222">Pobierz pakiet obr. / min `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="7cd0b-222">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="7cd0b-223">z [zwalnia][] strony na komputerze Fedora.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-223">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="7cd0b-224">Następnie wykonaj następujące czynności w terminalu:</span><span class="sxs-lookup"><span data-stu-id="7cd0b-224">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="7cd0b-225">Można także zainstalować obr. / min bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="7cd0b-225">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="7cd0b-226">Dezinstalacja - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="7cd0b-226">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="7cd0b-227">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="7cd0b-227">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="7cd0b-228">Obsługa architektury jest eksperymentalne.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-228">Arch support is experimental.</span></span>

<span data-ttu-id="7cd0b-229">Program PowerShell jest dostępny z [Arch systemu Linux][] użytkownika repozytorium (AUR).</span><span class="sxs-lookup"><span data-stu-id="7cd0b-229">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="7cd0b-230">Może być skompilowana przy użyciu [najnowsze tagiem wydania][arch-release]</span><span class="sxs-lookup"><span data-stu-id="7cd0b-230">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="7cd0b-231">Może być kompilowane z [najnowsze zatwierdzenie do wzorca][arch-git]</span><span class="sxs-lookup"><span data-stu-id="7cd0b-231">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="7cd0b-232">Można zainstalować, za pomocą [najnowszej wersji pliku binarnego][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="7cd0b-232">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="7cd0b-233">Pakiety w AUR są utrzymywane społeczności — Brak obsługi oficjalnych.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-233">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="7cd0b-234">Aby uzyskać więcej informacji na temat instalowania pakietów z AUR, zobacz [wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) lub społeczności [pliku DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="7cd0b-234">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch systemu Linux]: https://www.archlinux.org/download/
[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="7cd0b-236">Przyciągaj pakietu</span><span class="sxs-lookup"><span data-stu-id="7cd0b-236">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="7cd0b-237">Wprowadzenie snapd</span><span class="sxs-lookup"><span data-stu-id="7cd0b-237">Getting snapd</span></span>

<span data-ttu-id="7cd0b-238">`snapd` jest wymagany do uruchomienia przyciąganie.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-238">`snapd` is required to run snaps.</span></span>
<span data-ttu-id="7cd0b-239">Użyj [w instrukcjach](https://docs.snapcraft.io/core/install) aby upewnić się, że masz `snapd` zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-239">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="7cd0b-240">Instalację za pomocą przystawki</span><span class="sxs-lookup"><span data-stu-id="7cd0b-240">Installation via Snap</span></span>

<span data-ttu-id="7cd0b-241">Program PowerShell Core dla systemu Linux, są publikowane w [magazynu przystawki](https://snapcraft.io/store) łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="7cd0b-241">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="7cd0b-242">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-242">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="7cd0b-243">Po zainstalowaniu przystawki zostanie automatycznie uaktualniona, ale możesz wyzwolić uaktualnienia przy użyciu `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-243">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="7cd0b-244">Dezinstalacja</span><span class="sxs-lookup"><span data-stu-id="7cd0b-244">Uninstallation</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="7cd0b-245">Kali</span><span class="sxs-lookup"><span data-stu-id="7cd0b-245">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="7cd0b-246">Instalacja</span><span class="sxs-lookup"><span data-stu-id="7cd0b-246">Installation</span></span>

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

### <a name="uninstallation---kali"></a><span data-ttu-id="7cd0b-247">Dezinstalacja - Kali</span><span class="sxs-lookup"><span data-stu-id="7cd0b-247">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="7cd0b-248">Raspbian</span><span class="sxs-lookup"><span data-stu-id="7cd0b-248">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="7cd0b-249">Obsługa Raspbian jest eksperymentalne.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-249">Raspbian support is experimental.</span></span>

<span data-ttu-id="7cd0b-250">Program PowerShell jest obecnie obsługiwane tylko w Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-250">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="7cd0b-251">Również CoreCLR (i w związku z tym program PowerShell Core) będą działać tylko na urządzeniach Pi 2 i Pi 3 jako inne urządzenia, takie jak [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), ma nieobsługiwany procesor.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-251">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="7cd0b-252">Pobierz [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) i postępuj zgodnie z [instrukcje dotyczące instalacji](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) uruchomienie go na swoje Pi.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-252">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="7cd0b-253">Instalacja</span><span class="sxs-lookup"><span data-stu-id="7cd0b-253">Installation</span></span>

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

<span data-ttu-id="7cd0b-254">Opcjonalnie można utworzyć łącza symbolicznego, aby można było uruchomić środowisko PowerShell bez określenia ścieżki do "pwsh" binarny</span><span class="sxs-lookup"><span data-stu-id="7cd0b-254">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="7cd0b-255">Dezinstalacja - Raspbian</span><span class="sxs-lookup"><span data-stu-id="7cd0b-255">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="7cd0b-256">Binarny archiwa</span><span class="sxs-lookup"><span data-stu-id="7cd0b-256">Binary Archives</span></span>

<span data-ttu-id="7cd0b-257">Plik binarny programu PowerShell `tar.gz` archiwa są dostarczane dla platform Linux umożliwić zaawansowanych scenariuszach wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-257">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="7cd0b-258">Zależności</span><span class="sxs-lookup"><span data-stu-id="7cd0b-258">Dependencies</span></span>

<span data-ttu-id="7cd0b-259">PowerShell tworzy przenośne pliki binarne dla wszystkich dystrybucjach systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-259">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="7cd0b-260">Środowisko uruchomieniowe programu .NET Core wymaga różnych składników zależnych w różnych dystrybucjach — a więc programu PowerShell działa tak samo.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-260">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="7cd0b-261">Poniższej tabeli przedstawiono zależności platformy .NET Core 2.0, które są oficjalnie obsługiwane przez różne dystrybucje systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-261">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="7cd0b-262">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="7cd0b-262">OS</span></span>                 | <span data-ttu-id="7cd0b-263">Zależności</span><span class="sxs-lookup"><span data-stu-id="7cd0b-263">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="7cd0b-264">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="7cd0b-264">Ubuntu 14.04</span></span>       | <span data-ttu-id="7cd0b-265">libc6, liblttng libgssapi-krb5-2, libgcc1,-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="7cd0b-265">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7cd0b-266">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="7cd0b-266">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="7cd0b-267">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="7cd0b-267">Ubuntu 16.04</span></span>       | <span data-ttu-id="7cd0b-268">libc6, liblttng libgssapi-krb5-2, libgcc1,-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="7cd0b-268">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7cd0b-269">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="7cd0b-269">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="7cd0b-270">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="7cd0b-270">Ubuntu 17.10</span></span>       | <span data-ttu-id="7cd0b-271">libc6, liblttng libgssapi-krb5-2, libgcc1,-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="7cd0b-271">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7cd0b-272">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="7cd0b-272">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="7cd0b-273">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="7cd0b-273">Ubuntu 18.04</span></span>       | <span data-ttu-id="7cd0b-274">libc6, liblttng libgssapi-krb5-2, libgcc1,-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="7cd0b-274">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7cd0b-275">libcurl3 libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="7cd0b-275">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="7cd0b-276">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="7cd0b-276">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="7cd0b-277">libc6, liblttng libgssapi-krb5-2, libgcc1,-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="7cd0b-277">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7cd0b-278">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="7cd0b-278">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="7cd0b-279">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="7cd0b-279">Debian 9 (Stretch)</span></span> | <span data-ttu-id="7cd0b-280">libc6, liblttng libgssapi-krb5-2, libgcc1,-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="7cd0b-280">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7cd0b-281">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="7cd0b-281">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="7cd0b-282">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7cd0b-282">CentOS 7</span></span> <br> <span data-ttu-id="7cd0b-283">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="7cd0b-283">Oracle Linux 7</span></span> <br> <span data-ttu-id="7cd0b-284">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="7cd0b-284">RHEL 7</span></span> <br> <span data-ttu-id="7cd0b-285">OpenSUSE OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="7cd0b-285">OpenSUSE OpenSUSE 42.3</span></span> | <span data-ttu-id="7cd0b-286">libunwind, libcurl, biblioteki openssl, libicu</span><span class="sxs-lookup"><span data-stu-id="7cd0b-286">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="7cd0b-287">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="7cd0b-287">Fedora 27</span></span> <br> <span data-ttu-id="7cd0b-288">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="7cd0b-288">Fedora 28</span></span> | <span data-ttu-id="7cd0b-289">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="7cd0b-289">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="7cd0b-290">Aby wdrożyć pliki binarne programu PowerShell, w dystrybucjach systemu Linux, które nie są oficjalnie obsługiwane, należy zainstalować wymagane zależności dla docelowego systemu operacyjnego w oddzielne kroki.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-290">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="7cd0b-291">Na przykład naszym [dockerfile Amazon Linux] [ amazon-dockerfile] najpierw zainstalowanie zależności, a następnie wyodrębnia systemu Linux `tar.gz` archiwum.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-291">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="7cd0b-292">Instalacja — archiwum binarne</span><span class="sxs-lookup"><span data-stu-id="7cd0b-292">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="7cd0b-293">Linux</span><span class="sxs-lookup"><span data-stu-id="7cd0b-293">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="7cd0b-294">Odinstalowywanie archiwum binarne</span><span class="sxs-lookup"><span data-stu-id="7cd0b-294">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="7cd0b-295">Ścieżki</span><span class="sxs-lookup"><span data-stu-id="7cd0b-295">Paths</span></span>

* <span data-ttu-id="7cd0b-296">`$PSHOME` jest `/opt/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="7cd0b-296">`$PSHOME` is `/opt/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="7cd0b-297">Profile użytkowników będą odczytywane z `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="7cd0b-297">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="7cd0b-298">Domyślne profile będą odczytywane z `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="7cd0b-298">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="7cd0b-299">Moduły użytkownika zostanie odczytany z `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="7cd0b-299">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="7cd0b-300">Udostępnione moduły będą odczytywane z `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="7cd0b-300">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="7cd0b-301">Domyślne moduły będą odczytywane z `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="7cd0b-301">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="7cd0b-302">Historia PSReadline zostanie zarejestrowana w celu `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="7cd0b-302">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="7cd0b-303">Profile przestrzegają konfiguracji dla hosta programu PowerShell, więc domyślne profile specyficzne dla hosta istnieje w `Microsoft.PowerShell_profile.ps1` w tej samej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-303">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="7cd0b-304">Stosuje się do programu PowerShell [specyfikację katalogu Base XDG] [ xdg-bds] w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="7cd0b-304">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[zwalnia]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
