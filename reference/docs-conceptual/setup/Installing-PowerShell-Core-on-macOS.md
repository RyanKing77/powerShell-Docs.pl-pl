---
title: Instalowanie programu PowerShell Core w systemie macOS
description: Informacje o instalowaniu programu PowerShell Core w systemie macOS
ms.date: 08/06/2018
ms.openlocfilehash: e226cd64f8788ae74dc72fdc0cd219923b7a2cd6
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002363"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="41a1e-103">Instalowanie programu PowerShell Core w systemie macOS</span><span class="sxs-lookup"><span data-stu-id="41a1e-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="41a1e-104">Program PowerShell Core obsługuje system macOS 10.12 i wyższych.</span><span class="sxs-lookup"><span data-stu-id="41a1e-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="41a1e-105">Wszystkie pakiety są dostępne w usłudze GitHub [zwalnia][] strony.</span><span class="sxs-lookup"><span data-stu-id="41a1e-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="41a1e-106">Po zainstalowaniu pakietu Uruchom `pwsh` z poziomu terminalu.</span><span class="sxs-lookup"><span data-stu-id="41a1e-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="41a1e-107">Instalacja najnowsza wersja stabilna za pośrednictwem Homebrew w systemie macOS 10.12 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="41a1e-107">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="41a1e-108">[Homebrew] [ brew] to Menedżer pakietów preferowanych dla systemu macOS.</span><span class="sxs-lookup"><span data-stu-id="41a1e-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="41a1e-109">Jeśli `brew` nie znaleziono polecenia, musisz zainstalować następujące Homebrew [zgodnie z instrukcjami][brew].</span><span class="sxs-lookup"><span data-stu-id="41a1e-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="41a1e-110">Teraz można zainstalować programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="41a1e-110">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="41a1e-111">Na koniec sprawdź, czy Twoja instalacja działa prawidłowo:</span><span class="sxs-lookup"><span data-stu-id="41a1e-111">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="41a1e-112">Po udostępnieniu nowej wersji programu PowerShell, po prostu zaktualizuj wzory firmy Homebrew i Uaktualnij program PowerShell:</span><span class="sxs-lookup"><span data-stu-id="41a1e-112">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="41a1e-113">Powyższe polecenia mogą być wywoływane z w ramach hosta programu PowerShell (pwsh), ale następnie powłoki programu PowerShell, należy ponownie uruchomić, aby zakończyć uaktualnianie, a następnie Odśwież wartości widocznych na $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="41a1e-113">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="41a1e-114">Instalacja najnowszą wersję zapoznawczą wersji za pomocą Homebrew w systemie macOS 10.12 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="41a1e-114">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="41a1e-115">[Homebrew] [ brew] to Menedżer pakietów preferowanych dla systemu macOS.</span><span class="sxs-lookup"><span data-stu-id="41a1e-115">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="41a1e-116">Jeśli `brew` nie znaleziono polecenia, musisz zainstalować następujące Homebrew [zgodnie z instrukcjami][brew].</span><span class="sxs-lookup"><span data-stu-id="41a1e-116">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="41a1e-117">Po zainstalowaniu Homebrew Instalowanie programu PowerShell jest proste.</span><span class="sxs-lookup"><span data-stu-id="41a1e-117">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="41a1e-118">Najpierw zainstaluj [wersji Cask] [ cask-versions] można zainstalować alternatywne wersje pakietów cask:</span><span class="sxs-lookup"><span data-stu-id="41a1e-118">First, install [Cask-Versions][cask-versions] which lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="41a1e-119">Teraz można zainstalować programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="41a1e-119">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="41a1e-120">Na koniec sprawdź, czy Twoja instalacja działa prawidłowo:</span><span class="sxs-lookup"><span data-stu-id="41a1e-120">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="41a1e-121">Po udostępnieniu nowej wersji programu PowerShell, po prostu zaktualizuj wzory firmy Homebrew i Uaktualnij program PowerShell:</span><span class="sxs-lookup"><span data-stu-id="41a1e-121">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="41a1e-122">Powyższe polecenia mogą być wywoływane z w ramach hosta programu PowerShell (pwsh), ale następnie powłoki programu PowerShell, należy ponownie uruchomić, aby ukończyć uaktualnienie.</span><span class="sxs-lookup"><span data-stu-id="41a1e-122">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="41a1e-123">i Odśwież wartości widocznych na $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="41a1e-123">and refresh the values shown in $PSVersionTable.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="41a1e-124">Instalację za pomocą bezpośredniego pobierania</span><span class="sxs-lookup"><span data-stu-id="41a1e-124">Installation via Direct Download</span></span>

<span data-ttu-id="41a1e-125">Pobierz pakiet zapisanego pakietu `powershell-6.1.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="41a1e-125">Download the PKG package `powershell-6.1.0-osx-x64.pkg`</span></span>
<span data-ttu-id="41a1e-126">z [zwalnia][] strony na komputerze z systemem macOS.</span><span class="sxs-lookup"><span data-stu-id="41a1e-126">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="41a1e-127">Możesz kliknij dwukrotnie plik i postępuj zgodnie z instrukcjami lub zainstalować ją z poziomu terminalu:</span><span class="sxs-lookup"><span data-stu-id="41a1e-127">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="41a1e-128">Binarny archiwa</span><span class="sxs-lookup"><span data-stu-id="41a1e-128">Binary Archives</span></span>

<span data-ttu-id="41a1e-129">Plik binarny programu PowerShell `tar.gz` archiwa są dostarczane dla platformy z systemem macOS w celu umożliwienia zaawansowanych scenariuszach wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="41a1e-129">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="41a1e-130">Instalowanie pliku binarnego archiwów w systemie macOS</span><span class="sxs-lookup"><span data-stu-id="41a1e-130">Installing binary archives on macOS</span></span>

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

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="41a1e-131">Odinstalowywanie programu PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="41a1e-131">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="41a1e-132">Po zainstalowaniu programu PowerShell przy użyciu Homebrew, dezinstalacja jest łatwe:</span><span class="sxs-lookup"><span data-stu-id="41a1e-132">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="41a1e-133">Po zainstalowaniu programu PowerShell direct pobrania przy użyciu programu PowerShell należy usunąć ręcznie:</span><span class="sxs-lookup"><span data-stu-id="41a1e-133">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="41a1e-134">Aby usunąć dodatkowe ścieżki programu PowerShell, zobacz [ścieżki](#paths) sekcji w niniejszym dokumencie i usuń żądany ścieżek przy użyciu `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="41a1e-134">To remove the additional PowerShell paths, please see the [paths](#paths) section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="41a1e-135">Nie jest to konieczne, jeśli został zainstalowany przy użyciu Homebrew.</span><span class="sxs-lookup"><span data-stu-id="41a1e-135">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="41a1e-136">Ścieżki</span><span class="sxs-lookup"><span data-stu-id="41a1e-136">Paths</span></span>

* <span data-ttu-id="41a1e-137">`$PSHOME` jest `/usr/local/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="41a1e-137">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="41a1e-138">Profile użytkowników będą odczytywane z `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="41a1e-138">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="41a1e-139">Domyślne profile będą odczytywane z `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="41a1e-139">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="41a1e-140">Moduły użytkownika zostanie odczytany z `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="41a1e-140">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="41a1e-141">Udostępnione moduły będą odczytywane z `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="41a1e-141">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="41a1e-142">Domyślne moduły będą odczytywane z `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="41a1e-142">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="41a1e-143">Historia PSReadline zostanie zarejestrowana w celu `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="41a1e-143">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="41a1e-144">Profile przestrzegają konfiguracji dla hosta programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="41a1e-144">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="41a1e-145">Dlatego domyślne profile specyficzne dla hosta istnieje w `Microsoft.PowerShell_profile.ps1` w tej samej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="41a1e-145">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="41a1e-146">Stosuje się do programu PowerShell [specyfikację katalogu Base XDG] [ xdg-bds] w systemie macOS.</span><span class="sxs-lookup"><span data-stu-id="41a1e-146">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="41a1e-147">Ponieważ system macOS jest typem pochodnym BSD, prefiks `/usr/local` jest używana zamiast `/opt`.</span><span class="sxs-lookup"><span data-stu-id="41a1e-147">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="41a1e-148">W związku z tym `$PSHOME` jest `/usr/local/microsoft/powershell/6.1.0/`, a Link symboliczny jest umieszczany na `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="41a1e-148">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="41a1e-149">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="41a1e-149">Additional Resources</span></span>

* <span data-ttu-id="41a1e-150">[Homebrew w sieci Web][brew]</span><span class="sxs-lookup"><span data-stu-id="41a1e-150">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="41a1e-151">[Repozytorium Github Homebrew][GitHub]</span><span class="sxs-lookup"><span data-stu-id="41a1e-151">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="41a1e-152">[Homebrew Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="41a1e-152">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[zwalnia]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
