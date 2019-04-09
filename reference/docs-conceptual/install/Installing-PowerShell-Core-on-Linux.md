---
title: Instalowanie programu PowerShell Core w systemie Linux
description: Informacje o instalowaniu programu PowerShell Core w różnych dystrybucjach systemu Linux
ms.date: 08/06/2018
ms.openlocfilehash: 06194550f4e73f9dd38f8cdc25f6c7f698cafce2
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293337"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="ad9db-103">Instalowanie programu PowerShell Core w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="ad9db-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="ad9db-104">Obsługuje [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04] [ u1804], [Ubuntu 18.10][u1810], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [ openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], i [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="ad9db-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810],  [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="ad9db-105">Dystrybucje systemu Linux, które nie są oficjalnie obsługiwane, spróbuj użyć [pakiet przyciąganie PowerShell][snap].</span><span class="sxs-lookup"><span data-stu-id="ad9db-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="ad9db-106">Możesz też spróbować wdrażania plików binarnych programu PowerShell bezpośrednio przy użyciu systemu Linux [ `tar.gz` archiwum][tar], ale należy skonfigurować niezbędne zależności, w oparciu o system operacyjny w oddzielne kroki.</span><span class="sxs-lookup"><span data-stu-id="ad9db-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="ad9db-107">Wszystkie pakiety są dostępne w usłudze GitHub [zwalnia][] strony.</span><span class="sxs-lookup"><span data-stu-id="ad9db-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="ad9db-108">Po zainstalowaniu pakietu Uruchom `pwsh` z poziomu terminalu.</span><span class="sxs-lookup"><span data-stu-id="ad9db-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
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

## <a name="installing-preview-releases"></a><span data-ttu-id="ad9db-109">Instalowanie wersji zapoznawczych</span><span class="sxs-lookup"><span data-stu-id="ad9db-109">Installing Preview Releases</span></span>

<span data-ttu-id="ad9db-110">Podczas instalowania wersji programu PowerShell Core w wersji zapoznawczej dla systemu Linux przy użyciu repozytorium pakietów, nazwy pakietu zmieni się z `powershell` do `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="ad9db-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="ad9db-111">Instalowanie przy użyciu bezpośredniego pobierania nie ulega zmianie, inna niż nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="ad9db-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="ad9db-112">W tym miejscu znajduje się tabela polecenia, aby zainstalować pakiety w wersji zapoznawczej i stabilny, przy użyciu różnych menedżerów pakietów:</span><span class="sxs-lookup"><span data-stu-id="ad9db-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="ad9db-113">Distribution(s)</span><span class="sxs-lookup"><span data-stu-id="ad9db-113">Distribution(s)</span></span>|<span data-ttu-id="ad9db-114">Polecenie stabilne</span><span class="sxs-lookup"><span data-stu-id="ad9db-114">Stable Command</span></span> | <span data-ttu-id="ad9db-115">Polecenia w wersji zapoznawczej</span><span class="sxs-lookup"><span data-stu-id="ad9db-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="ad9db-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="ad9db-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="ad9db-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="ad9db-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="ad9db-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="ad9db-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="ad9db-119">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="ad9db-119">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="ad9db-120">Instalację przy użyciu repozytorium pakietów — Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="ad9db-120">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="ad9db-121">Program PowerShell Core dla systemu Linux jest publikowany repozytoriów pakietów do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="ad9db-121">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="ad9db-122">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="ad9db-122">This is the preferred method.</span></span>

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

<span data-ttu-id="ad9db-123">Jako administratora należy zarejestrować się w repozytorium firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ad9db-123">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="ad9db-124">Od tego momentu, po prostu musisz użyć `sudo apt-get upgrade powershell` do aktualizacji instalacji.</span><span class="sxs-lookup"><span data-stu-id="ad9db-124">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="ad9db-125">Instalację za pomocą bezpośredniego pobierania — Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="ad9db-125">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="ad9db-126">Pobierz pakiet Debian</span><span class="sxs-lookup"><span data-stu-id="ad9db-126">Download the Debian package</span></span>
`powershell_6.2.0-1.ubuntu.14.04_amd64.deb`
<span data-ttu-id="ad9db-127">z [zwalnia][] strony na komputerze Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="ad9db-127">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="ad9db-128">Następnie wykonaj następujące czynności w terminalu:</span><span class="sxs-lookup"><span data-stu-id="ad9db-128">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="ad9db-129">`dpkg -i` Polecenia nie powiodło się niewypełnienia zależności.</span><span class="sxs-lookup"><span data-stu-id="ad9db-129">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="ad9db-130">Następne polecenie `apt-get install -f` rozwiązuje te problemy, a następnie kończy Konfigurowanie pakietami programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ad9db-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="ad9db-131">Dezinstalacja — Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="ad9db-131">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="ad9db-132">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ad9db-132">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="ad9db-133">Instalację przy użyciu repozytorium pakietów — Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ad9db-133">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="ad9db-134">Program PowerShell Core dla systemu Linux jest publikowany repozytoriów pakietów do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="ad9db-134">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="ad9db-135">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="ad9db-135">This is the preferred method.</span></span>

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

<span data-ttu-id="ad9db-136">Po zarejestrowaniu programu Microsoft repository raz jako administratora, od tego momentu, po prostu musisz użyć `sudo apt-get upgrade powershell` ją zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="ad9db-136">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="ad9db-137">Instalację za pomocą bezpośredniego pobierania — Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ad9db-137">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="ad9db-138">Pobierz pakiet Debian</span><span class="sxs-lookup"><span data-stu-id="ad9db-138">Download the Debian package</span></span>
`powershell_6.2.0-1.ubuntu.16.04_amd64.deb`
<span data-ttu-id="ad9db-139">z [zwalnia][] strony na komputerze Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="ad9db-139">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="ad9db-140">Następnie wykonaj następujące czynności w terminalu:</span><span class="sxs-lookup"><span data-stu-id="ad9db-140">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="ad9db-141">`dpkg -i` Polecenia nie powiodło się niewypełnienia zależności.</span><span class="sxs-lookup"><span data-stu-id="ad9db-141">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="ad9db-142">Następne polecenie `apt-get install -f` rozwiązuje te problemy, a następnie kończy Konfigurowanie pakietami programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ad9db-142">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="ad9db-143">Dezinstalacja — Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ad9db-143">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="ad9db-144">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="ad9db-144">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="ad9db-145">Instalację przy użyciu repozytorium pakietów — Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="ad9db-145">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="ad9db-146">Program PowerShell Core dla systemu Linux jest publikowany repozytoriów pakietów do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="ad9db-146">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="ad9db-147">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="ad9db-147">This is the preferred method.</span></span>

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

<span data-ttu-id="ad9db-148">Po zarejestrowaniu programu Microsoft repository raz jako administratora, od tego momentu, po prostu musisz użyć `sudo apt-get upgrade powershell` ją zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="ad9db-148">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="ad9db-149">Instalację za pomocą bezpośredniego pobierania — Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="ad9db-149">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="ad9db-150">Pobierz pakiet Debian</span><span class="sxs-lookup"><span data-stu-id="ad9db-150">Download the Debian package</span></span>
`powershell_6.2.0-1.ubuntu.18.04_amd64.deb`
<span data-ttu-id="ad9db-151">z [zwalnia][] strony na komputerze Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="ad9db-151">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="ad9db-152">Następnie wykonaj następujące czynności w terminalu:</span><span class="sxs-lookup"><span data-stu-id="ad9db-152">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="ad9db-153">`dpkg -i` Polecenia nie powiodło się niewypełnienia zależności.</span><span class="sxs-lookup"><span data-stu-id="ad9db-153">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="ad9db-154">Następne polecenie `apt-get install -f` rozwiązuje te problemy, a następnie kończy Konfigurowanie pakietami programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ad9db-154">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="ad9db-155">Dezinstalacja — Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="ad9db-155">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="ad9db-156">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="ad9db-156">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="ad9db-157">Ponieważ 18.10 [tymczasowe wersji](https://www.ubuntu.com/about/release-cycle), jest on tylko [wspieranym przez społeczność](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="ad9db-157">As 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle), it is only [community supported](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span></span>

<span data-ttu-id="ad9db-158">Instalowanie na 18.10 jest świadczona za pośrednictwem `snapd`.</span><span class="sxs-lookup"><span data-stu-id="ad9db-158">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="ad9db-159">Zobacz [przyciąganie pakietu] [ snap] pełne instrukcje;</span><span class="sxs-lookup"><span data-stu-id="ad9db-159">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="ad9db-160">Debian 8</span><span class="sxs-lookup"><span data-stu-id="ad9db-160">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="ad9db-161">Instalację przy użyciu repozytorium pakietów — Debian 8</span><span class="sxs-lookup"><span data-stu-id="ad9db-161">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="ad9db-162">Program PowerShell Core dla systemu Linux jest publikowany repozytoriów pakietów do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="ad9db-162">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="ad9db-163">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="ad9db-163">This is the preferred method.</span></span>

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

<span data-ttu-id="ad9db-164">Po zarejestrowaniu programu Microsoft repository raz jako administratora, od tego momentu, po prostu musisz użyć `sudo apt-get upgrade powershell` ją zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="ad9db-164">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

## <a name="debian-9"></a><span data-ttu-id="ad9db-165">Debian 9</span><span class="sxs-lookup"><span data-stu-id="ad9db-165">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="ad9db-166">Instalację przy użyciu repozytorium pakietów - Debian 9</span><span class="sxs-lookup"><span data-stu-id="ad9db-166">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="ad9db-167">Program PowerShell Core dla systemu Linux jest publikowany repozytoriów pakietów do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="ad9db-167">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="ad9db-168">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="ad9db-168">This is the preferred method.</span></span>

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

<span data-ttu-id="ad9db-169">Po zarejestrowaniu programu Microsoft repository raz jako administratora, od tego momentu, po prostu musisz użyć `sudo apt-get upgrade powershell` ją zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="ad9db-169">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="ad9db-170">Instalację za pomocą bezpośredniego pobierania - Debian 9</span><span class="sxs-lookup"><span data-stu-id="ad9db-170">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="ad9db-171">Pobierz pakiet Debian</span><span class="sxs-lookup"><span data-stu-id="ad9db-171">Download the Debian package</span></span>
`powershell_6.2.0-1.debian.9_amd64.deb`
<span data-ttu-id="ad9db-172">z [zwalnia][] strony na komputerze Debian.</span><span class="sxs-lookup"><span data-stu-id="ad9db-172">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="ad9db-173">Następnie wykonaj następujące czynności w terminalu:</span><span class="sxs-lookup"><span data-stu-id="ad9db-173">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="ad9db-174">Dezinstalacja — Debian 9</span><span class="sxs-lookup"><span data-stu-id="ad9db-174">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="ad9db-175">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ad9db-175">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="ad9db-176">Ten pakiet działa także w systemie Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="ad9db-176">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="ad9db-177">Instalację przy użyciu repozytorium pakietów (preferowany) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ad9db-177">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="ad9db-178">Program PowerShell Core dla systemu Linux jest publikowany oficjalnych repozytoriów firmy Microsoft do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="ad9db-178">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="ad9db-179">Po zarejestrowaniu programu Microsoft repository raz jako administratora, po prostu musisz użyć `sudo yum update powershell` do zaktualizowania programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ad9db-179">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="ad9db-180">Instalację za pomocą bezpośredniego pobierania - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ad9db-180">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="ad9db-181">Za pomocą [CentOS 7][], Pobierz pakiet obr. / min</span><span class="sxs-lookup"><span data-stu-id="ad9db-181">Using [CentOS 7][], download the RPM package</span></span>
`powershell-6.2.0-1.rhel.7.x86_64.rpm`
<span data-ttu-id="ad9db-182">z [zwalnia][] strony na komputerze CentOS.</span><span class="sxs-lookup"><span data-stu-id="ad9db-182">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="ad9db-183">Następnie wykonaj następujące czynności w terminalu:</span><span class="sxs-lookup"><span data-stu-id="ad9db-183">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="ad9db-184">Można także zainstalować obr. / min bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="ad9db-184">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="ad9db-185">Dezinstalacja - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ad9db-185">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[<span data-ttu-id="ad9db-186">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ad9db-186">CentOS 7</span></span>]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="ad9db-187">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="ad9db-187">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="ad9db-188">Instalację przy użyciu repozytorium pakietów (preferowany) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="ad9db-188">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="ad9db-189">Program PowerShell Core dla systemu Linux jest publikowany oficjalnych repozytoriów firmy Microsoft do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="ad9db-189">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="ad9db-190">Po zarejestrowaniu programu Microsoft repository raz jako administratora, po prostu musisz użyć `sudo yum update powershell` do zaktualizowania programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ad9db-190">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="ad9db-191">Instalację za pomocą bezpośredniego pobierania - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="ad9db-191">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="ad9db-192">Pobierz pakiet obr. / min</span><span class="sxs-lookup"><span data-stu-id="ad9db-192">Download the RPM package</span></span>
`powershell-6.2.0-1.rhel.7.x86_64.rpm`
<span data-ttu-id="ad9db-193">z [zwalnia][] strony na komputerze Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="ad9db-193">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="ad9db-194">Następnie wykonaj następujące czynności w terminalu:</span><span class="sxs-lookup"><span data-stu-id="ad9db-194">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="ad9db-195">Można także zainstalować obr. / min bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="ad9db-195">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="ad9db-196">Dezinstalacja - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="ad9db-196">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="ad9db-197">openSUSE</span><span class="sxs-lookup"><span data-stu-id="ad9db-197">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="ad9db-198">Instalacja — openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="ad9db-198">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="ad9db-199">Instalacja — openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="ad9db-199">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="ad9db-200">Dezinstalacja - openSUSE 42.3, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="ad9db-200">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="ad9db-201">Fedora</span><span class="sxs-lookup"><span data-stu-id="ad9db-201">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="ad9db-202">Fedora 28 jest obsługiwane tylko w sytuacji, w programie PowerShell Core 6.1 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="ad9db-202">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="ad9db-203">Instalację przy użyciu repozytorium pakietów (preferowany) - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="ad9db-203">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="ad9db-204">Program PowerShell Core dla systemu Linux jest publikowany oficjalnych repozytoriów firmy Microsoft do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="ad9db-204">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="ad9db-205">Instalację za pomocą bezpośredniego pobierania - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="ad9db-205">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="ad9db-206">Pobierz pakiet obr. / min</span><span class="sxs-lookup"><span data-stu-id="ad9db-206">Download the RPM package</span></span>
`powershell-6.2.0-1.rhel.7.x86_64.rpm`
<span data-ttu-id="ad9db-207">z [zwalnia][] strony na komputerze Fedora.</span><span class="sxs-lookup"><span data-stu-id="ad9db-207">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="ad9db-208">Następnie wykonaj następujące czynności w terminalu:</span><span class="sxs-lookup"><span data-stu-id="ad9db-208">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="ad9db-209">Można także zainstalować obr. / min bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="ad9db-209">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="ad9db-210">Dezinstalacja - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="ad9db-210">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="ad9db-211">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="ad9db-211">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="ad9db-212">Obsługa architektury jest eksperymentalne.</span><span class="sxs-lookup"><span data-stu-id="ad9db-212">Arch support is experimental.</span></span>

<span data-ttu-id="ad9db-213">Program PowerShell jest dostępny z [Arch Linux][] użytkownika repozytorium (AUR).</span><span class="sxs-lookup"><span data-stu-id="ad9db-213">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="ad9db-214">Może być skompilowana przy użyciu [najnowsze tagiem wydania][arch-release]</span><span class="sxs-lookup"><span data-stu-id="ad9db-214">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="ad9db-215">Może być kompilowane z [najnowsze zatwierdzenie do wzorca][arch-git]</span><span class="sxs-lookup"><span data-stu-id="ad9db-215">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="ad9db-216">Można zainstalować, za pomocą [najnowszej wersji pliku binarnego][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="ad9db-216">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="ad9db-217">Pakiety w AUR są utrzymywane społeczności — Brak obsługi oficjalnych.</span><span class="sxs-lookup"><span data-stu-id="ad9db-217">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="ad9db-218">Aby uzyskać więcej informacji na temat instalowania pakietów z AUR, zobacz [wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) lub społeczności [pliku DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="ad9db-218">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[<span data-ttu-id="ad9db-219">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="ad9db-219">Arch Linux</span></span>]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="ad9db-220">Przyciągaj pakietu</span><span class="sxs-lookup"><span data-stu-id="ad9db-220">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="ad9db-221">Wprowadzenie snapd</span><span class="sxs-lookup"><span data-stu-id="ad9db-221">Getting snapd</span></span>

`snapd` <span data-ttu-id="ad9db-222">jest wymagany do uruchomienia przyciąganie.</span><span class="sxs-lookup"><span data-stu-id="ad9db-222">is required to run snaps.</span></span>
<span data-ttu-id="ad9db-223">Użyj [w instrukcjach](https://docs.snapcraft.io/core/install) aby upewnić się, że masz `snapd` zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="ad9db-223">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="ad9db-224">Instalację za pomocą przystawki</span><span class="sxs-lookup"><span data-stu-id="ad9db-224">Installation via Snap</span></span>

<span data-ttu-id="ad9db-225">Program PowerShell Core dla systemu Linux, są publikowane w [magazynu przystawki](https://snapcraft.io/store) łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="ad9db-225">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="ad9db-226">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="ad9db-226">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="ad9db-227">Jeśli chcesz zainstalować wersję zapoznawczą, skorzystaj z następujących metod.</span><span class="sxs-lookup"><span data-stu-id="ad9db-227">If you want to install preview version, use following method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="ad9db-228">Po zainstalowaniu przystawki zostanie automatycznie uaktualniona, ale możesz wyzwolić uaktualnienia przy użyciu `sudo snap refresh powershell` lub `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="ad9db-228">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="ad9db-229">Dezinstalacja</span><span class="sxs-lookup"><span data-stu-id="ad9db-229">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="ad9db-230">lub</span><span class="sxs-lookup"><span data-stu-id="ad9db-230">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="ad9db-231">Kali</span><span class="sxs-lookup"><span data-stu-id="ad9db-231">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="ad9db-232">Instalacja — Kali</span><span class="sxs-lookup"><span data-stu-id="ad9db-232">Installation - Kali</span></span>

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

### <a name="uninstallation---kali"></a><span data-ttu-id="ad9db-233">Dezinstalacja - Kali</span><span class="sxs-lookup"><span data-stu-id="ad9db-233">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="ad9db-234">Raspbian</span><span class="sxs-lookup"><span data-stu-id="ad9db-234">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="ad9db-235">Obsługa Raspbian jest eksperymentalne.</span><span class="sxs-lookup"><span data-stu-id="ad9db-235">Raspbian support is experimental.</span></span>

<span data-ttu-id="ad9db-236">Program PowerShell jest obecnie obsługiwane tylko w Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="ad9db-236">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="ad9db-237">Również CoreCLR (i w związku z tym program PowerShell Core) będą działać tylko na urządzeniach Pi 2 i Pi 3 jako inne urządzenia, takie jak [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), ma nieobsługiwany procesor.</span><span class="sxs-lookup"><span data-stu-id="ad9db-237">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="ad9db-238">Pobierz [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) i postępuj zgodnie z [instrukcje dotyczące instalacji](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) uruchomienie go na swoje Pi.</span><span class="sxs-lookup"><span data-stu-id="ad9db-238">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="ad9db-239">Instalacja — Raspbian</span><span class="sxs-lookup"><span data-stu-id="ad9db-239">Installation - Raspbian</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.2.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="ad9db-240">Opcjonalnie można utworzyć łącza symbolicznego, aby można było uruchomić środowisko PowerShell bez określenia ścieżki do "pwsh" binarny</span><span class="sxs-lookup"><span data-stu-id="ad9db-240">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="ad9db-241">Dezinstalacja - Raspbian</span><span class="sxs-lookup"><span data-stu-id="ad9db-241">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="ad9db-242">Binarny archiwa</span><span class="sxs-lookup"><span data-stu-id="ad9db-242">Binary Archives</span></span>

<span data-ttu-id="ad9db-243">Plik binarny programu PowerShell `tar.gz` archiwa są dostarczane dla platform Linux umożliwić zaawansowanych scenariuszach wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="ad9db-243">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="ad9db-244">Zależności</span><span class="sxs-lookup"><span data-stu-id="ad9db-244">Dependencies</span></span>

<span data-ttu-id="ad9db-245">PowerShell tworzy przenośne pliki binarne dla wszystkich dystrybucjach systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="ad9db-245">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="ad9db-246">Środowisko uruchomieniowe programu .NET Core wymaga różnych składników zależnych w różnych dystrybucjach — a więc programu PowerShell działa tak samo.</span><span class="sxs-lookup"><span data-stu-id="ad9db-246">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="ad9db-247">Poniższej tabeli przedstawiono zależności platformy .NET Core 2.0, które są oficjalnie obsługiwane przez różne dystrybucje systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="ad9db-247">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="ad9db-248">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="ad9db-248">OS</span></span>                 | <span data-ttu-id="ad9db-249">Zależności</span><span class="sxs-lookup"><span data-stu-id="ad9db-249">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="ad9db-250">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="ad9db-250">Ubuntu 14.04</span></span>       | <span data-ttu-id="ad9db-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="ad9db-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ad9db-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="ad9db-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="ad9db-253">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ad9db-253">Ubuntu 16.04</span></span>       | <span data-ttu-id="ad9db-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="ad9db-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ad9db-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="ad9db-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="ad9db-256">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="ad9db-256">Ubuntu 17.10</span></span>       | <span data-ttu-id="ad9db-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="ad9db-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ad9db-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="ad9db-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="ad9db-259">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="ad9db-259">Ubuntu 18.04</span></span>       | <span data-ttu-id="ad9db-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="ad9db-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ad9db-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="ad9db-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="ad9db-262">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="ad9db-262">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="ad9db-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="ad9db-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ad9db-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="ad9db-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="ad9db-265">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="ad9db-265">Debian 9 (Stretch)</span></span> | <span data-ttu-id="ad9db-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="ad9db-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ad9db-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="ad9db-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="ad9db-268">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ad9db-268">CentOS 7</span></span> <br> <span data-ttu-id="ad9db-269">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="ad9db-269">Oracle Linux 7</span></span> <br> <span data-ttu-id="ad9db-270">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="ad9db-270">RHEL 7</span></span> | <span data-ttu-id="ad9db-271">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="ad9db-271">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="ad9db-272">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="ad9db-272">openSUSE 42.3</span></span> | <span data-ttu-id="ad9db-273">libcurl4 libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="ad9db-273">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="ad9db-274">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="ad9db-274">openSUSE Leap 15</span></span> | <span data-ttu-id="ad9db-275">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="ad9db-275">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="ad9db-276">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="ad9db-276">Fedora 27</span></span> <br> <span data-ttu-id="ad9db-277">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="ad9db-277">Fedora 28</span></span> | <span data-ttu-id="ad9db-278">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="ad9db-278">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="ad9db-279">Aby wdrożyć pliki binarne programu PowerShell, w dystrybucjach systemu Linux, które nie są oficjalnie obsługiwane, należy zainstalować wymagane zależności dla docelowego systemu operacyjnego w oddzielne kroki.</span><span class="sxs-lookup"><span data-stu-id="ad9db-279">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="ad9db-280">Na przykład naszym [dockerfile Amazon Linux] [ amazon-dockerfile] najpierw zainstalowanie zależności, a następnie wyodrębnia systemu Linux `tar.gz` archiwum.</span><span class="sxs-lookup"><span data-stu-id="ad9db-280">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="ad9db-281">Instalacja — archiwum binarne</span><span class="sxs-lookup"><span data-stu-id="ad9db-281">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="ad9db-282">Linux</span><span class="sxs-lookup"><span data-stu-id="ad9db-282">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="ad9db-283">Odinstalowywanie archiwum binarne</span><span class="sxs-lookup"><span data-stu-id="ad9db-283">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="ad9db-284">Ścieżki</span><span class="sxs-lookup"><span data-stu-id="ad9db-284">Paths</span></span>

* `$PSHOME` <span data-ttu-id="ad9db-285">jest</span><span class="sxs-lookup"><span data-stu-id="ad9db-285">is</span></span> `/opt/microsoft/powershell/6.2.0/`
* <span data-ttu-id="ad9db-286">Profile użytkowników będą odczytywane z</span><span class="sxs-lookup"><span data-stu-id="ad9db-286">User profiles will be read from</span></span> `~/.config/powershell/profile.ps1`
* <span data-ttu-id="ad9db-287">Domyślne profile będą odczytywane z</span><span class="sxs-lookup"><span data-stu-id="ad9db-287">Default profiles will be read from</span></span> `$PSHOME/profile.ps1`
* <span data-ttu-id="ad9db-288">Moduły użytkownika zostanie odczytany z</span><span class="sxs-lookup"><span data-stu-id="ad9db-288">User modules will be read from</span></span> `~/.local/share/powershell/Modules`
* <span data-ttu-id="ad9db-289">Udostępnione moduły będą odczytywane z</span><span class="sxs-lookup"><span data-stu-id="ad9db-289">Shared modules will be read from</span></span> `/usr/local/share/powershell/Modules`
* <span data-ttu-id="ad9db-290">Domyślne moduły będą odczytywane z</span><span class="sxs-lookup"><span data-stu-id="ad9db-290">Default modules will be read from</span></span> `$PSHOME/Modules`
* <span data-ttu-id="ad9db-291">Historia PSReadline zostanie zarejestrowana w celu</span><span class="sxs-lookup"><span data-stu-id="ad9db-291">PSReadline history will be recorded to</span></span> `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

<span data-ttu-id="ad9db-292">Profile przestrzegają konfiguracji dla hosta programu PowerShell, więc domyślne profile specyficzne dla hosta istnieje w `Microsoft.PowerShell_profile.ps1` w tej samej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="ad9db-292">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="ad9db-293">Stosuje się do programu PowerShell [specyfikację katalogu Base XDG] [ xdg-bds] w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="ad9db-293">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[<span data-ttu-id="ad9db-294">Wersje</span><span class="sxs-lookup"><span data-stu-id="ad9db-294">releases</span></span>]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
