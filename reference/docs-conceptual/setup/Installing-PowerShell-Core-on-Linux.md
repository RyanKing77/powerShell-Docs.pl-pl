# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="c9109-101">Instalowanie programu PowerShell Core w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="c9109-101">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="c9109-102">Obsługuje [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10] [ u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27 ] [ fedora], [Fedora 28][fedora], i [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="c9109-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="c9109-103">Dystrybucje systemu Linux, które nie są oficjalnie obsługiwane, spróbuj użyć [PowerShell AppImage][lai].</span><span class="sxs-lookup"><span data-stu-id="c9109-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="c9109-104">Możesz też spróbować wdrażania plików binarnych programu PowerShell bezpośrednio przy użyciu systemu Linux [ `tar.gz` archiwum][tar], ale należy skonfigurować niezbędne zależności, w oparciu o system operacyjny w oddzielne kroki.</span><span class="sxs-lookup"><span data-stu-id="c9109-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="c9109-105">Wszystkie pakiety są dostępne w usłudze GitHub [zwalnia][] strony.</span><span class="sxs-lookup"><span data-stu-id="c9109-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="c9109-106">Po zainstalowaniu pakietu Uruchom `pwsh` z poziomu terminalu.</span><span class="sxs-lookup"><span data-stu-id="c9109-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1710
[u18]: #ubuntu-1804
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-423
[fedora]: #fedora
[arch]: #arch-linux
[lai]: #linux-appimage
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="c9109-107">Instalowanie wersji zapoznawczych</span><span class="sxs-lookup"><span data-stu-id="c9109-107">Installing Preview Releases</span></span>

<span data-ttu-id="c9109-108">Podczas instalowania wersji programu PowerShell Core w wersji zapoznawczej dla systemu Linux przy użyciu repozytorium pakietów, nazwy pakietu zmieni się z `powershell` do `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="c9109-108">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="c9109-109">Instalowanie przy użyciu bezpośredniego pobierania nie ulega zmianie, inna niż nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="c9109-109">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="c9109-110">W tym miejscu znajduje się tabela polecenia, aby zainstalować pakiety w wersji zapoznawczej i stabilny, przy użyciu różnych menedżerów pakietów:</span><span class="sxs-lookup"><span data-stu-id="c9109-110">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="c9109-111">Distribution(s)</span><span class="sxs-lookup"><span data-stu-id="c9109-111">Distribution(s)</span></span>|<span data-ttu-id="c9109-112">Polecenie stabilne</span><span class="sxs-lookup"><span data-stu-id="c9109-112">Stable Command</span></span> | <span data-ttu-id="c9109-113">Polecenia w wersji zapoznawczej</span><span class="sxs-lookup"><span data-stu-id="c9109-113">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="c9109-114">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="c9109-114">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="c9109-115">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="c9109-115">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="c9109-116">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="c9109-116">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="c9109-117">Fedora</span><span class="sxs-lookup"><span data-stu-id="c9109-117">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="c9109-118">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c9109-118">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="c9109-119">Instalację przy użyciu repozytorium pakietów — Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c9109-119">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="c9109-120">Program PowerShell Core dla systemu Linux jest publikowany repozytoriów pakietów do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="c9109-120">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c9109-121">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="c9109-121">This is the preferred method.</span></span>

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

<span data-ttu-id="c9109-122">Jako administratora należy zarejestrować się w repozytorium firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c9109-122">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="c9109-123">Od tego momentu, po prostu musisz użyć `sudo apt-get upgrade powershell` do aktualizacji instalacji.</span><span class="sxs-lookup"><span data-stu-id="c9109-123">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="c9109-124">Instalację za pomocą bezpośredniego pobierania — Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c9109-124">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="c9109-125">Pobierz pakiet Debian `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` z [zwalnia][] strony na komputerze Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="c9109-125">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="c9109-126">Następnie wykonaj następujące czynności w terminalu:</span><span class="sxs-lookup"><span data-stu-id="c9109-126">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="c9109-127">`dpkg -i` Polecenia nie powiodło się niewypełnienia zależności.</span><span class="sxs-lookup"><span data-stu-id="c9109-127">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="c9109-128">Następne polecenie `apt-get install -f` rozwiązuje te problemy, a następnie kończy Konfigurowanie pakietami programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c9109-128">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="c9109-129">Dezinstalacja — Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c9109-129">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="c9109-130">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c9109-130">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="c9109-131">Instalację przy użyciu repozytorium pakietów — Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c9109-131">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="c9109-132">Program PowerShell Core dla systemu Linux jest publikowany repozytoriów pakietów do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="c9109-132">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c9109-133">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="c9109-133">This is the preferred method.</span></span>

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

<span data-ttu-id="c9109-134">Po zarejestrowaniu programu Microsoft repository raz jako administratora, od tego momentu, po prostu musisz użyć `sudo apt-get upgrade powershell` ją zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="c9109-134">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="c9109-135">Instalację za pomocą bezpośredniego pobierania — Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c9109-135">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="c9109-136">Pobierz pakiet Debian `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` z [zwalnia][] strony na komputerze Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="c9109-136">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="c9109-137">Następnie wykonaj następujące czynności w terminalu:</span><span class="sxs-lookup"><span data-stu-id="c9109-137">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="c9109-138">`dpkg -i` Polecenia nie powiodło się niewypełnienia zależności.</span><span class="sxs-lookup"><span data-stu-id="c9109-138">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="c9109-139">Następne polecenie `apt-get install -f` rozwiązuje te problemy, a następnie kończy Konfigurowanie pakietami programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c9109-139">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="c9109-140">Dezinstalacja — Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c9109-140">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1710"></a><span data-ttu-id="c9109-141">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="c9109-141">Ubuntu 17.10</span></span>

> [!NOTE]
> <span data-ttu-id="c9109-142">Dodano obsługę systemu Ubuntu 17.04 po `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="c9109-142">Support for Ubuntu 17.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1710"></a><span data-ttu-id="c9109-143">Instalację przy użyciu repozytorium pakietów — Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="c9109-143">Installation via Package Repository - Ubuntu 17.10</span></span>

<span data-ttu-id="c9109-144">Program PowerShell Core dla systemu Linux jest publikowany repozytoriów pakietów do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="c9109-144">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c9109-145">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="c9109-145">This is the preferred method.</span></span>

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

<span data-ttu-id="c9109-146">Po zarejestrowaniu programu Microsoft repository raz jako administratora, od tego momentu, po prostu musisz użyć `sudo apt-get upgrade powershell` ją zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="c9109-146">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1710"></a><span data-ttu-id="c9109-147">Instalację za pomocą bezpośredniego pobierania — Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="c9109-147">Installation via Direct Download - Ubuntu 17.10</span></span>

<span data-ttu-id="c9109-148">Pobierz pakiet Debian `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` z [zwalnia][] strony na komputerze Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="c9109-148">Download the Debian package `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="c9109-149">Następnie wykonaj następujące czynności w terminalu:</span><span class="sxs-lookup"><span data-stu-id="c9109-149">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.10_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="c9109-150">`dpkg -i` Polecenia nie powiodło się niewypełnienia zależności.</span><span class="sxs-lookup"><span data-stu-id="c9109-150">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="c9109-151">Następne polecenie `apt-get install -f` rozwiązuje te problemy, a następnie kończy Konfigurowanie pakietami programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c9109-151">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1710"></a><span data-ttu-id="c9109-152">Dezinstalacja — Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="c9109-152">Uninstallation - Ubuntu 17.10</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="c9109-153">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="c9109-153">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="c9109-154">Dodano obsługę systemu Ubuntu 18.04 po `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="c9109-154">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="c9109-155">Instalację przy użyciu repozytorium pakietów — Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="c9109-155">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="c9109-156">Program PowerShell Core dla systemu Linux jest publikowany repozytoriów pakietów do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="c9109-156">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c9109-157">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="c9109-157">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell-preview

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="c9109-158">Po zarejestrowaniu programu Microsoft repository raz jako administratora, od tego momentu, po prostu musisz użyć `sudo apt-get upgrade powershell` ją zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="c9109-158">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="c9109-159">Instalację za pomocą bezpośredniego pobierania — Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="c9109-159">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="c9109-160">Pobierz pakiet Debian `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` z [zwalnia][] strony na komputerze Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="c9109-160">Download the Debian package `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="c9109-161">Następnie wykonaj następujące czynności w terminalu:</span><span class="sxs-lookup"><span data-stu-id="c9109-161">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="c9109-162">`dpkg -i` Polecenia nie powiodło się niewypełnienia zależności.</span><span class="sxs-lookup"><span data-stu-id="c9109-162">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="c9109-163">Następne polecenie `apt-get install -f` rozwiązuje te problemy, a następnie kończy Konfigurowanie pakietami programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c9109-163">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="c9109-164">Dezinstalacja — Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="c9109-164">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="c9109-165">Debian 8</span><span class="sxs-lookup"><span data-stu-id="c9109-165">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="c9109-166">Instalację przy użyciu repozytorium pakietów — Debian 8</span><span class="sxs-lookup"><span data-stu-id="c9109-166">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="c9109-167">Program PowerShell Core dla systemu Linux jest publikowany repozytoriów pakietów do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="c9109-167">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c9109-168">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="c9109-168">This is the preferred method.</span></span>

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

<span data-ttu-id="c9109-169">Po zarejestrowaniu programu Microsoft repository raz jako administratora, od tego momentu, po prostu musisz użyć `sudo apt-get upgrade powershell` ją zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="c9109-169">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="c9109-170">Instalację za pomocą bezpośredniego pobierania — Debian 8</span><span class="sxs-lookup"><span data-stu-id="c9109-170">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="c9109-171">Pobierz pakiet Debian `powershell_6.0.2-1.debian.8_amd64.deb` z [zwalnia][] strony na komputerze Debian.</span><span class="sxs-lookup"><span data-stu-id="c9109-171">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="c9109-172">Następnie wykonaj następujące czynności w terminalu:</span><span class="sxs-lookup"><span data-stu-id="c9109-172">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="c9109-173">`dpkg -i` Polecenia nie powiodło się niewypełnienia zależności.</span><span class="sxs-lookup"><span data-stu-id="c9109-173">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="c9109-174">Następne polecenie `apt-get install -f` rozwiązuje te problemy, a następnie kończy Konfigurowanie pakietami programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c9109-174">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="c9109-175">Dezinstalacja — Debian 8</span><span class="sxs-lookup"><span data-stu-id="c9109-175">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="c9109-176">Debian 9</span><span class="sxs-lookup"><span data-stu-id="c9109-176">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="c9109-177">Instalację przy użyciu repozytorium pakietów - Debian 9</span><span class="sxs-lookup"><span data-stu-id="c9109-177">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="c9109-178">Program PowerShell Core dla systemu Linux jest publikowany repozytoriów pakietów do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="c9109-178">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c9109-179">Jest to preferowana metoda.</span><span class="sxs-lookup"><span data-stu-id="c9109-179">This is the preferred method.</span></span>

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

<span data-ttu-id="c9109-180">Po zarejestrowaniu programu Microsoft repository raz jako administratora, od tego momentu, po prostu musisz użyć `sudo apt-get upgrade powershell` ją zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="c9109-180">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="c9109-181">Instalację za pomocą bezpośredniego pobierania - Debian 9</span><span class="sxs-lookup"><span data-stu-id="c9109-181">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="c9109-182">Pobierz pakiet Debian `powershell_6.0.2-1.debian.9_amd64.deb` z [zwalnia][] strony na komputerze Debian.</span><span class="sxs-lookup"><span data-stu-id="c9109-182">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="c9109-183">Następnie wykonaj następujące czynności w terminalu:</span><span class="sxs-lookup"><span data-stu-id="c9109-183">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="c9109-184">Dezinstalacja — Debian 9</span><span class="sxs-lookup"><span data-stu-id="c9109-184">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="c9109-185">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c9109-185">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="c9109-186">Ten pakiet działa także w systemie Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="c9109-186">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="c9109-187">Instalację przy użyciu repozytorium pakietów (preferowany) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c9109-187">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="c9109-188">Program PowerShell Core dla systemu Linux jest publikowany oficjalnych repozytoriów firmy Microsoft do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="c9109-188">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="c9109-189">Po zarejestrowaniu programu Microsoft repository raz jako administratora, po prostu musisz użyć `sudo yum update powershell` do zaktualizowania programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c9109-189">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="c9109-190">Instalację za pomocą bezpośredniego pobierania - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c9109-190">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="c9109-191">Za pomocą [CentOS 7][], Pobierz pakiet RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` z [zwalnia][] strony na komputerze CentOS.</span><span class="sxs-lookup"><span data-stu-id="c9109-191">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="c9109-192">Następnie wykonaj następujące czynności w terminalu:</span><span class="sxs-lookup"><span data-stu-id="c9109-192">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="c9109-193">Można także zainstalować obr. / min bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="c9109-193">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="c9109-194">Dezinstalacja - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c9109-194">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="c9109-196">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="c9109-196">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="c9109-197">Instalację przy użyciu repozytorium pakietów (preferowany) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="c9109-197">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="c9109-198">Program PowerShell Core dla systemu Linux jest publikowany oficjalnych repozytoriów firmy Microsoft do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="c9109-198">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="c9109-199">Po zarejestrowaniu programu Microsoft repository raz jako administratora, po prostu musisz użyć `sudo yum update powershell` do zaktualizowania programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c9109-199">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="c9109-200">Instalację za pomocą bezpośredniego pobierania - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="c9109-200">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="c9109-201">Pobierz pakiet RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` z [zwalnia][] strony na komputerze Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="c9109-201">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="c9109-202">Następnie wykonaj następujące czynności w terminalu:</span><span class="sxs-lookup"><span data-stu-id="c9109-202">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="c9109-203">Można także zainstalować obr. / min bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="c9109-203">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="c9109-204">Dezinstalacja - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="c9109-204">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-423"></a><span data-ttu-id="c9109-205">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="c9109-205">OpenSUSE 42.3</span></span>

<span data-ttu-id="c9109-206">Podczas instalowania programu PowerShell Core `zypper` może Zgłoś następujący błąd:</span><span class="sxs-lookup"><span data-stu-id="c9109-206">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="c9109-207">W takim przypadku upewnij się, że zgodne `libcurl` biblioteka jest obecny, sprawdzając, czy następujące polecenie pokazuje `libcurl4` pakietu jako zainstalowane:</span><span class="sxs-lookup"><span data-stu-id="c9109-207">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="c9109-208">Następnie wybierz `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` rozwiązania podczas instalowania pakietu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c9109-208">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-423"></a><span data-ttu-id="c9109-209">Instalację przy użyciu repozytorium pakietów (preferowany) - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="c9109-209">Installation via Package Repository (preferred) - OpenSUSE 42.3</span></span>

<span data-ttu-id="c9109-210">Program PowerShell Core dla systemu Linux jest publikowany oficjalnych repozytoriów firmy Microsoft do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="c9109-210">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-423"></a><span data-ttu-id="c9109-211">Instalację za pomocą bezpośredniego pobierania - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="c9109-211">Installation via Direct Download - OpenSUSE 42.3</span></span>

<span data-ttu-id="c9109-212">Pobierz pakiet RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` z [zwalnia][] strony na komputerze OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="c9109-212">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="c9109-213">Można także zainstalować obr. / min bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="c9109-213">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-423"></a><span data-ttu-id="c9109-214">Dezinstalacja - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="c9109-214">Uninstallation - OpenSUSE 42.3</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="c9109-215">Fedora</span><span class="sxs-lookup"><span data-stu-id="c9109-215">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="c9109-216">Fedora 28 jest obsługiwane tylko w sytuacji, w programie PowerShell Core 6.1 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="c9109-216">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="c9109-217">Instalację przy użyciu repozytorium pakietów (preferowany) - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="c9109-217">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="c9109-218">Program PowerShell Core dla systemu Linux jest publikowany oficjalnych repozytoriów firmy Microsoft do łatwej instalacji (i aktualizacji).</span><span class="sxs-lookup"><span data-stu-id="c9109-218">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="c9109-219">Instalację za pomocą bezpośredniego pobierania - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="c9109-219">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="c9109-220">Pobierz pakiet RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` z [zwalnia][] strony na komputerze Fedora.</span><span class="sxs-lookup"><span data-stu-id="c9109-220">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="c9109-221">Następnie wykonaj następujące czynności w terminalu:</span><span class="sxs-lookup"><span data-stu-id="c9109-221">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="c9109-222">Można także zainstalować obr. / min bez pośredniego kroku pobierania go:</span><span class="sxs-lookup"><span data-stu-id="c9109-222">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="c9109-223">Dezinstalacja - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="c9109-223">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="c9109-224">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="c9109-224">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="c9109-225">Obsługa architektury jest eksperymentalne.</span><span class="sxs-lookup"><span data-stu-id="c9109-225">Arch support is experimental.</span></span>

<span data-ttu-id="c9109-226">Program PowerShell jest dostępny z [Arch systemu Linux][] użytkownika repozytorium (AUR).</span><span class="sxs-lookup"><span data-stu-id="c9109-226">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="c9109-227">Może być skompilowana przy użyciu [najnowsze tagiem wydania][arch-release]</span><span class="sxs-lookup"><span data-stu-id="c9109-227">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="c9109-228">Może być kompilowane z [najnowsze zatwierdzenie do wzorca][arch-git]</span><span class="sxs-lookup"><span data-stu-id="c9109-228">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="c9109-229">Można zainstalować, za pomocą [najnowszej wersji pliku binarnego][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="c9109-229">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="c9109-230">Pakiety w AUR są utrzymywane społeczności — Brak obsługi oficjalnych.</span><span class="sxs-lookup"><span data-stu-id="c9109-230">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="c9109-231">Aby uzyskać więcej informacji na temat instalowania pakietów z AUR, zobacz [wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) lub społeczności [pliku DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="c9109-231">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch systemu Linux]: https://www.archlinux.org/download/
[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="c9109-233">AppImage systemu Linux</span><span class="sxs-lookup"><span data-stu-id="c9109-233">Linux AppImage</span></span>

> [!NOTE]
> <span data-ttu-id="c9109-234">Obsługa AppImage jest eksperymentalny</span><span class="sxs-lookup"><span data-stu-id="c9109-234">AppImage support is experimental</span></span>

<span data-ttu-id="c9109-235">Przy użyciu najnowszych dystrybucji systemu Linux, Pobierz AppImage `powershell-6.0.1-x86_64.AppImage` z [zwalnia][] strony na maszyny z systemem Linux.</span><span class="sxs-lookup"><span data-stu-id="c9109-235">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="c9109-236">Następnie wykonaj następujące czynności w terminalu:</span><span class="sxs-lookup"><span data-stu-id="c9109-236">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="c9109-237">[AppImage][] pozwala na uruchamianie programu PowerShell bez instalowania.</span><span class="sxs-lookup"><span data-stu-id="c9109-237">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="c9109-238">Jest przenośny aplikację, która razem w jednym pakiecie spójnego środowiska PowerShell i jego zależności (w tym zależności systemu .NET Core).</span><span class="sxs-lookup"><span data-stu-id="c9109-238">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="c9109-239">Ten pakiet jest pojedynczy plik binarny, który działa niezależnie od dystrybucji systemu Linux użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c9109-239">This package is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="c9109-241">Kali</span><span class="sxs-lookup"><span data-stu-id="c9109-241">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="c9109-242">Obsługa Kali jest eksperymentalne.</span><span class="sxs-lookup"><span data-stu-id="c9109-242">Kali support is experimental.</span></span>

### <a name="installation"></a><span data-ttu-id="c9109-243">Instalacja</span><span class="sxs-lookup"><span data-stu-id="c9109-243">Installation</span></span>

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="c9109-244">Uruchamianie programu PowerShell w najnowszych Kali (Kali przewijane GNU/Linux) bez instalowania</span><span class="sxs-lookup"><span data-stu-id="c9109-244">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="c9109-245">Dezinstalacja - Kali</span><span class="sxs-lookup"><span data-stu-id="c9109-245">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="c9109-246">Raspbian</span><span class="sxs-lookup"><span data-stu-id="c9109-246">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="c9109-247">Obsługa Raspbian jest eksperymentalne.</span><span class="sxs-lookup"><span data-stu-id="c9109-247">Raspbian support is experimental.</span></span>

<span data-ttu-id="c9109-248">Program PowerShell jest obecnie obsługiwane tylko w Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="c9109-248">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="c9109-249">Również CoreCLR (i w związku z tym program PowerShell Core) będą działać tylko na urządzeniach Pi 2 i Pi 3 jako inne urządzenia, takie jak [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), ma nieobsługiwany procesor.</span><span class="sxs-lookup"><span data-stu-id="c9109-249">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="c9109-250">Pobierz [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) i postępuj zgodnie z [instrukcje dotyczące instalacji](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) uruchomienie go na swoje Pi.</span><span class="sxs-lookup"><span data-stu-id="c9109-250">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="c9109-251">Instalacja</span><span class="sxs-lookup"><span data-stu-id="c9109-251">Installation</span></span>

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

<span data-ttu-id="c9109-252">Opcjonalnie można utworzyć łącza symbolicznego, aby można było uruchomić środowisko PowerShell bez określenia ścieżki do "pwsh" binarny</span><span class="sxs-lookup"><span data-stu-id="c9109-252">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="c9109-253">Dezinstalacja - Raspbian</span><span class="sxs-lookup"><span data-stu-id="c9109-253">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="c9109-254">Binarny archiwa</span><span class="sxs-lookup"><span data-stu-id="c9109-254">Binary Archives</span></span>

<span data-ttu-id="c9109-255">Plik binarny programu PowerShell `tar.gz` archiwa są dostarczane dla platform Linux umożliwić zaawansowanych scenariuszach wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="c9109-255">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="c9109-256">Zależności</span><span class="sxs-lookup"><span data-stu-id="c9109-256">Dependencies</span></span>

<span data-ttu-id="c9109-257">PowerShell tworzy przenośne pliki binarne dla wszystkich dystrybucjach systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="c9109-257">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="c9109-258">Środowisko uruchomieniowe programu .NET Core wymaga różnych składników zależnych w różnych dystrybucjach — a więc programu PowerShell działa tak samo.</span><span class="sxs-lookup"><span data-stu-id="c9109-258">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="c9109-259">Poniższej tabeli przedstawiono zależności platformy .NET Core 2.0, które są oficjalnie obsługiwane przez różne dystrybucje systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="c9109-259">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="c9109-260">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="c9109-260">OS</span></span>                 | <span data-ttu-id="c9109-261">Zależności</span><span class="sxs-lookup"><span data-stu-id="c9109-261">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="c9109-262">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c9109-262">Ubuntu 14.04</span></span>       | <span data-ttu-id="c9109-263">libc6, liblttng libgssapi-krb5-2, libgcc1,-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="c9109-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c9109-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="c9109-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="c9109-265">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c9109-265">Ubuntu 16.04</span></span>       | <span data-ttu-id="c9109-266">libc6, liblttng libgssapi-krb5-2, libgcc1,-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="c9109-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c9109-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="c9109-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="c9109-268">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="c9109-268">Ubuntu 17.10</span></span>       | <span data-ttu-id="c9109-269">libc6, liblttng libgssapi-krb5-2, libgcc1,-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="c9109-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c9109-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="c9109-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="c9109-271">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="c9109-271">Ubuntu 18.04</span></span>       | <span data-ttu-id="c9109-272">libc6, liblttng libgssapi-krb5-2, libgcc1,-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="c9109-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c9109-273">libcurl3 libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="c9109-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="c9109-274">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="c9109-274">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="c9109-275">libc6, liblttng libgssapi-krb5-2, libgcc1,-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="c9109-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c9109-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="c9109-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="c9109-277">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="c9109-277">Debian 9 (Stretch)</span></span> | <span data-ttu-id="c9109-278">libc6, liblttng libgssapi-krb5-2, libgcc1,-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="c9109-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c9109-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="c9109-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="c9109-280">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c9109-280">CentOS 7</span></span> <br> <span data-ttu-id="c9109-281">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="c9109-281">Oracle Linux 7</span></span> <br> <span data-ttu-id="c9109-282">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="c9109-282">RHEL 7</span></span> <br> <span data-ttu-id="c9109-283">OpenSUSE OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="c9109-283">OpenSUSE OpenSUSE 42.3</span></span> | <span data-ttu-id="c9109-284">libunwind, libcurl, biblioteki openssl, libicu</span><span class="sxs-lookup"><span data-stu-id="c9109-284">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="c9109-285">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="c9109-285">Fedora 27</span></span> <br> <span data-ttu-id="c9109-286">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="c9109-286">Fedora 28</span></span> | <span data-ttu-id="c9109-287">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="c9109-287">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="c9109-288">Aby wdrożyć pliki binarne programu PowerShell, w dystrybucjach systemu Linux, które nie są oficjalnie obsługiwane, należy zainstalować wymagane zależności dla docelowego systemu operacyjnego w oddzielne kroki.</span><span class="sxs-lookup"><span data-stu-id="c9109-288">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="c9109-289">Na przykład naszym [dockerfile Amazon Linux] [ amazon-dockerfile] najpierw zainstalowanie zależności, a następnie wyodrębnia systemu Linux `tar.gz` archiwum.</span><span class="sxs-lookup"><span data-stu-id="c9109-289">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="c9109-290">Instalacja — archiwum binarne</span><span class="sxs-lookup"><span data-stu-id="c9109-290">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="c9109-291">Linux</span><span class="sxs-lookup"><span data-stu-id="c9109-291">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="c9109-292">Odinstalowywanie archiwum binarne</span><span class="sxs-lookup"><span data-stu-id="c9109-292">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="c9109-293">Ścieżki</span><span class="sxs-lookup"><span data-stu-id="c9109-293">Paths</span></span>

* <span data-ttu-id="c9109-294">`$PSHOME` jest `/opt/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="c9109-294">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="c9109-295">Profile użytkowników będą odczytywane z `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="c9109-295">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="c9109-296">Domyślne profile będą odczytywane z `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="c9109-296">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="c9109-297">Moduły użytkownika zostanie odczytany z `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="c9109-297">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="c9109-298">Udostępnione moduły będą odczytywane z `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="c9109-298">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="c9109-299">Domyślne moduły będą odczytywane z `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="c9109-299">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="c9109-300">Historia PSReadline zostanie zarejestrowana w celu `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="c9109-300">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="c9109-301">Profile przestrzegają konfiguracji dla hosta programu PowerShell, więc domyślne profile specyficzne dla hosta istnieje w `Microsoft.PowerShell_profile.ps1` w tej samej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="c9109-301">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="c9109-302">Stosuje się do programu PowerShell [specyfikację katalogu Base XDG] [ xdg-bds] w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="c9109-302">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[zwalnia]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
