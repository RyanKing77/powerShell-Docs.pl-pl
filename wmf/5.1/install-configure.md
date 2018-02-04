---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
contributor: keithb
title: Instalowanie i konfigurowanie WMF 5.1
ms.openlocfilehash: f58676de6f7a5c51ba586a8c607097af8e60d0c9
ms.sourcegitcommit: 18e3bfae83ffe282d3fd1a45f5386f3b7250f0c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2018
---
# <a name="install-and-configure-wmf-51"></a>Instalowanie i konfigurowanie WMF 5.1 #


## <a name="download-and-install-the-wmf-51-package"></a>Pobierz i zainstaluj pakiet WMF 5.1

Pobierz pakiet WMF 5.1 dla systemu operacyjnego i architektury, które chcesz zainstalować ją na:

| System operacyjny       | Wymagania wstępne           | Łącza pakietu                          |
|------------------------|-------------------------|----------------------------------------|
| Windows Server 2012 R2 |                         | [Win8.1AndW2K12R2-KB3191564-x64.msu][] |
| Windows Server 2012    |                         | [W2K12-KB3191565-x64.msu][]            |
| Windows Server 2008 R2 | [.NET Framework 4.5.2][]| [Win7AndW2K8R2-KB3191566-x64.ZIP][]    |
| Windows 8.1            |                         | **x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</br>**x86:** [Win8.1-KB3191564-x86.msu][] |
| Windows 7 z dodatkiem SP1          | [.NET Framework 4.5.2][]| **x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</br>**x86:** [Win7-KB3191566-x86.ZIP][] |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a>Zainstaluj WMF 5.1 dla systemu Windows Server 2008 R2 i Windows 7

> **Uwaga:** instrukcje instalacji systemu Windows Server 2008 R2 i Windows 7 zostały zmienione i różnią się od instrukcji dla innych pakietów. Instrukcje dotyczące instalacji systemu Windows Server 2012 R2, Windows Server 2012 i Windows 8.1 są poniżej.

**Instalowanie WMF 5.1 w systemie Windows Server 2008 R2 i Windows 7**

1. Przejdź do folderu, do którego został pobrany plik ZIP.

2. Kliknij prawym przyciskiem myszy w pliku ZIP, a następnie wybierz "Wyodrębnij wszystkie...". Zip zawiera pliki 2: MSU i w pliku skryptu instalacji WMF5.1.PS1.
Po wypakowaniu plików ZIP, zawartość można skopiować na dowolnym komputerze z systemem Windows 7 lub Windows Server 2008 R2.

3. Po wyodrębnieniu zawartości pliku ZIP, Otwórz program PowerShell jako administrator, a następnie przejdź do folderu zawierającego zawartość pliku ZIP.

4. Uruchom skrypt instalacji Wmf5.1.ps1 w tym folderze, a następnie postępuj zgodnie z instrukcjami. Ten skrypt Sprawdzanie wymagań wstępnych na komputerze lokalnym i zainstaluj WMF 5.1, jeśli wymagania wstępne zostały spełnione. Poniżej przedstawiono wymagania wstępne.

Zainstaluj WMF5.1.ps1 przyjmuje następujące parametry do jej obsługi ułatwiają automatyzowanie instalacji w systemie Windows Server 2008 R2 i Windows 7:

- AcceptEula: Jeśli ten parametr jest dostarczany, Umowa licencyjna jest akceptowane automatycznie i nie będą wyświetlane.
- AllowRestart: Ten parametr tylko można użyć, gdy AcceptEula został określony. Jeśli ten parametr jest dołączony, a następnie ponowne uruchomienie jest wymagane po zainstalowaniu pakietu WMF 5.1, ponowne uruchomienie nastąpi bez monitowania natychmiast po zakończeniu instalacji.

**WMF 5.1 wymagania wstępne dotyczące systemu Windows Server 2008 R2 z dodatkiem SP1 i Windows 7 z dodatkiem SP1**

Instalacja programu WMF 5.1 w systemie Windows Server 2008 R2 z dodatkiem SP1 lub Windows 7 z dodatkiem SP1 wymaga następujących elementów:
- Musi być zainstalowany najnowszy dodatek service pack.
- WMF 3.0 **nie mogą** można zainstalować. Instalowanie WMF 5.1 za pośrednictwem WMF 3.0 spowoduje utratę PSModulePath, co może powodować inne aplikacje, aby zakończyć się niepowodzeniem. Przed zainstalowaniem WMF 5.1, należy albo odinstalować pakietu AMF 3.0 lub Zapisz PSModulePath i przywracania go ręcznie po zakończeniu instalacji WMF 5.1.
- WMF 5.1 wymaga co najmniej [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642).
Można zainstalować programu Microsoft .NET Framework 4.5.2, zgodnie z instrukcjami w lokalizacji pobierania.

**Zależności usługi WinRM**

Windows PowerShell Desired stan konfiguracji (DSC) zależy od usługi WinRM.
Usługa WinRM nie jest włączona domyślnie w systemie Windows Server 2008 R2 i Windows 7.
Uruchom `Set-WSManQuickConfig`, w programie Windows PowerShell z podwyższonym poziomem uprawnień sesji, aby włączyć usługę WinRM.


## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a>Zainstaluj WMF 5.1 dla systemu Windows Server 2012 R2, Windows Server 2012 i Windows 8.1
**Zainstaluj z Eksploratora Windows (lub Eksploratora plików w systemie Windows Server 2012 R2 lub Windows 8.1)**

1. Przejdź do folderu, do którego został pobrany plik MSU.
2. Kliknij dwukrotnie MSU go uruchomić.

**Instalowanie przy użyciu wiersza polecenia**

1. Po pobraniu poprawny pakiet dla architektury komputera, Otwórz okno wiersza polecenia z podwyższonym poziomem uprawnień użytkownika (Uruchom jako Administrator). W opcji instalacji Server Core systemu Windows Server 2012 R2, Windows Server 2012 lub Windows Server 2008 R2 z dodatkiem SP1 wiersz polecenia z podwyższonym poziomem uprawnień użytkownika domyślnie otwierany.
2. Przejdź do folderu, do którego została pobrana lub kopiowane do pakietu instalacyjnego WMF 5.1.
3. Uruchom jedno z następujących poleceń:
   - Uruchom na komputerach z systemem Windows Server 2012 R2 lub Windows 8.1 x64 `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.
   - Na komputerach z systemem Windows Server 2012 Uruchom `W2K12-KB3191565-x64.msu /quiet`.
   - Uruchom na komputerach z systemem Windows 8.1 x86 `Win8.1-KB3191564-x86.msu /quiet`.

> [!NOTE]
> Instalowanie WMF 5.1 wymaga ponownego uruchomienia. Przy użyciu `/quiet` opcja zostanie wykonany ponowny rozruch systemu bez ostrzeżenia.
> Użyj `/norestart` opcję, aby uniknąć ponownego rozruchu. Jednak WMF 5.1 nie zostanie zainstalowana, dopóki ponownym uruchomieniu.