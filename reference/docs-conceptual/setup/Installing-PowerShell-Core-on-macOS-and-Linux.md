# <a name="installing-powershell-core-on-macos-and-linux"></a><span data-ttu-id="73a23-101">Instalowanie programu PowerShell Core w systemach macOS i Linux</span><span class="sxs-lookup"><span data-stu-id="73a23-101">Installing PowerShell Core on macOS and Linux</span></span>

<span data-ttu-id="73a23-102">Obsługuje [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04] [ u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25 ] [ fed25], [Fedora 26][fed26], [Arch Linux][arch]i [macOS 10.12][mac].</span><span class="sxs-lookup"><span data-stu-id="73a23-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26], [Arch Linux][arch], and [macOS 10.12][mac].</span></span>

<span data-ttu-id="73a23-103">Dla dystrybucje systemu Linux, które nie są obsługiwane oficjalnie, można spróbować użyć [PowerShell AppImage][lai].</span><span class="sxs-lookup"><span data-stu-id="73a23-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span> <span data-ttu-id="73a23-104">Można też spróbować wdrożenia plików binarnych programu PowerShell bezpośrednio przy użyciu systemu Linux [ `tar.gz` archiwum][tar], ale należy skonfigurować wymagane zależności, oparte na system operacyjny w oddzielne kroki.</span><span class="sxs-lookup"><span data-stu-id="73a23-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="73a23-105">Wszystkie pakiety są dostępne w naszej witrynie GitHub [zwalnia][] strony.</span><span class="sxs-lookup"><span data-stu-id="73a23-105">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="73a23-106">Po zainstalowaniu pakietu `pwsh` z terminalu.</span><span class="sxs-lookup"><span data-stu-id="73a23-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

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

## <a name="ubuntu-1404"></a><span data-ttu-id="73a23-107">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="73a23-107">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="73a23-108">Instalacja za pośrednictwem repozytorium pakietów - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="73a23-108">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="73a23-109">Podstawowe programu PowerShell dla systemu Linux jest publikowany dla repozytoriów pakietu do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="73a23-109">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span> <span data-ttu-id="73a23-110">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="73a23-110">This is the preferred method.</span></span>

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

<span data-ttu-id="73a23-111">Po zarejestrowaniu repozytorium Microsoft raz jako administratora, od, wystarczy użyć `sudo apt-get upgrade powershell` go zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="73a23-111">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="73a23-112">Instalacja za pośrednictwem bezpośredniego pobierania - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="73a23-112">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="73a23-113">Pobierz pakiet Debian `powershell_6.0.0-1.ubuntu.14.04_amd64.deb` z [zwalnia][] strony na maszynie Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="73a23-113">Download the Debian package `powershell_6.0.0-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.14.04_amd64.deb
```

<span data-ttu-id="73a23-114">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="73a23-114">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="73a23-115">Należy pamiętać, że `dpkg -i` zakończy się niepowodzeniem z zależności unmet; następne polecenie `apt-get install -f` rozpoznaje je, a następnie kończy Konfigurowanie pakietu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="73a23-115">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="73a23-116">Dezinstalacja - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="73a23-116">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="73a23-117">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="73a23-117">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="73a23-118">Instalacja za pośrednictwem repozytorium pakietów - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="73a23-118">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="73a23-119">Podstawowe programu PowerShell dla systemu Linux jest publikowany dla repozytoriów pakietu do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="73a23-119">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="73a23-120">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="73a23-120">This is the preferred method.</span></span>

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

<span data-ttu-id="73a23-121">Po zarejestrowaniu repozytorium Microsoft raz jako administratora, od, wystarczy użyć `sudo apt-get upgrade powershell` go zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="73a23-121">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="73a23-122">Instalacja za pośrednictwem bezpośredniego pobierania - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="73a23-122">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="73a23-123">Pobierz pakiet Debian `powershell_6.0.0-1.ubuntu.16.04_amd64.deb` z [zwalnia][] strony na maszynie Ubuntu:</span><span class="sxs-lookup"><span data-stu-id="73a23-123">Download the Debian package `powershell_6.0.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
```

<span data-ttu-id="73a23-124">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="73a23-124">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="73a23-125">Należy pamiętać, że `dpkg -i` zakończy się niepowodzeniem z zależności unmet; następne polecenie `apt-get install -f` rozpoznaje je, a następnie kończy Konfigurowanie pakietu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="73a23-125">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="73a23-126">Dezinstalacja - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="73a23-126">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a><span data-ttu-id="73a23-127">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="73a23-127">Ubuntu 17.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1704"></a><span data-ttu-id="73a23-128">Instalacja za pośrednictwem repozytorium pakietów - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="73a23-128">Installation via Package Repository - Ubuntu 17.04</span></span>

<span data-ttu-id="73a23-129">Podstawowe programu PowerShell dla systemu Linux jest publikowany dla repozytoriów pakietu do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="73a23-129">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="73a23-130">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="73a23-130">This is the preferred method.</span></span>

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

<span data-ttu-id="73a23-131">Po zarejestrowaniu repozytorium Microsoft raz jako administratora, od, wystarczy użyć `sudo apt-get upgrade powershell` go zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="73a23-131">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1704"></a><span data-ttu-id="73a23-132">Instalacja za pośrednictwem bezpośredniego pobierania - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="73a23-132">Installation via Direct Download - Ubuntu 17.04</span></span>

<span data-ttu-id="73a23-133">Pobierz pakiet Debian `powershell_6.0.0-1.ubuntu.17.04_amd64.deb` z [zwalnia][] strony na maszynie Ubuntu:</span><span class="sxs-lookup"><span data-stu-id="73a23-133">Download the Debian package `powershell_6.0.0-1.ubuntu.17.04_amd64.deb` from the [releases][] page onto the Ubuntu machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.17.04_amd64.deb
```

<span data-ttu-id="73a23-134">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="73a23-134">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="73a23-135">Należy pamiętać, że `dpkg -i` zakończy się niepowodzeniem z zależności unmet; następne polecenie `apt-get install -f` rozpoznaje je, a następnie kończy Konfigurowanie pakietu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="73a23-135">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1704"></a><span data-ttu-id="73a23-136">Dezinstalacja - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="73a23-136">Uninstallation - Ubuntu 17.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="73a23-137">Debian 8</span><span class="sxs-lookup"><span data-stu-id="73a23-137">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="73a23-138">Instalacja za pośrednictwem repozytorium pakietów - Debian 8</span><span class="sxs-lookup"><span data-stu-id="73a23-138">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="73a23-139">Podstawowe programu PowerShell dla systemu Linux jest publikowany dla repozytoriów pakietu do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="73a23-139">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="73a23-140">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="73a23-140">This is the preferred method.</span></span>

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

<span data-ttu-id="73a23-141">Po zarejestrowaniu repozytorium Microsoft raz jako administratora, od, wystarczy użyć `sudo apt-get upgrade powershell` go zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="73a23-141">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="73a23-142">Instalacja za pośrednictwem bezpośredniego pobierania - Debian 8</span><span class="sxs-lookup"><span data-stu-id="73a23-142">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="73a23-143">Pobierz pakiet Debian `powershell_6.0.0-1.debian.8_amd64.deb` z [zwalnia][] strony na maszynie Debian:</span><span class="sxs-lookup"><span data-stu-id="73a23-143">Download the Debian package `powershell_6.0.0-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.8_amd64.deb
```

<span data-ttu-id="73a23-144">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="73a23-144">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="73a23-145">Należy pamiętać, że `dpkg -i` zakończy się niepowodzeniem z zależności unmet; następne polecenie `apt-get install -f` rozpoznaje je, a następnie kończy Konfigurowanie pakietu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="73a23-145">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="73a23-146">Dezinstalacja - Debian 8</span><span class="sxs-lookup"><span data-stu-id="73a23-146">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="73a23-147">Debian 9</span><span class="sxs-lookup"><span data-stu-id="73a23-147">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="73a23-148">Instalacja za pośrednictwem repozytorium pakietów - Debian 9</span><span class="sxs-lookup"><span data-stu-id="73a23-148">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="73a23-149">Podstawowe programu PowerShell dla systemu Linux jest publikowany dla repozytoriów pakietu do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="73a23-149">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="73a23-150">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="73a23-150">This is the preferred method.</span></span>

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

<span data-ttu-id="73a23-151">Po zarejestrowaniu repozytorium Microsoft raz jako administratora, od, wystarczy użyć `sudo apt-get upgrade powershell` go zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="73a23-151">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="73a23-152">Instalacja za pośrednictwem bezpośredniego pobierania - Debian 9</span><span class="sxs-lookup"><span data-stu-id="73a23-152">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="73a23-153">Pobierz pakiet Debian `powershell_6.0.0-1.debian.9_amd64.deb` z [zwalnia][] strony na maszynie Debian:</span><span class="sxs-lookup"><span data-stu-id="73a23-153">Download the Debian package `powershell_6.0.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

<span data-ttu-id="73a23-154">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="73a23-154">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="73a23-155">Należy pamiętać, że `dpkg -i` zakończy się niepowodzeniem z zależności unmet; następne polecenie `apt-get install -f` rozpoznaje je, a następnie kończy Konfigurowanie pakietu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="73a23-155">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-9"></a><span data-ttu-id="73a23-156">Dezinstalacja - Debian 9</span><span class="sxs-lookup"><span data-stu-id="73a23-156">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="73a23-157">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="73a23-157">CentOS 7</span></span>

> <span data-ttu-id="73a23-158">Ten pakiet jest również działa na Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="73a23-158">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="73a23-159">Instalacja za pośrednictwem repozytorium pakietów (preferowane) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="73a23-159">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="73a23-160">Podstawowe programu PowerShell dla systemu Linux jest publikowany oficjalnego repozytoria Microsoft easy instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="73a23-160">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="73a23-161">Po zarejestrowaniu repozytorium Microsoft raz jako administratora, wystarczy użyć `sudo yum update powershell` aktualizacji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="73a23-161">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="73a23-162">Instalacja za pośrednictwem bezpośredniego pobierania - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="73a23-162">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="73a23-163">Przy użyciu [CentOS 7][], Pobierz pakiet RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` z [zwalnia][] strony na maszynie CentOS:</span><span class="sxs-lookup"><span data-stu-id="73a23-163">Using [CentOS 7][], download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="73a23-164">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="73a23-164">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="73a23-165">Można także zainstalować RPM bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="73a23-165">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="73a23-166">Dezinstalacja - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="73a23-166">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="73a23-168">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="73a23-168">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="73a23-169">Instalacja za pośrednictwem repozytorium pakietów (preferowane) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="73a23-169">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="73a23-170">Podstawowe programu PowerShell dla systemu Linux jest publikowany oficjalnego repozytoria Microsoft easy instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="73a23-170">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="73a23-171">Po zarejestrowaniu repozytorium Microsoft raz jako administratora, wystarczy użyć `sudo yum update powershell` aktualizacji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="73a23-171">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="73a23-172">Instalacja za pośrednictwem bezpośredniego pobierania - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="73a23-172">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="73a23-173">Pobierz pakiet RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` z [zwalnia][] strony na maszynie Red Hat Enterprise Linux:</span><span class="sxs-lookup"><span data-stu-id="73a23-173">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

<span data-ttu-id="73a23-174">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="73a23-174">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="73a23-175">Można także zainstalować RPM bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="73a23-175">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="73a23-176">Dezinstalacja - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="73a23-176">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="73a23-177">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="73a23-177">OpenSUSE 42.2</span></span>

> <span data-ttu-id="73a23-178">**Uwaga:** podczas instalowania programu PowerShell Core, OpenSUSE może zgłosić, nic nie zapewnia `libcurl`.</span><span class="sxs-lookup"><span data-stu-id="73a23-178">**Note:** When installing PowerShell Core, OpenSUSE may report that nothing provides `libcurl`.</span></span>
<span data-ttu-id="73a23-179">`libcurl`powinno być już zainstalowane w obsługiwanych wersjach OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="73a23-179">`libcurl` should already be installed on supported versions of OpenSUSE.</span></span>
<span data-ttu-id="73a23-180">Uruchom `zypper search libcurl` o potwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="73a23-180">Run `zypper search libcurl` to confirm.</span></span>
<span data-ttu-id="73a23-181">Błąd przedstawi 2 rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="73a23-181">The error will present 2 'solutions'.</span></span> <span data-ttu-id="73a23-182">Wybierz pozycję "Rozwiązania 2", aby kontynuować instalację programu PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="73a23-182">Choose 'Solution 2' to continue installing PowerShell Core.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="73a23-183">Instalacja za pośrednictwem repozytorium pakietów (preferowane) - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="73a23-183">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="73a23-184">Podstawowe programu PowerShell dla systemu Linux jest publikowany oficjalnego repozytoria Microsoft easy instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="73a23-184">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="73a23-185">Instalacja za pośrednictwem bezpośredniego pobierania - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="73a23-185">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="73a23-186">Pobierz pakiet RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` z [zwalnia][] strony na maszynie OpenSUSE:</span><span class="sxs-lookup"><span data-stu-id="73a23-186">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="73a23-187">Można także zainstalować RPM bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="73a23-187">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="73a23-188">Dezinstalacja - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="73a23-188">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora-25"></a><span data-ttu-id="73a23-189">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="73a23-189">Fedora 25</span></span>

### <a name="installation-via-package-repository-preferred---fedora-25"></a><span data-ttu-id="73a23-190">Instalacja za pośrednictwem repozytorium pakietów (preferowane) - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="73a23-190">Installation via Package Repository (preferred) - Fedora 25</span></span>

<span data-ttu-id="73a23-191">Podstawowe programu PowerShell dla systemu Linux jest publikowany oficjalnego repozytoria Microsoft easy instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="73a23-191">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-25"></a><span data-ttu-id="73a23-192">Instalacja za pośrednictwem bezpośredniego pobierania - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="73a23-192">Installation via Direct Download - Fedora 25</span></span>

<span data-ttu-id="73a23-193">Pobierz pakiet RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` z [zwalnia][] strony na maszynie Fedora:</span><span class="sxs-lookup"><span data-stu-id="73a23-193">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="73a23-194">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="73a23-194">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="73a23-195">Można także zainstalować RPM bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="73a23-195">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a><span data-ttu-id="73a23-196">Dezinstalacja - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="73a23-196">Uninstallation - Fedora 25</span></span>

```sh
sudo dnf remove powershell
```

## <a name="fedora-26"></a><span data-ttu-id="73a23-197">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="73a23-197">Fedora 26</span></span>

### <a name="installation-via-package-repository-preferred---fedora-26"></a><span data-ttu-id="73a23-198">Instalacja za pośrednictwem repozytorium pakietów (preferowane) - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="73a23-198">Installation via Package Repository (preferred) - Fedora 26</span></span>

<span data-ttu-id="73a23-199">Podstawowe programu PowerShell dla systemu Linux jest publikowany oficjalnego repozytoria Microsoft easy instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="73a23-199">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-26"></a><span data-ttu-id="73a23-200">Instalacja za pośrednictwem bezpośredniego pobierania - 26 Fedora</span><span class="sxs-lookup"><span data-stu-id="73a23-200">Installation via Direct Download - Fedora 26</span></span>

<span data-ttu-id="73a23-201">Pobierz pakiet RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` z [zwalnia][] strony na maszynie Fedora:</span><span class="sxs-lookup"><span data-stu-id="73a23-201">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="73a23-202">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="73a23-202">Then execute the following in the terminal:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="73a23-203">Można także zainstalować RPM bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="73a23-203">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a><span data-ttu-id="73a23-204">Dezinstalacja - 26 Fedora</span><span class="sxs-lookup"><span data-stu-id="73a23-204">Uninstallation - Fedora 26</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="73a23-205">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="73a23-205">Arch Linux</span></span>

<span data-ttu-id="73a23-206">Środowisko PowerShell jest dostępny z [Arch Linux][] użytkownika repozytorium (AUR).</span><span class="sxs-lookup"><span data-stu-id="73a23-206">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="73a23-207">Może być kompilowana przy użyciu [najnowszej oznakowane zlecenia][arch-release]</span><span class="sxs-lookup"><span data-stu-id="73a23-207">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="73a23-208">Mogą być kompilowane z [najnowszym zatwierdzeniu do wzorca][arch-git]</span><span class="sxs-lookup"><span data-stu-id="73a23-208">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="73a23-209">Można zainstalować, za pomocą [najnowszej wersji pliku binarnego][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="73a23-209">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="73a23-210">Pakiety w AUR Wspólnotę utrzymane — nie jest oficjalną obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="73a23-210">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="73a23-211">Aby uzyskać więcej informacji na temat instalowania pakietów z AUR, zobacz [wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) lub społeczności [plik DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="73a23-211">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="73a23-213">AppImage systemu Linux</span><span class="sxs-lookup"><span data-stu-id="73a23-213">Linux AppImage</span></span>

<span data-ttu-id="73a23-214">Przy użyciu najnowszych dystrybucji systemu Linux, Pobierz AppImage `powershell-6.0.0-x86_64.AppImage` z [zwalnia][] strony na komputerze systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="73a23-214">Using a recent Linux distribution, download the AppImage `powershell-6.0.0-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="73a23-215">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="73a23-215">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.0-x86_64.AppImage
./powershell-6.0.0-x86_64.AppImage
```

<span data-ttu-id="73a23-216">[AppImage][] umożliwia uruchamianie programu PowerShell bez jej instalowania.</span><span class="sxs-lookup"><span data-stu-id="73a23-216">The [AppImage][] lets you run PowerShell without installing it.</span></span> <span data-ttu-id="73a23-217">Jest przenośnych aplikacji, która zawiera w jednym pakiecie spójnego środowiska PowerShell i jego zależności (w tym oprogramowanie .NET Core zależności systemu).</span><span class="sxs-lookup"><span data-stu-id="73a23-217">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span> <span data-ttu-id="73a23-218">Ten pakiet działa niezależnie od dystrybucji systemu Linux użytkownika, a jest jedną wartość binarną.</span><span class="sxs-lookup"><span data-stu-id="73a23-218">This package works independently of the user's Linux distribution, and is a single binary.</span></span>

[appimage]: http://appimage.org/

## <a name="macos-1012"></a><span data-ttu-id="73a23-220">macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="73a23-220">macOS 10.12</span></span>

### <a name="installation-via-homebrew-preferred---macos-1012"></a><span data-ttu-id="73a23-221">Instalacja za pomocą oprogramowania Homebrew (preferowane) - macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="73a23-221">Installation via Homebrew (preferred) - macOS 10.12</span></span>

<span data-ttu-id="73a23-222">[Homebrew] [ brew] jest brak Menedżer pakietów dla macOS.</span><span class="sxs-lookup"><span data-stu-id="73a23-222">[Homebrew][brew] is the missing package manager for macOS.</span></span> <span data-ttu-id="73a23-223">Jeśli `brew` nie znaleziono polecenia, należy zainstalować następujące Homebrew [zgodnie z instrukcjami][brew].</span><span class="sxs-lookup"><span data-stu-id="73a23-223">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="73a23-224">Po zainstalowaniu oprogramowania Homebrew Instalowanie programu PowerShell jest bardzo proste.</span><span class="sxs-lookup"><span data-stu-id="73a23-224">Once you've installed Homebrew, installing PowerShell is easy.</span></span> <span data-ttu-id="73a23-225">Najpierw zainstaluj [pojemnika transportowego Homebrew][cask], więc można zainstalować więcej pakietów:</span><span class="sxs-lookup"><span data-stu-id="73a23-225">First, install [Homebrew-Cask][cask], so you can install more packages:</span></span>

```sh
brew tap caskroom/cask
```

<span data-ttu-id="73a23-226">Teraz można zainstalować programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="73a23-226">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="73a23-227">Po udostępnieniu nowej wersji programu PowerShell, po prostu zaktualizuj wzory dla oprogramowania Homebrew i uaktualnienia programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="73a23-227">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask reinstall powershell
```

> <span data-ttu-id="73a23-228">Uwaga: z powodu [ten problem w pojemnika transportowego](https://github.com/caskroom/homebrew-cask/issues/29301), musisz obecnie wykonać reinstall do uaktualnienia.</span><span class="sxs-lookup"><span data-stu-id="73a23-228">Note: because of [this issue in Cask](https://github.com/caskroom/homebrew-cask/issues/29301), you currently have to do a reinstall to upgrade.</span></span>

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download---macos-1012"></a><span data-ttu-id="73a23-229">Instalacja za pośrednictwem bezpośredniego pobieranie - macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="73a23-229">Installation via Direct Download - macOS 10.12</span></span>

<span data-ttu-id="73a23-230">Przy użyciu macOS 10.12, Pobierz pakiet PKG `powershell-6.0.0-osx.10.12-x64.pkg` z [zwalnia][] strony na maszynie macOS.</span><span class="sxs-lookup"><span data-stu-id="73a23-230">Using macOS 10.12, download the PKG package `powershell-6.0.0-osx.10.12-x64.pkg` from the [releases][] page onto the macOS machine.</span></span>

<span data-ttu-id="73a23-231">Kliknij dwukrotnie plik i postępuj zgodnie z monitami albo zainstalować go z terminala:</span><span class="sxs-lookup"><span data-stu-id="73a23-231">Either double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.0-osx.10.12-x64.pkg -target /
```

### <a name="uninstallation---macos-1012"></a><span data-ttu-id="73a23-232">Dezinstalacja - macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="73a23-232">Uninstallation - macOS 10.12</span></span>

<span data-ttu-id="73a23-233">Po zainstalowaniu programu PowerShell z oprogramowania Homebrew dezinstalacji jest łatwe:</span><span class="sxs-lookup"><span data-stu-id="73a23-233">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="73a23-234">Po zainstalowaniu programu PowerShell za pomocą bezpośredniego pobierania programu PowerShell musi zostać usunięte ręcznie:</span><span class="sxs-lookup"><span data-stu-id="73a23-234">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="73a23-235">Aby odinstalować dodatkowe ścieżki programu PowerShell (np. Ścieżka profilu użytkownika) można znaleźć pod adresem [ścieżki] [ paths] sekcji poniżej w tym dokumencie i usunąć żądaną ścieżki na `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="73a23-235">To uninstall the additional PowerShell paths (such as the user profile path) please see the [paths][paths] section below in this document and remove the desired the paths with `sudo rm`.</span></span> <span data-ttu-id="73a23-236">(Uwaga: nie jest to konieczne, jeśli podczas instalacji oprogramowania Homebrew.)</span><span class="sxs-lookup"><span data-stu-id="73a23-236">(Note: this is not necessary if you installed with Homebrew.)</span></span>

[paths]:#paths

## <a name="kali"></a><span data-ttu-id="73a23-237">Kali</span><span class="sxs-lookup"><span data-stu-id="73a23-237">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="73a23-238">Instalacja</span><span class="sxs-lookup"><span data-stu-id="73a23-238">Installation</span></span>

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="73a23-239">Uruchom program PowerShell w najnowszej Kali (Kali przewijane GNU/Linux) bez instalowania go</span><span class="sxs-lookup"><span data-stu-id="73a23-239">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.0-x86_64.AppImage

# Start PowerShell
./powershell-6.0.0-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="73a23-240">Dezinstalacja - Kali</span><span class="sxs-lookup"><span data-stu-id="73a23-240">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell-6.0.0-x86_64.AppImage
```

## <a name="raspbian"></a><span data-ttu-id="73a23-241">Raspbian</span><span class="sxs-lookup"><span data-stu-id="73a23-241">Raspbian</span></span>

<span data-ttu-id="73a23-242">Obecnie programu PowerShell jest obsługiwana tylko na Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="73a23-242">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

### <a name="installation"></a><span data-ttu-id="73a23-243">Instalacja</span><span class="sxs-lookup"><span data-stu-id="73a23-243">Installation</span></span>

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

### <a name="uninstallation---raspbian"></a><span data-ttu-id="73a23-244">Dezinstalacja - Raspbian</span><span class="sxs-lookup"><span data-stu-id="73a23-244">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="73a23-245">Archiwa binarne</span><span class="sxs-lookup"><span data-stu-id="73a23-245">Binary Archives</span></span>

<span data-ttu-id="73a23-246">Dane binarne środowiska PowerShell `tar.gz` archiwa są udostępniane dla macOS i platformy Linux, aby włączyć zaawansowanych scenariuszach wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="73a23-246">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="73a23-247">Zależności</span><span class="sxs-lookup"><span data-stu-id="73a23-247">Dependencies</span></span>

<span data-ttu-id="73a23-248">Dla systemu Linux programu PowerShell kompilacje przenośne pliki binarne dla wszystkich dystrybucje systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="73a23-248">For Linux, PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="73a23-249">Jednak różnych zależności na różne dystrybucje wymaga środowiska uruchomieniowego .NET Core i dlatego programu PowerShell jest taka sama.</span><span class="sxs-lookup"><span data-stu-id="73a23-249">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="73a23-250">W poniższej tabeli przedstawiono zależności .NET Core 2.0 na różnych dystrybucje systemu Linux, które oficjalnie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="73a23-250">The following chart shows the .NET Core 2.0 dependencies on different Linux distributions that are officially supported.</span></span>

| <span data-ttu-id="73a23-251">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="73a23-251">OS</span></span>                 | <span data-ttu-id="73a23-252">Zależności</span><span class="sxs-lookup"><span data-stu-id="73a23-252">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="73a23-253">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="73a23-253">Ubuntu 14.04</span></span>       | <span data-ttu-id="73a23-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="73a23-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="73a23-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="73a23-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="73a23-256">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="73a23-256">Ubuntu 16.04</span></span>       | <span data-ttu-id="73a23-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="73a23-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="73a23-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="73a23-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="73a23-259">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="73a23-259">Ubuntu 17.04</span></span>       | <span data-ttu-id="73a23-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="73a23-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="73a23-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="73a23-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="73a23-262">Debian 8 (Joasia)</span><span class="sxs-lookup"><span data-stu-id="73a23-262">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="73a23-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="73a23-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="73a23-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="73a23-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="73a23-265">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="73a23-265">Debian 9 (Stretch)</span></span> | <span data-ttu-id="73a23-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="73a23-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="73a23-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="73a23-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="73a23-268">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="73a23-268">CentOS 7</span></span> <br> <span data-ttu-id="73a23-269">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="73a23-269">Oracle Linux 7</span></span> <br> <span data-ttu-id="73a23-270">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="73a23-270">RHEL 7</span></span> <br> <span data-ttu-id="73a23-271">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="73a23-271">OpenSUSE 42.2</span></span> <br> <span data-ttu-id="73a23-272">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="73a23-272">Fedora 25</span></span> | <span data-ttu-id="73a23-273">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="73a23-273">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="73a23-274">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="73a23-274">Fedora 26</span></span>          | <span data-ttu-id="73a23-275">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="73a23-275">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="73a23-276">W celu wdrożenia plików binarnych programu PowerShell na dystrybucje systemu Linux, które nie są obsługiwane oficjalnie, musisz zainstalować zależności niezbędne dla docelowego systemu operacyjnego w oddzielne kroki.</span><span class="sxs-lookup"><span data-stu-id="73a23-276">In order to deploy PowerShell binaries on Linux distributions that are not officially supported, you would need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="73a23-277">Na przykład naszych [plik dockerfile Amazon Linux] [ amazon-dockerfile] najpierw instaluje zależności, a następnie wyodrębnia systemu Linux `tar.gz` archiwum.</span><span class="sxs-lookup"><span data-stu-id="73a23-277">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="73a23-278">Instalacja — archiwa binarne</span><span class="sxs-lookup"><span data-stu-id="73a23-278">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="73a23-279">Linux</span><span class="sxs-lookup"><span data-stu-id="73a23-279">Linux</span></span>

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

#### <a name="macos"></a><span data-ttu-id="73a23-280">macOS</span><span class="sxs-lookup"><span data-stu-id="73a23-280">macOS</span></span>

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

### <a name="uninstallation---binary-archives"></a><span data-ttu-id="73a23-281">Dezinstalacja - archiwa binarne</span><span class="sxs-lookup"><span data-stu-id="73a23-281">Uninstallation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="73a23-282">Linux</span><span class="sxs-lookup"><span data-stu-id="73a23-282">Linux</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

#### <a name="macos"></a><span data-ttu-id="73a23-283">macOS</span><span class="sxs-lookup"><span data-stu-id="73a23-283">macOS</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="73a23-284">Ścieżki</span><span class="sxs-lookup"><span data-stu-id="73a23-284">Paths</span></span>

* <span data-ttu-id="73a23-285">`$PSHOME`jest`/opt/microsoft/powershell/6.0.0/`</span><span class="sxs-lookup"><span data-stu-id="73a23-285">`$PSHOME` is `/opt/microsoft/powershell/6.0.0/`</span></span>
* <span data-ttu-id="73a23-286">Profile użytkowników będą odczytywane z`~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="73a23-286">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="73a23-287">Domyślne profile będą odczytywane z`$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="73a23-287">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="73a23-288">Moduły użytkownika będą odczytywane z`~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="73a23-288">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="73a23-289">Udostępniony moduły będą odczytywane z`/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="73a23-289">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="73a23-290">Domyślne moduły będą odczytywane z`$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="73a23-290">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="73a23-291">Historia PSReadline zostanie zarejestrowana w celu`~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="73a23-291">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="73a23-292">Profile przestrzegać konfiguracji na hosta w programie PowerShell, więc domyślne profile specyficzne dla hosta istnieje w `Microsoft.PowerShell_profile.ps1` w tej samej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="73a23-292">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="73a23-293">W systemie Linux i macOS [specyfikacji katalogu Base XDG] [ xdg-bds] jest przestrzegana.</span><span class="sxs-lookup"><span data-stu-id="73a23-293">On Linux and macOS, the [XDG Base Directory Specification][xdg-bds] is respected.</span></span>

<span data-ttu-id="73a23-294">Należy pamiętać, że ponieważ macOS jest typem pochodnym BSD, zamiast `/opt`, prefiks używany jest `/usr/local`.</span><span class="sxs-lookup"><span data-stu-id="73a23-294">Note that because macOS is a derivation of BSD, instead of `/opt`, the prefix used is `/usr/local`.</span></span> <span data-ttu-id="73a23-295">W związku z tym `$PSHOME` jest `/usr/local/microsoft/powershell/6.0.0/`, i Utwórz Link symboliczny znajduje się w `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="73a23-295">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.0/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

[zwalnia]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
