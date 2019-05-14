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
# <a name="installing-powershell-core-on-macos"></a>Instalowanie programu PowerShell Core w systemie macOS

Program PowerShell Core obsługuje system macOS 10.12 i wyższych.
Wszystkie pakiety są dostępne w usłudze GitHub [Wersje][] strony.
Po zainstalowaniu pakietu Uruchom `pwsh` z poziomu terminalu.

## <a name="about-brew"></a>Temat Brew

[Homebrew] [ brew] to Menedżer pakietów preferowanych dla systemu macOS.
Jeśli `brew` nie znaleziono polecenia, musisz zainstalować następujące Homebrew [zgodnie z instrukcjami][brew].
W przeciwnym razie możesz zainstalować program PowerShell, za pośrednictwem [Pobierz bezpośrednie](#installation-via-direct-download) lub [archiwum binarne](#binary-archives).

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a>Instalacja najnowsza wersja stabilna za pośrednictwem Homebrew w systemie macOS 10.12 lub nowszej

Zobacz [o Brew](#about-brew) uzyskać informacji na temat Brew.

Teraz można zainstalować programu PowerShell:

```sh
brew cask install powershell
```

Na koniec sprawdź, czy Twoja instalacja działa prawidłowo:

```sh
pwsh
```

Po udostępnieniu nowej wersji programu PowerShell, zaktualizuj wzory firmy Homebrew i Uaktualnij program PowerShell:

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> Powyższe polecenia mogą być wywoływane z w ramach hosta programu PowerShell (pwsh), ale następnie powłoki programu PowerShell, należy ponownie uruchomić, aby zakończyć uaktualnianie, a następnie Odśwież wartości widocznych na `$PSVersionTable`.

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a>Instalacja najnowszą wersję zapoznawczą wersji za pomocą Homebrew w systemie macOS 10.12 lub nowszej

Zobacz [o Brew](#about-brew) uzyskać informacji na temat Brew.

Po zainstalowaniu Homebrew, można zainstalować programu PowerShell.
Najpierw zainstaluj [wersji Cask] [ cask-versions] pakiet, który umożliwia zainstalowanie alternatywne wersje pakietów cask:

```sh
brew tap homebrew/cask-versions
```

Teraz można zainstalować programu PowerShell:

```sh
brew cask install powershell-preview
```

Na koniec sprawdź, czy Twoja instalacja działa prawidłowo:

```sh
pwsh-preview
```

Po udostępnieniu nowej wersji programu PowerShell, zaktualizuj wzory firmy Homebrew i Uaktualnij program PowerShell:

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> Powyższe polecenia mogą być wywoływane z w ramach hosta programu PowerShell (pwsh), ale następnie powłoki programu PowerShell, należy ponownie uruchomić, aby ukończyć uaktualnienie.
> i Odśwież wartości widocznych na `$PSVersionTable`.

## <a name="installation-via-direct-download"></a>Instalację za pomocą bezpośredniego pobierania

Pobierz pakiet zapisanego pakietu `powershell-6.2.0-osx-x64.pkg`
z [Wersje][] strony na komputerze z systemem macOS.

Możesz kliknij dwukrotnie plik i postępuj zgodnie z instrukcjami lub zainstalować ją z poziomu terminalu:

```sh
sudo installer -pkg powershell-6.2.0-osx-x64.pkg -target /
```

Zainstaluj [OpenSSL](#install-openssl). Biblioteki OpenSSL jest wymagany dla operacji modelu wspólnych informacji i komunikacji zdalnej programu PowerShell.

## <a name="binary-archives"></a>Binarny archiwa

Plik binarny programu PowerShell `tar.gz` archiwa są dostarczane dla platformy z systemem macOS w celu umożliwienia zaawansowanych scenariuszach wdrożenia.

### <a name="installing-binary-archives-on-macos"></a>Instalowanie pliku binarnego archiwów w systemie macOS

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

Zainstaluj [OpenSSL](#install-openssl). Biblioteki OpenSSL jest wymagany dla operacji modelu wspólnych informacji i komunikacji zdalnej programu PowerShell.

## <a name="installing-dependencies"></a>Instalacja zależności

### <a name="install-xcode-command-line-tools"></a>Zainstaluj narzędzia wiersza polecenia programu XCode

```sh
xcode-select --install
```

### <a name="install-openssl"></a>Zainstalować protokół OpenSSL

Biblioteki OpenSSL jest wymagany dla operacji modelu wspólnych informacji i komunikacji zdalnej programu PowerShell. Można zainstalować za pomocą MacPorts lub Brew.

#### <a name="install-openssl-via-brew"></a>Zainstalować protokół OpenSSL, za pośrednictwem Brew

Zobacz [o Brew](#about-brew) uzyskać informacji na temat Brew.

Aby zainstalować protokół OpenSSL, uruchom `brew install openssl`.

#### <a name="install-openssl-via-macports"></a>Zainstalować protokół OpenSSL, za pośrednictwem MacPorts

1. Zainstaluj [narzędzi wiersza polecenia narzędzia XCode](#install-xcode-command-line-tools).
1. Zainstaluj MacPorts.
   Aby uzyskać instrukcje, zobacz [Przewodnik instalacji](https://guide.macports.org/chunked/installing.macports.html).
1. Zaktualizuj MacPorts uruchamiając `sudo port selfupdate`.
1. Uaktualnij pakiety MacPorts, uruchamiając `sudo port upgrade outdated`.
1. Zainstalować protokół OpenSSL, uruchamiając `sudo port install openssl`.
1. Połącz biblioteki, aby udostępnić je do programu PowerShell:

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a>Odinstalowywanie programu PowerShell Core

Po zainstalowaniu programu PowerShell przy użyciu Homebrew, użyj następującego polecenia do odinstalowania:

```sh
brew cask uninstall powershell
```

Po zainstalowaniu programu PowerShell direct pobrania przy użyciu programu PowerShell należy usunąć ręcznie:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Aby usunąć dodatkowe ścieżki programu PowerShell, zapoznaj się [ścieżki](#paths) sekcji w niniejszym dokumencie i usuwanie ścieżki przy użyciu `sudo rm`.

> [!NOTE]
> Nie jest to konieczne, jeśli został zainstalowany przy użyciu Homebrew.

## <a name="paths"></a>Ścieżki

* `$PSHOME` jest `/usr/local/microsoft/powershell/6.2.0/`
* Profile użytkowników będą odczytywane z `~/.config/powershell/profile.ps1`
* Domyślne profile będą odczytywane z `$PSHOME/profile.ps1`
* Moduły użytkownika zostanie odczytany z `~/.local/share/powershell/Modules`
* Udostępnione moduły będą odczytywane z `/usr/local/share/powershell/Modules`
* Domyślne moduły będą odczytywane z `$PSHOME/Modules`
* Historia PSReadline zostanie zarejestrowana w celu `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Profile przestrzegają konfiguracji dla hosta programu PowerShell.
Aby profil domyślny specyficzne dla hosta istnieje w `Microsoft.PowerShell_profile.ps1` w tej samej lokalizacji.

Stosuje się do programu PowerShell [specyfikację katalogu Base XDG] [ xdg-bds] w systemie macOS.

Ponieważ system macOS jest typem pochodnym BSD, prefiks `/usr/local` jest używana zamiast `/opt`.
Dlatego `$PSHOME` jest `/usr/local/microsoft/powershell/6.2.0/`, i łącza symbolicznego, jest umieszczany na `/usr/local/bin/pwsh`.

## <a name="additional-resources"></a>Dodatkowe zasoby

* [Homebrew w sieci Web][brew]
* [Repozytorium Github Homebrew][GitHub]
* [Homebrew-Cask][cask]

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[Wersje]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
