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
# <a name="installing-powershell-core-on-macos"></a>Instalowanie programu PowerShell Core w systemie macOS

Program PowerShell Core obsługuje system macOS 10.12 i wyższych.
Wszystkie pakiety są dostępne w usłudze GitHub [zwalnia][] strony.
Po zainstalowaniu pakietu Uruchom `pwsh` z poziomu terminalu.

### <a name="installation-via-homebrew-on-macos-1012"></a>Instalację za pomocą Homebrew w systemie macOS 10.12 +

[Homebrew] [ brew] to Menedżer pakietów preferowanych dla systemu macOS.
W oknie terminalu wpisz `brew` do uruchomienia Homebrew.  Jeśli `brew` nie znaleziono polecenia, musisz zainstalować następujące Homebrew [zgodnie z instrukcjami][brew].

> [!NOTE]
> Jeśli zainstalowano Homebrew w przeszłości, zawsze jest dobry pomysł, aby uruchomić "brew resetowania aktualizacji" & & "brew update".
```sh
brew update-reset
brew update
```

> Starsze wersje programu Homebrew używane naciśnij "caskroom/cask", która przestarzałe i migracji do "homebrew/cask".  Więcej informacji znajduje się w temacie [Homebrew cask][cask]. Aby wyświetlić listę Twojej bieżącej podsłuchu, należy użyć polecenia "brew naciśnij".  Jeśli widzisz "caskroom/cask" można użyć "brew aktualizacji" Aby migrować podsłuchu Homebrew.

```sh
brew tap
brew update
```

Po zainstalowane/aktualizacji Homebrew, instalowanie programu PowerShell jest proste.

Aby zainstalować program PowerShell:

```sh
brew cask install powershell
```

Na koniec sprawdź, czy Twoja instalacja działa prawidłowo:

```sh
pwsh
```

Aby zakończyć działanie programu PowerShell, a następnie wróć do powłoki bash, użyj polecenia "exit".
```sh
exit
```

Po udostępnieniu nowej wersji programu PowerShell, po prostu zaktualizuj wzory firmy Homebrew i Uaktualnij program PowerShell:

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> Powyższe polecenia mogą być wywoływane z w ramach hosta programu PowerShell (pwsh), ale następnie powłoki programu PowerShell, należy ponownie uruchomić, aby zakończyć uaktualnianie, a następnie Odśwież wartości widocznych na $PSVersionTable.

### <a name="installing-preview-via-homebrew-on-macos-1012"></a>Instalowanie wersji zapoznawczej za pośrednictwem Homebrew w systemie macOS 10.12 +

[Homebrew] [ brew] to Menedżer pakietów preferowanych dla systemu macOS.
W oknie terminalu wpisz `brew` do uruchomienia Homebrew.  Jeśli `brew` nie znaleziono polecenia, musisz zainstalować następujące Homebrew [zgodnie z instrukcjami][brew].

> [!NOTE]
> Jeśli zainstalowano Homebrew w przeszłości, zawsze jest dobry pomysł, aby uruchomić "brew resetowania aktualizacji" & & "brew update".
```sh
brew update-reset
brew update
```

Następnie użytkownik musi nacisnąć `versions` beczki repozytorium, aby uzyskać pakiet (wersja zapoznawcza):

```sh
brew tap homebrew/cask-versions
```

Aby zainstalować program PowerShell w wersji zapoznawczej:

```sh
brew cask install powershell-preview
```

Na koniec sprawdź, czy Twoja instalacja działa prawidłowo:

```sh
pwsh-preview
```

Podczas wydawane są nowe wersje programu PowerShell, po prostu zaktualizuj wzory firmy Homebrew i uaktualnienie wersji programu PowerShell:

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> Powyższe polecenia mogą być wywoływane z w ramach hosta programu PowerShell (pwsh), ale następnie powłoki programu PowerShell, należy ponownie uruchomić, aby zakończyć uaktualnianie, a następnie Odśwież wartości widocznych na $PSVersionTable.

### <a name="installation-via-direct-download"></a>Instalację za pomocą bezpośredniego pobierania

Pobierz pakiet PKG `powershell-6.0.2-osx.10.12-x64.pkg` z [zwalnia][] strony na komputerze z systemem macOS.

Możesz kliknij dwukrotnie plik i postępuj zgodnie z instrukcjami lub zainstalować ją z poziomu terminalu:

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a>Binarny archiwa

Plik binarny programu PowerShell `tar.gz` archiwa znajdują się na systemach macOS i Linux platformy, aby włączyć zaawansowanych scenariuszach wdrożenia.

### <a name="installing-binary-archives-on-macos"></a>Instalowanie pliku binarnego archiwów w systemie macOS

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

Po zainstalowaniu programu PowerShell przy użyciu Homebrew, dezinstalacja jest łatwe:

```sh
brew cask uninstall powershell
```

Po zainstalowaniu programu PowerShell direct pobrania przy użyciu programu PowerShell należy usunąć ręcznie:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Aby usunąć dodatkowe ścieżki programu PowerShell, zobacz [ścieżki][] sekcji w niniejszym dokumencie i usuń żądany ścieżek przy użyciu `sudo rm`.

> [!NOTE]
> Nie jest to konieczne, jeśli został zainstalowany przy użyciu Homebrew.

[Ścieżki]:#paths

## <a name="paths"></a>Ścieżki

* `$PSHOME` jest `/usr/local/microsoft/powershell/6.0.2/`
* Profile użytkowników będą odczytywane z `~/.config/powershell/profile.ps1`
* Domyślne profile będą odczytywane z `$PSHOME/profile.ps1`
* Moduły użytkownika zostanie odczytany z `~/.local/share/powershell/Modules`
* Udostępnione moduły będą odczytywane z `/usr/local/share/powershell/Modules`
* Domyślne moduły będą odczytywane z `$PSHOME/Modules`
* Historia PSReadline zostanie zarejestrowana w celu `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Profile przestrzegają konfiguracji dla hosta programu PowerShell.
Dlatego domyślne profile specyficzne dla hosta istnieje w `Microsoft.PowerShell_profile.ps1` w tej samej lokalizacji.

Stosuje się do programu PowerShell [specyfikację katalogu Base XDG] [ xdg-bds] w systemie macOS.

Ponieważ system macOS jest typem pochodnym BSD, prefiks `/usr/local` jest używana zamiast `/opt`.
W związku z tym `$PSHOME` jest `/usr/local/microsoft/powershell/6.0.2/`, a Link symboliczny jest umieszczany na `/usr/local/bin/pwsh`.

## <a name="additional-resources"></a>Dodatkowe zasoby

* [Homebrew w sieci Web][brew]
* [Repozytorium Github Homebrew][GitHub]
* [Homebrew Cask][cask]


[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[zwalnia]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
