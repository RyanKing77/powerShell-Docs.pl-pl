---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Co nowego w programie Windows PowerShell 5.0
ms.openlocfilehash: a21e6af9f23ac8bb3ddf84dbfa67a67f3ff93b24
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055108"
---
# <a name="whats-new-in-windows-powershell-50"></a>Co nowego w programie Windows PowerShell 5.0

Windows PowerShell 5.0 zawiera istotne nowe funkcje, które rozszerzają zakres jego zastosowań, zwiększyć jego użyteczność i umożliwiają kontrolowanie i zarządzanie komputerami z systemem Windows, łatwiejsze i bardziej kompleksowe.

Windows PowerShell 5.0 jest zgodne z poprzednimi wersjami. Polecenia cmdlet, dostawców, moduły, przystawki, skrypty, funkcje i profile, które zostały zaprojektowane dla programu Windows PowerShell 4.0, Windows PowerShell 3.0 i Windows PowerShell 2.0 jest ogólnie pracy w programie Windows PowerShell 5.0, bez konieczności wprowadzania zmian.

## <a name="installing-windows-powershell"></a>Instalowanie programu Windows PowerShell

Windows PowerShell 5.0 jest instalowany domyślnie w systemie Windows Server 2016 Technical Preview i Windows 10.

Aby zainstalować program Windows PowerShell 5.0 w systemie Windows Server 2012 R2, Windows 8.1 Enterprise lub Windows 8.1 Pro, Pobierz i zainstaluj [Windows Management Framework 5.0](https://aka.ms/wmf5download). Pamiętaj odczytać szczegółów pobierania i spełniać wszystkie wymagania systemowe, przed zainstalowaniem programu Windows Management Framework 5.0.

## <a name="in-this-topic"></a>W tym temacie

- [Aktualizacje programu Windows PowerShell 4.0 DSC w KB 3000850](#windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850)
- [Nowe funkcje programu Windows PowerShell 5.0](#new-features-in-windows-powershell-50)
- [Nowe funkcje programu Windows PowerShell 4.0](#new-features-in-windows-powershell-40)
- [Nowe funkcje w środowisku Windows PowerShell 3.0](#new-features-in-windows-powershell-30)

## <a name="windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850"></a>Aktualizacje programu Windows PowerShell 4.0 w listopadzie 2014 r. pakiet zbiorczy (KB 3000850)

Wiele aktualizacji i ulepszeń do Windows PowerShell Desired State Configuration (DSC) w wersji 4.0 programu Windows PowerShell są dostępne w [listopada 2014 r. pakiet zbiorczy aktualizacji dla systemu Windows RT 8.1, Windows 8.1 i Windows Server 2012 R2](https://support.microsoft.com/kb/3000850/) (KB 3000850 ). Można określić, jeśli KB 3000850 jest zainstalowany w systemie, uruchamiając `Get-Hotfix -Id KB3000850` w programie Windows PowerShell.

- Aktualizacje istniejących poleceń cmdlet w [PSDesiredStateConfiguration](https://technet.microsoft.com/library/dn391651(v=wps.640).aspx) modułu
  - [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) jest szybszy (szczególnie w środowisku ISE).
  - [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) ma nowy parametr - UseExisting, który przywrócenie ostatniej konfiguracji zastosowane.
  - [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) -Force został rozwiązany.
  - [Get-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn407378.aspx) przedstawia bardziej użyteczne informacje na temat stanu aparatu.
  - [Test-DscConfiguration](https://technet.microsoft.com/library/dn407382.aspx) teraz zwraca nazwę komputera oraz wartość PRAWDA lub FAŁSZ.
  - [Nowe DscChecksum](https://technet.microsoft.com/library/dn521622.aspx) obsługuje teraz ścieżki UNC.

- Nowe polecenia cmdlet w [PSDesiredStateConfiguration](https://technet.microsoft.com/library/dn391651(v=wps.640).aspx) modułu
  - [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541(v=wps.630).aspx):  Wykonuje sprawdzenie, czy serwer na żądanie ściągnięcia.
  - [Stop-DscConfiguration](https://technet.microsoft.com/library/mt143542(v=wps.630).aspx):  Zatrzymuje konfiguracji, który jest już uruchomiony.
  - [Remove-DscConfigurationDocument](https://technet.microsoft.com/library/mt143544(v=wps.630).aspx):  Umożliwia usuwanie dokumentów konfiguracji poszczególnych etapów (oczekujące poprzedniej i bieżącej).

- Ulepszenia języka
  - DependsOn obsługuje teraz zasoby złożone.
  - DependsOn obsługuje teraz liczb w polu nazwy wystąpienia zasobu.
  - Wyrażenia węzła, które dają puste nie są już zgłaszać błędy.
  - Błąd, który występuje, gdy węzeł wynikiem wyrażenia jest pusty, został rozwiązany.
  - Konfiguracje wywoływania współpracują teraz konfiguracje w konsoli programu Windows PowerShell.

- Ulepszenia tryb ściągania
  - Tryb ściągania obsługuje teraz wszystkie pliki ZIP.
  - **AllowModuleOverwrite** teraz działa prawidłowo.

- Ulepszenia odporności
  - Nowe **element DebugMode** umożliwia ponowne ładowanie modułów zasobów.
  - Jeśli wystąpi błąd konfiguracji, plik pending.mof nie został usunięty.
  - Lokalne Configuration Manager (LCM) jest teraz bardziej odporne na błędy, w przypadku ustawienia metaconfiguration zostały uszkodzone.

- Ulepszenia diagnostyki
  - Ostrzeżenie jest wyświetlane, gdy LCM ustawia zegar inne ustawienia niż określono.
  - Pliki dziennika błędów zawierają teraz stos wywołań dla zasobów programu Windows PowerShell.

- Ulepszenia elastyczność
  - Zasób LocalConfigurationManager ma nową właściwość **ActionAfterReboot**.
    - ContinueConfiguration (wartość domyślna): Automatycznie wznowi konfigurację po ponownym uruchomieniu węzła docelowego.
    - StopConfiguration: Automatycznie wznawia konfigurację po ponownym uruchomieniu węzła.
  - Uruchom spójności może teraz częściej niż operacja ŚCIĄGNIĘCIA lub na odwrót.
  - Obsługa wersji:  DSC można teraz rozpoznania dokumentu, który został wygenerowany nowszego klienta (dołączone do [WMF 5.0](https://aka.ms/wmf5download)).

- Ulepszenia zapobiegania błąd
  - Wersja modułu jest teraz wymuszane przed zastosowaniem konfiguracji.
  - **DebugPreference** teraz jest ustawione prawidłowo dla Get-, Set- lub TargetResource testu połączenia.

- Ulepszenia obsługi poświadczeń
  - Certyfikat jest używany teraz, jeśli obie **certyfikatu** i **PSDscAllowPlainTextPassword** zostały określone.
  - Poświadczenia są odszyfrowywane, nawet w przypadku Get TargetResource.
  - Metaconfiguration poświadczenia są szyfrowane i odszyfrowywane.
  - PSCredentials teraz są odszyfrowywane, gdy są one osadzonego obiektu.

- Ulepszenia wbudowanych zasobów
  - Zasób pakietu
    - Nie instaluje już nieprawidłowy pakiet (z lokalnej lub sieci web źródła).
    - Teraz obsługuje protokół HTTPS.
  - Obsługiwane jest teraz do obsługi protokołu HTTPS w [pakietu zasobów](https://technet.microsoft.com/library/dn282132.aspx).
  - [Zasób archiwum](https://technet.microsoft.com/library/dn249917.aspx) obsługuje teraz poświadczeń.

## <a name="new-features-in-windows-powershell-50"></a>Nowe funkcje programu Windows PowerShell 5.0

- [Nowe funkcje w programie Windows PowerShell](#new-features-in-windows-powershell)
- [Nowe funkcje programu Windows PowerShell Desired State Configuration](#new-features-in-windows-powershell-desired-state-configuration)
- [Nowe funkcje w środowisku Windows PowerShell ISE](#new-features-in-windows-powershell-ise)
- [Nowe funkcje w usługach sieci Web programu Windows PowerShell](#new-features-in-windows-powershell-web-services-management-odata-iis-extension)
- [Istotne poprawki błędów w programie Windows PowerShell 5.0](#notable-bug-fixes-in-windows-powershell-50)

### <a name="new-features-in-windows-powershell"></a>Nowe funkcje w programie Windows PowerShell

- Począwszy od programu Windows PowerShell 5.0, można tworzyć przy użyciu klas, za pomocą formalne składnia i semantyka, które są podobne do innych języków programowania obiektowego. **Klasa**, **wyliczenia**, i dodano innych słów kluczowych języka programu Windows PowerShell do obsługi nowych funkcji. Aby uzyskać więcej informacji na temat pracy z klasami Zobacz about_Classes.

- Windows PowerShell 5.0 wprowadzono strumień informacji o nowej, ze strukturą, który służy do przesyłania danych ze strukturą między skryptu i jego obiektów wywołujących (lub środowisko hostingu). Host zapisu umożliwia teraz wyemituj dane wyjściowe do strumienia informacji. Strumienie informacji działa również w przypadku PowerShell.Streams, zadania, zaplanowanych zadań i przepływów pracy. Następujące funkcje obsługuje strumień informacji.
  - Nowe informacje o zapisu polecenie cmdlet umożliwiający określenie, jak środowiska Windows PowerShell obsługuje dane strumienia informacji dla polecenia. Write-Host jest otoką zapisuj informacji. Do działania przepływu pracy obsługiwane są także informacje zapisu.
  - Dwa nowe wspólne parametry InformationVariable i InformationAction, umożliwiają określają sposób wyświetlania informacji strumieni z poleceniem. Prawidłowe wartości dla InformationAction są SilentlyContinue, Stop, Kontynuuj, Inquire, Ignoruj lub wstrzymania z SilentlyContinue domyślna. InformationVariable Określa ciąg jako nazwę zmiennej, do którego chcesz, aby dane Write-Host z poleceniem, który został zapisany.
  - Nową zmienną preferencji InformationPreference, określa preferencje domyślne dla informacji o przesyłanie strumieniowe danych w sesji programu Windows PowerShell. Wartość domyślna to SilentlyContinue.
  - Dodano dwa nowe wspólnych parametrów przepływów pracy, PSInformation i InformationAction.
  - Polecenie Format-Table kolumn tabeli teraz są automatycznie formatowane poprzez ocenę pierwszy 300ms danych, które przechodzą przez strumień.

- We współpracy z [Microsoft Research](https://research.microsoft.com/), dodano nowe polecenie cmdlet ConvertFrom-ciąg. Ciąg ConvertFrom umożliwia wyodrębnianie i analizowanie obiektów ze strukturą z zawartości ciągów tekstowych. Aby uzyskać więcej informacji zobacz ConvertFrom-ciąg.
- Nowe polecenie cmdlet Convert-String automatycznie formatuje tekst oparty na przykład, w którym należy podać parametr - przykład.
- Nowy moduł Microsoft.PowerShell.Archive, zawiera polecenia cmdlet, które umożliwiają Kompresuj pliki i foldery w pliki z archiwum (określana także jako pliku ZIP), Wyodrębnij pliki z istniejących plików ZIP i aktualizować pliki ZIP z nowszymi wersjami pliki skompresowane w nich.
- Nowego modułu PackageManagement, umożliwia odnajdywanie i instalowanie pakietów oprogramowania w Internecie. Modułu PackageManagement (wcześniej znane jako OneGet) jest Menedżer lub multiplekser istniejących menedżerów pakietów (nazywane również pakietu dostawców) ujednolicenie zarządzania pakietu Windows przy użyciu pojedynczego interfejsu programu Windows PowerShell.
- Nowy moduł PowerShellGet, umożliwia znajdowanie, instalowanie, publikowanie i aktualizowanie modułów i zasobów DSC na [galerii programu PowerShell](https://www.powershellgallery.com/), lub na repozytorium moduł wewnętrzny, który można skonfigurować, uruchamiając polecenie cmdlet Register-PSRepository.
- Nowe słowo kluczowe języka **ukryty**, dodano do określenia, czy członek (właściwość lub metoda) nie jest wyświetlana domyślnie w wynikach Get-Member (chyba że dodasz parametru - Force). Właściwości lub metody, które zostały oznaczone jako ukryte również nie są wyświetlane w wynikach funkcji IntelliSense, chyba że jesteś w kontekście, w którym element członkowski powinny być widoczne; na przykład automatyczne $ zmiennej to powinny pokazywać ukryte elementy członkowskie w przypadku metody klasy.
- Nowy element, Usuń element i Get-ChildItem zostały rozszerzone i obsługuje tworzenie i zarządzanie nimi [łącza symbolicznego](https://en.wikipedia.org/wiki/Symbolic_link). **- ItemType** parametru dla elementu New akceptuje nową wartość **SymbolicLink**. Teraz można tworzyć łącza symbolicznego w jednym wierszu, uruchamiając polecenie cmdlet New-Item.
- Polecenie GET-ChildItem ma również nowe — głębokość parametr, który umożliwia z parametrem - Recurse limit rekursji. Na przykład Get-ChildItem-Recurse - 2 głębokość zwraca wyniki z bieżącego folderu wszystkich folderów podrzędnych w bieżącym folderze oraz wszystkich folderów w ramach elementu podrzędnego folderów.
- Copy-Item teraz umożliwia możesz skopiować pliki lub foldery z jednej sesji programu Windows PowerShell do innego, co oznacza, skopiuj pliki do sesji, które są połączone z komputerami zdalnymi (łącznie z komputerów z systemem [serwera Nano Server](https://blogs.technet.com/b/windowsserver/archive/2015/04/08/microsoft-announces-nano-server-for-modern-apps-and-cloud.aspx), i zatem mieć interfejs nie). Do kopiowania plików, określ identyfikatory sesji PSSession jako wartość nowe parametry - FromSession i - ToSession, a następnie dodaj - ścieżka - i docelowym, aby określić ścieżkę źródła i miejsca docelowego, odpowiednio. Na przykład Copy-Item-c: ścieżka\\mójplik.txt - ToSession $s — d: docelowy\\destinationFolder.
- Transkrypcja programu Windows PowerShell został ulepszony, aby dotyczyć wszystkich aplikacji hostingu (np. Windows PowerShell ISE) oprócz host konsoli (**powershell.exe**). Po włączeniu można skonfigurować opcje transkrypcji (w tym włączenie transkrypcji systemowe) **włączyć transkrypcji PowerShell** znaleziono szablony/Windows w administracyjnej części/Windows ustawienia zasad grupy Program PowerShell.
- Nowa funkcja śledzenia szczegółowy skrypt umożliwia szczegółowe śledzenie i analizy użycia skryptów programu Windows PowerShell w systemie. Włączenie śledzenia szczegółowy skrypt programu Windows PowerShell dzienników wszystkich blokach skryptu w dzienniku zdarzeń śledzenie zdarzeń dla Windows (ETW) **Microsoft-Windows-PowerShell/Operational**.
- Począwszy od programu Windows PowerShell 5.0, nowe polecenia cmdlet składnię komunikatów kryptograficznych obsługują szyfrowanie i odszyfrowywanie zawartości przy użyciu formatu standardowego IETF kryptograficznie ochrony wiadomości, zgodnie z opisem w [RFC5652](https://tools.ietf.org/html/rfc5652). Dodano polecenia cmdlet Get-CmsMessage, Chroń CmsMessage i Unprotect CmsMessage [Microsoft.PowerShell.Security](https://technet.microsoft.com/library/hh849807.aspx) modułu.
- Nowe polecenia cmdlet w [Microsoft.PowerShell.Utility](https://technet.microsoft.com/library/hh849958.aspx) modułu, obszarem działania Get, obszarem działania debugowania, Get-RunspaceDebug, Enable RunspaceDebug i Disable-RunspaceDebug pozwalają na ustawienie opcji debugowania na obszarze działania i uruchamianie i zatrzymywanie debugowanie w obszarze działania. Do debugowania na dowolnych obszarach działania (czyli obszary działania nie są obszarem działania domyślne dla konsoli programu Windows PowerShell lub w sesji środowiska Windows PowerShell ISE) programu Windows PowerShell umożliwia ustawianie punktów przerwania w skrypcie i dodano zatrzymywanie punktów przerwania skryptu uruchomione, dopóki nie można dołączyć debugera do debugowania skryptu w obszarze działania. Zagnieżdżone debugowania dla dowolnych obszarach działania dodano obsługę do debugera skryptów programu Windows PowerShell dla obszary działania.
- Dodano nowe polecenie cmdlet Format szesnastkowy [Microsoft.PowerShell.Utility](https://technet.microsoft.com/library/hh849958.aspx) modułu. Format szesnastkowy umożliwia wyświetlanie danych tekstowych lub binarnych w formacie szesnastkowym.
- Dodano polecenia cmdlet Schowka GET i Set-Schowka [Microsoft.PowerShell.Utility](https://technet.microsoft.com/library/hh849958.aspx) modułu; mogą ułatwić transferem zawartości do i z sesji środowiska Windows PowerShell. Polecenia cmdlet Schowka obsługuje obrazy, pliki audio, listy plików i tekst.
- Dodano nowe polecenie cmdlet Clear-RecycleBin [Microsoft.PowerShell.Management](https://technet.microsoft.com/library/hh849827(v=wps.640).aspx) moduł; pustych elementów tego polecenia cmdlet, Recycle Bin dla stałych dysków zawiera zewnętrzne stacje dysków. Domyślnie monit o potwierdzenie polecenia Clear-RecycleBin, ponieważ ConfirmImpact.High ustawiono właściwość ConfirmImpact polecenia cmdlet.
- Nowe polecenie cmdlet New-TemporaryFile pozwala utworzyć pliku tymczasowego w ramach mechanizmu obsługi skryptów. Domyślnie nowy plik tymczasowy zostanie utworzony w ```C:\Users\<user name>\AppData\Local\Temp```.
- Out-File, Dodaj zawartość i polecenia cmdlet Set-Content powstał nowy parametr - NoNewline, który pomija znakiem nowego wiersza po danych wyjściowych.
- Polecenie cmdlet New-Guid korzysta z klasy identyfikator Guid programu .NET Framework, można wygenerować identyfikatora GUID, przydatne podczas pisania skryptów lub zasoby DSC.
- Ponieważ informacje o wersji pliku mogą być może być mylące, szczególnie w przypadku, po pliku jest zastosowana poprawka, nowe właściwości skryptu FileVersionRaw i ProductVersionRaw są dostępne dla obiektów FileInfo. Na przykład uruchomieniem następujące polecenie, aby wyświetlić wartości tych właściwości powershell.exe, gdzie $pid zawiera identyfikator procesu dla uruchomionej sesji programu Windows PowerShell:  ```Get-Process -Id $pid -FileVersionInfo | Format-List *version* -Force```
- Nowe polecenia cmdlet Enter PSHostProcess i PSHostProcess zakończenia umożliwiają debugowanie skryptów programu Windows PowerShell w procesach, niezależnie od bieżącego procesu, który działa w konsoli programu Windows PowerShell. Uruchom PSHostProcess Enter, aby wprowadzić lub dołączyć do określonego procesu o identyfikatorze, a następnie uruchom obszarem działania Get do zwrócenia active obszarach działania w ramach procesu. Uruchom PSHostProcess Zakończ, aby odłączyć od procesu, po zakończeniu debugowania skryptu w ramach procesu.
- Dodano nowe polecenie cmdlet Wait-debugera [Microsoft.PowerShell.Utility](https://technet.microsoft.com/library/hh849958.aspx) modułu. Możesz uruchomić oczekiwania-debugera, aby zatrzymać skrypt w debugerze Przed uruchomieniem następną instrukcję w skrypcie.
- Debuger przepływu pracy środowiska Windows PowerShell obsługuje teraz ukończenie polecenia lub kartę, a następnie można debugować funkcje zagnieżdżony przepływ pracy. Teraz można nacisnąć klawisz **Ctrl + Break** wprowadzenia debugera, uruchamianie skryptu, lokalne i zdalne sesji i skrypt przepływu pracy.
- Dodano polecenie cmdlet debugowania zadania [Microsoft.PowerShell.Core](https://technet.microsoft.com/library/hh849695.aspx) modułu, aby debugować uruchamianie skryptów zadania przepływu pracy środowiska Windows PowerShell, tła i zadania uruchomione w sesji zdalnej.
- Nowy stan AtBreakpoint, została dodana do zadań programu Windows PowerShell. Stan AtBreakpoint ma zastosowanie, gdy zadanie jest uruchomione skryptu, który zawiera Ustawianie punktów przerwania, a skrypt został trafiony punkt przerwania. Jeśli zadanie zostało zatrzymane w punkcie przerwania debugowania, należy debugować zadania, uruchamiając polecenie cmdlet debugowania zadania.
- Windows PowerShell 5.0 implementuje obsługę wielu wersji pojedynczy moduł programu Windows PowerShell, w tym samym folderze, w $PSModulePath. Właściwość RequiredVersion została dodana do klasy ModuleSpecification, aby pomóc uzyskać odpowiednią wersję modułu; Ta właściwość jest wzajemnie wykluczających się przy użyciu właściwości ModuleVersion. RequiredVersion jest teraz obsługiwana jako część wartości parametru element FullyQualifiedName Get-Module Import-Module i polecenia cmdlet Remove-Module.
- Będzie można wykonywać sprawdzanie poprawności wersji modułu, uruchamiając polecenie cmdlet Test-ModuleManifest.
- Wyniki polecenia cmdlet Get-Command są teraz wyświetlane kolumny wersji; nowe właściwość wersja została dodana do klasy CommandInfo. Get-Command przedstawiono polecenia z wielu wersji tego samego modułu. Właściwości wersji jest również częścią klasy pochodne CmdletInfo: CmdletInfo i ApplicationInfo.
- Get-Command ma nowy parametr - ShowCommandInfo, która zwraca informacje ShowCommand jako PSObjects. Jest to szczególnie przydatne funkcje podczas uruchamiania polecenia Show w środowisku Windows PowerShell ISE, przy użyciu komunikacji zdalnej programu Windows PowerShell. Parametr - ShowCommandInfo zastępuje istniejącą funkcję Get SerializedCommand modułu Microsoft.PowerShell.Utility skryptu Get SerializedCommand jest jednak nadal dostępne do obsługi skryptów niskiego poziomu.
- Nowe polecenie cmdlet Get-ItemPropertyValue pozwala uzyskać wartość właściwości bez przy użyciu notacji z kropką. Na przykład w starszych wersjach programu Windows PowerShell, można uruchomić następujące polecenie, aby pobrać wartości właściwości podstawy aplikacji PowerShellEngine klucza rejestru: **(Get-zmieniona właściwość elementu — ścieżka HKLM:\\oprogramowania\\Microsoft\\PowerShell\\3\\PowerShellEngine — nazwa ApplicationBase). ApplicationBase**. Począwszy od programu Windows PowerShell 5.0, możesz uruchomić **Get ItemPropertyValue-HKLM ścieżki:\\oprogramowania\\Microsoft\\PowerShell\\3\\PowerShellEngine — ApplicationBase nazwy** .
- Konsolę programu Windows PowerShell używa teraz kolorowania, podobnie jak w przypadku środowiska Windows PowerShell ISE.
- Nowy moduł NetworkSwitch zawiera polecenia cmdlet, które umożliwiają zastosowanie przełącznika, wirtualnej sieci LAN (VLAN) i podstawowa konfiguracja portu przełącznika sieci warstwy 2 do przełączników sieciowych z certyfikatem logo systemu Windows Server 2012 R2.
- Dodano parametr element FullyQualifiedName do poleceń cmdlet Import-Module i Remove-Module, do obsługi, przechowywania wielu wersji pojedynczy moduł.
- Save-Help, Update-Help, Import-PSSession, Export-PSSession i Get-Command ma nowy parametr FullyQualifiedModule typu ModuleSpecification. Dodaj ten parametr, aby określić modułu w jego w pełni kwalifikowanej nazwy.
- Wartość **$PSVersionTable.PSVersion** został zaktualizowany do wersji 5.0.
- Program WMF 5.0 (PowerShell 5.0) zawiera **usług Pester** modułu.  Pester jest testowania jednostkowego dla programu PowerShell. Zapewnia kilka słów kluczowych prosty w obsłudze, które pozwalają na tworzenie testów dla skryptów.

### <a name="new-features-in-windows-powershell-desired-state-configuration"></a>Nowe funkcje programu Windows PowerShell Desired State Configuration

- Ulepszenia języka programu Windows PowerShell umożliwiają definiowanie zasobów Windows PowerShell Desired State Configuration (DSC) przy użyciu klas. Import-DscResource jest teraz dynamiczne słowo kluczowe true; Program Windows PowerShell analizuje modułu głównego określonego modułu, Wyszukiwanie klas, które zawierają atrybut DscResource. Klasy umożliwia teraz zdefiniować zasoby DSC, w których nie jest wymagany plik MOF, ani podfolderu DSCResource w folderze modułu. Plik modułu programu Windows PowerShell może zawierać wielu klas zasobów DSC.
- Nowy parametr ThrottleLimit, dołączonym do następujących poleceń cmdlet w PSDesiredStateConfiguration module. Dodaj parametr ThrottleLimit, aby określić liczbę komputerów docelowych lub urządzeń, na których ma zostać polecenia do pracy w tym samym czasie.
  - Get-DscConfiguration
  - Get-DscConfigurationStatus
  - Get-DscLocalConfigurationManager
  - Przywracanie DscConfiguration
  - Test-DscConfiguration
  - Porównaj DscConfiguration
  - Publikowanie DscConfiguration
  - Set-DscLocalConfigurationManager
  - Start-DscConfiguration
  - Update-DscConfiguration
- Za pomocą scentralizowanego DSC raportowanie błędów, szczegółowych informacji o błędach jest nie tylko rejestrowane w zdarzeń dziennika, ale mogą być wysyłane do centralnej lokalizacji w celu późniejszej analizy. Do przechowywania błędy konfiguracji DSC, które miały miejsce dla każdego serwera w swoim środowisku, można użyć tej centralnej lokalizacji. Po zdefiniowaniu w metadanych konfiguracji serwera raportów wszystkie błędy są wysyłane do serwera raportów, a następnie przechowywane w bazie danych. Możesz skonfigurować tę funkcję, niezależnie od tego, czy węzeł docelowy jest skonfigurowany do ściągania konfiguracji z serwera ściągania.
- Ulepszenia środowiska Windows PowerShell ISE jej obsługi ułatwiają realizację tworzenia zasobu DSC. Można teraz wykonaj następujące czynności.
  - Wyświetla listę wszystkich zasobów DSC w ramach **konfiguracji** lub **węzła** bloku, wprowadzając **Ctrl + spacja** w pustym wierszu w bloku.
  - Automatyczne uzupełnianie na właściwości zasobów **wyliczenie** typu.
  - Automatyczne uzupełnianie na **DependsOn** własności zasobów DSC, w oparciu o innych wystąpień zasobów w konfiguracji.
  - Ulepszone kartę zakończenia wartości właściwości zasobu.
- Użytkownik może teraz uruchomić zasobami dostępnymi w ramach określonego zestawu poświadczeń, dodając **PSDscRunAsCredential** atrybutu do bloku węzła. Na przykład PSDscRunAsCredential = Get-Credential Contoso\\DscUser. Ta funkcja jest przydatne w przypadku tworzenia konfiguracji, które uruchom Instalator Windows i instalatory pliku wykonywalnego, dostęp do gałęzi rejestru użytkownika lub wykonywać inne zadania poza bieżący kontekst użytkownika.
- Dodano obsługę (w oparciu o x86) 32-bitową **konfiguracji** — słowo kluczowe.
- Program Windows PowerShell teraz obejmuje obsługę niestandardowej pomocy dla konfiguracji DSC, określonych przez dodanie \[CmdletBinding()] funkcji wygenerowaną konfigurację.
- Nowy **DscLocalConfigurationManager** atrybut określa blok konfiguracji meta-konfiguracji, który jest używany do konfigurowania DSC Local Configuration Manager. Ten atrybut ogranicza konfiguracji zawierającego tylko elementy, co powoduje ich skonfigurowanie DSC Local Configuration Manager. Podczas przetwarzania tej konfiguracji generuje \*. plik meta.mof, który jest następnie wysyłana do węzłów odpowiedniego obiektu docelowego, uruchamiając polecenie cmdlet Set-DscLocalConfigurationManager.
- Konfiguracje częściowe są teraz dozwolone w programie Windows PowerShell 5.0. Konfiguracja dokumentów można dostarczyć do węzła we fragmentach. W przypadku węzła do odbierania wielu fragmentów dokumentu konfiguracji węzła Local Configuration Manager musisz wybrać opcję do określenia oczekiwanych fragmentów
- Synchronizacja między komputerami jest nowa w DSC w programie Windows PowerShell 5.0. Za pomocą wbudowanych WaitFor\* zasobów (**WaitForAll**, **WaitForAny**, i **WaitForSome**), możesz teraz określić zależności na komputerach podczas konfiguracji jest uruchamiana, bez zewnętrznych aranżacji. Te zasoby zawierają synchronizacji węzła do węzła przy użyciu połączenia modelu wspólnych informacji za pośrednictwem protokołu WS-Man. Konfiguracja poczekać, aż zmianę stanu określonego zasobu innego komputera.
- Po prostu wystarczająco administracji (JEA), nowa funkcja zabezpieczeń delegowanie, korzysta z DSC i programu Windows PowerShell ograniczone obszary działania ułatwiające przedsiębiorstwom bezpieczne od utraty danych lub naruszenie przez pracowników, czy zamierzone lub przypadkowe. Aby uzyskać więcej informacji na temat technologii JEA, w tym, gdzie można pobrać zasobu xJEA DSC, zobacz [Just Enough Administration, krok po kroku](https://blogs.technet.com/b/privatecloud/archive/2014/05/14/just-enough-administration-step-by-step.aspx).
- Dodano następujące nowe polecenia cmdlet modułu PSDesiredStateConfiguration.
  - Nowe polecenie cmdlet Get-DscConfigurationStatus pobiera ogólne informacje o stanie konfiguracji z węzła docelowego. Można uzyskać stanu ostatniego lub wszystkie konfiguracje.
  - Nowe polecenie cmdlet Compare-DscConfiguration porównuje określonej konfiguracji z faktycznym stanem co najmniej jeden węzeł docelowy.
  - Nowe polecenie cmdlet Publish-DscConfiguration kopiuje pliku MOF konfiguracji do węzła docelowego, ale nie ma zastosowania konfiguracji. Konfiguracja jest stosowana podczas następnego przebiegu spójności lub po uruchomieniu polecenia cmdlet Update-DscConfiguration.
  - Nowe polecenie cmdlet Test-DscConfiguration umożliwia zweryfikowanie, że wynikowa konfiguracja odpowiada wymaganą konfiguracją, zwraca wartość PRAWDA, jeśli konfiguracji dopasowuje odpowiednią konfigurację, lub FAŁSZ, jeśli rzeczywista konfiguracja nie jest zgodna żądany Konfiguracja.
  - Nowe polecenie cmdlet Update-DscConfiguration wymusza konfiguracji do przetworzenia. W przypadku programu Local Configuration Manager w tryb ściągania, polecenie cmdlet pobiera konfigurację z serwera ściągania przed zastosowaniem.

### <a name="new-features-in-windows-powershell-ise"></a>Nowe funkcje w środowisku Windows PowerShell ISE

- Teraz możesz edytować zdalnego skryptów programu Windows PowerShell i plikami w lokalnej kopii środowiska Windows PowerShell ISE systemem Enter-PSSession, aby rozpocząć sesję zdalną na komputerze, który zapisuje pliki, które chcesz edytować, a następnie uruchamiając **PSEdit \<ścieżkę i nazwę pliku na komputerze zdalnym\>**. Ta funkcja ułatwia edycji plików programu Windows PowerShell, które są przechowywane w opcji instalacji Server Core systemu Windows Server, których nie można uruchomić program Windows PowerShell ISE.
- Polecenie cmdlet Start-zapis jest teraz obsługiwany w środowisku Windows PowerShell ISE.
- Można teraz debugować skrypty zdalnego w środowisku Windows PowerShell ISE.
- Nowe polecenie menu, **Przerwij wszystko** (Ctrl + B) przerywa debugowanie lokalne i zdalne uruchamianie skryptów.

### <a name="new-features-in-windows-powershell-web-services-management-odata-iis-extension"></a>Nowe funkcje w usługach sieci Web programu Windows PowerShell (rozszerzenie zarządzania OData IIS)

- Począwszy od programu Windows PowerShell 5.0, można wygenerować zestaw poleceń cmdlet programu Windows PowerShell, oparte na funkcji udostępnianych przez dany punkt końcowy OData, uruchamiając polecenie cmdlet Export-ODataEndpointProxy, znaleziono w nowym [ Microsoft.PowerShell.OdataUtils](https://technet.microsoft.com/library/dn818507(v=wps.640).aspx) modułu.

### <a name="notable-bug-fixes-in-windows-powershell-50"></a>Istotne poprawki błędów w programie Windows PowerShell 5.0

- Windows PowerShell 5.0 zawiera nową metodę implementacji modelu COM, która oferuje znaczne ulepszenia wydajności, podczas pracy z obiektami COM. Wideo demonstracyjne efekt, zobacz [Com_Perf_Improvements](https://1drv.ms/1qu3UPZ).
- Wprowadzono znaczne ulepszenia wydajności w pierwszym zakończenie karty w sesji programu Windows PowerShell, skrócić czas ukończenia karty przez prawie 500 ms.

## <a name="new-features-in-windows-powershell-40"></a>Nowe funkcje programu Windows PowerShell 4.0

Windows PowerShell 4.0 jest zgodne z poprzednimi wersjami. Polecenia cmdlet, dostawców, moduły, przystawki, skrypty, funkcje i profile, które zostały zaprojektowane dla programu Windows PowerShell 3.0 i Windows PowerShell 2.0 działają w programie Windows PowerShell 4.0, bez konieczności wprowadzania zmian.

Windows PowerShell 4.0 jest zainstalowana domyślnie w systemie Windows 8.1 i Windows Server 2012 R2. Aby zainstalować program Windows PowerShell 4.0, Windows 7 z dodatkiem SP1 lub Windows Server 2008 R2, Pobierz i zainstaluj [Windows Management Framework 4.0](https://www.microsoft.com/download/details.aspx?id=40855). Pamiętaj odczytać szczegółów pobierania i spełniać wszystkie wymagania systemowe, przed zainstalowaniem programu Windows Management Framework 4.0.

- [Nowe funkcje w programie Windows PowerShell](#new-features-in-windows-powershell-1)
- [Nowe funkcje w Windows PowerShell zintegrowane Scripting Environment (ISE)](#new-features-in-windows-powershell-integrated-scripting-environment-ise)
- [Nowe funkcje w przepływie pracy programu Windows PowerShell](#new-features-in-windows-powershell-workflow)
- [Nowe funkcje w usługach sieci Web programu Windows PowerShell](#new-features-in-windows-powershell-web-services)
- [Nowe funkcje w programie Windows PowerShell Web Access](#new-features-in-windows-powershell-web-access)
- [Istotne poprawki błędów w programie Windows PowerShell 4.0](#notable-bug-fixes-in-windows-powershell-40)

Windows PowerShell 4.0 obejmuje następujące nowe funkcje.

### <a name="new-features-in-windows-powershell"></a>Nowe funkcje w programie Windows PowerShell

- **Windows PowerShell Desired State Configuration** (DSC) jest systemem zarządzania w programie Windows PowerShell 4.0, umożliwiająca wdrażanie i zarządzanie dane konfiguracyjne dla usług oprogramowania i środowiska, w którym są uruchomione te usługi. Aby uzyskać więcej informacji na temat DSC, zobacz [Rozpoczynanie pracy z usługą Windows PowerShell Desired State Configuration](https://technet.microsoft.com/library/c134aa32-b085-4656-9a89-955d8ff768d0).
- **Save-Help** teraz umożliwia zapisywanie pomocy dla modułów, które są zainstalowane na komputerach zdalnych. Save-Help umożliwia pobieranie modułu pomocy z klienta podłączonej do Internetu (na którym nie wszystkie moduły, dla których ma dotyczyć pomoc są musi być zainstalowany), a następnie skopiuj zapisane pomocy do zdalnego folderu udostępnionego lub komputerze zdalnym, który nie ma Internet dostęp.
- Debuger programu Windows PowerShell został rozszerzony w celu zezwolenia na debugowanie przepływów pracy programu Windows PowerShell, a także skrypty, które są uruchomione na komputerach zdalnych. Przepływy pracy środowiska Windows PowerShell można teraz debugować na poziomie skryptu z wiersza polecenia środowiska Windows PowerShell lub programu Windows PowerShell ISE. Można teraz debugować skrypty programu Windows PowerShell, w tym skryptowych przepływach pracy, sesji zdalnej. Sesji debugowania zdalnego zostaną zachowane w sesji zdalnej programu Windows PowerShell, które rozłączone, a następnie później ponownie podłączony.
- A **RunNow** parametr **Register-ScheduledJob** i **Set-ScheduledJob** eliminuje potrzebę zestawu bezpośredniego daty i godziny rozpoczęcia zadań przy użyciu **Wyzwalacza** parametru.
- **Invoke-RestMethod** i **Invoke-WebRequest** umożliwiają teraz ustawić wszystkie nagłówki przy użyciu parametru nagłówków. Mimo że ten parametr ma zawsze istniała, była jedną z kilku parametrów dla polecenia cmdlet w sieci web, które spowodowały błędy lub wyjątki.
- **Get-Module** ma nowy parametr **element FullyQualifiedName**, typu **ModuleSpecification\[]**. **Element FullyQualifiedName** parametr Get-Module umożliwia teraz określić modułu przy użyciu modułu nazwę, wersję i, opcjonalnie, jego identyfikator GUID.
- Domyślne ustawienie zasad wykonywania w systemie Windows Server 2012 R2 jest **RemoteSigned**. Na Windows 8.1 nie ma zmian w domyślnych ustawień.
- Począwszy od programu Windows PowerShell 4.0, wywołanie metody przy użyciu nazw metoda dynamiczna jest obsługiwana. Można użyć zmiennej do przechowywania nazwy metody, a następnie dynamicznie wywołania metody, wywołując zmiennej.
- Zadania asynchronicznego przepływu pracy nie jest już są usuwane, gdy przed upłynięciem limitu czasu określony przez **PSElapsedTimeoutSec** upłynął typowego parametru przepływu pracy.
- Nowy parametr **RepeatIndefinitely**, została dodana do **New-JobTrigger** i **Set-JobTrigger** polecenia cmdlet. Pozwala to wyeliminować konieczność określania **TimeSpan.MaxValue** wartość **RepetitionDuration** parametru, aby uruchomić zaplanowanego zadania wielokrotnie nieokreślony.
- A **Passthru** parametr został dodany do **Enable-JobTrigger** i **Disable-JobTrigger** polecenia cmdlet. Z parametru Passthru Wyświetla wszystkie obiekty, które są tworzone lub modyfikowane przez polecenie.
- Nazwy parametrów do określania grupy roboczej w **Add-Computer** i **Remove-Computer** poleceń cmdlet teraz są spójne. Oba polecenia cmdlet teraz użyć parametru **Nazwa_grupy_roboczej**.
- Nowy parametr typowe **PipelineVariable**, został dodany. PipelineVariable pozwala zapisać wyniki gazociągami polecenie (lub część polecenia gazociągami) jako zmienną, który może być przekazywany przez resztę potoku.
- Filtrowanie przy użyciu składni metody kolekcji jest teraz obsługiwane. Oznacza to, czy można teraz filtrować zbiór obiektów przy użyciu uproszczoną składnię, podobnie jak w przypadku Where() lub Where-Object, sformatowane jako wywołania metody. Oto przykład: .Where (get-Process) ({$_. Nazwa — dopasowania "powershell"})
- **Get-Process** polecenie cmdlet ma nowy parametr przełącznika **IncludeUserName**.
- Nowe polecenie cmdlet **Get FileHash**, która zwraca wartość skrótu pliku w jednym z kilku formatów dla określonego pliku, został dodany.
- W programu Windows PowerShell 4.0, jeśli moduł **DefaultCommandPrefix** klucza w swoim manifeście lub jeśli użytkownik importuje moduł o **prefiksu** parametru **ExportedCommands**właściwość modułu zawiera polecenia w module z prefiksem. Po uruchomieniu polecenia przy użyciu składni kwalifikowana modułu ModuleName\\CommandName, nazwy poleceń musi zawierać prefiks.
- Wartość **$PSVersionTable.PSVersion** została zaktualizowana w celu 4.0.
- **WHERE()** zachowanie operator został zmieniony. `Collection.Where('property -match name')` akceptowanie wyrażenia ciągu w formacie `"Property -CompareOperator Value"` nie jest już obsługiwana. Jednak **Where()** operator akceptuje wyrażenia ciągu w formacie scriptblock; ta funkcja jest nadal obsługiwana.

### <a name="new-features-in-windows-powershell-integrated-scripting-environment-ise"></a>Nowe funkcje w Windows PowerShell zintegrowane Scripting Environment (ISE)

- Windows PowerShell ISE obsługuje debugowanie przepływu pracy programu Windows PowerShell i zdalne debugowanie skryptu.
- Dodano obsługę funkcji IntelliSense dla dostawców Desired State Configuration programu Windows PowerShell i konfiguracji.

### <a name="new-features-in-windows-powershell-workflow"></a>Nowe funkcje w przepływie pracy programu Windows PowerShell

- Dodano obsługę nowej **PipelineVariable** typowego parametru w kontekście iteracyjne potoki, takich jak te używane przez System Center Orchestrator; oznacza to, Uruchom polecenia, po prostu od lewej do prawej, w przeciwieństwie do potoków przeplatane uruchomiona przy użyciu przesyłania strumieniowego.
- Wiązanie parametru został znacząco udoskonalony w celu pracować poza kartę uzupełniania scenariuszy, takich jak polecenia, które nie istnieją w bieżącym obszarze działania.
- Obsługa kontenerów niestandardowych działań dołączonym do przepływu pracy środowiska Windows PowerShell. W przypadku parametru działania typów **działania**, **działania\[]** (lub jest kolekcją ogólną działania) i dostarczone przez użytkownika bloku skryptu jako argument, a następnie programu Windows PowerShell Przepływ pracy konwertuje blok skryptu XAML, podobnie jak w przypadku normalnej kompilacji pracy skryptu programu Windows PowerShell.
- Po awarii programu Windows PowerShell Workflow automatycznie połączy się ponownie na węzłach zarządzanych.
- Teraz możesz ograniczyć **Foreach-równoległe** instrukcji działania przy użyciu **ThrottleLimit** właściwości.
- **ErrorAction** typowego parametru ma nową prawidłową wartość **Wstrzymaj**, która jest przeznaczona wyłącznie dla przepływów pracy.
- Punkt końcowy przepływu pracy teraz automatycznie zamyka, jeśli istnieją nie aktywne sesje, żadne zadania w toku i żadne oczekujące zadania. Ta funkcja zmniejsza wykorzystanie zasobów na komputerze, który działa jako serwer przepływu pracy po spełnieniu warunków automatycznego zamknięcia.

### <a name="new-features-in-windows-powershell-web-services"></a>Nowe funkcje w usługach sieci Web programu Windows PowerShell

- Po wystąpieniu błędu w usługach sieci Web Services (PSWS, również o nazwie OData IIS rozszerzenie do zarządzania), podczas Windows PowerShell polecenia cmdlet jest uruchomiony, bardziej szczegółowy komunikat o błędzie komunikaty są zwracane do obiektu wywołującego. Ponadto, postępuj zgodnie z kodami błędów [wytycznych kod błędu systemu Windows Azure REST API](https://msdn.microsoft.com/library/windowsazure/dd179357.aspx).
- Punkt końcowy można teraz określić wersję interfejsu API, a także wymusić użycie określonej wersji interfejsu API. Zawsze, gdy wystąpi niezgodność wersji między klientem i serwerem, błędy są wyświetlane zarówno klient, jak i serwera.
- Zarządzanie schematem wysyłania został uproszczony przez automatyczne generowanie wartości dla wszystkich pól, brakuje w schemacie. Generowanie występuje, jako dobry punkt wyjścia, nawet jeśli schemat wysyłania nie istnieje.
- Typ obsługi w PSWS został ulepszony, aby obsługiwać typy, które zachowuje się podobnie jak za pomocą innego konstruktora niż Konstruktor domyślny **PSTypeConverter** w programie Windows PowerShell. Dzięki temu można korzystać z PSWS tych typów złożonych.
- PSWS teraz umożliwia rozwijanie skojarzonego wystąpienia podczas wykonywania zapytania. Dla większych binarne zawartości (takich jak obrazy, audio lub wideo) koszt transferu jest znaczący, a lepiej transferu danych binarnych bez kodowania. PSWS używa strumieni nazwany zasób dla przesyłania bez kodowania. Strumień zasobu o nazwie jest właściwością jednostki **Edm.Stream** typu. Każdego strumienia nazwany zasób ma oddzielne identyfikator URI dla operacji GET lub aktualizacji.
- Akcje protokołu OData teraz mechanizm umożliwiający wywoływanie innego niż CRUD (tworzenia, odczytu, aktualizacji i usuwania) metod w zasobie. Możesz wywołać akcję, wysyłając żądanie HTTP POST do identyfikatora URI, który jest zdefiniowany dla akcji. Parametry akcji są definiowane w treści żądania POST.
- Aby były zgodne z wytycznymi dotyczącymi platformy Windows Azure, można uprościć wszystkie adresy URL. Zmiany zawarte w **klucza jako Segment** umożliwia pojedynczego kluczy może być reprezentowana jako segmentów. Należy pamiętać, odwołań, korzystających z wielu wartości klucza tak jak poprzednio wymagają formacie wartości rozdzielanych przecinkami w nawiasach notacji.
- Przed tym wydaniem PSWS tylko aż do wykonania, tworzenia, aktualizacji i usuwania działań był Post wywoływanie, umieść lub usunąć z zasobem najwyższego poziomu. Nowość w tej wersji PSWS operacje zasobów znajdujących się umożliwiają użytkownikom osiągnąć takie same wyniki podczas osiągnięciem tego samego zasobu mniej bezpośrednio zbliża się tak, jakby były zawarte w tych zasobów.

### <a name="new-features-in-windows-powershell-web-access"></a>Nowe funkcje w programie Windows PowerShell Web Access

- Można odłączyć od i ponowne łączenie do istniejącej sesji w konsoli internetowej programu Windows PowerShell Web Access. A **Zapisz** przycisk w konsoli sieci web umożliwia rozłączyć sesję bez usuwania go i ponownie połączyć się z sesją innego czasu.
- Domyślne parametry mogą być wyświetlane na stronie logowania. Aby wyświetlić parametry domyślne, należy skonfigurować wszystkie ustawienia wyświetlane w wartości **opcjonalne ustawienia połączenia** obszar strony logowania w pliku o nazwie **web.config**. Możesz użyć **web.config** pliku, aby skonfigurować wszystkie opcjonalne ustawienia połączenia z wyjątkiem drugi lub alternatywnego zestawu poświadczeń.
- W systemie Windows Server 2012 R2 można zdalnie zarządzać reguł autoryzacji programu Windows PowerShell Web Access. **Add-PswaAuthorizationRule** i **Test-PswaAuthorizationRule** polecenia cmdlet zawierają teraz parametr Credential, która umożliwia administratorom zarządzanie reguły autoryzacji na komputerze zdalnym lub w Sesja programu Windows PowerShell Web Access.
- Istnieje już wiele sesji programu Windows PowerShell Web Access w pojedynczej sesji przeglądarki, za pomocą nowej karcie przeglądarki dla każdej sesji. Nie potrzebujesz już można otworzyć nową sesję przeglądarki, aby nawiązać połączenie z nową sesję w konsoli internetowej programu Windows PowerShell.

### <a name="notable-bug-fixes-in-windows-powershell-40"></a>Istotne poprawki błędów w programie Windows PowerShell 4.0

- **Get-Counter** teraz można zwrócić liczniki, które zawiera znak apostrofu w francuskim wersji systemu Windows.
- Możesz teraz przeglądać **GetType** metoda po deserializacji obiektów.
- **#Requires** instrukcje umożliwiają teraz użytkownikom, muszą mieć prawa dostępu administratora, jeśli to konieczne.
- **Woluminów Csv Import** polecenia cmdlet obecnie ignoruje pustych wierszy.
- Problem, w których program Windows PowerShell ISE używa zbyt dużo pamięci podczas korzystania z **Invoke-WebRequest** polecenia został rozwiązany.
- **Get-Module** wyświetli teraz wersje modułu w **wersji** kolumny.
- Remove-Item - Recurse teraz usuwa elementy z podfolderów, zgodnie z oczekiwaniami.
- A **UserName** właściwość została dodana do **Get-Process** danych wyjściowych obiektów.
- **Invoke RestMethod** polecenie cmdlet zwraca teraz wszystkie dostępne wyniki.
- **Dodawanie elementu członkowskiego** teraz zostaną uwzględnione w obiektach HashTable, nawet jeśli tabele nie mają jeszcze dostępne.
- **Select-Object - rozwiń** już nie powiedzie się lub generuje wyjątek, jeśli wartość właściwości ma wartość null lub pusty.
- **Get-Process** można teraz używać w potoku z innymi poleceniami, które pobierają **ComputerName** właściwości z obiektów.
- **ConvertTo Json** i **ConvertFrom-Json** mogą teraz akceptować warunków w ramach podwójnych cudzysłowów, a jego komunikaty o błędach są teraz możliwych do zlokalizowania.
- **Get-Job** teraz zwraca wszelkie ukończone zaplanowane zadania, nawet w nowej sesji.
- Problemy związane z Instalowanie i odinstalowywanie wirtualnych dysków twardych za pomocą **FileSystem** dostawcy w programie Windows PowerShell 4.0 zostały naprawione. Programu Windows PowerShell jest teraz w stanie wykryć nowe dyski, gdy są zainstalowane w tej samej sesji.
- Nie trzeba jawnie załadować **ScheduledJob** lub **przepływu pracy** modułów, aby pracować z ich typy zadań.
- Wprowadzono ulepszenia wydajności procesu importowania przepływów pracy, które definiują zagnieżdżone przepływy pracy; Ten proces działa teraz szybciej.

## <a name="new-features-in-windows-powershell-30"></a>Nowe funkcje w środowisku Windows PowerShell 3.0

Windows PowerShell 3.0 zawiera następujące nowe funkcje.

- [Przepływ pracy programu Windows PowerShell](#windows-powershell-workflow)
- [Windows PowerShell Web Access](#windows-powershell-web-access)
- [Nowe funkcje programu Windows PowerShell ISE](#new-windows-powershell-ise-features)
- [Obsługa Microsoft .NET Framework 4.0](#support-for-microsoft-net-framework-4)
- [Obsługa środowiska preinstalacji Windows](#support-for-windows-preinstallation-environment)
- [Sesje rozłączone](#disconnected-sessions)
- [Łączność niezawodnej sesji](#robust-session-connectivity)
- [System aktualizowalnej pomocy](#updatable-help-system)
- [Rozszerzoną pomoc Online](#enhanced-online-help)
- [Integracja modelu CIM](#cim-integration)
- [Pliki konfiguracji sesji](#session-configuration-files)
- [Zaplanowane zadania i integracja harmonogramu zadań](#scheduled-jobs-and-task-scheduler-integration)
- [Ulepszenia języka programu PowerShell Windows](#windows-powershell-language-enhancements)
- [Nowe polecenia cmdlet Core](#new-core-cmdlets)
- [Ulepszenia istniejących podstawowych poleceń cmdlet i dostawców](#improvements-to-existing-core-cmdlets-and-providers)
- [Importowanie modułów zdalnego i odnajdywania](#remote-module-import-and-discovery)
- [Uzupełnianie po naciśnięciu tabulatora rozszerzone](#enhanced-tab-completion)
- [Automatyczne ładowanie modułu](#module-auto-loading)
- [Ulepszenia środowiska modułu](#module-experience-improvements)
- [Polecenie uproszczone odnajdywania](#simplified-command-discovery)
- [Ulepszone rejestrowanie, diagnostyki i obsługa zasad grupy](#improved-logging-diagnostics-and-group-policy-support)
- [Formatowanie i udoskonaleń wyjściowego](#formatting-and-output-improvements)
- [Środowisko hosta rozszerzonej konsoli](#enhanced-console-host-experience)
- [Nowe polecenie Cmdlet i hostowania interfejsów API](#new-cmdlet-and-hosting-apis)
- [Ulepszenia wydajności](#performance-improvements)
- [Uruchom jako i udostępnione hosta — Obsługa](#runas-and-shared-host-support)
- [Ulepszenia obsługi znaków specjalnych](#special-character-handling-improvements)

### <a name="windows-powershell-workflow"></a>Przepływ pracy programu Windows PowerShell

Przepływ pracy programu Windows PowerShell oferuje funkcje programu Windows Workflow Foundation dla programu Windows PowerShell. Można pisanie przepływów pracy w XAML lub w języku środowiska Windows PowerShell i uruchom je tak, jak należy uruchomić polecenie cmdlet. [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) polecenie cmdlet pobiera poleceń przepływu pracy i [Get-Help](https://technet.microsoft.com/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) polecenie cmdlet pobiera tematy Pomocy dotyczące przepływów pracy.

Przepływy pracy są sekwencji działań związanych z zarządzaniem multicomputer, które są długotrwałych, powtarzalne, często powtarzane, równoległego, przerywania, suspendable i ponownego uruchamiania. Przepływy pracy, może zostać wznowiona od zamierzonych lub przypadkowych przerwy w usługach, takich jak awaria sieci, ponowne uruchomienie Windows lub awarii zasilania.

Przepływy pracy są również przenośne; może być wyeksportowany jako lub importowane z plików XAML. Możesz tworzyć niestandardowe konfiguracje sesji, które umożliwiają przepływu pracy lub działania w przepływie pracy do uruchamiania przez użytkowników delegowanego lub podrzędnego.

Poniżej przedstawiono zalety przepływu pracy środowiska Windows PowerShell

- Automatyzacja sekwencji długotrwałych zadań.
- **Zdalne monitorowanie podzadań długotrwałych**. Stan i postęp działań są widoczne w dowolnym momencie.
- **Zarządzanie multicomputer.** Jednocześnie uruchamiać zadania jako przepływy pracy na tysięcy węzłów zarządzanych. Przepływu pracy środowiska Windows PowerShell zawiera wbudowane bibliotekę typowych parametrów zarządzania, takich jak **PSComputerName**, która umożliwia zarządzanie wieloma komputerami scenariuszy.
- **Pojedyncze zadanie wykonywania złożonych procesów.** Możesz łączyć pokrewne skrypty, które implementują cały scenariusz end-to-end w jednym przepływie pracy.
- **Trwałość.** : przepływ pracy jest zapisany (lub wskazywany przez sprawdzenie) w określonych punktach definiowane przez jego autora wznowienia przepływu pracy od ostatniego utrwalonego zadania (lub punktu kontrolnego), zamiast ponownego uruchamiania przepływu pracy od samego początku.
- **Robustness.** Automatyczne odzyskiwanie po awarii. Przepływy pracy poradzą sobie planowanych i nieplanowanych ponownego uruchomienia. Można wstrzymać wykonywania przepływu pracy i wznowienie przepływu pracy od ostatniego punktu stanu trwałego. Autorzy przepływu pracy można wyznaczyć konkretne działania, ponowne uruchamianie w razie awarii na jeden lub więcej węzłów zarządzanych.
- **Możliwość odłączyć, połącz się ponownie i uruchamiać w odłączonej sesji.** Użytkownicy mogą połączyć i odłączyć się od serwera przepływu pracy, ale przepływ pracy działa w sposób ciągły. Możesz wylogować się z komputera klienckiego lub uruchom ponownie komputer i Monitoruj wykonywanie przepływu pracy z innego komputera bez przerywania przepływu pracy.
- **Podczas planowania.** Podobnie jak wszystkie polecenia cmdlet programu Windows PowerShell lub skryptu można zaplanować zadania przepływu pracy.
- **Przepływ pracy i ograniczania przepustowości połączenia.** Połączenia z węzłami i wykonywanie przepływu pracy mogą być ograniczone, umożliwiając w ten sposób scenariusze dotyczące skalowalności i wysokiej dostępności.

### <a name="windows-powershell-web-access"></a>Windows PowerShell Web Access

Windows PowerShell Web Access jest funkcją systemu Windows Server 2012, która pozwala użytkownikom na uruchamianie poleceń programu Windows PowerShell i skryptów z poziomu konsoli sieci web. Urządzenia korzystające z konsoli sieci web, które nie wymagają programu Windows PowerShell, oprogramowanie do zarządzania zdalnego lub instalacje wtyczki przeglądarki. Wszystko, co jest wymagane jest prawidłowo skonfigurowana brama programu Windows PowerShell Web Access i przeglądarka na urządzeniu klienckim obsługuje język JavaScript, która akceptuje pliki cookie.

Aby uzyskać więcej informacji, zobacz [wdrożenia Windows PowerShell Web Access](https://go.microsoft.com/fwlink/p/?LinkID=221050).

### <a name="new-windows-powershell-ise-features"></a>Nowe funkcje programu Windows PowerShell ISE

Dla programu Windows PowerShell 3.0, Windows PowerShell zintegrowane Scripting Environment (ISE) oferuje wiele nowych funkcji, w tym funkcji IntelliSense, okno polecenia Show ujednoliconego okienku konsoli, fragmenty kodu, parowanie nawiasów klamrowych, Rozwiń / Zwiń sekcje, automatycznego zapisywania, ostatnio używanych elementów listy, kopię sformatowanego, blokowanie kopiowania i Pełna obsługa pisania przepływów pracy skryptów programu Windows PowerShell. Aby uzyskać więcej informacji, zobacz [about_Windows_PowerShell_ISE [3]](https://technet.microsoft.com/library/dfa54d47-60c6-4fff-8197-c747e8d411bb).

### <a name="support-for-microsoft-net-framework-4"></a>Obsługa Microsoft .NET Framework 4

Program Windows PowerShell jest skompilowana wspólnej 4.0 środowiska uruchomieniowego języka. Polecenia cmdlet, skrypty i autorzy przepływów pracy za pomocą nowych klas Microsoft .NET Framework 4 w programie Windows PowerShell, funkcje, które obejmują zgodności aplikacji i wdrożenia, Managed Extensibility Framework, przetwarzania równoległego, sieć, Windows Communication Foundation i Windows Workflow Foundation.

### <a name="support-for-windows-preinstallation-environment"></a>Obsługa środowiska preinstalacji Windows

Windows PowerShell 3.0 jest składnikiem opcjonalnym Windows środowisko preinstalacji systemu Windows (Windows PE) 4.0 dla systemu Windows 8. Windows PE to minimalny system operacyjny, który uruchamia komputer, który nie ma systemu operacyjnego i przygotowuje je do instalacji Windows. Środowiska Windows PE może służyć do partycji i sformatować dyski twarde, kopiować obrazy dysków na komputerze i inicjowania Instalatora Windows z udziału sieciowego. Windows PowerShell 3.0 może służyć w środowisku Windows PE do zarządzania wdrażaniem, diagnostyki i scenariuszy odzyskiwania.

### <a name="disconnected-sessions"></a>Sesje rozłączone

Począwszy od programu Windows PowerShell 3.0 trwały zarządzany przez użytkownika sesji ("sterować") tworzonych za pomocą polecenia cmdlet New-PSSession są zapisywane na komputerze zdalnym. Nie są one zależne od sesji, w którym zostały utworzone.

Teraz możesz odłączyć od sesji bez zakłócania pracy z poleceniami, które są uruchomione w sesji. Można zamknąć sesję i Wyłącz komputer. Później można ponownie połączyć się z sesją z innej sesji na tym samym lub na innym komputerze.

**ComputerName** parametru [Get-PSSession](https://technet.microsoft.com/library/b2b10531-d0df-4746-b877-e75c09955cb6) polecenie cmdlet pobiera z wszystkich sesji użytkownika, które podłączenia do komputera, teraz nawet, jeśli zostały one uruchomione w innej sesji na innym komputerze. Można nawiązać sesji, Pobierz wyniki polecenia, Uruchom nowe polecenia i następnie rozłączyć sesję.

Dodano nowe polecenia cmdlet do obsługi funkcji sesji o odłączony tym [Disconnect-PSSession](https://technet.microsoft.com/library/f8f95111-612f-4cba-9098-77904b0473d8), [Connect-PSSession](https://technet.microsoft.com/library/b803dd29-f208-4079-80d4-db04d778f060), i Receive-PSSession, a nowe parametry zostały dodane do polecenia cmdlet, które sterować, zarządzania, takimi jak **InDisconnectedSession** parametru [Invoke-Command](https://technet.microsoft.com/library/906b4b41-7da8-4330-9363-e7164e5e6970) polecenia cmdlet.

Ta funkcja odłączony sesji jest obsługiwana tylko wtedy, gdy komputery, zarówno na poziomie źródłowym ("client") i przerywa końcach połączenia ("serwer") są uruchomione programu Windows PowerShell 3.0.

### <a name="robust-session-connectivity"></a>Łączność niezawodnej sesji

Windows PowerShell 3.0 wykrywa nieoczekiwany straty korzystać z łączności między klientem a serwerem i podejmie próbę ponownego ustanowienia łączności i automatycznie wznowić wykonywanie. Jeśli nie można ponownie ustanowić połączenia klient serwer, w wyznaczonym czasie, użytkownik jest powiadamiany, a sesja zostaje rozłączona. Podczas próby ponownego połączenia programu Windows PowerShell udostępnia ciągłym informacjom użytkownika.

Jeśli rozłączona sesja została uruchomiona przy użyciu invokecommand —, programu Windows PowerShell tworzy zadanie odłączonej sesji ułatwić Połącz się ponownie i wznowić wykonywanie.

Te funkcje zapewniają bardziej niezawodne i możliwe do odzyskania Obsługa komunikacji zdalnej i umożliwiają użytkownikom do wykonywania długotrwałych zadań, które wymagają niezawodne sesje, takie jak przepływy pracy.

### <a name="updatable-help-system"></a>System aktualizowalnej pomocy

Możesz teraz pobrać pliki zaktualizowane pomocy dla poleceń cmdlet w modułach. [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) polecenia cmdlet identyfikuje najnowszych plików pomocy, pobiera je z Internetu, wypakowuje je, sprawdza poprawność ich i instaluje je w poprawnym katalogu specyficzny dla języka dla modułu.

Aby użyć plików pomocy zaktualizowany, po prostu wpisz `Get-Help`. Nie trzeba uruchomić system Windows lub programu Windows PowerShell. Aby zaktualizować Pomoc dla modułów w katalogu $pshome, należy uruchomić program Windows PowerShell przy użyciu opcji "Uruchom jako administrator".

Do obsługi użytkowników, którzy nie mają dostępu do Internetu i użytkowników za zaporami, nowa [Save-Help](https://technet.microsoft.com/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa) polecenie cmdlet pobiera pliki pomocy do katalogu w systemie plików, na przykład do udziału plików. Użytkownicy mogą następnie korzystać [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) polecenie cmdlet umożliwiające uzyskanie pomocy zaktualizowanych plików z udziału plików.

Możesz użyć [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) pliki wszystkie polecenia cmdlet, aby zaktualizować pomoc lub moduły określonego we wszystkich obsługiwanych interfejsu użytkownika kultur. Możesz nawet umieścić [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) polecenia w swoim profilu programu Windows PowerShell. Domyślnie środowisko Windows PowerShell pliki do pobrania plików pomocy dla modułu nie więcej niż jeden raz każdego dnia.

Moduły systemu Windows 8 i Windows Server 2012 nie dołączaj plików pomocy. Aby pobrać najnowsze pliki pomocy, wpisz `Update-Help`. Aby uzyskać więcej informacji, wpisz `Get-Help` (bez parametrów) lub adresem [about_Updatable_Help](https://technet.microsoft.com/library/10bba75c-f4ac-4ca1-bbf3-8f34dd521ffe).

Gdy pliki pomocy dla polecenia cmdlet nie są zainstalowane na komputerze, [Get-Help](https://technet.microsoft.com/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) polecenie cmdlet wyświetla teraz Pomoc wygenerowany automatycznie. Wygenerowany automatycznie pomocy zawiera składnię polecenia i instrukcje dotyczące korzystania z [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) polecenia cmdlet do pobierania plików pomocy.

Wszelkie autora modułu może obsługiwać aktualizowalnej pomocy dla swojego modułu. Możesz uwzględnić pliki pomocy w module i za pomocą aktualizowalnej pomocy aktualizować lub Pomiń pliki pomocy i używać aktualizowalnej pomocy do zainstalowania go. Aby uzyskać więcej informacji na temat obsługi aktualizowalnej pomocy zobacz [Obsługa aktualizowalnej pomocy](https://go.microsoft.com/FWLink/?LinkID=242129) w bibliotece MSDN.

### <a name="enhanced-online-help"></a>Rozszerzoną pomoc Online

Pomoc programu Windows PowerShell jest wartościowy zasób przeznaczony dla wszystkich użytkowników, ale jest szczególnie ważne dla użytkowników, którzy nie obsługują lub nie można zainstalować pliki zaktualizowane pomocy.

Aby uzyskać pomoc online dla każdego polecenia cmdlet programu Windows PowerShell, wpisz:

```
Get-Help <cmdlet-name> -Online
```

Program Windows PowerShell spowoduje otwarcie wersji online tematu pomocy w domyślnej przeglądarce internetowej.

**Get-Help-Online** funkcji w środowisku Windows PowerShell 3.0 jest teraz jeszcze bardziej wydajne, ponieważ działa ona, nawet gdy plików pomocy dla polecenia cmdlet nie są zainstalowane na komputerze. **Get-Help-Online** funkcja pobiera identyfikator URI dla tematu Pomocy online z właściwości HelpUri, poleceń cmdlet i zaawansowane funkcje.

```
PS C:\>(Get-Command Get-ScheduledJob).HelpUri
http://go.microsoft.com/fwlink/?LinkID=223923
```

W programie Windows PowerShell 3.0, autorzy C# polecenia cmdlet można wypełnić **HelpUri** właściwości, tworząc **HelpUri** atrybutów klasy polecenia cmdlet. Autorzy zaawansowane funkcje mogą definiować **HelpUri** właściwość **CmdletBinding** atrybutu. Wartość **HelpUri** właściwości musi zaczynać się od "http" lub "https".

Możesz również uwzględnić **HelpUri** wartość pierwszego łącza powiązane z pliku pomocy polecenia cmdlet opartego na XML lub. Dyrektywa łącze Pomoc oparta na komentarz w funkcji.

Aby uzyskać więcej informacji na temat obsługi pomocy online, zobacz [Obsługa pomocy Online](/powershell/developer/module/supporting-online-help) w Microsoft Docs.

### <a name="cim-integration"></a>Integracja modelu CIM

Windows PowerShell 3.0 zawiera obsługę dla modelu wspólnych informacji (CIM), oferujący wspólnych definicji informacji o zarządzaniu systemy, sieci, aplikacji i usług, umożliwiając im wymianę informacji o zarządzaniu między systemy heterogenicznych. Obsługa modelu wspólnych informacji w programie Windows PowerShell 3.0, w tym możliwość tworzenia środowiska Windows PowerShell polecenia cmdlet na podstawie klasy modelu CIM nowej lub istniejącej, poleceń na podstawie polecenia cmdlet definicji plików XML, pomocy technicznej dla platformy .NET modelu wspólnych informacji. Interfejs API modelu wspólnych informacji polecenia cmdlet do zarządzania i dostawców usługi WMI w wersji 2.0.

### <a name="session-configuration-files"></a>Pliki konfiguracji sesji

Począwszy od programu Windows PowerShell 3.0 można zaprojektować niestandardową konfigurację sesji przy użyciu pliku. Plik konfiguracji nowej sesji umożliwia określenie środowiska sesji korzystających z konfiguracji sesji, które moduły skryptów, w tym i pliki w formacie są ładowane do sesji, można użyć poleceń cmdlet i język elementy użytkowników, którzy, które moduły i Skrypty można uruchomić, a zmienne, które mogą zobaczyć.

Można zaprojektować sesji, w którym użytkownicy mogą jedynie uruchamiać polecenia cmdlet z jednego konkretnego modułu lub sesji, w której użytkownicy mają pełną obsługą języka, dostęp do wszystkich modułów i dostęp do skryptów służących do wykonywania zaawansowanych zadań.

W poprzednich wersjach programu Windows PowerShell, kontroli na tym poziomie była dostępna tylko dla osób, które można zapisać C# program lub skrypt uruchamiania złożonych. Teraz każdy członek grupy Administratorzy na komputerze można dostosować konfigurację sesji przy użyciu pliku konfiguracji.

Aby utworzyć plik konfiguracji sesji, użyj [New PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866) polecenia cmdlet. Aby zastosować plik konfiguracji sesji do konfiguracji sesji, należy użyć [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) lub [Set-PSSessionConfiguration](https://technet.microsoft.com/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) polecenia cmdlet.

Aby uzyskać więcej informacji, zobacz [about_Session_Configuration_Files](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configuration_files?view=powershell-5.0) i [New PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866).

### <a name="scheduled-jobs-and-task-scheduler-integration"></a>Zaplanowane zadania i integracja harmonogramu zadań

Możesz teraz zaplanować zadania w tle programu Windows PowerShell i zarządzać nimi w programie Windows PowerShell i w harmonogramie zadań.

Zadania zaplanowane w programie Windows PowerShell są przydatne w środowisku hybrydowym zadania harmonogramu zadań i zadań w tle programu Windows PowerShell.

Np. zadań w tle programu Windows PowerShell zaplanowane zadania uruchamiane asynchronicznie w tle. Wystąpienia elementu Zaplanowane zadanie, które zostały wykonane można zarządzać za pomocą polecenia cmdlet zadania, takie jak [zadanie rozpoczęcia](https://technet.microsoft.com/library/2bc04935-0deb-4ec0-b856-d7290cca6442) i [Get-Job](https://technet.microsoft.com/library/1352c534-7193-46ca-9ab1-0c5219a661ad).

Np. zadań harmonogramu zadań można uruchamiać zadania zaplanowane, jednorazowe lub powtarzającym się harmonogramem lub w odpowiedzi na akcję lub zdarzeń. Można wyświetlać i zarządzać zaplanowanych zadań w harmonogramie zadań, włączać i wyłączać je, zgodnie z potrzebami, uruchamiaj je lub ich używać jako szablonów i określenie warunków, w których rozpoczęciem zadań.

Ponadto zaplanowane zadania są dostarczane z dostosowany zestaw poleceń cmdlet do zarządzania nimi. Polecenia cmdlet umożliwiają tworzenia, edytowania, zarządzania, wyłączyć i ponownie włącz zaplanowane zadania, tworzenie zaplanowanego zadania wyzwalaczy i ustaw opcje zaplanowanego zadania.

Aby uzyskać więcej informacji o zaplanowanych zadaniach, zobacz [about_Scheduled_Jobs](https://technet.microsoft.com/library/3b546629-703c-4939-b44f-52dd567bce92).

### <a name="windows-powershell-language-enhancements"></a>Ulepszenia języka programu PowerShell Windows

Windows PowerShell 3.0 zawiera wiele funkcji, które ułatwiają jego język prostsze, łatwiejsze do użycia oraz uniknąć typowych błędów. Ulepszenia obejmują właściwości wyliczenia, liczby i długości właściwości skalarne obiektów, nowych operatorów przekierowania, modyfikator zakresu $Using, formatowanie automatycznych zmiennych, elastyczne skryptu PSItem, atrybutów, zmiennych, uproszczone atrybutu argumenty, nazwy poleceń liczbowych, analizowania Stop — operator, tablicy udoskonalone splatting, nowe operatory bitowe, uporządkowany słowników, PSCustomObject rzutowania i rozszerzona Pomoc oparta na komentarzach.

### <a name="new-core-cmdlets"></a>Nowe polecenia cmdlet Core

Nowe polecenia cmdlet zostały dodane do instalacji programu Windows PowerShell Core, w tym polecenia cmdlet do zarządzania zaplanowanych zadań, odłączonej sesji, integracja modelu wspólnych informacji i aktualizowalnej pomocy systemu.

|||
|-|-|
|Dodaj JobTrigger|Nowe z JobTrigger|
|Connect-PSSession|New-PSSessionConfigurationFile|
|ConvertFrom-Json|New-PSTransportOption|
|ConvertTo-Json|New-PSWorkflowExecutionOption|
|Disable-JobTrigger|New-PSWorkflowSession|
|Disable-ScheduledJob|New-ScheduledJobOption|
|Odłącz PSSession|Nowy WinEvent|
|Enable-JobTrigger|Odbieranie PSSession|
|Enable-ScheduledJob|Register-CimIndicationEvent|
|Get-CimAssociatedInstance|Register-ScheduledJob|
|Get-CimClass|Remove-CimInstance|
|Get-CimInstance|Remove-CimSession|
|Get-CimSession|Remove-TypeData|
|Get-ControlPanelItem|Rename-Computer|
|Get-IseSnippet|Resume-Job|
|Get-JobTrigger|Save-Help|
|Get-ScheduledJob|Set-CimInstance|
|Get-ScheduledJobOption|Set-JobTrigger|
|Get-TypeData|Set-ScheduledJob|
|Import-IseSnippet|Set-ScheduledJobOption|
|Invoke-AsWorkflow|Polecenia Show|
|Invoke-CimMethod|Show-ControlPanelItem|
|Invoke-RestMethod|Suspend-Job|
|Invoke-WebRequest|Test-PSSessionConfigurationFile|
|New-CimInstance|Odblokuj plik|
|Nowy CimSession|Unregister-ScheduledJob|
|New-CimSessionOption|Update-Help|
|New-IseSnippet||

### <a name="improvements-to-existing-core-cmdlets-and-providers"></a>Ulepszenia istniejących podstawowych poleceń cmdlet i dostawców

Windows PowerShell 3.0 zawiera nowe funkcje dla istniejących poleceń cmdlet, łącznie z uproszczoną składnię i nowe parametry dla następujących poleceń cmdlet: Polecenia cmdlet komputera służące, CSV poleceń cmdlet Get-ChildItem Get-Command Get-Content, Get-historii — obiekt miary, polecenia cmdlet zabezpieczeń, Select-Object, wybierz parametry, Split-Path, Rozpocznij proces, program Tee-Object, Test-Connection Dodawanie elementu członkowskiego i polecenia cmdlet usługi WMI.

Dostawcy programu Windows PowerShell zostały również znacznie poprawiony, łącznie z obsługą dostawcy certyfikatu zarządzania certyfikatami Secure Socket Layer (SSL) dla hosta sieci web, obsługa poświadczeń, dyski sieciowe trwałe i alternatywne strumienie danych w system plików, dysków.

### <a name="remote-module-import-and-discovery"></a>Importowanie modułów zdalnego i odnajdywania

Windows PowerShell 3.0 rozszerza odnajdywania modułu, importowanie i możliwości niejawne komunikacji zdalnej na komputerach zdalnych. Polecenia cmdlet modułu pobieranie modułów na komputerach zdalnych i zaimportować moduły na komputerze lokalnym lub zdalnym przy użyciu komunikacji zdalnej programu Windows PowerShell. Obsługa nowej sesji CIM umożliwia modelu wspólnych informacji i usługi WMI do zarządzania komputerami z innych niż Windows, importując polecenia na komputerze lokalnym, która niejawnie uruchamiana na komputerze zdalnym.

Aby uzyskać więcej informacji, zobacz Tematy pomocy dla [Get-Module](https://technet.microsoft.com/library/2cccd4c4-9a21-4c77-b691-984ee57242e1) i [Import-Module](https://technet.microsoft.com/library/af616c24-e122-4098-930e-1e3ea2080ade) polecenia cmdlet.

### <a name="enhanced-tab-completion"></a>Uzupełnianie po naciśnięciu tabulatora rozszerzone

Uzupełnianie po naciśnięciu tabulatora w konsoli programu Windows PowerShell teraz kończy nazwy poleceń cmdlet, parametry, wartości parametrów, wyliczenia, .NET Framework typy, COM obiektów, ukryte katalogów i więcej. Funkcję uzupełniania karta została napisana, na podstawie nowego analizatora i drzewo abstrakcyjnej składni, aby obsługiwać więcej scenariuszy, w tym drzew analizy w pamięci i uzupełniania po naciśnięciu tabulatora w linii środkowej.

### <a name="module-auto-loading"></a>Automatyczne ładowanie modułu

[Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) polecenia cmdlet teraz pobiera wszystkie polecenia cmdlet i funkcji ze wszystkich modułów, które są zainstalowane na komputerze, nawet jeśli moduł nie jest zaimportowany do bieżącej sesji.

Po otrzymaniu polecenia cmdlet, które należy służy ona od razu bez importowania wszystkich modułów. Moduły programu Windows PowerShell są teraz importowane automatycznie podczas korzystania z każdego polecenia cmdlet w module. Nie potrzebujesz już moduł i zaimportować go do korzystania z jego poleceń cmdlet.

Automatyczne importowanie modułów jest wyzwalany za pomocą polecenia cmdlet za pomocą polecenia działa **Get-Command** dla polecenia cmdlet bez symboli wieloznacznych lub uruchamia [Get-Help](https://technet.microsoft.com/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) dla polecenia cmdlet bez symboli wieloznacznych.

Można włączyć, wyłączyć i skonfigurować automatyczne importowanie modułów przy użyciu **$PSModuleAutoLoadingPreference** zmiennej preferencji.

Aby uzyskać więcej informacji, zobacz [modułach](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_modules?view=powershell-5.0), [about_Preference_Variables [4]](https://technet.microsoft.com/library/31344314-be29-4286-b039-afa5460cbe8b)i tematy Pomocy dotyczące [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) i [Import-Module](https://technet.microsoft.com/library/af616c24-e122-4098-930e-1e3ea2080ade) polecenia cmdlet.

### <a name="module-experience-improvements"></a>Ulepszenia środowiska modułu

Windows PowerShell 3.0 zapewnia obsługę zaawansowanych funkcji na moduły, w tym następujące nowe funkcje.

1. Moduł rejestrowania dla poszczególnych modułów (LogPipelineExecutionDetails) i nowe ustawienie zasad grupy "Włącz na moduł rejestrowania"
2. Rozszerzony obiektów modułu, które udostępniają wartości z manifestu modułu
3. Nowe **ExportedCommands** właściwość moduły, w tym zagnieżdżone modułów, które polecenia wszystkich typów łączy
4. Ulepszone wykrywanie dostępnych modułów (niezaznaczone zaimportowanych), w tym, co **ścieżki** i **ListAvailable** parametry w tym samym poleceniu
5. Nowe **DefaultCommandPrefix** klucza w manifestach modułu, które pozwala uniknąć konfliktów nazw bez wprowadzania zmian w kodzie modułu.
6. Ulepszone wymagania modułu, w tym w pełni kwalifikowana wymaganych modułów z wersją i identyfikator GUID i automatyczne zaimportowanie wymaganych modułów
7. Zapewniająca, sprawnego funkcjonowania [New ModuleManifest](https://technet.microsoft.com/library/512adced-f42f-4e88-ba7c-834fc9e5d047) polecenia cmdlet.
8. Nowe **modułu** parametr #Requires
9. Ulepszone [Import-Module](https://technet.microsoft.com/library/af616c24-e122-4098-930e-1e3ea2080ade) polecenia cmdlet z obu **MinimumVersion** i **RequiredVersion** parametrów.

### <a name="simplified-command-discovery"></a>Polecenie uproszczone odnajdywania

Nie trzeba importować wszystkie moduły w celu odnalezienia poleceń dostępnych w sesji środowiska. W programie Windows PowerShell 3.0 [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) polecenie cmdlet pobiera wszystkie polecenia z wszystkich zainstalowanych modułów. I, jeśli używasz polecenia, moduł, który eksportuje polecenie jest automatycznie importowane do sesji.

Nowy [polecenie Pokaż](https://technet.microsoft.com/library/65bba50b-91a8-49d5-80a2-a30fc684ba41) polecenia cmdlet przeznaczone dla początkujących. Polecenia w oknie można wyszukiwać. Możesz wyświetlić wszystkie polecenia lub filtrowania przez moduł, zaimportować moduł, klikając przycisk, użyj pola tekstowe i list rozwijanych, aby skonstruować prawidłowe polecenie, a następnie skopiować lub uruchom polecenie bez wychodzenia z okna.

### <a name="improved-logging-diagnostics-and-group-policy-support"></a>Ulepszone rejestrowanie, diagnostyki i obsługa zasad grupy

Windows PowerShell 3.0 poprawia rejestrowanie i śledzenie pomocy technicznej dla modułów i poleceń, z obsługą śledzenia zdarzeń w dziennikach zdarzeń systemu Windows (Windows), można edytować **LogPipelineExecutionDetails** właściwość modułów i "Włącz na moduł Grupa rejestrowania"ustawienie zasad. Teraz można uzyskać wartości parametrów dane dziennika, wyświetlając właściwości dziennika.

### <a name="formatting-and-output-improvements"></a>Formatowanie i udoskonaleń wyjściowego

Nowy format i danych wyjściowych ulepszenia poprawy efektywności wszyscy użytkownicy programu Windows PowerShell. Ulepszenia obejmują przekierowywanie danych wyjściowych dla wszystkich strumieni, rozszerzone polecenia cmdlet w typ aktualizacji, które dodaje typy dynamicznie bez plików Format.ps1xml, zawijanie wyrazów w danych wyjściowych, domyślnie właściwości formatowania niestandardowych obiektów **PSCustomObject** tekst, ulepszone formatowanie dla obiektów WMI heterogenicznych obiektów i pomocy technicznej do przeciążenia metody odnajdywania.

### <a name="enhanced-console-host-experience"></a>Środowisko hosta rozszerzonej konsoli

Program hosta w konsoli programu Windows PowerShell oferuje nowe funkcje w środowisku Windows PowerShell 3.0 tym pojedynczego komórek wielowątkowych domyślnie. Nowa opcja "Uruchom przy użyciu programu PowerShell" w Eksploratorze plików umożliwia uruchamianie skryptów w sesji bez ograniczeń po prostu, klikając prawym przyciskiem myszy. Szybciej uruchamia nowej logiki uruchamiania hosta w konsoli programu Windows PowerShell i nowe czcionki pozwalają personalizować środowisko okna konsoli znanych.

Aby uzyskać więcej informacji, zobacz [about_Run_With_PowerShell](https://technet.microsoft.com/library/c9d9ca5f-eff9-4409-be9d-e43b5b4087eb).

### <a name="new-cmdlet-and-hosting-apis"></a>Nowe polecenie Cmdlet i hostowania interfejsów API

Nowe polecenia Cmdlet interfejsu API i interfejs API hostingu obejmują drzewo składni zaawansowane publicznych interfejsów API (AST) i interfejsów API dla stronicowania potoku, potoki zagnieżdżonych, uzupełniania po naciśnięciu tabulatora pule obszarem działania, Windows RT, atrybut przestarzałe polecenia cmdlet i czasownik i rzeczownik właściwości obiektu FunctionInfo.

### <a name="performance-improvements"></a>Ulepszenia wydajności

Znaczne ulepszenia wydajności w programie Windows PowerShell pochodzą z nowego analizatora języka, który bazuje na dynamicznego środowiska uruchomieniowego języka (DLR) w programie .NET Framework 4. scenę kompilacji skryptu środowiska uruchomieniowego, ulepszenia niezawodności aparatu i zmiany algorytmem [Get-ChildItem](https://technet.microsoft.com/library/75cf79bb-4db6-4a67-8c36-3d20754e2190) , ulepszenia jej wydajności, szczególnie w przypadku udziałów wyszukiwanie w sieci.

### <a name="runas-and-shared-host-support"></a>Uruchom jako i udostępnione hosta — Obsługa

Windows PowerShell 3.0 obejmuje obsługę funkcji Uruchom jako i udostępnione hosta.

*RunAs* funkcja, przeznaczona dla przepływu pracy programu Windows PowerShell, umożliwia użytkownikom konfiguracji sesji tworzenia sesji, które są uruchamiane z uprawnieniami konta użytkownika udostępnionego. Umożliwia to mniej uprzywilejowane użytkownikom na uruchamianie określonych poleceń i skryptów z uprawnieniami administratora oraz zmniejsza potrzebę Dodawanie mniej starszy użytkowników do grupy Administratorzy.

**SharedHost** funkcji umożliwia wielu użytkownikom na wielu komputerach, aby połączyć się z sesją przepływu pracy, który jest jednocześnie, a następnie monitorować postęp przepływu pracy. Użytkowników można uruchomić przepływu pracy na jednym komputerze, a następnie nawiązać sesji przepływu pracy na innym komputerze bez rozłączeniu sesji z oryginalnego komputera. Użytkownicy muszą mieć takie same uprawnienia i korzystać z tej samej konfiguracji sesji. Aby uzyskać więcej informacji zobacz "Systemem Windows przepływu pracy programu PowerShell" w środowisku wprowadzenie przepływu pracy programu Windows PowerShell.

### <a name="special-character-handling-improvements"></a>Ulepszenia obsługi znaków specjalnych

Aby zwiększyć możliwości programu Windows PowerShell 3.0 do interpretacji i zapewnia prawidłowej obsługi znaków specjalnych, **LiteralPath** parametr, który obsługuje znaki specjalne w ścieżkach, jest prawidłowy w prawie wszystkie polecenia cmdlet, które mają  **Ścieżka** parametru, w tym nowym [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) i [Save-Help](https://technet.microsoft.com/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa) polecenia cmdlet. Analizator obejmuje również logikę specjalną w celu poprawy obsługi znaków początkowych (\`) i nawiasy kwadratowe w nazwach plików i ścieżek.

## <a name="see-also"></a>Zobacz też

- [about_Windows_PowerShell_5.0](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_powershell_5.0?view=powershell-5.0)
- [Windows PowerShell](https://go.microsoft.com/fwlink/?LinkID=107116)
