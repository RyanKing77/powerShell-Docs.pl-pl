# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="4c567-101">Instalowanie programu PowerShell Core w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="4c567-101">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="4c567-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="4c567-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="4c567-103">Dla dystrybucje systemu Linux, które nie są obsługiwane oficjalnie, można spróbować użyć [PowerShell AppImage][lai].</span><span class="sxs-lookup"><span data-stu-id="4c567-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="4c567-104">Można też spróbować wdrożenia plików binarnych programu PowerShell bezpośrednio przy użyciu systemu Linux [ `tar.gz` archiwum][tar], ale należy skonfigurować wymagane zależności, oparte na system operacyjny w oddzielne kroki.</span><span class="sxs-lookup"><span data-stu-id="4c567-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="4c567-105">Wszystkie pakiety są dostępne w naszej witrynie GitHub [zwalnia][] strony.</span><span class="sxs-lookup"><span data-stu-id="4c567-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="4c567-106">Po zainstalowaniu pakietu `pwsh` z terminalu.</span><span class="sxs-lookup"><span data-stu-id="4c567-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

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

## <a name="installing-preview-releases"></a><span data-ttu-id="4c567-107">Instalowanie wersji Preview</span><span class="sxs-lookup"><span data-stu-id="4c567-107">Installing Preview Releases</span></span>

<span data-ttu-id="4c567-108">Podczas instalowania wersji zapoznawczej Core programu PowerShell dla systemu Linux za pomocą z repozytorium pakietów, nazwę pakietu zmieni się z `powershell` do `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="4c567-108">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="4c567-109">Instalowanie za pośrednictwem bezpośredniego pobierania nie ulega zmianie, inną niż nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="4c567-109">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="4c567-110">W tym miejscu znajduje się tabela polecenia, aby zainstalować te pakiety w wersji zapoznawczej i stabilny, przy użyciu różnych menedżerów pakietu:</span><span class="sxs-lookup"><span data-stu-id="4c567-110">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="4c567-111">Distrobution(s)</span><span class="sxs-lookup"><span data-stu-id="4c567-111">Distrobution(s)</span></span>|<span data-ttu-id="4c567-112">Polecenie stabilna</span><span class="sxs-lookup"><span data-stu-id="4c567-112">Stable Command</span></span> | <span data-ttu-id="4c567-113">Polecenie Podgląd</span><span class="sxs-lookup"><span data-stu-id="4c567-113">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="4c567-114">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="4c567-114">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="4c567-115">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="4c567-115">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="4c567-116">openSUSE</span><span class="sxs-lookup"><span data-stu-id="4c567-116">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="4c567-117">Fedora</span><span class="sxs-lookup"><span data-stu-id="4c567-117">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="4c567-118">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="4c567-118">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="4c567-119">Instalacja za pośrednictwem repozytorium pakietów - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="4c567-119">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="4c567-120">Podstawowe programu PowerShell dla systemu Linux jest publikowany dla repozytoriów pakietu do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="4c567-120">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="4c567-121">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="4c567-121">This is the preferred method.</span></span>

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

<span data-ttu-id="4c567-122">Jako administratora Zarejestruj repozytorium firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4c567-122">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="4c567-123">Następnie należy po prostu użyć `sudo apt-get upgrade powershell` aktualizacji instalacji.</span><span class="sxs-lookup"><span data-stu-id="4c567-123">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="4c567-124">Instalacja za pośrednictwem bezpośredniego pobierania - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="4c567-124">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="4c567-125">Pobierz pakiet Debian `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` z [zwalnia][] strony na maszynie Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="4c567-125">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="4c567-126">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4c567-126">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="4c567-127">`dpkg -i` Polecenia nie powiodło się unmet zależności.</span><span class="sxs-lookup"><span data-stu-id="4c567-127">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="4c567-128">Następne polecenie `apt-get install -f` rozwiązanie tych problemów, a następnie zakończeniu konfigurowania pakietu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c567-128">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="4c567-129">Dezinstalacja - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="4c567-129">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="4c567-130">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="4c567-130">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="4c567-131">Instalacja za pośrednictwem repozytorium pakietów - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="4c567-131">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="4c567-132">Podstawowe programu PowerShell dla systemu Linux jest publikowany dla repozytoriów pakietu do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="4c567-132">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="4c567-133">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="4c567-133">This is the preferred method.</span></span>

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

<span data-ttu-id="4c567-134">Po zarejestrowaniu repozytorium Microsoft raz jako administratora, od, wystarczy użyć `sudo apt-get upgrade powershell` go zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="4c567-134">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="4c567-135">Instalacja za pośrednictwem bezpośredniego pobierania - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="4c567-135">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="4c567-136">Pobierz pakiet Debian `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` z [zwalnia][] strony na maszynie Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="4c567-136">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="4c567-137">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4c567-137">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="4c567-138">`dpkg -i` Polecenia nie powiodło się unmet zależności.</span><span class="sxs-lookup"><span data-stu-id="4c567-138">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="4c567-139">Następne polecenie `apt-get install -f` rozwiązanie tych problemów, a następnie zakończeniu konfigurowania pakietu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c567-139">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="4c567-140">Dezinstalacja - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="4c567-140">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1710"></a><span data-ttu-id="4c567-141">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="4c567-141">Ubuntu 17.10</span></span>

> [!NOTE]
> <span data-ttu-id="4c567-142">Dodano obsługę Ubuntu 17.04 po `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="4c567-142">Support for Ubuntu 17.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1710"></a><span data-ttu-id="4c567-143">Instalacja za pośrednictwem repozytorium pakietów - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="4c567-143">Installation via Package Repository - Ubuntu 17.10</span></span>

<span data-ttu-id="4c567-144">Podstawowe programu PowerShell dla systemu Linux jest publikowany dla repozytoriów pakietu do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="4c567-144">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="4c567-145">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="4c567-145">This is the preferred method.</span></span>

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

<span data-ttu-id="4c567-146">Po zarejestrowaniu repozytorium Microsoft raz jako administratora, od, wystarczy użyć `sudo apt-get upgrade powershell` go zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="4c567-146">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1710"></a><span data-ttu-id="4c567-147">Instalacja za pośrednictwem bezpośredniego pobierania - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="4c567-147">Installation via Direct Download - Ubuntu 17.10</span></span>

<span data-ttu-id="4c567-148">Pobierz pakiet Debian `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` z [zwalnia][] strony na maszynie Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="4c567-148">Download the Debian package `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="4c567-149">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4c567-149">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.10_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="4c567-150">`dpkg -i` Polecenia nie powiodło się unmet zależności.</span><span class="sxs-lookup"><span data-stu-id="4c567-150">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="4c567-151">Następne polecenie `apt-get install -f` rozwiązanie tych problemów, a następnie zakończeniu konfigurowania pakietu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c567-151">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1710"></a><span data-ttu-id="4c567-152">Dezinstalacja - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="4c567-152">Uninstallation - Ubuntu 17.10</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="4c567-153">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="4c567-153">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="4c567-154">Dodano obsługę Ubuntu 18.04 po `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="4c567-154">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="4c567-155">Instalacja za pośrednictwem repozytorium pakietów - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="4c567-155">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="4c567-156">Podstawowe programu PowerShell dla systemu Linux jest publikowany dla repozytoriów pakietu do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="4c567-156">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="4c567-157">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="4c567-157">This is the preferred method.</span></span>

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

<span data-ttu-id="4c567-158">Po zarejestrowaniu repozytorium Microsoft raz jako administratora, od, wystarczy użyć `sudo apt-get upgrade powershell` go zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="4c567-158">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="4c567-159">Instalacja za pośrednictwem bezpośredniego pobierania - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="4c567-159">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="4c567-160">Pobierz pakiet Debian `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` z [zwalnia][] strony na maszynie Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="4c567-160">Download the Debian package `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="4c567-161">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4c567-161">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="4c567-162">`dpkg -i` Polecenia nie powiodło się unmet zależności.</span><span class="sxs-lookup"><span data-stu-id="4c567-162">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="4c567-163">Następne polecenie `apt-get install -f` rozwiązanie tych problemów, a następnie zakończeniu konfigurowania pakietu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c567-163">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1710"></a><span data-ttu-id="4c567-164">Dezinstalacja - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="4c567-164">Uninstallation - Ubuntu 17.10</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="4c567-165">Debian 8</span><span class="sxs-lookup"><span data-stu-id="4c567-165">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="4c567-166">Instalacja za pośrednictwem repozytorium pakietów - Debian 8</span><span class="sxs-lookup"><span data-stu-id="4c567-166">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="4c567-167">Podstawowe programu PowerShell dla systemu Linux jest publikowany dla repozytoriów pakietu do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="4c567-167">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="4c567-168">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="4c567-168">This is the preferred method.</span></span>

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

<span data-ttu-id="4c567-169">Po zarejestrowaniu repozytorium Microsoft raz jako administratora, od, wystarczy użyć `sudo apt-get upgrade powershell` go zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="4c567-169">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="4c567-170">Instalacja za pośrednictwem bezpośredniego pobierania - Debian 8</span><span class="sxs-lookup"><span data-stu-id="4c567-170">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="4c567-171">Pobierz pakiet Debian `powershell_6.0.2-1.debian.8_amd64.deb` z [zwalnia][] strony na Debian maszyny.</span><span class="sxs-lookup"><span data-stu-id="4c567-171">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="4c567-172">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4c567-172">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="4c567-173">`dpkg -i` Polecenia nie powiodło się unmet zależności.</span><span class="sxs-lookup"><span data-stu-id="4c567-173">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="4c567-174">Następne polecenie `apt-get install -f` rozwiązanie tych problemów, a następnie zakończeniu konfigurowania pakietu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c567-174">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="4c567-175">Dezinstalacja - Debian 8</span><span class="sxs-lookup"><span data-stu-id="4c567-175">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="4c567-176">Debian 9</span><span class="sxs-lookup"><span data-stu-id="4c567-176">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="4c567-177">Instalacja za pośrednictwem repozytorium pakietów - Debian 9</span><span class="sxs-lookup"><span data-stu-id="4c567-177">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="4c567-178">Podstawowe programu PowerShell dla systemu Linux jest publikowany dla repozytoriów pakietu do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="4c567-178">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="4c567-179">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="4c567-179">This is the preferred method.</span></span>

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

<span data-ttu-id="4c567-180">Po zarejestrowaniu repozytorium Microsoft raz jako administratora, od, wystarczy użyć `sudo apt-get upgrade powershell` go zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="4c567-180">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="4c567-181">Instalacja za pośrednictwem bezpośredniego pobierania - Debian 9</span><span class="sxs-lookup"><span data-stu-id="4c567-181">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="4c567-182">Pobierz pakiet Debian `powershell_6.0.2-1.debian.9_amd64.deb` z [zwalnia][] strony na Debian maszyny.</span><span class="sxs-lookup"><span data-stu-id="4c567-182">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="4c567-183">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4c567-183">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="4c567-184">Dezinstalacja - Debian 9</span><span class="sxs-lookup"><span data-stu-id="4c567-184">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="4c567-185">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="4c567-185">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="4c567-186">Ten pakiet jest również działa na Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="4c567-186">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="4c567-187">Instalacja za pośrednictwem repozytorium pakietów (preferowane) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="4c567-187">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="4c567-188">Podstawowe programu PowerShell dla systemu Linux jest publikowany oficjalnego repozytoria Microsoft easy instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="4c567-188">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="4c567-189">Po zarejestrowaniu repozytorium Microsoft raz jako administratora, wystarczy użyć `sudo yum update powershell` aktualizacji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c567-189">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="4c567-190">Instalacja za pośrednictwem bezpośredniego pobierania - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="4c567-190">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="4c567-191">Przy użyciu [CentOS 7][], Pobierz pakiet RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` z [zwalnia][] strony na maszynie CentOS.</span><span class="sxs-lookup"><span data-stu-id="4c567-191">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="4c567-192">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4c567-192">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="4c567-193">Można także zainstalować RPM bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="4c567-193">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="4c567-194">Dezinstalacja - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="4c567-194">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="4c567-196">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="4c567-196">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="4c567-197">Instalacja za pośrednictwem repozytorium pakietów (preferowane) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="4c567-197">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="4c567-198">Podstawowe programu PowerShell dla systemu Linux jest publikowany oficjalnego repozytoria Microsoft easy instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="4c567-198">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="4c567-199">Po zarejestrowaniu repozytorium Microsoft raz jako administratora, wystarczy użyć `sudo yum update powershell` aktualizacji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c567-199">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="4c567-200">Instalacja za pośrednictwem bezpośredniego pobierania - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="4c567-200">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="4c567-201">Pobierz pakiet RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` z [zwalnia][] strony na maszynie Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="4c567-201">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="4c567-202">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4c567-202">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="4c567-203">Można także zainstalować RPM bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="4c567-203">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="4c567-204">Dezinstalacja - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="4c567-204">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="4c567-205">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="4c567-205">OpenSUSE 42.2</span></span>

<span data-ttu-id="4c567-206">Podczas instalacji podstawowej programu PowerShell `zypper` może Zgłoś następujący błąd:</span><span class="sxs-lookup"><span data-stu-id="4c567-206">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="4c567-207">W takim przypadku sprawdź, czy zgodna `libcurl` biblioteki występuje przez sprawdzenie, czy następujące polecenie pokazuje `libcurl4` pakietu jako zainstalowane:</span><span class="sxs-lookup"><span data-stu-id="4c567-207">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="4c567-208">Następnie wybierz pozycję `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` rozwiązania podczas instalowania pakietu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c567-208">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="4c567-209">Instalacja za pośrednictwem repozytorium pakietów (preferowane) - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="4c567-209">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="4c567-210">Podstawowe programu PowerShell dla systemu Linux jest publikowany oficjalnego repozytoria Microsoft easy instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="4c567-210">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="4c567-211">Instalacja za pośrednictwem bezpośredniego pobierania - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="4c567-211">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="4c567-212">Pobierz pakiet RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` z [zwalnia][] strony na maszynie OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="4c567-212">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="4c567-213">Można także zainstalować RPM bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="4c567-213">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="4c567-214">Dezinstalacja - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="4c567-214">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="4c567-215">Fedora</span><span class="sxs-lookup"><span data-stu-id="4c567-215">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="4c567-216">Fedora 28 jest obsługiwana tylko w programie PowerShell Core 6.1 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="4c567-216">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="4c567-217">Instalacja za pośrednictwem repozytorium pakietów (preferowane) - Fedora 27 Fedora 28</span><span class="sxs-lookup"><span data-stu-id="4c567-217">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="4c567-218">Podstawowe programu PowerShell dla systemu Linux jest publikowany oficjalnego repozytoria Microsoft easy instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="4c567-218">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="4c567-219">Instalacja za pośrednictwem bezpośredniego pobierania - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="4c567-219">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="4c567-220">Pobierz pakiet RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` z [zwalnia][] strony na maszynie Fedora.</span><span class="sxs-lookup"><span data-stu-id="4c567-220">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="4c567-221">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4c567-221">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="4c567-222">Można także zainstalować RPM bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="4c567-222">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="4c567-223">Dezinstalacja - Fedora 27 Fedora 28</span><span class="sxs-lookup"><span data-stu-id="4c567-223">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="4c567-224">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="4c567-224">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="4c567-225">Obsługa architektury jest eksperymentalne.</span><span class="sxs-lookup"><span data-stu-id="4c567-225">Arch support is experimental.</span></span>

<span data-ttu-id="4c567-226">Środowisko PowerShell jest dostępny z [Arch Linux][] użytkownika repozytorium (AUR).</span><span class="sxs-lookup"><span data-stu-id="4c567-226">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="4c567-227">Może być kompilowana przy użyciu [najnowszej oznakowane zlecenia][arch-release]</span><span class="sxs-lookup"><span data-stu-id="4c567-227">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="4c567-228">Mogą być kompilowane z [najnowszym zatwierdzeniu do wzorca][arch-git]</span><span class="sxs-lookup"><span data-stu-id="4c567-228">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="4c567-229">Można zainstalować, za pomocą [najnowszej wersji pliku binarnego][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="4c567-229">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="4c567-230">Pakiety w AUR Wspólnotę utrzymane — nie jest oficjalną obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="4c567-230">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="4c567-231">Aby uzyskać więcej informacji na temat instalowania pakietów z AUR, zobacz [wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) lub społeczności [plik DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="4c567-231">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="4c567-233">AppImage systemu Linux</span><span class="sxs-lookup"><span data-stu-id="4c567-233">Linux AppImage</span></span>

> [!NOTE]
> <span data-ttu-id="4c567-234">Obsługa AppImage jest eksperymentalna</span><span class="sxs-lookup"><span data-stu-id="4c567-234">AppImage support is experimental</span></span>

<span data-ttu-id="4c567-235">Przy użyciu najnowszych dystrybucji systemu Linux, Pobierz AppImage `powershell-6.0.1-x86_64.AppImage` z [zwalnia][] strony na komputerze systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="4c567-235">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="4c567-236">W terminalu następnie wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4c567-236">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="4c567-237">[AppImage][] umożliwia uruchamianie programu PowerShell bez jej instalowania.</span><span class="sxs-lookup"><span data-stu-id="4c567-237">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="4c567-238">Jest przenośnych aplikacji, która zawiera w jednym pakiecie spójnego środowiska PowerShell i jego zależności (w tym oprogramowanie .NET Core zależności systemu).</span><span class="sxs-lookup"><span data-stu-id="4c567-238">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="4c567-239">Ten pakiet jest jedną wartość binarną, która działa niezależnie od dystrybucji systemu Linux przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4c567-239">This package  is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="4c567-241">Kali</span><span class="sxs-lookup"><span data-stu-id="4c567-241">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="4c567-242">Obsługa Kali jest eksperymentalne.</span><span class="sxs-lookup"><span data-stu-id="4c567-242">Kali support is experimental.</span></span>

### <a name="installation"></a><span data-ttu-id="4c567-243">Instalacja</span><span class="sxs-lookup"><span data-stu-id="4c567-243">Installation</span></span>

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="4c567-244">Uruchom program PowerShell w najnowszej Kali (Kali przewijane GNU/Linux) bez instalowania go</span><span class="sxs-lookup"><span data-stu-id="4c567-244">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="4c567-245">Dezinstalacja - Kali</span><span class="sxs-lookup"><span data-stu-id="4c567-245">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="4c567-246">Raspbian</span><span class="sxs-lookup"><span data-stu-id="4c567-246">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="4c567-247">Obsługa Raspbian jest eksperymentalne.</span><span class="sxs-lookup"><span data-stu-id="4c567-247">Raspbian support is experimental.</span></span>

<span data-ttu-id="4c567-248">Obecnie programu PowerShell jest obsługiwana tylko na Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="4c567-248">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="4c567-249">Również środowisko CoreCLR (i w związku z tym podstawowe programu PowerShell) będą działać tylko na urządzeniach Pi 2 i Pi 3 jako inne urządzenia, tak samo, jak [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), nieobsługiwany procesor.</span><span class="sxs-lookup"><span data-stu-id="4c567-249">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="4c567-250">Pobierz [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) i postępuj zgodnie z [instrukcje dotyczące instalacji](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) uzyskać na Twoje Pi.</span><span class="sxs-lookup"><span data-stu-id="4c567-250">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="4c567-251">Instalacja</span><span class="sxs-lookup"><span data-stu-id="4c567-251">Installation</span></span>

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

<span data-ttu-id="4c567-252">Opcjonalnie można utworzyć łącza symbolicznego, aby można było uruchomić program PowerShell bez określenia ścieżki do "pwsh" binarne</span><span class="sxs-lookup"><span data-stu-id="4c567-252">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="4c567-253">Dezinstalacja - Raspbian</span><span class="sxs-lookup"><span data-stu-id="4c567-253">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="4c567-254">Archiwa binarne</span><span class="sxs-lookup"><span data-stu-id="4c567-254">Binary Archives</span></span>

<span data-ttu-id="4c567-255">Dane binarne środowiska PowerShell `tar.gz` archiwa są udostępniane dla platform Linux umożliwić wdrożenie zaawansowanych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="4c567-255">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="4c567-256">Zależności</span><span class="sxs-lookup"><span data-stu-id="4c567-256">Dependencies</span></span>

<span data-ttu-id="4c567-257">PowerShell kompilacje przenośne pliki binarne dla wszystkich dystrybucje systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="4c567-257">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="4c567-258">Jednak różnych zależności na różne dystrybucje wymaga środowiska uruchomieniowego .NET Core i dlatego programu PowerShell jest taka sama.</span><span class="sxs-lookup"><span data-stu-id="4c567-258">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="4c567-259">W poniższej tabeli przedstawiono zależności .NET Core 2.0 oficjalnie obsługiwanych w różnych dystrybucje systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="4c567-259">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="4c567-260">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="4c567-260">OS</span></span>                 | <span data-ttu-id="4c567-261">Zależności</span><span class="sxs-lookup"><span data-stu-id="4c567-261">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="4c567-262">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="4c567-262">Ubuntu 14.04</span></span>       | <span data-ttu-id="4c567-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="4c567-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="4c567-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="4c567-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="4c567-265">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="4c567-265">Ubuntu 16.04</span></span>       | <span data-ttu-id="4c567-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="4c567-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="4c567-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="4c567-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="4c567-268">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="4c567-268">Ubuntu 17.10</span></span>       | <span data-ttu-id="4c567-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="4c567-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="4c567-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="4c567-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="4c567-271">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="4c567-271">Ubuntu 18.04</span></span>       | <span data-ttu-id="4c567-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="4c567-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="4c567-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="4c567-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="4c567-274">Debian 8 (Joasia)</span><span class="sxs-lookup"><span data-stu-id="4c567-274">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="4c567-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="4c567-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="4c567-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="4c567-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="4c567-277">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="4c567-277">Debian 9 (Stretch)</span></span> | <span data-ttu-id="4c567-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="4c567-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="4c567-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="4c567-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="4c567-280">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="4c567-280">CentOS 7</span></span> <br> <span data-ttu-id="4c567-281">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="4c567-281">Oracle Linux 7</span></span> <br> <span data-ttu-id="4c567-282">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="4c567-282">RHEL 7</span></span> <br> <span data-ttu-id="4c567-283">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="4c567-283">OpenSUSE 42.2</span></span> | <span data-ttu-id="4c567-284">libunwind, libcurl, biblioteki openssl, libicu</span><span class="sxs-lookup"><span data-stu-id="4c567-284">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="4c567-285">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="4c567-285">Fedora 27</span></span> <br> <span data-ttu-id="4c567-286">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="4c567-286">Fedora 28</span></span> | <span data-ttu-id="4c567-287">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="4c567-287">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="4c567-288">Aby wdrożyć pliki binarne programu PowerShell na dystrybucje systemu Linux, które nie są obsługiwane oficjalnie, należy zainstalować zależności niezbędne dla docelowego systemu operacyjnego w oddzielne kroki.</span><span class="sxs-lookup"><span data-stu-id="4c567-288">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="4c567-289">Na przykład naszych [plik dockerfile Amazon Linux] [ amazon-dockerfile] najpierw instaluje zależności, a następnie wyodrębnia systemu Linux `tar.gz` archiwum.</span><span class="sxs-lookup"><span data-stu-id="4c567-289">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="4c567-290">Instalacja — archiwa binarne</span><span class="sxs-lookup"><span data-stu-id="4c567-290">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="4c567-291">Linux</span><span class="sxs-lookup"><span data-stu-id="4c567-291">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="4c567-292">Odinstalowanie archiwa binarne</span><span class="sxs-lookup"><span data-stu-id="4c567-292">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="4c567-293">Ścieżki</span><span class="sxs-lookup"><span data-stu-id="4c567-293">Paths</span></span>

* <span data-ttu-id="4c567-294">`$PSHOME` jest `/opt/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="4c567-294">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="4c567-295">Profile użytkowników będą odczytywane z `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="4c567-295">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="4c567-296">Domyślne profile będą odczytywane z `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="4c567-296">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="4c567-297">Moduły użytkownika będą odczytywane z `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="4c567-297">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="4c567-298">Udostępniony moduły będą odczytywane z `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="4c567-298">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="4c567-299">Domyślne moduły będą odczytywane z `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="4c567-299">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="4c567-300">Historia PSReadline zostanie zarejestrowana w celu `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="4c567-300">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="4c567-301">Profile przestrzegać konfiguracji na hosta w programie PowerShell, więc domyślne profile specyficzne dla hosta istnieje w `Microsoft.PowerShell_profile.ps1` w tej samej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="4c567-301">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="4c567-302">PowerShell szanuje [specyfikacji katalogu Base XDG] [ xdg-bds] w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="4c567-302">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[zwalnia]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
