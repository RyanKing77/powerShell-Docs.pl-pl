# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="1d35c-101">Instalowanie programu PowerShell Core w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="1d35c-101">Installing PowerShell Core on Linux</span></span>

Supports <bpt id="p1">[</bpt>Ubuntu 14.04<ept id="p1">]</ept><bpt id="p2">[</bpt><ept id="p2">u14]</ept>, <bpt id="p3">[</bpt>Ubuntu 16.04<ept id="p3">]</ept><bpt id="p4">[</bpt><ept id="p4">u16]</ept>, <bpt id="p5">[</bpt>Ubuntu 17.04<ept id="p5">]</ept><bpt id="p6">[</bpt><ept id="p6">u17]</ept>, <bpt id="p7">[</bpt>Debian 8<ept id="p7">]</ept><bpt id="p8">[</bpt><ept id="p8">deb8]</ept>, <bpt id="p9">[</bpt>Debian 9<ept id="p9">]</ept><bpt id="p10">[</bpt><ept id="p10">deb9]</ept>, <bpt id="p11">[</bpt>CentOS 7<ept id="p11">]</ept><bpt id="p12">[</bpt><ept id="p12">cos]</ept>, <bpt id="p13">[</bpt>Red Hat Enterprise Linux (RHEL) 7<ept id="p13">]</ept><bpt id="p14">[</bpt><ept id="p14">rhel7]</ept>, <bpt id="p15">[</bpt>OpenSUSE 42.2<ept id="p15">]</ept><bpt id="p16">[</bpt><ept id="p16">opensuse]</ept>, <bpt id="p17">[</bpt>Fedora 27<ept id="p17">]</ept><bpt id="p18">[</bpt><ept id="p18">fedora]</ept>, <bpt id="p19">[</bpt>Fedora 28<ept id="p19">]</ept><bpt id="p20">[</bpt><ept id="p20">fedora]</ept>, and <bpt id="p21">[</bpt>Arch Linux<ept id="p21">]</ept><bpt id="p22">[</bpt><ept id="p22">arch]</ept>.

<span data-ttu-id="1d35c-103">Dla dystrybucje systemu Linux, które nie są obsługiwane oficjalnie, można spróbować użyć [PowerShell AppImage][lai].</span><span class="sxs-lookup"><span data-stu-id="1d35c-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="1d35c-104">Można też spróbować wdrożenia plików binarnych programu PowerShell bezpośrednio przy użyciu systemu Linux [ `tar.gz` archiwum][tar], ale należy skonfigurować wymagane zależności, oparte na system operacyjny w oddzielne kroki.</span><span class="sxs-lookup"><span data-stu-id="1d35c-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="1d35c-105">Wszystkie pakiety są dostępne w naszej witrynie GitHub [Wersje][] strony.</span><span class="sxs-lookup"><span data-stu-id="1d35c-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="1d35c-106">Po zainstalowaniu pakietu `pwsh` z terminalu.</span><span class="sxs-lookup"><span data-stu-id="1d35c-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1704
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fedora]: #fedora
[arch]: #arch-linux
[lai]: #linux-appimage
[tar]: #binary-archives

## <a name="ubuntu-1404"></a><span data-ttu-id="1d35c-107">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="1d35c-107">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="1d35c-108">Instalacja za pośrednictwem repozytorium pakietów - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="1d35c-108">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="1d35c-109">Podstawowe programu PowerShell dla systemu Linux jest publikowany dla repozytoriów pakietu do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="1d35c-109">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="1d35c-110">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="1d35c-110">This is the preferred method.</span></span>

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

<span data-ttu-id="1d35c-111">Jako administratora Zarejestruj repozytorium firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1d35c-111">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="1d35c-112">Następnie należy po prostu użyć `sudo apt-get upgrade powershell` aktualizacji instalacji.</span><span class="sxs-lookup"><span data-stu-id="1d35c-112">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="1d35c-113">Instalacja za pośrednictwem bezpośredniego pobierania - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="1d35c-113">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="1d35c-114">Pobierz pakiet Debian `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` z [Wersje][] strony na maszynie Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="1d35c-114">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="1d35c-115">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="1d35c-115">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="1d35c-116">Należy pamiętać, że `dpkg -i` zakończy się niepowodzeniem z zależności unmet; następne polecenie `apt-get install -f` rozpoznaje je, a następnie kończy Konfigurowanie pakietu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d35c-116">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="1d35c-117">Dezinstalacja - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="1d35c-117">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="1d35c-118">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="1d35c-118">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="1d35c-119">Instalacja za pośrednictwem repozytorium pakietów - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="1d35c-119">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="1d35c-120">Podstawowe programu PowerShell dla systemu Linux jest publikowany dla repozytoriów pakietu do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="1d35c-120">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="1d35c-121">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="1d35c-121">This is the preferred method.</span></span>

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

<span data-ttu-id="1d35c-122">Po zarejestrowaniu repozytorium Microsoft raz jako administratora, od, wystarczy użyć `sudo apt-get upgrade powershell` go zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="1d35c-122">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="1d35c-123">Instalacja za pośrednictwem bezpośredniego pobierania - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="1d35c-123">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="1d35c-124">Pobierz pakiet Debian `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` z [Wersje][] strony na maszynie Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="1d35c-124">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="1d35c-125">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="1d35c-125">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="1d35c-126">Należy pamiętać, że `dpkg -i` zakończy się niepowodzeniem z zależności unmet; następne polecenie `apt-get install -f` rozpoznaje je, a następnie kończy Konfigurowanie pakietu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d35c-126">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="1d35c-127">Dezinstalacja - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="1d35c-127">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a><span data-ttu-id="1d35c-128">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="1d35c-128">Ubuntu 17.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1704"></a><span data-ttu-id="1d35c-129">Instalacja za pośrednictwem repozytorium pakietów - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="1d35c-129">Installation via Package Repository - Ubuntu 17.04</span></span>

<span data-ttu-id="1d35c-130">Podstawowe programu PowerShell dla systemu Linux jest publikowany dla repozytoriów pakietu do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="1d35c-130">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="1d35c-131">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="1d35c-131">This is the preferred method.</span></span>

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

<span data-ttu-id="1d35c-132">Po zarejestrowaniu repozytorium Microsoft raz jako administratora, od, wystarczy użyć `sudo apt-get upgrade powershell` go zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="1d35c-132">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1704"></a><span data-ttu-id="1d35c-133">Instalacja za pośrednictwem bezpośredniego pobierania - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="1d35c-133">Installation via Direct Download - Ubuntu 17.04</span></span>

<span data-ttu-id="1d35c-134">Pobierz pakiet Debian `powershell_6.0.2-1.ubuntu.17.04_amd64.deb` z [Wersje][] strony na maszynie Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="1d35c-134">Download the Debian package `powershell_6.0.2-1.ubuntu.17.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="1d35c-135">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="1d35c-135">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="1d35c-136">Należy pamiętać, że `dpkg -i` zakończy się niepowodzeniem z zależności unmet; następne polecenie `apt-get install -f` rozpoznaje je, a następnie kończy Konfigurowanie pakietu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d35c-136">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1704"></a><span data-ttu-id="1d35c-137">Dezinstalacja - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="1d35c-137">Uninstallation - Ubuntu 17.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="1d35c-138">Debian 8</span><span class="sxs-lookup"><span data-stu-id="1d35c-138">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="1d35c-139">Instalacja za pośrednictwem repozytorium pakietów - Debian 8</span><span class="sxs-lookup"><span data-stu-id="1d35c-139">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="1d35c-140">Podstawowe programu PowerShell dla systemu Linux jest publikowany dla repozytoriów pakietu do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="1d35c-140">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="1d35c-141">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="1d35c-141">This is the preferred method.</span></span>

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

<span data-ttu-id="1d35c-142">Po zarejestrowaniu repozytorium Microsoft raz jako administratora, od, wystarczy użyć `sudo apt-get upgrade powershell` go zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="1d35c-142">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="1d35c-143">Instalacja za pośrednictwem bezpośredniego pobierania - Debian 8</span><span class="sxs-lookup"><span data-stu-id="1d35c-143">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="1d35c-144">Pobierz pakiet Debian `powershell_6.0.2-1.debian.8_amd64.deb` z [Wersje][] strony na Debian maszyny.</span><span class="sxs-lookup"><span data-stu-id="1d35c-144">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="1d35c-145">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="1d35c-145">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="1d35c-146">Należy pamiętać, że `dpkg -i` zakończy się niepowodzeniem z unmet zależności.</span><span class="sxs-lookup"><span data-stu-id="1d35c-146">Please note that `dpkg -i` will fail with unmet dependencies.</span></span>
> <span data-ttu-id="1d35c-147">Następne polecenie `apt-get install -f` rozpoznaje je, a następnie kończy Konfigurowanie pakietu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d35c-147">The next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="1d35c-148">Dezinstalacja - Debian 8</span><span class="sxs-lookup"><span data-stu-id="1d35c-148">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="1d35c-149">Debian 9</span><span class="sxs-lookup"><span data-stu-id="1d35c-149">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="1d35c-150">Instalacja za pośrednictwem repozytorium pakietów - Debian 9</span><span class="sxs-lookup"><span data-stu-id="1d35c-150">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="1d35c-151">Podstawowe programu PowerShell dla systemu Linux jest publikowany dla repozytoriów pakietu do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="1d35c-151">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="1d35c-152">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="1d35c-152">This is the preferred method.</span></span>

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

<span data-ttu-id="1d35c-153">Po zarejestrowaniu repozytorium Microsoft raz jako administratora, od, wystarczy użyć `sudo apt-get upgrade powershell` go zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="1d35c-153">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="1d35c-154">Instalacja za pośrednictwem bezpośredniego pobierania - Debian 9</span><span class="sxs-lookup"><span data-stu-id="1d35c-154">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="1d35c-155">Pobierz pakiet Debian `powershell_6.0.2-1.debian.9_amd64.deb` z [Wersje][] strony na Debian maszyny.</span><span class="sxs-lookup"><span data-stu-id="1d35c-155">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="1d35c-156">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="1d35c-156">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="1d35c-157">Należy pamiętać, że `dpkg -i` zakończy się niepowodzeniem z unmet zależności.</span><span class="sxs-lookup"><span data-stu-id="1d35c-157">Please note that `dpkg -i` will fail with unmet dependencies.</span></span>
> <span data-ttu-id="1d35c-158">Następne polecenie `apt-get install -f` rozpoznaje je, a następnie kończy Konfigurowanie pakietu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d35c-158">The next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-9"></a><span data-ttu-id="1d35c-159">Dezinstalacja - Debian 9</span><span class="sxs-lookup"><span data-stu-id="1d35c-159">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="1d35c-160">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="1d35c-160">CentOS 7</span></span>

> <span data-ttu-id="1d35c-161">Ten pakiet jest również działa na Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="1d35c-161">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="1d35c-162">Instalacja za pośrednictwem repozytorium pakietów (preferowane) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="1d35c-162">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="1d35c-163">Podstawowe programu PowerShell dla systemu Linux jest publikowany oficjalnego repozytoria Microsoft easy instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="1d35c-163">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="1d35c-164">Po zarejestrowaniu repozytorium Microsoft raz jako administratora, wystarczy użyć `sudo yum update powershell` aktualizacji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d35c-164">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="1d35c-165">Instalacja za pośrednictwem bezpośredniego pobierania - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="1d35c-165">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="1d35c-166">Przy użyciu [CentOS 7][], Pobierz pakiet RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` z [Wersje][] strony na maszynie CentOS.</span><span class="sxs-lookup"><span data-stu-id="1d35c-166">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="1d35c-167">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="1d35c-167">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="1d35c-168">Można także zainstalować RPM bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="1d35c-168">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="1d35c-169">Dezinstalacja - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="1d35c-169">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="1d35c-171">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="1d35c-171">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="1d35c-172">Instalacja za pośrednictwem repozytorium pakietów (preferowane) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="1d35c-172">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="1d35c-173">Podstawowe programu PowerShell dla systemu Linux jest publikowany oficjalnego repozytoria Microsoft easy instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="1d35c-173">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="1d35c-174">Po zarejestrowaniu repozytorium Microsoft raz jako administratora, wystarczy użyć `sudo yum update powershell` aktualizacji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d35c-174">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="1d35c-175">Instalacja za pośrednictwem bezpośredniego pobierania - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="1d35c-175">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="1d35c-176">Pobierz pakiet RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` z [Wersje][] strony na maszynie Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="1d35c-176">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="1d35c-177">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="1d35c-177">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="1d35c-178">Można także zainstalować RPM bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="1d35c-178">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="1d35c-179">Dezinstalacja - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="1d35c-179">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="1d35c-180">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="1d35c-180">OpenSUSE 42.2</span></span>

> [!NOTE]
> <span data-ttu-id="1d35c-181">Podczas instalacji podstawowej programu PowerShell `zypper` może Zgłoś następujący błąd:</span><span class="sxs-lookup"><span data-stu-id="1d35c-181">When installing PowerShell Core, `zypper` may report the following error:</span></span>
>
> ```Output
> Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
>  Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
>  Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
> ```
>
> <span data-ttu-id="1d35c-182">W takim przypadku sprawdź, czy zgodna `libcurl` biblioteki występuje przez sprawdzenie, czy następujące polecenie pokazuje `libcurl4` pakietu jako zainstalowane:</span><span class="sxs-lookup"><span data-stu-id="1d35c-182">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>
>
> ```sh
> zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
> ```
>
> <span data-ttu-id="1d35c-183">Następnie wybierz pozycję `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` rozwiązania podczas instalowania pakietu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d35c-183">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="1d35c-184">Instalacja za pośrednictwem repozytorium pakietów (preferowane) - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="1d35c-184">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="1d35c-185">Podstawowe programu PowerShell dla systemu Linux jest publikowany oficjalnego repozytoria Microsoft easy instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="1d35c-185">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="1d35c-186">Instalacja za pośrednictwem bezpośredniego pobierania - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="1d35c-186">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="1d35c-187">Pobierz pakiet RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` z [Wersje][] strony na maszynie OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="1d35c-187">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="1d35c-188">Można także zainstalować RPM bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="1d35c-188">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="1d35c-189">Dezinstalacja - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="1d35c-189">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="1d35c-190">Fedora</span><span class="sxs-lookup"><span data-stu-id="1d35c-190">Fedora</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="1d35c-191">Instalacja za pośrednictwem repozytorium pakietów (preferowane) - Fedora 27 Fedora 28</span><span class="sxs-lookup"><span data-stu-id="1d35c-191">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="1d35c-192">Podstawowe programu PowerShell dla systemu Linux jest publikowany oficjalnego repozytoria Microsoft easy instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="1d35c-192">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="1d35c-193">Instalacja za pośrednictwem bezpośredniego pobierania - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="1d35c-193">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="1d35c-194">Pobierz pakiet RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` z [Wersje][] strony na maszynie Fedora.</span><span class="sxs-lookup"><span data-stu-id="1d35c-194">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="1d35c-195">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="1d35c-195">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="1d35c-196">Można także zainstalować RPM bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="1d35c-196">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="1d35c-197">Dezinstalacja - Fedora 27 Fedora 28</span><span class="sxs-lookup"><span data-stu-id="1d35c-197">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="1d35c-198">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="1d35c-198">Arch Linux</span></span>

<span data-ttu-id="1d35c-199">Środowisko PowerShell jest dostępny z [Arch systemu Linux][] użytkownika repozytorium (AUR).</span><span class="sxs-lookup"><span data-stu-id="1d35c-199">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="1d35c-200">Może być kompilowana przy użyciu [najnowszej oznakowane zlecenia][arch-release]</span><span class="sxs-lookup"><span data-stu-id="1d35c-200">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="1d35c-201">Mogą być kompilowane z [najnowszym zatwierdzeniu do wzorca][arch-git]</span><span class="sxs-lookup"><span data-stu-id="1d35c-201">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="1d35c-202">Można zainstalować, za pomocą [najnowszej wersji pliku binarnego][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="1d35c-202">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="1d35c-203">Pakiety w AUR Wspólnotę utrzymane — nie jest oficjalną obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="1d35c-203">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="1d35c-204">Aby uzyskać więcej informacji na temat instalowania pakietów z AUR, zobacz [wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) lub społeczności [plik DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="1d35c-204">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch systemu Linux]: https://www.archlinux.org/download/
[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="1d35c-206">AppImage systemu Linux</span><span class="sxs-lookup"><span data-stu-id="1d35c-206">Linux AppImage</span></span>

<span data-ttu-id="1d35c-207">Przy użyciu najnowszych dystrybucji systemu Linux, Pobierz AppImage `powershell-6.0.1-x86_64.AppImage` z [Wersje][] strony na komputerze systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="1d35c-207">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="1d35c-208">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="1d35c-208">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="1d35c-209">[AppImage][] umożliwia uruchamianie programu PowerShell bez jej instalowania.</span><span class="sxs-lookup"><span data-stu-id="1d35c-209">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="1d35c-210">Jest przenośnych aplikacji, która zawiera w jednym pakiecie spójnego środowiska PowerShell i jego zależności (w tym oprogramowanie .NET Core zależności systemu).</span><span class="sxs-lookup"><span data-stu-id="1d35c-210">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="1d35c-211">Ten pakiet jest jedną wartość binarną, która działa niezależnie od dystrybucji systemu Linux przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1d35c-211">This package  is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="1d35c-213">Kali</span><span class="sxs-lookup"><span data-stu-id="1d35c-213">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="1d35c-214">Instalacja</span><span class="sxs-lookup"><span data-stu-id="1d35c-214">Installation</span></span>

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="1d35c-215">Uruchom program PowerShell w najnowszej Kali (Kali przewijane GNU/Linux) bez instalowania go</span><span class="sxs-lookup"><span data-stu-id="1d35c-215">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="1d35c-216">Dezinstalacja - Kali</span><span class="sxs-lookup"><span data-stu-id="1d35c-216">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="1d35c-217">Raspbian</span><span class="sxs-lookup"><span data-stu-id="1d35c-217">Raspbian</span></span>

<span data-ttu-id="1d35c-218">Obecnie programu PowerShell jest obsługiwana tylko na Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="1d35c-218">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="1d35c-219">Również środowisko CoreCLR (i w związku z tym podstawowe programu PowerShell) będą działać tylko na urządzeniach Pi 2 i Pi 3 jako inne urządzenia, tak samo, jak [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), nieobsługiwany procesor.</span><span class="sxs-lookup"><span data-stu-id="1d35c-219">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="1d35c-220">Pobierz [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) i postępuj zgodnie z [instrukcje dotyczące instalacji](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) uzyskać na Twoje Pi.</span><span class="sxs-lookup"><span data-stu-id="1d35c-220">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="1d35c-221">Instalacja</span><span class="sxs-lookup"><span data-stu-id="1d35c-221">Installation</span></span>

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

<span data-ttu-id="1d35c-222">Opcjonalnie można utworzyć łącza symbolicznego, aby można było uruchomić program PowerShell bez określenia ścieżki do "pwsh" binarne</span><span class="sxs-lookup"><span data-stu-id="1d35c-222">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="1d35c-223">Dezinstalacja - Raspbian</span><span class="sxs-lookup"><span data-stu-id="1d35c-223">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="1d35c-224">Archiwa binarne</span><span class="sxs-lookup"><span data-stu-id="1d35c-224">Binary Archives</span></span>

<span data-ttu-id="1d35c-225">Dane binarne środowiska PowerShell `tar.gz` archiwa są udostępniane dla platform Linux umożliwić wdrożenie zaawansowanych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="1d35c-225">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="1d35c-226">Zależności</span><span class="sxs-lookup"><span data-stu-id="1d35c-226">Dependencies</span></span>

<span data-ttu-id="1d35c-227">PowerShell kompilacje przenośne pliki binarne dla wszystkich dystrybucje systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="1d35c-227">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="1d35c-228">Jednak różnych zależności na różne dystrybucje wymaga środowiska uruchomieniowego .NET Core i dlatego programu PowerShell jest taka sama.</span><span class="sxs-lookup"><span data-stu-id="1d35c-228">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="1d35c-229">W poniższej tabeli przedstawiono zależności .NET Core 2.0 oficjalnie obsługiwanych w różnych dystrybucje systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="1d35c-229">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="1d35c-230">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="1d35c-230">OS</span></span>                 | <span data-ttu-id="1d35c-231">Zależności</span><span class="sxs-lookup"><span data-stu-id="1d35c-231">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="1d35c-232">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="1d35c-232">Ubuntu 14.04</span></span>       | <span data-ttu-id="1d35c-233">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="1d35c-233">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="1d35c-234">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="1d35c-234">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="1d35c-235">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="1d35c-235">Ubuntu 16.04</span></span>       | <span data-ttu-id="1d35c-236">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="1d35c-236">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="1d35c-237">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="1d35c-237">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="1d35c-238">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="1d35c-238">Ubuntu 17.04</span></span>       | <span data-ttu-id="1d35c-239">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="1d35c-239">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="1d35c-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="1d35c-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="1d35c-241">Debian 8 (Joasia)</span><span class="sxs-lookup"><span data-stu-id="1d35c-241">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="1d35c-242">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="1d35c-242">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="1d35c-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="1d35c-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="1d35c-244">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="1d35c-244">Debian 9 (Stretch)</span></span> | <span data-ttu-id="1d35c-245">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="1d35c-245">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="1d35c-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="1d35c-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="1d35c-247">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="1d35c-247">CentOS 7</span></span> <br> <span data-ttu-id="1d35c-248">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="1d35c-248">Oracle Linux 7</span></span> <br> <span data-ttu-id="1d35c-249">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="1d35c-249">RHEL 7</span></span> <br> <span data-ttu-id="1d35c-250">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="1d35c-250">OpenSUSE 42.2</span></span> | <span data-ttu-id="1d35c-251">libunwind, libcurl, biblioteki openssl, libicu</span><span class="sxs-lookup"><span data-stu-id="1d35c-251">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="1d35c-252">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="1d35c-252">Fedora 27</span></span> <br> <span data-ttu-id="1d35c-253">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="1d35c-253">Fedora 28</span></span> | <span data-ttu-id="1d35c-254">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="1d35c-254">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="1d35c-255">Aby wdrożyć pliki binarne programu PowerShell na dystrybucje systemu Linux, które nie są obsługiwane oficjalnie, należy zainstalować zależności niezbędne dla docelowego systemu operacyjnego w oddzielne kroki.</span><span class="sxs-lookup"><span data-stu-id="1d35c-255">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="1d35c-256">Na przykład naszych [plik dockerfile Amazon Linux] [ amazon-dockerfile] najpierw instaluje zależności, a następnie wyodrębnia systemu Linux `tar.gz` archiwum.</span><span class="sxs-lookup"><span data-stu-id="1d35c-256">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="1d35c-257">Instalacja — archiwa binarne</span><span class="sxs-lookup"><span data-stu-id="1d35c-257">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="1d35c-258">Linux</span><span class="sxs-lookup"><span data-stu-id="1d35c-258">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="1d35c-259">Odinstalowanie archiwa binarne</span><span class="sxs-lookup"><span data-stu-id="1d35c-259">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="1d35c-260">Ścieżki</span><span class="sxs-lookup"><span data-stu-id="1d35c-260">Paths</span></span>

* <span data-ttu-id="1d35c-261">`$PSHOME` jest `/opt/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="1d35c-261">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="1d35c-262">Profile użytkowników będą odczytywane z `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="1d35c-262">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="1d35c-263">Domyślne profile będą odczytywane z `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="1d35c-263">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="1d35c-264">Moduły użytkownika będą odczytywane z `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="1d35c-264">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="1d35c-265">Udostępniony moduły będą odczytywane z `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="1d35c-265">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="1d35c-266">Domyślne moduły będą odczytywane z `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="1d35c-266">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="1d35c-267">Historia PSReadline zostanie zarejestrowana w celu `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="1d35c-267">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="1d35c-268">Profile przestrzegać konfiguracji na hosta w programie PowerShell, więc domyślne profile specyficzne dla hosta istnieje w `Microsoft.PowerShell_profile.ps1` w tej samej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="1d35c-268">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="1d35c-269">PowerShell szanuje [specyfikacji katalogu Base XDG] [ xdg-bds] w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="1d35c-269">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[Wersje]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
