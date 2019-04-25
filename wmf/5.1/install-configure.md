---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
contributor: keithb
title: Zainstaluj i skonfiguruj program WMF 5.1
ms.openlocfilehash: c439d0851189a89a81fa38194632dc54475a001d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085001"
---
# <a name="install-and-configure-wmf-51"></a>Instalowanie i konfigurowanie programu WMF 5.1

## <a name="download-and-install-the-wmf-51-package"></a>Pobierz i zainstaluj pakiet WMF 5.1

Pobierz program WMF 5.1 dla systemu operacyjnego i architekturę, którą chcesz zainstalować je na:

| System operacyjny       | Wymagania wstępne           | Pakiet łącza                          |
|------------------------|-------------------------|----------------------------------------|
| Windows Server 2012 R2 |                         | [Win8.1AndW2K12R2-KB3191564-x64.msu][] |
| Windows Server 2012    |                         | [W2K12-KB3191565-x64.msu][]            |
| Windows Server 2008 R2 | [.NET Framework 4.5.2][]| [Win7AndW2K8R2-KB3191566-x64.ZIP][]    |
| Windows 8.1            |                         | **x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</br>**x86:** [Win8.1-KB3191564-x86.msu][] |
| Windows 7 SP1          | [.NET Framework 4.5.2][]| **x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</br>**x86:** [Win7-KB3191566-x86.ZIP][] |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a>Zainstaluj program WMF 5.1 dla systemu Windows Server 2008 R2 i Windows 7

> [!NOTE]
> Instrukcje dotyczące instalacji systemu Windows Server 2008 R2 i Windows 7 uległy zmianie, a różnią się od instrukcji dla innych pakietów. Instrukcje dotyczące instalacji dla systemu Windows Server 2012 R2, Windows Server 2012 i Windows 8.1 są poniżej.

**Instalowanie programu WMF 5.1 w systemie Windows Server 2008 R2 i Windows 7**

1. Przejdź do folderu, do którego został pobrany plik ZIP.

2. Kliknij prawym przyciskiem myszy w pliku ZIP, a następnie wybierz "Wyodrębnij wszystko...". Plik Zip zawiera pliki 2: MSU oraz pliku skryptu instalacji WMF5.1.PS1.
Po wypakowaniu plików ZIP, możesz skopiować zawartość do dowolnej maszyny z systemem Windows 7 lub Windows Server 2008 R2.

3. Po wyodrębnieniu zawartości pliku ZIP, Otwórz program PowerShell jako administrator, a następnie przejdź do folderu zawierającego zawartość pliku ZIP.

4. Uruchom skrypt instalacji Wmf5.1.ps1 w tym folderze, a następnie postępuj zgodnie z instrukcjami. Ten skrypt Sprawdzanie wymagań wstępnych na komputerze lokalnym i zainstaluj program WMF 5.1, jeśli wymagania wstępne zostały spełnione. Poniżej przedstawiono wymagania wstępne.

Zainstaluj WMF5.1.ps1 przyjmuje następujące parametry, aby ułatwić zautomatyzowanie instalacji w systemie Windows Server 2008 R2 i Windows 7:

- AcceptEula: Jeśli ten parametr jest dołączony, Umowa licencyjna akceptowane automatycznie i nie będą wyświetlane.
- AllowRestart: Tego parametru należy używać tylko jeśli określono AcceptEula. Jeśli ten parametr jest dołączony, a następnie ponowne uruchomienie jest wymagane po zainstalowaniu programu WMF 5.1, ponowne uruchomienie nastąpi bez monitowania użytkownika natychmiast, po zakończeniu instalacji.

**WMF 5.1 wymagania wstępne dotyczące systemu Windows Server 2008 R2 z dodatkiem SP1 i Windows 7 z dodatkiem SP1**

Instalacja programu WMF 5.1 w systemie Windows Server 2008 R2 z dodatkiem SP1 lub Windows 7 z dodatkiem SP1, należy spełnić następujące wymagania:
- Musi być zainstalowany najnowszy dodatek service pack.
- WMF 3.0 **nie** można zainstalować. Instalowanie programu WMF 5.1 za pośrednictwem programu WMF 3.0 spowoduje utratę PSModulePath, co może powodować inne aplikacje nie powiedzie się. Przed zainstalowaniem programu WMF 5.1, należy albo odinstalować programu WMF 3.0 lub zapisać PSModulePath i przywracania go ręcznie po zakończeniu instalacji programu WMF 5.1.
- Program WMF 5.1 wymaga co najmniej [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642).
Postępując zgodnie z instrukcjami w lokalizacji pobierania, można zainstalować programu Microsoft .NET Framework 4.5.2.

**Zależności usługi WinRM**

Windows PowerShell Desired State Configuration (DSC) jest zależna od usługi WinRM.
Domyślnie w systemie Windows Server 2008 R2 i Windows 7 nie jest włączona usługa WinRM.
Uruchom `Set-WSManQuickConfig`, programu Windows PowerShell z podwyższonym poziomem uprawnień sesji, aby włączyć usługę WinRM.

## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a>Zainstaluj program WMF 5.1 dla systemu Windows Server 2012 R2, Windows Server 2012 i Windows 8.1

**Zainstaluj z Eksploratora Windows (lub Eksploratora plików w systemie Windows Server 2012 R2 lub Windows 8.1)**

1. Przejdź do folderu, do którego został pobrany plik MSU.
2. Kliknij dwukrotnie MSU do jej uruchomienia.

**Instalowanie z wiersza polecenia**

1. Po pobraniu właściwy pakiet dla architektury komputera, Otwórz okno wiersza polecenia z podwyższonym poziomem uprawnień użytkownika (Uruchom jako Administrator). W opcji instalacji Server Core systemu Windows Server 2012 R2, Windows Server 2012 lub Windows Server 2008 R2 z dodatkiem SP1 wiersz polecenia z podwyższonym poziomem uprawnień użytkownika domyślnie otwierany.
2. Zmień katalogi na folder, do którego została pobrana lub kopiowane do pakietu instalacyjnego programu WMF 5.1.
3. Uruchom jedno z następujących poleceń:
   - Uruchom na komputerach z systemem Windows Server 2012 R2 lub Windows 8.1 x64 `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.
   - Na komputerach z systemem Windows Server 2012 Uruchom `W2K12-KB3191565-x64.msu /quiet`.
   - Uruchom na komputerach z systemem Windows 8.1 x86 `Win8.1-KB3191564-x86.msu /quiet`.

> [!NOTE]
> Instalowanie programu WMF 5.1 wymaga ponownego uruchomienia systemu. Za pomocą `/quiet` opcji spowoduje ponowne uruchomienie systemu bez ostrzeżenia.
> Użyj `/norestart` opcję, aby uniknąć ponownego uruchomienia. Jednak program WMF 5.1 nie zostanie zainstalowany, dopóki nie zostały uruchomione ponownie.
