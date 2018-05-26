---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Co to jest nowe w programie Windows PowerShell 5.0
ms.openlocfilehash: f5a27c0541e21b379f88b318cbe09a0344c1b372
ms.sourcegitcommit: 735ccab3fb3834ccd8559fab6700b798e8e5ffbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2018
---
# <a name="whats-new-in-windows-powershell-50"></a>Co to jest nowe w programie Windows PowerShell 5.0
Windows PowerShell 5.0 zawiera znaczące nowe funkcje, które poszerzają, zwiększyć jego użyteczność i umożliwiają kontrolowanie i zarządzanie komputerami z systemem Windows, łatwiejsze i bardziej kompleksowe.

Windows PowerShell 5.0 jest zgodny z poprzednimi wersjami. Polecenia cmdlet, dostawców modułów, przystawki, skrypty, funkcje i profilów, które zostały zaprojektowane dla programu Windows PowerShell 4.0, Windows PowerShell 3.0 i Windows PowerShell 2.0, zwykle działa w programie Windows PowerShell 5.0 bez zmian.

# <a name="installing-windows-powershell"></a>Instalowanie programu Windows PowerShell
Windows PowerShell 5.0 jest instalowany domyślnie w systemie Windows Server 2016 Technical Preview i Windows 10.

Aby zainstalować program Windows PowerShell 5.0 w systemie Windows Server 2012 R2, Windows 8.1 Enterprise lub Windows 8.1 Pro, Pobierz i zainstaluj [Windows Management Framework 5.0](http://aka.ms/wmf5download). Pamiętaj odczytać szczegółów pobierania i spełnia wszystkie wymagania systemowe, przed zainstalowaniem Windows Management Framework 5.0.

## <a name="in-this-topic"></a>W tym temacie

- [Aktualizacje programu Windows PowerShell 4.0 DSC w KB 3000850](#windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850)
- [Nowe funkcje programu Windows PowerShell 5.0](#new-features-in-windows-powershell-50)
- [Nowe funkcje programu Windows PowerShell 4.0](#new-features-in-windows-powershell-40)
- [Nowe funkcje programu Windows PowerShell 3.0](#new-features-in-windows-powershell-30)

## <a name="windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850"></a>Aktualizacje programu Windows PowerShell 4.0 w listopadzie 2014 r. zbiorczy (KB 3000850)
Wiele aktualizacji i ulepszeń do systemu Windows PowerShell Desired stan konfiguracji (DSC) w programie Windows PowerShell 4.0 są dostępne w [pakiet zbiorczy aktualizacji listopada 2014 r. dla systemu Windows RT 8.1, Windows 8.1 i Windows Server 2012 R2](https://support.microsoft.com/kb/3000850/) (KB 3000850 ). Można określić, czy KB 3000850 jest zainstalowany w systemie, uruchamiając `Get-Hotfix -Id KB3000850` w programie Windows PowerShell.

- Aktualizacje do istniejących poleceń cmdlet w [PSDesiredStateConfiguration](https://technet.microsoft.com/library/dn391651(v=wps.640).aspx) modułu

    -   [Get-DscResource](http://technet.microsoft.com/library/dn521625.aspx) jest szybsze (szczególnie w ISE).

    -   [Początek DscConfiguration](http://technet.microsoft.com/library/dn521623.aspx) ma nowy parametr - UseExisting, który spowoduje ponowne zastosowanie ostatniej konfiguracji zastosowane.

    -   [Start-DscConfiguration](http://technet.microsoft.com/library/dn521623.aspx) -Force został rozwiązany.

    -   [Get-DscLocalConfigurationManager](http://technet.microsoft.com/library/dn407378.aspx) Wyświetla bardziej użyteczne informacje o stanie aparatu.

    -   [Test DscConfiguration](http://technet.microsoft.com/library/dn407382.aspx) teraz zwraca nazwę komputera oraz wartość PRAWDA lub FAŁSZ.

    -   [Nowy DscChecksum](http://technet.microsoft.com/library/dn521622.aspx) obsługuje teraz ścieżki UNC.

- Nowe polecenia cmdlet w [PSDesiredStateConfiguration](http://technet.microsoft.com/library/dn391651(v=wps.640).aspx) modułu

    -   [Aktualizacja DscConfiguration](http://technet.microsoft.com/library/mt143541(v=wps.630).aspx): sprawdza serwera na żądanie ściągnięcia.

    -   [Stop-DscConfiguration](http://technet.microsoft.com/library/mt143542(v=wps.630).aspx): Zatrzymuje konfiguracji, która jest już uruchomiona.

    -   [Usuń DscConfigurationDocument](http://technet.microsoft.com/library/mt143544(v=wps.630).aspx): umożliwia usuwanie dokumentów konfiguracji poszczególnych etapów (oczekujące, poprzednie lub bieżący).

- Funkcje języka

    -   DependsOn obsługuje teraz złożonego zasobów.

    -   DependsOn obsługuje teraz liczb w polu nazwy wystąpienia zasobu.

    -   Wyrażenia węzła, których ocena ma pusty już generują błędy.

    -   Błąd występuje, jeśli węzeł wyrażenie pustą został rozwiązany.

    -   Konfiguracje wywoływania pracy teraz konfiguracje w konsoli środowiska Windows PowerShell.

- Ulepszenia trybu ściągania

    -   Tryb ściągnięcia obsługuje teraz wszystkie pliki ZIP.

    -   **AllowModuleOverwrite** teraz działa prawidłowo.

- Ulepszenia odporności

    -   Nowy **DebugMode** umożliwia ponowne ładowanie modułów zasobów.

    -   W przypadku niepowodzenia konfiguracji plik pending.mof nie został usunięty.

    -   Lokalnego Menedżera konfiguracji (LCM) jest teraz bardziej elastyczne, w przypadku ustawienia metakonfigurację są uszkodzone.

- Ulepszenia diagnostycznych

    -   Ostrzeżenie jest wyświetlane, gdy LCM ustawia czasomierz inne ustawienia niż określono.

    -   Pliki dziennika błędów zawierają teraz stosu wywołań zasobów programu Windows PowerShell.

- Ulepszenia elastyczność

    -   Zasób LocalConfigurationManager ma nową właściwość **ActionAfterReboot**.

        -   ContinueConfiguration (wartość domyślna): automatycznie wznawia konfiguracji po ponownym uruchomieniu węzła docelowego.

        -   StopConfiguration: Nie automatycznie wznowić konfiguracji po ponownym uruchomieniu węzła.

    -   Uruchom spójności może teraz częściej niż operacji ŚCIĄGANIA lub na odwrót.

    -   Obsługa wersji: DSC teraz może rozpoznać dokument, który został wygenerowany na kliencie nowszej (dołączonego [WMF 5.0](http://aka.ms/wmf5download)).

- Ulepszenia zapobiegania błąd

    -   Obecnie jest wymuszany wersji modułu, przed zastosowaniem konfiguracji.

    -   **DebugPreference** jest teraz prawidłowo dla Get, Set- lub wywołania TargetResource testu.

- Obsługa ulepszenia poświadczeń

    -   Certyfikat jest używany teraz, jeśli obie **certyfikatu** i **PSDscAllowPlainTextPassword** zostały określone.

    -   Poświadczenia są odszyfrowywane, nawet w przypadku Get TargetResource.

    -   Metakonfigurację poświadczenia są szyfrowane i odszyfrowywane.

    -   PSCredentials teraz są odszyfrowywane, gdy są one osadzonego obiektu.

- Ulepszenia wbudowanych zasobów

    -   Zasób pakietu

        -   Nie instaluje pakietu niewłaściwy (albo z lokalnej lub sieci web źródła).

        -   Teraz obsługuje protokół HTTPS.

    -   Jest teraz obsługiwane dla protokołu HTTPS w [pakietu zasobów](http://technet.microsoft.com/library/dn282132.aspx).

    -   [Archiwum zasobów](http://technet.microsoft.com/library/dn249917.aspx) obsługuje teraz poświadczeń.

## <a name="new-features-in-windows-powershell-50"></a>Nowe funkcje programu Windows PowerShell 5.0

- [Nowe funkcje w programie Windows PowerShell](#new-features-in-windows-powershell)
- [Nowe funkcje w konfiguracji żądanego stanu programu Windows PowerShell](#new-features-in-windows-powershell-desired-state-configuration)
- [Nowe funkcje programu Windows PowerShell ISE](#new-features-in-windows-powershell-ise)
- [Nowe funkcje usług sieci Web programu Windows PowerShell](#new-features-in-windows-powershell-web-services-management-odata-iis-extension)
- [Ważne poprawki w programie Windows PowerShell 5.0](#notable-bug-fixes-in-windows-powershell-50)

### <a name="new-features-in-windows-powershell"></a>Nowe funkcje w programie Windows PowerShell

- Począwszy od programu Windows PowerShell 5.0, można tworzyć przy użyciu klasy, przy użyciu składni formalnego i semantyki są podobne do innych zorientowane obiektowo języków programowania. **Klasa**, **wyliczenia**, oraz innych słów kluczowych zostały dodane do języka programu Windows PowerShell do obsługi nowej funkcji. Aby uzyskać więcej informacji na temat pracy z klasami Zobacz about_Classes.

- Windows PowerShell 5.0 wprowadzono nowe informacje strukturalnych strumień, który służy do przesyłania danych strukturalnych między skrypt i jego obiektów wywołujących (lub środowisko macierzyste). Write-Host umożliwia teraz Emituj dane wyjściowe do strumienia informacji. Strumienie informacji również działać PowerShell.Streams, zadań, zaplanowanych zadań i przepływów pracy. Następujące funkcje obsługi strumienia informacji.

    -   Nowe informacje zapisu polecenie cmdlet pozwala określić, jak środowiska Windows PowerShell obsługuje informacji strumienia danych dla polecenia. Write-Host jest otoką informacji zapisu. Działania przepływu pracy obsługiwane są także informacje zapisu.

    -   Dwa nowe parametry wspólne, InformationVariable i InformationAction, umożliwiają określają sposób wyświetlania informacji strumieni polecenia. Prawidłowe wartości InformationAction to SilentlyContinue, Stop, Kontynuuj, Inquire, Ignoruj lub zawieszenia z SilentlyContinue jest wartość domyślna. InformationVariable Określa ciąg, jako nazwę zmiennej, do której ma zostać polecenia zapisane dane Write-Host.

    -   Nową zmienną preferencji InformationPreference, określa preferencje domyślne informacje strumienia danych w sesji programu Windows PowerShell. Wartość domyślna to SilentlyContinue.

    -   Dodano dwa nowe wspólnych parametrów przepływów pracy, PSInformation i InformationAction.

    -   Polecenie Format-Table kolumn tabeli teraz są automatycznie formatowane przez obliczania pierwszego 300ms danych, który przechodzi przez strumień.

- We współpracy z [Microsoft Research](http://research.microsoft.com/), dodano nowe polecenie cmdlet ConvertFrom ciągu. Ciąg ConvertFrom pozwala wyodrębnić i analizować strukturalnych obiektów z zawartości ciągów tekstowych. Aby uzyskać więcej informacji zobacz ConvertFrom ciągu.

- Nowe polecenie cmdlet przekonwertować ciągu automatycznie formatuje oparte na przykład podaj parametr - przykładowy tekst.

- Nowy moduł, Microsoft.PowerShell.Archive, zawiera polecenia cmdlet, które umożliwiają Kompresuj pliki i foldery w plikach archiwum (określane również jako ZIP), Wyodrębnij pliki z istniejących plików ZIP i aktualizować pliki ZIP z nowszymi wersjami pliki skompresowane w nich.

- Nowy moduł, PackageManagement, umożliwia wykrywanie i zainstaluj pakiety oprogramowania w Internecie. Moduł PackageManagement (wcześniej znane jako OneGet) jest multiplekser istniejących menedżerów pakietu (nazywanych również dostawców pakietu) lub Menedżera ujednolicenie zarządzania pakietu Windows za pomocą jednego interfejsu programu Windows PowerShell.

- Nowy moduł, PowerShellGet, pozwala znaleźć, instalowanie, publikowanie oraz aktualizowanie moduły i DSC zasobów na [galerii programu PowerShell](http://www.powershellgallery.com/), lub repozytorium modułu wewnętrznego, które można skonfigurować przy użyciu polecenia cmdlet Register-PSRepository.

- Nowe słowo kluczowe języka **Hidden**, został dodany do określenia członka (właściwości lub metody) nie jest wyświetlany domyślnie w wynikach elementu członkowskiego Get (chyba że dodasz parametru - Force). Właściwości lub metody, które zostały oznaczone jako ukryte również nie są wyświetlane w wynikach IntelliSense, chyba że znajdują się w kontekście, w którym powinny być widoczne; element członkowski na przykład automatyczne $ zmiennej to powinny wskazywać ukrytych elementów członkowskich w przypadku metody klasy.

- Nowy element, Usuń element i Get-ChildItem zostały rozszerzone i obsługuje tworzenie i zarządzanie nim [łącza symbolicznego](http://en.wikipedia.org/wiki/Symbolic_link). **- ItemType** parametrem elementu nowy akceptuje nową wartość **SymbolicLink**. Teraz można tworzyć łącza symbolicznego w jednym wierszu, uruchamiając polecenie cmdlet New-Item.

- Get-ChildItem ma również new - głębokość parametr, który umożliwia z parametrem - Recurse limit rekursji. Na przykład Get-ChildItem-Recurse - 2 głębokość zwraca wyniki z bieżącym folderze wszystkich folderów podrzędnych w bieżącym folderze oraz wszystkich folderów w ramach elementu podrzędnego folderów.

- Teraz umożliwiają kopiujesz pliki lub foldery z jedną sesję programu Windows PowerShell do innego, co oznacza, że można kopiować pliki do sesji, które są podłączone do komputerów zdalnych, copy-Item (łącznie z komputerów z systemem [Nano Server](http://blogs.technet.com/b/windowsserver/archive/2015/04/08/microsoft-announces-nano-server-for-modern-apps-and-cloud.aspx), i zatem mieć interfejs nie). Do kopiowania plików, podaj identyfikatory PSSession jako wartość nowe parametry - FromSession i - ToSession, a następnie dodaj - ścieżka - i docelowym, aby określić ścieżkę źródła i docelowym, odpowiednio. Na przykład Copy-Item-c: ścieżki\\mojplik.txt - ToSession $s — d: docelowego\\destinationFolder.

- Udoskonalono przekształcania środowiska Windows PowerShell do zastosowania do wszystkich aplikacji hostingu (na przykład programu Windows PowerShell ISE) oprócz host konsoli (**powershell.exe**). Można skonfigurować opcje zapisu (m.in. Włączanie zapis całego systemu), należy włączyć **włączyć przekształcania PowerShell** znaleziono szablonów/Windows w administracyjne składniki/Windows ustawienia zasad grupy Środowiska PowerShell.

- Nowa funkcja śledzenia szczegółowy skrypt umożliwia szczegółowe śledzenie i analizy użycia skryptów środowiska Windows PowerShell w systemie. Po włączeniu śledzenia szczegółowy skrypt programu Windows PowerShell dzienników wszystkich blokach skryptu w dzienniku zdarzeń śledzenia zdarzeń systemu Windows (ETW) **Microsoft-Windows-PowerShell/Operational**.

- Począwszy od programu Windows PowerShell 5.0 nowe polecenia cmdlet składni wiadomości kryptograficznych obsługują szyfrowanie i odszyfrowywanie zawartości przy użyciu standardowego formatu IETF kryptograficznie ochrony wiadomości w [RFC5652](http://tools.ietf.org/html/rfc5652). Polecenia cmdlet Get-CmsMessage, Chroń CmsMessage i Unprotect-CmsMessage zostały dodane do [Microsoft.PowerShell.Security](http://technet.microsoft.com/library/hh849807.aspx) modułu.

- Nowe polecenia cmdlet w [Microsoft.PowerShell.Utility](http://technet.microsoft.com/library/hh849958.aspx) modułu, obszaru działania Get obszaru działania debugowania, Get-RunspaceDebug, RunspaceDebug Włącz i Wyłącz-RunspaceDebug pozwalają na ustawienie opcji debugowania na obszarów działania i rozpoczęcie i zakończenie debugowanie w obszarze działania. Debugowanie dowolnych obszarach działania "oznacza to, obszarach działania, które nie są obszaru działania domyślne dla konsoli programu Windows PowerShell lub w sesji programu Windows PowerShell ISE" "środowiska Windows PowerShell pozwala ustawić punkty przerwania w skrypcie i dodać punkty przerwania zatrzymać skrypt z uruchomione, dopóki nie można dołączyć debugera, aby debugować skrypt obszaru działania. Zagnieżdżone obsługę debugowania dla dowolnych obszarach działania dodano do debugera skryptów środowiska Windows PowerShell dla obszary działania.

- Dodano nowe polecenie cmdlet Format szesnastkowy [Microsoft.PowerShell.Utility](http://technet.microsoft.com/library/hh849958.aspx) modułu. Format szesnastkowy umożliwia wyświetlanie danych tekstowych lub binarnych w formacie szesnastkowym.

- Polecenia cmdlet Get-Schowka i Schowka zestawu zostały dodane do [Microsoft.PowerShell.Utility](http://technet.microsoft.com/library/hh849958.aspx) modułu; ich do jej obsługi ułatwiają transferem zawartości do i z sesji środowiska Windows PowerShell. Polecenia cmdlet Schowek obsługuje obrazów, plików audio listy plików i tekst.

- Dodano nowe polecenie cmdlet Clear-RecycleBin [Microsoft.PowerShell.Management](http://technet.microsoft.com/library/hh849827(v=wps.640).aspx) moduł; pustych elementów tego polecenia cmdlet, odtwarzanie Bin na dysku stałym, w tym zewnętrznych dysków. Domyślnie monit o potwierdzenie polecenia Clear-RecycleBin, ponieważ właściwość ConfirmImpact, polecenia cmdlet jest ustawiona na ConfirmImpact.High.

- Nowe polecenie cmdlet New-TemporaryFile umożliwia utworzenie pliku tymczasowego w ramach wykonywania skryptów. Domyślnie nowy plik tymczasowy zostanie utworzony w ```C:\Users\<user name>\AppData\Local\Temp```.

- Out-File, Dodaj zawartość i polecenia cmdlet Set-Content już nowy parametr - NoNewline, które pomija znakiem nowego wiersza po danych wyjściowych.

- Polecenia cmdlet New-Guid wykorzystuje klasy identyfikatora Guid programu .NET Framework do generowania identyfikatora GUID, przydatne podczas pisania skryptów lub zasobów usługi Konfiguracja DSC.

- Ponieważ informacje o wersji pliku mogą być mylące, szczególnie po pliku jest poprawkami, nowe właściwości skryptu FileVersionRaw i ProductVersionRaw są dostępne dla obiektów FileInfo. Na przykład można wykonać następujące polecenie, aby wyświetlić wartości tych właściwości powershell.exe, gdzie $pid zawiera identyfikator procesu uruchomionej sesji programu Windows PowerShell:  ```Get-Process -Id $pid -FileVersionInfo | Format-List *version* -Force```

- Nowe polecenia cmdlet Enter PSHostProcess i PSHostProcess zakończenia umożliwiają debugowania skryptów programu Windows PowerShell w procesach, które są oddzielne od bieżącego procesu uruchomionego w konsoli środowiska Windows PowerShell. Uruchom Enter-PSHostProcess do wprowadzania i dołączyć do Identyfikatora określonego procesu, a następnie uruchom obszaru działania Get do zwrócenia active obszarach działania w ramach procesu. Uruchom PSHostProcess zakończenia można odłączyć od procesu po zakończeniu debugowania skryptu w ramach procesu.

- Dodano nowe polecenie cmdlet debuger oczekiwania [Microsoft.PowerShell.Utility](http://technet.microsoft.com/library/hh849958.aspx) modułu. Można uruchomić debugera oczekiwania zatrzymać skrypt w debugerze Przed uruchomieniem następnej instrukcji w skrypcie.

- Debuger przepływu pracy środowiska Windows PowerShell obsługuje teraz wykonania polecenia lub kartę i można debugować funkcje zagnieżdżony przepływ pracy. Teraz możesz nacisnąć **klawisze Ctrl + Break** wprowadzenia debuger uruchamianie skryptu, sesje lokalnych i zdalnych i skrypt przepływu pracy.

- Polecenia cmdlet zadania debugowania został dodany do [Microsoft.PowerShell.Core](http://technet.microsoft.com/library/hh849695.aspx) modułu do debugowania uruchamianie skryptów zadania przepływu pracy środowiska Windows PowerShell, tła i zadania uruchomione w sesji zdalnej.

- Nowy stan AtBreakpoint, została dodana do zadań programu Windows PowerShell. Stan AtBreakpoint ma zastosowanie, gdy praca jest wykonywana skryptu, który zawiera Ustaw punkty przerwania, a skrypt został trafiony punkt przerwania. Gdy zadanie zostało zatrzymane w punkcie przerwania debugowania, musisz debugować zadania przy użyciu polecenia cmdlet zadania debugowania.

- Windows PowerShell 5.0 zapewnia obsługę wielu wersji pojedynczy moduł programu Windows PowerShell, w tym samym folderze, w $PSModulePath. Właściwość RequiredVersion została dodana do klasy ModuleSpecification, aby uzyskać odpowiednią wersję modułu; Ta właściwość jest wykluczają się wzajemnie z właściwością ModuleVersion. RequiredVersion jest teraz obsługiwana jako część wartości parametru element FullyQualifiedName polecenia Get-Module Import-Module i polecenia cmdlet Remove-modułu.

- Teraz można przeprowadzać sprawdzania poprawności wersji modułu przy użyciu polecenia cmdlet Test-ModuleManifest.

- Wyniki polecenia cmdlet Get-Command jest teraz wyświetlany kolumny wersji; nowe właściwości wersji dodano do klasy CommandInfo. Get-Command zawiera polecenia z różnymi wersjami tego samego modułu. Właściwość Version jest również częścią klas pochodnych CmdletInfo: CmdletInfo i ApplicationInfo.

- Get-Command ma nowy parametr - ShowCommandInfo, zwracająca informacji ShowCommand jako PSObjects. Jest to szczególnie przydatne funkcje Pokaż polecenia jest uruchamiania w środowisku Windows PowerShell ISE przy użyciu komunikacji zdalnej programu Windows PowerShell. Parametr - ShowCommandInfo zastępuje funkcję Get-SerializedCommand istniejących w Microsoft.PowerShell.Utility module, ale skryptu Get SerializedCommand jest nadal dostępny do obsługi skryptów niskiego poziomu.

- Nowe polecenie cmdlet Get-ItemPropertyValue pozwala uzyskać wartość właściwości bez używając zapisu kropkowego. Na przykład w starszych wersjach programu Windows PowerShell, można uruchomić następujące polecenie, aby pobrać wartości właściwości baza aplikacji klucza rejestru PowerShellEngine: **(Get-ItemProperty-HKLM ścieżki:\\oprogramowania\\ Microsoft\\PowerShell\\3\\PowerShellEngine-Name ApplicationBase). ApplicationBase**. Począwszy od programu Windows PowerShell 5.0, można uruchomić **Get ItemPropertyValue-HKLM ścieżki:\\oprogramowania\\Microsoft\\programu PowerShell\\3\\PowerShellEngine-ApplicationBase nazwy** .

- Konsola programu Windows PowerShell korzysta teraz kolorowania, tak jak w przypadku programu Windows PowerShell ISE.

- Nowy moduł NetworkSwitch zawiera polecenia cmdlet, które umożliwiają stosowanie przełącznika, wirtualnych sieci LAN (VLAN) i podstawowa konfiguracja portu przełącznika sieci warstwy 2 do przełączników sieciowych certyfikatem logo systemu Windows Server 2012 R2.

- Parametr element FullyQualifiedName dodano do polecenia cmdlet Import-Module i Usuń modułu, do obsługi, przechowywania wielu wersji pojedynczy moduł.

- Save-Help, Update-Help PSSession importu, eksportu-PSSession i Get-Command ma nowy parametr FullyQualifiedModule typu ModuleSpecification. Dodaj ten parametr, aby określić w pełni kwalifikowanej nazwy modułu.

- Wartość **$PSVersionTable.PSVersion** została zaktualizowana w celu 5.0.

### <a name="new-features-in-windows-powershell-desired-state-configuration"></a>Nowe funkcje w konfiguracji żądanego stanu programu Windows PowerShell

- Funkcje języka programu Windows PowerShell umożliwiają definiowanie zasobów systemu Windows PowerShell Desired stan konfiguracji (DSC) przy użyciu klasy. DscResource importowania jest teraz true słowa kluczowego dynamicznych. Określony moduł analizuje środowiska Windows PowerShell "™ modułu głównego s, wyszukiwanie dla klas, które zawierają atrybut DscResource. Klasy można teraz używać do definiowania DSC zasobów, w których nie jest wymagany plik MOF ani DSCResource podfolderu w folderze modułu. Plik modułu programu Windows PowerShell może zawierać wielu klas zasobów usługi Konfiguracja DSC.

- Nowy parametr ThrottleLimit, dodano do następujących poleceń cmdlet w PSDesiredStateConfiguration module. Dodaj parametr ThrottleLimit, aby określić liczbę komputerów docelowych lub urządzeń, na których mają polecenia do pracy w tym samym czasie.

    -   Get-DscConfiguration

    -   Get-DscConfigurationStatus

    -   Get-DscLocalConfigurationManager

    -   Przywracanie DscConfiguration

    -   DscConfiguration testu

    -   Porównaj DscConfiguration

    -   Publikowanie DscConfiguration

    -   Zestaw DscLocalConfigurationManager

    -   Start DscConfiguration

    -   DscConfiguration aktualizacji

- Z scentralizowane DSC raportowanie błędów, informacje o błędzie sformatowanego jest nie tylko rejestrowane w przypadku dziennika, ale mogą być wysyłane do centralnej lokalizacji w celu późniejszej analizy. Do przechowywania błędy konfiguracji DSC, które wystąpiły na każdym serwerze w środowisku, można użyć tej centralnej lokalizacji. Po serwera raportów jest zdefiniowany w konfiguracji meta, wszystkie błędy są wysyłane do serwera raportów i następnie przechowywane w bazie danych. Można skonfigurować tę funkcję, niezależnie od tego, czy węzeł docelowy jest skonfigurowany do ściągania konfiguracje z serwera ściągania.

- Ulepszenia dotyczące programu Windows PowerShell ISE ułatwiają tworzenie zasobu usługi Konfiguracja DSC. Można teraz wykonać następujące czynności.

    -   Wyświetl listę wszystkich zasobów DSC w **konfiguracji** lub **węzła** bloku, wprowadzając **klawisze Ctrl + spacja** w pustym wierszu w bloku.

    -   Automatyczne uzupełnianie dla właściwości zasobów **wyliczenie** typu.

    -   Automatyczne uzupełnianie na **DependsOn** właściwości zasobów DSC, w oparciu o inne wystąpienia zasobu w konfiguracji.

    -   Ulepszone kartę ukończenia wartości właściwości zasobów.

- Użytkownik może teraz uruchomić zasób w określonym zestawie poświadczeń przez dodanie **PSDscRunAsCredential** atrybutu blok węzła. Na przykład PSDscRunAsCredential = Get-Credential Contoso\\DscUser. Ta funkcja jest przydatna przy tworzeniu konfiguracji, które uruchomienia Instalatora systemu Windows i instalatorów pliku wykonywalnego, dostęp do gałęzi rejestru dla poszczególnych użytkowników lub wykonywać inne zadania poza bieżącego kontekstu użytkownika.

- Dodano obsługę (w oparciu o x86) 32-bitowego dla **konfiguracji** — słowo kluczowe.

- Program Windows PowerShell zawiera teraz obsługę niestandardowych pomocy w przypadku konfiguracji DSC zdefiniowany przez dodanie \[CmdletBinding()] funkcji wygenerowanego konfiguracji.

- Nowy **DscLocalConfigurationManager** atrybut określa blok konfiguracji jako meta konfigurację, która służy do konfiguracji DSC lokalny program Configuration Manager. Ten atrybut ogranicza konfiguracji zawierającego tylko elementy, co powoduje ich skonfigurowanie DSC lokalny program Configuration Manager. Podczas przetwarzania tej konfiguracji generuje \*. meta.mof pliku, który jest następnie wysyłana do węzłów odpowiednich docelowych przy użyciu polecenia cmdlet Set-DscLocalConfigurationManager.

- Konfiguracje z częściowa teraz są dozwolone w programie Windows PowerShell 5.0. Konfiguracja dokumentów można dostarczyć do węzła w fragmenty. Dla węzła do odbierania wielu fragmentów dokumentu konfiguracji, węzeł "™ s lokalny program Configuration Manager należy najpierw ustawić do określenia oczekiwanych fragmentów

- Synchronizacja między komputerami stanowi nowość w DSC w programie Windows PowerShell 5.0. Za pomocą wbudowanych WaitFor\* zasobów (**WaitForAll**, **WaitForAny**, i **WaitForSome**), można teraz określić zależności na komputerach podczas konfiguracji jest uruchamiana, bez orchestrations zewnętrznych. Te zasoby zawierają węzła do węzła synchronizacji przy użyciu połączeń modelu wspólnych informacji za pomocą protokołu WS-Man. Konfiguracja poczekać na inny komputer "™ zmianę stanu określonego zasobu s.

- Tylko wystarczająco administracyjnej (JEA), funkcją zabezpieczeń delegowania, wykorzystanie DSC i środowiska Windows PowerShell ograniczone obszary działania ułatwiające bezpieczne przedsiębiorstwa przed utratą danych lub naruszenie przez pracowników, czy zamierzone lub przypadkowe. Aby uzyskać więcej informacji o JEA, w której można pobrać zasobu xJEA DSC, w tym temacie [tylko tyle administracji, krok po kroku](http://blogs.technet.com/b/privatecloud/archive/2014/05/14/just-enough-administration-step-by-step.aspx).

- W PSDesiredStateConfiguration module zostały dodane następujące nowe polecenia cmdlet.

    -   Nowe polecenie cmdlet Get-DscConfigurationStatus pobiera informacje wysokiego poziomu o stan konfiguracji z węzła docelowego. Można uzyskać stanu ostatniego lub wszystkie konfiguracje.

    -   Nowe polecenie cmdlet Porównaj DscConfiguration porównuje określonej konfiguracji z faktycznym stanem co najmniej jeden węzeł docelowy.

    -   Nowe polecenie cmdlet Publish-DscConfiguration kopiuje plik MOF konfiguracji do węzła docelowego, ale nie ma zastosowania konfiguracji. Konfiguracja zostanie zastosowana podczas przebiegu spójności dalej lub po uruchomieniu polecenia cmdlet DscConfiguration aktualizacji.

    -   Nowe polecenie cmdlet Test-DscConfiguration pozwala sprawdzić, czy otrzymana Konfiguracja zgodna wymaganą konfiguracją, zwraca wartość PRAWDA, jeśli konfiguracja pasuje wymaganą konfigurację, lub FAŁSZ, gdy rzeczywista konfiguracja nie jest zgodna żądaną Konfiguracja.

    -   Nowe polecenie cmdlet Update-DscConfiguration wymusza konfigurację do przetworzenia. Jeśli lokalny program Configuration Manager jest w trybie ściągania, polecenie cmdlet pobiera przed zastosowaniem konfiguracji z serwera ściągania.

### <a name="new-features-in-windows-powershell-ise"></a>Nowe funkcje programu Windows PowerShell ISE

- Zdalnego skryptów programu Windows PowerShell i pliki w lokalną kopię programu Windows PowerShell ISE można teraz edytować, uruchamiając Enter-PSSession, aby rozpocząć sesję zdalnego na komputerze, który "™ s przechowywania plików, który chcesz edytować, a następnie uruchomienia **PSEdit <path and file name on the remote computer>**. Funkcja ta ułatwia edycji plików programu Windows PowerShell, które są przechowywane w opcji instalacji Server Core systemu Windows Server, których nie można uruchomić programu Windows PowerShell ISE.

- Polecenie cmdlet Start-zapis jest teraz obsługiwana w środowisku Windows PowerShell ISE.

- Teraz można debugować zdalnego skryptów w środowisku Windows PowerShell ISE.

- Nowe polecenie menu, **Przerwij wszystkie** (Ctrl + B) przechodzi do debugera lokalne i zdalne uruchamianie skryptów.

### <a name="new-features-in-windows-powershell-web-services-management-odata-iis-extension"></a>Nowe funkcje w usługach sieci Web systemu Windows PowerShell (rozszerzenie usług IIS OData zarządzania)

- Począwszy od programu Windows PowerShell 5.0, można wygenerować zestaw poleceń cmdlet Windows PowerShell, w oparciu o funkcje udostępniane przez dany punkt końcowy OData, uruchamiając polecenie cmdlet Export-ODataEndpointProxy znaleziono w nowym [ Microsoft.PowerShell.OdataUtils](http://technet.microsoft.com/library/dn818507(v=wps.640).aspx) modułu.

### <a name="notable-bug-fixes-in-windows-powershell-50"></a>Ważne poprawki w programie Windows PowerShell 5.0

- Windows PowerShell 5.0 zawiera nową implementacją COM, który zapewnia znaczną poprawę wydajności podczas pracy z obiektami COM. Aby wideo demonstracyjne efektu, zobacz [Com_Perf_Improvements](http://1drv.ms/1qu3UPZ).

- Znaczący wzrost wydajności zostały wprowadzone do pierwszego wykonania kartę w sesji środowiska Windows PowerShell, skrócić czas ukończenia kartę przez prawie 500 ms.

## <a name="new-features-in-windows-powershell-40"></a>Nowe funkcje programu Windows PowerShell 4.0
Windows PowerShell 4.0 jest zgodny z poprzednimi wersjami. Polecenia cmdlet, dostawców modułów, przystawki, skrypty, funkcje i profile, które zostały zaprojektowane dla programu Windows PowerShell 3.0 i Windows PowerShell 2.0 działa w programie Windows PowerShell 4.0 bez zmian.

Windows PowerShell 4.0 jest instalowana domyślnie na Windows 8.1 i Windows Server 2012 R2. Aby zainstalować program Windows PowerShell 4.0 w systemie Windows 7 z dodatkiem SP1 lub Windows Server 2008 R2, Pobierz i zainstaluj [Windows Management Framework 4.0](http://www.microsoft.com/download/details.aspx?id=40855). Pamiętaj odczytać szczegółów pobierania i spełnia wszystkie wymagania systemowe, przed zainstalowaniem systemu Windows Management Framework 4.0.

- [Nowe funkcje w programie Windows PowerShell](#new-features-in-windows-powershell-1)
- [Nowe funkcje w Windows PowerShell Integrated Scripting Environment (ISE)](#new-features-in-windows-powershell-integrated-scripting-environment-ise)
- [Nowe funkcje w przepływie pracy programu Windows PowerShell](#new-features-in-windows-powershell-workflow)
- [Nowe funkcje usług sieci Web programu Windows PowerShell](#new-features-in-windows-powershell-web-services)
- [Nowe funkcje programu Windows PowerShell Web Access](#new-features-in-windows-powershell-web-access)
- [Ważne poprawki w programie Windows PowerShell 4.0](#notable-bug-fixes-in-windows-powershell-40)

Windows PowerShell 4.0 obejmuje następujące nowe funkcje.

### <a name="new-features-in-windows-powershell"></a>Nowe funkcje w programie Windows PowerShell

- **Konfiguracja żądanego stanu programu Windows PowerShell** (DSC) jest systemem zarządzania w programie Windows PowerShell 4.0, która umożliwia wdrażanie i zarządzanie danych konfiguracji usług oprogramowania i środowisko, w którym są uruchomione następujące usługi. Aby uzyskać więcej informacji o konfiguracji DSC, zobacz [wprowadzenie do konfiguracji żądanego stanu programu Windows PowerShell](https://technet.microsoft.com/library/c134aa32-b085-4656-9a89-955d8ff768d0).

- **Save-Help** teraz umożliwia zapisywanie pomocy dla modułów, które są zainstalowane na komputerach zdalnych. Save-Help służy do pobierania modułu pomocy z podłączonej do Internetu (na którym nie wszystkie moduły, dla których ma dotyczyć pomoc są zawsze zainstalowanego klienta), a następnie skopiuj zapisane ułatwiają zdalny folder udostępniony lub komputerze zdalnym, który nie ma Internet dostęp.

- Debuger programu Windows PowerShell została rozszerzona w celu zezwolenia na debugowanie przepływów pracy programu Windows PowerShell, a także skrypty, które są uruchomione na komputerach zdalnych. Przepływy pracy programu Windows PowerShell może być debugowany teraz na poziomie skryptu z wiersza polecenia programu Windows PowerShell lub programu Windows PowerShell ISE. Skrypty programu Windows PowerShell, w tym skryptowych przepływów pracy, może być debugowany teraz sesji zdalnej. Sesje debugowania zdalnego zostaną zachowane w sesji zdalnej programu Windows PowerShell, które odłączony i później ponownie.

- A **RunNow** parametr **Register-ScheduledJob** i **Set-ScheduledJob** eliminuje potrzebę ustawienia natychmiastowego datę i godzinę rozpoczęcia zadań za pomocą **Wyzwalacz** parametru.

- **Invoke-RestMethod** i **Invoke WebRequest** teraz pozwalają na ustawienie wszystkich nagłówków przy użyciu parametru nagłówków. Mimo że zawsze zarania tego parametru, został jeden z kilku parametrów dla polecenia cmdlet w sieci web, które spowodowały wyjątkami lub błędami.

- **Get-Module** ma nowy parametr **element FullyQualifiedName**, typu **ModuleSpecification\[]**. **Element FullyQualifiedName** parametr Get-Module teraz pozwala określić moduł przy użyciu modułu nazwę, wersję i opcjonalnie jego identyfikator GUID.

- Domyślne ustawienie zasad wykonywania w systemie Windows Server 2012 R2 to **RemoteSigned**. Na Windows 8.1 nie została zmieniona w domyślnym ustawieniem.

- Począwszy od programu Windows PowerShell 4.0, wywołanie metody przy użyciu nazwy metod dynamicznych jest obsługiwana. Można użyć zmiennej, aby zapisać nazwę metody, a następnie dynamicznie wywołać metody po wywołaniu zmiennej.

- Zadania asynchronicznego przepływu pracy nie są już usuwane po upływie limitu czasu, który jest określony przez **PSElapsedTimeoutSec** upłynął typowego parametru przepływu pracy.

- Nowy parametr **RepeatIndefinitely**, został dodany do **New-JobTrigger** i **Set-JobTrigger** polecenia cmdlet. Eliminuje to konieczność określania **TimeSpan.MaxValue** wartość **RepetitionDuration** parametr, aby uruchomić zaplanowanego zadania wielokrotnie nieokreślony.

- A **Passthru** parametr został dodany do **Enable-JobTrigger** i **Disable-JobTrigger** polecenia cmdlet. Parametru Passthru Wyświetla wszystkie obiekty, które są tworzone lub modyfikowane przez polecenie.

- Nazwy parametrów służącą do grupy roboczej w **Add-Computer** i **Remove-Computer** poleceń cmdlet, teraz są spójne. Oba polecenia cmdlet używają teraz parametr **Nazwa_grupy_roboczej**.

- Nowy parametr wspólnej **PipelineVariable**, został dodany. PipelineVariable umożliwia zapisywanie wyników polecenia gazociągami (lub część polecenia gazociągami) jako zmienną, które mogą być przekazywane do pozostałej części potoku.

- Filtrowanie przy użyciu składni metody kolekcji jest teraz obsługiwane. Oznacza to, że kolekcję obiektów obecnie można filtrować przy użyciu składni uproszczoną, podobnie jak w przypadku Where() lub Where-Object, sformatowane jako wywołanie metody. Przykład: .where (Get-Process) ({$_. Nazwa — odpowiada "powershell"})

- **Get-Process** polecenie cmdlet ma nowy parametr przełącznika **IncludeUserName**.

- Nowe polecenie cmdlet **Get-FileHash**, która zwraca wartość skrótu pliku w jednym z kilku formatów dla określonego pliku, został dodany.

- W programu Windows PowerShell 4.0, jeśli korzysta z modułu **DefaultCommandPrefix** klucza w swoim manifeście lub jeśli użytkownik importuje moduł o **prefiksu** parametru **ExportedCommands**właściwość modułu zawiera poleceń w module z prefiksem. Po uruchomieniu polecenia przy użyciu składni kwalifikowanej Nazwa_modułu\\CommandName, nazwy polecenia muszą zawierać prefiks.

- Wartość **$PSVersionTable.PSVersion** została zaktualizowana w celu 4.0.

- **WHERE()** zachowanie operator został zmieniony. `Collection.Where('property -match name')` akceptowanie wyrażenia ciągu w formacie `"Property -CompareOperator Value"` nie jest już obsługiwana. Jednak **Where()** operator akceptuje wyrażenie ciągu w formacie scriptblock; nadal jest to obsługiwane.

### <a name="new-features-in-windows-powershell-integrated-scripting-environment-ise"></a>Nowe funkcje w Windows PowerShell Integrated Scripting Environment (ISE)

- Windows PowerShell ISE obsługuje debugowanie przepływu pracy środowiska Windows PowerShell i zdalne debugowanie skryptu.

- Dodano obsługę funkcji IntelliSense dla dostawcy konfiguracji żądanego stanu programu Windows PowerShell i konfiguracji.

### <a name="new-features-in-windows-powershell-workflow"></a>Nowe funkcje w przepływie pracy programu Windows PowerShell

- Dodano obsługę nowej **PipelineVariable** wspólnego parametru w kontekście potoki iteracyjną, takich jak zasoby używane przez System Center Orchestrator; oznacza to, że Uruchom polecenia po prostu od lewej do prawej, w przeciwieństwie do potoków przeplatane uruchomiony przy użyciu przesyłania strumieniowego.

- Wiązanie parametru został znacząco udoskonalony w celu pracy poza kartę ukończenia scenariuszy, takich jak z poleceniami, które nie istnieją w bieżącym obszarze działania.

- Dodano obsługę dla kontenera niestandardowych działań do przepływu pracy programu Windows PowerShell. Jeśli parametr działania jest typów **działania**, **działania\[]**""lub jest ogólny zbiór działań "i podanego przez użytkownika blok skryptu jako argument, a następnie systemu Windows Przepływ pracy programu PowerShell konwertuje bloku skryptu w języku XAML, podobnie jak w przypadku normalnych kompilacji skrypt do przepływu pracy programu Windows PowerShell.

- Po awarii Windows PowerShell Workflow automatycznie ponownie nawiąże połączenie z węzłów zarządzanych.

- Teraz możesz ograniczyć **Foreach-Parallel** instrukcje działania za pomocą **ThrottleLimit** właściwości.

- **ErrorAction** typowy parametr ma wartość prawidłowe nowe **zawieszenia**, która jest wyłącznie dla przepływów pracy.

- Punkt końcowy przepływu pracy teraz automatycznie zamyka, jeśli istnieją nie aktywne sesje, żadne zadania w toku i żadne oczekujące zadania. Ta funkcja oszczędza zasobów na komputerze, na którym działa jak serwer przepływu pracy, po spełnieniu warunków automatycznego zamknięcia.

### <a name="new-features-in-windows-powershell-web-services"></a>Nowe funkcje usług sieci Web programu Windows PowerShell

- W programie Windows PowerShell Web Services (PSWS, również o nazwie OData IIS rozszerzenie zarządzania), podczas gdy wystąpi błąd polecenia cmdlet jest uruchomiona, bardziej szczegółowe informacje o błędzie komunikaty są zwracane do obiektu wywołującego. Ponadto należy wykonać kody błędów [wytyczne kodu błędu interfejsu API REST Azure z systemem Windows](http://msdn.microsoft.com/library/windowsazure/dd179357.aspx).

- Punkt końcowy można teraz określić wersję interfejsu API, a także wymusić użycie określonej wersji interfejsu API. Zawsze, gdy występuje niezgodność wersji między klientem a serwerem, błędy są wyświetlane zarówno klient, jak i serwera.

- Zarządzanie schematem wysyłania uproszczonej przez automatyczne generowanie wartości brakujące pola w schemacie. Generowanie występuje, jako punktu wyjścia przydatne, nawet jeśli schemat wysyłania nie istnieje.

- Typem obsługi w PSWS została zwiększona do obsługi typów, które działa podobnie do za pomocą konstruktora innego niż Konstruktor domyślny **PSTypeConverter** w programie Windows PowerShell. Dzięki temu można korzystać z PSWS tych typów złożonych.

- Teraz PSWS umożliwia rozwijanie skojarzonego wystąpienia podczas wykonywania zapytania. Dla większych binarny zawartości (np. obrazów, audio i wideo) koszt przeniesienia jest ważna, a lepiej transferu danych binarnych bez kodowania. PSWS używa zasobów o nazwie strumienie przesyłania bez kodowania. Strumień zasobu o nazwie jest właściwością jednostki **Edm.Stream** typu. Każdego strumienia zasobu o nazwie ma oddzielne identyfikator URI dla operacji GET lub aktualizacji.

- Akcji OData teraz mechanizm umożliwiający wywoływanie metod (tworzenia, odczytu, aktualizacji i usuwania) z systemem innym niż CRUD na zasobie. Akcji mogą być wywoływane przez wysłanie żądania POST protokołu HTTP do identyfikatora URI, który jest zdefiniowany dla akcji. Parametry działania są definiowane w treści żądania POST.

- Być zgodne z wytycznymi systemu Windows Azure, należy uprościć wszystkie adresy URL. Zmiany zawarte w **klucz jako Segment** umożliwia pojedynczego kluczy może być reprezentowana jako segmentów. Należy pamiętać, że odwołania, które używają wielu wartości klucza wymaga wartości rozdzielanych przecinkami w nawiasach notacji jak poprzednio.

- Przed tej wersji PSWS tylko sposób wykonania utworzenia, aktualizacji lub usuwania operacji został wywołania Post, Put, lub usuwanie zasobu najwyższego poziomu. Nowe w tej wersji PSWS zasobów zawartych działań umożliwiają użytkownikom osiągnięcia takie same wyniki podczas nawiązywania połączenia tego samego zasobu mniej bezpośrednio zbliża się tak, jakby były zawarte w tych zasobów.

### <a name="new-features-in-windows-powershell-web-access"></a>Nowe funkcje programu Windows PowerShell Web Access

- Można odłączyć i ponownie połączyć się z istniejącej sesji w konsoli internetowej programu Windows PowerShell Web Access. A **zapisać** przycisk w konsoli sieci web umożliwia rozłączyć sesję bez usuwania go i ponownie połączyć się z sesją innego czasu.

- Domyślne parametry mogą być wyświetlane na stronie logowania. Aby wyświetlić parametry domyślne, należy skonfigurować wszystkie ustawienia wyświetlane w wartości **opcjonalne ustawienia połączenia** obszar strony logowania w pliku o nazwie **web.config**. Można użyć **web.config** plik do skonfigurowania wszystkich opcjonalne ustawienia połączenia z wyjątkiem drugi lub alternatywnego zestawu poświadczeń.

- W systemie Windows Server 2012 R2 można zdalnie zarządzać reguł autoryzacji dla programu Windows PowerShell Web Access. **Add-PswaAuthorizationRule** i **Test-PswaAuthorizationRule** polecenia cmdlet zawierają teraz parametr Credential, która umożliwia administratorom zarządzanie reguły autoryzacji z komputera zdalnego lub w Sesja programu Windows PowerShell Web Access.

- Istnieje już wiele sesji programu Windows PowerShell Web Access w pojedynczej sesji przeglądarki, za pomocą nowej karty przeglądarki dla każdej sesji. Nie trzeba otworzyć sesję przeglądarki do nawiązania połączenia w nowej sesji, w konsoli internetowej programu Windows PowerShell.

### <a name="notable-bug-fixes-in-windows-powershell-40"></a>Ważne poprawki w programie Windows PowerShell 4.0

- **Get-Counter** teraz przywrócić liczniki, które zawierają apostrof w francuskim wersji systemu Windows.

- Możesz teraz przeglądać **GetType** metody zdeserializowany obiektów.

- **#Requires** instrukcje umożliwiają teraz użytkownikom wymagane uprawnienia dostępu administratora, jeśli to konieczne.

- **Import Csv** polecenia cmdlet teraz ignoruje puste wiersze.

- Problem, na których programu Windows PowerShell ISE używa zbyt dużej ilości pamięci podczas uruchamiania **Invoke WebRequest** polecenia został rozwiązany.

- **Get-Module** są obecnie wyświetlane wersji modułu w **wersji** kolumny.

- Element Remove - Recurse teraz usuwa elementy z podfolderów, zgodnie z oczekiwaniami.

- A **UserName** właściwość została dodana do **Get-Process** output obiektów.

- **Invoke RestMethod** polecenie cmdlet zwraca teraz wszystkie dostępne wyniki.

- **Dodaj element członkowski** teraz zostaną uwzględnione w obiektach HashTable, nawet jeśli obiektach HashTable nie jeszcze uzyskano.

- **Select-Object - rozwiń** już nie powiedzie się lub generuje wyjątek, jeśli wartość właściwości jest zerowa lub pusta.

- **Get-Process** można teraz używać w potoku z innymi poleceniami, które pobierają **ComputerName** właściwości obiektów.

- **ConvertTo-Json** i **ConvertFrom Json** można teraz zaakceptuj postanowienia w podwójne cudzysłowy, a jego komunikaty o błędach są teraz lokalizowalny.

- **Get-Job** teraz zwraca żadnego ukończone zaplanowanych zadań, nawet w nowej sesji.

- Problemy z Instalowanie i odinstalowywanie dysków VHD za pomocą **FileSystem** Naprawiono dostawcy w programie Windows PowerShell 4.0. Programu Windows PowerShell jest teraz w stanie wykryć nowe dyski, gdy są one zainstalowane w tej samej sesji.

- Nie trzeba w sposób jawny załadować **ScheduledJob** lub **przepływu pracy** modułów do pracy z ich typy zadań.

- Wprowadzono ulepszenia wydajności procesu importowania przepływy pracy, które definiują zagnieżdżone przepływy pracy; Ten proces jest teraz szybsze.

## <a name="new-features-in-windows-powershell-30"></a>Nowe funkcje programu Windows PowerShell 3.0
Program Windows PowerShell 3.0 obejmuje następujące nowe funkcje.

- [Przepływ pracy programu Windows PowerShell](#windows-powershell-workflow)
- [Windows PowerShell Web Access](#windows-powershell-web-access)
- [Nowe funkcje programu PowerShell ISE systemu Windows](#new-windows-powershell-ise-features)
- [Obsługa programu Microsoft .NET Framework 4.0](#support-for-microsoft-net-framework-4)
- [Obsługa środowiska preinstalacji systemu Windows](#support-for-windows-preinstallation-environment)
- [Sesje rozłączone](#disconnected-sessions)
- [Sesja niezawodna łączności](#robust-session-connectivity)
- [System aktualizowalnej pomocy](#updatable-help-system)
- [Ulepszone pomocy Online](#enhanced-online-help)
- [Integracja modelu wspólnych informacji](#cim-integration)
- [Pliki konfiguracji sesji](#session-configuration-files)
- [Zaplanowane zadania i integracja z harmonogramu zadań](#scheduled-jobs-and-task-scheduler-integration)
- [Funkcje języka programu PowerShell systemu Windows](#windows-powershell-language-enhancements)
- [Nowe polecenia cmdlet Core](#new-core-cmdlets)
- [Ulepszenia istniejących podstawowych poleceń cmdlet i dostawców](#improvements-to-existing-core-cmdlets-and-providers)
- [Importuj moduł zdalnego i odnajdywania](#remote-module-import-and-discovery)
- [Uzupełnianie po naciśnięciu tabulatora rozszerzone](#enhanced-tab-completion)
- [Automatyczne ładowanie modułu](#module-auto-loading)
- [Ulepszenia obsługi modułu](#module-experience-improvements)
- [Polecenie uproszczony odnajdywania](#simplified-command-discovery)
- [Rejestrowanie udoskonalone, diagnostyki i obsługa zasad grupy](#improved-logging-diagnostics-and-group-policy-support)
- [Formatowanie i ulepszenia danych wyjściowych](#formatting-and-output-improvements)
- [Środowisko hosta rozszerzone konsoli](#enhanced-console-host-experience)
- [Nowe polecenia Cmdlet i hostingu API](#new-cmdlet-and-hosting-apis)
- [Ulepszenia wydajności](#performance-improvements)
- [Uruchom jako i obsługa hostów udostępnionego](#runas-and-shared-host-support)
- [Ulepszenia obsługi znaków specjalnych](#special-character-handling-improvements)

### <a name="windows-powershell-workflow"></a>Przepływ pracy programu Windows PowerShell
Przepływ pracy programu Windows PowerShell oferuje możliwości programu Windows Workflow Foundation programu Windows PowerShell. Możesz pisanie przepływów pracy w języku XAML, lub w języku środowiska Windows PowerShell i uruchom je tak samo, jak należy uruchomić polecenie cmdlet. [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) polecenie cmdlet pobiera poleceń workflw i [Get-Help](https://technet.microsoft.com/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) polecenie cmdlet pobiera tematy Pomocy dotyczące przepływów pracy.

Przepływy pracy są sekwencje zadań związanych z zarządzaniem multicomputer, które są długotrwałe, powtarzalne częste, działania równoległego, przerywania, suspendable i uruchamiać ponownie. Przepływy pracy mogą zostać wznowiony od przerwaniu zamierzone lub przypadkowe, na przykład awaria sieci, ponowne uruchomienie systemu Windows lub awarii zasilania.

Przepływy pracy są również przenośne; mogą być eksportowane jako lub importowane z plików XAML. Można pisać niestandardowe konfiguracje sesji umożliwiające przepływu pracy lub działania w przepływie pracy do uruchamiania przez użytkowników delegowanej lub podrzędnego.

Poniżej przedstawiono zalety przepływu pracy środowiska Windows PowerShell

- Automatyzacja zadań Sekwencyjna, długotrwałą.

- **Zdalne monitorowanie długotrwałych zadań**. Stan i postęp działań są widoczne w dowolnym momencie.

- **Multicomputer zarządzania.** Jednocześnie uruchamiać zadania jako przepływy pracy na tysięcy węzłów zarządzanych. Przepływ pracy programu Windows PowerShell zawiera wbudowaną bibliotekę wspólnych parametrów zarządzania, takich jak **PSComputerName**, umożliwiające zarządzanie wieloma komputerami scenariuszy.

- **Pojedyncze zadanie wykonywanie złożonych procesów.** Możesz łączyć pokrewne skrypty, które implementują cały scenariusz end-to-end w jednym przepływie pracy.

- **Trwałość.** : przepływ pracy jest zapisany (lub odnosi się do wyboru) w określonych punktach zdefiniowanego przez jego autora, będzie możliwe wznowienie działania przepływu pracy od ostatniego utrwalonego zadania (lub punktu kontrolnego), zamiast ponownego uruchamiania przepływu pracy od początku.

- **Niezawodność.** Automatyczne odzyskiwanie po awarii. Przepływy pracy poradzą sobie planowanych lub nieplanowanych ponownego uruchomienia. Można wstrzymać wykonywania przepływu pracy, a następnie wznowienie przepływu pracy od ostatniego punktu trwałości. Autorzy przepływu pracy można wyznaczyć konkretne działania, aby uruchomić ponownie w razie awarii na co najmniej jeden z węzłów zarządzanych.

- **Możliwość odłączyć, połącz się ponownie i uruchomić w sesji rozłączonych.** Użytkownicy mogą połączyć i zakończyć połączenie z serwerem przepływu pracy, ale przepływ pracy działa w sposób ciągły. Możesz wylogować się z komputera klienckiego lub uruchom ponownie komputer i monitorować wykonywania przepływu pracy z innego komputera bez przerywania tego przepływu pracy.

- **Podczas planowania.** Podobnie jak wszystkie polecenia cmdlet programu Windows PowerShell lub skryptu można zaplanować zadania przepływu pracy.

- **Przepływ pracy i ograniczania przepustowości połączenia.** Wykonywania przepływu pracy i nawiązania połączenia z węzłami może być ograniczony umożliwiając scenariusze skalowalności i wysokiej dostępności.

### <a name="windows-powershell-web-access"></a>Windows PowerShell Web Access
Windows PowerShell Web Access to funkcja systemu Windows Server 2012, która pozwala użytkownikom na uruchamianie poleceń środowiska Windows PowerShell i skryptów w konsoli sieci web. Urządzenia używające konsoli sieci web nie wymagają programu Windows PowerShell, oprogramowanie do zarządzania zdalnego lub instalacje wtyczki przeglądarki. Jest wymagany jest prawidłowo skonfigurowana brama programu Windows PowerShell Web Access i przeglądarka na urządzeniu klienckim obsługująca język JavaScript i akceptuje pliki cookie.

Aby uzyskać więcej informacji, zobacz [wdrażanie programu Windows PowerShell Web Access](http://go.microsoft.com/fwlink/p/?LinkID=221050).

### <a name="new-windows-powershell-ise-features"></a>Nowe funkcje programu PowerShell ISE systemu Windows
Dla programu Windows PowerShell 3.0, Windows PowerShell Integrated Scripting Environment (ISE) ma wiele nowych funkcji, w tym funkcji IntelliSense, okno polecenia Pokaż ujednoliconego okienku konsoli, fragmenty kodu, pasujących nawiasów klamrowych, rozwiń węzeł zwinięte sekcje, automatycznego zapisywania, ostatnio używanych elementów listy, rozbudowane kopii kopii bloku i pełną obsługę pisania przepływów pracy skryptu programu Windows PowerShell. Aby uzyskać więcej informacji, zobacz [about_Windows_PowerShell_ISE [3]](https://technet.microsoft.com/library/dfa54d47-60c6-4fff-8197-c747e8d411bb).

### <a name="support-for-microsoft-net-framework-4"></a>Obsługa programu Microsoft .NET Framework 4
Utworzono środowiska Windows PowerShell przy użyciu wspólnej 4.0 środowiska uruchomieniowego języka. Polecenia cmdlet, skrypt i autorów przepływu pracy można użyć nowych klas Microsoft .NET Framework 4 w programie Windows PowerShell z funkcjami, które obejmują zgodność aplikacji i wdrażania, Managed Extensibility Framework, równoległe obliczeniowych, sieci, systemu Windows Communication Foundation i programu Windows Workflow Foundation.

### <a name="support-for-windows-preinstallation-environment"></a>Obsługa środowiska preinstalacji systemu Windows
Program Windows PowerShell 3.0 jest opcjonalny składnik środowisko preinstalacji systemu Windows (Windows PE) 4.0, dla systemu Windows 8. Windows PE to minimalny system operacyjny, który uruchamia komputer, który nie ma systemu operacyjnego i przygotowuje je do instalacji systemu Windows. Środowiska Preinstalacyjnego systemu Windows może służyć do partycji i sformatować dyski twarde, kopiować obrazy dysków na komputerze i inicjowania Instalatora systemu Windows z udziału sieciowego. Program Windows PowerShell 3.0 można w środowisku Windows PE Zarządzanie wdrażaniem, diagnostyki i scenariuszy odzyskiwania.

### <a name="disconnected-sessions"></a>Sesje rozłączone
W programie Windows PowerShell 3.0, trwałe zarządzana przez użytkownika sesji ("PSSessions") utworzonych za pomocą polecenia cmdlet New-PSSession są zapisywane na komputerze zdalnym. Nie są one zależne od sesji, w której zostały utworzone.

Teraz możesz odłączyć od sesji bez zakłócania pracy z poleceniami, które są uruchomione w sesji. Możesz zamknąć sesji i Wyłącz komputer. Później można ponownie połączyć się z sesją z innej sesji na tym samym lub na innym komputerze.

**ComputerName** parametr [Get-PSSession](https://technet.microsoft.com/library/b2b10531-d0df-4746-b877-e75c09955cb6) polecenie cmdlet pobiera z wszystkie sesje użytkowników, które połączyć się z komputerem, teraz nawet, jeśli zostały one uruchomione w innej sesji na innym komputerze. Można nawiązać sesji, wyniki polecenia, Uruchom nowe polecenia, a następnie rozłączyć sesję.

Dodano nowe polecenia cmdlet do obsługi funkcji rozłączone sesje tym [Disconnect-PSSession](https://technet.microsoft.com/library/f8f95111-612f-4cba-9098-77904b0473d8), [Connect-PSSession](https://technet.microsoft.com/library/b803dd29-f208-4079-80d4-db04d778f060), i Receive-PSSession i nowe parametry zostały dodane do polecenia cmdlet, których zarządzanie PSSessions, takich jak **InDisconnectedSession** parametr [Invoke-Command](https://technet.microsoft.com/library/906b4b41-7da8-4330-9363-e7164e5e6970) polecenia cmdlet.

Funkcja odłączony sesji jest obsługiwana tylko wtedy, gdy komputery zarówno na poziomie źródłowym ("client") i przerywa końców połączenia ("server") są uruchomione programu Windows PowerShell 3.0.

### <a name="robust-session-connectivity"></a>Sesja niezawodna łączności
Program Windows PowerShell 3.0 wykrywa straty Nieoczekiwana łączności między klientem a serwerem i podejmie próbę ponownego nawiązania połączenia i automatycznie wznawia wykonywanie. Jeśli nie można ponownie ustanowić połączenia klient serwer, w przydzielonym czasie, użytkownik jest powiadamiany i zostanie rozłączona sesja. Podczas próby ponownego połączenia programu Windows PowerShell udostępnia ciągłym informacjom zwrotnym dla użytkownika.

Jeśli rozłączona sesja została uruchomiona przy użyciu InvokeCommand, programu Windows PowerShell tworzy zadanie odłączonej sesji ułatwić Połącz się ponownie i wznowić wykonywanie.

Te funkcje Obsługa komunikacji zdalnej bardziej niezawodne i możliwe do odzyskania oraz umożliwić użytkownikom do wykonywania długotrwałych zadań, które wymagają niezawodnych sesji, takie jak przepływów pracy.

### <a name="updatable-help-system"></a>System aktualizowalnej pomocy
Można teraz pobrać pliki zaktualizowany pomocy dla poleceń cmdlet w modułach. [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) polecenia cmdlet identyfikuje najnowszych plików pomocy, pobiera je z Internetu, wypakowuje je, sprawdza je i instaluje je w poprawnym katalogu określonego języka dla modułu.

Aby używać plików pomocy zaktualizowany, po prostu wpisz `Get-Help`. Nie jest konieczne ponowne uruchomienie systemu Windows lub programu Windows PowerShell. Aby zaktualizować Pomoc dla modułów w katalogu $pshome, uruchom program Windows PowerShell przy użyciu opcji "Uruchom jako administrator".

Do obsługi użytkowników, którzy nie mają dostępu do Internetu i użytkownicy za zaporą, nowe [Save-Help](https://technet.microsoft.com/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa) polecenie cmdlet pobiera pliki pomocy do katalogu w systemie plików, na przykład do udziału plików. Użytkownicy mogą następnie skorzystać [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) polecenia cmdlet, aby pobrać pliki pomocy zaktualizowane z udziału plików.

Można użyć [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) pliki polecenia cmdlet, aby zaktualizować Pomoc dla wszystkich lub moduły określonego we wszystkich obsługiwanych interfejsu użytkownika kultur. Można nawet zawiesić [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) w profilu programu Windows PowerShell. Domyślnie programu Windows PowerShell pobiera pliki pomocy dla modułu nie więcej niż jeden raz każdego dnia.

Moduły Windows 8 i Windows Server 2012 należy umieszczać pliki pomocy. Aby pobrać najnowsze pliki pomocy, wpisz `Update-Help`. Aby uzyskać więcej informacji, wpisz `Get-Help` (bez parametrów) lub zobacz [about_Updatable_Help](https://technet.microsoft.com/library/10bba75c-f4ac-4ca1-bbf3-8f34dd521ffe).

Gdy pliki pomocy dla polecenia cmdlet nie są zainstalowane na komputerze, [Get-Help](https://technet.microsoft.com/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) polecenia cmdlet są obecnie wyświetlane automatycznie generowanej pomocy. Automatycznie generowanej pomocy zawiera składnię polecenia i instrukcje dotyczące używania [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) polecenia cmdlet, aby pobrać pliki pomocy.

Dowolnego autora modułu może obsługiwać aktualizowalnej pomocy dla ich modułu. Możesz obejmują pliki pomocy w module i użyj aktualizowalnej pomocy, aby je aktualizować lub Pomiń pliki pomocy i użyj aktualizowalnej pomocy, aby je zainstalować. Aby uzyskać więcej informacji na temat obsługi aktualizowalnej pomocy, zobacz [Obsługa aktualizowalnej pomocy](http://go.microsoft.com/FWLink/?LinkID=242129) w witrynie MSDN.

### <a name="enhanced-online-help"></a>Ulepszone pomocy Online
Pomoc programu Windows PowerShell jest zasobem cenne dla wszystkich użytkowników, ale jest szczególnie ważne dla użytkowników, których nie chcesz lub nie można zainstalować pliki pomocy zaktualizowane.

Aby uzyskać pomoc online dla każdego polecenia cmdlet programu Windows PowerShell, wpisz:

```
Get-Help <cmdlet-name> -Online
```

Programu Windows PowerShell powoduje otwarcie wersji online tematu pomocy w domyślnej przeglądarki internetowej.

**Get-Help-Online** funkcji w środowisku Windows PowerShell 3.0 jest teraz jeszcze bardziej skuteczne, ponieważ działa ona, nawet jeśli pliki pomocy dla polecenia cmdlet nie są zainstalowane na komputerze. **Get-Help-Online** funkcja pobiera identyfikator URI dla tematu Pomocy online z właściwości HelpUri poleceń cmdlet i zaawansowane funkcje.

```
PS C:\>(Get-Command Get-ScheduledJob).HelpUri
http://go.microsoft.com/fwlink/?LinkID=223923
```

W programie Windows PowerShell 3.0, autorzy C# polecenia cmdlet można wypełnić **HelpUri** właściwości tworząc **HelpUri** atrybutu dla klasy polecenia cmdlet. Autorzy zaawansowane funkcje mogą definiować **HelpUri** właściwość **CmdletBinding** atrybutu. Wartość **HelpUri** właściwości musi zaczynać się od "http" lub "https".

Możesz również uwzględnić **HelpUri** wartości w pierwszy link powiązane z pliku pomocy polecenia cmdlet opartego na XML lub. Dyrektywa Link Pomoc oparta na komentarzach w funkcji.

Aby uzyskać więcej informacji na temat obsługi pomocy online, zobacz [Obsługa pomocy Online](http://go.microsoft.com/fwlink/?LinkId=242132) w witrynie MSDN.

### <a name="cim-integration"></a>Integracja modelu wspólnych informacji
Program Windows PowerShell 3.0 obsługuje dla wspólnych informacji (CIM), co zapewnia wspólnych definicji informacji zarządzania dla systemów, sieci, aplikacji i usług, dzięki czemu wymiany informacji o zarządzaniu między systemy heterogenicznych. Obsługa modelu wspólnych informacji w programie Windows PowerShell 3.0, w tym możliwość tworzenia oparte na klasy modelu CIM nowy lub istniejący, poleceń cmdlet środowiska Windows PowerShell na podstawie polecenia cmdlet definicji pliki XML, pomocy technicznej dla programu .NET Framework modelu wspólnych informacji. Interfejs API modelu wspólnych informacji poleceń cmdlet do zarządzania i dostawców usługi WMI 2.0.

### <a name="session-configuration-files"></a>Pliki konfiguracji sesji
W programie Windows PowerShell 3.0, można zaprojektować niestandardową konfigurację sesji przy użyciu pliku. Plik konfiguracji nowej sesji umożliwia określenie sesji, które korzysta z konfiguracji sesji, które moduły skryptów, w tym środowisku i pliki w formacie są ładowane do sesji, można użyć poleceń cmdlet i język użytkowników elementy, które moduły i Skrypty można uruchomić i zmienne, które będą mogli wyświetlać.

Można zaprojektować sesji, w którym użytkownicy mogą uruchamiać tylko polecenia cmdlet z jednego określonego modułu lub sesji, w której użytkownicy mają pełną obsługą języka, dostęp do wszystkich modułów i dostępu do skryptów służących do wykonywania zaawansowanych zadań.

W poprzednich wersjach programu Windows PowerShell kontrolę na tym poziomie nie była dostępna tylko do tych osób, które można zapisać program C# lub skrypt uruchamiania złożonych. Teraz każdy członek grupy Administratorzy na komputerze można dostosować konfigurację sesji przy użyciu pliku konfiguracji.

Aby utworzyć plik konfiguracji sesji, należy użyć [PSSessionConfigurationFile nowy](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866) polecenia cmdlet. Aby zastosować plik konfiguracji sesji do konfiguracji sesji, należy użyć [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) lub [Set-PSSessionConfiguration](https://technet.microsoft.com/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) polecenia cmdlet.

Aby uzyskać więcej informacji, zobacz [informacje o plikach](https://technet.microsoft.com/library/c7217447-1ebf-477b-a8ef-4dbe9a1473b8) i [PSSessionConfigurationFile nowy](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866).

### <a name="scheduled-jobs-and-task-scheduler-integration"></a>Zaplanowane zadania i integracja z harmonogramu zadań
Można teraz planować zadań w tle programu Windows PowerShell i zarządzać nimi w programie Windows PowerShell i w harmonogramie zadań.

Zadania zaplanowane środowiska Windows PowerShell są przydatne hybrydowego zadań w tle programu Windows PowerShell i zadań harmonogramu zadań.

Podobnie jak zadań w tle programu Windows PowerShell zaplanowane zadania uruchamiane asynchronicznie w tle. Wystąpienia zaplanowanych zadań, które ukończyły można zarządzać za pomocą polecenia cmdlet zadania, takie jak [rozpoczęcia zadania](https://technet.microsoft.com/library/2bc04935-0deb-4ec0-b856-d7290cca6442) i [Get-Job](https://technet.microsoft.com/library/1352c534-7193-46ca-9ab1-0c5219a661ad).

Podobnie jak zadania harmonogramu zadań można uruchomić zaplanowanych zadań zgodnie z harmonogramem jednokrotne lub cykliczne, lub w odpowiedzi na akcję lub zdarzeń. Można wyświetlić i zarządzać zadań zaplanowanych w harmonogramie zadań, włączyć i wyłączyć je w razie potrzeby, uruchom je lub użyj ich jako szablon, a określenie warunków, w których uruchomić zadania.

Ponadto zaplanowane zadania mają dostosowane zestaw poleceń cmdlet do zarządzania nimi. Polecenia cmdlet umożliwiają tworzenia, edytowania, zarządzanie, wyłączyć i ponownie włączyć zaplanowanych zadań, Utwórz zaplanowane zadanie wyzwalaczy i ustaw opcje zaplanowanego zadania.

Aby uzyskać więcej informacji na temat zaplanowanych zadań, zobacz [about_Scheduled_Jobs](https://technet.microsoft.com/library/3b546629-703c-4939-b44f-52dd567bce92).

### <a name="windows-powershell-language-enhancements"></a>Funkcje języka programu PowerShell systemu Windows
Windows PowerShell 3.0 zawiera wiele funkcji, które ułatwiają jego język prostsze, łatwiejsze do użycia oraz w celu uniknięcia typowych błędów. Ulepszenia obejmują właściwości wyliczenia, liczby i długości właściwości skalarne obiektów, nowych operatorów przekierowania, modyfikator zakresu $Using, formatowanie automatycznych zmiennych, elastyczne skryptu PSItem, atrybuty zmiennych, uproszczone atrybutu argumenty, nazw liczbowych poleceń, analizowania Stop operatora, splatting ulepszone tablicy, nowych operatorów bitowych, uporządkowanej słowników, rzutowanie PSCustomObject i rozszerzona Pomoc oparta na komentarzach.

### <a name="new-core-cmdlets"></a>Nowe polecenia cmdlet Core
Dodano nowe polecenia cmdlet w instalacji programu Windows PowerShell Core, łącznie z poleceniami cmdlet do zarządzania zaplanowanych zadań, rozłączonych sesji, integracji modelu wspólnych informacji i nadaje się do aktualizacji Pomocy systemu.

|||
|-|-|
|Dodaj JobTrigger|Nowy JobTrigger|
|Connect-PSSession|Nowe PSSessionConfigurationFile|
|ConvertFrom Json|New-PSTransportOption|
|ConvertTo-Json|Nowe PSWorkflowExecutionOption|
|Disable-JobTrigger|New-PSWorkflowSession|
|Disable-ScheduledJob|Nowe ScheduledJobOption|
|Odłącz PSSession|Nowe WinEvent|
|Włącz JobTrigger|Odbieranie PSSession|
|Włącz ScheduledJob|Rejestr CimIndicationEvent|
|Get-CimAssociatedInstance|Register-ScheduledJob|
|Get-CimClass|Usuń CimInstance|
|Get-CimInstance|Remove-CimSession|
|Get-CimSession|Usuń TypeData|
|Get-ControlPanelItem|Zmień nazwę komputera|
|Get-IseSnippet|Resume-Job|
|Get-JobTrigger|Save-Help|
|Get-ScheduledJob|Zestaw CimInstance|
|Get-ScheduledJobOption|Set-JobTrigger|
|Get-TypeData|Set-ScheduledJob|
|IseSnippet importu|Zestaw ScheduledJobOption|
|Wywołanie AsWorkflow|Pokaż polecenia|
|Wywołanie CimMethod|Pokaż ControlPanelItem|
|Wywołanie RestMethod|Wstrzymaj zadanie|
|Wywołanie WebRequest|PSSessionConfigurationFile testu|
|Nowe CimInstance|Odblokować plik|
|Nowy CimSession|Unregister-ScheduledJob|
|Nowe CimSessionOption|Update-Help|
|Nowe IseSnippet||

### <a name="improvements-to-existing-core-cmdlets-and-providers"></a>Ulepszenia istniejących podstawowych poleceń cmdlet i dostawców
Windows PowerShell 3.0 obejmuje nowe funkcje istniejących poleceń cmdlet wraz ze składnią uproszczoną i nowe parametry dla następujących poleceń cmdlet: polecenia cmdlet Computer, CSV polecenia cmdlet Get-ChildItem Get-Command, Get-Content zabezpieczeń Get-Historia obiektu miary polecenia cmdlet Select-Object, wybierz ciąg, Podziel-Path, procesu uruchamiania Tee-Object, Test-Connection, Dodaj członków i polecenia cmdlet usługi WMI.

Dostawcy programu Windows PowerShell również udoskonalone znacznie, w tym obsługa dostawcy certyfikatów zarządzania certyfikatami Secure Socket Layer (SSL) dla usługi hostingu sieci web, obsługa poświadczeń, dyski sieciowe trwałe i alternatywne strumienie danych w system plików dysków.

### <a name="remote-module-import-and-discovery"></a>Importuj moduł zdalnego i odnajdywania
Program Windows PowerShell 3.0 rozszerza odnajdywania modułu, importowanie i możliwości niejawne komunikacji zdalnej na komputerach zdalnych. Polecenia cmdlet modułu uzyskać modułów na komputerach zdalnych i zaimportuj moduły na komputerze lokalnym lub zdalnym przy użyciu komunikacji zdalnej programu Windows PowerShell. Obsługa nowej sesji CIM umożliwia przy użyciu modelu wspólnych informacji i usługi WMI do zarządzania komputerami z systemem innym niż Windows, importując poleceń na komputerze lokalnym, który niejawnie uruchomiony na komputerze zdalnym.

Aby uzyskać więcej informacji, zobacz Tematy pomocy dla [Get-Module](https://technet.microsoft.com/library/2cccd4c4-9a21-4c77-b691-984ee57242e1) i [Import-Module](https://technet.microsoft.com/library/af616c24-e122-4098-930e-1e3ea2080ade) polecenia cmdlet.

### <a name="enhanced-tab-completion"></a>Uzupełnianie po naciśnięciu tabulatora rozszerzone
Uzupełnianie po naciśnięciu tabulatora w konsoli środowiska Windows PowerShell teraz uzupełnia nazwy poleceń cmdlet, parametry, wartości parametrów, wyliczenia, platformy .NET Framework typów, COM obiektów, foldery i więcej. Funkcję uzupełniania karta została napisana, na podstawie nowy analizator składni i drzewa składni abstrakcyjnej do obsługi scenariuszy, w tym drzewa analizy w pamięci i uzupełniania po naciśnięciu tabulatora linii środkowej.

### <a name="module-auto-loading"></a>Automatyczne ładowanie modułu
[Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) polecenia cmdlet teraz pobiera wszystkie polecenia cmdlet i funkcje z wszystkich modułów, które są zainstalowane na komputerze, nawet jeśli moduł nie został zaimportowany do bieżącej sesji.

Po wyświetleniu okna polecenia cmdlet, które są potrzebne, można go natychmiast bez importowania wszelkich modułów. Moduły programu Windows PowerShell teraz są importowane automatycznie, korzystając z dowolnym poleceniu cmdlet w module. Nie należy do wyszukania modułu i zaimportować go do korzystania z jego poleceń cmdlet.

Automatyczne importowanie modułów zostanie wywołany za pomocą polecenia cmdlet uruchomione w poleceniu, **Get-Command** dla polecenia cmdlet bez symboli wieloznacznych lub systemem [Get-Help](https://technet.microsoft.com/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) dla polecenia cmdlet bez symboli wieloznacznych.

Można włączyć, wyłączyć i skonfigurować automatyczne importowanie modułów za pomocą **$PSModuleAutoLoadingPreference** zmiennej preferencji.

Aby uzyskać więcej informacji, zobacz [modułach [4]](https://technet.microsoft.com/library/94f57429-a539-4aee-bb0d-205cd7e801f9), [about_Preference_Variables [4]](https://technet.microsoft.com/library/31344314-be29-4286-b039-afa5460cbe8b)i tematy pomocy dla [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) i [Import-Module ](https://technet.microsoft.com/library/af616c24-e122-4098-930e-1e3ea2080ade) polecenia cmdlet.

### <a name="module-experience-improvements"></a>Ulepszenia obsługi modułu
Moduły, w tym następujące nowe funkcje programu Windows PowerShell 3.0 oferuje obsługę zaawansowanych funkcji.

1. Modułu rejestrowania dla poszczególnych modułów (LogPipelineExecutionDetails) i nowe ustawienie zasad grupy "Włącz na modułu rejestrowania"

2. Rozszerzony modułu obiektów, które udostępniają wartości w manifeście modułu

3. Nowy **ExportedCommands** właściwości moduły, w tym zagnieżdżone modułów, które polecenia wszystkie typy łączy

4. Ulepszone odnajdowania dostępne modułów (które nie zostały zaimportowane), w tym, co pozwala **ścieżki** i **flagą ListAvailable** parametrów w tym samym poleceniu

5. Nowy **DefaultCommandPrefix** kluczy w module manifestów, które pozwala uniknąć konfliktów nazw bez zmiany kodu modułu.

6. Ulepszone wymagania modułu, w tym pełną wymagane moduły z wersją i identyfikator GUID i automatyczne importowanie wymagane moduły

7. Zapewniająca, sprawnego funkcjonowania [ModuleManifest nowy](https://technet.microsoft.com/library/512adced-f42f-4e88-ba7c-834fc9e5d047) polecenia cmdlet.

8. Nowy **modułu** parametr #Requires

9. Ulepszone [Import-Module](https://technet.microsoft.com/library/af616c24-e122-4098-930e-1e3ea2080ade) polecenia cmdlet zarówno **MinimumVersion** i **RequiredVersion** parametrów.

### <a name="simplified-command-discovery"></a>Polecenie uproszczony odnajdywania
Nie trzeba importować wszystkie moduły, aby odnaleźć dostępne do sesji polecenia. W programie Windows PowerShell 3.0 [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) polecenie cmdlet pobiera wszystkie polecenia ze wszystkich zainstalowanych modułów. A jeśli używasz polecenia moduł, który eksportuje polecenia jest automatycznie importowane do sesji.

Nowy [Pokaż polecenie](https://technet.microsoft.com/library/65bba50b-91a8-49d5-80a2-a30fc684ba41) polecenia cmdlet jest przeznaczona szczególnie dla początkujących użytkowników. W oknie można wyszukiwać. Można wyświetlić wszystkie polecenia lub filtrować przez moduł, zaimportować moduł, klikając przycisk, użyj pola tekstowe i list rozwijanych, aby utworzyć prawidłowe polecenie, a następnie skopiować lub uruchom polecenie bez zamykania okna.

### <a name="improved-logging-diagnostics-and-group-policy-support"></a>Rejestrowanie udoskonalone, diagnostyki i obsługa zasad grupy
Program Windows PowerShell 3.0 poprawia rejestrowania i śledzenia pomocy technicznej dla poleceń i moduły ze śledzenia zdarzeń w dziennikach zdarzeń systemu Windows (ETW), można edytować **LogPipelineExecutionDetails** właściwości modułów i "Włącz w Module Grupy rejestrowania"ustawienia zasad. Teraz można uzyskać wartości parametrów z szczegóły dziennika za pomocą wyświetlania właściwości dziennika.

### <a name="formatting-and-output-improvements"></a>Formatowanie i ulepszenia danych wyjściowych
Nowy format i dane wyjściowe ulepszenia zwiększyć wydajność wszystkich użytkowników programu Windows PowerShell. Ulepszenia obejmują przekierowywanie danych wyjściowych dla wszystkich strumieni, rozszerzone polecenia cmdlet typ aktualizacji, które dodaje typy dynamicznie bez plików Format.ps1xml, zawijania słów w danych wyjściowych domyślnej właściwości formatowania niestandardowych obiektów **PSCustomObject** tekst, ulepszone formatowanie obiektów WMI i heterogenicznych obiektów i obsługę przeciążenia metody odnajdywania.

### <a name="enhanced-console-host-experience"></a>Środowisko hosta rozszerzone konsoli
Program Windows PowerShell konsoli hosta ma nowe funkcje w tym pojedynczego komórek wielowątkowych domyślnie programu Windows PowerShell 3.0. Nowa opcja "Uruchamianie ze środowiska PowerShell" w Eksploratorze plików umożliwia uruchamianie skryptów w sesji nieograniczony przez kliknięcie prawym przyciskiem myszy. Nowe Logika uruchamiania hosta konsoli uruchamia środowiska Windows PowerShell szybciej i nowych czcionek pozwalają personalizować środowisko okna konsoli znane.

Aby uzyskać więcej informacji, zobacz [about_Run_With_PowerShell](https://technet.microsoft.com/library/c9d9ca5f-eff9-4409-be9d-e43b5b4087eb).

### <a name="new-cmdlet-and-hosting-apis"></a>Nowe polecenia Cmdlet i hostingu API
Nowe polecenia Cmdlet interfejsu API i obsługa interfejsu API obejmują drzewo składni zaawansowane publiczny (AST) interfejsów API i interfejsów API potoku stronicowania, zagnieżdżonych potoki, uzupełniania po naciśnięciu tabulatora pule obszaru działania, Windows RT, atrybut przestarzałe polecenia cmdlet i właściwości zlecenie i rzeczownik obiektu FunctionInfo.

### <a name="performance-improvements"></a>Ulepszenia wydajności
Znaczący wzrost wydajności w programie Windows PowerShell pochodzą z nowego analizatora języka, który jest oparty na dynamiczne środowiska uruchomieniowego języka (DLR) w programie .NET Framework 4., wraz z kompilacja skryptu środowiska uruchomieniowego, aparat ulepszenia niezawodności i zmiany Algorytm [Get-ChildItem](https://technet.microsoft.com/library/75cf79bb-4db6-4a67-8c36-3d20754e2190) który zwiększenia wydajności, szczególnie w przypadku udziałów wyszukiwanie w sieci.

### <a name="runas-and-shared-host-support"></a>Uruchom jako i obsługa hostów udostępnionego
Program Windows PowerShell 3.0 obejmuje obsługę funkcji Uruchom jako i udostępnionych przez hosta.

*RunAs* funkcja przeznaczona dla przepływu pracy środowiska Windows PowerShell, umożliwia użytkownikom konfiguracji sesji, tworzenia sesji, które są uruchamiane z uprawnieniami konta użytkownika udostępnionego. Umożliwia to mniej uprzywilejowanej użytkownikom na uruchamianie określonych poleceń i skryptów z uprawnieniami administratora oraz zmniejsza potrzebę Dodawanie mniej wyższych użytkowników do grupy Administratorzy.

**SharedHost** funkcji umożliwia wielu użytkownikom na wielu komputerach, aby podłączyć się jednocześnie sesję przepływu pracy i monitorować postęp przepływu pracy. Użytkownicy mogą uruchomić przepływ pracy na jednym komputerze, a następnie nawiązać sesji przepływu pracy na innym komputerze bez rozłączeniu sesji z oryginalnego komputera. Użytkownicy muszą mieć te same uprawnienia i używać tą samą konfiguracją sesji. Aby uzyskać więcej informacji zobacz "Systemem Windows PowerShell Workflow" w wprowadzenie do przepływu pracy środowiska Windows PowerShell.

### <a name="special-character-handling-improvements"></a>Ulepszenia obsługi znaków specjalnych
Aby zwiększyć możliwości programu Windows PowerShell 3.0 interpretowania i prawidłowej obsługi znaków specjalnych, **LiteralPath** parametr, który obsługuje znaków specjalnych w ścieżkach, jest prawidłowy w niemal wszystkich poleceń cmdlet, które mają  **Ścieżka** parametru, w tym nowe [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) i [Save-Help](https://technet.microsoft.com/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa) polecenia cmdlet. Analizator obejmuje również specjalną logikę do poprawy obsługi znaku backtick (\`) i nawiasy kwadratowe w nazwach plików i ścieżek.

## <a name="see-also"></a>Zobacz też
- [about_Windows_PowerShell_5.0](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_powershell_5.0?view=powershell-5.0)
- [Środowisko Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116)