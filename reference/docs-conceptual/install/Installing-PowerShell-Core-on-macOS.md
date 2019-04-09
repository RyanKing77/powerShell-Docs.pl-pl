---
title: Instalowanie programu PowerShell Core w systemie macOS
description: Informacje o instalowaniu programu PowerShell Core w systemie macOS
ms.date: 12/12/2018
ms.openlocfilehash: 7db8ca0cb6d13db8ce7f11b4a4b03b7d3f9b6feb
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293405"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="bac42-103">Instalowanie programu PowerShell Core w systemie macOS</span><span class="sxs-lookup"><span data-stu-id="bac42-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="bac42-104">Program PowerShell Core obsługuje system macOS 10.12 i wyższych.</span><span class="sxs-lookup"><span data-stu-id="bac42-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="bac42-105">Wszystkie pakiety są dostępne w usłudze GitHub [zwalnia][] strony.</span><span class="sxs-lookup"><span data-stu-id="bac42-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="bac42-106">Po zainstalowaniu pakietu Uruchom `pwsh` z poziomu terminalu.</span><span class="sxs-lookup"><span data-stu-id="bac42-106">After the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="about-brew"></a><span data-ttu-id="bac42-107">Temat Brew</span><span class="sxs-lookup"><span data-stu-id="bac42-107">About Brew</span></span>

<span data-ttu-id="bac42-108">[Homebrew] [ brew] to Menedżer pakietów preferowanych dla systemu macOS.</span><span class="sxs-lookup"><span data-stu-id="bac42-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="bac42-109">Jeśli `brew` nie znaleziono polecenia, musisz zainstalować następujące Homebrew [zgodnie z instrukcjami][brew].</span><span class="sxs-lookup"><span data-stu-id="bac42-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="bac42-110">Instalacja najnowsza wersja stabilna za pośrednictwem Homebrew w systemie macOS 10.12 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="bac42-110">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="bac42-111">Zobacz [o Brew](#about-brew) uzyskać informacji na temat Brew.</span><span class="sxs-lookup"><span data-stu-id="bac42-111">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="bac42-112">Teraz można zainstalować programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="bac42-112">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="bac42-113">Na koniec sprawdź, czy Twoja instalacja działa prawidłowo:</span><span class="sxs-lookup"><span data-stu-id="bac42-113">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="bac42-114">Po udostępnieniu nowej wersji programu PowerShell, zaktualizuj wzory firmy Homebrew i Uaktualnij program PowerShell:</span><span class="sxs-lookup"><span data-stu-id="bac42-114">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="bac42-115">Powyższe polecenia mogą być wywoływane z w ramach hosta programu PowerShell (pwsh), ale następnie powłoki programu PowerShell, należy ponownie uruchomić, aby zakończyć uaktualnianie, a następnie Odśwież wartości widocznych na `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="bac42-115">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="bac42-116">Instalacja najnowszą wersję zapoznawczą wersji za pomocą Homebrew w systemie macOS 10.12 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="bac42-116">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="bac42-117">Zobacz [o Brew](#about-brew) uzyskać informacji na temat Brew.</span><span class="sxs-lookup"><span data-stu-id="bac42-117">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="bac42-118">Po zainstalowaniu Homebrew, można zainstalować programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bac42-118">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="bac42-119">Najpierw zainstaluj [wersji Cask] [ cask-versions] pakiet, który umożliwia zainstalowanie alternatywne wersje pakietów cask:</span><span class="sxs-lookup"><span data-stu-id="bac42-119">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="bac42-120">Teraz można zainstalować programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="bac42-120">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="bac42-121">Na koniec sprawdź, czy Twoja instalacja działa prawidłowo:</span><span class="sxs-lookup"><span data-stu-id="bac42-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="bac42-122">Po udostępnieniu nowej wersji programu PowerShell, zaktualizuj wzory firmy Homebrew i Uaktualnij program PowerShell:</span><span class="sxs-lookup"><span data-stu-id="bac42-122">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="bac42-123">Powyższe polecenia mogą być wywoływane z w ramach hosta programu PowerShell (pwsh), ale następnie powłoki programu PowerShell, należy ponownie uruchomić, aby ukończyć uaktualnienie.</span><span class="sxs-lookup"><span data-stu-id="bac42-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="bac42-124">i Odśwież wartości widocznych na `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="bac42-124">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="bac42-125">Instalację za pomocą bezpośredniego pobierania</span><span class="sxs-lookup"><span data-stu-id="bac42-125">Installation via Direct Download</span></span>

<span data-ttu-id="bac42-126">Pobierz pakiet zapisanego pakietu</span><span class="sxs-lookup"><span data-stu-id="bac42-126">Download the PKG package</span></span>
`powershell-6.2.0-osx-x64.pkg`
<span data-ttu-id="bac42-127">z [zwalnia][] strony na komputerze z systemem macOS.</span><span class="sxs-lookup"><span data-stu-id="bac42-127">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="bac42-128">Możesz kliknij dwukrotnie plik i postępuj zgodnie z instrukcjami lub zainstalować ją z poziomu terminalu:</span><span class="sxs-lookup"><span data-stu-id="bac42-128">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.2.0-osx-x64.pkg -target /
```

<span data-ttu-id="bac42-129">Zainstaluj [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="bac42-129">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="bac42-130">Biblioteki OpenSSL jest wymagany dla operacji modelu wspólnych informacji i komunikacji zdalnej programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bac42-130">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="bac42-131">Binarny archiwa</span><span class="sxs-lookup"><span data-stu-id="bac42-131">Binary Archives</span></span>

<span data-ttu-id="bac42-132">Plik binarny programu PowerShell `tar.gz` archiwa są dostarczane dla platformy z systemem macOS w celu umożliwienia zaawansowanych scenariuszach wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="bac42-132">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="bac42-133">Instalowanie pliku binarnego archiwów w systemie macOS</span><span class="sxs-lookup"><span data-stu-id="bac42-133">Installing binary archives on macOS</span></span>

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

<span data-ttu-id="bac42-134">Zainstaluj [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="bac42-134">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="bac42-135">Biblioteki OpenSSL jest wymagany dla operacji modelu wspólnych informacji i komunikacji zdalnej programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bac42-135">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="bac42-136">Instalacja zależności</span><span class="sxs-lookup"><span data-stu-id="bac42-136">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="bac42-137">Zainstaluj narzędzia wiersza polecenia programu XCode</span><span class="sxs-lookup"><span data-stu-id="bac42-137">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="bac42-138">Zainstalować protokół OpenSSL</span><span class="sxs-lookup"><span data-stu-id="bac42-138">Install OpenSSL</span></span>

<span data-ttu-id="bac42-139">Biblioteki OpenSSL jest wymagany dla operacji modelu wspólnych informacji i komunikacji zdalnej programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bac42-139">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="bac42-140">Można zainstalować za pomocą MacPorts lub Brew.</span><span class="sxs-lookup"><span data-stu-id="bac42-140">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="bac42-141">Zainstalować protokół OpenSSL, za pośrednictwem Brew</span><span class="sxs-lookup"><span data-stu-id="bac42-141">Install OpenSSL via Brew</span></span>

<span data-ttu-id="bac42-142">Zobacz [o Brew](#about-brew) uzyskać informacji na temat Brew.</span><span class="sxs-lookup"><span data-stu-id="bac42-142">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="bac42-143">Aby zainstalować protokół OpenSSL, uruchom `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="bac42-143">To install OpenSSL, run `brew install openssl`.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="bac42-144">Zainstalować protokół OpenSSL, za pośrednictwem MacPorts</span><span class="sxs-lookup"><span data-stu-id="bac42-144">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="bac42-145">Zainstaluj [narzędzi wiersza polecenia narzędzia XCode](#install-xcode-command-line-tools).</span><span class="sxs-lookup"><span data-stu-id="bac42-145">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="bac42-146">Zainstaluj MacPorts.</span><span class="sxs-lookup"><span data-stu-id="bac42-146">Install MacPorts.</span></span>
   <span data-ttu-id="bac42-147">Aby uzyskać instrukcje, zobacz [Przewodnik instalacji](https://guide.macports.org/chunked/installing.macports.html).</span><span class="sxs-lookup"><span data-stu-id="bac42-147">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="bac42-148">Zaktualizuj MacPorts uruchamiając `sudo port selfupdate`.</span><span class="sxs-lookup"><span data-stu-id="bac42-148">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="bac42-149">Uaktualnij pakiety MacPorts, uruchamiając `sudo port upgrade outdated`.</span><span class="sxs-lookup"><span data-stu-id="bac42-149">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="bac42-150">Zainstalować protokół OpenSSL, uruchamiając `sudo port install openssl`.</span><span class="sxs-lookup"><span data-stu-id="bac42-150">Install OpenSSL by running `sudo port install openssl`.</span></span>
1. <span data-ttu-id="bac42-151">Połącz biblioteki, aby udostępnić je do programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="bac42-151">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="bac42-152">Odinstalowywanie programu PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="bac42-152">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="bac42-153">Po zainstalowaniu programu PowerShell przy użyciu Homebrew, użyj następującego polecenia do odinstalowania:</span><span class="sxs-lookup"><span data-stu-id="bac42-153">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="bac42-154">Po zainstalowaniu programu PowerShell direct pobrania przy użyciu programu PowerShell należy usunąć ręcznie:</span><span class="sxs-lookup"><span data-stu-id="bac42-154">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="bac42-155">Aby usunąć dodatkowe ścieżki programu PowerShell, zapoznaj się [ścieżki](#paths) sekcji w niniejszym dokumencie i usuwanie ścieżki przy użyciu `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="bac42-155">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="bac42-156">Nie jest to konieczne, jeśli został zainstalowany przy użyciu Homebrew.</span><span class="sxs-lookup"><span data-stu-id="bac42-156">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="bac42-157">Ścieżki</span><span class="sxs-lookup"><span data-stu-id="bac42-157">Paths</span></span>

* `$PSHOME` <span data-ttu-id="bac42-158">jest</span><span class="sxs-lookup"><span data-stu-id="bac42-158">is</span></span> `/usr/local/microsoft/powershell/6.2.0/`
* <span data-ttu-id="bac42-159">Profile użytkowników będą odczytywane z</span><span class="sxs-lookup"><span data-stu-id="bac42-159">User profiles will be read from</span></span> `~/.config/powershell/profile.ps1`
* <span data-ttu-id="bac42-160">Domyślne profile będą odczytywane z</span><span class="sxs-lookup"><span data-stu-id="bac42-160">Default profiles will be read from</span></span> `$PSHOME/profile.ps1`
* <span data-ttu-id="bac42-161">Moduły użytkownika zostanie odczytany z</span><span class="sxs-lookup"><span data-stu-id="bac42-161">User modules will be read from</span></span> `~/.local/share/powershell/Modules`
* <span data-ttu-id="bac42-162">Udostępnione moduły będą odczytywane z</span><span class="sxs-lookup"><span data-stu-id="bac42-162">Shared modules will be read from</span></span> `/usr/local/share/powershell/Modules`
* <span data-ttu-id="bac42-163">Domyślne moduły będą odczytywane z</span><span class="sxs-lookup"><span data-stu-id="bac42-163">Default modules will be read from</span></span> `$PSHOME/Modules`
* <span data-ttu-id="bac42-164">Historia PSReadline zostanie zarejestrowana w celu</span><span class="sxs-lookup"><span data-stu-id="bac42-164">PSReadline history will be recorded to</span></span> `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

<span data-ttu-id="bac42-165">Profile przestrzegają konfiguracji dla hosta programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bac42-165">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="bac42-166">Aby profil domyślny specyficzne dla hosta istnieje w `Microsoft.PowerShell_profile.ps1` w tej samej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="bac42-166">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="bac42-167">Stosuje się do programu PowerShell [specyfikację katalogu Base XDG] [ xdg-bds] w systemie macOS.</span><span class="sxs-lookup"><span data-stu-id="bac42-167">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="bac42-168">Ponieważ system macOS jest typem pochodnym BSD, prefiks `/usr/local` jest używana zamiast `/opt`.</span><span class="sxs-lookup"><span data-stu-id="bac42-168">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="bac42-169">Dlatego `$PSHOME` jest `/usr/local/microsoft/powershell/6.2.0/`, i łącza symbolicznego, jest umieszczany na `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="bac42-169">So, `$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="bac42-170">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="bac42-170">Additional Resources</span></span>

* <span data-ttu-id="bac42-171">[Homebrew w sieci Web][brew]</span><span class="sxs-lookup"><span data-stu-id="bac42-171">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="bac42-172">[Repozytorium Github Homebrew][GitHub]</span><span class="sxs-lookup"><span data-stu-id="bac42-172">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="bac42-173">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="bac42-173">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[<span data-ttu-id="bac42-174">Wersje</span><span class="sxs-lookup"><span data-stu-id="bac42-174">releases</span></span>]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
