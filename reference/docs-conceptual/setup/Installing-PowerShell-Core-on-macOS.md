---
title: Instalowanie programu PowerShell Core w systemie macOS
description: Informacje o instalowaniu programu PowerShell Core w systemie macOS
ms.date: 08/06/2018
ms.openlocfilehash: ff1814d95b3ca3fa8497069dff249fd2ad5576ef
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587469"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="8b959-103">Instalowanie programu PowerShell Core w systemie macOS</span><span class="sxs-lookup"><span data-stu-id="8b959-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="8b959-104">Program PowerShell Core obsługuje system macOS 10.12 i wyższych.</span><span class="sxs-lookup"><span data-stu-id="8b959-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="8b959-105">Wszystkie pakiety są dostępne w usłudze GitHub [zwalnia][] strony.</span><span class="sxs-lookup"><span data-stu-id="8b959-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="8b959-106">Po zainstalowaniu pakietu Uruchom `pwsh` z poziomu terminalu.</span><span class="sxs-lookup"><span data-stu-id="8b959-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

### <a name="installation-via-homebrew-on-macos-1012"></a><span data-ttu-id="8b959-107">Instalację za pomocą Homebrew w systemie macOS 10.12 +</span><span class="sxs-lookup"><span data-stu-id="8b959-107">Installation via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="8b959-108">[Homebrew] [ brew] to Menedżer pakietów preferowanych dla systemu macOS.</span><span class="sxs-lookup"><span data-stu-id="8b959-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="8b959-109">W oknie terminalu wpisz `brew` do uruchomienia Homebrew.</span><span class="sxs-lookup"><span data-stu-id="8b959-109">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="8b959-110">Jeśli `brew` nie znaleziono polecenia, musisz zainstalować następujące Homebrew [zgodnie z instrukcjami][brew].</span><span class="sxs-lookup"><span data-stu-id="8b959-110">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="8b959-111">Jeśli zainstalowano Homebrew w przeszłości, zawsze jest dobry pomysł, aby uruchomić "brew resetowania aktualizacji" & & "brew update".</span><span class="sxs-lookup"><span data-stu-id="8b959-111">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

> <span data-ttu-id="8b959-112">Starsze wersje programu Homebrew używane naciśnij "caskroom/cask", która przestarzałe i migracji do "homebrew/cask".</span><span class="sxs-lookup"><span data-stu-id="8b959-112">Older versions of Homebrew used the tap 'caskroom/cask', which has been deprecated, and migrated into 'homebrew/cask'.</span></span>  <span data-ttu-id="8b959-113">Więcej informacji znajduje się w temacie [Homebrew cask][cask].</span><span class="sxs-lookup"><span data-stu-id="8b959-113">More information can be found at [Homebrew-cask][cask].</span></span> <span data-ttu-id="8b959-114">Aby wyświetlić listę Twojej bieżącej podsłuchu, należy użyć polecenia "brew naciśnij".</span><span class="sxs-lookup"><span data-stu-id="8b959-114">Use the 'brew tap' command to list your current taps.</span></span>  <span data-ttu-id="8b959-115">Jeśli widzisz "caskroom/cask" można użyć "brew aktualizacji" Aby migrować podsłuchu Homebrew.</span><span class="sxs-lookup"><span data-stu-id="8b959-115">If you see 'caskroom/cask' you can use 'brew update' to have Homebrew migrate the taps.</span></span>

```sh
brew tap
brew update
```

<span data-ttu-id="8b959-116">Po zainstalowane/aktualizacji Homebrew, instalowanie programu PowerShell jest proste.</span><span class="sxs-lookup"><span data-stu-id="8b959-116">Once you've installed/updated Homebrew, installing PowerShell is easy.</span></span>

<span data-ttu-id="8b959-117">Aby zainstalować program PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8b959-117">To install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="8b959-118">Na koniec sprawdź, czy Twoja instalacja działa prawidłowo:</span><span class="sxs-lookup"><span data-stu-id="8b959-118">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="8b959-119">Aby zakończyć działanie programu PowerShell, a następnie wróć do powłoki bash, użyj polecenia "exit".</span><span class="sxs-lookup"><span data-stu-id="8b959-119">To exit PowerShell, and return to bash, use the 'exit' command.</span></span>
```sh
exit
```

<span data-ttu-id="8b959-120">Po udostępnieniu nowej wersji programu PowerShell, po prostu zaktualizuj wzory firmy Homebrew i Uaktualnij program PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8b959-120">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="8b959-121">Powyższe polecenia mogą być wywoływane z w ramach hosta programu PowerShell (pwsh), ale następnie powłoki programu PowerShell, należy ponownie uruchomić, aby zakończyć uaktualnianie, a następnie Odśwież wartości widocznych na $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="8b959-121">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installing-preview-via-homebrew-on-macos-1012"></a><span data-ttu-id="8b959-122">Instalowanie wersji zapoznawczej za pośrednictwem Homebrew w systemie macOS 10.12 +</span><span class="sxs-lookup"><span data-stu-id="8b959-122">Installing Preview via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="8b959-123">[Homebrew] [ brew] to Menedżer pakietów preferowanych dla systemu macOS.</span><span class="sxs-lookup"><span data-stu-id="8b959-123">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="8b959-124">W oknie terminalu wpisz `brew` do uruchomienia Homebrew.</span><span class="sxs-lookup"><span data-stu-id="8b959-124">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="8b959-125">Jeśli `brew` nie znaleziono polecenia, musisz zainstalować następujące Homebrew [zgodnie z instrukcjami][brew].</span><span class="sxs-lookup"><span data-stu-id="8b959-125">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="8b959-126">Jeśli zainstalowano Homebrew w przeszłości, zawsze jest dobry pomysł, aby uruchomić "brew resetowania aktualizacji" & & "brew update".</span><span class="sxs-lookup"><span data-stu-id="8b959-126">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

<span data-ttu-id="8b959-127">Następnie użytkownik musi nacisnąć `versions` beczki repozytorium, aby uzyskać pakiet (wersja zapoznawcza):</span><span class="sxs-lookup"><span data-stu-id="8b959-127">Then, you must tap the `versions` casks repository to get the preview package:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="8b959-128">Aby zainstalować program PowerShell w wersji zapoznawczej:</span><span class="sxs-lookup"><span data-stu-id="8b959-128">To install PowerShell Preview:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="8b959-129">Na koniec sprawdź, czy Twoja instalacja działa prawidłowo:</span><span class="sxs-lookup"><span data-stu-id="8b959-129">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="8b959-130">Podczas wydawane są nowe wersje programu PowerShell, po prostu zaktualizuj wzory firmy Homebrew i uaktualnienie wersji programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8b959-130">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell Preview:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="8b959-131">Powyższe polecenia mogą być wywoływane z w ramach hosta programu PowerShell (pwsh), ale następnie powłoki programu PowerShell, należy ponownie uruchomić, aby zakończyć uaktualnianie, a następnie Odśwież wartości widocznych na $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="8b959-131">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installation-via-direct-download"></a><span data-ttu-id="8b959-132">Instalację za pomocą bezpośredniego pobierania</span><span class="sxs-lookup"><span data-stu-id="8b959-132">Installation via Direct Download</span></span>

<span data-ttu-id="8b959-133">Pobierz pakiet PKG `powershell-6.0.2-osx.10.12-x64.pkg` z [zwalnia][] strony na komputerze z systemem macOS.</span><span class="sxs-lookup"><span data-stu-id="8b959-133">Download the PKG package `powershell-6.0.2-osx.10.12-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="8b959-134">Możesz kliknij dwukrotnie plik i postępuj zgodnie z instrukcjami lub zainstalować ją z poziomu terminalu:</span><span class="sxs-lookup"><span data-stu-id="8b959-134">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="8b959-135">Binarny archiwa</span><span class="sxs-lookup"><span data-stu-id="8b959-135">Binary Archives</span></span>

<span data-ttu-id="8b959-136">Plik binarny programu PowerShell `tar.gz` archiwa znajdują się na systemach macOS i Linux platformy, aby włączyć zaawansowanych scenariuszach wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="8b959-136">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="8b959-137">Instalowanie pliku binarnego archiwów w systemie macOS</span><span class="sxs-lookup"><span data-stu-id="8b959-137">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.2/pwsh /usr/local/bin/pwsh
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="8b959-138">Odinstalowywanie programu PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="8b959-138">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="8b959-139">Po zainstalowaniu programu PowerShell przy użyciu Homebrew, dezinstalacja jest łatwe:</span><span class="sxs-lookup"><span data-stu-id="8b959-139">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="8b959-140">Po zainstalowaniu programu PowerShell direct pobrania przy użyciu programu PowerShell należy usunąć ręcznie:</span><span class="sxs-lookup"><span data-stu-id="8b959-140">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="8b959-141">Aby usunąć dodatkowe ścieżki programu PowerShell, zobacz [ścieżki][] sekcji w niniejszym dokumencie i usuń żądany ścieżek przy użyciu `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="8b959-141">To remove the additional PowerShell paths, please see the [paths][] section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="8b959-142">Nie jest to konieczne, jeśli został zainstalowany przy użyciu Homebrew.</span><span class="sxs-lookup"><span data-stu-id="8b959-142">This is not necessary if you installed with Homebrew.</span></span>

[Ścieżki]:#paths
[paths]:#paths

## <a name="paths"></a><span data-ttu-id="8b959-144">Ścieżki</span><span class="sxs-lookup"><span data-stu-id="8b959-144">Paths</span></span>

* <span data-ttu-id="8b959-145">`$PSHOME` jest `/usr/local/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="8b959-145">`$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="8b959-146">Profile użytkowników będą odczytywane z `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="8b959-146">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="8b959-147">Domyślne profile będą odczytywane z `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="8b959-147">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="8b959-148">Moduły użytkownika zostanie odczytany z `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="8b959-148">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="8b959-149">Udostępnione moduły będą odczytywane z `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="8b959-149">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="8b959-150">Domyślne moduły będą odczytywane z `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="8b959-150">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="8b959-151">Historia PSReadline zostanie zarejestrowana w celu `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="8b959-151">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="8b959-152">Profile przestrzegają konfiguracji dla hosta programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b959-152">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="8b959-153">Dlatego domyślne profile specyficzne dla hosta istnieje w `Microsoft.PowerShell_profile.ps1` w tej samej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="8b959-153">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="8b959-154">Stosuje się do programu PowerShell [specyfikację katalogu Base XDG] [ xdg-bds] w systemie macOS.</span><span class="sxs-lookup"><span data-stu-id="8b959-154">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="8b959-155">Ponieważ system macOS jest typem pochodnym BSD, prefiks `/usr/local` jest używana zamiast `/opt`.</span><span class="sxs-lookup"><span data-stu-id="8b959-155">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="8b959-156">W związku z tym `$PSHOME` jest `/usr/local/microsoft/powershell/6.0.2/`, a Link symboliczny jest umieszczany na `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="8b959-156">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="8b959-157">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="8b959-157">Additional Resources</span></span>

* <span data-ttu-id="8b959-158">[Homebrew w sieci Web][brew]</span><span class="sxs-lookup"><span data-stu-id="8b959-158">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="8b959-159">[Repozytorium Github Homebrew][GitHub]</span><span class="sxs-lookup"><span data-stu-id="8b959-159">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="8b959-160">[Homebrew Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="8b959-160">[Homebrew-Cask][cask]</span></span>


[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[zwalnia]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
