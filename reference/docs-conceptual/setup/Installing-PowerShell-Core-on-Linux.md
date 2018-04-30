# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="4a438-101">Instalowanie programu PowerShell Core w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="4a438-101">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="4a438-102">Obsługuje [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04] [ u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25 ] [ fed25], [Fedora 26][fed26], i [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="4a438-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26], and [Arch Linux][arch].</span></span>

<span data-ttu-id="4a438-103">Dla dystrybucje systemu Linux, które nie są obsługiwane oficjalnie, można spróbować użyć [PowerShell AppImage][lai].</span><span class="sxs-lookup"><span data-stu-id="4a438-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="4a438-104">Można też spróbować wdrożenia plików binarnych programu PowerShell bezpośrednio przy użyciu systemu Linux [ `tar.gz` archiwum][tar], ale należy skonfigurować wymagane zależności, oparte na system operacyjny w oddzielne kroki.</span><span class="sxs-lookup"><span data-stu-id="4a438-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="4a438-105">Wszystkie pakiety są dostępne w naszej witrynie GitHub [zwalnia][] strony.</span><span class="sxs-lookup"><span data-stu-id="4a438-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="4a438-106">Po zainstalowaniu pakietu `pwsh` z terminalu.</span><span class="sxs-lookup"><span data-stu-id="4a438-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

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
[tar]: #binary-archives

## <a name="ubuntu-1404"></a><span data-ttu-id="4a438-107">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="4a438-107">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="4a438-108">Instalacja za pośrednictwem repozytorium pakietów - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="4a438-108">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="4a438-109">Podstawowe programu PowerShell dla systemu Linux jest publikowany dla repozytoriów pakietu do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="4a438-109">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="4a438-110">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="4a438-110">This is the preferred method.</span></span>

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

<span data-ttu-id="4a438-111">Jako administratora Zarejestruj repozytorium firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4a438-111">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="4a438-112">Następnie należy po prostu użyć `sudo apt-get upgrade powershell` aktualizacji instalacji.</span><span class="sxs-lookup"><span data-stu-id="4a438-112">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="4a438-113">Instalacja za pośrednictwem bezpośredniego pobierania - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="4a438-113">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="4a438-114">Pobierz pakiet Debian `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` z [zwalnia][] strony na maszynie Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="4a438-114">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="4a438-115">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4a438-115">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="4a438-116">Należy pamiętać, że `dpkg -i` zakończy się niepowodzeniem z zależności unmet; następne polecenie `apt-get install -f` rozpoznaje je, a następnie kończy Konfigurowanie pakietu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a438-116">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="4a438-117">Dezinstalacja - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="4a438-117">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="4a438-118">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="4a438-118">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="4a438-119">Instalacja za pośrednictwem repozytorium pakietów - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="4a438-119">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="4a438-120">Podstawowe programu PowerShell dla systemu Linux jest publikowany dla repozytoriów pakietu do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="4a438-120">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="4a438-121">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="4a438-121">This is the preferred method.</span></span>

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

<span data-ttu-id="4a438-122">Po zarejestrowaniu repozytorium Microsoft raz jako administratora, od, wystarczy użyć `sudo apt-get upgrade powershell` go zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="4a438-122">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="4a438-123">Instalacja za pośrednictwem bezpośredniego pobierania - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="4a438-123">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="4a438-124">Pobierz pakiet Debian `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` z [zwalnia][] strony na maszynie Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="4a438-124">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="4a438-125">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4a438-125">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="4a438-126">Należy pamiętać, że `dpkg -i` zakończy się niepowodzeniem z zależności unmet; następne polecenie `apt-get install -f` rozpoznaje je, a następnie kończy Konfigurowanie pakietu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a438-126">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="4a438-127">Dezinstalacja - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="4a438-127">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a><span data-ttu-id="4a438-128">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="4a438-128">Ubuntu 17.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1704"></a><span data-ttu-id="4a438-129">Instalacja za pośrednictwem repozytorium pakietów - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="4a438-129">Installation via Package Repository - Ubuntu 17.04</span></span>

<span data-ttu-id="4a438-130">Podstawowe programu PowerShell dla systemu Linux jest publikowany dla repozytoriów pakietu do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="4a438-130">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="4a438-131">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="4a438-131">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/17.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="4a438-132">Po zarejestrowaniu repozytorium Microsoft raz jako administratora, od, wystarczy użyć `sudo apt-get upgrade powershell` go zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="4a438-132">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1704"></a><span data-ttu-id="4a438-133">Instalacja za pośrednictwem bezpośredniego pobierania - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="4a438-133">Installation via Direct Download - Ubuntu 17.04</span></span>

<span data-ttu-id="4a438-134">Pobierz pakiet Debian `powershell_6.0.2-1.ubuntu.17.04_amd64.deb` z [zwalnia][] strony na maszynie Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="4a438-134">Download the Debian package `powershell_6.0.2-1.ubuntu.17.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="4a438-135">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4a438-135">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="4a438-136">Należy pamiętać, że `dpkg -i` zakończy się niepowodzeniem z zależności unmet; następne polecenie `apt-get install -f` rozpoznaje je, a następnie kończy Konfigurowanie pakietu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a438-136">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1704"></a><span data-ttu-id="4a438-137">Dezinstalacja - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="4a438-137">Uninstallation - Ubuntu 17.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="4a438-138">Debian 8</span><span class="sxs-lookup"><span data-stu-id="4a438-138">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="4a438-139">Instalacja za pośrednictwem repozytorium pakietów - Debian 8</span><span class="sxs-lookup"><span data-stu-id="4a438-139">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="4a438-140">Podstawowe programu PowerShell dla systemu Linux jest publikowany dla repozytoriów pakietu do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="4a438-140">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="4a438-141">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="4a438-141">This is the preferred method.</span></span>

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

<span data-ttu-id="4a438-142">Po zarejestrowaniu repozytorium Microsoft raz jako administratora, od, wystarczy użyć `sudo apt-get upgrade powershell` go zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="4a438-142">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="4a438-143">Instalacja za pośrednictwem bezpośredniego pobierania - Debian 8</span><span class="sxs-lookup"><span data-stu-id="4a438-143">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="4a438-144">Pobierz pakiet Debian `powershell_6.0.2-1.debian.8_amd64.deb` z [zwalnia][] strony na Debian maszyny.</span><span class="sxs-lookup"><span data-stu-id="4a438-144">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="4a438-145">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4a438-145">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="4a438-146">Należy pamiętać, że `dpkg -i` zakończy się niepowodzeniem z unmet zależności.</span><span class="sxs-lookup"><span data-stu-id="4a438-146">Please note that `dpkg -i` will fail with unmet dependencies.</span></span>
> <span data-ttu-id="4a438-147">Następne polecenie `apt-get install -f` rozpoznaje je, a następnie kończy Konfigurowanie pakietu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a438-147">The next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="4a438-148">Dezinstalacja - Debian 8</span><span class="sxs-lookup"><span data-stu-id="4a438-148">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="4a438-149">Debian 9</span><span class="sxs-lookup"><span data-stu-id="4a438-149">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="4a438-150">Instalacja za pośrednictwem repozytorium pakietów - Debian 9</span><span class="sxs-lookup"><span data-stu-id="4a438-150">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="4a438-151">Podstawowe programu PowerShell dla systemu Linux jest publikowany dla repozytoriów pakietu do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="4a438-151">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="4a438-152">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="4a438-152">This is the preferred method.</span></span>

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

<span data-ttu-id="4a438-153">Po zarejestrowaniu repozytorium Microsoft raz jako administratora, od, wystarczy użyć `sudo apt-get upgrade powershell` go zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="4a438-153">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="4a438-154">Instalacja za pośrednictwem bezpośredniego pobierania - Debian 9</span><span class="sxs-lookup"><span data-stu-id="4a438-154">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="4a438-155">Pobierz pakiet Debian `powershell_6.0.2-1.debian.9_amd64.deb` z [zwalnia][] strony na Debian maszyny.</span><span class="sxs-lookup"><span data-stu-id="4a438-155">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="4a438-156">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4a438-156">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="4a438-157">Należy pamiętać, że `dpkg -i` zakończy się niepowodzeniem z unmet zależności.</span><span class="sxs-lookup"><span data-stu-id="4a438-157">Please note that `dpkg -i` will fail with unmet dependencies.</span></span>
> <span data-ttu-id="4a438-158">Następne polecenie `apt-get install -f` rozpoznaje je, a następnie kończy Konfigurowanie pakietu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a438-158">The next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-9"></a><span data-ttu-id="4a438-159">Dezinstalacja - Debian 9</span><span class="sxs-lookup"><span data-stu-id="4a438-159">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="4a438-160">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="4a438-160">CentOS 7</span></span>

> <span data-ttu-id="4a438-161">Ten pakiet jest również działa na Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="4a438-161">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="4a438-162">Instalacja za pośrednictwem repozytorium pakietów (preferowane) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="4a438-162">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="4a438-163">Podstawowe programu PowerShell dla systemu Linux jest publikowany oficjalnego repozytoria Microsoft easy instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="4a438-163">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="4a438-164">Po zarejestrowaniu repozytorium Microsoft raz jako administratora, wystarczy użyć `sudo yum update powershell` aktualizacji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a438-164">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="4a438-165">Instalacja za pośrednictwem bezpośredniego pobierania - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="4a438-165">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="4a438-166">Przy użyciu [CentOS 7][], Pobierz pakiet RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` z [zwalnia][] strony na maszynie CentOS.</span><span class="sxs-lookup"><span data-stu-id="4a438-166">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="4a438-167">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4a438-167">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="4a438-168">Można także zainstalować RPM bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="4a438-168">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="4a438-169">Dezinstalacja - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="4a438-169">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="4a438-171">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="4a438-171">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="4a438-172">Instalacja za pośrednictwem repozytorium pakietów (preferowane) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="4a438-172">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="4a438-173">Podstawowe programu PowerShell dla systemu Linux jest publikowany oficjalnego repozytoria Microsoft easy instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="4a438-173">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="4a438-174">Po zarejestrowaniu repozytorium Microsoft raz jako administratora, wystarczy użyć `sudo yum update powershell` aktualizacji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a438-174">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="4a438-175">Instalacja za pośrednictwem bezpośredniego pobierania - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="4a438-175">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="4a438-176">Pobierz pakiet RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` z [zwalnia][] strony na maszynie Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="4a438-176">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="4a438-177">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4a438-177">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="4a438-178">Można także zainstalować RPM bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="4a438-178">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="4a438-179">Dezinstalacja - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="4a438-179">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="4a438-180">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="4a438-180">OpenSUSE 42.2</span></span>

> [!NOTE]
> <span data-ttu-id="4a438-181">Podczas instalacji podstawowej programu PowerShell `zypper` może Zgłoś następujący błąd:</span><span class="sxs-lookup"><span data-stu-id="4a438-181">When installing PowerShell Core, `zypper` may report the following error:</span></span>
>
> ```Output
> Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
>  Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
>  Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
> ```
>
> <span data-ttu-id="4a438-182">W takim przypadku sprawdź, czy zgodna `libcurl` biblioteki występuje przez sprawdzenie, czy następujące polecenie pokazuje `libcurl4` pakietu jako zainstalowane:</span><span class="sxs-lookup"><span data-stu-id="4a438-182">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>
>
> ```sh
> zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
> ```
>
> <span data-ttu-id="4a438-183">Następnie wybierz pozycję `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` rozwiązania podczas instalowania pakietu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a438-183">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="4a438-184">Instalacja za pośrednictwem repozytorium pakietów (preferowane) - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="4a438-184">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="4a438-185">Podstawowe programu PowerShell dla systemu Linux jest publikowany oficjalnego repozytoria Microsoft easy instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="4a438-185">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="4a438-186">Instalacja za pośrednictwem bezpośredniego pobierania - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="4a438-186">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="4a438-187">Pobierz pakiet RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` z [zwalnia][] strony na maszynie OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="4a438-187">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="4a438-188">Można także zainstalować RPM bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="4a438-188">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="4a438-189">Dezinstalacja - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="4a438-189">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora-25"></a><span data-ttu-id="4a438-190">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="4a438-190">Fedora 25</span></span>

### <a name="installation-via-package-repository-preferred---fedora-25"></a><span data-ttu-id="4a438-191">Instalacja za pośrednictwem repozytorium pakietów (preferowane) - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="4a438-191">Installation via Package Repository (preferred) - Fedora 25</span></span>

<span data-ttu-id="4a438-192">Podstawowe programu PowerShell dla systemu Linux jest publikowany oficjalnego repozytoria Microsoft easy instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="4a438-192">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-25"></a><span data-ttu-id="4a438-193">Instalacja za pośrednictwem bezpośredniego pobierania - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="4a438-193">Installation via Direct Download - Fedora 25</span></span>

<span data-ttu-id="4a438-194">Pobierz pakiet RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` z [zwalnia][] strony na maszynie Fedora.</span><span class="sxs-lookup"><span data-stu-id="4a438-194">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="4a438-195">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4a438-195">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="4a438-196">Można także zainstalować RPM bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="4a438-196">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a><span data-ttu-id="4a438-197">Dezinstalacja - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="4a438-197">Uninstallation - Fedora 25</span></span>

```sh
sudo dnf remove powershell
```

## <a name="fedora-26"></a><span data-ttu-id="4a438-198">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="4a438-198">Fedora 26</span></span>

### <a name="installation-via-package-repository-preferred---fedora-26"></a><span data-ttu-id="4a438-199">Instalacja za pośrednictwem repozytorium pakietów (preferowane) - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="4a438-199">Installation via Package Repository (preferred) - Fedora 26</span></span>

<span data-ttu-id="4a438-200">Podstawowe programu PowerShell dla systemu Linux jest publikowany oficjalnego repozytoria Microsoft easy instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="4a438-200">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-26"></a><span data-ttu-id="4a438-201">Instalacja za pośrednictwem bezpośredniego pobierania - 26 Fedora</span><span class="sxs-lookup"><span data-stu-id="4a438-201">Installation via Direct Download - Fedora 26</span></span>

<span data-ttu-id="4a438-202">Pobierz pakiet RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` z [zwalnia][] strony na maszynie Fedora.</span><span class="sxs-lookup"><span data-stu-id="4a438-202">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="4a438-203">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4a438-203">Then execute the following in the terminal:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="4a438-204">Można także zainstalować RPM bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="4a438-204">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a><span data-ttu-id="4a438-205">Dezinstalacja - 26 Fedora</span><span class="sxs-lookup"><span data-stu-id="4a438-205">Uninstallation - Fedora 26</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="4a438-206">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="4a438-206">Arch Linux</span></span>

<span data-ttu-id="4a438-207">Środowisko PowerShell jest dostępny z [Arch Linux][] użytkownika repozytorium (AUR).</span><span class="sxs-lookup"><span data-stu-id="4a438-207">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="4a438-208">Może być kompilowana przy użyciu [najnowszej oznakowane zlecenia][arch-release]</span><span class="sxs-lookup"><span data-stu-id="4a438-208">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="4a438-209">Mogą być kompilowane z [najnowszym zatwierdzeniu do wzorca][arch-git]</span><span class="sxs-lookup"><span data-stu-id="4a438-209">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="4a438-210">Można zainstalować, za pomocą [najnowszej wersji pliku binarnego][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="4a438-210">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="4a438-211">Pakiety w AUR Wspólnotę utrzymane — nie jest oficjalną obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="4a438-211">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="4a438-212">Aby uzyskać więcej informacji na temat instalowania pakietów z AUR, zobacz [wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) lub społeczności [plik DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="4a438-212">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="4a438-214">AppImage systemu Linux</span><span class="sxs-lookup"><span data-stu-id="4a438-214">Linux AppImage</span></span>

<span data-ttu-id="4a438-215">Przy użyciu najnowszych dystrybucji systemu Linux, Pobierz AppImage `powershell-6.0.1-x86_64.AppImage` z [zwalnia][] strony na komputerze systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="4a438-215">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="4a438-216">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4a438-216">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="4a438-217">[AppImage][] umożliwia uruchamianie programu PowerShell bez jej instalowania.</span><span class="sxs-lookup"><span data-stu-id="4a438-217">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="4a438-218">Jest przenośnych aplikacji, która zawiera w jednym pakiecie spójnego środowiska PowerShell i jego zależności (w tym oprogramowanie .NET Core zależności systemu).</span><span class="sxs-lookup"><span data-stu-id="4a438-218">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="4a438-219">Ten pakiet jest jedną wartość binarną, która działa niezależnie od dystrybucji systemu Linux przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4a438-219">This package  is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="4a438-221">Kali</span><span class="sxs-lookup"><span data-stu-id="4a438-221">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="4a438-222">Instalacja</span><span class="sxs-lookup"><span data-stu-id="4a438-222">Installation</span></span>

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="4a438-223">Uruchom program PowerShell w najnowszej Kali (Kali przewijane GNU/Linux) bez instalowania go</span><span class="sxs-lookup"><span data-stu-id="4a438-223">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="4a438-224">Dezinstalacja - Kali</span><span class="sxs-lookup"><span data-stu-id="4a438-224">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="4a438-225">Raspbian</span><span class="sxs-lookup"><span data-stu-id="4a438-225">Raspbian</span></span>

<span data-ttu-id="4a438-226">Obecnie programu PowerShell jest obsługiwana tylko na Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="4a438-226">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="4a438-227">Również środowisko CoreCLR (i w związku z tym podstawowe programu PowerShell) będą działać tylko na urządzeniach Pi 2 i Pi 3 jako inne urządzenia, tak samo, jak [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), nieobsługiwany procesor.</span><span class="sxs-lookup"><span data-stu-id="4a438-227">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="4a438-228">Pobierz [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) i postępuj zgodnie z [instrukcje dotyczące instalacji](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) uzyskać na Twoje Pi.</span><span class="sxs-lookup"><span data-stu-id="4a438-228">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="4a438-229">Instalacja</span><span class="sxs-lookup"><span data-stu-id="4a438-229">Installation</span></span>

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

<span data-ttu-id="4a438-230">Opcjonalnie można utworzyć łącza symbolicznego, aby można było uruchomić program PowerShell bez określenia ścieżki do "pwsh" binarne</span><span class="sxs-lookup"><span data-stu-id="4a438-230">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="4a438-231">Dezinstalacja - Raspbian</span><span class="sxs-lookup"><span data-stu-id="4a438-231">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="4a438-232">Archiwa binarne</span><span class="sxs-lookup"><span data-stu-id="4a438-232">Binary Archives</span></span>

<span data-ttu-id="4a438-233">Dane binarne środowiska PowerShell `tar.gz` archiwa są udostępniane dla platform Linux umożliwić wdrożenie zaawansowanych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="4a438-233">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="4a438-234">Zależności</span><span class="sxs-lookup"><span data-stu-id="4a438-234">Dependencies</span></span>

<span data-ttu-id="4a438-235">PowerShell kompilacje przenośne pliki binarne dla wszystkich dystrybucje systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="4a438-235">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="4a438-236">Jednak różnych zależności na różne dystrybucje wymaga środowiska uruchomieniowego .NET Core i dlatego programu PowerShell jest taka sama.</span><span class="sxs-lookup"><span data-stu-id="4a438-236">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="4a438-237">W poniższej tabeli przedstawiono zależności .NET Core 2.0 oficjalnie obsługiwanych w różnych dystrybucje systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="4a438-237">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="4a438-238">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="4a438-238">OS</span></span>                 | <span data-ttu-id="4a438-239">Zależności</span><span class="sxs-lookup"><span data-stu-id="4a438-239">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="4a438-240">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="4a438-240">Ubuntu 14.04</span></span>       | <span data-ttu-id="4a438-241">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="4a438-241">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="4a438-242">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="4a438-242">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="4a438-243">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="4a438-243">Ubuntu 16.04</span></span>       | <span data-ttu-id="4a438-244">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="4a438-244">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="4a438-245">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="4a438-245">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="4a438-246">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="4a438-246">Ubuntu 17.04</span></span>       | <span data-ttu-id="4a438-247">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="4a438-247">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="4a438-248">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="4a438-248">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="4a438-249">Debian 8 (Joasia)</span><span class="sxs-lookup"><span data-stu-id="4a438-249">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="4a438-250">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="4a438-250">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="4a438-251">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="4a438-251">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="4a438-252">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="4a438-252">Debian 9 (Stretch)</span></span> | <span data-ttu-id="4a438-253">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="4a438-253">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="4a438-254">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="4a438-254">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="4a438-255">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="4a438-255">CentOS 7</span></span> <br> <span data-ttu-id="4a438-256">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="4a438-256">Oracle Linux 7</span></span> <br> <span data-ttu-id="4a438-257">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="4a438-257">RHEL 7</span></span> <br> <span data-ttu-id="4a438-258">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="4a438-258">OpenSUSE 42.2</span></span> <br> <span data-ttu-id="4a438-259">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="4a438-259">Fedora 25</span></span> | <span data-ttu-id="4a438-260">libunwind, libcurl, biblioteki openssl, libicu</span><span class="sxs-lookup"><span data-stu-id="4a438-260">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="4a438-261">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="4a438-261">Fedora 26</span></span>          | <span data-ttu-id="4a438-262">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="4a438-262">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="4a438-263">Aby wdrożyć pliki binarne programu PowerShell na dystrybucje systemu Linux, które nie są obsługiwane oficjalnie, należy zainstalować zależności niezbędne dla docelowego systemu operacyjnego w oddzielne kroki.</span><span class="sxs-lookup"><span data-stu-id="4a438-263">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="4a438-264">Na przykład naszych [plik dockerfile Amazon Linux] [ amazon-dockerfile] najpierw instaluje zależności, a następnie wyodrębnia systemu Linux `tar.gz` archiwum.</span><span class="sxs-lookup"><span data-stu-id="4a438-264">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="4a438-265">Instalacja — archiwa binarne</span><span class="sxs-lookup"><span data-stu-id="4a438-265">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="4a438-266">Linux</span><span class="sxs-lookup"><span data-stu-id="4a438-266">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="4a438-267">Odinstalowanie archiwa binarne</span><span class="sxs-lookup"><span data-stu-id="4a438-267">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="4a438-268">Ścieżki</span><span class="sxs-lookup"><span data-stu-id="4a438-268">Paths</span></span>

* <span data-ttu-id="4a438-269">`$PSHOME` jest `/opt/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="4a438-269">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="4a438-270">Profile użytkowników będą odczytywane z `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="4a438-270">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="4a438-271">Domyślne profile będą odczytywane z `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="4a438-271">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="4a438-272">Moduły użytkownika będą odczytywane z `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="4a438-272">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="4a438-273">Udostępniony moduły będą odczytywane z `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="4a438-273">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="4a438-274">Domyślne moduły będą odczytywane z `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="4a438-274">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="4a438-275">Historia PSReadline zostanie zarejestrowana w celu `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="4a438-275">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="4a438-276">Profile przestrzegać konfiguracji na hosta w programie PowerShell, więc domyślne profile specyficzne dla hosta istnieje w `Microsoft.PowerShell_profile.ps1` w tej samej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="4a438-276">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="4a438-277">PowerShell szanuje [specyfikacji katalogu Base XDG] [ xdg-bds] w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="4a438-277">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[zwalnia]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
