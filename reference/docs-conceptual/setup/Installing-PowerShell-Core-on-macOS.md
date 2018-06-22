# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="9955d-101">Instalowanie programu PowerShell Core w systemie macOS</span><span class="sxs-lookup"><span data-stu-id="9955d-101">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="9955d-102">PowerShell Core obsługuje macOS 10.12 i wyższych.</span><span class="sxs-lookup"><span data-stu-id="9955d-102">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="9955d-103">Wszystkie pakiety są dostępne w naszej witrynie GitHub [Wersje][] strony.</span><span class="sxs-lookup"><span data-stu-id="9955d-103">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="9955d-104">Po zainstalowaniu pakietu `pwsh` z terminalu.</span><span class="sxs-lookup"><span data-stu-id="9955d-104">Once the package is installed, run `pwsh` from a terminal.</span></span>

### <a name="installation-via-homebrew-on-macos-1012"></a><span data-ttu-id="9955d-105">Instalacja za pomocą oprogramowania Homebrew na macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="9955d-105">Installation via Homebrew on macOS 10.12</span></span>

<span data-ttu-id="9955d-106">[Homebrew] [ brew] jest Menedżer pakietów preferowanych dla macOS.</span><span class="sxs-lookup"><span data-stu-id="9955d-106">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="9955d-107">Jeśli `brew` nie znaleziono polecenia, należy zainstalować następujące Homebrew [zgodnie z instrukcjami][brew].</span><span class="sxs-lookup"><span data-stu-id="9955d-107">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="9955d-108">Po zainstalowaniu oprogramowania Homebrew Instalowanie programu PowerShell jest bardzo proste.</span><span class="sxs-lookup"><span data-stu-id="9955d-108">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="9955d-109">Najpierw zainstaluj [pojemnika transportowego Homebrew][cask], więc można zainstalować więcej pakietów:</span><span class="sxs-lookup"><span data-stu-id="9955d-109">First, install [Homebrew-Cask][cask], so you can install more packages:</span></span>

```sh
brew tap caskroom/cask
```

<span data-ttu-id="9955d-110">Teraz można zainstalować programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="9955d-110">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="9955d-111">Na koniec sprawdź, czy instalacji działa prawidłowo:</span><span class="sxs-lookup"><span data-stu-id="9955d-111">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="9955d-112">Po udostępnieniu nowej wersji programu PowerShell, po prostu zaktualizuj wzory dla oprogramowania Homebrew i uaktualnienia programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="9955d-112">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="9955d-113">W ramach hosta programu PowerShell (pwsh) można wywołać z powyższych poleceń, ale następnie powłoki PowerShell, należy ponownie uruchomić, aby dokończyć uaktualnianie i Odśwież wartości widoczne w $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="9955d-113">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download"></a><span data-ttu-id="9955d-114">Instalacja za pośrednictwem bezpośredniego pobierania</span><span class="sxs-lookup"><span data-stu-id="9955d-114">Installation via Direct Download</span></span>

<span data-ttu-id="9955d-115">Pobierz pakiet PKG `powershell-6.0.2-osx.10.12-x64.pkg` z [Wersje][] strony na tym komputerze macOS.</span><span class="sxs-lookup"><span data-stu-id="9955d-115">Download the PKG package `powershell-6.0.2-osx.10.12-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="9955d-116">Możesz kliknij dwukrotnie plik i postępuj zgodnie z monitami lub zainstalować go z terminala:</span><span class="sxs-lookup"><span data-stu-id="9955d-116">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="9955d-117">Archiwa binarne</span><span class="sxs-lookup"><span data-stu-id="9955d-117">Binary Archives</span></span>

<span data-ttu-id="9955d-118">Dane binarne środowiska PowerShell `tar.gz` archiwa są udostępniane dla macOS i platformy Linux, aby włączyć zaawansowanych scenariuszach wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="9955d-118">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="9955d-119">Instalowanie archiwa binarnego na macOS</span><span class="sxs-lookup"><span data-stu-id="9955d-119">Installing binary archives on macOS</span></span>

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

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="9955d-120">Odinstalowywanie programu PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="9955d-120">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="9955d-121">Po zainstalowaniu programu PowerShell z oprogramowania Homebrew dezinstalacji jest łatwe:</span><span class="sxs-lookup"><span data-stu-id="9955d-121">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="9955d-122">Po zainstalowaniu programu PowerShell za pomocą bezpośredniego pobierania programu PowerShell musi zostać usunięte ręcznie:</span><span class="sxs-lookup"><span data-stu-id="9955d-122">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="9955d-123">Aby usunąć dodatkowe ścieżki programu PowerShell, zobacz [ścieżki][] sekcję w tym dokumencie i usunąć żądaną ścieżek przy użyciu `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="9955d-123">To remove the additional PowerShell paths, please see the [paths][] section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="9955d-124">Nie jest to konieczne, jeśli podczas instalacji oprogramowania Homebrew.</span><span class="sxs-lookup"><span data-stu-id="9955d-124">This is not necessary if you installed with Homebrew.</span></span>

[Ścieżki]:#paths
[paths]:#paths

## <a name="paths"></a><span data-ttu-id="9955d-126">Ścieżki</span><span class="sxs-lookup"><span data-stu-id="9955d-126">Paths</span></span>

* <span data-ttu-id="9955d-127">`$PSHOME` jest `/usr/local/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="9955d-127">`$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="9955d-128">Profile użytkowników będą odczytywane z `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="9955d-128">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="9955d-129">Domyślne profile będą odczytywane z `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="9955d-129">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="9955d-130">Moduły użytkownika będą odczytywane z `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="9955d-130">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="9955d-131">Udostępniony moduły będą odczytywane z `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="9955d-131">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="9955d-132">Domyślne moduły będą odczytywane z `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="9955d-132">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="9955d-133">Historia PSReadline zostanie zarejestrowana w celu `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="9955d-133">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="9955d-134">Profile zgodne konfiguracji na hosta w programie PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9955d-134">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="9955d-135">Dlatego domyślnych profilów specyficzne dla hosta istnieje w `Microsoft.PowerShell_profile.ps1` w tej samej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="9955d-135">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="9955d-136">PowerShell szanuje [specyfikacji katalogu Base XDG] [ xdg-bds] na macOS.</span><span class="sxs-lookup"><span data-stu-id="9955d-136">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="9955d-137">Ponieważ system macOS jest typem pochodnym BSD, prefiks `/usr/local` jest używany zamiast `/opt`.</span><span class="sxs-lookup"><span data-stu-id="9955d-137">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="9955d-138">W związku z tym `$PSHOME` jest `/usr/local/microsoft/powershell/6.0.2/`, i Utwórz Link symboliczny znajduje się w `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="9955d-138">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

[Wersje]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
