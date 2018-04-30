# <a name="installing-powershell-core-on-macos"></a>Instalowanie programu PowerShell Core na macOS

PowerShell Core obsługuje macOS 10.12 i wyższych.
Wszystkie pakiety są dostępne w naszej witrynie GitHub [zwalnia][] strony.
Po zainstalowaniu pakietu `pwsh` z terminalu.

### <a name="installation-via-homebrew-on-macos-1012"></a>Instalacja za pomocą oprogramowania Homebrew na macOS 10.12

[Homebrew] [ brew] jest Menedżer pakietów preferowanych dla macOS.
Jeśli `brew` nie znaleziono polecenia, należy zainstalować następujące Homebrew [zgodnie z instrukcjami][brew].

Po zainstalowaniu oprogramowania Homebrew Instalowanie programu PowerShell jest bardzo proste.
Najpierw zainstaluj [pojemnika transportowego Homebrew][cask], więc można zainstalować więcej pakietów:

```sh
brew tap caskroom/cask
```

Teraz można zainstalować programu PowerShell:

```sh
brew cask install powershell
```

Na koniec sprawdź, czy instalacji działa prawidłowo:

```sh
pwsh
```

Po udostępnieniu nowej wersji programu PowerShell, po prostu zaktualizuj wzory dla oprogramowania Homebrew i uaktualnienia programu PowerShell:

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> W ramach hosta programu PowerShell (pwsh) można wywołać z powyższych poleceń, ale następnie powłoki PowerShell, należy ponownie uruchomić, aby ukończyć uaktualnianie.
> i Odśwież wartości widoczne w $PSVersionTable.

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download"></a>Instalacja za pośrednictwem bezpośredniego pobierania

Pobierz pakiet PKG `powershell-6.0.2-osx.10.12-x64.pkg` z [zwalnia][] strony na tym komputerze macOS.

Możesz kliknij dwukrotnie plik i postępuj zgodnie z monitami lub zainstalować go z terminala:

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a>Archiwa binarne

Dane binarne środowiska PowerShell `tar.gz` archiwa są udostępniane dla macOS i platformy Linux, aby włączyć zaawansowanych scenariuszach wdrożenia.

### <a name="installing-binary-archives-on-macos"></a>Instalowanie archiwa binarnego na macOS

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

## <a name="uninstalling-powershell-core"></a>Odinstalowywanie programu PowerShell Core

Po zainstalowaniu programu PowerShell z oprogramowania Homebrew dezinstalacji jest łatwe:

```sh
brew cask uninstall powershell
```

Po zainstalowaniu programu PowerShell za pomocą bezpośredniego pobierania programu PowerShell musi zostać usunięte ręcznie:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Aby usunąć dodatkowe ścieżki programu PowerShell, zobacz [ścieżki][] sekcję w tym dokumencie i usunąć żądaną ścieżek przy użyciu `sudo rm`.

> [!NOTE]
> Nie jest to konieczne, jeśli podczas instalacji oprogramowania Homebrew.

[ścieżki]:#paths

## <a name="paths"></a>Ścieżki

* `$PSHOME` jest `/opt/microsoft/powershell/6.0.0/`
* Profile użytkowników będą odczytywane z `~/.config/powershell/profile.ps1`
* Domyślne profile będą odczytywane z `$PSHOME/profile.ps1`
* Moduły użytkownika będą odczytywane z `~/.local/share/powershell/Modules`
* Udostępniony moduły będą odczytywane z `/usr/local/share/powershell/Modules`
* Domyślne moduły będą odczytywane z `$PSHOME/Modules`
* Historia PSReadline zostanie zarejestrowana w celu `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Profile zgodne konfiguracji na hosta w programie PowerShell.
Dlatego domyślnych profilów specyficzne dla hosta istnieje w `Microsoft.PowerShell_profile.ps1` w tej samej lokalizacji.

PowerShell szanuje [specyfikacji katalogu Base XDG] [ xdg-bds] na macOS.

Ponieważ system macOS jest typem pochodnym BSD, prefiks `/usr/local` jest używany zamiast `/opt`.
W związku z tym `$PSHOME` jest `/usr/local/microsoft/powershell/6.0.0/`, i Utwórz Link symboliczny znajduje się w `/usr/local/bin/pwsh`.

[zwalnia]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
