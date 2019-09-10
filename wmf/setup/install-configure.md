---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
contributor: keithb
title: Instalowanie i konfigurowanie programu WMF 5.1
ms.openlocfilehash: 241f52be011e1afc87d25c9a934db0c1e0361b76
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848134"
---
# <a name="install-and-configure-wmf-51"></a>Instalowanie i Konfigurowanie systemu WMF 5,1

> [!IMPORTANT]
> WMF 5,0 jest zastępowany przez WMF 5,1. Użytkownicy z pakietem WMF 5,0 muszą uaktualnić do wersji WMF 5,1, aby uzyskać pomoc techniczną.
> **WMF 5,1 wymaga .NET Framework 4.5.2** (lub powyżej). Instalacja powiedzie się, ale funkcje kluczowych zakończą się niepowodzeniem, jeśli nie zainstalowano platformy .NET 4.5.2 (lub nowszej).

## <a name="download-and-install-the-wmf-51-package"></a>Pobieranie i instalowanie pakietu WMF 5,1

Pobierz pakiet WMF 5,1 dla systemu operacyjnego i architektury, w których chcesz go zainstalować:

| System operacyjny       | Wymagania wstępne           | Linki pakietów                          |
|------------------------|-------------------------|----------------------------------------|
| Windows Server 2012 R2 |                         | [Win8.1AndW2K12R2-KB3191564-x64.msu][] |
| Windows Server 2012    |                         | [W2K12-KB3191565-x64.msu][]            |
| Windows Server 2008 R2 | [.NET Framework 4.5.2][]| [Win7AndW2K8R2-KB3191566-x64.ZIP][]    |
| Windows 8.1            |                         | **procesorów** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</br>**wyposażone** [Win8.1-KB3191564-x86.msu][] |
| Windows 7 z dodatkiem SP1          | [.NET Framework 4.5.2][]| **procesorów** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</br>**wyposażone** [Win7-KB3191566-x86.ZIP][] |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

- Przed zainstalowaniem pakietu WMF 5,1 RTM należy odinstalować wersję zapoznawczą WMF 5,1.
- Pakiet WMF 5,1 może być instalowany bezpośrednio przez WMF 5,0 lub WMF 4,0.
- Przed zainstalowaniem programu WMF 5,1 w systemach Windows 7 i Windows Server 2008 R2 **nie jest wymagane** zainstalowanie programu WMF 4,0.

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a>Instalowanie programu WMF 5,1 dla systemu Windows Server 2008 R2 i Windows 7

> [!NOTE]
> Instrukcje dotyczące instalacji systemu Windows Server 2008 R2 i Windows 7 zostały zmienione i różnią się od instrukcji innych pakietów. Instrukcje dotyczące instalacji systemu Windows Server 2012 R2, Windows Server 2012 i Windows 8.1 są poniżej.

### <a name="wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1"></a>Wymagania wstępne programu WMF 5,1 dla systemów Windows Server 2008 R2 z dodatkiem SP1 i Windows 7 z dodatkiem SP1

Instalacja programu WMF 5,1 w systemie Windows Server 2008 R2 z dodatkiem SP1 lub Windows 7 z dodatkiem SP1 wymaga następujących elementów:

- Należy zainstalować najnowszy dodatek Service Pack.
- **Nie** można zainstalować pakietu WMF 3,0. Zainstalowanie programu WMF 5,1 over WMF 3,0 spowoduje utratę **PSModulePath** (`$env:PSModulePath`), co może spowodować niepowodzenie innych aplikacji. Przed zainstalowaniem programu WMF 5,1 należy odinstalować program WMF 3,0 lub zapisać **PSModulePath** , a następnie przywrócić go ręcznie po zakończeniu instalacji programu WMF 5,1.
- Program WMF 5,1 wymaga co najmniej [.NET Framework 4.5.2](https://www.microsoft.com/download/details.aspx?id=42642).
  Microsoft .NET Framework 4.5.2 można zainstalować, postępując zgodnie z instrukcjami w lokalizacji pobierania.

### <a name="installing-wmf-51-on-windows-server-2008-r2-and-windows-7"></a>Instalowanie programu WMF 5,1 w systemie Windows Server 2008 R2 i Windows 7

1. Przejdź do folderu, do którego pobrano plik ZIP.

2. Kliknij prawym przyciskiem myszy plik ZIP, a następnie wybierz pozycję **Wyodrębnij wszystko...** . Plik zip zawiera dwa pliki: msu i `Install-WMF5.1.ps1` plik skryptu. Po rozpakowaniu pliku ZIP można skopiować jego zawartość na dowolną maszynę z systemem Windows 7 lub Windows Server 2008 R2.

3. Po wyodrębnieniu zawartości pliku ZIP Otwórz program PowerShell jako administrator, a następnie przejdź do folderu zawierającego zawartość pliku ZIP.

4. `Install-WMF5.1.ps1` Uruchom skrypt w tym folderze i postępuj zgodnie z instrukcjami. Ten skrypt sprawdzi wymagania wstępne na maszynie lokalnej i zainstaluje program WMF 5,1, jeśli spełniono wymagania wstępne. Wymagania wstępne są wymienione poniżej.

   `Install-WMF5.1.ps1`przyjmuje następujące parametry, aby ułatwić automatyzację instalacji w systemie Windows Server 2008 R2 i Windows 7:

   - **AcceptEula**: Po uwzględnieniu tego parametru Umowa EULA zostanie automatycznie zaakceptowana i nie będzie wyświetlana.
   - **AllowRestart**: Tego parametru można użyć tylko wtedy, gdy określono AcceptEula. Jeśli ten parametr jest dołączony, a ponowne uruchomienie jest wymagane po zainstalowaniu programu WMF 5,1, ponowne uruchomienie nastąpi bez monitowania natychmiast po zakończeniu instalacji.

## <a name="winrm-dependency"></a>Zależność usługi WinRM

Konfiguracja żądanego stanu programu Windows PowerShell (DSC) zależy od usługi WinRM. Usługa WinRM nie jest domyślnie włączona w systemie Windows Server 2008 R2 i Windows 7. Aby `Set-WSManQuickConfig`włączyć usługę WinRM, uruchom polecenie w sesji programu Windows PowerShell z podwyższonym poziomem uprawnień.

## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a>Zainstaluj program WMF 5,1 dla systemu Windows Server 2012 R2, Windows Server 2012 i Windows 8.1

### <a name="install-from-windows-file-explorer"></a>Zainstaluj z Eksploratora plików systemu Windows

1. Przejdź do folderu, do którego pobrano plik MSU.
2. Kliknij dwukrotnie element MSU, aby go uruchomić.

### <a name="installing-from-the-command-prompt"></a>Instalowanie z wiersza polecenia

1. Po pobraniu poprawnego pakietu dla architektury komputera Otwórz okno wiersza polecenia z podwyższonym poziomem uprawnień użytkownika (Uruchom jako administrator). W opcjach instalacji Server Core systemu Windows Server 2012 R2, Windows Server 2012 lub Windows Server 2008 R2 SP1, wiersz polecenia jest uruchamiany domyślnie z podwyższonym poziomem uprawnień użytkownika.
2. Zmień katalogi na folder, do którego pobrano lub skopiowano pakiet instalacyjny WMF 5,1.
3. Uruchom jedno z następujących poleceń:
   - Na komputerach z systemem Windows Server 2012 R2 lub Windows 8.1 x64 Uruchom `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`polecenie.
   - Na komputerach z systemem Windows Server 2012 Uruchom `W2K12-KB3191565-x64.msu /quiet`polecenie.
   - Na komputerach z systemem Windows 8.1 x86 Uruchom `Win8.1-KB3191564-x86.msu /quiet`polecenie.

> [!NOTE]
> Zainstalowanie programu WMF 5,1 wymaga ponownego uruchomienia komputera. `/quiet` Użycie opcji spowoduje ponowne uruchomienie systemu bez ostrzeżenia. Użyj opcji `/norestart` , aby uniknąć ponownego uruchomienia. Jednak program WMF 5,1 nie zostanie zainstalowany, dopóki nie zostanie ponownie uruchomiony.
