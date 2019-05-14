---
title: Instalowanie programu PowerShell Core w systemie macOS
description: Informacje o instalowaniu programu PowerShell Core w systemie macOS
ms.date: 12/12/2018
ms.openlocfilehash: 70f5d64aa8a697a9011d07fbcb2bb821463827e1
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229736"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="d49c3-103">Instalowanie programu PowerShell Core w systemie macOS</span><span class="sxs-lookup"><span data-stu-id="d49c3-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="d49c3-104">Program PowerShell Core obsługuje system macOS 10.12 i wyższych.</span><span class="sxs-lookup"><span data-stu-id="d49c3-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="d49c3-105">Wszystkie pakiety są dostępne w usłudze GitHub [Wersje][] strony.</span><span class="sxs-lookup"><span data-stu-id="d49c3-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="d49c3-106">Po zainstalowaniu pakietu Uruchom `pwsh` z poziomu terminalu.</span><span class="sxs-lookup"><span data-stu-id="d49c3-106">After the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="about-brew"></a><span data-ttu-id="d49c3-107">Temat Brew</span><span class="sxs-lookup"><span data-stu-id="d49c3-107">About Brew</span></span>

<span data-ttu-id="d49c3-108">[Homebrew] [ brew] to Menedżer pakietów preferowanych dla systemu macOS.</span><span class="sxs-lookup"><span data-stu-id="d49c3-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="d49c3-109">Jeśli `brew` nie znaleziono polecenia, musisz zainstalować następujące Homebrew [zgodnie z instrukcjami][brew].</span><span class="sxs-lookup"><span data-stu-id="d49c3-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>
<span data-ttu-id="d49c3-110">W przeciwnym razie możesz zainstalować program PowerShell, za pośrednictwem [Pobierz bezpośrednie](#installation-via-direct-download) lub [archiwum binarne](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="d49c3-110">Otherwise you may install PowerShell via [Direct Download](#installation-via-direct-download) or from [Binary Archives](#binary-archives).</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="d49c3-111">Instalacja najnowsza wersja stabilna za pośrednictwem Homebrew w systemie macOS 10.12 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="d49c3-111">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="d49c3-112">Zobacz [o Brew](#about-brew) uzyskać informacji na temat Brew.</span><span class="sxs-lookup"><span data-stu-id="d49c3-112">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="d49c3-113">Teraz można zainstalować programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d49c3-113">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="d49c3-114">Na koniec sprawdź, czy Twoja instalacja działa prawidłowo:</span><span class="sxs-lookup"><span data-stu-id="d49c3-114">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="d49c3-115">Po udostępnieniu nowej wersji programu PowerShell, zaktualizuj wzory firmy Homebrew i Uaktualnij program PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d49c3-115">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="d49c3-116">Powyższe polecenia mogą być wywoływane z w ramach hosta programu PowerShell (pwsh), ale następnie powłoki programu PowerShell, należy ponownie uruchomić, aby zakończyć uaktualnianie, a następnie Odśwież wartości widocznych na `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="d49c3-116">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="d49c3-117">Instalacja najnowszą wersję zapoznawczą wersji za pomocą Homebrew w systemie macOS 10.12 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="d49c3-117">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="d49c3-118">Zobacz [o Brew](#about-brew) uzyskać informacji na temat Brew.</span><span class="sxs-lookup"><span data-stu-id="d49c3-118">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="d49c3-119">Po zainstalowaniu Homebrew, można zainstalować programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d49c3-119">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="d49c3-120">Najpierw zainstaluj [wersji Cask] [ cask-versions] pakiet, który umożliwia zainstalowanie alternatywne wersje pakietów cask:</span><span class="sxs-lookup"><span data-stu-id="d49c3-120">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="d49c3-121">Teraz można zainstalować programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d49c3-121">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="d49c3-122">Na koniec sprawdź, czy Twoja instalacja działa prawidłowo:</span><span class="sxs-lookup"><span data-stu-id="d49c3-122">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="d49c3-123">Po udostępnieniu nowej wersji programu PowerShell, zaktualizuj wzory firmy Homebrew i Uaktualnij program PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d49c3-123">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="d49c3-124">Powyższe polecenia mogą być wywoływane z w ramach hosta programu PowerShell (pwsh), ale następnie powłoki programu PowerShell, należy ponownie uruchomić, aby ukończyć uaktualnienie.</span><span class="sxs-lookup"><span data-stu-id="d49c3-124">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="d49c3-125">i Odśwież wartości widocznych na `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="d49c3-125">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="d49c3-126">Instalację za pomocą bezpośredniego pobierania</span><span class="sxs-lookup"><span data-stu-id="d49c3-126">Installation via Direct Download</span></span>

<span data-ttu-id="d49c3-127">Pobierz pakiet zapisanego pakietu `powershell-6.2.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="d49c3-127">Download the PKG package `powershell-6.2.0-osx-x64.pkg`</span></span>
<span data-ttu-id="d49c3-128">z [Wersje][] strony na komputerze z systemem macOS.</span><span class="sxs-lookup"><span data-stu-id="d49c3-128">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="d49c3-129">Możesz kliknij dwukrotnie plik i postępuj zgodnie z instrukcjami lub zainstalować ją z poziomu terminalu:</span><span class="sxs-lookup"><span data-stu-id="d49c3-129">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.2.0-osx-x64.pkg -target /
```

<span data-ttu-id="d49c3-130">Zainstaluj [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="d49c3-130">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="d49c3-131">Biblioteki OpenSSL jest wymagany dla operacji modelu wspólnych informacji i komunikacji zdalnej programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d49c3-131">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="d49c3-132">Binarny archiwa</span><span class="sxs-lookup"><span data-stu-id="d49c3-132">Binary Archives</span></span>

<span data-ttu-id="d49c3-133">Plik binarny programu PowerShell `tar.gz` archiwa są dostarczane dla platformy z systemem macOS w celu umożliwienia zaawansowanych scenariuszach wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="d49c3-133">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="d49c3-134">Instalowanie pliku binarnego archiwów w systemie macOS</span><span class="sxs-lookup"><span data-stu-id="d49c3-134">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.2.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.2.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.2.0/pwsh /usr/local/bin/pwsh
```

<span data-ttu-id="d49c3-135">Zainstaluj [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="d49c3-135">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="d49c3-136">Biblioteki OpenSSL jest wymagany dla operacji modelu wspólnych informacji i komunikacji zdalnej programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d49c3-136">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="d49c3-137">Instalacja zależności</span><span class="sxs-lookup"><span data-stu-id="d49c3-137">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="d49c3-138">Zainstaluj narzędzia wiersza polecenia programu XCode</span><span class="sxs-lookup"><span data-stu-id="d49c3-138">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="d49c3-139">Zainstalować protokół OpenSSL</span><span class="sxs-lookup"><span data-stu-id="d49c3-139">Install OpenSSL</span></span>

<span data-ttu-id="d49c3-140">Biblioteki OpenSSL jest wymagany dla operacji modelu wspólnych informacji i komunikacji zdalnej programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d49c3-140">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="d49c3-141">Można zainstalować za pomocą MacPorts lub Brew.</span><span class="sxs-lookup"><span data-stu-id="d49c3-141">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="d49c3-142">Zainstalować protokół OpenSSL, za pośrednictwem Brew</span><span class="sxs-lookup"><span data-stu-id="d49c3-142">Install OpenSSL via Brew</span></span>

<span data-ttu-id="d49c3-143">Zobacz [o Brew](#about-brew) uzyskać informacji na temat Brew.</span><span class="sxs-lookup"><span data-stu-id="d49c3-143">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="d49c3-144">Aby zainstalować protokół OpenSSL, uruchom `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="d49c3-144">To install OpenSSL, run `brew install openssl`.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="d49c3-145">Zainstalować protokół OpenSSL, za pośrednictwem MacPorts</span><span class="sxs-lookup"><span data-stu-id="d49c3-145">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="d49c3-146">Zainstaluj [narzędzi wiersza polecenia narzędzia XCode](#install-xcode-command-line-tools).</span><span class="sxs-lookup"><span data-stu-id="d49c3-146">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="d49c3-147">Zainstaluj MacPorts.</span><span class="sxs-lookup"><span data-stu-id="d49c3-147">Install MacPorts.</span></span>
   <span data-ttu-id="d49c3-148">Aby uzyskać instrukcje, zobacz [Przewodnik instalacji](https://guide.macports.org/chunked/installing.macports.html).</span><span class="sxs-lookup"><span data-stu-id="d49c3-148">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="d49c3-149">Zaktualizuj MacPorts uruchamiając `sudo port selfupdate`.</span><span class="sxs-lookup"><span data-stu-id="d49c3-149">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="d49c3-150">Uaktualnij pakiety MacPorts, uruchamiając `sudo port upgrade outdated`.</span><span class="sxs-lookup"><span data-stu-id="d49c3-150">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="d49c3-151">Zainstalować protokół OpenSSL, uruchamiając `sudo port install openssl`.</span><span class="sxs-lookup"><span data-stu-id="d49c3-151">Install OpenSSL by running `sudo port install openssl`.</span></span>
1. <span data-ttu-id="d49c3-152">Połącz biblioteki, aby udostępnić je do programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d49c3-152">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="d49c3-153">Odinstalowywanie programu PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="d49c3-153">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="d49c3-154">Po zainstalowaniu programu PowerShell przy użyciu Homebrew, użyj następującego polecenia do odinstalowania:</span><span class="sxs-lookup"><span data-stu-id="d49c3-154">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="d49c3-155">Po zainstalowaniu programu PowerShell direct pobrania przy użyciu programu PowerShell należy usunąć ręcznie:</span><span class="sxs-lookup"><span data-stu-id="d49c3-155">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="d49c3-156">Aby usunąć dodatkowe ścieżki programu PowerShell, zapoznaj się [ścieżki](#paths) sekcji w niniejszym dokumencie i usuwanie ścieżki przy użyciu `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="d49c3-156">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="d49c3-157">Nie jest to konieczne, jeśli został zainstalowany przy użyciu Homebrew.</span><span class="sxs-lookup"><span data-stu-id="d49c3-157">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="d49c3-158">Ścieżki</span><span class="sxs-lookup"><span data-stu-id="d49c3-158">Paths</span></span>

* <span data-ttu-id="d49c3-159">`$PSHOME` jest `/usr/local/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="d49c3-159">`$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="d49c3-160">Profile użytkowników będą odczytywane z `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="d49c3-160">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="d49c3-161">Domyślne profile będą odczytywane z `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="d49c3-161">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="d49c3-162">Moduły użytkownika zostanie odczytany z `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="d49c3-162">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="d49c3-163">Udostępnione moduły będą odczytywane z `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="d49c3-163">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="d49c3-164">Domyślne moduły będą odczytywane z `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="d49c3-164">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="d49c3-165">Historia PSReadline zostanie zarejestrowana w celu `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="d49c3-165">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="d49c3-166">Profile przestrzegają konfiguracji dla hosta programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d49c3-166">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="d49c3-167">Aby profil domyślny specyficzne dla hosta istnieje w `Microsoft.PowerShell_profile.ps1` w tej samej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="d49c3-167">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="d49c3-168">Stosuje się do programu PowerShell [specyfikację katalogu Base XDG] [ xdg-bds] w systemie macOS.</span><span class="sxs-lookup"><span data-stu-id="d49c3-168">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="d49c3-169">Ponieważ system macOS jest typem pochodnym BSD, prefiks `/usr/local` jest używana zamiast `/opt`.</span><span class="sxs-lookup"><span data-stu-id="d49c3-169">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="d49c3-170">Dlatego `$PSHOME` jest `/usr/local/microsoft/powershell/6.2.0/`, i łącza symbolicznego, jest umieszczany na `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="d49c3-170">So, `$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="d49c3-171">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="d49c3-171">Additional Resources</span></span>

* <span data-ttu-id="d49c3-172">[Homebrew w sieci Web][brew]</span><span class="sxs-lookup"><span data-stu-id="d49c3-172">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="d49c3-173">[Repozytorium Github Homebrew][GitHub]</span><span class="sxs-lookup"><span data-stu-id="d49c3-173">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="d49c3-174">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="d49c3-174">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[Wersje]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
