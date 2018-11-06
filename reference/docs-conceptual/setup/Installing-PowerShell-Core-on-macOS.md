---
title: Instalowanie programu PowerShell Core w systemie macOS
description: Informacje o instalowaniu programu PowerShell Core w systemie macOS
ms.date: 11/02/2018
ms.openlocfilehash: 162e841bf71d708e9db84ea1bb2dbef13924783b
ms.sourcegitcommit: f4247d3f91d06ec392c4cd66921ce7d0456a2bd9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2018
ms.locfileid: "50998507"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="e48b0-103">Instalowanie programu PowerShell Core w systemie macOS</span><span class="sxs-lookup"><span data-stu-id="e48b0-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="e48b0-104">Program PowerShell Core obsługuje system macOS 10.12 i wyższych.</span><span class="sxs-lookup"><span data-stu-id="e48b0-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="e48b0-105">Wszystkie pakiety są dostępne w usłudze GitHub [zwalnia][] strony.</span><span class="sxs-lookup"><span data-stu-id="e48b0-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="e48b0-106">Po zainstalowaniu pakietu Uruchom `pwsh` z poziomu terminalu.</span><span class="sxs-lookup"><span data-stu-id="e48b0-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="about-brew"></a><span data-ttu-id="e48b0-107">Temat Brew</span><span class="sxs-lookup"><span data-stu-id="e48b0-107">About Brew</span></span>

<span data-ttu-id="e48b0-108">[Homebrew] [ brew] to Menedżer pakietów preferowanych dla systemu macOS.</span><span class="sxs-lookup"><span data-stu-id="e48b0-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="e48b0-109">Jeśli `brew` nie znaleziono polecenia, musisz zainstalować następujące Homebrew [zgodnie z instrukcjami][brew].</span><span class="sxs-lookup"><span data-stu-id="e48b0-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="e48b0-110">Instalacja najnowsza wersja stabilna za pośrednictwem Homebrew w systemie macOS 10.12 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="e48b0-110">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="e48b0-111">Zobacz [o Brew](#about-brew) uzyskać informacji na temat Brew.</span><span class="sxs-lookup"><span data-stu-id="e48b0-111">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="e48b0-112">Teraz można zainstalować programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e48b0-112">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="e48b0-113">Na koniec sprawdź, czy Twoja instalacja działa prawidłowo:</span><span class="sxs-lookup"><span data-stu-id="e48b0-113">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="e48b0-114">Po udostępnieniu nowej wersji programu PowerShell, po prostu zaktualizuj wzory firmy Homebrew i Uaktualnij program PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e48b0-114">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="e48b0-115">Powyższe polecenia mogą być wywoływane z w ramach hosta programu PowerShell (pwsh), ale następnie powłoki programu PowerShell, należy ponownie uruchomić, aby zakończyć uaktualnianie, a następnie Odśwież wartości widocznych na $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="e48b0-115">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="e48b0-116">Instalacja najnowszą wersję zapoznawczą wersji za pomocą Homebrew w systemie macOS 10.12 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="e48b0-116">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="e48b0-117">Zobacz [o Brew](#about-brew) uzyskać informacji na temat Brew.</span><span class="sxs-lookup"><span data-stu-id="e48b0-117">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="e48b0-118">Po zainstalowaniu Homebrew Instalowanie programu PowerShell jest proste.</span><span class="sxs-lookup"><span data-stu-id="e48b0-118">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="e48b0-119">Najpierw zainstaluj [wersji Cask] [ cask-versions] można zainstalować alternatywne wersje pakietów cask:</span><span class="sxs-lookup"><span data-stu-id="e48b0-119">First, install [Cask-Versions][cask-versions] which lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="e48b0-120">Teraz można zainstalować programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e48b0-120">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="e48b0-121">Na koniec sprawdź, czy Twoja instalacja działa prawidłowo:</span><span class="sxs-lookup"><span data-stu-id="e48b0-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="e48b0-122">Po udostępnieniu nowej wersji programu PowerShell, po prostu zaktualizuj wzory firmy Homebrew i Uaktualnij program PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e48b0-122">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="e48b0-123">Powyższe polecenia mogą być wywoływane z w ramach hosta programu PowerShell (pwsh), ale następnie powłoki programu PowerShell, należy ponownie uruchomić, aby ukończyć uaktualnienie.</span><span class="sxs-lookup"><span data-stu-id="e48b0-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="e48b0-124">i Odśwież wartości widocznych na $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="e48b0-124">and refresh the values shown in $PSVersionTable.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="e48b0-125">Instalację za pomocą bezpośredniego pobierania</span><span class="sxs-lookup"><span data-stu-id="e48b0-125">Installation via Direct Download</span></span>

<span data-ttu-id="e48b0-126">Pobierz pakiet zapisanego pakietu `powershell-6.1.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="e48b0-126">Download the PKG package `powershell-6.1.0-osx-x64.pkg`</span></span>
<span data-ttu-id="e48b0-127">z [zwalnia][] strony na komputerze z systemem macOS.</span><span class="sxs-lookup"><span data-stu-id="e48b0-127">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="e48b0-128">Możesz kliknij dwukrotnie plik i postępuj zgodnie z instrukcjami lub zainstalować ją z poziomu terminalu:</span><span class="sxs-lookup"><span data-stu-id="e48b0-128">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

<span data-ttu-id="e48b0-129">Zainstaluj [OpenSSL](#install-openssl) jak jest to niezbędne do komunikacji zdalnej programu PowerShell i operacji modelu wspólnych informacji.</span><span class="sxs-lookup"><span data-stu-id="e48b0-129">Install [OpenSSL](#install-openssl) as this is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="e48b0-130">Binarny archiwa</span><span class="sxs-lookup"><span data-stu-id="e48b0-130">Binary Archives</span></span>

<span data-ttu-id="e48b0-131">Plik binarny programu PowerShell `tar.gz` archiwa są dostarczane dla platformy z systemem macOS w celu umożliwienia zaawansowanych scenariuszach wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="e48b0-131">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="e48b0-132">Instalowanie pliku binarnego archiwów w systemie macOS</span><span class="sxs-lookup"><span data-stu-id="e48b0-132">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.1.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.1.0/pwsh /usr/local/bin/pwsh
```

<span data-ttu-id="e48b0-133">Zainstaluj [OpenSSL](#install-openssl) jak jest to niezbędne do komunikacji zdalnej programu PowerShell i operacji modelu wspólnych informacji.</span><span class="sxs-lookup"><span data-stu-id="e48b0-133">Install [OpenSSL](#install-openssl) as this is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="e48b0-134">Instalacja zależności</span><span class="sxs-lookup"><span data-stu-id="e48b0-134">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="e48b0-135">Zainstaluj narzędzia wiersza polecenia programu XCode</span><span class="sxs-lookup"><span data-stu-id="e48b0-135">Install XCode command line tools</span></span>

```shell
xcode-select -install
```

### <a name="install-openssl"></a><span data-ttu-id="e48b0-136">Zainstalować protokół OpenSSL</span><span class="sxs-lookup"><span data-stu-id="e48b0-136">Install OpenSSL</span></span>

<span data-ttu-id="e48b0-137">Biblioteki OpenSSL jest wymagany dla operacji modelu wspólnych informacji i komunikacji zdalnej programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e48b0-137">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>  <span data-ttu-id="e48b0-138">Można zainstalować za pomocą MacPorts lub Brew.</span><span class="sxs-lookup"><span data-stu-id="e48b0-138">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="e48b0-139">Zainstalować protokół OpenSSL, za pośrednictwem Brew</span><span class="sxs-lookup"><span data-stu-id="e48b0-139">Install OpenSSL via Brew</span></span>

<span data-ttu-id="e48b0-140">Zobacz [o Brew](#about-brew) uzyskać informacji na temat Brew.</span><span class="sxs-lookup"><span data-stu-id="e48b0-140">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="e48b0-141">Uruchom `brew install openssl` zainstalować protokół OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="e48b0-141">Run `brew install openssl` to install OpenSSL.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="e48b0-142">Zainstalować protokół OpenSSL, za pośrednictwem MacPorts</span><span class="sxs-lookup"><span data-stu-id="e48b0-142">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="e48b0-143">Instalowanie [narzędzi wiersza polecenia programu XCode](#install-xcode-command-line-tools)</span><span class="sxs-lookup"><span data-stu-id="e48b0-143">Instal the [XCode command line tools](#install-xcode-command-line-tools)</span></span>
1. <span data-ttu-id="e48b0-144">Zainstaluj MacPorts.</span><span class="sxs-lookup"><span data-stu-id="e48b0-144">Install MacPorts.</span></span>
   <span data-ttu-id="e48b0-145">Zobacz [Przewodnik instalacji](https://guide.macports.org/chunked/installing.macports.html) Jeśli potrzebujesz instrukcji.</span><span class="sxs-lookup"><span data-stu-id="e48b0-145">See the [installation guide](https://guide.macports.org/chunked/installing.macports.html) if you need instructions.</span></span>
1. <span data-ttu-id="e48b0-146">Zaktualizuj MacPorts uruchamiając `sudo port selfupdate`</span><span class="sxs-lookup"><span data-stu-id="e48b0-146">Update MacPorts by running `sudo port selfupdate`</span></span>
1. <span data-ttu-id="e48b0-147">Uaktualnij pakiety MacPorts, uruchamiając `sudo port upgrade outdated`</span><span class="sxs-lookup"><span data-stu-id="e48b0-147">Upgrade MacPorts packages by running `sudo port upgrade outdated`</span></span>
1. <span data-ttu-id="e48b0-148">Zainstalować protokół OpenSSL, uruchamiając, uruchamiając `sudo port instal openssl`</span><span class="sxs-lookup"><span data-stu-id="e48b0-148">Install OpenSSL by running by running `sudo port instal openssl`</span></span>
1. <span data-ttu-id="e48b0-149">Połącz biblioteki, aby można go używać programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e48b0-149">Link the libraries so that PowerShell can use it.</span></span>

```shell
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="e48b0-150">Odinstalowywanie programu PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="e48b0-150">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="e48b0-151">Po zainstalowaniu programu PowerShell przy użyciu Homebrew, dezinstalacja jest łatwe:</span><span class="sxs-lookup"><span data-stu-id="e48b0-151">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="e48b0-152">Po zainstalowaniu programu PowerShell direct pobrania przy użyciu programu PowerShell należy usunąć ręcznie:</span><span class="sxs-lookup"><span data-stu-id="e48b0-152">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="e48b0-153">Aby usunąć dodatkowe ścieżki programu PowerShell, zobacz [ścieżki](#paths) sekcji w niniejszym dokumencie i usuń żądany ścieżek przy użyciu `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="e48b0-153">To remove the additional PowerShell paths, please see the [paths](#paths) section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="e48b0-154">Nie jest to konieczne, jeśli został zainstalowany przy użyciu Homebrew.</span><span class="sxs-lookup"><span data-stu-id="e48b0-154">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="e48b0-155">Ścieżki</span><span class="sxs-lookup"><span data-stu-id="e48b0-155">Paths</span></span>

* <span data-ttu-id="e48b0-156">`$PSHOME` jest `/usr/local/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="e48b0-156">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="e48b0-157">Profile użytkowników będą odczytywane z `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="e48b0-157">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="e48b0-158">Domyślne profile będą odczytywane z `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="e48b0-158">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="e48b0-159">Moduły użytkownika zostanie odczytany z `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="e48b0-159">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="e48b0-160">Udostępnione moduły będą odczytywane z `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="e48b0-160">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="e48b0-161">Domyślne moduły będą odczytywane z `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="e48b0-161">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="e48b0-162">Historia PSReadline zostanie zarejestrowana w celu `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="e48b0-162">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="e48b0-163">Profile przestrzegają konfiguracji dla hosta programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e48b0-163">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="e48b0-164">Dlatego domyślne profile specyficzne dla hosta istnieje w `Microsoft.PowerShell_profile.ps1` w tej samej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="e48b0-164">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="e48b0-165">Stosuje się do programu PowerShell [specyfikację katalogu Base XDG] [ xdg-bds] w systemie macOS.</span><span class="sxs-lookup"><span data-stu-id="e48b0-165">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="e48b0-166">Ponieważ system macOS jest typem pochodnym BSD, prefiks `/usr/local` jest używana zamiast `/opt`.</span><span class="sxs-lookup"><span data-stu-id="e48b0-166">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="e48b0-167">W efekcie `$PSHOME` jest `/usr/local/microsoft/powershell/6.1.0/`, i łącza symbolicznego, jest umieszczany na `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="e48b0-167">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="e48b0-168">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="e48b0-168">Additional Resources</span></span>

* <span data-ttu-id="e48b0-169">[Homebrew w sieci Web][brew]</span><span class="sxs-lookup"><span data-stu-id="e48b0-169">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="e48b0-170">[Repozytorium Github Homebrew][GitHub]</span><span class="sxs-lookup"><span data-stu-id="e48b0-170">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="e48b0-171">[Homebrew Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="e48b0-171">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[zwalnia]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
