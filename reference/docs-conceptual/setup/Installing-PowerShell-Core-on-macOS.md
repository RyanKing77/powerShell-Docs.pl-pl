---
title: Instalowanie programu PowerShell Core w systemie macOS
description: Informacje o instalowaniu programu PowerShell Core w systemie macOS
ms.date: 08/06/2018
ms.openlocfilehash: 50b8dbbf26f02580e4be45978c926d5337da6b63
ms.sourcegitcommit: b235c58b34d23317076540631f5cf83f1f309c0d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45557164"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="06f37-103">Instalowanie programu PowerShell Core w systemie macOS</span><span class="sxs-lookup"><span data-stu-id="06f37-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="06f37-104">Program PowerShell Core obsługuje system macOS 10.12 i wyższych.</span><span class="sxs-lookup"><span data-stu-id="06f37-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="06f37-105">Wszystkie pakiety są dostępne w usłudze GitHub [zwalnia][] strony.</span><span class="sxs-lookup"><span data-stu-id="06f37-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="06f37-106">Po zainstalowaniu pakietu Uruchom `pwsh` z poziomu terminalu.</span><span class="sxs-lookup"><span data-stu-id="06f37-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

### <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="06f37-107">Instalacja najnowszą wersję zapoznawczą wersji za pomocą Homebrew w systemie macOS 10.12 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="06f37-107">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="06f37-108">[Homebrew] [ brew] to Menedżer pakietów preferowanych dla systemu macOS.</span><span class="sxs-lookup"><span data-stu-id="06f37-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="06f37-109">Jeśli `brew` nie znaleziono polecenia, musisz zainstalować następujące Homebrew [zgodnie z instrukcjami][brew].</span><span class="sxs-lookup"><span data-stu-id="06f37-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="06f37-110">Po zainstalowaniu Homebrew Instalowanie programu PowerShell jest proste.</span><span class="sxs-lookup"><span data-stu-id="06f37-110">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="06f37-111">Najpierw zainstaluj [Homebrew Cask][cask], dzięki czemu można zainstalować dodatkowych pakietów i instalacji [Cask wersji] [cask wersja], która pozwala na instalowanie alternatywne wersje pakietów:</span><span class="sxs-lookup"><span data-stu-id="06f37-111">First, install [Homebrew-Cask][cask], so you can install more packages and install [Cask-Versions][cask-version] which lets you install alternative versions of packages:</span></span>

```sh
brew tap caskroom/cask
brew tap caskroom/versions
```

<span data-ttu-id="06f37-112">Teraz można zainstalować programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="06f37-112">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="06f37-113">Na koniec sprawdź, czy Twoja instalacja działa prawidłowo:</span><span class="sxs-lookup"><span data-stu-id="06f37-113">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="06f37-114">Po udostępnieniu nowej wersji programu PowerShell, po prostu zaktualizuj wzory firmy Homebrew i Uaktualnij program PowerShell:</span><span class="sxs-lookup"><span data-stu-id="06f37-114">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="06f37-115">Powyższe polecenia mogą być wywoływane z w ramach hosta programu PowerShell (pwsh), ale następnie powłoki programu PowerShell, należy ponownie uruchomić, aby ukończyć uaktualnienie.</span><span class="sxs-lookup"><span data-stu-id="06f37-115">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="06f37-116">i Odśwież wartości widocznych na $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="06f37-116">and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions

### <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="06f37-117">Instalacja najnowszą wersję zapoznawczą wersji za pomocą Homebrew w systemie macOS 10.12 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="06f37-117">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="06f37-118">[Homebrew] [ brew] to Menedżer pakietów preferowanych dla systemu macOS.</span><span class="sxs-lookup"><span data-stu-id="06f37-118">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="06f37-119">Jeśli `brew` nie znaleziono polecenia, musisz zainstalować następujące Homebrew [zgodnie z instrukcjami][brew].</span><span class="sxs-lookup"><span data-stu-id="06f37-119">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="06f37-120">Po zainstalowaniu Homebrew Instalowanie programu PowerShell jest proste.</span><span class="sxs-lookup"><span data-stu-id="06f37-120">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="06f37-121">Najpierw zainstaluj [Homebrew Cask][cask], dzięki czemu można zainstalować dodatkowych pakietów i instalacji [Cask wersji] [cask wersja], która pozwala na instalowanie alternatywne wersje pakietów:</span><span class="sxs-lookup"><span data-stu-id="06f37-121">First, install [Homebrew-Cask][cask], so you can install more packages and install [Cask-Versions][cask-version] which lets you install alternative versions of packages:</span></span>

```sh
brew tap caskroom/cask
brew tap caskroom/versions
```

<span data-ttu-id="06f37-122">Teraz można zainstalować programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="06f37-122">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="06f37-123">Na koniec sprawdź, czy Twoja instalacja działa prawidłowo:</span><span class="sxs-lookup"><span data-stu-id="06f37-123">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="06f37-124">Po udostępnieniu nowej wersji programu PowerShell, po prostu zaktualizuj wzory firmy Homebrew i Uaktualnij program PowerShell:</span><span class="sxs-lookup"><span data-stu-id="06f37-124">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="06f37-125">Powyższe polecenia mogą być wywoływane z w ramach hosta programu PowerShell (pwsh), ale następnie powłoki programu PowerShell, należy ponownie uruchomić, aby ukończyć uaktualnienie.</span><span class="sxs-lookup"><span data-stu-id="06f37-125">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="06f37-126">i Odśwież wartości widocznych na $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="06f37-126">and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions

### <a name="installation-via-direct-download"></a><span data-ttu-id="06f37-127">Instalację za pomocą bezpośredniego pobierania</span><span class="sxs-lookup"><span data-stu-id="06f37-127">Installation via Direct Download</span></span>

<span data-ttu-id="06f37-128">Pobierz pakiet zapisanego pakietu `powershell-6.1.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="06f37-128">Download the PKG package `powershell-6.1.0-osx-x64.pkg`</span></span>
<span data-ttu-id="06f37-129">z [zwalnia][] strony na komputerze z systemem macOS.</span><span class="sxs-lookup"><span data-stu-id="06f37-129">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="06f37-130">Możesz kliknij dwukrotnie plik i postępuj zgodnie z instrukcjami lub zainstalować ją z poziomu terminalu:</span><span class="sxs-lookup"><span data-stu-id="06f37-130">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="06f37-131">Binarny archiwa</span><span class="sxs-lookup"><span data-stu-id="06f37-131">Binary Archives</span></span>

<span data-ttu-id="06f37-132">Plik binarny programu PowerShell `tar.gz` archiwa znajdują się na systemach macOS i Linux platformy, aby włączyć zaawansowanych scenariuszach wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="06f37-132">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="06f37-133">Instalowanie pliku binarnego archiwów w systemie macOS</span><span class="sxs-lookup"><span data-stu-id="06f37-133">Installing binary archives on macOS</span></span>

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

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="06f37-134">Odinstalowywanie programu PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="06f37-134">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="06f37-135">Po zainstalowaniu programu PowerShell przy użyciu Homebrew, dezinstalacja jest łatwe:</span><span class="sxs-lookup"><span data-stu-id="06f37-135">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="06f37-136">Po zainstalowaniu programu PowerShell direct pobrania przy użyciu programu PowerShell należy usunąć ręcznie:</span><span class="sxs-lookup"><span data-stu-id="06f37-136">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="06f37-137">Aby usunąć dodatkowe ścieżki programu PowerShell, zobacz [ścieżki][] sekcji w niniejszym dokumencie i usuń żądany ścieżek przy użyciu `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="06f37-137">To remove the additional PowerShell paths, please see the [paths][] section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="06f37-138">Nie jest to konieczne, jeśli został zainstalowany przy użyciu Homebrew.</span><span class="sxs-lookup"><span data-stu-id="06f37-138">This is not necessary if you installed with Homebrew.</span></span>

[Ścieżki]:#paths
[paths]:#paths

## <a name="paths"></a><span data-ttu-id="06f37-140">Ścieżki</span><span class="sxs-lookup"><span data-stu-id="06f37-140">Paths</span></span>

* <span data-ttu-id="06f37-141">`$PSHOME` jest `/usr/local/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="06f37-141">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="06f37-142">Profile użytkowników będą odczytywane z `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="06f37-142">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="06f37-143">Domyślne profile będą odczytywane z `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="06f37-143">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="06f37-144">Moduły użytkownika zostanie odczytany z `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="06f37-144">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="06f37-145">Udostępnione moduły będą odczytywane z `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="06f37-145">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="06f37-146">Domyślne moduły będą odczytywane z `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="06f37-146">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="06f37-147">Historia PSReadline zostanie zarejestrowana w celu `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="06f37-147">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="06f37-148">Profile przestrzegają konfiguracji dla hosta programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="06f37-148">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="06f37-149">Dlatego domyślne profile specyficzne dla hosta istnieje w `Microsoft.PowerShell_profile.ps1` w tej samej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="06f37-149">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="06f37-150">Stosuje się do programu PowerShell [specyfikację katalogu Base XDG] [ xdg-bds] w systemie macOS.</span><span class="sxs-lookup"><span data-stu-id="06f37-150">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="06f37-151">Ponieważ system macOS jest typem pochodnym BSD, prefiks `/usr/local` jest używana zamiast `/opt`.</span><span class="sxs-lookup"><span data-stu-id="06f37-151">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="06f37-152">W związku z tym `$PSHOME` jest `/usr/local/microsoft/powershell/6.1.0/`, a Link symboliczny jest umieszczany na `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="06f37-152">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="06f37-153">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="06f37-153">Additional Resources</span></span>

* <span data-ttu-id="06f37-154">[Homebrew w sieci Web][brew]</span><span class="sxs-lookup"><span data-stu-id="06f37-154">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="06f37-155">[Repozytorium Github Homebrew][GitHub]</span><span class="sxs-lookup"><span data-stu-id="06f37-155">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="06f37-156">[Homebrew Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="06f37-156">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[zwalnia]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
